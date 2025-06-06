---
applyTo: "**/api/infrastructure/repositories/*.repository.ts"
---

# api/infrastructure/repositories/*.repository.ts

2つのメソッドしか実装しません。

- write
  - Entityを受け取りデータベースに書き込む
  - return null
- read
  - データベースを読み取りEntityに詰め替えて返す

```tsx
import { UserEntity } from "~/domain/entities/user.entity"
import { NameValue } from "~/domain/values/name.value"
import type { Context } from "~/env"

export class UserRepository {
  constructor(readonly c: Context) {}

  async write(entity: UserEntity) {
    try {
      await this.c.var.database.prismaUser.upsert({
        where: { id: entity.id },
        create: {
          id: entity.id,
        },
        update: {
          login: entity.login,
        },
      })

      return null
    } catch (e) {
      console.error(e)
      return new Error()
    }
  }

  async read(id: string): Promise<UserEntity | null> {
    try {
      const data = await this.c.var.database.prismaUser.findUniqueOrThrow({
        where: { id },
      })

      if (data === null) {
        return null
      }

      return new UserEntity({
        id: data.id,
      })
    } catch (e) {
      console.error(e)
      return null
    }
  }
}
```
