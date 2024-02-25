<!-- # Running Examples -->
# サンプルコードを実行する

<!-- The easiest way to get familiar with nannou is to explore the examples. -->
nannouを使いこなす最も簡単な方法は、サンプルを調べることだ。

<!-- Nannou provides three collections of examples: -->
Nannouは3つの例を挙げている：

| **パス** | **説明** |
| --- | --- |
| [**`examples/`**](https://github.com/nannou-org/nannou/tree/master/examples) | Nannouのデモンストレーションを分類した実例集。 |
| [**`generative_design/`**](https://github.com/nannou-org/nannou/tree/master/generative_design) | Generative Gestaltung](http://www.generative-gestaltung.de/)の例をp5.jsからnannouに移植。 |
| [**`nature_of_code/`**](https://github.com/nannou-org/nannou/tree/master/nature_of_code) | [Nature of Code](https://natureofcode.com/)の例をProcessingからnannouに移植。 |

<!-- To get the examples we can clone the nannou repository. -->
サンプルを入手するには、nannouリポジトリをクローンする。

```bash
git clone https://github.com/nannou-org/nannou
```

<!-- If you do not have `git` installed you can press the "Clone or download" button at the top of this page and then press "Download .zip". -->
`git`がインストールされていない場合は、このページの一番上にある "Clone or download"ボタンを押して、"Download.zip"を押してください。

<!-- Now, change the current directory to `nannou`. -->
ここで、カレントディレクトリを`nannou`に変更する。

```bash
cd nannou
```

<!-- Run the example using cargo! -->
cargoを使ってサンプルを実行する！

```bash
cargo run --release --example draw
```

<!-- The `--release` flag means we want to build with optimisations enabled. -->
`release`フラグは、最適化を有効にしてビルドすることを意味する。

<!-- The value passed via the `--example` flag matches the `name` property of an entry within the `[[examples]]` table of the package's `Cargo.toml` file. The matched entry's `path` property points to the source file to build: -->
`example`フラグで渡された値は、パッケージの `Cargo.toml` ファイルの `[[examples]]` テーブル内のエントリの `name` プロパティにマッチします。マッチしたエントリの `path` プロパティはビルドするソースファイルを指す：

```toml
# Draw
[[example]]
name = "draw"
path = "draw/draw.rs"
```

<!-- If we were to look through the nature of code directory and decide we want to run the following example: -->
コード・ディレクトリの性質に目を通し、次の例を実行したいと決めたとする：

```toml
# Chapter 1 Vectors
[[example]]
name = "1_1_bouncingball_novectors"
path = "chp_01_vectors/1_1_bouncingball_novectors.rs"
```

<!-- We could do so with the following: -->
次のようにすればいい：

```bash
cargo run --release --example 1_1_bouncingball_novectors
```

<!-- In general, the name of the example will almost always be the file name without the `.rs` extension. -->
一般的に、サンプルの名前はほとんどの場合、拡張子 `.rs` を除いたファイル名になります。

<!-- If you are compiling nannou for the first time you will see cargo download and build all the necessary dependencies. This might take a while! Luckily, we only have to wait for this the first time. -->
初めてnannouをコンパイルする場合、cargoが必要な依存関係をすべてダウンロードし、ビルドするのが見えます。これにはしばらく時間がかかるかもしれない！幸運なことに、これを待つ必要があるのは最初の1回だけです。

![cargo](https://i.imgur.com/5OBNqMB.gif)

<!-- Once the example compiles you should see the following window appear. -->
サンプルがコンパイルされると、次のようなウィンドウが表示されるはずだ。

![draw_HD](https://i.imgur.com/HVVamUI.gif)

<!-- To run any of the other examples, replace `draw` with the name of the desired example. -->
他の例を実行するには、`draw`を希望する例の名前に置き換える。
