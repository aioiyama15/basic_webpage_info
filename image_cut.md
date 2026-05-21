# 写真の切り取り 

## object-fit:

  ### cover;
  親要素のサイズいっぱいに画像が表示される
  親要素に隙間がないように表示されるので、画像の端が一部見えなくなる。
  画像の比率を一定に保つときに使用する。
  ```css
  .sample_box{
    object-fit: cover;
  }
  ```

  ### contain;
  親要素のサイズの中で画像が隠れない最大サイズで表示される。
  画像全体を表示したいときに使用する。

  ```css
  .sample_box{
    object-fit: contain;
  }
  ```
.

.

.


## 切り取りを細かく制御する

object-fit:coverでは、アスペクト比を指定していい感じに切り取ってもらえます。しかし「　右端で切り取る　」や、「　中央を小さく　」、「　中央少し下　」のような指定ができません。

そこで、absolute とその他CSSを組み合わせることで調整を可能にしたコードを作成しました。
以下のコードは画像の中央少し上部を中心に指定したサイズで切り取るというコードになります。

HTML
```html
    <div class="staff">
        <div class="staff_image">
            <img src="./img/sampleple.jpg" alt="スタッフ1">
        </div>
        <p class="staff_name">スタッフ1</p>
        <p class="staff_title">スタッフ1の説明文がここに入ります。</p>
    </div>
```

CSS
```css
    .staff {
        .staff_image {
            position: relative;
            width: 20vw;
            height: 30vw;
            overflow: hidden;
        }

        img {
            position: absolute;
            top: 70%;
            left: 50%;
            transform: translate(-50%, -50%);
            display: block;
            width: 140%;
            height: auto;
        }
    }
```