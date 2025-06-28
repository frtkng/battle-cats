# Mini Battle Cats — Simple HTML5 Tower Defense

> 🎮  Inspired by *にゃんこ大戦争* / *The Battle Cats*. A single‑file browser game you can fork, tweak, and share.

---

## 概要 / Overview

* **ワンファイル** (`index.html`) だけで動くブラウザゲーム。
* 60 FPS 描画 (`requestAnimationFrame`) とシンプルな物理判定。
* ボタンひとつでネコを出撃 → 敵拠点 HP を 0 にすれば勝利。
* コードを数行変更するだけでユニット追加・画像差し替えが可能。

## Quick Start

```bash
# 1. Clone or download
$ git clone https://github.com/<user>/mini-battle-cats.git
$ cd mini-battle-cats

# 2. Launch
# Option A: double‑click index.html (offline OK)
# Option B: serve locally if browser blocks file://
$ python -m http.server 8000
# open http://localhost:8000/index.html
```

## How to Play

| Action         | 操作                      | Cost / Effect   |
| -------------- | ----------------------- | --------------- |
| Spawn Cat      | Click **Cat 100円**      | 100円消費、近接ユニット出撃 |
| Passive income | None                    | +20円 / 秒        |
| Win            | Destroy enemy base (右端) | —               |
| Lose           | 自拠点 HP が 0              | —               |

## File Structure

```
.
├── index.html   # full game (logic + UI + styles)
└── README.md    # this file
```

## Customisation Guide

### Add a New Unit

1. `class Unit` をコピー or パラメータ化。
2. `hp`, `atk`, `speed`, `width`, `height`, `color` を調整。
3. 画面下 UI に新ボタンを追加し、クリックで `units.push(new Unit(...))`。

### Use Sprites

```js
const img = new Image();
img.src = 'cat.png';
// inside draw()
ctx.drawImage(img, this.x, this.y, this.width, this.height);
```

### Balance Tweaks

| Parameter        | Location                       | Meaning     |
| ---------------- | ------------------------------ | ----------- |
| Money income     | `money += dt * 20`             | 経過秒 × 20円   |
| Enemy spawn rate | `if(enemyTimer > 3)`           | 秒数を下げて難易度UP |
| Base HP          | `bases.player.hp` / `enemy.hp` | 耐久値調整       |

## Roadmap ✨

* Multiple lanes & ranged units
* Sprite animation / atlas
* Sound effects & BGM
* Upgrade system & levels
* Touch UI for mobile

## Contributing

Issues & PRs welcome! Feel free to fork and remix.

## License

MIT © 2025 Kengo
