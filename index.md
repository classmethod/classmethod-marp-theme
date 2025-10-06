---
marp: true
theme: classmethod
paginate: true
title: Classmethod Marp Theme
description: クラスメソッドのスライドデザインを参考に作成したMarpテーマ
---

<!-- _class: title -->
<!-- _paginate: false -->

![classmethod-logo w:400px](https://classmethod.jp/wp-content/themes/cmn/assets/images/common/logo_classmethod.svg)

# Classmethod Marp Theme
## セットアップスライド

2025/08/19 更新

---

# 概要
クラスメソッドのスライドデザインを参考に作成したMarpテーマです。


## 参考リンク

#### サンプルスライド
こちらのリンクからサンプルスライドをみることができます。
https://classmethod.github.io/classmethod-marp-theme/sample-slide.html

#### Github

https://github.com/classmethod/classmethod-marp-theme

#### Marp 公式サイト

https://marp.app/

---

# 特徴

## 📝 マークダウンでスライド作成
クラスメソッドのスライドデザインのスライドがマークダウンで作成可能

## 🤗 豊富な要素対応
テーブル、コードブロック、引用など、マークダウン要素に対応

## 🤖 生成AIで作りやすい
生成AIに内容、README.md、sample-slide.mdを入力して爆速でスライド作成可能

---

<!-- _class: section -->
<!-- _paginate: false -->

## 利用方法

VSCodeやCLIで簡単に使えます

---

<!-- _class: content-image-right content-60 -->

# VSCodeでの設定方法
![w:450px](./images/vscode-marp-theme-setup.png)
![w:450px](./images/sample-slide-title.png)

1. Marpの拡張機能をインストール
   https://marketplace.visualstudio.com/items?itemName=marp-team.marp-vscode
2. VSCodeの設定を開く（`Cmd+,` または `Ctrl+,`）
3. 検索ボックスで「`Markdown › Marp: Themes`」を検索
4. 「項目の追加」をクリック
5. 以下のリンクを入力
   ```
   https://classmethod.github.io/classmethod-marp-theme/classmethod-theme.css
   ```
6. Markdownファイルの先頭でテーマを指定
7. サンプルスライドを参考にスライドを作成
8. このスライドと同じデザインになったらOK！

---
<!-- _class: image -->

# VSCode拡張機能を利用してマークダウンからスライドを表示する
右上のMarpアイコンからマークダウンをスライドで表示することができます

![w:1000px](https://raw.githubusercontent.com/marp-team/marp-vscode/main/docs/toggle.gif)

---
<!-- _class: image -->

# VSCode拡張機能を利用してHTML・PDFへの出力を行う

右上のMarpアイコンからHTML・PDFへの出力を行うことができます

![w:1000px](https://raw.githubusercontent.com/marp-team/marp-vscode/main/docs/export.gif)

---

# CLIでの利用

1. Githubから[テーマのCSSファイル](https://github.com/classmethod/classmethod-marp-theme/blob/main/classmethod-theme.css)をダウンロード

2. Marp形式で作成したマークダウンファイルを用意

3. Markdownファイルの先頭でテーマを指定

4. 以下のコマンドを実行

```bash
npx @marp-team/marp-cli@latest slide.md --theme your-directory/classmethod-theme.css
```

---

# テーマの指定方法

Markdownファイルの先頭に以下のFront Matterを記述します

```markdown
---
marp: true
theme: classmethod
---
```

これだけでクラスメソッドのデザインテーマが適用されます！

<br>

## 細かい内容は**サンプルスライド**をご覧ください！

https://classmethod.github.io/classmethod-marp-theme/sample-slide.html

---


# :robot:AIを使ってスライドを作成する方法（オススメ）

1. スライドの内容を考える
2. sample-slide.mdのテキストをコピー（下図参照）
リンク: https://github.com/classmethod/classmethod-marp-theme/blob/main/sample-slide.md
3. AIツール(Cursor, Claude Codeなど)のチャット欄に貼り付け
```md
{sample-slide.mdのコピペ}
このテンプレートを使って〇〇.mdの内容のMarpスライドを作成して〇〇.mdに出力してください。
```
4. スライドの内容、レイアウト、画像のサイズを調整

![w:500px](images/sample-slide-copy.png)

---

<!-- _class: all-text-center align-center -->

![w:450px](https://classmethod.jp/wp-content/themes/cmn/assets/images/common/logo_classmethod.svg)

# ぜひお試しください！

このテーマはクラスメソッド社の内部使用を目的として作成されています