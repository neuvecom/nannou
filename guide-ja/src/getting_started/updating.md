<!-- # Updating nannou -->
# nannouの更新

<!-- You can update to a new version of nannou by editing your `Cargo.toml` file to use the new crate. For version 0.12 add the line -->
nannouの新しいバージョンにアップデートするには、`Cargo.toml`ファイルを編集して新しいクレートを使用します。バージョン0.12では以下の行を追加してください。

```toml
nannou = "0.12"
```

<!-- Then within the nannou directory run the following to update all dependencies: -->
次に、nannouディレクトリ内で以下を実行し、すべての依存関係を更新する：

```bash
cargo update
```

<!-- ## Updating Rust. -->
## Rustを更新

<!-- From time to time, a nannou update might require features from a newer version of rustc. For example, nannou 0.12 is known to require at least rustc 1.35.0. In these cases, you can update your rust toolchain to the latest version by running the following: -->
時々、nannouのアップデートは、より新しいバージョンのrustcの機能を必要とするかもしれません。例えば、nannou 0.12は少なくともrustc 1.35.0を必要とすることが知られています。このような場合、以下を実行することでrustツールチェーンを最新バージョンに更新することができます：

```bash
rustup update
```
