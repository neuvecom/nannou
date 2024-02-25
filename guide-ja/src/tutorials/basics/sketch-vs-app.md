<!-- # Basics - `sketch` vs `app` -->
# 基本 - `sketch` vs `app`

<!-- **Tutorial Info** -->
**チュートリアル情報**

- 著者: mitchmindtree
- 必要な知識:
    - [はじめに](/getting_started.md)
- 読書時間：7分

---

<!-- When creating a new nannou project we have two options for kicking off our program: -->
nannouの新しいプロジェクトを立ち上げる際、私たちには2つの選択肢がある：

1. `nannou::sketch`
2. `nannou::app`.

<!-- Let's find out exactly what the differences are! -->
何が違うのか、具体的に調べてみよう！

<!-- > **Note:** When referring to *app* throughout this tutorial, we are referring to a nannou project that is run via `nannou::app`. We are *not* referring to the `App` type that often appears as the first argument in nannou functions.
> Hopefully we can point to an `App` oriented tutorial some day soon! -->
> このチュートリアルで **app** と表記する場合は、`nannou::app` を介して実行される nannou プロジェクトを指します。`nannou::app` を介して実行される nannou プロジェクトを指しています。
> 近いうちに `App` 指向のチュートリアルを紹介できるといいですね！

<!-- ## Sketches -->
## スケッチ

<!-- **Sketches** are perfect for quick doodles and casual creations. They only require a simple `view` function designed to make it easy to start drawing quickly and easily. -->
**スケッチ**は、簡単な落書きや気軽な創作に最適です。簡単な`ビュー`機能だけで、素早く簡単に描き始めることができます。

<!-- Here is what the [sketch template](https://github.com/nannou-org/nannou/blob/master/examples/templates/template_sketch.rs) looks like: -->
[スケッチテンプレート](https://github.com/nannou-org/nannou/blob/master/examples/templates/template_sketch.rs)はこんな感じ：

```rust,no_run
use nannou::prelude::*;

fn main() {
    nannou::sketch(view).run()
}

fn view(app: &App, frame: Frame) {
    let draw = app.draw();
    draw.background().color(PLUM);
    draw.ellipse().color(STEELBLUE);
    draw.to_frame(app, &frame).unwrap();
}
```

<!-- While you cannot update or track any custom state, we still have access to plenty of fun inputs including time, the state of the keyboard, mouse and more. -->
カスタムの状態を更新したり追跡したりすることはできないが、時間やキーボード、マウスの状態など、楽しい入力にアクセスすることはできる。

<!-- ## Apps -->
## アプリ

<!-- **Apps** are better suited to more sophisticated artworks or even fully fledged applications. They allow for greater flexibility and finer grained control than sketches, but also require a little more setup. -->
**アプリケーション**は、より洗練されたアートワークや、本格的なアプリケーションに適しています。スケッチよりも柔軟性が高く、きめ細かいコントロールが可能ですが、セットアップも少し必要になります。

<!-- Here is what the [app template](https://github.com/nannou-org/nannou/blob/master/examples/templates/template_app.rs) looks like: -->
[アプリテンプレート](https://github.com/nannou-org/nannou/blob/master/examples/templates/template_app.rs)はこんな感じ：

```rust,no_run
use nannou::prelude::*;

fn main() {
    nannou::app(model).update(update).run();
}

struct Model {
    _window: window::Id,
}

fn model(app: &App) -> Model {
    let _window = app.new_window().view(view).build().unwrap();
    Model { _window }
}

fn update(_app: &App, _model: &mut Model, _update: Update) {}

fn view(app: &App, _model: &Model, frame: Frame) {
    let draw = app.draw();
    draw.background().color(PLUM);
    draw.ellipse().color(STEELBLUE);
    draw.to_frame(app, &frame).unwrap();
}
```

<!-- More specifically, the primary difference is that an app allows for working with custom ***state*** (i.e. the `Model`), whereas a sketch does not. -->
より具体的に言うと、アプリではカスタム***ステート***（つまり`モデル`）を扱うことができるのに対し、スケッチではそれができないというのが主な違いです。

> ***ホットな情報！***
>
> ライン:
>
> ```rust,ignore
> nannou::sketch(view).run()
> ```
> は単に
>
> ```rust,ignore
> nannou::app(model).simple_window(view).run()
> ```
> ただし、`model`は必要なく、`view`関数も若干シンプルになっている。

<!-- ## Switching from `sketch` to `app` -->
## `sketch` から `app` に切り替える

<!-- In the end it does not make a great deal of difference what you choose, you can always switch from one to the other in the middle of a project! -->
結局のところ、どちらを選んでも大差はなく、プロジェクトの途中でいつでも切り替えることができる！

<!-- If your sketch is getting particularly fancy and you would like to add some more flexibility, you can turn it into an app by following these steps: -->
スケッチが特に派手になってきて、さらに柔軟性を加えたい場合は、以下の手順でアプリにすることができます：

<!-- 1. Change your `main` function from -->
1. メイン関数を下記から切り替える

   ```rust,no_run
   # #![allow(dead_code)]
   # use nannou::prelude::*;
   # fn main() {
   nannou::sketch(view).run()
   # }
   # fn view(_: &App, _: Frame) {}
   ```

   から

   ```rust,no_run
   # #![allow(dead_code)]
   # use nannou::prelude::*;
   # fn main() {
   nannou::app(model).simple_window(view).run()
   # }
   # struct Model {}
   # fn model(_: &App) -> Model { Model {} }
   # fn view(_: &App, _: &Model, _: Frame) {}
   ```

<!-- 2. Add a `Model` for tracking state: -->
2. 状態を追跡するための `Model` を追加する：

   ```rust,no_run
   # #![allow(dead_code)]
   # fn main() {}
   struct Model {}
   ```

<!-- 3. Add a `model` function for creating the `Model`: -->
3. モデル`を作成するための `model` 関数を追加する：

   ```rust,no_Run
   # #![allow(dead_code)]
   # use nannou::prelude::*;
   # fn main() {}
   # struct Model {}
   fn model(_app: &App) -> Model {
       Model {}
   }
   ```

<!-- 4. Change the `view` function signature from: -->
4. `view` 関数のシグネチャを次のように変更する：

   ```rust,no_run
   # #![allow(dead_code, unused_variables)]
   # use nannou::prelude::*;
   # fn main() {}
   fn view(app: &App, frame: Frame) {
   # }
   ```

   から

   ```rust,no_run
   # #![allow(dead_code, unused_variables)]
   # use nannou::prelude::*;
   # fn main() {}
   # struct Model {}
   fn view(app: &App, _model: &Model, frame: Frame) {
   # }
   ```

<!-- And that's it! You are now ready to take your sketch to the next level. -->
それで終わりです！これで、あなたのスケッチを次のレベルに引き上げる準備が整いました。

<!-- ## Overview -->
## まとめ

|     | **Sketch** | **App** |
| --- | ---------- | ------- |
| 早く描き始める方が簡単？ | Yes | No |
| `モデル`か使える? | No | Yes |
| `オーディオ/LASER/MIDI/etc`か使える？ | No | Yes |
| `main`関数は次のようになる：| `nannou::sketch(view)` | `nannou::app(model)` |
| テンプレート | [template_sketch.rs](https://github.com/nannou-org/nannou/blob/master/examples/templates/template_sketch.rs) | [template_app.rs](https://github.com/nannou-org/nannou/blob/master/examples/templates/template_app.rs) |
| 素晴らしいものを作れるか？ | Yes | Yes |

<!-- To learn more about nannou **sketches** visit the [Draw a sketch](/tutorials/basics/draw-a-sketch.md) tutorial. -->
nannou **スケッチ**についてもっと知りたい方は、[スケッチを描く](/tutorials/basics/draw-a-sketch.md)チュートリアルをご覧ください。

<!-- To learn more about nannou **apps** visit the [Anatomy of a nannou app](/tutorials/basics/anatomy-of-a-nannou-app.md) tutorial. -->
nannou **アプリ**についてもっと知りたい方は、チュートリアル[nannouアプリの解剖](/tutorials/basics/anatomy-of-a-nannou-app.md)をご覧ください。
