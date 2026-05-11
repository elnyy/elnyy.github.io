---
title: "【まどドラ】フレンドメダルの獲得方法と獲得量"
description: "フレンドメダルの獲得方法と獲得量についてのまとめです。"
date: "2026-05-11T13:52:03Z"
thumbnail: "https://pbs.twimg.com/profile_banners/1777865487755718656/1777514765/1080x360"
categories:
  - "games"
tags:
  - "まどドラ"
---
<!--more-->
今更ですが、フレンドメダルの獲得方法とその獲得量をまとめました。

<table>
<caption>
フレンドメダル獲得方法と獲得量(26/05/11)
	<tbody>
		<tr>
			<td>獲得方法</td>
			<td>獲得量</td>
		<tr>
			<td>リンクレイドで「いいね」 をする</td>
			<td>100</td>
		</tr>
		</tr>
		<tr>
			<td>相互フォローのプレイヤーからキオクをレンタルする</td>
			<td>100</td>
		</tr>
		<tr>
			<td>相互フォローのプレイヤーにキオクをレンタルされる</td>
			<td>100</td>
		</tr>
		<tr>
			<td>フォロー/フォロワーのプレイヤーにキオクをレンタルされる</td>
			<td>70</td>
		</tr>
		<tr>
			<td>フレンド以外のプレイヤーからキオクをレンタルする</td>
			<td>40</td>
		</tr>
		<tr>
			<td>フレンド以外のプレイヤーにキオクをレンタルされる</td>
			<td>40</td>
		</tr>
	</tbody>
</table>

また、フレンドメダルには**一日の獲得量に上限があります**。

<u>10,000個</u>です。

ふつうにやっていたらこの量に到達することはないので気にすることはなさそうですが。

これと同じような内容をゲーム内の「ヘルプ」=>「フレンド」=>「フレンドメダルについて」から見れるので、そっちを参考にしたほうがいいと思います。
~~なら、なんでこんなページ作った?~~

## マギアキー１つ獲得するまでのパターン

フレンドメダルで交換できるアイテムといえば、マギアキーがあります。

無課金者にとってはマギアキーの価値はかなり高いと思います。

しかし、フレンドメダル3000個でマギアキー１つなので、かなり頑張って集めないといけません。

約3000個集めるのにどんなパターンがあるのか、ランダムで出力するスクリプトを置いておくので、色々なパターンを見て何か参考になったらいいですね(?)

  <button id="generateBtn">生成する</button>

  <pre id="result"></pre>

  <script>
    // 3000個獲得パターン
    const patterns = [
      { name: "リンクレイドで「いいね」をする", value: 100 },
      { name: "相互フォローのプレイヤーからキオクをレンタルする", value: 100 },
      { name: "相互フォローのプレイヤーにキオクをレンタルされる", value: 100 },
      { name: "フォロー/フォロワーのプレイヤーにキオクをレンタルされる", value: 70 },
      { name: "フレンド以外のプレイヤーからキオクをレンタルする", value: 40 },
      { name: "フレンド以外のプレイヤーにキオクをレンタルされる", value: 40 },
    ];

    const TARGET = 3000;

    // ランダム生成
    function generateRandomPattern() {
      let total = 0;
      const result = {};

      // 初期化
      patterns.forEach(p => {
        result[p.name] = 0;
      });

      while (total < TARGET) {
        const remain = TARGET - total;

        // 残り以内で選べるもの
        const available = patterns.filter(p => p.value <= remain);

        if (available.length === 0) {
          break;
        }

        // ランダム選択
        const selected =
          available[Math.floor(Math.random() * available.length)];

        result[selected.name]++;
        total += selected.value;
      }

      return {
        result,
        total
      };
    }

    // 表示
    function render() {
      const output = document.getElementById("result");

      const data = generateRandomPattern();

      let text = "=== 3000個獲得パターン ===\n\n";

      for (const [name, count] of Object.entries(data.result)) {
        if (count > 0) {
          const value = patterns.find(p => p.name === name).value;
          const subtotal = value * count;

          text += `${name} × ${count}回 = ${subtotal}個\n`;
        }
      }

      text += "\n----------------------\n";
      text += `合計: ${data.total}個`;

      output.textContent = text;
    }

    // ボタン押下
    document
      .getElementById("generateBtn")
      .addEventListener("click", render);

    // 初回表示
    render();
  </script>

</body>
</html>
