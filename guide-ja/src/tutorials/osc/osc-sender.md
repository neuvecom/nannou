<!-- # Sending OSC -->
# OSCの送信

<!-- **Tutorial Info** -->
**チュートリアル情報**

- 著者: [madskjeldgaard](https://madskjeldgaard.dk)
- 必要な知識:
    - [nannouアプリの解剖](/tutorials/basics/anatomy-of-a-nannou-app.md)
    - [2D形状の描画s](/tutorials/basics/drawing-2d-shapes.md)
    - [画面上で円を動かす](/tutorials/tutorial/moving-a-circle-about.md)
    - [OSCの紹介](/tutorials/osc/osc-introduction.md)
- 読書時間：20分

---

<!-- In this tutorial we will cover how to send OSC data from a nannou app to another application using the `nannou_osc` crate. -->
このチュートリアルでは、`nannou_osc`クレートを使ってnannouアプリから他のアプリケーションにOSCデータを送信する方法を説明する。

<!-- We are going to write a simple program which has a circle moving about on the screen while the circle's position is sent via OSC to another application. We will continue working on the app from [Moving a circle about on the screen](/tutorials/basics/moving-a-circle-about.md). -->
円の位置をOSC経由で他のアプリケーションに送りながら、画面上で円を動かす簡単なプログラムを書きます。引き続き、[スクリーン上で円を動かす](/tutorials/basics/moving-a-circle-about.md)のアプリに取り組みます。

<!-- ## Setting up an OSC sender -->
## OSC senderの設定

<!-- At the top of your `main.rs`-file, import the `nannou_osc` crate and make it available in your program via the shorthand `osc`. -->
`main.rs`ファイルの先頭で、`nannou_osc`クレートをインポートし、`osc`という省略記法を使ってプログラム内で利用できるようにする。

```rust, norun
# #![allow(unused_imports)]
use nannou_osc as osc;
# fn main(){}
```

<!-- The first thing we then need to do is set up our OSC-sender in the `Model`-struct you may have seen in other nannou-tutorials.
Add a field to the struct called `sender` with a [Sender](https://docs.rs/nannou_osc/latest/nannou_osc/send/struct.Sender.html)-struct as the type input. -->
まず最初にすることは、他のnannou-tutorialで見たことがあるかもしれない`Model`構造体にOSC-senderをセットアップすることだ。
[Sender](https://docs.rs/nannou_osc/latest/nannou_osc/send/struct.Sender.html)-structを型入力として、`sender`というフィールドをstructに追加する。

```rust,no_run
# #![allow(dead_code, unused_imports)]
# use nannou_osc as osc;
struct Model {
    sender: osc::Sender<osc::Connected>,
}
# fn main() {}
```

<!-- Next, we need to setup our `Model` struct using the `model` function. Don't worry if it looks a bit daunting at first, we will go through it step by step. -->
次に `model` 関数を使って `Model` 構造体をセットアップする必要がある。最初は少し難しく見えても心配しないでください。

```rust,no_run
# #![allow(dead_code, unused_imports)]
# use nannou_osc as osc;
# use nannou::prelude::*;
# struct Model {
#   sender: osc::Sender<osc::Connected>,
# }
fn model(_app: &App) -> Model {
    let port = 1234;
    let target_addr = format!("{}:{}", "127.0.0.1", port);

	let sender = osc::sender()
        .expect("Could not bind to default socket")
        .connect(target_addr)
        .expect("Could not connect to socket at address");

    Model { sender }
}
# fn main() {}
```

<!-- First, let's choose the network port that our data will be sent to. -->
まず、データを送信するネットワーク・ポートを選択しよう。

```rust,no_run
# #![allow(unused_variables)]
# fn main() {
let port = 1234;
# }
```
<!-- The osc-sender expects a string in the format "address:port", for example `"127.0.0.1:1234"`. -->
osc-senderは "address:port "という形式の文字列を想定している。例えば `"127.0.0.1:1234"` などです。

<!-- The address can either be an internal address or the address of another computer on your network. In this tutorial we will be targetting our own computer's internal address which is represented by `"127.0.0.1"`. -->
アドレスは内部アドレスでも、ネットワーク上の他のコンピュータのアドレスでもかまいません。このチュートリアルでは、`"127.0.0.1"`で表される自分のコンピュータの内部アドレスをターゲットにします。

```rust,no_run
# #![allow(unused_variables)]
# fn main() {
# let port = 1234;
let target_addr = format!("{}:{}", "127.0.0.1", port);
# }
```

<!-- Lastly, we need to bind our OSC sender to the network socket. This isn't always successful, so we are attaching the `expect()`-method (read more about [`expect()` here](https://doc.rust-lang.org/std/option/enum.Option.html#method.expect)) to post an error message if it is not successful. If it is successful, the `.connect(target_addr)`-method is used to connect the sender to the target address. Again, this may be unsuccesful so we use the `expect()`-method on the result of that operation as well. -->
最後に、OSCの送信者をネットワーク・ソケットにバインドする必要がある。これは必ずしも成功するとは限らないので、`expect()`メソッド（[`expect()`についてはこちら](https://doc.rust-lang.org/std/option/enum.Option.html#method.expect)を使って、成功しなかった場合にエラーメッセージを表示するようにしている。成功した場合は、`.connect(target_addr)`メソッドを使って送信者とターゲットのアドレスを接続します。ここでも失敗する可能性があるので、この操作の結果に対しても `expect()` メソッドを使用します。

```rust,no_run
# #![allow(unused_variables)]
# use nannou_osc as osc;
# fn main() {
#     let port = 1234;
#     let target_addr = format!("{}:{}", "127.0.0.1", port);
let sender = osc::sender()
    .expect("Could not bind to default socket")
    .connect(target_addr)
    .expect("Could not connect to socket at address");
# }
```
<!-- ### Sending OSC messages -->
### OSCメッセージの送信

<!-- An OSC packet consists of at least two components: An OSC address and 0 or more arguments containing data. The OSC address is not to be confused with the network address we connected to before. Instead, an OSC address is a path sort of like a URL, for example `/circle/position`. -->
OSCパケットは少なくとも2つの要素から構成される：OSCアドレスと、データを含む0個以上の引数である。OSCアドレスは、以前に接続したネットワーク・アドレスと混同してはいけない。OSCアドレスはURLのようなもので、例えば`/circle/position`のようなものです。

<!-- To create an OSC packet, we first need to make an address. -->
OSCパケットを作るには、まずアドレスを作る必要がある。

```rust,no_run
# #![allow(unused_variables)]
# fn main() {
let osc_addr = "/circle/position".to_string();
# }
```

<!-- Then create a vector of arguments. These need to be formatted using the types found in [osc::Type](https://docs.rs/nannou_osc/latest/nannou_osc/enum.Type.html) in the nannou_osc crate. Below we create an argument list of two floating point values: the `x` and `y` coordinates of our circle. -->
次に引数のベクトルを作る。これらはnannou_oscクレートの[osc::Type](https://docs.rs/nannou_osc/latest/nannou_osc/enum.Type.html)にある型を使って整形する必要がある。以下では2つの浮動小数点値からなる引数リストを作成する。

```rust,no_run
# #![allow(unused_variables)]
# use nannou_osc as osc;
# fn main() {
# let x = 0.0;
# let y = 0.0;
let args = vec![osc::Type::Float(x), osc::Type::Float(y)];
#
# }

```
<!-- Now, bringing these two things together we get an OSC packet. The sender expect these to be delivered in a tuple. -->
さて、この2つを合わせるとOSCパケットになる。送信側は、これらがタプルで配送されることを期待する。

```rust,no_run
# #![allow(unreachable_code, unused_variables)]
# fn main() {
# let osc_addr = unimplemented!();
# let args = unimplemented!();
let packet = (osc_addr, args);
# }
```

<!-- [Reading the documentation](https://docs.rs/nannou_osc/latest/nannou_osc/send/struct.Sender.html#method.send-1) for the `send`-method, we can see that it returns a Result type which will either contain the number of bytes written (if it was successful) and, more importantly, some useful errors of type CommunicationError if it was not succesful. To discard the error part of this, we use the `ok()` method at the end. -->
[ドキュメントを読むと](https://docs.rs/nannou_osc/latest/nannou_osc/send/struct.Sender.html#method.send-1)、`send`メソッドはResult型を返すことがわかる。このResult型には（成功した場合は）書き込まれたバイト数が格納され、さらに重要なことに、成功しなかった場合はCommunicationError型の有用なエラーが格納される。このエラーの部分を破棄するには、最後に `ok()` メソッドを使う。

```rust,no_run
# #![allow(unreachable_code, unused_variables)]
# use nannou_osc as osc;
# struct Model {
#    sender: osc::Sender<osc::Connected>,
# }
# fn main() {
#    let model: Model = unimplemented!();
#    let osc_addr = "/circle/position".to_string();
#    let args = vec![osc::Type::Float(0.0), osc::Type::Float(0.0)];
#    let packet = (osc_addr, args);
    model.sender.send(packet).ok();
# }
```

<!-- ## The finished app -->
## 完成したアプリ

```rust,no_run
use nannou::prelude::*;
use nannou_osc as osc;

fn main() {
    nannou::app(model).simple_window(view).run();
}

struct Model {
    sender: osc::Sender<osc::Connected>,
}

fn model(_app: &App) -> Model {
    // The network port that data is being sent to
    let port = 1234;

    // The osc-sender expects a string in the format "address:port", for example "127.0.0.1:1234"
    // "127.0.0.1" is equivalent to your computers internal address.
    let target_addr = format!("{}:{}", "127.0.0.1", port);

    // This is the osc Sender which contains a couple of expectations in case something goes wrong.
    let sender = osc::sender()
        .expect("Could not bind to default socket")
        .connect(target_addr)
        .expect("Could not connect to socket at address");

    Model { sender }
}

fn view(app: &App, model: &Model, frame: Frame) {
    // Use app time to progress through a sine wave
    let sine = app.time.sin();
    let slowersine = (app.time / 2.0).sin();

    // Get boundary of the window (to constrain the movements of our circle)
    let boundary = app.window_rect();

    // Map the sine wave functions to ranges between the boundaries of the window
    let x = map_range(sine, -1.0, 1.0, boundary.left(), boundary.right());
    let y = map_range(slowersine, -1.0, 1.0, boundary.bottom(), boundary.top());

    // Send x-y coordinates as OSC
    let osc_addr = "/circle/position".to_string();
    let args = vec![osc::Type::Float(x), osc::Type::Float(y)];
    let packet = (osc_addr, args);

    model.sender.send(packet).ok();

    // Prepare to draw.
    let draw = app.draw();

    // Clear the background to purple.
    draw.background().color(PLUM);

    // Draw a blue ellipse at the x/y coordinates 0.0, 0.0
    draw.ellipse().color(STEELBLUE).x_y(x, y);

    draw.to_frame(app, &frame).unwrap();
}
```

<!-- In the next tutorial we will take a look at how to receive our OSC values and do something interesting with them. -->
次のチュートリアルでは、OSCの値を受け取り、それを使って何か面白いことをする方法を見ていきます。
