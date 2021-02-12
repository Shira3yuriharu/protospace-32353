# テーブル設計

## users テーブル

| Column    | Type   | Options     |
| --------  | ------ | ----------- |
| email     | string | NOT NULL    |
| password  | string | NOT NULL    |
| name      | string | NOT NULL    |
| profile   | text   | NOT NULL    |
| occupation| text   | NOT NULL    |
| position  | text   | NOT NULL    |

### Association

- has_many :comments
- has_many :prototypes, through: comments

## prototypes テーブル

| Column    | Type      | Options     |
| ------    | ------    | ----------- |
| title     | string    | NOT NULL    |
| catch_copy| text      | NOT NULL    |
| user      | references|             |
#### *imageはActiveStorageで実装

### Association

- has_many :comments
- belongs_to :users, through: comments

## comments テーブル

| Column      | Type       | Options  |
| ------      | ---------- | -------- |
| text        | text       | NOT NULL |
| user        | references |          |
| prototype   | references |          |

### Association

- belongs_to :users
- belongs_to :prototypes
