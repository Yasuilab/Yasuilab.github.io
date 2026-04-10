# 安井研究室 ウェブサイト 管理マニュアル

---
実際のサイト：https://yasuilab.github.io/
## 目次

### 変更したい内容から探す

| やりたいこと | 参照先 |
|-------------|--------|
| 教員名・連絡先・説明文を変えたい | [基本情報の変更](#基本情報の変更) |
| トップページの文章・写真を変えたい | [トップページの編集](#トップページの編集) |
| メール・SNSリンクを変えたい | [ソーシャルリンクの変更](#ソーシャルリンクの変更) |
| お知らせや記事を追加したい | [お知らせ・ブログ記事の追加](#お知らせブログ記事の追加) |
| 卒研・修士・博士・セミナーのページを変えたい | [教育ページの編集](#教育ページの編集) |
| 論文リストを更新したい | [論文リストの追加](#論文リストの追加) |
| 画像・PDFを追加したい | [ファイルの追加](#ファイルの追加) |

### 操作方法から探す

- [ファイルを編集する（初心者向け：GitHub上で直接編集）](#github-上で作業する初心者向け)
- [ファイルを編集する（開発者向け：ローカル環境で確認しながら編集）](#開発者向けローカル環境で編集する)
- [ファイル構成](#ファイル構成)

---

## ファイルを編集・追加する方法

### GitHub 上で作業する（初心者向け）

#### 記事の追加
記事の追加など、新規ファイルが必要な場合はブラウザ上で作成できます。

1. このリポジトリのページをブラウザで開く
2. ファイルを置きたいフォルダ（例：`_posts/`）をクリックして開く
3. 右上の **"Add file"** → **"Create new file"** をクリック
4. 画面上部の入力欄にファイル名を入力する（例：`2026-04-10-spring-seminar.md`）
5. 下の編集エリアに内容を書く
6. 画面右上の **"Commit changes"** ボタンを押す
7. 数分後に自動でサイトが更新される

#### 記事の編集

特別なソフトのインストールは不要です。ブラウザだけで編集できます。

1. このリポジトリのページをブラウザで開く
2. 編集したいファイルをクリックして開く
3. 右上の鉛筆アイコン（✏️ Edit this file）をクリック
4. 内容を編集する
5. 画面下部の **"Commit changes"** ボタンを押す
6. 数分後に自動でサイトが更新される

> **注意**：編集内容は即座に公開されます。大きな変更の場合は、開発者向けの方法で事前に確認することをお勧めします。

---

### 開発者向け：ローカル環境で編集する

変更をサイトに反映する前に手元で確認できます。Docker が必要です。

**事前準備：Docker のインストール**

[Docker 公式サイト（Docker Desktop）](https://www.docker.com/products/docker-desktop/) からインストールしてください。

```bash
# 初回・依存関係変更時
docker compose up --build

# 通常起動
docker compose up
```

基本的には、起動後にブラウザで http://localhost:8080 を開くと確認できます。  
ファイルを保存すると自動的にページが更新されます。

```bash
# 停止するとき
docker compose down
```

---

## 基本情報の変更

**編集ファイル：`_config.yml`**

| 変更したい項目 | 該当するキー名 |
|--------------|--------------|
| サイトのタイトル | `title` |
| 教員の姓 | `first_name` |
| 教員の名 | `last_name` |
| サイトの説明文 | `description` |
| 連絡先の補足文（ソーシャルアイコン下のひとこと） | `contact_note` |

**例：**
```yaml
title: 安井 Laboratory
first_name: 安井
last_name: 清一
contact_note: >
  お問い合わせはメールにてお気軽にどうぞ。
```

---

## トップページの編集

**編集ファイル：`_pages/about.md`**

### プロフィール画像

1. 画像ファイルを `assets/img/` に置く
2. `_pages/about.md` の `profile.image:` にファイル名を書く

```yaml
profile:
  image: yasui.jpg   # assets/img/ に置いたファイル名
```

### 住所・電話番号

`_pages/about.md` の `more_info:` を編集します。

```yaml
  more_info: >
    <p>指導教員：安井 清一 教授</p>
    <p>〒278-8510 千葉県野田市山崎2641</p>
    <p>TEL: 04-7124-1501（代表） 内線 3824</p>
```

### 自己紹介文

ファイル末尾の `---` より下の部分を自由に編集します。

---

## ソーシャルリンクの変更

**編集ファイル：`_data/socials.yml`**

```yaml
email: you@example.com       # メールアドレス（要変更）
facebook_id: your_username   # Facebook ユーザー名（要変更）
custom_social:
  logo: fas fa-university    # アイコン（Font Awesome のクラス名）
  title: 研究者データベース
  url: "https://..."         # URL（& が含まれる場合はダブルクォートで囲む）
```

> **Font Awesome アイコンを変えたい場合**：[Font Awesome アイコン一覧](https://fontawesome.com/icons) で探し、`fas fa-○○` の形式で指定します。

---

## お知らせ・ブログ記事の追加

**編集フォルダ：`_posts/`**

### 記事ファイルの作り方

`_posts/` フォルダ内に、以下の名前でファイルを作成します。

**ファイル名：** `YYYY-MM-DD-任意のタイトル.md`  
（例：`2026-04-01-spring-seminar.md`）

**ファイルの中身：**

```markdown
---
layout: post
title: 記事のタイトル
date: 2026-04-01 00:00:00
description: 一覧ページに表示される概要文
tags: お知らせ
categories: news
---

ここに本文を書きます。

**太字**、*斜体*、箇条書きなど、Markdown 記法が使えます。

- 項目1
- 項目2
```

### トップページの表示件数を変える

`_pages/about.md` の `latest_posts.limit` を変更します。

```yaml
latest_posts:
  enabled: true
  limit: 3   # ← この数字を変える
```

---

## 教育ページの編集

**編集フォルダ：`_education/`**

| ファイル名 | 対応するページ |
|-----------|--------------|
| `seminar.md` | セミナー |
| `bachelor.md` | 卒業研究 |
| `master.md` | 修士課程 |
| `docter.md` | 博士課程 |

各ファイルを開き、`---` より下の本文部分を自由に編集します。  
Markdown 記法が使えます（見出し `##`、箇条書き `-`、表 `|` など）。

> **表示順序を変えたい場合**：フロントマターの `importance:` の数値を変えます。数値が小さいほど上に表示されます。

---

## 論文リストの追加

**編集ファイル：`_bibliography/papers.bib`**

BibTeX 形式で論文情報を追記します。

```bibtex
@article{yamada2025example,
  title   = {論文タイトル},
  author  = {Yamada, Taro and Yasui, Seiichi},
  journal = {ジャーナル名},
  year    = {2025},
  volume  = {1},
  pages   = {1--10}
}
```

**トップページの「主要論文」欄に表示したい場合**は、`selected = {true}` を追加します。

```bibtex
@article{yamada2025example,
  ...
  selected = {true}
}
```

---

## ファイルの追加

### 画像

`assets/img/` フォルダに画像ファイル（JPG・PNG など）を置きます。  
ページから参照するときは `/assets/img/ファイル名` と書きます。

### PDF

`assets/pdf/` フォルダに PDF ファイルを置きます。  
ページから参照するときは `/assets/pdf/ファイル名.pdf` と書きます。

---

## ファイル構成

```
_config.yml           # サイト全体の設定（基本情報など）
_data/
  socials.yml         # ソーシャルリンク
_pages/
  about.md            # トップページ
_posts/               # ブログ記事（お知らせ）
_education/           # 教育ページ（卒研・修士・博士・セミナー）
_bibliography/
  papers.bib          # 論文リスト（BibTeX形式）
assets/
  img/                # 画像ファイル
  pdf/                # PDF ファイル
```
