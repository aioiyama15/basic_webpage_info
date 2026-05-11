ウィンドウのリサイズ中に何度も処理が走り、ガクついたり重くなったりする現象（チャタリング）を解決するには、「デバウンス（Debounce）」という手法が非常に有効です。

リサイズが終わるのを待ってから1回だけ処理を実行する仕組みを、HTML/CSS/JSのセットで解説します。

---

### 1. サンプルコード

このコードは、リサイズが止まってから **500ms（0.5秒）** 経過したタイミングで、背景色を変更するデモです。

#### HTML

```html

<div id="status">ウィンドウをリサイズしてみてください</div>
<p>現在のサイズ: <span id="size-display">---</span></p>

```

#### JavaScript

```javascript
// 実行したいメインの処理
function updateLayout() {
  const width = window.innerWidth;
  const height = window.innerHeight;
  
  document.getElementById('size-display').innerText = `${width}px × ${height}px`;
  document.body.style.backgroundColor = '#e0f7fa'; // 確定時に色を変える
  console.log('レイアウト更新完了！');
}

// デバウンス関数：特定の時間、呼び出しがなければ実行する
function debounce(func, delay) {
  let timer;
  return function() {
    // 実行前にタイマーをクリア（リサイズ中はずっとクリアされ続ける）
    clearTimeout(timer);
    
    // 指定時間後に実行するように予約
    timer = setTimeout(() => {
      func.apply(this, arguments);
    }, delay);
  };
}

// 0.5秒待機するデバウンス済みのイベントリスナーを登録
window.addEventListener('resize', debounce(() => {
  document.body.style.backgroundColor = '#ffc107'; // リサイズ中の色
  updateLayout();
}, 500));

```

---

### 2. 仕組みの図解

通常の `resize` イベントは、1秒間に数十回発生するため、その都度重い計算（DOM操作など）を行うと画面が「ちらつき」ます。デバウンスを入れることで、以下のように制御されます。

* **リサイズ開始:** タイマーがセットされる。
* **連続リサイズ中:** 前のタイマーが破棄され、新しいタイマーがセットし直される（＝実行されない）。
* **リサイズ停止:** 最後にセットされたタイマーが **0.5秒間破棄されず** に残る。
* **実行:** 0.5秒経過後、ようやく `updateLayout` が呼ばれる。

---

### 3. CSSでの補足（よりスムーズにするために）

JavaScriptでの処理だけでなく、CSSの `transition` を併用すると、数値の変化がより滑らかに見え、ユーザーに「ちらつき」を感じさせない工夫ができます。

```css
body {
  transition: background-color 0.3s ease; /* 色の変化をふわっとさせる */
}

#status {
  padding: 20px;
  font-weight: bold;
  font-size: 1.2rem;
}

```

### まとめ

* **`clearTimeout`** で前の予約をキャンセルするのが肝。
* **`setTimeout`** で「最後の1回」を待つ。
* 待機時間は、今回のご要望に合わせて `500` (ms) に設定しています。

この仕組みは、ウィンドウのリサイズだけでなく、**検索フォームの入力（インクリメンタルサーチ）** などでもよく使われる非常に重要なテクニックですよ！