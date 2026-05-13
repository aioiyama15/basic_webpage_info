# レイアウトの基本

## 中央ぞろえ

## 方法1
div要素は、横幅いっぱいに要素サイズが指定されているので、
```css
.box{
    width: fit-content;
}
```
これは、spanタグと同じです。もともとspanを使用した場合、これは必要ありません。

widthをコンテンツ要素のサイズに固定し、
```css
.box{
    margin: 0 auto;
}
```

で中央ぞろえできます。
## 方法2
inline要素のみ（div等）
```css
.box{
    text-align: center;
}
```
でdiv内の要素を中央にできます。

## 横ならべの手法

```css
.box{
    display:flex;
}
```
が基本。
二つの要素を横に並べるときに、中央に空の要素を挟んでおくとレイアウトしやすい。padding を親要素にかけたときに、同一の空白を中の要素にかけることが難しい。

左の要素（写真など）の右に空白をつけるだけだと、左右を入れ替えるとレイアウトだと破綻する。

中央に空の要素を入れることでこの問題を解決できる。


```md
[　写真　]　[空白div] [文字要素]
[文字要素]　[空白div] [　写真　]
```
入れ替わりのないレイアウトには不要。

## 枠の中にスライドを作成するテクニック

### 概要
- 枠、スライダーを重ねる
- 枠とスライドのサイズを一緒に変化させる
- スライドの中の画像サイズが違う場合でも同じ枠の中に画像をキレイに表示する。

以下のCSSのよってそれを実現する。
```css
.main_section .swiper,
.main_section .swiper-wrapper,
.main_section .swiper-slide {
  width: 100%;
  aspect-ratio: 16/9;
}

.frame {
  width: 100%;
  aspect-ratio: 16/9;
  position: absolute;
  top: 0;
  left: 0;
  pointer-events: none;
  z-index: 2;

}


.main_section .swiper-slide img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

```

aspect-ratio によって、画像の縦横比率を保つ。
タブレットとスマホは、画像サイズをそのまま参照している。
比率なので、画像のpx数をそのまま書いても問題ないです。