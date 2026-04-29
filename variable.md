可変レイアウトのまとめ

## NGなスタイルの書き方

```style
    width:1366px;
```
widthを固定すると、画面サイズを変更したときに追従しません。
padding、 marginのpxはいいですが、コンテンツの横幅、縦幅を固定するような書き方はよくないです。

## box-sizing
box-sizingとは最新のCSS規格「CSS3」から追加されたプロパティです。このプロパティにより「要素の幅（width）と高さ（height）の中にpaddingとborderを含めるかどうか」という設定ができます。

https://saruwakakun.com/html-css/reference/box-sizing#google_vignette

## min-width
画面の横幅が大きいときは、横幅を小さくしておきたいが、画面が小さい場合は追従したい

```style
.box{
    min-width:1000px
}
```