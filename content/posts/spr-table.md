---
title: "(スプレッドシート)表をHTMLのtableに変換してくれるサイト"
description: ""
date: "2026-05-12T14:30:28Z"
thumbnail: ""
categories:
  - "tool"
tags:
  - "スプレッドシート"
---
<!--more-->
スプレッドシートで作った表を簡単にHTMLのテーブルに変換してくれるサイトです。

https://codeshack.io/excel-to-html-table-converter/

手順としては、
1. スプレッドシートで表を作成する
2. エクセルファイルとしてダウンロードする
3. サイトにエクセルファイルを読み込んで変換する


実践してみます。まずは、tableに変換したい表をスプレッドシートで作成します。
![](/images/spr-6-1.png)

「ファイル」=>「ダウンロード」=>「Microsoft Excel (.xlsx)」からエクセルファイルとしてダウンロードします。
![](/images/spr-6-2.png)

上記サイトにアクセスし、下記画像の点線部分をクリックしてダウンロードしたエクセルファイルをアップロードします。
![](/images/spr-6-3.png)

一瞬で「Generated HTML Table」の欄に、HTMLのテーブルが出力されました。
![](/images/spr-6-4.png)

また、下の方にスクロースすると画像のようなオプションがあります。
![](/images/spr-6-5.png)
必要に応じてシートを変更したり、ヘッダーのON/OFFを切り替えたりできます。

---

以下が実際にスプレッドシートを変換して作ったテーブルです。
<table>
  <thead>
    <tr>
      <th>国</th>
      <th>昼間のあいさつ</th>
      <th>お礼の言葉</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>日本</td>
      <td>こんにちは</td>
      <td>ありがとう</td>
    </tr>
    <tr>
      <td>韓国</td>
      <td>アンニョンハセヨ</td>
      <td>カムサハムニダ</td>
    </tr>
    <tr>
      <td>中国</td>
      <td>ニーハオ</td>
      <td>シィエシィエ</td>
    </tr>
    <tr>
      <td>アメリカ</td>
      <td>ハロー</td>
      <td>サンキュー</td>
    </tr>
    <tr>
      <td>ドイツ</td>
      <td>グーテン・ターク</td>
      <td>ダンケ</td>
    </tr>
    <tr>
      <td>フランス</td>
      <td>ボンジュール</td>
      <td>メルシー</td>
    </tr>
    <tr>
      <td>イタリア</td>
      <td>ブォンジョルノ</td>
      <td>グラッツィエ</td>
    </tr>
  </tbody>
</table>
