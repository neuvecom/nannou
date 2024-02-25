<!-- # PR Checklist -->
# PRチェックリスト

<!-- When creating a PR, there are a few things you can do to help the process of landing your changes go smoothly: -->
PRを作成する際、変更をスムーズに着地させるためにできることがいくつかあります：

<!-- - **Code Formatting** - The most common step to forget is running `cargo fmt --all` (I forget all the time)! This step ensures there is a consistent style across nannou's codebase.
- **Errors** - All changes must build successfully, and all tests must complete successfully before we can merge each PR. Keep in mind that running tests locally can take a loooooong time, so sometimes it can be easier to open your PR and let the repo bot check for you. 
- **Warnings** - Make sure to address any lingering code warnings before your last commit. Keep in mind that sometimes warnings already exist due to changes in the compiler's linter between versions. Try to at least make sure that your changes do not add any new ones 😀
- **Check Examples** - Make sure the examples still work by running `cargo run --bin run_all_examples`. This executes a script that builds and runs　all the examples in the project. You need to do a manual check to see if examples have failed to run successfully (e.g. check for wgpu validation errors).
- **Documentation** - If you have made any changes that could benefit from updating some code documentation, please be sure to do so! Try to put yourself in the shoes of someone reading your code for the first time.
- **Changelog** - [The changelog][nannou-changelog] acts as a human-friendly history of the repo that becomes especially useful to community members when updating between different versions of nannou. Be sure to add your changes to `guide/src/changelog.md`.
- **PR Comment** - Be sure to add the following to your PR to make it easier for reviewers to understand and land your code:
    - **Motivation** for changes. What inspired the PR? Please link to any related issues.
    - **Summary** of changes. Anything that might help the reviewer to understand your what your changes do will go a long way! -->
- **コードのフォーマット** - 一番忘れがちなステップは、`cargo fmt --all` を実行することです（私はいつも忘れてしまいます）！このステップによって、nannouのコードベース全体で一貫したスタイルが保たれます。
- **エラー** - 各PRをマージする前に、すべての変更が正常にビルドされ、すべてのテストが正常に完了する必要があります。ローカルでテストを実行すると長い時間がかかるので、PRをオープンしてレポボットにチェックさせる方が簡単な場合もあることを覚えておいてください。
- **警告** - 最後のコミットの前に、残っているコードの警告に対処してください。バージョン間でコンパイラのリンターが変更されたために、すでに警告が存在していることがあることを覚えておいてください。少なくとも、あなたの変更によって新たな警告が追加されないように注意してください。
- **サンプルをチェックする** - `cargo run --bin run_all_examples` を実行して、サンプルがまだ動作していることを確認してください。これは、プロジェクト内の全てのサンプルをビルドして実行するスクリプトを実行します。サンプルが正常に実行できない場合は、手動でチェックする必要があります（例えば、wgpuの検証エラーをチェックする）。
- **ドキュメンテーション** - コード・ドキュメンテーションを更新することで役に立つような変更を加えた場合は、必ずそうしてください！あなたのコードを初めて読む人の立場になって考えてみてください。
- **変更履歴** - [変更履歴][nannou-changelog]はレポジトリの履歴として、特にコミュニティメンバーが異なるバージョンのnannouを更新する際に役立ちます。変更点は必ず `guide/src/changelog.md` に追加してください。
- **PRコメント** - あなたのコードをレビュアーが理解し、着地しやすくするために、PRには必ず以下を追加してください：
    - 変更の**動機**。PRのきっかけは何ですか？関連する問題があればリンクしてください。
    - 変更点の**概要**。レビュアーがあなたの変更点を理解する助けになるようなものであれば、何でもかまいません！

<!-- If you forget one of these steps before making your PR, don't panic! The nannou repo has a CI (continuous integration) bot that will check for some of these steps and notify you if anything is out of order. Once the bot checks pass, a community member will review the rest. -->
PRを作成する前にこれらのステップの一つを忘れてしまっても、慌てないでください！nannouレポにはCI（継続的インテグレーション）ボットがあり、これらのステップのいくつかをチェックし、何か問題があれば通知してくれます。ボットのチェックが通ったら、コミュニティメンバーが残りをレビューします。

[nannou-changelog]: https://guide.nannou.cc/changelog.html
