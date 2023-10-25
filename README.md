# QRcode で情報共有

[実際に開発で使用したリポジトリ AndroidQR_java](https://github.com/Laplacekmk/AndroidQR_java)

[アプリ紹介記事](https://zenn.dev/rakuda_jp/articles/5c6d626134f31d)

gcp アカウントの請求方法を消去しているため、実行自体はできますが、ログイン画面から動きません。
ご容赦お願い申し上げます。

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
