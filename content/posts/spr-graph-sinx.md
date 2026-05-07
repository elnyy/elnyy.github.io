---
title: "(スプレッドシート)y=sinxのグラフを作成する"
description: "スプレッドシートでsinxのグラフを作成する"
date: "2026-05-07T12:25:58Z"
toc: true
thumbnail: ""
categories:
  - "TOOL"
tags:
  - "スプレッドシート"
---
<!--more-->
スプレッドシートでy=sinxのグラフを作成していきます。

x軸の範囲は、度数法で、1<=x>=360とします。

## y軸x軸のデータを用意
まずは、列Aにx軸のデータを入れることにします。
`=ROW()`をA1に記述して、A360の行までコピーします。
![](/images/spr-5-0.png)

次にy軸のデータを列Bに入力します。

B1に次の式を入力し、B360までコピーします。
```
=sin(radians(row()))
```
* sin() ... ラジアンで指定した角度のsinを返す
* radians() ... 角度の値を度数からラジアンに変換する
* row() ... 指定したセルの行番号を返す。引数を空にすると、現在の行番号を返す。
![](/images/spr-5-1.png)

データが用意できたら次はいよいよグラフの挿入です。

## グラフを挿入する
「挿入」=>「グラフ」を選択します。
グラフの種類は「平滑線(へいかつせん)」です。
![](/images/spr-5-2.png)

グラフの「データ範囲」を指定します。先ほどy軸のデータとして入力した、b1:b360を指定します。
![](/images/spr-5-3.png)

これでy=sinx特有のきれいな正弦波が完成です。
![](/images/spr-5-6.png)

しかし、x軸が見れないのは少々不便ですね。x軸を追加しましょう。

### x軸も追加しよう
「グラフディタ」の「設定」から、「X軸を追加」を押下し、データ範囲を選択します。言わずもがなですが、A1:A360を指定します。
![](/images/spr-5-4.png)

すると、このようにx軸が表示されました。
![](/images/spr-5-5.png)

---

以下は完成したグラフの埋め込みです。
グラフの上をなぞると、x,yの値が表示されます。
<iframe width="600" height="371" seamless frameborder="0" scrolling="no" src="https://docs.google.com/spreadsheets/d/e/2PACX-1vT1kNtea8FIVA7vJCQc2JnZ-ITmu_JrOAj4F8f2VwmIJ-O_vd2x0wSKdSdsiHCWdpmhEpJKdWgXKbTF/pubchart?oid=1088953947&amp;format=interactive"></iframe>

また、SVGもダウンロードしてみました。
![](/images/spr-chart-sinx.svg)

## 所感
今回作成したy=sinxをもっとカスタマイズしてみたり、違い種類のグラフ作図もやっていきたい。

てか、なにげに初めて知ったんですがグラフのエクスポート色々できていいですね。

上に置いていおいた埋め込みやSVGの他にもPNG,PDFもいけます。

楽に色々エクスポートできるのはめっちゃ好きです。
