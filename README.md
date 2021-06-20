# README

# テーブル設計

## users テーブル

| Column             | Type     | Options                  |
| ------------------ | -------- | -------------------      |
| nickname           | string   | null: false              |
| email              | string   | null: false,unique: true |
| encrypted_password | string   | null: false              |
| family_name        | string   | null: false              |
| family_name_kana   | string   | null: false              |
| first_name         | string   | null: false              |
| first_name_kana    | string   | null: false              |
| birth_day          | date     | null: false              |


### Association

- has_many :comment
- has_many :items
- has_many :seller_items,buyers


## items テーブル

| Column             | Type      | Options     |
| ------------------ | --------- | ----------- |
| name               | string    | null: false |
| introduction       | text      | null: false |
| category_id        | integer   | null: false |
| item_condition_id  | integer   | null: false |
| delivery_charge_id | integer   | null: false |
| shipment_source_id | integer   | null: false |
| preparation_day_id | integer   | null: false |
| price              | integer   | null: false |
| user               |references | null: false, foreign_key: true |

### Association

- belong_to :user
- has_many  :comments
- has_one   :seller_item,buyer


## comments テーブル

| Column      | Type       | Options                        |
| ----------- | ---------- | ------------------------------ |
| text        | text       | null: false                    |
| item        | references | null: false, foreign_key: true |

### Association

- belong_to :item


## seller_items,buyers テーブル

| Column      | Type       | Options                        |
| ----------- | ---------- | ------------------------------ |
| item        | references | null: false, foreign_key: true |
| user        | references | null: false, foreign_key: true |

 ### Association

- belong_to :item
- belong_to :user
- has_one : shipping_address


## shipping_addresses

| Column            | Type       | Options     |
| ----------------- | ---------- | ----------- |
| postal_code       | string     | null: false |
| prefecture        | integer    | null: false |
| municipality      | string     | null: false |
| address           | string     | null: false |
| building_name     | string     |
| phone_number      | string     | null: false |
| seller_item,buyer | references | null: false, foreign_key: true |


### Association

- belong_to :seller_item,buyer
