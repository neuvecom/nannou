<!-- # Installing Rust -->
# Rustのインストール

<!-- Nannou is a library written for the [Rust programming language](https://www.rust-lang.org/). Thus, the first step is to install Rust! -->
Nannouは[Rustプログラミング言語](https://www.rust-lang.org/)用に書かれたライブラリです。したがって、最初のステップはRustをインストールすることである！

<!-- To install Rust on **Windows**, download and run the installer from [here](https://www.rust-lang.org/tools/install). If you're on **macOS** or **Linux**, open up your terminal, copy the text below, paste it into your terminal and hit enter. -->
Rustを**Windows**にインストールするには、[こちら](https://www.rust-lang.org/tools/install)からインストーラをダウンロードして実行してください。**macOS**または**Linux**の場合は、ターミナルを開いて以下のテキストをコピーし、ターミナルに貼り付けてエンターキーを押してください。

```bash
curl https://sh.rustup.rs -sSf | sh
```

<!-- Now Rust is installed! -->
これでRustがインストールされた！

<!-- Next we will install some tools that help IDEs do fancy things like auto-completion and go-to-definition. -->
次に、IDEがオートコンプリートやgo-to-definitionのような派手なことをするのを助けるツールをいくつかインストールする。

```bash
rustup component add rust-src rustfmt-preview rust-analysis
```

<!-- Please see [this link](https://www.rust-lang.org/tools/install) if you would like more information on the Rust installation process. -->
Rustのインストールプロセスについて、より詳しい情報をお知りになりたい方は、この[リンク](https://www.rust-lang.org/tools/install)をご覧ください。
