# nannou [![Actions Status](https://github.com/nannou-org/nannou/workflows/nannou/badge.svg)](https://github.com/nannou-org/nannou/actions) [![Backers on Open Collective](https://opencollective.com/nannou/backers/badge.svg)](https://guide.nannou.cc/contributors.html#backers) [![Sponsors on Open Collective](https://opencollective.com/nannou/sponsors/badge.svg)](https://guide.nannou.cc/contributors.html#sponsors)

![nannou_logo](https://i.imgur.com/1ldLFfj.png)

<!-- An open-source creative-coding toolkit for Rust. -->
Rust用のオープンソースのクリエイティブ・コーディング・ツールキット。

<!-- **nannou** is a collection of code aimed at making it easy for artists to express themselves with simple, fast, reliable, portable code.  Whether working on a 12-month installation or a 5 minute sketch, this framework aims to give artists easy access to the tools they need. -->
**nannou**は、アーティストがシンプルで、速く、信頼性が高く、ポータブルなコードで自分自身を表現することを容易にすることを目的としたコードのコレクションです。  12ヶ月のインスタレーションでも5分のスケッチでも、このフレームワークはアーティストが必要なツールに簡単にアクセスできることを目指しています。

<!-- The project was started out of a desire for a creative coding framework inspired by Processing, OpenFrameworks and Cinder, but for Rust. <sup>Named after [this](https://www.youtube.com/watch?v=A-Pkx37kYf4).</sup> -->
このプロジェクトは、Processing、OpenFrameworks、Cinderにインスパイアされた、Rust用のクリエイティブなコーディングフレームワークが欲しいという願望から始まった。<sup>[これ](https://www.youtube.com/watch?v=A-Pkx37kYf4) にちなんで命名。</sup>

|     |     |     |
| --- |:---:| ---:|
| [![1](https://i.imgur.com/kPn91tW.gif)](https://github.com/nannou-org/nannou/blob/master/examples/draw/draw_polygon.rs) | [![2](https://i.imgur.com/gaiWHZX.gif)](https://github.com/nannou-org/nannou/blob/master/examples/ui/egui/simple_ui.rs) | [![3](https://i.imgur.com/lm4RI4N.gif)](https://github.com/nannou-org/nannou/blob/master/examples/draw/draw_polyline.rs) |

<!-- ### A Quick Note -->
### メモ

<!-- It is still early days and there is a lot of work to be done. Feel free to help out! -->
まだ日が浅く、やるべきことはたくさんある。遠慮なく手伝ってほしい！

<!-- ## The Guide -->
## ガイド
※日本語版ガイドは準備中です。下記は英語版にリンクします。

- [**Welcome!**](https://www.guide.nannou.cc/)
- [**Why Nannou?**](https://www.guide.nannou.cc/why_nannou.html)
  - [**Goals**](https://www.guide.nannou.cc/why_nannou.html#goals)
  - [**Why Rust?**](https://www.guide.nannou.cc/why_nannou.html#why-rust)
  - [**FOSS Licensing**](https://guide.nannou.cc/why_nannou.html#why-the-apachemit-dual-licensing)
- [**Getting Started**](https://www.guide.nannou.cc/getting_started.html)
  - [**Platform-specific Setup**](https://www.guide.nannou.cc/getting_started/platform-specific_setup.html)
  - [**Installing Rust**](https://www.guide.nannou.cc/getting_started/installing_rust.html)
  - [**Editor Setup**](https://www.guide.nannou.cc/getting_started/editor_setup.html)
  - [**Running Examples**](https://www.guide.nannou.cc/getting_started/running_examples.html)
  - [**Create A Project**](https://www.guide.nannou.cc/getting_started/create_a_project.html)
  - [**Upgrading to a New Release**](https://guide.nannou.cc/getting_started/upgrading.html)
- [**Tutorials**](https://www.guide.nannou.cc/tutorials.html)
- [**Community Tutorials**](https://www.guide.nannou.cc/community_tutorials.html)
- [**Developer Reference**](https://www.guide.nannou.cc/developer_reference.html)
- [**API Reference**](https://www.guide.nannou.cc/api_reference.html)
- [**Showcases**](https://www.guide.nannou.cc/showcases.html)
- [**Changelog**](https://www.guide.nannou.cc/changelog.html)
- [**Contributors**](https://www.guide.nannou.cc/contributors.html)
- [**Code of Conduct**](https://guide.nannou.cc/code_of_conduct.html)

<!-- ## Examples -->
## 活用例

<!-- The following collection of **examples** are a great way to get familiar with nannou. -->
以下の**サンプル集**は、nannouに慣れるための素晴らしいお手本である。

| **ディレクトリ** | **説明** |
| --- | --- |
| [**`examples/`**](./examples) | Nannouの使い方を示す実例集! |
| [**`generative_design/`**](./generative_design) | [Generative Gestaltung](http://www.generative-gestaltung.de/) の例をp5.jsからnannouに移植。 |
| [**`nature_of_code/`**](./nature_of_code) | [Nature of Code](https://natureofcode.com/) の例をProcessingからnannouに移植。|

<!-- If you spot an example that interests you, you may run it with the following: -->
興味のある作例を見つけたら、次のように実行することができる：

```
cargo run --release --example <example_name>
```

<!-- where `<example_name>` is the example's file name without the `.rs`. Note that the first run might take a while in order to build nannou first, but consecutive runs should be much quicker. -->
ここで `<example_name>` は `.rs` を除いたサンプルのファイル名である。nannouを最初にビルドするため、最初の実行には時間がかかるかもしれないが、連続した実行はずっと速くなるはずである。

<!-- ## Libraries -->
## ライブラリー

<!-- The following nannou **libraries** are included within this repository. -->
このリポジトリには以下の nannou **ライブラリ**が含まれています。

| **ライブラリ** | **リンク** | **説明** |
| --- | --- | --- |
| [**`nannou`**](./nannou) | [![Crates.io](https://img.shields.io/crates/v/nannou.svg)](https://crates.io/crates/nannou) [![docs.rs](https://docs.rs/nannou/badge.svg)](https://docs.rs/nannou/) | アプリ、スケッチ、グラフィック、ウィンドウ、UI。 |
| [**`nannou_audio`**](./nannou_audio) | [![Crates.io](https://img.shields.io/crates/v/nannou_audio.svg)](https://crates.io/crates/nannou_audio) [![docs.rs](https://docs.rs/nannou_audio/badge.svg)](https://docs.rs/nannou_audio/) | オーディオホスト、デバイス、ストリーム。 |
| [**`nannou_core`**](./nannou_core) | [![Crates.io](https://img.shields.io/crates/v/nannou_core.svg)](https://crates.io/crates/nannou_core) [![docs.rs](https://docs.rs/nannou_core/badge.svg)](https://docs.rs/nannou_core/) | ヘッドレス、エンベデッド、ライブラリのためのジャスト・ザ・コア。 |
| [**`nannou_egui`**](./nannou_egui) | [![Crates.io](https://img.shields.io/crates/v/nannou_egui.svg)](https://crates.io/crates/nannou_egui) [![docs.rs](https://docs.rs/nannou_egui/badge.svg)](https://docs.rs/nannou_egui/) | nannouアプリでegui UIを作成するために。 |
| [**`nannou_isf`**](./nannou_isf) | [![Crates.io](https://img.shields.io/crates/v/nannou_isf.svg)](https://crates.io/crates/nannou_isf) [![docs.rs](https://docs.rs/nannou_isf/badge.svg)](https://docs.rs/nannou_isf/) | インタラクティブなシェーダーフォーマットパイプライン。 |
| [**`nannou_laser`**](./nannou_laser) | [![Crates.io](https://img.shields.io/crates/v/nannou_laser.svg)](https://crates.io/crates/nannou_laser) [![docs.rs](https://docs.rs/nannou_laser/badge.svg)](https://docs.rs/nannou_laser/) | LASERデバイス、ストリーム、パスの最適化。 |
| [**`nannou_mesh`**](./nannou_mesh) | [![Crates.io](https://img.shields.io/crates/v/nannou_mesh.svg)](https://crates.io/crates/nannou_mesh) [![docs.rs](https://docs.rs/nannou_mesh/badge.svg)](https://docs.rs/nannou_mesh/) | チャンネルからメッシュを合成するAPI。 |
| [**`nannou_osc`**](./nannou_osc) | [![Crates.io](https://img.shields.io/crates/v/nannou_osc.svg)](https://crates.io/crates/nannou_osc) [![docs.rs](https://docs.rs/nannou_osc/badge.svg)](https://docs.rs/nannou_osc/) | シンプルなOSC送受信機。|
| [**`nannou_wgpu`**](./nannou_wgpu) | [![Crates.io](https://img.shields.io/crates/v/nannou_wgpu.svg)](https://crates.io/crates/nannou_wgpu) [![docs.rs](https://docs.rs/nannou_wgpu/badge.svg)](https://docs.rs/nannou_wgpu/) | WGPUヘルパーとエクステンション。 |

<!-- ## Tools -->
## ツール

<!-- A couple of tools are also included, though there some issues we would like to　address before we can recommend using them just yet! -->
いくつかのツールも含まれているが、まだ使用をお勧めする前に解決したい問題がある！

| **ツール** | **リンク** | **説明** |
| --- | --- | --- |
| [**`nannou_new`**](./nannou_new) | [![Crates.io](https://img.shields.io/crates/v/nannou_new.svg)](https://crates.io/crates/nannou_new) | nannouプロジェクトのジェネレーター。 |
| [**`nannou_package`**](./nannou_package) | [![Crates.io](https://img.shields.io/crates/v/nannou_package.svg)](https://crates.io/crates/nannou_package) | nannouのアプリを配布用にパッケージングする。 |

<!-- ## Links -->
## リンク

- [Website](https://www.nannou.cc/)
- [Guide](https://www.guide.nannou.cc/)
- [Slack](https://communityinviter.com/apps/nannou/join-nannou-slack) / [Matrix](https://matrix.to/#/+nannou:matrix.org)
- [Support nannou!](https://opencollective.com/nannou)
