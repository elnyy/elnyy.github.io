---
title: "(Linux)ntpdateで時刻を同期する(init)"
description: "Linut,特にinitシステムで時刻を同期する方法のメモです"
date: "2026-06-19T13:36:00Z"
thumbnail: ""
categories:
  - "Linux"
tags:
  - "ntp"
---
<!--more-->
## 環境
```
$ cat /etc/issue
Devuan GNU/Linux excalibur \n \l
```

linuxで時刻同期です。

私はinit使いなので、よくみんなが使っている(?)systemdで使える同期コマンドは使えません。(timedatectlとか?)

ということで、

## <u>`ntpdate`を使って時刻同期をします</u>

manを少し覗いてみると、色々なオプションがあって使い方が複雑そうですね。
```
SYNOPSIS
       ntpdate  [-46bBdqsuv]  [-a  key]  [-k keyfile] [-o version] [-t
       timeout] server [...]
```
ですが、今回は時刻同期をしたいだけなのでオプションは特に必要ないです。

引数にある`server`として、NTPサーバーを指定すればいいだけです。
NTPサーバーはJSTならntp.nict.jpを使えばいいと思います。

実行例
```
$ sudo ntpdate ntp.nict.jp
```
システム時刻設定には管理者権限が必要なことをお忘れなく。

もしうまくいかない場合、時刻が一日以上ずれているなら、`date -s`で年月日だけでも先に設定しておきましょう。
```
$ sudo date -s "20260619" # yyyy/mm/dd
```

日付に大きなズレがあるとNTPの同期がうまくいかないことがあるかもしれないからです。



以上

## 参考
* https://jjy.nict.go.jp/tsp/PubNtp/
    * NTPサーバーが掲載されている
* `man ntpdate`

## 小言
実験で、`date -s`を使ってわざと時刻をずらして`ntpdate ntp.nict.jp`で同期する
というのを何度か試していたんですが、なぜか失敗するときがありました。これに関してはなぜななのか検討
がつかない。。。
ちなみに、失敗するときのエラーメッセージは`ntpdig: no eligible servers`。

今ふと思ったんだけど、NTPサーバーに頻繁に接続しすぎて拒否られているだけなのかも...!

２回連続で成功することはなくて、１回成功したあと何度か失敗し、また１回成功、、、という感じだったし。それがげ原因かも。
