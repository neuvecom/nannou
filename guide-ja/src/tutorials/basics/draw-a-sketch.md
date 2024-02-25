<!-- # Draw a Sketch -->
# スケッチを描く

<!-- **Tutorial Info** -->
**チュートリアル情報**
- 著者: tpltnt
- 必要な知識:
    - [はじめに](/getting_started.md)
- 読書時間：5分

---


<!-- **Nannou is a framework for creative coding in Rust.** A framework can be thought of as a collection of building blocks to help accomplish a goal.
A sketch is the smallest/fastest way to get results with nannou.
Here is one example which just yields a blue window: -->
**NannouはRustでクリエイティブコーディングするためのフレームワークです。** フレームワークは、ある目標を達成するためのビルディング・ブロックの集合体と考えることができる。
スケッチは、nannouで結果を得るための最も小さく、最も速い方法です。
ここでは、青いウィンドウを生成する例を示します：

```rust,no_run
use nannou::prelude::*;

fn main() {
    nannou::sketch(view).run();
}

fn view(app: &App, frame: Frame) {
    // get canvas to draw on
    let draw = app.draw();

    // set background to blue
    draw.background().color(BLUE);

    // put everything on the frame
    draw.to_frame(app, &frame).unwrap();
}
```

<!-- You can exit the sketch by pressing `ESC`. -->
`ESC`を押すとスケッチを終了できます。

<!-- ## Explaining the Code -->
## コードの説明

<!-- A sketch consists of at least two functions: `main()` and `view()`.
First we import some building blocks: -->
スケッチは少なくとも2つの関数から構成される：`main()`と `view()`である。
まず、いくつかの構成要素をインポートする：

```rust,no_run
# #![allow(unused_imports)]
use nannou::prelude::*;
# fn main() {}
```

<!-- After this import the actual sketching code starts. The `main()` functions is where all your logic starts. The code -->
このインポートの後、実際のスケッチ・コードが始まります。`main()`関数がすべてのロジックの始まりです。そのコード

```rust,no_run
# use nannou::prelude::*;
#
# fn main() {
    nannou::sketch(view).run();
# }
# fn view(_app: &App, _frame: Frame) {}
```

<!-- calls a function to draw on the single window (`view()` in this case). This function has the signature `fn(_: &App, _: Frame);`. Don't worry if you don't know what a function signature is. Just copy the `main()` function and you will be fine. -->
この関数は、単一のウィンドウ（ここでは `view()`）に描画するための関数を呼び出します。この関数は `fn(_: &App, _: Frame);` というシグネチャを持っています。関数のシグネチャが分からなくても心配しないでください。`main()`関数をコピーすれば大丈夫です。

<!-- Within the view() function, what we draw to the Frame will be presented in our window. -->
view()関数の中では、Frameに描画したものがウィンドウに表示されます。

```rust,no_run
# #![allow(unused_imports)]
# use nannou::prelude::*;
# fn main() {
#    nannou::sketch(view).run();
# }
fn view(app: &App, frame: Frame) {
    let draw = app.draw();

    draw.background().color(BLUE);

    draw.to_frame(app, &frame).unwrap();
}
```

<!-- This function follows the same scheme. First some setup is done. The line -->
この関数も同じスキームに従う。最初にいくつかのセットアップが行われる。その行

```rust,no_run
# #![allow(unused_imports, unused_variables)]
# use nannou::prelude::*;
# fn main() {
#    nannou::sketch(view).run();
# }
# fn view(app: &App, _frame: Frame) {
let draw = app.draw();
# }
```

<!-- lets us assign a canvas-like datatype to the variable `draw`.
We can now paint on the this canvas by setting the background to blue. -->
変数 `draw` にキャンバスのようなデータ型を代入することができる。
背景を青に設定することで、このキャンバスに絵を描くことができる。

```rust,no_run
# #![allow(unused_imports)]
# use nannou::prelude::*;
# fn main() {
#    nannou::sketch(view).run();
# }
# fn view(app: &App, _frame: Frame) {
# let draw = app.draw();
draw.background().color(BLUE);
# }
```

<!-- Now we have a canvas with only a blue background. We take this canvas and create a computer graphics frame from it to display in the main window. -->
これで青い背景だけのキャンバスができた。このキャンバスからCGフレームを作り、メイン・ウィンドウに表示する。

```rust,no_run
# #![allow(unused_imports)]
# use nannou::prelude::*;
# fn main() {
#    nannou::sketch(view).run();
# }
# fn view(app: &App, frame: Frame) {
# let draw = app.draw();
draw.to_frame(app, &frame).unwrap();
# }
```

<!-- If you find the desire to respond to other kinds of events, interact with other kinds of input/output, track some state, or need more flexibility in general, you might be interested in creating a [nannou app](./anatomy-of-a-nannou-app.md) instead! You can also learn more about the difference between sketches and apps [here](./sketch-vs-app.md). -->
他の種類のイベントに反応したい、他の種類の入出力とやりとりしたい、状態を追跡したい、一般的にもっと柔軟性が必要だ、という場合は、代わりに[nannouアプリ](./anatomy-of-a-nannou-app.md)を作成することに興味があるかもしれません！また、スケッチとアプリの違いについては[こちら](./sketch-vs-app.md)を参照してください。
