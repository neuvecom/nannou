<!-- # Tutorials -->
# チュートリアル

<!-- In the previous chapter we prepared everything needed to start our own Nannou project! In this chapter, we will take a more focused look at all of the different features we can add to our Nannou project. -->
前章では、Nannouプロジェクトを始めるために必要なものをすべて準備しました！この章では、Nannouプロジェクトに追加できる様々な機能について、より焦点を絞って見ていきます。

<!-- If you are new to Nannou or Rust we recommend starting with the "Basics" tutorials before going on. If you are feeling more confident, feel free to choose your own adventure through the following tutorials depending on what you want to add to your project! -->
NannouやRustが初めての方は、「基礎」チュートリアルから始めることをお勧めします。もし自信があるようでしたら、以下のチュートリアルをご自分のプロジェクトに追加したい内容に合わせて自由に選んでください！

<!-- ## Rust Basics -->
## Rustの基礎

<!-- Tutorials for learning the basics of Rust with nannou. -->
nannouでRustの基礎を学ぶためのチュートリアル。 

- [Rustの変数](https://doc.rust-lang.org/book/ch03-01-variables-and-mutability.html)
- [Rustのコントロールフロー](https://doc.rust-lang.org/book/ch03-05-control-flow.html)
- [Rustの機能](https://doc.rust-lang.org/book/ch03-03-how-functions-work.html)

<!-- ## Nannou Basics -->
## Nannouの基礎

<!-- A suite of tutorials for getting familiar with the Nannou environment. -->
Nannouの環境に慣れるためのチュートリアル集。

- [Nannouアプリの解剖](/tutorials/basics/anatomy-of-a-nannou-app.md)
- [スケッチを描く](/tutorials/basics/draw-a-sketch.md)
- [スケッチ vs アプリ](/tutorials/basics/sketch-vs-app.md)
- [Windowの調整](/tutorials/basics/window-coordinates.md)
- Nannou events

<!-- ## Drawing -->
## 描画

<!-- Working with Nannou's `Draw` API - a simple approach of coding graphics. -->
Nannouの `Draw` API を使った作業 - グラフィックをコーディングするシンプルなアプローチ。

- [2D shapesの描画](/tutorials/draw/drawing-2d-shapes.md)
- [円のアニメーション](/tutorials/draw/animating-a-circle.md)
- [画像を描く](/tutorials/draw/drawing-images.md)
- 3D shapesの描画
- meshesの描画

<!-- ## Windowing -->
## ウィンドウ

<!-- Walk-throughs for creating and working with one or more windows. -->
1つまたは複数のウィンドウを作成して作業するためのウォークスルー。

<!-- - Building a custom window
- Creating multiple windows
- Drawing to different windows
- Fullscreen on startup
- Automatically positioning windows -->
- カスタムウィンドウの作成
- 複数のウィンドウを作成する
- 異なるウィンドウへの描画
- 起動時のフルスクリーン
- ウィンドウの自動配置

## GUI

<!-- How to create a GUI (Graphical User Interface) for you Nannou project. -->
NannouプロジェクトのGUI（グラフィカル・ユーザー・インターフェイス）の作り方。

<!-- *NOTE: It might be best to wait for [#383](https://github.com/nannou-org/nannou/issues/383) before addressing these.* -->
*注：[#383](https://github.com/nannou-org/nannou/issues/383)を待ってから対処するのがベストかもしれません。

<!-- - Creating a UI
- Exploring available UI widgets
- Multi-window UI -->
- UIの作成
- 利用可能なUIウィジェットの探索
- マルチウィンドウUI

## Audio

<!-- A suite of guides for working with audio in Nannou. -->
Nannouでオーディオを扱うためのガイド一式。

<!-- - Setting up audio output
- Setting up audio input
- Selecting specific audio devices
- Playing an audio file
- Basic audio synthesis
- Many channel audio streams
- Feeding audio input to output
- Visualising audio -->
- オーディオ出力の設定
- オーディオ入力の設定
- 特定のオーディオデバイスを選択する
- オーディオファイルを再生する
- 基本的なオーディオ合成
- 多チャンネルのオーディオストリーム
- オーディオ入力を出力に送る
- オーディオの視覚化

## Video

<!-- Loading, playing and recording video in Nannou. -->
Nannouでのビデオの読み込み、再生、録画。

<!-- - Drawing video
- Recording a window to video
- Manipulating video playback -->
- ビデオを描く
- ウィンドウをビデオに録画する
- ビデオの再生を操作する

## WGPU

<!-- Understanding the lower level that underlies all graphics in Nannou. -->
Nannouのすべてのグラフィックの根底にある下層を理解する。

<!-- - What is WGPU?
- The graphics pipeline
- Compute shaders
- Fragment shaders
- Vertex shaders -->
- WGPUとは？
- グラフィックスパイプライン
- コンピュートシェーダー
- フラグメントシェーダー
- バーテックスシェーダー

<!-- ## Projection Mapping -->
## プロジェクションマッピング

<!-- Getting started with using Nannou for projection mapping. -->
Nannouのプロジェクションマッピングを始めよう

<!-- - Basic quad-warping. -->
- 基本的な4回転ワープ。

## LASERs

<!-- Detecting and outputting to LASER DACs on a network. -->
ネットワーク上のLASER DACを検出し、出力する。

<!-- - Connecting to a LASER.
- Detecting LASER DACs.
- Tweaking LASER interpolation and optimisations. -->
- LASERへの接続
- LASER DACの検出
- LASERの補間と最適化の調整

## OSC

- [OSC入門](/tutorials/osc/osc-introduction.md).
- [OSC送信](/tutorials/osc/osc-sender.md).
- OSCの受信

## DMX

<!-- Working with DMX over the network via sACN. -->
sACN経由でネットワーク上のDMXと連携。

<!-- - Working with the sacn crate. -->
- サクンクレートでの作業。

## Serial over USB

<!-- Working with Serial data in a cross-platform manner. -->
クロスプラットフォームでシリアルデータを扱う。

<!-- - Reading USB serial data.
- Writing USB serial data. -->
- USBシリアルデータの読み込み
- USBシリアルデータの書き込み

<br>

---

<!-- If you were unable to find what you were looking for above, or if you have an idea for a tutorial not yet present, please feel free to create an issue or a pull request! -->
上記でお探しのものが見つからなかった場合、またはまだ存在しないチュートリアルのアイデアがある場合は、遠慮なく課題またはプルリクエストを作成してください！
