可変レイアウトのまとめ

## NGなスタイルの書き方

```css
.box{
    width:1366px;
}
   
```



widthを固定すると、画面サイズを変更したときに追従しません。
padding、 marginのpxはいいですが、コンテンツの横幅、縦幅を固定するような書き方はよくないです。

## 正しい書き方

## box-sizing
box-sizingとは最新のCSS規格「CSS3」から追加されたプロパティです。このプロパティにより「要素の幅（width）と高さ（height）の中にpaddingとborderを含めるかどうか」という設定ができます。

```css
#borderbox p {
  box-sizing: border-box;
}
```
https://saruwakakun.com/html-css/reference/box-sizing#google_vignette


## min maxの考え方

max minは、二つの値の大きい方か小さいほうのどちらかをとれるオプションです。
min-widthのcssの場合は、片方の値が、通常描画される要素のサイズになります。
もう一つが、指定した値です。

minは取りうる最小の値として指定されるようです。小さい方ではなく、最小値という意味だそうです。

```css
.box{
    min-width:800px
}
```
そのため、800になるまでは、元の値、それより小さくなると、800pxで固定されるようです。


## max-width
取りうる最大値を設定します。
画面の横幅が大きいときは、横幅を固定おきたいが、画面が小さい場合は追従したい

```css
.box{
    max-width:1000px
}
```
## min-height
最低限の高さを得るときに使用。

```css
.box{
    min-height:100vh;
}
.box{
    min-height:200px;
}
```
ウィンドウの高さ分は最低確保する場合は、100vhを使用します。
