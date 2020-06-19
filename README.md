# README

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|username|string|null: false|
|email|string|null: false, unique: true|
|password|string|null: false|

### Association
- has_many :messages
- has_many :groups, through: :groups_users
- has_many :groups_users

## messagesテーブル
|column|Type|options|
|------|----|-------|
|body|text|null: false|
|image|string||
|group|references|foreign_key: true|
|user|references|foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group

## groupsテーブル
|column|Type|options|
|------|----|-------|
|name|string|null: false, unique: true|

### Association
- has_many :user, through: :groups_users
- has_many :messages
- has many :groups_users

## groups_usersテーブル
|column|Type|options|
|------|----|-------|
|user|references|null: false, foreign_key: true|
|group|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user