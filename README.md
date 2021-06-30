# furima-app

## users テーブル (ユーザー情報)

| Column             | Type   | Options                |
| ------------------ | ------ | ---------------------- |
| email              | string | not null, unique: true |
| encrypted_password | string | not null               |
| first_name         | string | not null               |
| last_name          | string | not null               |
| first_name_kana    | string | not null               |
| last_name_kana     | string | not null               |
| birth              | string | not null               |
| nickname           | string | not null, unique: true |

### Association

-has_many :purchases
-has_many :items

## purchases テーブル (購入記録)

| Column     | Type       | Options                        |
| ---------- | ---------- | ------------------------------ |
| user_id    | references | null: false, foreign_key: true |
| item_id    | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :item
- has_one :residence

##  itemsテーブル (商品情報)

| Column     | Type       | Options                           |
| ---------- | ---------- | --------------------------------- |
| image      |            |                                   |
| item_name  | text       | not null                          |
| item_info  | text       | not null                          |
| category   | string     | not null                          |
| sales      | string     | not null                          |
| shipping   | string     | not null                          |
| prefecture | string     | not null                          |
| scheduled  | string     | not null                          |
| price      | Integer    | not null                          |
| user_id    | references | null: false, foreign_key: true    |

### Association

- belongs_to :user
- has_one :purchase

## orders テーブル (発送先情報)

| Column         | Type       | Options                        |
| -------------- | ---------- | ------------------------------ |
| card_number    | string     | not null                       |
| card_exp-month | string     | not null                       |
| card_exp-year  | string     | not null                       |
| card_cvc       | string     | not null                       |
| postal_code    | string     | not null                       |
| prefecture     | string     | not null                       |
| city           | string     | not null                       |
| addresses      | string     | not null                       |
| building       | string     |                                |
| phone_number   | Integer    | not null                       |
| user_id        | references | null: false, foreign_key: true |
| item_id        | references | null: false, foreign_key: true |

### Association

- belongs_to :residence
