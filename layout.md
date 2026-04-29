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

