# furima-app

## users テーブル (ユーザー情報)

| Column             | Type   | Options                   |
| ------------------ | ------ | ------------------------- |
| email              | string | null: false, unique: true |
| encrypted_password | string | null: false               |
| first_name         | string | null: false               |
| last_name          | string | null: false               |
| first_name_kana    | string | null: false               |
| last_name_kana     | string | null: false               |
| birth              | date   | null: false               |
| nickname           | string | null: false               |

### Association

-has_many :purchases
-has_many :items

## purchases テーブル (購入記録)

| Column     | Type       | Options                        |
| ---------- | ---------- | ------------------------------ |
| user       | references | null: false, foreign_key: true |
| item       | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :item
- has_one :order

##  itemsテーブル (商品情報)

| Column     | Type       | Options                           |
| ---------- | ---------- | --------------------------------- |
| item_name  | text       | null: false                       |
| item_info  | text       | null: false                       |
| category   | string     | null: false                       |
| sales      | string     | null: false                       |
| shipping   | string     | null: false                       |
| prefecture | string     | null: false                       |
| scheduled  | string     | null: false                       |
| price      | Integer    | null: false                       |
| user       | references | null: false, foreign_key: true    |

### Association

- belongs_to :user
- has_one :purchase

## orders テーブル (発送先情報)

| Column         | Type       | Options                        |
| -------------- | ---------- | ------------------------------ |
| postal_code    | string     | null: false                    |
| prefecture     | string     | null: false                    |
| city           | string     | null: false                    |
| addresses      | string     | null: false                    |
| building       | string     |                                |
| phone_number   | Integer    | null: false                    |
| purchase       | references | null: false, foreign_key: true |

### Association

- belongs_to :purchase
