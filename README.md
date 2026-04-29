# Cafe こもれび ウェブサイト - 公開＆写真追加ガイド

---

## 📁 フォルダ構成

```
cafe-komorebi/
├── index.html          ← サイト本体
├── images/             ← 写真を入れるフォルダ
│   ├── hero.jpg        ← ①メインビジュアル（横長推奨：1600×900px以上）
│   ├── menu1.jpg       ← ②メニュー写真1（正方形〜4:3推奨）
│   ├── menu2.jpg       ← ③メニュー写真2
│   ├── menu3.jpg       ← ④メニュー写真3
│   ├── gallery1.jpg    ← ⑤ギャラリー写真1（正方形推奨）
│   ├── gallery2.jpg    ← ⑥ギャラリー写真2
│   ├── gallery3.jpg    ← ⑦ギャラリー写真3
│   └── gallery4.jpg    ← ⑧ギャラリー写真4
└── README.md           ← このファイル
```

---

## STEP 1：GitHubにリポジトリを作る

1. https://github.com にログイン
2. 右上の「+」→「New repository」をクリック
3. 以下を入力：
   - Repository name: `cafe-komorebi`
   - Public を選択
   - 「Create repository」をクリック

4. ターミナルで以下を実行：

```bash
# ダウンロードしたフォルダに移動
cd cafe-komorebi

# Gitを初期化
git init
git add .
git commit -m "初回アップロード"

# GitHubに接続（URLは自分のリポジトリに合わせて変更）
git remote add origin https://github.com/あなたのユーザー名/cafe-komorebi.git
git branch -M main
git push -u origin main
```

---

## STEP 2：Vercelにデプロイ（公開）する

1. https://vercel.com にログイン（GitHubアカウントで）
2. 「Add New...」→「Project」をクリック
3. 「Import Git Repository」で `cafe-komorebi` を選択
4. そのまま「Deploy」をクリック

→ 数十秒で `cafe-komorebi.vercel.app` のようなURLが発行されます！
→ このURLをスマホのブラウザで開けば、もう見られます。

---

## STEP 3：写真を追加する ⭐ここが本題！

### 3-1. 写真を用意する

スマホで撮った写真でOKです。ファイル名を以下のように変更してください：

| ファイル名 | 用途 | 推奨サイズ |
|-----------|------|-----------|
| hero.jpg | メインの大きな写真 | 横1600px以上 |
| menu1.jpg | メニュー写真1 | 800×600px程度 |
| menu2.jpg | メニュー写真2 | 800×600px程度 |
| menu3.jpg | メニュー写真3 | 800×600px程度 |
| gallery1.jpg | ギャラリー1 | 800×800px程度 |
| gallery2.jpg | ギャラリー2 | 800×800px程度 |
| gallery3.jpg | ギャラリー3 | 800×800px程度 |
| gallery4.jpg | ギャラリー4 | 800×800px程度 |

※ .png でもOKですが、ファイルサイズが大きくなるので .jpg 推奨

### 3-2. images フォルダに写真を入れる

`cafe-komorebi/images/` フォルダに写真を入れます。

### 3-3. index.html を編集する

テキストエディタ（メモ帳でもOK、VS Codeが便利）で `index.html` を開いて、
以下の部分を探して書き換えます。

#### 写真① メインビジュアル
「写真① メインビジュアル」で検索すると見つかります。

変更前：
```html
<div class="hero-right" id="photo-hero">
  <div class="photo-placeholder">
    ...
  </div>
</div>
```

変更後：
```html
<div class="hero-right" id="photo-hero" style="background-image: url('images/hero.jpg');">
  <!-- プレースホルダーを削除またはコメントアウト -->
</div>
```

#### 写真②③④ メニュー写真
「写真②」「写真③」「写真④」で検索。

変更前：
```html
<div class="menu-card-image" id="photo-menu1">
  <div class="photo-placeholder">...</div>
</div>
```

変更後：
```html
<div class="menu-card-image" id="photo-menu1" style="background-image: url('images/menu1.jpg');">
</div>
```

※ photo-menu2 → images/menu2.jpg、photo-menu3 → images/menu3.jpg も同様

#### 写真⑤⑥⑦⑧ ギャラリー写真
「写真⑤」〜「写真⑧」で検索。

変更前：
```html
<div class="gallery-item reveal" id="photo-gallery1">
  <div class="photo-placeholder">...</div>
</div>
```

変更後：
```html
<div class="gallery-item reveal" id="photo-gallery1" style="background-image: url('images/gallery1.jpg');">
</div>
```

### 3-4. GitHubにプッシュする

```bash
cd cafe-komorebi
git add .
git commit -m "写真を追加"
git push
```

→ 数十秒後、Vercelが自動で更新してくれます！
→ サイトをリロードすると写真が表示されます。

---

## 写真を差し替えたいとき

同じファイル名で新しい写真を `images/` に入れて、git push するだけ！

```bash
# 写真を上書き保存したあと
git add .
git commit -m "写真を差し替え"
git push
```

---

## よくある質問

**Q: 写真のファイル名は変えられる？**
→ 変えられます。ただし index.html 内の url('images/○○.jpg') も合わせて変更してください。

**Q: 写真が表示されない**
→ ファイル名の大文字小文字が一致しているか確認してください（Hero.JPG ≠ hero.jpg）

**Q: スマホで撮った写真が重い**
→ https://squoosh.app/ で圧縮すると軽くなります（200KB以下推奨）

**Q: 独自ドメイン（cafe-komorebi.com）を使いたい**
→ Vercelの Settings > Domains で設定できます。ドメインは Googleドメイン等で年1,500円程度で購入できます。
