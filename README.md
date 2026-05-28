# EC1000本ノック #001
Java + Spring Boot で構築した EC サイト。
## 新しく学習、取り組んだこと
```txt
vscode + copilot でのコーディング
簡易的な開発フローの作成とそれに則った開発
コーディングなど設計
DI
AOP
DBのmigration
Render
Javaの監視
```
## 開発フロー
```
リポジトリ作成
TODO作成
技術選定
ユースケース整理
デザイン作成
ER図作成
素材集め
環境構築
スキーマ定義
Migration作成
API設計
Routing設計
認証設計
UIコンポーネント設計
コーディング
動作確認(手動デバッグ)
デプロイの設定
本番環境構築
デプロイ
監視・ログ設定
README修正
```
## 使用技術

### バックエンド
```txt
Java 21
Spring Boot
Spring MVC
Spring Data JPA
Bean Validation
Spring AOP
Spring Actuator
Flyway
Lombok
Gradle
```
### フロントエンド
```txt
Thymeleaf
HTML
CSS
Tailwind CSS
JavaScript
```
### DB
```txt
PostgreSQL
```
### PaaS
```txt
Render
```
## DBテーブル
### users
| カラム名 | 型 | 説明 |
|---|---|---|
| id | bigint | PK |
| name | varchar | ユーザー名 |
| email | varchar | メールアドレス |
| created_at | timestamp | 作成日時 |
### product_categories
| カラム名 | 型 | 説明 |
|---|---|---|
| id | bigint | PK |
| name | varchar | カテゴリ名 |
| status | varchar | CategoryStatus(enum) |
| created_at | timestamp | 作成日時
### products
カラム名 | 型 | 説明 |
|---|---|---|
| id | bigint | PK |
| category_id | bigint | FK |
| name | varchar | 商品名 |
| description | text | 商品説明 |
| price | integer | 価格 |
| stock | integer | 在庫数 |
| image_url | varchar | 商品画像URL |
| status | varchar | ProductStatus(enum) |
| created_at | timestamp | 作成日時 |
### carts
| カラム名 | 型 | 説明 |
|---|---|---|
| id | bigint | PK |
| user_id | bigint | FK |
| status | varchar | CartStatus(enum) |
| created_at | timestamp | 作成日時 |
### cart_items
| カラム名 | 型 | 説明 |
|---|---|---|
| id | bigint | PK |
| cart_id | bigint | FK |
| product_id | bigint | FK |
| quantity | integer | 数量 |
| created_at | timestamp | 作成日時 |
### orders
| カラム名 | 型 | 説明 |
|---|---|---|
| id | bigint | PK |
| user_id | bigint | FK |
| total_price | integer | 合計金額 |
| status | varchar | OrderStatus(enum) |
| created_at | timestamp | 作成日時
### order_items
| カラム名 | 型 | 説明 |
|---|---|---|
| id | bigint | PK |
| order_id | bigint | FK |
| product_id | bigint | FK |
| product_name | varchar | 注文時商品名 |
| price | integer | 注文時価格 |
| quantity | integer | 数量 |
| created_at | timestamp | 作成日時 |
## enum
### ProductStatus
ACTIVE
HIDDEN
SOLD_OUT

---

### CartStatus
ACTIVE
ORDERED
EXPIRED

---

### OrderStatus

CREATED
CANCELLED

---

### CategoryStatus

ACTIVE
HIDDEN
