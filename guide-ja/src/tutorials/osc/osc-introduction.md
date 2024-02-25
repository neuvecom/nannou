<!-- # An Intro to OSC -->
# OSC入門

<!-- **Tutorial Info** -->
**チュートリアル情報**

- 著者: [madskjeldgaard](https://madskjeldgaard.dk)
- 必要な知識:
    - [nannouアプリの解剖](/tutorials/basics/anatomy-of-a-nannou-app.md)
- 読書時間：5分
---

<!-- ## What is OSC? -->
## OSCとは？

<!-- Open Sound Control or [OSC](http://opensoundcontrol.org/) is a protocol for communicating between different pieces of software and/or computers. It is based on network technology and offers a flexible way to share control data between processes with a high level of precision, either internally on your local machine or through a network connection. -->
Open Sound Controlまたは[OSC](http://opensoundcontrol.org/)は、異なるソフトウェアやコンピュータ間で通信するためのプロトコルです。ネットワーク技術をベースにしており、ローカルマシンの内部またはネットワーク接続を介して、プロセス間で制御データを高い精度で共有する柔軟な方法を提供します。

<!-- In nannou it's possible to both send and receive OSC data, allowing you to control other software or let nannou be controlled by other software. -->
nannouではOSCデータの送受信が可能なので、他のソフトウェアをコントロールしたり、他のソフトウェアからnannouをコントロールさせたりすることができます。

<!-- ## Setting up OSC -->
## OSC のセットアップ

<!-- To use OSC in nannou, it is necessary to add the `nannou_osc` crate as a dependency in your nannou project. -->
nannouでOSCを使うには、`nannou_osc`クレートをnannouプロジェクトに依存関係として追加する必要があります。

<!-- Open up your `Cargo.toml` file at the root of your nannou project and add the following line under the `[dependencies]` tag: -->
nannouプロジェクトのルートにある`Cargo.toml`ファイルを開き、`[dependencies]`タグの下に以下の行を追加する：

```toml
nannou_osc = "0.15.0"
```

<!-- The value in the quotes is the version of the OSC package. At the time of writing this, `"0.15.0"` is the latest version. -->
引用符の中の値はOSCパッケージのバージョンです。これを書いている時点では、`"0.15.0"`が最新バージョンです。

<!-- To get the latest version of the osc library, execute `cargo search nannou_osc` on the command line and read the resulting version from there. -->
oscライブラリの最新バージョンを取得するには、コマンドラインで`cargo search nannou_osc`を実行し、そこから結果のバージョンを読み込む。

<!-- To use the crate in your nannou-projects you can add a use-statement at the top of your `main.rs` file to import the OSC-functionality. -->
nannouプロジェクトでこのクレートを使用するには、`main.rs`ファイルの先頭にuseステートメントを追加して、OSC機能をインポートします。

```rust,no_run
# #![allow(unused_imports)]
use nannou_osc as osc;
# fn main() {}
```
