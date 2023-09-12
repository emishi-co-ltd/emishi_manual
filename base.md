# 【ベース】エミシコーディング規約

## ファイル命名規則

| 言語 | ケース | 用例 |
|-----------|-----------|-----------|
| HTML,CSS | ケバブケース | kebab-case |
| JavaScript | キャメルケース | camelCase |
| PHP | スネークケース | snake_case |

WordPressなどのCMSやフレームワーク内では、その規定に従う。

### SCSSについて

FLOCSS に従い作成している場合、コンパイルしないファイルの先頭にアンダースコア(_)をつけること。
また、それぞれのレイヤーの頭文字を接頭辞としてつけること。
(例) l-header の場合 「_l-header.scss」とする。

それ以外の場合、ケバブケースを用いること。

## プロジェクトの構成

ファイル構成は以下を推奨します。

``` -
public_html
├─ assets
│  ├─ css
│  ├─ fonts
│  ├─ images
│  ├─ inc
│  ├─ js
│  ├─ libs
│  └─ vendor
├─ src
│  ├─ assets
│  │  ├─ scss
│  │  ├─ images
│  │  ├─ js
│  │  └─ vendor
│  ├─ node_modules
│  ├─ package-lock.json
│  ├─ package.json
│  └─ webpack.config.js
├─ index.html
├─ ...
├─ .gitignore
```
