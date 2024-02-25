<!-- # Publishing New Versions -->
# 新バージョンの公開

<!-- The nannou repo allows community members to open a PR for publishing a new version of any or all of the nannou crates. This makes it much easier for maintainers to publish a new release - all we have to do is accept your PR! -->
nannou repoでは、コミュニティメンバーがnannouクレートの一部または全部の新バージョンを公開するためのPRをオープンすることができます。これにより、メンテナは新しいリリースを発行しやすくなります！

<!-- If you would like to see a new version of a crate published, follow these steps: -->
新バージョンのクレートの公開を希望する場合は、以下の手順に従ってください：

<!-- ## Choose a Version -->
## バージョン選択

<!-- The version to use for the next version of the crate(s) you wish to publish will depend on the changes that have been made to the crate(s). The nannou crates follow the rust convention which you can read about [here][cargo-toml-version]. -->
公開したいクレートの次のバージョンに使用するバージョンは、クレートに加えられた変更に依存します。nannouのクレートは、[こちら][cargo-toml-version]を参照してください。

<!-- > _**Hot tip**! Each of the numbers in a crate version has its own name:_ -->
> ホットなヒントクレート・バージョンの各番号にはそれぞれ名前があります。
>
> ```
> MAJOR.MINOR.PATCH
> ```
><!-- > _E.g. in the version `0.15.3` the `0` is the "major" version, the `15` is the "minor" version and the `3` is the "patch" or "tiny" version. Keep an eye out for these names when reading about versioning in Rust._ -->
> 例えば、バージョン `0.15.3` では、`0` が「メジャー」バージョン、`15` が「マイナー」バージョン、そして `3` が「パッチ」または「小さな」バージョンです。
> Rust._のバージョン管理について読むときは、これらの名前に注意してください。

<!-- Also necessary to keep in mind is that nannou synchronises versions that represent a breaking change (e.g. a change from `0.15.3` to `0.16.0` or `1.0.4` to `2.0.0`). In these cases, all crates with the name `nannou` or `nannou_*` should be published together with the same version. This version synchronisation makes it easier for users to intuit compatible versions of nannou crates without the need to manually check all of the dependency versions on crates.io. -->
また、nannou はブレークチェンジを表すバージョンを同期させます（例えば `0.15.3` から `0.16.0`、`1.0.4` から `2.0.0`）。このような場合、`nannou` または `nannou_*` という名前を持つすべてのクレートを同じバージョンで公開する必要がある。このバージョン同期により、ユーザーはcrates.ioの依存バージョンをすべて手動でチェックすることなく、nannouクレートの互換バージョンを直感的に理解しやすくなります。

<!-- ## Update Cargo.toml -->
## Cargo.tomlを更新する

<!-- There are two sections of the `Cargo.toml` file(s) that will need updating. -->
`Cargo.toml`ファイルには、更新が必要なセクションが2つある。

<!-- 1. The `version` field under the `[package]` section.
2. The `version` field of the `[dependencies]` and `[dev-dependencies]` sections of each crate in the repo that uses the crate. E.g. the `nannou` crate is a dependency of `nannou_isf`. If we wish to update the version of `nannou`, we will also need to update the version of `nannou` specified in the `[dependencies]` section of `nannou_isf`. -->
1. `[package]` セクションの下の `version` フィールド。
2. クレートを使っているリポジトリの各クレートの `[dependencies]` セクションと `[dev-dependencies]` セクションの `version` フィールド。例えば、 `nannou` クレートは `nannou_isf` の依存関係である。`nannou` のバージョンを更新したい場合は、`nannou_isf` の `[dependencies]` セクションにある `nannou` のバージョンも更新する必要がある。

<!-- This can be quite a lot of Cargo.toml changes in the case that you are updating the version of all of the `nannou_*` crates! -->
`nannou_*`クレートすべてのバージョンを更新する場合、Cargo.tomlの変更量はかなり多くなります！

<!-- To make this easier, the nannou repo includes a small program at `scripts/set_version`. You can use it like so: -->
これを簡単にするために、nannouのレポには`scripts/set_version`に小さなプログラムが含まれています。次のように使うことができる：

```
cargo run --bin set_version -- "0.42.0"
```

This will:
こうなる：

<!-- - Find all crates via the cargo workspace Cargo.toml file.
- Sets the specified version number for each of the `nannou*` packages and updates each of their respective `nannou*` dependencies.
- Edits their Cargo.toml files with the result. -->
- カーゴワークスペース Cargo.toml ファイルからすべてのクレートを検索する。
- それぞれの `nannou*` パッケージに指定されたバージョン番号を設定し、それぞれの `nannou*` 依存パッケージを更新する。
- その結果でそれぞれの Cargo.toml ファイルを編集する。

<!-- ## Update the Guide -->
## ガイドを更新する

<!-- There are two places where we must update the version in the guide: -->
ガイドのバージョンを更新しなければならない箇所が2箇所ある：

<!-- 1. The **Changelog**. You can find it at `guide/src/changelog.md`. See the most recent version in the guide for a demonstration of how to update the version. For the most part, this just involves adding a date and release heading under the `Unreleased` heading.
2. Update the nannou version number in step 3 of the `guide/src/getting_started/create_a_project.md` section.  See the `[dependencies]` section of the code snippet. -->
1. **チェンジログ** `guide/src/changelog.md`にあります。バージョンの更新方法については、ガイドの最新版を参照してください。ほとんどの場合、`Unreleased`の見出しの下に日付とリリースの見出しを追加するだけです。
2. `guide/src/getting_started/create_a_project.md`セクションのステップ3にあるnannouのバージョン番号を更新してください。コードスニペットの `[dependencies]` セクションを参照してください。

<!-- Otherwise, we avoid referring to specific versions in the guide to make updating easier. If you happen to be familiar with grep, this command can help you to double check that there are no more places to update: -->
そうでなければ、アップデートを容易にするため、ガイドでは特定のバージョンに言及しないようにしている。もしあなたがgrepに慣れているのであれば、このコマンドは更新すべき場所がもうないことを再確認するのに役立つだろう：

```
grep -nr "= \"0.14\"" guide/
```

<!-- where `0.14` would be replaced with the beginning of the previous version of `nannou`. This should should list the files and line numbers where the previous version still exists and likely needs updating. -->
ここで、`0.14`は以前のバージョンの`nannou`の先頭に置き換えられる。これにより、以前のバージョンがまだ存在し、更新が必要であると思われるファイルと行番号がリストアップされるはずである。

<!-- ## Open a PR -->
## PRを開設する

<!-- Now you should be ready to open a PR! Be sure to follow the [PR Checklist](./pr-checklist.md). -->
<!-- Once your PR is reviewed and merged, the nannou repo's CI bot will automatically publish the new versions. -->
<!-- Congrats, you just published some new goodies to crates.io for the nannou community! -->
これでPRを開設する準備が整いました！[PRチェックリスト](./pr-checklist.md)に必ず従ってください。  
あなたのPRがレビューされ、マージされると、nannouリポジトリのCIボットが自動的に新しいバージョンを公開します。  
おめでとうございます。nannouコミュニティのためにcrates.ioに新しいグッズを公開しましたね！

[cargo-toml-version]: https://doc.rust-lang.org/cargo/reference/manifest.html#the-version-field
