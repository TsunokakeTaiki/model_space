# テーブル設計

## Users テーブル

| Column             | Type    | Options     |
| ------------------ | ------- | ----------- |
| nickname           | string  | null: false |
| email              | string  | null: false |
| encrypted_password | string  | null: false |
| prefecture_id      | integer | null: false |
| city               | string  |             |
| admin_id           | integer | null: false |

### Association

- has_many :shops
- has_many :comments

## Shops テーブル

| Column            | Type       | Options                        |
| ----------------- | ---------- | ------------------------------ |
| name              | string     | null: false                    |
| prefecture_id     | integer    | null: false                    |
| city              | string     |                                |
| info              | text       |                                |
| tool_rental_id    | integer    | null: false                    |
| painting_booth_id | integer    | null: false                    |
| kit_storage_id    | integer    | null: false                    |
| user              | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- has_many :comments

## Comments テーブル

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| text    | text       | null: false                    |
| user_id | references | null: false, foreign_key: true |
| shop_id | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :shop
