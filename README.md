# README

# テーブル設計

## users テーブル

| Column           | Type   | Options     |
| ---------------- | ------ | ----------- |
| nickname         | string | null: false |
| email            | string | null: false |
| password         | string | null: false |
| family_name      | string | null: false |
| family_name_kana | string | null: false |
| first_name       | string | null: false |
| first_name_kana  | string | null: false |
| birth_day        | date   | null: false |
| birth_month      | date   | null: false |
| birth_year       | date   | null: false |

### Association

- has_many :comment
- has_many :item
- has_many :seller_item
- has_one  :buyer


## items テーブル

| Column          | Type      | Options     |
| --------------- | --------- | ----------- |
| name            | string    | null: false |
| introduction    | text      | null: false |
| category        | integer   | null: false |
| item_condition  | integer   | null: false |
| delivery_charge | integer   | null: false |
| shipment_source | integer   | null: false |
| preparation_day | integer   | null: false |
| price           | integer   | null: false |
| user            |references | null: false, foreign_key: true |

### Association

- belong_to :user
- has_many  :comment
- has_one   :seller_item


## comments テーブル

| Column      | Type       | Options                        |
| ----------- | ---------- | ------------------------------ |
| text        | text       | null: false                    |
| item        | references | null: false, foreign_key: true |

### Association

- belong_to :item


## seller_items テーブル

| Column      | Type       | Options                        |
| ----------- | ---------- | ------------------------------ |
| item        | references | null: false, foreign_key: true |

 ### Association

- belong_to :item
- has_one :buyer


## buyers テーブル

| Column      | Type       | Options                        |
| ----------- | ---------- | ------------------------------ |
| seller_item | references | null: false, foreign_key: true |
| user        | references | null: false, foreign_key: true |

### Association

- belong_to :seller_item
- belong_to :user
- has_one   :credit_card


## credit_cards テーブル

| Column           | Type       | Options     |
| ---------------- | ---------- | ----------- |
| card_number      | integer    | null: false |
| expiration_month | date       | null: false |
| expiration_year  | date       | null: false |
| security_code    | integer    | null: false |

### Association

- belong_to :buyer


## shipping_addresses

| Column           | Type       | Options     |
| ---------------- | ---------- | ----------- |
| postal_code      | integer    | null: false |
| prefecture       | integer    | null: false |
| municipality     | integer    | null: false |
| address          | integer    | null: false |
| building_name    | integer    |
| phone_number     | integer    | null: false |
