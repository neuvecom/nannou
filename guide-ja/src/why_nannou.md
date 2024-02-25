<!-- # Why Nannou? -->
# なぜNannouなのか？

<!-- **nannou** is a collection of code aimed at making it easy for artists to express themselves with simple, fast, reliable, portable code.  Whether working on a 12-month installation or a 5 minute sketch, this framework aims to give artists easy access to the tools they need. -->
**nannou**は、アーティストがシンプルで、速く、信頼性が高く、ポータブルなコードで自分自身を表現することを容易にすることを目的としたコードのコレクションです。  
12ヶ月のインスタレーションでも5分のスケッチでも、このフレームワークはアーティストが必要なツールに簡単にアクセスできることを目指しています。

<!-- The project was started out of a desire for a creative coding framework inspired by Processing, OpenFrameworks and Cinder, but for Rust. <sup>Named after [this](https://www.youtube.com/watch?v=A-Pkx37kYf4).</sup> -->
このプロジェクトは、Processing、OpenFrameworks、Cinderにインスパイアされた、Rust用のクリエイティブなコーディングフレームワークが欲しいという願望から始まった。<sup>[これ](https://www.youtube.com/watch?v=A-Pkx37kYf4) にちなんで命名。</sup>

<!-- ## Goals -->
## ゴール

<!-- Nannou aims to provide easy, cross-platform access to the things that artists need: -->
Nannouは、アーティストが必要とするものへの簡単でクロスプラットフォームなアクセスを提供することを目指している：

<!-- - [x] **Windowing & Events** via [winit](https://crates.io/crates/winit).
- [x] **Audio** via [CPAL](https://crates.io/crates/cpal). *Input and
  output streams. Duplex are not yet supported.*
- [ ] **Video** input, playback and processing (*would love suggestions and
  ideas*).
- [x] **GUI** via [egui](https://crates.io/crates/egui). *May switch to a custom
  nannou solution [in the
  future](https://github.com/nannou-org/nannou/issues/383)*.
- **Geometry** with functions and iterators for producing vertices and indices:
  - [x] 1D - `Scalar`, `Range`.
  - [x] 2D - `Path`, `Polyline`, `Polygon`, `Rect`, `Line`, `Ellipse`, `Quad`,
    `Tri`.
  - [x] 3D - `Cuboid`.
  - [ ] 3D TODO - `Ellipsoid`, `Cube`, Prisms, Pyramids, *Hedrons, Camera, etc.
  - [x] Vertex & index iterators.
  - [x] [Graph](https://docs.rs/nannou/latest/nannou/geom/graph/index.html) for
    composing geometry.
- **Graphics** via WGPU (via [wgpu-rs](https://github.com/gfx-rs/wgpu-rs)):
  - [x] [Draw](https://docs.rs/nannou/latest/nannou/draw/index.html) API. E.g.
    `draw.ellipse().w_h(20.0, 20.0).color(RED)`.
  - [x] [Mesh](https://docs.rs/nannou/latest/nannou/mesh/index.html) API.
  - [x] [Image](https://docs.rs/nannou/latest/nannou/image/index.html) API.
  - [x] [Texture](https://docs.rs/nannou/latest/nannou/wgpu/struct.Texture.html) API.
  - [x] [WGPU](https://docs.rs/nannou/latest/nannou/wgpu/index.html) API.
  - [x] [Text](https://docs.rs/nannou/latest/nannou/text/index.html) API.
  - [ ] Shader hot-loading. *See
    [hotglsl](https://github.com/nannou-org/hotglsl) and [nannou_isf
    WIP](https://github.com/nannou-org/nannou/tree/master/nannou_isf)*.
- **Protocols**:
  - [x] [OSC](https://docs.rs/nannou_osc) - Open Sound
    Control.
  - [x] [ISF](https://github.com/nannou-org/isf) - Interactive Shader Format.
  - [x] [CITP](https://github.com/nannou-org/citp) - Controller Interface
    Transport Protocol (network implementation is in progress).
  - [x] [Ether-Dream](https://github.com/nannou-org/ether-dream) Laser DAC
    protocol and network implementation.
  - [x] [DMX via sACN](https://github.com/lschmierer/sacn) - commonly used for
    lighting and effects.
  - [x] [Serial](https://crates.io/crates/serial) - commonly used for
    interfacing with LEDs and other hardware.
  - [ ] MIDI - No friendly nannou API is provided yet, but cross-platform MIDI I/O is possible via [midir](https://crates.io/crates/midir).
  - [x] [UDP](https://doc.rust-lang.org/std/net/struct.UdpSocket.html) via
    std.
  - [x] TCP
    [streams](https://doc.rust-lang.org/std/net/struct.TcpStream.html) and
    [listeners](https://doc.rust-lang.org/std/net/struct.TcpListener.html)
    via std.
- **Device & I/O stream APIs**:
  - [x] Windowing.
  - [x] Application events.
  - [x] [Audio](https://docs.rs/nannou/latest/nannou/app/struct.Audio.html).
  - [ ] Video.
  - [x] [Lasers](https://github.com/nannou-org/nannou/tree/master/nannou_laser).
  - [ ] Lights. *For now, we recommend DMX via the [sacn crate](https://docs.rs/sacn/0.4.4/sacn/).*
  - [ ] LEDs. *For now, we recommend DMX via the [sacn crate](https://docs.rs/sacn/0.4.4/sacn/).*
- [ ] **Graphical Node Graph** via [gantz](https://github.com/nannou-org/gantz).
- [ ] **GUI Editor**. -->

- [x] **Windowing & Events** via [winit](https://crates.io/crates/winit)
- [x] **オーディオ** via [CPAL](https://crates.io/crates/cpal)
  - *入力と出力ストリーム。二重はまだサポートされていません*
- [ ] **ビデオ** 入力、再生、処理 (*提案とアイデアを歓迎します*)
- [x] **GUI** via [egui](https://crates.io/crates/egui) 
  - *nannouのカスタムソリューション [将来的に](https://github.com/nannou-org/nannou/issues/383)*。
- **Geometry** 頂点とインデックスを生成するための関数とイテレータがあります：
  - [x] 1D - `スカラー`, `範囲`.
  - [x] 2D - `Path`、`Polyline`、`Polygon`、`Rect`、`Line`、`Ellipse`、`Quad`、`Tri`.
  - [x] 3D - `Cuboid`.
  - [ ] 3D TODO - `Ellipsoid`、`Cube`、プリズム、ピラミッド、*ヘドロン、カメラなど。
  - [x] 頂点とインデックスのイテレータ。
  - [x] [グラフ](https://docs.rs/nannou/latest/nannou/geom/graph/index.html) ジオメトリの合成用。
- **Graphics** via WGPU  via ([wgpu-rs](https://github.com/gfx-rs/wgpu-rs))：
  - [x] [Draw](https://docs.rs/nannou/latest/nannou/draw/index.html) API。
    - 例 `draw.ellipse().w_h(20.0, 20.0).color(RED)`
  - [x] [Mesh](https://docs.rs/nannou/latest/nannou/mesh/index.html) API.
  - [x] [Image](https://docs.rs/nannou/latest/nannou/image/index.html) API。
  - [x] [Texture](https://docs.rs/nannou/latest/nannou/wgpu/struct.Texture.html) API。
  - [x] [WGPU](https://docs.rs/nannou/latest/nannou/wgpu/index.html) API。
  - [x] [Text](https://docs.rs/nannou/latest/nannou/text/index.html) API。
  - [ ] シェーダーのホットローディング。
    - *参照　[hotglsl](https://github.com/nannou-org/hotglsl) および [nannou_isf WIP](https://github.com/nannou-org/nannou/tree/master/nannou_isf)*
- **プロトコル**：
  - [x] [OSC](https://docs.rs/nannou_osc) - オープンサウンドコントロール。
  - [x] [ISF](https://github.com/nannou-org/isf) - インタラクティブシェーダフォーマット。
  - [x] [CITP](https://github.com/nannou-org/citp) - コントローラインタフェーストランスポートプロトコル
    - (ネットワーク実装は進行中)。
  - [x] [Ether-Dream](https://github.com/nannou-org/ether-dream) レーザー DACプロトコルとネットワーク実装。
  - [x] [DMX via sACN](https://github.com/lschmierer/sacn) - 照明とエフェクトによく使われる。
  - [x] [Serial](https://crates.io/crates/serial) - LEDや他のハードウェアとのインターフェイスによく使われる。
  - [ ] MIDI - フレンドリーな nannou API はまだ提供されていません
    - [midir](https://crates.io/crates/midir) 経由でクロスプラットフォーム MIDI I/O が可能。
  - [x] [UDP](https://doc.rust-lang.org/std/net/struct.UdpSocket.html) via 標準。
  - [x] TCP [ストリーム](https://doc.rust-lang.org/std/net/struct.TcpStream.html) と[リスナー](https://doc.rust-lang.org/std/net/struct.TcpListener.html) via 標準。
- **デバイスとI/OストリームAPI**：
  - [x] ウィンドウ表示。
  - [x] アプリケーション・イベント。
  - [x] [オーディオ](https://docs.rs/nannou/latest/nannou/app/struct.Audio.html).
  - [ ] ビデオ。
  - [x] [Lasers](https://github.com/nannou-org/nannou/tree/master/nannou_laser).
  - ライト *今のところ、[sacn crate](https://docs.rs/sacn/0.4.4/sacn/) 経由のDMXを推奨します。*
  - LED *今のところ、[sacn crate](https://docs.rs/sacn/0.4.4/sacn/) 経由のDMXを推奨します。*
- [ ] **Graphical Node Graph** via [gantz](https://github.com/nannou-org/gantz).
- [ ] **GUIエディタ**.

<!-- Nannou aims to **use only pure-rust libraries**. As a new user you should require nothing more than `cargo build` to get going. Falling back to C-bindings will be considered as a temporary solution in the case that there are no Rust alternatives yet in development. We prefer to drive forward development of less mature rust-alternatives than depend on bindings to C code. This should make it easier for nannou *users* to become nannou *contributors* as they do not have to learn a second language in order to contribute upstream. -->
Nannouは**純粋な錆のライブラリ**だけを使うことを目指している。新しいユーザーであれば、`cargo build` 以外に必要なものはないはずです。C-バインディングへのフォールバックは、Rustの代替ライブラリがまだ開発されていない場合の一時的な解決策として考えます。私たちは、Cコードへのバインディングに依存するよりも、成熟していないRust代替の開発を推進することを好みます。これにより、上流に貢献するために第二言語を学ぶ必要がなくなるため、Nannouの*ユーザー*がNannouの*貢献者*になりやすくなるはずです。

<!-- Nannou **will not contain `unsafe` code** with the exception of bindings to operating systems or hardware APIs if necessary. -->
NannouはOSやハードウェアAPIへのバインディングが必要な場合を除き、**`安全でない`コードを含まない**。

<!-- Nannou wishes to **remove the need to decide between lots of different backends that provide access to the same hardware**. Instead, we want to focus on a specific set of backends and make sure that they work well. -->
Nannouは、**同じハードウェアにアクセスするために、多くの異なるバックエンドの中から選択する必要をなくしたい**と考えている。その代わりに、特定のバックエンドのセットに焦点を当て、それらがうまく機能するようにしたい。

<!-- ## Why Rust? -->
## なぜRustなのか？

<!-- Rust is a language that is both highly expressive and blazingly fast. Here are some of the reasons why we choose to use it: -->
Rustは、高い表現力と圧倒的な速さを併せ持つ言語です。私たちがRustを選んだ理由をいくつか紹介しましょう：

<!-- - **Super fast**, as in [C and C++ fast](https://benchmarksgame-team.pages.debian.net/benchmarksgame/fastest/rust-gpp.html).
- [**A standard package manager**](https://crates.io/) that makes it very easy to handle dependencies and share your own projects in seconds.
- **Highly portable.** Easily build for MacOS, Linux, Windows, Android, iOS and [so many others](https://forge.rust-lang.org/platform-support.html).
- **No header files** and no weird linking errors.
- **Sum Types and Pattern Matching** and no `NULL`.
- **Local type inference**. Only write types where it matters, no need to repeat yourself.
- A more modern, **ƒunctional and expressive style**.
- **Memory safe and data-race-free!** Get your ideas down without the fear of creating pointer spaghetti or segfault time-sinks.
- **Immutability by default.** Easily distinguish between variables that can change and those that can't at a glance.
- **Module system** resulting in very clean and concise name spaces.
- One of the kindest internet communities we've come across. Please visit mozilla's #rust or /r/rust if you're starting out and need any pointers. -->
- **超高速**、[C および C++ 高速](https://benchmarksgame-team.pages.debian.net/benchmarksgame/fastest/rust-gpp.html) 
- [**標準のパッケージマネージャ**](https://crates.io/)により、依存関係を扱うのが非常に簡単で、独自のプロジェクトを数秒で共有できます。
- **高い移植性** MacOS、Linux、Windows、Android、iOSおよび[その他](https://forge.rust-lang.org/platform-support.html)多くのプラットフォーム向けに簡単にビルドできます。
- **ヘッダーファイルがなく**、変なリンクエラーもありません。
- **豊富な型とパターンマッチ**と`NULL`なし。
- **ローカル型推論** 重要なところだけ型を書けば、繰り返す必要はない。
- より現代的、**機能的で、表現力豊かなスタイル**。
- **メモリ・セーフでデータ・レース・フリー！** ポインタ・スパゲッティやセグメンテーション・タイム・シンクを作成する心配なしにあなたのアイデアを実現することができます。
- **デフォルトでイミュータブル** 変更できる変数と変更できない変数を一目で簡単に区別できます。
- **モジュール・システム** 非常にクリーンで簡潔な名前空間をもたらします。
- もしあなたがこれから始めようとしていて、何かヒントが必要なら。mozillaの#rustや/r/rustをご覧ください。最も親切なインターネットコミュニティのひとつです。

<!-- ## Why the Apache/MIT dual licensing? -->
## なぜApacheとMITのデュアルライセンスなのか？

<!-- For the most part, nannou is trying to maintain as much flexibility and compatibility with the licensing of Rust itself, which is also [dual licensed](https://www.rust-lang.org/policies/licenses). -->
ほとんどの場合、nannouは、[デュアルライセンス](https://www.rust-lang.org/policies/licenses)であるRust自体のライセンスとの柔軟性と互換性をできるだけ維持しようとしている。

<!-- The Apache 2.0 and MIT license are very similar, but have a few key differences.
Using the Apache 2.0 license for contributions triggers the Apache 2.0 patent grant.
This grant is designed to protect against leveraging the patent law system to bypass(some) terms of the license. If the contribution is under the Apache 2.0 license, the contributor assures that they will not claim a violation of (their own) patents. If someone makes a work based on Apache 2.0 licensed code, they in turn also vow to not sue their users (for patent infringement).
The MIT license provides compatibility with a lot of other FLOSS licenses. -->
Apache 2.0ライセンスとMITライセンスは非常によく似ていますが、いくつかの重要な違いがあります。
貢献のためにApache 2.0ライセンスを使うと、Apache 2.0特許許可が発動します。
この許可は、特許法制度を利用してライセンスの(いくつかの)条項を迂回することを防ぐように設計されています。貢献がApache 2.0ライセンスの下にある場合、貢献者は(彼ら自身の)特許の侵害を主張しないことを保証します。誰かがApache 2.0ライセンスのコードに基づいて作品を作れば、彼らもまた、そのユーザを（特許侵害で）訴えないことを誓うのです。
MITライセンスは、他の多くのFLOSSライセンスとの互換性を提供する。

<!-- Further reading: -->
さらに読む：

* [Apacheライセンス Version 2.0](https://opensource.org/licenses/Apache-2.0)
* [MITライセンス](https://opensource.org/licenses/MIT)
* [お読みください: Rustライセンスが変更されました (ほんのちょっとだけ)](https://mail.mozilla.org/pipermail/rust-dev/2012-November/002664.html)
* [Apacheのデュアルライセンスの理由](https://internals.rust-lang.org/t/rationale-of-apache-dual-licensing/8952)
* [Apache 2.0の特許条項は何に対して保護されているのか？](https://opensource.stackexchange.com/questions/1881/against-what-does-the-apache-2-0-patent-clause-protect)
* [Apache 2ライセンスのGPLv2コンビネーションの例外](https://blog.gerv.net/2016/09/gplv2-combination-exception-for-the-apache-2-license/)
