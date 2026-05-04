---
title: "Janken"
description: ""
date: "2026-05-04T07:47:28Z"
thumbnail: ""
---
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Arcade Janken</title>
    <script src="https://cdn.jsdelivr.net/npm/phaser@3.60.0/dist/phaser.js"></script>
    <style>
        body {
            margin: 0;
            padding: 0;
            background-color: #000;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        canvas {
            box-shadow: 0 0 20px rgba(0, 255, 255, 0.2);
        }
    </style>
</head>
<body>

<script>
    // --- 定数と勝敗判定ロジック ---
    const HANDS = ['✊', '✌️', '✋']; // 0: グー, 1: チョキ, 2: パー
    
    // 数学的アプローチによる勝敗判定
    // (Player - Enemy + 3) % 3 の結果が 0=引き分け, 1=負け, 2=勝ち
    const checkWin = (player, enemy) => (player - enemy + 3) % 3;

    // --- 1. タイトルシーン ---
    class TitleScene extends Phaser.Scene {
        constructor() { super('TitleScene'); }

        create() {
            const width = this.cameras.main.width;
            const height = this.cameras.main.height;

            // タイトルテキスト
            this.add.text(width / 2, height / 3, 'CYBER JANKEN', {
                fontFamily: 'Arial Black', fontSize: '64px', color: '#0ff',
                stroke: '#000', strokeThickness: 8
            }).setOrigin(0.5);

            // スタートボタン作成
            const startBtn = this.add.text(width / 2, height / 1.5, '> START GAME <', {
                fontFamily: 'Courier', fontSize: '32px', color: '#fff',
                backgroundColor: '#333', padding: { x: 20, y: 10 }
            }).setOrigin(0.5).setInteractive();

            // ホバーアクションとクリックイベント
            startBtn.on('pointerover', () => startBtn.setStyle({ color: '#ff0' }));
            startBtn.on('pointerout', () => startBtn.setStyle({ color: '#fff' }));
            startBtn.on('pointerdown', () => {
                this.scene.start('GameScene', { streak: 0 }); // 連勝カウンターを0で初期化
            });
        }
    }

    // --- 2. メインゲームシーン ---
    class GameScene extends Phaser.Scene {
        constructor() { super('GameScene'); }

        init(data) {
            this.streak = data.streak || 0;
        }

        create() {
            const width = this.cameras.main.width;
            const height = this.cameras.main.height;

            // UI: 連勝数の表示
            this.add.text(20, 20, `WIN STREAK: ${this.streak}`, {
                fontFamily: 'Courier', fontSize: '24px', color: '#0f0'
            });

            this.add.text(width / 2, height / 4, '手を選んでください', {
                fontFamily: 'sans-serif', fontSize: '32px', color: '#fff'
            }).setOrigin(0.5);

            // ボタンの生成
            HANDS.forEach((hand, index) => {
                // 画面下部に等間隔で配置
                const xPos = width / 2 + (index - 1) * 200;
                const btn = this.add.text(xPos, height / 1.5, hand, { fontSize: '80px' })
                    .setOrigin(0.5)
                    .setInteractive();

                // アニメーション
                btn.on('pointerover', () => this.tweens.add({ targets: btn, scale: 1.2, duration: 100 }));
                btn.on('pointerout', () => this.tweens.add({ targets: btn, scale: 1.0, duration: 100 }));
                
                // 選択時の処理
                btn.on('pointerdown', () => this.playTurn(index));
            });
        }

        playTurn(playerChoice) {
            // 敵の手をランダムに決定
            const enemyChoice = Phaser.Math.Between(0, 2);
            
            // リザルトシーンへデータを渡して遷移
            this.scene.start('ResultScene', {
                playerChoice,
                enemyChoice,
                streak: this.streak
            });
        }
    }

    // --- 3. リザルトシーン ---
    class ResultScene extends Phaser.Scene {
        constructor() { super('ResultScene'); }

        init(data) {
            this.p = data.playerChoice;
            this.e = data.enemyChoice;
            this.streak = data.streak;
            this.resultCode = checkWin(this.p, this.e);
        }

        create() {
            const width = this.cameras.main.width;
            const height = this.cameras.main.height;

            // お互いの手を表示
            this.add.text(width / 4, height / 3, `YOU\n\n${HANDS[this.p]}`, { fontSize: '64px', align: 'center' }).setOrigin(0.5);
            this.add.text(width * 3 / 4, height / 3, `ENEMY\n\n${HANDS[this.e]}`, { fontSize: '64px', align: 'center' }).setOrigin(0.5);
            this.add.text(width / 2, height / 3 + 40, 'VS', { fontStyle: 'italic', fontSize: '48px', color: '#f00' }).setOrigin(0.5);

            // 勝敗結果のテキストと次への状態
            let resultText = '';
            let color = '';
            let nextStreak = this.streak;

            if (this.resultCode === 2) {
                resultText = 'YOU WIN!';
                color = '#0f0';
                nextStreak++;
            } else if (this.resultCode === 1) {
                resultText = 'YOU LOSE...';
                color = '#555';
                nextStreak = 0; // 連勝ストップ
            } else {
                resultText = 'DRAW';
                color = '#ff0';
            }

            const resultObj = this.add.text(width / 2, height / 1.8, resultText, {
                fontFamily: 'Arial Black', fontSize: '64px', color: color
            }).setOrigin(0.5).setScale(0);

            // 結果テキストのポップアップアニメーション
            this.tweens.add({
                targets: resultObj,
                scale: 1,
                ease: 'Back.easeOut',
                duration: 500,
                onComplete: () => {
                    this.createNextButton(width, height, nextStreak);
                }
            });
        }

        createNextButton(width, height, nextStreak) {
            const btnText = this.resultCode === 1 ? '> RETURN TO TITLE <' : '> NEXT BATTLE <';
            const nextBtn = this.add.text(width / 2, height / 1.2, btnText, {
                fontFamily: 'Courier', fontSize: '32px', color: '#fff',
                backgroundColor: '#333', padding: { x: 20, y: 10 }
            }).setOrigin(0.5).setInteractive();

            nextBtn.on('pointerover', () => nextBtn.setStyle({ color: '#ff0' }));
            nextBtn.on('pointerout', () => nextBtn.setStyle({ color: '#fff' }));
            
            nextBtn.on('pointerdown', () => {
                if (this.resultCode === 1) {
                    this.scene.start('TitleScene');
                } else {
                    this.scene.start('GameScene', { streak: nextStreak });
                }
            });
        }
    }

    // --- ゲーム設定と初期化 ---
    const config = {
        type: Phaser.AUTO,
        width: 800,
        height: 600,
        backgroundColor: '#1a1a2e', // 深いネイビーでサイバー感を演出
        parent: 'game-container',
        scene: [TitleScene, GameScene, ResultScene]
    };

    const game = new Phaser.Game(config);
</script>
</body>
</html>
