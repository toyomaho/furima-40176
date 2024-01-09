# README
# テーブル設計
null: false	カラムが空の状態では保存できない
unique: true	一意性のみ許可（同じ値は保存できない）
foreign_key: true	外部キーを設定（別テーブルのカラムを参照する）

## usersテーブル

| Column             | Type   | Options                   |
| ------------------ | ------ | ------------------------- |
| email              | string | null: false, unique: true |
| password           | string | null: false               |
| encrypted_password | string | null: false               |
| nickname           | string | null: false               |
| last-name          | string | null: false               |
| first-name         | string | null: false               |
| last-name-kana     | string | null: false               |
| first-name-kana    | string | null: false               |
| birth-date         | string | null: false               |

### Association
- has_many :items
- has_many :orders



## itemテーブル

| Column                   | Type       | Options                        |
| ------------------------ | ---------- | ------------------------------ |
| item-name                | string     | null: false                    |
| item-text                | text       | null: false                    |
| item-img                 | url        | null: false                    |
| item-category            | string     | null: false                    |
| item-sales-status        | string     | null: false                    |
| item-shipping-fee-status | string     | null: false                    |
| item-prefecture          | string     | null: false                    |
| item-scheduled-delivery  | string     | null: false                    |
| item-price               | string     | null: false                    |
| user_id                  | references | null: false, foreign_key: true |

### Association
- belongs_to :user
- has_one :order



## orderテーブル

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| item               | references | null: false, foreign_key: true |
| user               | references | null: false, foreign_key: true |

### Association
- belongs_to :item
- belongs_to :users



## shipping-addressテーブル

| Column       | Type       | Options                        |
| ------------ | ---------- | ------------------------------ |
| postal-code  | string     | null: false                    |
| prefecture   | string     | null: false                    |
| city         | string     | null: false                    |
| addresses    | string     | null: false                    |
| building     | string     |                                |
| phone-number | string     | null: false                    |
| order        | references | null: false, foreign_key: true |

### Association
- belongs_to :order