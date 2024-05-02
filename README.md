# Markedjs について

[公式サイト](https://marked.js.org/)

## インストール

CLI を使うためには、npm を使ったインストールが必要。
グローバルでなく、ローカルにインストールする場合は以下のコマンドを実行します。

```bash
npm i -D marked
```

## CLI の使い方

ローカルにインストールした場合は以下のように実行します。

```bash
npx marked -o sample.html
```

md ファイルの書き出し

```
echo "# Hello" > sample.md
```

## 使えるオプション

| オプション | 概要                                               | 例                         |
| ---------- | -------------------------------------------------- | -------------------------- |
| --help     | ヘルプ                                             | `npx marked --help`        |
| -o         | ファイル出力: 文字を打ち込む or ファイルインポート | `npx markd -o sample.html` |
| -i         | ファイルインポート: ファイルを指定して変換         | `npx marked -i sample.md`  |

## 実例

この README.md を HTML に変換したコマンド

```bash
npx marked -i README.md -o readme.html
```

## ブラウザに直接書き込む

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <title>Marked in the browser</title>
  </head>
  <body>
    <div id="content"></div>
    <script src="https://cdn.jsdelivr.net/npm/marked/marked.min.js"></script>
    <script>
      document.getElementById("content").innerHTML = marked.parse(
        "# Marked in the browser\n\nRendered by **marked**."
      );
    </script>
  </body>
</html>
```

```html
<script type="module">
  import { marked } from "https://cdn.jsdelivr.net/npm/marked/lib/marked.esm.js";
  document.getElementById("content").innerHTML = marked.parse(
    "# Marked in the browser\n\nRendered by **marked**."
  );
</script>
```

ファイルから読み取る場合

```html
<script type="module">
  import { marked } from "https://cdn.jsdelivr.net/npm/marked/lib/marked.esm.js";
  fetch("README.md")
    .then((response) => response.text())
    .then((text) => {
      document.getElementById("content").innerHTML = marked.parse(text);
    });
</script>
```
