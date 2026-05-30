# EC1000本ノック #001
Java + Spring Boot で構築した EC サイト。
## 新しく学習、取り組んだこと
```txt
vscode + copilot でのコーディング
v0を用いたデザイン作成
簡易的な開発フローの作成とそれに則った開発
  ユースケース(触りだけ作って断念)
コーディングなど設計
DI
AOP
DBのmigration
JOOQ
Render
Javaの監視
```
## ユースケース
### actor
購入者
商品管理者（自分）
### use cases
#### 購入者
- 商品を探す
- 商品詳細を確認する
- 商品を注文する
#### 管理者
- 商品を管理する
- 注文を管理する
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
JOOQ
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
|----------|----|------|
| id | BIGINT | PK |
| name | VARCHAR | 名前 |
| email | VARCHAR | メールアドレス |
| password | VARCHAR | パスワード |
| role | ENUM | purchaser/admin |
| created_at | DATETIME | 作成日時 |
| updated_at | DATETIME | 更新日時 |

---
### product_categories
| カラム名 | 型 | 説明 |
|----------|----|------|
| id | BIGINT | PK |
| name | VARCHAR | 商品名 |
| description | TEXT | 商品説明 |
| price | DECIMAL | 価格 |
| stock | INT | 在庫数 |
| created_at | DATETIME | 作成日時 |
| updated_at | DATETIME | 更新日時 |

---

### products
| カラム名 | 型 | 説明 |
|----------|----|------|
| id | BIGINT | PK |
| user_id | BIGINT | FK |
| order_date | DATETIME | 注文日時 |
| status | VARCHAR | 注文状態 |
| total_amount | DECIMAL | 合計金額 |
| created_at | DATETIME | 作成日時 |
| updated_at | DATETIME | 更新日時 |

---
### carts
| カラム名 | 型 | 説明 |
|----------|----|------|
| id | BIGINT | PK |
| user_id | BIGINT | FK |
| created_at | DATETIME | 作成日時 |
| updated_at | DATETIME | 更新日時 |

---

### cart_items
| カラム名 | 型 | 説明 |
|----------|----|------|
| id | BIGINT | PK |
| cart_id | BIGINT | FK |
| product_id | BIGINT | FK |
| quantity | INT | 数量 |
| created_at | DATETIME | 作成日時 |
| updated_at | DATETIME | 更新日時 |

---

### orders
| カラム名 | 型 | 説明 |
|----------|----|------|
| id | BIGINT | PK |
| user_id | BIGINT | FK |
| order_date | DATETIME | 注文日時 |
| status | VARCHAR | 注文状態 |
| total_amount | DECIMAL | 合計金額 |
| created_at | DATETIME | 作成日時 |
| updated_at | DATETIME | 更新日時 |

---

### order_items
| カラム名 | 型 | 説明 |
|----------|----|------|
| id | BIGINT | PK |
| order_id | BIGINT | FK |
| product_id | BIGINT | FK |
| quantity | INT | 数量 |
| unit_price | DECIMAL | 注文時単価 |
| created_at | DATETIME | 作成日時 |
| updated_at | DATETIME | 更新日時 |

---
## ER図
```txt
users
│
├── carts
│    │
│    └── cart_items ── products
│
└── orders
     │
     └── order_details ── products
```
---


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
