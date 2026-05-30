# EC1000本ノック #001
Java + Spring Boot で構築した EC サイト。
## 新しく学習、取り組んだこと
- vscode + copilot でのコーディング
- v0を用いたデザイン作成
- wsl環境での開発
- 簡易的な開発フローの作成とそれに則った開発
  ユースケース(触りだけ作って断念)
  ER図の作成(schema.dbmlから作成)
- コーディングなど設計
- DI
- AOP
- DBのmigration
- JOOQ
- Render
- Javaの監視
## 改善したいこと、新しく取り組みたくなったこと
①ER図をdbmlから作ると、データベースを変更するたびにdbmlと画像を修正しないといけなくなる
migrationから自動で生成するようにする
```txt
Migration
↓
DB
↓
ER図、スキーマドキュメント自動生成
```

## ユースケース
### actor
- 購入者
- 商品管理者（自分）
### use cases
購入者
- 商品を探す
- 商品詳細を確認する
- 商品を注文する
管理者
- 商品を管理する
- 注文を管理する
## 開発フロー
```md
1. リポジトリ作成
2. TODO作成
3. 技術選定
4. ユースケース整理
5. デザイン作成
6. ER図作成
7. 素材集め
8. 環境構築
9. スキーマ定義
10. Migration作成
11. API設計
12. Routing設計
13. 認証設計
14. UIコンポーネント設計
15. コーディング
16. 動作確認(手動デバッグ)
17. デプロイの設定
18. 本番環境構築
19. デプロイ
20. 監視・ログ設定
21. README修正
```
## 使用技術

### バックエンド
Language: 
  Java 21
Framework: 
  Spring Boot
build: 
  Gradle

- Spring MVC
- JOOQ
- Bean Validation
- Spring AOP
- Spring Actuator
- Flyway
- Lombok
### フロントエンド
- JavaScript
- Thymeleaf
- HTML
- CSS
- Tailwind CSS
### DB
PostgreSQL
### PaaS
Render
## DB
データベースのスキーマ
- [schema.dbml](./docs/schema.dbml)
![ERD](./docs/ERD.png)