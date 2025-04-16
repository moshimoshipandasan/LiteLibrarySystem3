# 図書館管理システム（LiteLibrarySystem3）

このシステムは、図書館の貸出・返却業務を効率化するためのシンプルなウェブアプリケーションです。Google Apps Script（GAS）を使用して実装されており、バーコードスキャン機能を備えています。

## 参照情報

- **スプレッドシートテンプレート**: [サンプルスプレッドシート](https://docs.google.com/spreadsheets/d/1YBsLeKQln_PxwqQyJpEal87O3nC5Vg29_kRWYYabtr0/copy)
- **参考システム**: [システム紹介ページ](https://sites.google.com/view/ueno999/top)

## サポート

本システムの利用にあたり、技術的なサポートが必要な場合は、YouTubeチャンネル[GIGAch](https://www.youtube.com/@gigach)の有料メンバーに登録することでサポートを受けることができます。

## システム概要

本システムは以下の4つの主要機能を提供します：

1. **図書貸出**：利用者IDと書籍IDを入力して貸出処理を行います
2. **利用者別返却**：利用者IDを入力して、その利用者の未返却本を一覧表示し返却処理を行います
3. **貸出書籍検索**：書籍IDを入力して、その書籍の貸出状況を確認します
4. **図書返却**：書籍IDを入力して返却処理を行います

各機能はURLパラメータ `?page=` で切り替えることができます。

## 各機能の詳細

### 1. 図書貸出（?page=なし）

メインの貸出画面です。利用者IDと書籍IDを入力して貸出処理を行います。

**特徴：**
- 利用者IDをスキャンすると、自動的に利用者情報を取得して表示します
- 利用者情報確定後、書籍IDを連続スキャンすることで複数冊の貸出が可能です
- スキャンした書籍のタイトルがリアルタイムで表示されます
- 「貸出登録」ボタンで一括して貸出処理を行います

**使用方法：**
1. 「利用者IDをスキャン」ボタンをクリックしてカメラを起動し、利用者IDをスキャンします（または手入力）
2. 利用者情報が表示されたら、「書籍IDをスキャン」ボタンをクリックしてカメラを起動し、書籍IDをスキャンします
3. 複数冊貸し出す場合は、続けて書籍IDをスキャンします
4. すべての書籍をスキャンしたら、「貸出登録」ボタンをクリックして処理を完了します

### 2. 利用者別返却（?page=user_returns）

特定の利用者が借りている本をまとめて返却するための画面です。

**特徴：**
- 利用者IDをスキャンすると、その利用者の未返却本が一覧表示されます
- チェックボックスで返却する本を選択できます
- 「全選択」チェックボックスで一括選択も可能です
- 「選択した本をまとめて返却」ボタンで選択した本だけを返却処理します

**使用方法：**
1. 「利用者IDをスキャン」ボタンをクリックしてカメラを起動し、利用者IDをスキャンします（または手入力）
2. 表示された未返却一覧から、返却する本のチェックボックスをオンにします
3. 「選択した本をまとめて返却」ボタンをクリックして返却処理を完了します

### 3. 貸出書籍検索（?page=finder）

書籍IDから貸出状況を検索する画面です。

**特徴：**
- 書籍IDをスキャンすると、その書籍の貸出履歴が表示されます
- 現在の貸出状況（貸出中か返却済みか）が色分け表示されます
  - 返却済：緑色
  - 未返却：赤色
- 利用者名とIDも表示されます

**使用方法：**
1. 「書籍IDをスキャン」ボタンをクリックしてカメラを起動し、書籍IDをスキャンします（または手入力）
2. 「検索」ボタンをクリックすると、その書籍の貸出履歴が表示されます

### 4. 図書返却（?page=return）

書籍IDを入力して返却処理を行う画面です。複数冊をまとめて返却できます。

**特徴：**
- 書籍IDをスキャンすると、書籍情報を取得して表示します
- 連続スキャンで複数冊の返却処理が可能です
- チェックボックスで返却する本を選択できます
- 「全選択」チェックボックスで一括選択も可能です
- 「選択した本をまとめて返却」ボタンで選択した本だけを返却処理します

**使用方法：**
1. 「書籍IDをスキャン」ボタンをクリックしてカメラを起動し、書籍IDをスキャンします（または手入力）
2. 複数冊返却する場合は、続けて書籍IDをスキャンします
3. 返却する本のチェックボックスをオンにします
4. 「選択した本をまとめて返却」ボタンをクリックして返却処理を完了します

## 共通機能

### バーコードスキャン

すべての画面で、IDの入力にバーコードスキャン機能を使用できます。

**特徴：**
- スマートフォンやタブレットのカメラを使用してバーコードを読み取ります
- スキャン成功時にはビープ音が鳴ります
- 連続スキャンにも対応しています

### レスポンシブデザイン

すべての画面がスマートフォンやタブレットでの操作に最適化されています。

**特徴：**
- 大きなボタンと入力フィールドで操作しやすい設計
- テーブル表示はスマートフォンでもカード形式で見やすく表示
- フォントサイズも十分に大きく設定

## 技術情報

- **フロントエンド**: HTML, CSS, JavaScript
- **バックエンド**: Google Apps Script (GAS)
- **データストレージ**: Google スプレッドシート
- **バーコードスキャン**: QuaggaJS ライブラリ

## 開発者情報

Noboru Ando @ Aoyama Gakuin University

## ライセンス

MIT License

Copyright (c) 2025 Noboru Ando @ Aoyama Gakuin University

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
