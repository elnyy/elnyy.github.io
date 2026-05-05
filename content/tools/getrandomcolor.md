---
title: "ランダムなカラーコードを出力するウェブツール"
description: ""
toc: false
date: "2026-05-04T13:39:28Z"
thumbnail: ""
categories:
  - "ウェブツール"
---
<!--more-->
<div style="text-align:center; margin-top:50px;">
  <button id="copyButton" onclick="copyColorCode()" style="padding:10px 20px; font-size:12px;">
コピー
</button>
  <h1 id="colorCode">#000000</h1>
  <div id="colorBox" style="width:200px; height:200px; margin:20px auto; background:#000000;"></div>
  <button onclick="generateColor()" style="padding:10px 20px; font-size:16px;">
生成
  </button>
</div>

<script>
function generateColor() {
  const color = "#" + Math.floor(Math.random() * 16777215).toString(16).padStart(6, '0');
  document.getElementById("colorCode").innerText = color;
  document.getElementById("colorBox").style.backgroundColor = color;

  copyButton.innerText = "コピー"
  
}

function copyColorCode() {
  navigator.clipboard.writeText(colorCode.innerText);
  copyButton.innerText = "コピーしました"
  
}

// 初回ロード時にも生成
generateColor();
</script>
<br>

---

## 使い方
このページにアクセスするだけで、ランダムなカラーコードを生成します。

また、「生成」ボタンを押すことで新しいカラーコードを出力することができます。

## TODO (2026/5/4)
- [x] カラーコードのコピーボタンの追加
- [ ] ショートハンドカラーコードも出力するように
- [ ] 生成のUNDO,REDOをできるように
