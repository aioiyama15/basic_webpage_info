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


## max-width
max-widthは、コンテンツの横幅の最大の値を指定します。
画面の横幅が大きいときは、横幅を1000px等で固定します。1000pxより小さくなると、コンテンツの横幅が、画面に合わせて小さくなります。
```css
.box{
    max-width:1000px;
}
```
1200px -> 1000px

800px -> 800px
## min-height
最低限の高さを指定したいときに使う。

```css
.box{
    min-height:100vh;
}
.box{
    min-height:200px;
}
```
ウィンドウの高さ分を最低確保する場合は、100vhを使用します。

minが200pxの場合、


100px -> 200px

200px -> 200px

300px -> 300px 



## min maxの考え方

本来の描画サイズと指定したサイズを比べるcssです。
minは取りうる最小の値として指定されるようです。小さい方ではなく、最小値という意味だそうです。最小値よりも小さく描画される要素は、最小値の大きさで表示されます。
maxは取りうる最大の値です。


```css
.box{
    min-width:800px;
}
```
そのため、800になるまでは、元の横幅、それより小さくなると、800pxで固定されるようです。


## clamp
```css
.box{
    width: clamp(500px, 50%, 1500px);
}
```
三行バージョン
```css
.box{
    width:50%;
    min-width:500px;/*最小値*/
    max-width:1500px;/*最大値*/
}
```


## box-sizing
box-sizingとは最新のCSS規格「CSS3」から追加されたプロパティです。このプロパティにより「要素の幅（width）と高さ（height）の中にpaddingとborderを含めるかどうか」という設定ができます。

```css
#borderbox p {
  box-sizing: border-box;
}
```
https://saruwakakun.com/html-css/reference/box-sizing#google_vignette

## 単語の折り返し

```css
span.line-chunk {
    display: inline-block;
    overflow-wrap: anywhere;
    word-break: normal;
}

```

```html
<span class="line-chunk">
    <span class="line-chunk">文字列文字列文字列文字列</span>
    <span class="line-chunk">文字列文字列文字列</span>
</span>
```