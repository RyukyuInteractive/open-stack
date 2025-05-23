# プロジェクトメンバー一覧表示機能

プロジェクトに所属するメンバーの一覧を表示するための機能です。

1. ユーザーがプロジェクトメンバー一覧画面を開く
2. システムがプロジェクトに所属するメンバー情報を取得する
3. システムがメンバー情報（ユーザー名、ロールなど）を一覧で表示する
4. ページネーションにより最大16件ずつ表示し、ユーザーが次/前のページを閲覧できる
5. ユーザーがメンバーの詳細情報を確認できる

## 技術要件

1. GraphQL APIを通じたプロジェクトメンバー情報の取得
2. ページネーション機能の実装（最大16件/ページ）
3. 権限に応じた操作ボタンの表示制御

## ビジネスルール

1. すべてのプロジェクトメンバーがメンバー一覧を閲覧可能
2. メンバー一覧はロール順（OWNER、ADMIN、MEMBER、VIEWER）で表示
3. 同一ロール内では名前順で表示

## UX要件

1. メンバーの役割と権限の視覚的な表示
2. レスポンシブデザインによるモバイル対応
3. ロールごとの色分けや視覚的区別の提供
