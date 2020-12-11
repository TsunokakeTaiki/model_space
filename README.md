# アプリケーション名	
モデルスペース


# アプリケーション概要
プラモデルやガレージキットといった模型やフィギュアが好きなユーザーが、知っている制作スペースを投稿し宣伝・シェアできるウェブサイト


# URL	
デプロイ次第記述


# テスト用アカウント	

## 権限者アカウント
mail：デプロイ次第記述
password：デプロイ次第記述

## 一般アカウント
mail：デプロイ次第記述
password：デプロイ次第記述

## Basic認証
ID：デプロイ次第記述
Pass：デプロイ次第記述


# 利用方法	
このアプリケーションの利用方法を説明しましょう。


# 目指した課題解決	
プラモデルに興味があるが何から始めたらわからない人が、近くに詳しい店舗があるかを見つけやすくできる。
一時的な引越し、出張などによって制作環境が用意できていないモデラーが近くに制作スペースがあるか確認しやすくできる。
オフ会やイベントなどの知らない出先で、破損してしまったが直す術がないときに近くに制作スペースがあるか確認しやすくできる


# 洗い出した要件	
スプレッドシートにまとめた要件定義を、マークダウンで記述しなおしましょう。


# 実装した機能についての特徴とGIF
デプロイ次第記述


# データベース設計	

## Users テーブル

| Column             | Type    | Options     |
| ------------------ | ------- | ----------- |
| nickname           | string  | null: false |
| email              | string  | null: false |
| encrypted_password | string  | null: false |
| prefecture_id      | integer | null: false |
| city               | string  |             |
| admin_id           | integer |             |

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
