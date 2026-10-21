# Web アプリの画面（GitHub Pages に置くもの）

このフォルダの `README.md` のほかは、`python portfolio/shared/build.py` が作る（直さない）。直すのは `portfolio/shared/web/`（共通の部品）と、見本の `web/`（例：`portfolio/05_site-photos/web/photo.html`）。

- 置き場所：GitHub の **shikumikobo/apps**（公開）の GitHub Pages → `https://shikumikobo.github.io/apps/`
- 画面の URL：`https://shikumikobo.github.io/apps/05/photo.html?s=<受け口のデプロイID>&k=<合言葉>`。台帳のメニュー「〜の画面の URL を出す」が作る
- ここにはお客さんごとの値（デプロイID・合言葉・台帳）を書かない。どのお客さんも同じ画面を使い、URL の `s` と `k` で分かれる
- 考え方：Google の中（HtmlService）で画面を出すと、Google にログインしている普通の Chrome で「ファイルを開くことができません」になった（2026-10-21）。外の画面から fetch で処理だけを送ると、ログインの情報が付かないので、だれでも同じに動く。設計は [../README.md](../README.md) の2章「入口とツールの定義」

## 初めの準備（人がする。1回だけ）

1. GitHub に **shikumikobo** のアカウントでログインし、右上の「+」→「New repository」
2. Repository name：`apps`、**Public**、ほかは空のまま →「Create repository」
3. 作ったら、AI に「apps を作った」と伝える（AI がこのフォルダの中身を送る）
4. AI が送ったあと、リポジトリの「Settings」→ 左の「Pages」→ Source「Deploy from a branch」、Branch「main」・「/ (root)」→「Save」。1〜2分で `https://shikumikobo.github.io/apps/` が開けるようになる

## 画面を直したとき（AI がする）

```bash
python portfolio/shared/build.py
```

```bash
python portfolio/shared/publish_site.py
```

`publish_site.py` は、このフォルダの中身を `C:\dev\shikumikobo-apps`（apps の作業用の写し）に写し、コミットして push する。
