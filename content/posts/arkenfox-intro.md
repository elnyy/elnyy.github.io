---
title: "(widows) FirefoxでArkenfoxのuser.jsを設定"
date: 2026-04-27T14:38:38Z
categories: ["Windows", "firefox"]
---
<!--more-->
## arkenfox user.jsとは
firefoxの設定をできる限りプライバシー重視に設定したい人向けのuser.jsである。

ソースコードは以下のURLから確認できる。
https://github.com/arkenfox/user.js/

## 導入方法
普通にuser.jsを設定する方法と同じように可能。

1. まず、URLバーから`about:profiles`にアクセスする。

2. 現在使用中のプロファイルを見つけたら、Local Directoryではなく、<u>Root Directory</u>の方のフォルダを開く。
![](/images/aboutprofiles.jpg)

3. 開いたフォルダ内で、`user.js`という名前でファイルを作る。

4. 以下のarkenfoxの`user.js`をコピーし、作成した`user.js`に貼り付ける。

https://raw.githubusercontent.com/arkenfox/user.js/refs/heads/master/user.js

5. firefoxの全てのタブを終了し、再度起動することで設定が反映されるはず。

## 設定が反映されない時は

* プロファイルは間違っていないか
    * about:profileを再度確認してみる
* ファイル名が`user.js`となっているか
    * 一語一句違ってはいけない
* 再起動できていない
    * Windows自体を再起動してみる


---

初期の設定だと、自分は使っていないアカウントメニューだとかが表示されていて鬱陶しいんですよ。
これをすれば見た目がスッキリするのでいいですね。

あと、極端にウェブサイトが機能しなくなるってこともありませんし。
