外部CSSの読み込みと使用のサンプル
```sass

@use "sass:meta";
@use "sass:math";
@use "variables"; // 読み込み

@function strip-unit($value) {
    @if meta.type-of($value)=="number" and not math.is-unitless($value) {
        @return math.div($value, $value * 0 + 1);
    }

    @return $value;
}

// 修正: variables.$breakpoint-pc に変更
@function pc($value, $base: variables.$breakpoint-pc) {
    @return calc(#{strip-unit($value)} / #{strip-unit($base)} * 100vw);
}

// 修正: variables.$breakpoint-sp に変更
@function sp($value, $base: variables.$breakpoint-sp) {
    @return calc(#{strip-unit($value)} / #{strip-unit($base)} * 100vw);
}
```