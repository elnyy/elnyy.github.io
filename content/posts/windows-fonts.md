---
title: "(Windows)フォントを変える"
description: "フォントを変えてみよう、そしてその方法を少しメモ"
date: "2026-06-14T01:18:11Z"
thumbnail: ""
categories:
  - "HOWTO"
tags:
  - "Windows"
---
<!--more-->
今日はWindows11でフォントを変えてみようと思います。
今回導入するフォントは[DotGothic16](https://fonts.google.com/specimen/DotGothic16)です。
DotGothic16は16x16のビットマップフォントで、古いビデオゲームを彷彿とさせるピクセルフォントです。

まずは、フォントファイルをゲットしたいので配布ページにアクセスし「Download all」をクリックしてダウンロード。
![](/images/dotgothic16-1.png)
「DotGothic16,Noto_Sans_JP.zip」という名前のZipファイルがダウンロードされたので、展開してみます。
![](/images/dotgothic16-2.png)
すると、２つのフォルダ「DotGothic16」「Noto_Sans_JP」が出てきました。
![](/images/dotgothic16-3.png)
名前からして使うのは「DotGothic16」かな。このフォルダの上には「DotGothic16-Regular.ttf」がありました。これがフォントファイルの本体です。

今度は、Windowsの設定を開き、「個人用設定」>「フォント」に進みます。
![](/images/dotgothic16-4.png)

「フォントを参照しインストールする」ボタンから先程のフォントファイル(.tff)を選択しました。
使用可能なフォントのリストを見るとちゃんと表示されていたので無事インストールできたようです。

...


...

あれ、インストールはできたようだけどWindowsのデフォルトフォントはどこで変えられるの？

設定を色々見ても見つからず、調べてみると...
![](/images/dotgothic16-5.png)
レジストリの書き換えが必要だということです。
無料ソフトを使えば安全に書き換えられるといのもあったんですがそこまでしなくていいかな..

気になる方はこちらが参考になるかもしれません。

https://tenshoku.mynavi.jp/engineer/guide/articles/ZGXbwxEAACgAC-r4


## おまけ
Windows全体のフォントを変えられなくても、せめてブラウザのフォントを変えてみます。
Chromeでは、「設定」>「デザイン」>「フォントをカスタマイズ」から標準フォントをDotGothic16に変更できました。
![](/images/dotgothic16-6.png)
試しに当サイトを開いてみると無事にフォントが反映されていることが分かります。
![](/images/dotgothic16-7.png)

補足として、設定したフォントでレンダリングしてくれないサイトがあります。
それらのサイトでは、
1. サードパーティーフォントを使うよう指定している
2. デバイス内の他のフォントが使うよう指定している

可能性が高いです。
話が長くなるので、ここで触れるのは避けますがまた別の機会に書ければと思います。

## 所感
対応できていないサイトも多いとはいえ、ウェブサイトをピクセルフォントで閲覧できるのは新鮮です。

たまにフォントを変えてみると気分転換になっていいですよ。

ちなみに、蛇足ですがピクセルといえば最近この歌をよく聞いています。

<iframe width="312" height="176" src="https://ext.nicovideo.jp/thumb/sm45865042" scrolling="no" style="border:solid 1px #ccc;" frameborder="0"><a href="https://www.nicovideo.jp/watch/sm45865042">ryo (supercell) / メルト CPK! Remix (初音ミク ver.)</a></iframe>
