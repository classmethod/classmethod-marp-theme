# Marp資料作成（ステップ3）

スライド設計書（slide-designの出力）から、Marp形式のスライド資料を生成する。このスキルの出力が最終成果物となる。

## 入力

ユーザーから以下の情報を受け取る。

| 項目 | 説明 | 形式 |
|------|------|------|
| スライド設計書 | slide-designの出力 | `02_slide-design_[資料名].md` |
| 画像ファイル | 使用する画像（任意） | パスまたは配置予定の説明 |

出力先は入力ファイルと同じフォルダに配置する。

## 出力

`03_marp_[資料名].md` を生成する。

### ファイル構造

```markdown
---
marp: true
theme: classmethod
paginate: true
title: [資料タイトル]
description: [資料の説明]
---

<!-- _class: title -->
<!-- _paginate: false -->

![classmethod-logo w:400px](https://classmethod.jp/wp-content/themes/cmn/assets/images/common/logo_classmethod.svg)

# [資料タイトル]

[日付や執筆者情報]

---

<!-- _class: section -->
<!-- _paginate: false -->

## [セクション名]
[セクションの説明文]

---

# [スライドタイトル]

[本文や箇条書き]

---

[以下、全スライドを記載]
```

## ワークフロー

### Step 1: スライド設計書の読み込み

`02_slide-design_[資料名].md` を読み込み、以下を把握する。

- 資料タイトルと説明
- スライド枚数と各スライドの構成
- 使用するレイアウトクラス
- 図表の配置位置

### Step 2: サンプルスライドの取得

以下のコマンドで最新のサンプルスライドを取得する。

```bash
curl -s https://raw.githubusercontent.com/classmethod/classmethod-marp-theme/main/sample-slide.md
```

取得したサンプルから以下を確認する。

- Front matter の記述方法
- 各レイアウトクラスの使用例
- 画像配置の記法
- コメント記法（`<!-- _class: xxx -->`）

詳細は [get-sample-slide.md](get-sample-slide.md) を参照。

### Step 3: Front matter の作成

ファイル冒頭のメタデータを作成する。

```yaml
---
marp: true
theme: classmethod
paginate: true
title: [資料タイトル]
description: [資料の説明（1〜2文）]
---
```

### Step 4: 表紙スライドの作成

表紙（titleレイアウト）を作成する。

```markdown
<!-- _class: title -->
<!-- _paginate: false -->

![classmethod-logo w:400px](https://classmethod.jp/wp-content/themes/cmn/assets/images/common/logo_classmethod.svg)

# [資料タイトル]

[日付や執筆者情報]

---
```

**注意点:**
- `_class` の前にアンダースコアを付ける
- ページネーションは false に設定
- ロゴのURLは固定値を使用

### Step 5: 各スライドの生成

スライド設計書に基づき、各スライドを生成する。

**基本的なスライド記法:**

```markdown
---

# [スライドタイトル]

[本文や箇条書き]

---
```

**セクションスライドの記法:**

```markdown
---

<!-- _class: section -->
<!-- _paginate: false -->

## [セクション名]
[説明文]

---
```

**図表を含むスライド（content-image）:**

```markdown
---

<!-- _class: content-image -->

# [スライドタイトル]

![w:700px]([画像パスまたはプレースホルダー])

[キャプションや説明文]

---
```

**横並びレイアウト（content-image-right）:**

```markdown
---

<!-- _class: content-image-right -->

# [スライドタイトル]

![w:500px]([画像パス])

- [ポイント1]
- [ポイント2]
- [ポイント3]

---
```

**カラムレイアウト（column-layout）:**

```markdown
---

<!-- _class: column-layout -->

# [スライドタイトル]

<div class="column">

## [左カラム]
- [項目1]
- [項目2]

</div>

<div class="column">

## [右カラム]
- [項目1]
- [項目2]

</div>

---
```

### Step 6: レイアウトクラスの適用

スライド設計書で指定されたレイアウトクラスを正確に適用する。

| レイアウトクラス | コメント記法 | ページネーション |
|-----------------|-------------|-----------------|
| title | `<!-- _class: title -->` | false |
| section | `<!-- _class: section -->` | false |
| 基本（指定なし） | コメント不要 | true（デフォルト） |
| image | `<!-- _class: image -->` | true |
| content-image | `<!-- _class: content-image -->` | true |
| content-image-right | `<!-- _class: content-image-right -->` | true |
| content-image-left | `<!-- _class: content-image-left -->` | true |
| column-layout | `<!-- _class: column-layout -->` | true |
| small-text | `<!-- _class: small-text -->` | true |
| no-header | `<!-- _class: no-header -->` | true |

**幅調整が必要な場合:**
- content-image-right/left では、`content-60` などのクラスを追加して幅を調整できる
- 例: `<!-- _class: content-image-right content-60 -->`

### Step 7: 画像の配置

図表が必要な箇所に画像を配置する。

**画像記法:**
```markdown
![w:700px](images/diagram.png)
```

**サイズ指定:**
- `w:XXpx`: 幅を指定（例: w:400px, w:700px）
- `h:XXpx`: 高さを指定（例: h:300px）

**画像が未準備の場合:**
プレースホルダーを使用する。

```markdown
![w:700px](https://placehold.jp/300x200.png)
<!-- TODO: ○○の図に差し替え -->
```

または、コメントのみを記載する。

```markdown
<!-- 画像: ○○の構成図（images/architecture.png）を配置予定 -->
```

### Step 8: 箇条書きと強調の適用

スライド設計書の内容を、適切に箇条書きや強調で表現する。

**箇条書き:**
```markdown
- 項目1
- 項目2
- 項目3
```

**番号付きリスト:**
```markdown
1. ステップ1
2. ステップ2
3. ステップ3
```

**強調（見出しの一部を青色にする）:**
```markdown
## 見出しの一部を**青色のアクセントカラー**にする
```

見出し内の `**` で囲まれた部分は青色のアクセントカラーになる。

### Step 9: 参考リンクの配置

スライド設計書に「参考リンク」がある場合、スライド末尾に配置する。

**参考リンクの記法:**
```markdown
参考: [リンクタイトル](URL)
```

リンクはスライドの本文の最後に配置し、「参考:」のラベルを付ける。

### Step 10: ページネーションの制御

適切にページネーションを制御する。

- 表紙（title）: `<!-- _paginate: false -->`
- セクション（section）: `<!-- _paginate: false -->`
- その他: デフォルト（true）のまま

### Step 11: ファイル出力

`03_marp_[資料名].md` を出力する。

ファイル作成後、以下をユーザーに伝える。

- 出力ファイルのパス
- スライド枚数
- 次のアクション（プレビュー、PDF変換など）
- 画像が未配置の場合はその旨

## Marp記法リファレンス

### Front matter

```yaml
---
marp: true
theme: classmethod
paginate: true
title: スライドタイトル
description: スライドの説明
---
```

### スライド区切り

```markdown
---
```

3つのハイフンで区切る。

### レイアウトクラス指定

```markdown
<!-- _class: section -->
```

コメント形式で指定。`_class` の前にアンダースコアを付ける。

### ページネーション制御

```markdown
<!-- _paginate: false -->
```

個別スライドでページ番号を非表示にする。

### 画像サイズ指定

```markdown
![w:400px](path/to/image.png)
![h:300px](path/to/image.png)
```

### 見出し強調

```markdown
## 見出しの一部を**青色**にする
```

見出し内の `**` 囲みは青色のアクセントカラーになる。

### コードブロック

````markdown
```typescript
const message: string = "Hello, Marp!";
console.log(message);
```
````

### 引用

```markdown
> 引用文
```

### テーブル

```markdown
| 列1 | 列2 | 列3 |
|-----|-----|-----|
| A   | B   | C   |
```

### カスタムCSS（スライド固有）

```markdown
<style scoped>
.highlight {
  background-color: #e3f2fd;
}
</style>

<div class="highlight">
強調したいコンテンツ
</div>
```

## エラー対処

| エラー | 原因 | 対処 |
|--------|------|------|
| スライド設計書が読めない | パスが間違っている | ユーザーに正しいパスを確認 |
| レイアウトが正しく表示されない | クラス名が間違っている | 最新のサンプルスライドを取得して確認 |
| 画像が表示されない | パスが間違っている | 画像ファイルの配置を確認 |
