# QRcode で情報共有

実際に開発で使用したリポジトリ -> [AndroidQR_java](https://github.com/Laplacekmk/AndroidQR_java)

プロジェクトの clone から実行までの流れは [実行手順](#exec) 参照。
ただ、gcp アカウントの請求方法を消去しているため、実行自体はできますが、ログイン画面から動きません。
ご容赦お願い申し上げます。

## 概要

### アプリ名

I・AM

### 使用言語

Android Java
c/c++
Google Apps Script

### 制作期間

4 ヶ月

## アプリ機能

相手の qrcode を読み取るか、 相手に読み取らせることでお互いの簡単な情報を交換できる。
読み取ったデータはデータベースへ保存され、 今まで交換してきた履歴が確認可能。

### Account 作成

Google account と LINE account のどちらかで作成する。

### Database

データベース作成は、 Google cloud sql for mysql を使用している。  
データベースとのやり取りは Google apps script (通称ギャス (gas)) を経由して行う。  
Gas で公開した webapi に対して post メソッドでリクエストを送り、  
リクエストに応じたクエリを gas が実行するという流れになっている。  

[Gas のコード](https://script.google.com/u/2/home/projects/1LiNjqAxbamMH6iaDeKBmMRstNkucSHI57KVhgS-7nSYwctJwuADSnmWX/edit)

### Qrcode 関係

Qrcode の作成には ZXing を使用。  
Qrcode の読み取りは openCV の画像処理を使用。

## 作った経緯

当時、 新型コロナウィルスの影響により隔週でリモート授業を行っていたため、クラスメイトとの交流が減り、 仲を深めることが難しい状況となっていた。 
この状況をふまえ、 「 **最速** でお互いについて知ることのできるアプリを作ろう」という意見が上がり、 制作を開始した。

## こだわり

- SNS アカウントによるログイン  
  こういったソーシャルログインを使用すると、
  SNS の多要素認証を利用できるので、セキュリティの向上につながる。
  また、Id やパスワードを保管する必要がなくユーザー情報の管理が容易になるという利点がある。
- QRcode を利用  
  近年 QRcode の利用が活発になってきているため、 学習の一環として QRcode を利用。
  作った経緯にもあるように、 最速での情報共有を目指していたため、 そこを実現するために
  QRcode を取り入れた。

<a id="exec"></a>

## 実行手順

前準備 [実行用ファイル保存場所](https://drive.google.com/drive/folders/1jj0yzLCwEM36_dOyABLbM79VjNNtr3T7?usp=sharing) にて OpenCV をダウンロード

1. android studio にて clone
2. ダウンロードした OpenCV を展開
3. new -> import modules にて 展開した フォルダを指定したのち、
   名前が :OpenCV であることを確認して ok
4. build.gradle(:app) の 59 行目 `implementation project(path: ':OpenCV')` のコメントアウトを外す
5. sync project
6. build project
7. 実行してログイン画面が出れば終了
