# 【CSS 編】FLOCSS（フロックス）を使った CSS 設計

## 参考

[FLOCSS 公式](https://github.com/hiloki/flocss)
[【CSS 設計】FLOCSS(フロックス)で保守性の高い記述を極める！](https://tane-be.co.jp/knowledge/web-design/2270/)

## FLOCSS の基本原則

FLOCSS は次の*3 つのレイヤー*と、*Object レイヤーの子レイヤー*で構成されます。

```-
scss
├─ Foundation
├─ Layout
└─ Object
   ├─ Component
   ├─ Project
   └─ Utility
```

> [!TIP]
>
> Foundation: ベースとなる CSS やリセット CSS など
> Layout: ヘッダーやフッター、共通で使用するレイアウト部分の CSS
> Component: 共通で使用したいパーツ部分の CSS
> Project: そのページのみで使用する部分のCSSなど
> Utility: わずかなスタイル調整のCSS

## エミシで使う FLOCSS

エミシでは FLOCSS の基本のレイヤーに加えて*global*レイヤーを加えて構成します。

```-
scss
├─ Global
├─ Foundation
├─ Layout
└─ Object
   ├─ Component
   ├─ Project
   └─ Utility
```

global は variables や mixins など、各scss ファイルで使うものをまとめておきます。  
実際に scss フォルダを作成する時は、以下のようになります。

```-
scss
├─ Global 
│  ├─ _g-functions.scss
│  ├─ _g-mixins.scss
│  ├─ _g-variables.scss
│  └─ _index.scss
├─ Foundation
│  ├─ _f-base.scss
│  ├─ _f-reset.scss
│  └─ _index.scss
├─ Layout
│  ├─ _l-header.scss
│  ├─ _l-footer.scss
│  ├─ ...
│  └─ _index.scss
└─ Object
   ├─ Component (共通で使用したい)
   ├─ Project (各ページごと)
   └─ Utility (わずかなスタイル調整)
```

## FLOCSS の基本的な class の書き方

- プレフィックス（接頭辞）をつける
- BEM の書き方を利用する

### プレフィックス（接頭辞）をつける

Layout には`l-`、Component には`c-`、Project には`p-`、Utility には`u-`というようにフォルダの頭文字を class に記述してください。  
共通パーツのボタンなら`c-btn`や、各ページの item なら`p-item`のようにしてください。

### BEM の書き方を利用する

BEM とは Blocks-Elements-Modifiers の略で、簡単にいうと親のブロック要素を引き継いで class 名を書くようなイメージです。

> [!TIP]
>
> - Block： 大枠となるブロック要素（section など）
> - Element： Block 中の要素（section 中の div など）
> - Modifier： Block や Element のスタイル（見た目や状態など）

例としては以下のようなイメージです。

```HTML: HTML
<section>
  <div class="p-home__content">
    <h2 class="p-home__content-title">
      <span class="p-home__content-title__icon"><img src="" alt="" /></span>
      <span class="p-home__content-title__text">タイトルが入ります</span>
    </h2>
    <p class="p-home__content-text -small">テキストが入ります</p>
    <p class="p-home__content-text -big">テキストが入ります</p>
  </div>
</section>
```

> [!IMPORTANT]
>
> Block と Element はアンダーバー(\_)2 つで区切る
> Element 以下の class 名はハイフン(-)1 つで区切る
> Modifier（色の変化や微妙にスタイルを変更したいスタイル） -small などの class を追加する

欠点として、名前が長くなりやすいので、なるべくアンダーバー(\_\_)は 2 箇所（塊が 3 つ）までにしてください。

NG: `p-home__content__title__icon`
OK: `p-home__content-title__icon`
