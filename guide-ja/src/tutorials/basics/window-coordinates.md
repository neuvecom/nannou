<!-- # Basics - Window Coordinates -->
# 基本 - ウィンドウの座標

<!-- **Tutorial Info** -->
**チュートリアル情報**

- 著者: mitchmindtree
- 必要な知識:
    - [はじめに](/getting_started.md)
- 読書時間：15分

---

<!-- **Coordinates** can be used to describe a position in space. Before we start drawing things in certain locations within our window, or animating them to move in certain directions, it can be very useful to understand the **coordinate system** that we are working with. -->
**座標**は空間内の位置を表すのに使われます。ウィンドウ内の特定の位置にものを描いたり、特定の方向に動くようにアニメートしたりする前に、扱っている**座標系**を理解しておくと非常に便利です。

<!-- Different kinds of coordinate systems are useful for different purposes. Let's take a look at nannou's **window coordinates**. -->
さまざまな種類の座標系は、さまざまな目的に役立つ。nannouの**窓座標**を見てみよう。

![window_coordinates.rs][3]

<!-- This is a screenshot of the [`window_coordinates.rs` example][2]. The example aims to help develop an intuition for how nannou's window coordinates work. In this case, we are presented with a window whose size is 600x400. We can see that: -->
これは[`window_coordinates.rs` example][2]のスクリーンショットである。この例題は、nannouのウィンドウ座標がどのように機能するかの直感を養うことを目的としている。この例では、サイズが600x400のウィンドウが表示されています。これを見ると

<!-- - The **x** and **y** values are **`[0.0, 0.0]`** in the **centre** of the window. This is called the *origin*.
- The **x** value **increases towards the right** and **decreases towards the left**.
- The **y** value **increases upwards** and **decreases downwards**.
- The distance from the left edge to the right edge is 600, equal to the window width.
- The distance from the bottom edge to the top edge is 400, equal to the window height.
- The distance from the centre to the left or right edge is 300, or half the window width.
- The distance from the centre to the top or bottom edge is 200, or half the window height. -->
- **x**と**y**の値はウィンドウの**中心**の**`[0.0, 0.0]`**です。これは*原点*と呼ばれます。
- **x**値は**右に向かって増加**し、**左に向かって減少**します。
- **y**値は**上方向に増加し**、**下方向に減少**します。
- 左端から右端までの距離は600であり、ウィンドウ幅に等しい。
- 下端から上端までの距離は400で、ウィンドウの高さに等しい。
- 中央から左端または右端までの距離は300で、ウィンドウ幅の半分です。
- 中央から上端または下端までの距離は200で、ウィンドウの高さの半分に相当する。

<!-- In other words, nannou uses a [Cartesian coordinate system][4] to describe window space, where the origin is in the centre, *y* increases upwards and the distance between the edges of the window are equal to the size of the window. -->
言い換えれば、nannouはウィンドウ空間を記述するために[デカルト座標系][4]を使用しており、原点は中心にあり、*y*は上方に増加し、ウィンドウの端間の距離はウィンドウのサイズに等しい。

<!-- ## Drawing in Window Coordinates -->
## ウィンドウ座標で描画

<!-- Having the origin in the centre is a theme that carries through to the way that we draw shapes with nannou's [`draw` API][20]. Let's see what happens if we change the example to draw a plum colored square at `[0.0, 0.0]` and with a size of `100.0`. -->
原点を中心に置くことは、nannouの[`draw` API][20]を使った図形の描き方にも通じるテーマだ。例えば、梅色の正方形を `[0.0, 0.0]` の位置に `100.0`の大きさで描くとどうなるか見てみよう。

```rust,no_run
# #![allow(unreachable_code, unused_variables)]
# use nannou::prelude::*;
# fn main() {
#     let draw: Draw = unimplemented!();
draw.rect()
    .x_y(0.0, 0.0)
    .w_h(100.0, 100.0)
    .color(PLUM);
# }
```

![window_coordinates.rs][5]

<!-- Notice that when we say `.x_y(0.0, 0.0)`, this refers to where the **centre** of the square will be placed. You might notice the same applies to other drawing primitives like ellipse and text. -->
`.x_y(0.0,0.0)`というのは、正方形の**中心**がどこに置かれるかを示していることに注意してください。楕円やテキストのような他の描画プリミティブも同じであることにお気づきでしょう。

<!-- ### Rotating the square -->
### 正方形の回転

<!-- This property of describing positions via the centre allows for performing all kinds of symmetrical operations with ease. Rotations are a nice example of this. Let's try rotating our plum square by 45 degrees. -->
中心を経由して位置を記述するというこの性質により、あらゆる種類の対称操作を簡単に実行できる。回転はその好例である。プラムの正方形を45度回転させてみよう。

```rust,no_run
# #![allow(unreachable_code, unused_variables)]
# use nannou::prelude::*;
# fn main() {
#     let draw: Draw = unimplemented!();
draw.rect()
    .x_y(0.0, 0.0)
    .w_h(100.0, 100.0)
    .z_degrees(45.0)
    .color(PLUM);
# }
```

![window_coordinates.rs][6]

<!-- Voila! -->
それだけだ！

<!-- ### Moving the square -->
### 正方形の移動

<!-- OK, now let's remove our rotation and try positioning the square so that the bottom left corner touches the origin while the top right corner touches the `[100.0, 100.0]` marker. -->
では、回転を外して、左下が原点に接し、右上が`[100.0, 100.0]`マーカーに接するように正方形を配置してみましょう。

<!-- In order to do this, we want to move the square so that it is halfway between the origin and the marker, so `[50.0, 50.0]`. -->
そのためには、原点とマーカーの中間になるように正方形を移動させたい。 `[50.0, 50.0]`

```rust,no_run
# #![allow(unreachable_code, unused_variables)]
# use nannou::prelude::*;
# fn main() {
#     let draw: Draw = unimplemented!();
draw.rect()
    .x_y(50.0, 50.0)
    .w_h(100.0, 100.0)
    .color(PLUM);
# }
```

![window_coordinates.rs][7]

<!-- So satisfying! -->
とても満足している！

<!-- *OK, but what if we want to position our square in the top-left corner of the window?* -->
*しかし、正方形をウィンドウの左上隅に配置したい場合はどうすればいいでしょうか？*

<!-- One approach would be to calculate the position by hand. For example, we know the top-left corner is equal to [-300, 200]. From there, we need to move the square to the right by half the width and down by half the height: -->
一つの方法は、手で位置を計算することである。例えば、左上の角は[-300, 200]に等しいことが分かっている。そこから、正方形を幅の半分だけ右に、高さの半分だけ下に移動させる必要がある：

```rust,no_run
# #![allow(unreachable_code, unused_variables)]
# use nannou::prelude::*;
# fn main() {
#     let draw: Draw = unimplemented!();
let side = 100.0;
let top_left = pt2(-300.0, 200.0);
let offset = vec2(side / 2.0, -side / 2.0);
let xy = top_left + offset;
draw.rect()
    .xy(xy)
    .w_h(side, side)
    .color(PLUM);
# }
```

![window_coordinates.rs][8]

<!-- OK that worked! But it was a **lot** of effort. And what if the size of the window changes? -->
よし、うまくいった！でも、かなりの労力だった。ウィンドウの大きさが変わったらどうする？

<!-- Enter, **`Rect`**. -->
`Rect` を入力してください。

<!-- ## Positioning with `Rect` -->
## `Rect` による位置決め

<!-- One of the most useful tools for working in window coordinates is [the `Rect` type][9]. As the name suggests, `Rect` allows us to work with rectangles in a variety of useful ways. We can [align][10] them, [pad][11] them, [shift][12] them, [stretch][13] them, [subdivide][14] them, check if they [contain a point][15] and more. -->
ウィンドウ座標で作業するための最も便利なツールの1つが[`Rect`型][9]である。その名前が示すように、`Rect`は矩形を様々な便利な方法で扱うことができる。整列][10]、[パッド][11]、[シフト][12]、[ストレッチ][13]、[細分化][14]、[点を含むかどうかのチェック][15]などができる。

<!-- One of the most useful applications of `Rect` is for describing the bounds of the window. Let's retrieve the window `Rect` with the name `win`. -->
`Rect`の最も便利な用途の一つは、ウィンドウの境界を記述することである。ウィンドウ `Rect` を `win` という名前で取得してみよう。

```rust,no_run
# #![allow(unreachable_code, unused_variables)]
# use nannou::prelude::*;
# fn main() {
#     let app: App = unimplemented!();
let win = app.window_rect();
# }
```

<!-- Let's use `win` to simplify aligning our plum square to the top left of the window. -->
ウインドウの左上に梅の正方形を揃えるのを簡単にするために、`win`を使ってみよう。

<!-- ### Alignment -->
### アライメント

<!-- First, let's make a `Rect` that represents the position and size of our plum square and call it `r`. -->
まず、梅色の正方形の位置と大きさを表す `Rect` を作り、それを `r` と呼ぶことにしよう。

```rust,no_run
# #![allow(unused_variables)]
# use nannou::prelude::*;
# fn main() {
let r = Rect::from_w_h(100.0, 100.0);
# }
```

<!-- `r` now represents our square, positioned at [0.0, 0.0] with a width and height of 100.0. We can confirm this by changing our square drawing code to use `r` like so: -->
`r`は正方形を表し、[0.0, 0.0]に位置し、幅と高さは100.0である。このことは、正方形の描画コードを `r` を使うように変更することで確認できる：

```rust,no_run
# #![allow(unreachable_code, unused_variables)]
# use nannou::prelude::*;
# fn main() {
#     let draw: Draw = unimplemented!();
let r = Rect::from_w_h(100.0f32, 100.0f32);
draw.rect()
    .xy(r.xy())
    .wh(r.wh())
    .color(PLUM);
# }
```

![window_coordinates.rs][5]

<!-- We can align our plum square to the `top_left_of` the window like so: -->
梅色の正方形をウィンドウの`top_left_of`に合わせるには次のようにする：

```rust,no_run
# #![allow(unreachable_code, unused_variables)]
# use nannou::prelude::*;
# fn main() {
#     let draw: Draw = unimplemented!();
#     let win: Rect = unimplemented!();
let r = Rect::from_w_h(100.0, 100.0).top_left_of(win);
draw.rect()
    .xy(r.xy())
    .wh(r.wh())
    .color(PLUM);
# }
```

![window_coordinates.rs][8]

<!-- Much nicer! -->
ずっといい！

<!-- *But what if we want some padding between the edges of the window and the　square?* -->
*しかし、ウィンドウの端と正方形の間にパディングが必要な場合はどうするのですか？

<!-- Let's take a look! -->
見てみよう！

### Padding

<!-- We can use padding to add some space between the edges of an area and the content within it. In nannou, we can use the `pad` method to produce a padded instance of a `Rect`. -->
パディングを使うと、領域の端とその中にあるコンテンツの間にスペースを追加することができる。nannouでは、`pad`メソッドを使ってパディングされた`Rect`のインスタンスを生成することができる。

<!-- Let's try padding the window rect by `25.0` and drawing it with a semi-transparent blue color: -->
ウィンドウの矩形を`25.0`だけパディングして、半透明の青色で描いてみよう：

```rust,no_run
# #![allow(unreachable_code, unused_variables)]
# use nannou::prelude::*;
# fn main() {
#     let draw: Draw = unimplemented!();
#     let win: Rect = unimplemented!();
let win_p = win.pad(25.0);
draw.rect()
    .xy(win_p.xy())
    .wh(win_p.wh())
    .color(rgba(0.3, 0.4, 0.7, 0.5));
# }
```

![window_coordinates.rs][16]

<!-- As you may have guessed, we can use this new padded `Rect` to align our plum square and achieve the desired look: -->
ご想像のとおり、この新しいパディングされた`Rect`を使って、梅の正方形を整列させ、望ましい外観を得ることができる：

```rust,no_run
# #![allow(unreachable_code, unused_variables)]
# use nannou::prelude::*;
# fn main() {
#     let draw: Draw = unimplemented!();
#     let win: Rect = unimplemented!();
let win_p = win.pad(25.0);
let r = Rect::from_w_h(100.0, 100.0).top_left_of(win_p);
draw.rect()
    .xy(r.xy())
    .wh(r.wh())
    .color(PLUM);
# }
```

![window_coordinates.rs][17]

<!-- ### Relative Positions -->
### 相対ポジション

<!-- Now that we have our plum square situated with some nice padding in the top left corner, let's try drawing a salmon colored circle with the same size right below it. -->
梅色の正方形が左上隅にきれいにパディングされたので、そのすぐ下に同じ大きさのサーモン色の円を描いてみよう。

<!-- Our handy `Rect` type provides methods for positioning `below`, `above`, `left_of` and `right_of` another `Rect`. Let's use the `below` method on a copy of the square's `Rect` so that we can use the resulting `Rect` to draw our circle: -->
この便利な `Rect` 型には、別の `Rect` の `below`、`above`、`left_of`、`right_of` に配置するためのメソッドが用意されています。それでは、正方形の `Rect` のコピーに対して `below` メソッドを使ってみよう：

```rust,no_run
# #![allow(unreachable_code, unused_variables)]
# use nannou::prelude::*;
# fn main() {
#     let draw: Draw = unimplemented!();
#     let win: Rect = unimplemented!();
let win_p = win.pad(25.0);
let square = Rect::from_w_h(100.0, 100.0).top_left_of(win_p);
draw.rect()
    .xy(square.xy())
    .wh(square.wh())
    .color(PLUM);

let circle = square.below(square);
draw.ellipse()
    .xy(circle.xy())
    .wh(circle.wh())
    .color(SALMON);
# }
```

![window_coordinates.rs][18]

<!-- For consistency, let's try and add the same padding between the circle and the square as we have between the square and the edges of the window. -->
一貫性を保つため、円と正方形の間に、正方形とウィンドウの端の間にあるのと同じパディングを追加してみましょう。

<!-- We can do so by using the `shift` method to "shift" the circle down from the square: -->
そのためには、`shift`メソッドを使って、円を正方形から下に「ずらす」：

```rust,no_run
# #![allow(unreachable_code, unused_variables)]
# use nannou::prelude::*;
# fn main() {
#     let draw: Draw = unimplemented!();
#     let win: Rect = unimplemented!();
let pad = 25.0;
let win_p = win.pad(pad);
let square = Rect::from_w_h(100.0, 100.0).top_left_of(win_p);
draw.rect()
    .xy(square.xy())
    .wh(square.wh())
    .color(PLUM);

let circle = square.below(square).shift_y(-pad);
draw.ellipse()
    .xy(circle.xy())
    .wh(circle.wh())
    .color(SALMON);
# }
```

![window_coordinates.rs][19]

<!-- *Gee wizz, I love salmon!* -->
*私はサーモンが大好きなんだ。*

<!-- There are many more fancy tricks we can do with `Rect` to assist as a guide for laying out our sketches. I'm already getting carried away, so I'll leave it as an exercise to the reader to check out [the `Rect` docs][9] and explore! -->
スケッチをレイアウトするためのガイドとして `Rect` を使うと、もっとたくさんの派手なトリックができる。私はすでに夢中になっているので、読者の皆さんは[`Rect`のドキュメント][9]をチェックし、探求する練習として残しておこう！

<!-- Before we bring this tutorial to a close, let's take a quick look at what we really mean by all these numbers. -->
このチュートリアルを終える前に、これらの数字が意味するところを簡単に見ておこう。

<!-- ## Points and Pixels -->
## 点と画素

<!-- *What exactly does 600x400 measure? Millimetres? Pixels? Something else?* -->
*600x400の正確なサイズは？ ミリメートル？ ピクセル？ 他の何か？*

<!-- In nannou, we generally describe positions within window space in **points**. Points are very similar to **pixels**, except that points allow us to work without having to worry about the "scale factor" of our display. -->
nannouでは通常、ウィンドウ空間内の位置を**ポイント**で表します。ポイントは**ピクセル**とよく似ているが、ポイントではディスプレイの「スケールファクター」を気にすることなく作業できる点が異なる。

> ***待って、"スケールファクター"って何？***
>
> **スケールファクター**は、ディスプレイ上のピクセルの密度を推論するのに役立つ。現代のディスプレイは、解像度とサイズの間に一貫した関係がない。例えば、最近の携帯電話は最大1440pの解像度を誇り、画面の大きさは数分の1であるにもかかわらず、平均的な1080pのデスクトップモニターよりも大きい！
>
> このため、ほとんどのデバイスは**スケールファクター**を公開しています。この値は、デバイス間で一貫したユーザー体験を可能にするために適用されるべき推奨UIスケーリングを記述します。nannouでは、このスケーリングされた空間を*ポイント*（別名*論理ピクセル*）と呼び、*物理*ピクセル空間を*ピクセル*と呼びます。*ポイント*で作業することで、nannouにスケーリングを任せることができます。
>
> ウィンドウの拡大縮小がどのように機能するかについては、nannouのウィンドウ・ライブラリ[こちら][1]で詳しく説明されている。
>
> ポイントからピクセルに変換するには、スケールファクターを掛けることができる：
>
> ```rust,no_run
> # #![allow(unreachable_code, unused_variables)]
> # use nannou::prelude::*;
> # fn main() {
> #     let points = 100.0;
> #     let window: Window = unimplemented!();
> let pixels = points * window.scale_factor();
> # }
> ```
>
> 同様に、スケールファクターで割ることでピクセルをポイントに変換できる：
>
> ```rust,no_run
> # #![allow(unreachable_code, unused_variables)]
> # use nannou::prelude::*;
> # fn main() {
> #     let pixels = 100.0;
> #     let window: Window = unimplemented!();
> let points = pixels / window.scale_factor();
> # }
> ```

<!-- ## Conclusion -->
## 結論

<!-- Thanks for reading! Hopefully this has helped to demystify window coordinates in nannou at least a little. -->
お読みいただきありがとうございました！これでnannouのwindow座標について少しは理解できただろうか。

<!-- Remember, the more you experiment and play, the more these things become second nature. Next thing you know you will start seeing everything in window coordinates! -->
実験して遊べば遊ぶほど、こうしたことが自然にできるようになることを覚えておいてほしい。気がつけば、すべてをウィンドウ座標で見るようになっているはずだ！

[1]: https://docs.rs/winit/latest/winit/dpi/index.html
[2]: https://github.com/nannou-org/nannou/tree/master/examples/nannou_basics/window_coordinates.rs
[3]: ./images/window_coordinates_example.png
[4]: https://en.wikipedia.org/wiki/Cartesian_coordinate_system
[5]: ./images/window_coordinates_example2.png
[6]: ./images/window_coordinates_example3.png
[7]: ./images/window_coordinates_example4.png
[8]: ./images/window_coordinates_example5.png
[9]: https://docs.rs/nannou/latest/nannou/geom/rect/struct.Rect.html
[10]: https://docs.rs/nannou/latest/nannou/geom/rect/struct.Rect.html#method.align_left_of
[11]: https://docs.rs/nannou/latest/nannou/geom/rect/struct.Rect.html#method.pad
[12]: https://docs.rs/nannou/latest/nannou/geom/rect/struct.Rect.html#method.shift
[13]: https://docs.rs/nannou/latest/nannou/geom/rect/struct.Rect.html#method.stretch_to_point
[14]: https://docs.rs/nannou/latest/nannou/geom/rect/struct.Rect.html#method.subdivisions_iter
[15]: https://docs.rs/nannou/latest/nannou/geom/rect/struct.Rect.html#method.contains
[16]: ./images/window_coordinates_example6.png
[17]: ./images/window_coordinates_example7.png
[18]: ./images/window_coordinates_example8.png
[19]: ./images/window_coordinates_example9.png
[20]: https://guide.nannou.cc/tutorials.html#drawing
