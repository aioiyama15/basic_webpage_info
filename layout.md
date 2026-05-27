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


## リスト

手順を書くような場合のリストCSS



```css


 ul,
 li {
     font-size: pc(17);
     line-height: 2.0;
     //  list-style: inside;
     /* 先頭の黒点を消す */
     padding: 0;
     /* 内側の余白を消す */
     margin: 0;
     /* 外側の余白を消す */
 }


 .process {
     margin-left: pc(50px);
 }

 .process>li {
     position: relative;
 }

 .process>li::before {
     position: absolute;
     left: pc(-40);
     top: pc(5);
     width: pc(30);
     height: pc(30);
     display: grid;
     place-items: center;
     background-color: #005726;
     color: #fff;
     font-size: pc(20);
     content: "";
     line-height: 0;
     font-weight: bold;
 }

 .process>#process_num_1::before {
     content: "1";
 }

 .process>#process_num_2::before {
     content: "2";
 }

 /* spanの vertical-align は不要になるので削除かリセット */
 li>span {
     vertical-align: baseline;
 }

```

```html

 <ul class="process">
    <li id="process_num_1">
        <h3>サンプル</h3>
        <p>サンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプル
        </p>
    </li>
    <li id="process_num_2">
        <h3>サンプル</h3>
        <p>サンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプル
        </p>
        <h3>サンプルサンプルサンプルサンプルサンプルサンプルサンプル</h3>
        <p>サンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプル
        </p>
        
        <div class="signal_list" style="display: flex;">
            <ul>
                <li class="green_list"><span>サンプル</span></li>
                <li class="green_list"><span>サンプル</span></li>
                <li class="green_list"><span>サンプル</span></li>
                <li class="green_list"><span>サンプル</span></li>
            </ul>
            <ul>
                <li class="green_list"><span>サンプル</span></li>
                <li class="green_list"><span>サンプル</span></li>
                <li class="green_list"><span>サンプル</span></li>
            </ul>
        </div>
        <p>サンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプル
        </p>

        <h3>サンプルサンプルサンプル</h3>
        <p>サンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプルサンプル
        </p>
    </li>

</ul>

```