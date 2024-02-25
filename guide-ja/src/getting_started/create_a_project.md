<!-- # Create A Project -->
# プロジェクトを作成する

<!-- Whether we are creating an artwork, an app, a quick sketch or an installation, we want to begin by creating a new project. A new nannou project lets us build a nannou application the way that *we* want to use it. -->
アートワーク、アプリ、簡単なスケッチ、インスタレーションなど、どのようなものを作るにしても、まずは新しいプロジェクトを作りましょう。新しいnannouプロジェクトは、私たちが使いたいようにnannouアプリケーションを構築することができます。

<!-- Eventually, the aim for Nannou is to provide a project generator tool which will allow us to do the following and much more in just a few clicks. For now, we can create a new project with just a few small steps: -->
最終的には、数回のクリックで以下のようなことができるプロジェクト・ジェネレーター・ツールを提供することを目標としている。今のところ、わずかなステップで新しいプロジェクトを作成することができる：

<!-- 1. Create the Rust project with the name of our project: -->
1. プロジェクト名でRustプロジェクトを作成する：

   ```bash
   cargo new my-project
   ```

<!-- 2. Change directory to the generated project. -->
2. 生成されたプロジェクトにディレクトリを変更する。

   ```bash
   cd my-project
   ```

<!-- 3. Edit the `Cargo.toml` file and add the latest version of nannou to the bottom like so: -->
3. `Cargo.toml`ファイルを編集し、最新バージョンのnannouを一番下に追加する：

   ```toml
   [package]
   name = "my_project"
   version = "0.1.0"
   authors = ["mitchmindtree <mitchell.nordine@gmail.com>"]
   edition = "2018"

   [dependencies]
   nannou = "0.17"
   ```

   <!-- Note that there is a chance the nannou version above might be out of date.
   You can check the latest version by typing `cargo search nannou` in your terminal. Be sure to change the author to your name too! -->
   上記のnannouのバージョンが古い可能性があることに注意してください。
   ターミナルで`cargo search nannou`と入力すれば、最新バージョンをチェックできます。作者もあなたの名前に変更してください！

<!-- 4. Replace the code in `src/main.rs` with the following to setup our nannou application. -->
4. `src/main.rs`のコードを以下のように置き換えて、nannouアプリケーションをセットアップする。

   ```rust,no_run
   # extern crate nannou;
   use nannou::prelude::*;

   fn main() {
       nannou::app(model)
           .update(update)
           .simple_window(view)
           .run();
   }

   struct Model {}

   fn model(_app: &App) -> Model {
       Model {}
   }

   fn update(_app: &App, _model: &mut Model, _update: Update) {
   }

   fn view(_app: &App, _model: &Model, frame: Frame) {
       frame.clear(PURPLE);
   }
   ```

   <!-- If you are new to Rust or simply do not understand the code above just yet, do not fear! In the first tutorial of the next chapter we will break down this code step-by-step. -->
   もしあなたがRustの初心者であったり、単に上記のコードをまだ理解していなかったりしても、恐れることはありません！次の章の最初のチュートリアルでは、このコードをステップ・バイ・ステップで分解していきます。

<!-- 5. Trigger the initial build and check that everything is working nicely by running our app! -->
5. 初期ビルドをトリガーし、アプリを実行してすべてがうまく動作していることを確認する！

   ```bash
   cargo run --release
   ```

   <!-- The first build might take a while, as we must build nannou and all of its dependencies from scratch. The following times that we run our app should be much faster! -->
   最初のビルドには時間がかかるかもしれない。nannouとその依存関係をすべてゼロからビルドしなければならないからだ。次にアプリを実行するときは、もっと速くなるはずだ！

   <!-- Once the project has finished building, it will begin running and we should be able to see a purple window. -->
   プロジェクトが構築し終わると、プロジェクトが動き始め、紫色のウィンドウが見えるはずだ。


<!-- **That's it!** If everything went as planned, you are now ready to start building your own nannou project. Of course, we probably want our application to be more than just a purple window. -->
**よっしゃ！** すべてが計画通りに進んだなら、あなた自身のnannouプロジェクトを作り始める準備が整いました。もちろん、アプリケーションを単なる紫色のウィンドウ以上のものにしたいでしょう。

<!-- To find out how to add more features to our project like graphics, audio, multiple windows, laser output, projection mapping and much more, let's take a look at the next chapter. -->
グラフィックス、オーディオ、マルチウィンドウ、レーザー出力、プロジェクションマッピングなど、プロジェクトにさらに機能を追加する方法については、次の章を参照してください。
