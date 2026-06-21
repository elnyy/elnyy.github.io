---
title: "LinuxにNvidiaのドライバーを導入(GTX1050ti)"
description: ""
date: "2026-06-21T13:05:06Z"
thumbnail: ""
categories:
  - "Linux"
  - "HOWTO"
tags:
  - "nvidia"
---
<!--more-->
## 環境
```
$ cat /etc/issue
Devuan GNU/Linux excalibur \n \l
```

## おおまかな手順
1. sources.listを編集
2. nvidia-detectをインストール
3. ドライバをインストール

順を追って説明していきます。
## 1. sources.listを編集
/etc/apt/sources.listを編集します。nvidia関連のソフトをゲットするには`non-free non-free-firmware contrib`を末尾につければいいらしい。(つけたら動いた)
```
# /etc/apt/sources.listに、元の`excalibur`の行を削除して、この行を追記します。
$ head -n1
deb http://jp.deb.devuan.org/merged excalibur          main non-free non-free-firmware contrib
```

## 2. nvidia-detectをインストール
nvidia-detectってなんだっけ？
```
$ nvidia-detect --help
Usage: nvidia-detect [PCIID]...
       Reports the Debian packages supporting the NVIDIA GPU that is
       installed on the local system (or given as a PCIID parameter).
```
超簡単にいうと、使っているGPUに合わせてドライバの
パッケージ名を出してくれるソフトです。

アップデート&インストールしましょう
```
$ sudo apt update && sudo apt install nvidia-detect
```
私の環境で実行してみると...
```
$ nvidia-detect
Detected NVIDIA GPUs:
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP107 [GeForce GTX 1050 Ti] [10de:1c82] (rev a1)

Checking card:  NVIDIA Corporation GP107 [GeForce GTX 1050 Ti] (rev a1)
Your card is supported by all driver versions.
Your card is also supported by the Tesla 535 drivers series.
It is recommended to install the
    nvidia-driver
package.

```

使っているGPU名(1050ti)と、`nvidia-driver`というドライバのインストール
を推奨してくれました。

ここで推奨されたドライバをインストールします。

## 3. ドライバをインストール
`nvidia-detect`で推奨されたドライバを`apt`でインストールします。

推奨されたドライバはGPUによって各々異なっていると思いますが、`nvidia-driver`の部分はそれに応じて変更してください。
```
$ sudo apt install nvidia-driver
```

以上 ドライバ導入完了です。

---

インストール中はダイアログが出るかもなので時折進捗を見ておくといいでしょう。あとは再起動することをお忘れなく。


最後にはちゃんとインストールできているか確認しようね

もしnouveau(ぬーぼー)がまだあったらblacklistに入れよう。
