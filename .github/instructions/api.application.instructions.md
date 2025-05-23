---
applyTo: "**/api/application/**/*.ts"
---

# api/application/**/*.ts

- idはcrypto.randomUUID()
- 例外はErrorをreturn
- try-catchする
- HTTPExceptionを返却する
- ユーザフレンドリーなエラーメッセージ

### create-*.ts

データを追加する。

```tsx
type Props = {
  name: string
}

/**
 * 組織を作成する
 */
export class CreateOrganization {
  constructor(
    readonly c: Context,
    readonly deps = {
      repository: new OrganizationRepository(c),
    },
  ) {}

  async run(props: Props) {
    try {
      const organizationId = crypto.randomUUID()

      const organization = new OrganizationEntity({
        id: organizationId,
        name: props.name,
      })

      const result = await this.deps.repository.write(organization)

      if (result instanceof Error) {
        return new InternalGraphQLError()
      }

      return organization
    } catch (error) {
      return new InternalGraphQLError()
    }
  }
}
```

### update-*.ts

データを更新する。

- ドメインモデルのメソッドを用いて更新する

```tsx
type Props = {
  id: string
  name: string
}

/**
 * 組織を作成する
 */
export class UpdateOrganization {
  constructor(
    readonly c: Context,
    readonly deps = {
      repository: new OrganizationRepository(c),
    },
  ) {}

  async run(props: Props) {
    try {
      const organization = await this.deps.repository.read(props.id)

      const draft = organization.updateName({
        name: props.name,
      })

      const result = await this.deps.repository.write(draft)

      if (result instanceof Error) {
        return new InternalGraphQLError()
      }
      
      return organization
    } catch (error) {
      return new InternalGraphQLError()
    }
  }
}
```
