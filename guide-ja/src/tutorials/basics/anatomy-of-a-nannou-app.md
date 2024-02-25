<!-- # Anatomy of a Nannou App -->
# Nannouアプリの解剖

<!-- **Tutorial Info** -->
**チュートリアル情報**

- 著者: tpltnt, mitchmindtree
- 必要な知識:
    - [はじめに](/getting_started.md)
- 読書時間：10分

---


<!-- **Nannou is a framework for creative coding in Rust.** A framework can be thought of as a collection of building blocks that help accomplish a goal.
Let's take a look at the building blocks for creative coding together. -->
**NannouはRustで創造的なコーディング**をするためのフレームワークです。
クリエイティブ・コーディングのためのビルディング・ブロックを一緒に見てみよう。

<!-- Here's an example of a bare-bones nannou app that opens an empty window: -->
以下は、空のウィンドウを開く素っ気ない南雲アプリの例である：

```rust,no_run
use nannou::prelude::*;

struct Model {}

fn main() {
    nannou::app(model)
        .event(event)
        .simple_window(view)
        .run();
}

fn model(_app: &App) -> Model {
    Model {}
}

fn event(_app: &App, _model: &mut Model, _event: Event) {
}

fn view(_app: &App, _model: &Model, _frame: Frame) {
}
```

<!-- We will start from the top! -->
トップから始めよう！

<!-- ## Import Common Items -->
## 共通項目のインポート

```rust,no_run
# #![allow(unused_imports)]
use nannou::prelude::*;
# fn main() {}
```

<!-- This line imports all of the commonly used items from nannou into scope. These include items such as `App`, `Frame`, and many more that we will learn about over time. To see the full list of items re-exported by the prelude, see [here](https://docs.rs/nannou/latest/nannou/prelude/index.html). -->
この行は、nannouからよく使われる項目をすべてスコープにインポートする。これには、`App` や `Frame` といったアイテムが含まれる。プレリュードによって再エクスポートされるアイテムの全リストを見るには、[ここ](https://docs.rs/nannou/latest/nannou/prelude/index.html)を参照してください。

<!-- > Note: Unlike some other languages, Rust does not automatically include everything from the libraries added to the project. This approach results in very clean namespaces and avoids conflicts between different items from different crates. That said, it also means we need to manually import every item we *do* want to use into scope. By providing a prelude nannou makes it a little easier to access all of the commonly used items. -->
> 注：他のいくつかの言語とは異なり、Rustはプロジェクトに追加されたライブラリのすべてを自動的にインクルードすることはありません。このアプローチにより、名前空間が非常にきれいになり、異なるクレートからの異なるアイテム間の衝突を避けることができます。とはいえ、これは、使いたいアイテムをすべて手動でスコープにインポートする必要があることを意味します。nannouがプレリュードを提供することで、よく使われるアイテムにアクセスするのが少し簡単になる。

<!-- ## **Model** - Our app state -->
## **モデル** - 我々のアプリの状態

```rust,no_run
# #![allow(dead_code)]
struct Model {}
# fn main() {}
```

<!-- The **Model** is where we define the state of our application. We can think of the model as the representation of our program at any point in time. Throughout the life of our program, we can update the model as certain events occur such as　mouse presses, key presses or timed updates. We can then present the model using some kind of output, e.g. by drawing to the screen or outputting to a laser. We　will look at these input and output events in more detail in another tutorial! Our example is as simple as possible, and we have no state to track. Thus our model can stay empty. -->
**モデル**は、アプリケーションの状態を定義する場所です。モデルは任意の時点におけるプログラムの表現と考えることができます。プログラムのライフサイクルを通じて、マウスを押したり、キーを押したり、時間を指定して更新したりといった特定のイベントが発生すると、モデルを更新することができます。そして、画面に描画したりレーザーに出力するなど、何らかの出力を使ってモデルを表示することができる。これらの入力と出力のイベントについては、別のチュートリアルで詳しく説明します！この例では、できるだけ単純で、追跡する状態もありません。したがって、モデルは空のままで構いません。

<!-- > Note: A `struct` describes a set of data. Our struct has no fields and thus is empty. There is no state information to be tracked in this example. -->
> 注： `struct`はデータの集合を記述する。この構造体にはフィールドがないので空です。この例では、追跡すべき状態情報はありません。

<!-- ## **main** - Where Rust programs begin and end -->
## **main** - Rust プログラムの始まりと終わり。

```rust,no_run
# use nannou::prelude::*;
# struct Model {}
fn main() {
    nannou::app(model)
        .event(event)
        .simple_window(view)
        .run();
}
# fn model(_app: &App) -> Model {
#     Model {}
# }
# fn event(_app: &App, _model: &mut Model, _event: Event) {
# }
# fn view(_app: &App, _model: &Model, _frame: Frame) {
# }
```

<!-- All Rust programs begin executing at the start of the `main` function and end when the `main` function ends. In most nannou programs, the main function is quite small. In short, we build a description of our app and then run it! -->
すべてのRustプログラムは、開始時に`main`関数を実行を開始し、`main`関数の終了時に終了する。ほとんどのnannouプログラムでは、main関数は非常に小さい。要するに、アプリの説明を構築し、それを実行する！

```rust,no_run
# use nannou::prelude::*;
# struct Model {}
# fn main() {
    nannou::app(model)       // Start building the app and specify our `model`
        .event(event)        // Specify that we want to handle app events with `event`
        .simple_window(view) // Request a simple window to which we'll draw with `view`
        .run();              // Run it!
# }
# fn model(_app: &App) -> Model {
#     Model {}
# }
# fn event(_app: &App, _model: &mut Model, _event: Event) {
# }
# fn view(_app: &App, _model: &Model, _frame: Frame) {
# }
```

<!-- We will describe what these **model**, **event** and **view** functions do below! -->
これらの**model**、**event**、**view**関数が何をするのかを以下に説明する！

<!-- > Note: In this app building process we get a hint at the fundamental design archetype of nannou apps. The approach is roughly based on the
[Model-View-Controller(MVC) pattern](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller), though equally inspired by [Functional Reactive Programming(FRP)](https://en.wikipedia.org/wiki/Functional_reactive_programming).
>
> In general, these paradigms split a program into:
>
> - a **model** describing the internal state
> - a **view** describing how to present the model and
> - a **controller** describing how to update the model on certain events.
>
> If you zoom out a bit you can think of the computer as a model, the screen as a view, and the keyboard or mouse as the controller. A user looks at the view and can change the state of the model using the controller. If a program does not require *user* input, the controller might use time or some other application event to modify the model. -->
> 注：このアプリの構築プロセスでは、nannouアプリの基本的な設計原型のヒントを得ることができる。このアプローチは、おおよそ
[Model-View-Controller(MVC)パターン](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller)に基づいているが、[Functional Reactive Programming(FRP)](https://en.wikipedia.org/wiki/Functional_reactive_programming)にも同様にインスパイアされている。
>
> 一般的に、これらのパラダイムはプログラムを次のように分割する：
>
> - **モデル**: 内部状態を記述する 
> - **ビュー**: モデルの見せ方を記述する
> - **コントローラ**: 特定のイベントに対してモデルを更新する方法を記述する
>
> 少し拡大すると、コンピュータをモデル、画面をビュー、キーボードやマウスをコントローラと考えることができます。ユーザーはビューを見て、コントローラを使ってモデルの状態を変更できる。プログラムが*ユーザ*の入力を必要としない場合、コントローラはモデルを変更するために時間や他のアプリケーションイベントを使用するかもしれません。

<!-- ## **model** - initialise our Model -->
## **model** - モデルを初期化する

```rust,no_run
# #![allow(dead_code)]
# use nannou::prelude::*;
# struct Model {}
fn model(_app: &App) -> Model {
    Model {}
}
# fn main() {}
```

<!-- The `model` function is run once at the beginning of the nannou app and produces a fresh, new instance of the **Model** that we declared previously, AKA the app state. This can be thought of as the "setup" stage of our application. Here, we might do things like create some windows, create a GUI, load some images or anything else that we want to happen once at the beginning of our program. We will learn how to do all of these things in future tutorials, but for now we will just return an instance of our empty **Model**. -->
`model`関数は nannouアプリの最初に一度だけ実行され、以前に宣言した **Model** の新しいインスタンス、別名アプリの状態を生成します。これはアプリケーションの「セットアップ」段階と考えることができます。ここでは、ウィンドウを作成したり、GUIを作成したり、画像を読み込んだり、プログラムの最初に一度だけ行いたいことを行います。これらのことをどのように行うかは今後のチュートリアルで学びますが、今は単に空の **Model** のインスタンスを返すことにします。

<!-- > Note: To assist with the creation of windows, GUIs, audio streams and other kinds of I/O, access to the **App** is provided as an *input* to the function.
> The **App** type can be thought of as a helper type that wraps up the finicky details of the application (such as establishing event loops, spawning I/O streams, etc) and provides an easy to use, high-level API on top. Providing access to the **App** via a function's first argument is a common practice throughout nannou's API.
> -->
> 注：ウィンドウ、GUI、オーディオストリーム、その他の種類のI/Oの作成を支援するために、**App**へのアクセスが関数への*入力*として提供される。
> **App**型は、アプリケーションの微妙な詳細(イベントループの確立、I/Oストリームの生成など)をラップし、その上に使いやすい高レベルのAPIを提供するヘルパー型と考えることができます。関数の第1引数を介して**App**へのアクセスを提供することは、nannouのAPI全体に共通する慣行である。
>
> ```rust,no_run
> # #![allow(dead_code)]
> # use nannou::prelude::*;
> # struct Model {}
> //                ----- Access to the `App` passed as an input to the function.
> //               /
> //              v
> fn model(_app: &App) -> Model {
>     Model {}
> }
> # fn main() {}
> ```
><!-- > You can learn more about what the **App** is responsible for and capable of [here](https://docs.rs/nannou/latest/nannou/app/struct.App.html). -->
> **アプリ**が何を担当し、何ができるのかについては、[こちら](https://docs.rs/nannou/latest/nannou/app/struct.App.html)をご覧ください。

<!-- ## **event** - updating the Model on app events -->
## **event** - アプリのイベントでモデルを更新する

```rust,no_run
# #![allow(dead_code)]
# use nannou::prelude::*;
# struct Model {}
fn event(_app: &App, _model: &mut Model, _event: Event) {
}
# fn main() {}
```

<!-- The **event** function is some code that will run every time some kind of app event occurs. There are many different kinds of app events including mouse and keyboard presses, window resizes, timed updates and many more. Each of these are events during which we may wish to update our **Model** in some way. For example, we may wish to turn a camera when a mouse is moved, begin drawing a shape when a button is pressed, or step forward an animation on timed updates. -->
**event**関数は、何らかのアプリイベントが発生するたびに実行されるコードです。アプリのイベントには、マウスやキーボードの押下、ウィンドウのリサイズ、時間指定の更新など、さまざまな種類があります。これらのイベントはそれぞれ、何らかの方法で **Model** を更新したいイベントです。例えば、マウスが動かされたときにカメラを回転させたり、ボタンが押されたときにシェイプの描画を開始したり、タイムドアップデートでアニメーションを前進させたりしたいと思うかもしれません。

<!-- All of these events are described within the **Event** type. One way to distinguish between which event is currently occurring is to ["pattern match"](https://doc.rust-lang.org/book/ch06-02-match.html) on the event and handle only those events that we care about, ignoring all the others. A simpler approach is to not register an **event** function while building the app at all, and instead only register more specific functions for those events that we care about. -->
これらのイベントはすべて**Event**型で記述される。現在発生しているイベントを区別する1つの方法は、イベント上で["パターン・マッチ"](https://doc.rust-lang.org/book/ch06-02-match.html)を行い、気になるイベントだけを処理し、他のイベントはすべて無視することである。もっと簡単な方法は、アプリをビルドするときに**event**関数をまったく登録せず、その代わりに、気になるイベントに対してより特定の関数のみを登録することです。

<!-- For example, if instead of handling *all* events we only want to handle timed updates (an event that by default occurs 60 times per second) we could change our app building code to this: -->
例えば、*すべての*イベントを処理する代わりに、定時更新（デフォルトでは1秒間に60回発生するイベント）のみを処理したい場合、アプリのビルドコードを次のように変更することができる：

```rust,no_run
# #![allow(dead_code)]
# use nannou::prelude::*;
# struct Model {}
fn main() {
    nannou::app(model)
        .update(update) // rather than `.event(event)`, now we only subscribe to updates
        .simple_window(view)
        .run();
}
# fn model(_app: &App) -> Model {
#     Model {}
# }
# fn update(_app: &App, _model: &mut Model, _update: Update) {
# }
# fn view(_app: &App, _model: &Model, _frame: Frame) {
# }
```

<!-- And remove our `event` function in favour of an `update` function: -->
そして、`event`関数を削除して、`update`関数を使う：

```rust,no_run
# #![allow(dead_code)]
# use nannou::prelude::*;
# struct Model {}
fn update(_app: &App, _model: &mut Model, _update: Update) {
}
# fn main() {}
```

<!-- Now, our new **update** function will only run each time a timed update occurs. -->
これで、新しい**update**関数は、定時更新が発生するたびに実行されるようになった。

<!-- > Note: Nannou provides a whole suite of different events that may be registered while building an app or window in this way. See the [all_functions.rs example](https://github.com/nannou-org/nannou/blob/master/examples/nannou_basics/all_functions.rs) for a demonstration of most of the different kinds of events that are available. -->
> 注：Nannouは、この方法でアプリやウィンドウを構築する際に登録できる、さまざまなイベント一式を提供しています。[all_functions.rsの例](https://github.com/nannou-org/nannou/blob/master/examples/nannou_basics/all_functions.rs)を参照してください。

<!-- ## **view** - presenting the Model to a window -->
## **view** - モデルをウィンドウに表示する

```rust,no_run
# #![allow(dead_code)]
# use nannou::prelude::*;
# struct Model {}
fn view(_app: &App, _model: &Model, _frame: Frame) {
}
# fn main() {}
```

<!-- Finally, the **view** allows us to present the state of the model to a window by drawing to its **Frame** and returning the frame at the end. Here we can change the background colour, use the **Draw** API to draw a scene, draw a GUI to the window or even use the wgpu API to draw to the frame using our own textures and render passes. All of this will be covered by future tutorials. -->
最後に、**view**では、**Frame**に描画し、最後にフレームを返すことで、モデルの状態をウィンドウに表示することができます。ここでは、背景色を変更したり、**Draw** APIを使用してシーンを描画したり、ウィンドウにGUIを描画したり、あるいはwgpu APIを使用して独自のテクスチャとレンダーパスを使用してフレームに描画することもできます。これら全ては今後のチュートリアルでカバーする予定だ。

<!-- ## Concluding Remarks -->
## 結びの言葉

<!-- Hopefully this has given you a rough idea of how nannou apps work! Do not stress if some of the syntax looks confusing or some of the specifics still seem unclear - we will aim to cover these and more in future tutorials :) -->
nannouアプリがどのように機能するか、おおまかなイメージをつかんでいただけたと思います！構文が分かりにくかったり、詳細がまだ不明確だったりしても、ストレスを感じないでください。😀
