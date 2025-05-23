# プロジェクト情報更新機能

## 概要

プロジェクト情報更新機能は、既存のプロジェクトの基本情報を変更するための機能です。プロジェクトオーナーや管理者がプロジェクト名やログイン名を更新することができます。

## 機能要件

### プロジェクト情報更新

プロジェクトの基本情報を更新する機能を提供します。

1. プロジェクト名の変更
2. プロジェクトログイン名の更新
3. 更新内容の保存処理
4. 更新完了後のフィードバック表示

## 技術要件

1. GraphQL APIを通じたプロジェクト情報の更新
2. プロジェクト名のバリデーション
3. ログイン名の一意性チェック
4. 更新日時(updatedAt)の自動更新

## ビジネスルール

1. プロジェクト情報の更新はオーナー(OWNER)と管理者(ADMIN)のみ可能
2. プロジェクト名は128文字以内でなければならない
3. プロジェクト更新時は更新日時(updatedAt)を自動更新

## UX要件

1. 直感的な編集インターフェース
2. フォーム入力のリアルタイムバリデーション
3. 変更のフィードバックを即時表示
