<!-- # the nannou guide -->
# Nannouガイド

<!-- The one-stop-shop for everything someone might want to know about nannou! -->
Nannouに関するあらゆる情報をワンストップで提供する！

<!-- ## Working on the Book -->
## Bookに取り組む

<!-- The easiest way to build, render and read the book is as follows: -->
Bookを作り、レンダリングし、読む最も簡単な方法は以下の通りである：

<!-- - Clone the repo. -->
- リポジトリをクローンする。
  ```bash
  git clone https://github.com/nannou-org/nannou
  cd nannou/guide
  ```
<!-- - Install the [Rust markdown book](https://github.com/rust-lang-nursery/mdBook) tool. -->
- [Rust markdown book](https://github.com/rust-lang-nursery/mdBook) ツールをインストールする。
  ```
  cargo install mdbook
  ```
<!-- - Make `mdbook` watch the repo, re-build on file changes and host at `localhost:3000`. -->
- `mdbook`にリポジトリを監視させ、ファイル変更時に再ビルドし、`localhost:3000`でホストする。
  ```
  mdbook serve
  ```
<!-- - Open your browser and point it to `localhost:3000` to find the rendered markdown book. -->
- ブラウザを開き、`localhost:3000`を指定して、HTMLにレンダリングされたマークダウンBookを確認する。

<!-- You should now have a hot-loading environment where you can edit the book markdown and see the results rendered in your browser each time you save a file. -->
これで、Bookのマークダウンを編集し、ファイルを保存するたびにブラウザに表示される結果を確認できる、ホットロード環境が整ったはずだ。

<!-- ## Running Tests -->
## テストの実行

<!-- To run the tests, do the following: -->
テストを実行するには、以下のようにする：

```bash
cd book-tests
cargo test
```

<!-- The `build.rs` will retrieve all `rust` code snippets from the markdown files and generate a test file so that they all may be tested during `cargo test`. -->
`build.rs`はマークダウンファイルからすべての`rust`のコード・スニペットを取得し、`cargo test`でテストできるようにテスト・ファイルを生成する。

<!-- We do this rather than using the `mdbook test` as `mdbook test` does not support including remote dependencies. -->
`mdbook test`はリモートの依存関係を含むことをサポートしていないため、`mdbook test`を使うのではなく、このようにする。

<!-- ## License -->
## ライセンス

<!-- Licensed under either of -->
任意で以下のいずれかのライセンスが適用されます。

 <!-- * Apache License, Version 2.0, ([LICENSE-APACHE](LICENSE-APACHE) or http://www.apache.org/licenses/LICENSE-2.0) -->
* Apache ライセンス、バージョン 2.0, ([LICENSE-APACHE](LICENSE-APACHE) または http://www.apache.org/licenses/LICENSE-2.0)
 <!-- * MIT license ([LICENSE-MIT](LICENSE-MIT) or http://opensource.org/licenses/MIT) -->
* MIT ライセンス ([LICENSE-MIT](LICENSE-MIT) または http://opensource.org/licenses/MIT)

<!-- at your option. -->

<!-- **Contributions** -->
**貢献**

<!-- Unless you explicitly state otherwise, any contribution intentionally submitted for inclusion in the work by you, as defined in the Apache-2.0 license, shall be dual licensed as above, without any additional terms or conditions. -->
あなたが明示的に別段の定めをしない限り、Apache-2.0ライセンスで定義されているように、あなたによって作品に含めるために意図的に提出された貢献は、いかなる追加条項や条件もなく、上記のように二重ライセンスされるものとします。
