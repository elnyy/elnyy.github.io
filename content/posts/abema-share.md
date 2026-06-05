---
title: "アベマTVの動画をDiscordで画面共有する(chrome)"
description: "アベマTVをDiscordで画面共有する方法です。"
date: "2026-06-05T15:59:35Z"
thumbnail: "/images/chrome1.jpg"
categories:
  - "HOWTO"
  - "Browser"
tags:
  - "Discord"
  - "Chrome"
---
<!--more-->

アベマTVの動画をDiscordで画面共有しようとすると、共有画面では動画再生が停止されてしまいす。
これは恐らく、DRM（Digital Rights Management）制御と呼ばれる、デジタルコンテンツの権利を守るための仕組みのためだと思われます。

DRM制御について詳しくはここを見るといいかもしれない

https://business.adobe.com/jp/blog/basics/digital-rights-management

方法を紹介する前に、私が実証したOS/ブラウザを書いておきます。
* OS
    * Windows11
* Browser
    * Google Chrome 149

(他環境であってもほぼほぼいけるだろうけど)

では、その方法を紹介見ていきます。とはいっても、設定項目を１つ変えるだけ。

<u>Chromeを開いて、「システム」から「GPUアクセラレーション」をOFFにする。</u>

![](/images/chrome1.jpg)

再起動をすれば、設定が反映され無事に画面共有ができるようになっているはず。

他のブラウザ(firefoxなど)でも同じようにいけるんじゃないかな～。設定自体簡単に変えられるので試せる人は試してみてください。

１つ注意点としては、GPUを積んでいるPCの人はパフォーマンス的にはGPUアクセラレーションはONのほうがいいです。もし、この設定をOFFにしてパフォーマンスに問題が発生したらONに戻しましょう。GPUない人やパフォーマンス気にしない人には関係ないです。
