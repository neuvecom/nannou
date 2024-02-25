<!-- # Platform-specific Setup -->
# プラットフォーム固有のセットアップ

<!-- Before we get started, let's make sure we have all the necessary ingredients for installing Rust and building nannou projects. -->
始める前に、Rustのインストールとnannouプロジェクトの構築に必要な材料がすべて揃っていることを確認しよう。

<!-- Depending on what OS you are running, you might require an extra step or two. -->
使っているOSによっては、もう1、2ステップ追加する必要があるかもしれない。

<!-- By the way, if you notice some steps are missing from this section of the guide, feel free to open an issue or PR at [the nannou guide repo](https://github.com/nannou-org/nannou/tree/master/guide)! -->
ところで、このガイドのセクションでいくつかのステップが欠けていることに気づいたら、遠慮なく[the nannou guide repo](https://github.com/nannou-org/nannou/tree/master/guide)でissueかPRを開いてください！

## macOS

<!-- Ensure that you have xcode-tools installed: -->
xcode-toolsがインストールされていることを確認する：

```bash
xcode-select --install
```

<!-- Some examples require that you have `cmake` installed as well. The easiest way to achieve this is to use [Homebrew](https://brew.sh). -->
いくつかの例では `cmake` もインストールしておく必要があります。これを実現する最も簡単な方法は、[Homebrew](https://brew.sh) を使うことです。

```bash
brew install cmake
```

<!-- This should provide all the developer tools needed for building nannou. -->
これで、nannouのビルドに必要な開発者ツールはすべて揃うはずだ。

## Windows

<!-- Rust requires the C++ build tools for Visual Studio. The Rust book has this to say: -->
RustにはVisual Studio用のC++ビルドツールが必要です。Rustの本にはこうある：

<!-- > On Windows, go to [https://www.rust-lang.org/tools/install](https://www.rust-lang.org/tools/install) and follow the instructions for installing Rust. At some point in the installation, you’ll receive a message explaining that you’ll also need the C++ build tools for Visual Studio 2013 or later. The easiest way to acquire the build tools is to install [Build Tools for Visual Studio 2019](https://www.visualstudio.com/downloads/#build-tools-for-visual-studio-2019).
> The tools are in the Other Tools and Frameworks section. -->
> Windows では、[https://www.rust-lang.org/tools/install](https://www.rust-lang.org/tools/install) にアクセスし、Rustのインストール手順に従ってください。インストールのある時点で、Visual Studio 2013以降用のC++ビルドツールも必要であることを説明するメッセージが表示されます。ビルドツールを入手する最も簡単な方法は、[Build Tools for Visual Studio 2019](https://www.visualstudio.com/downloads/#build-tools-for-visual-studio-2019) をインストールすることです。
> ツールは、その他のツールとフレームワークセクションにあります。

## Linux

<!-- Ensure you have the following system packages installed: -->
以下のシステム・パッケージがインストールされていることを確認してください：

- **Basic dev packages**

  <!-- First make sure the basic dev packages are installed. -->
  まず、基本的な開発パッケージがインストールされていることを確認する。
  <!-- - `curl` will be required by `rustup` the rust toolchain manager.
  - `build-essential` will be required by `rustc` the rust compiler for linking.
  - `pkg-config` is used by some build scripts to source information about certain libraries.
  - `alsa` dev packages are required for `nannou_audio`. -->
  - `curl`は `rustup` Rustツールチェーンマネージャーによって必要とされる。
  - `build-essential` は、Rust コンパイラの `rustc` がリンクする際に必要となる。
  - `pkg-config` はビルドスクリプトが特定のライブラリに関する情報を取得するために使用する。
  - `nannou_audio` には `alsa` 開発パッケージが必要である。

  <!-- For Debian/Ubuntu users: -->
  Debian/Ubuntuユーザーの方へ：
  ```bash
  sudo apt-get install curl build-essential python cmake pkg-config
  ```

- **alsa dev package**

  <!-- For Fedora users: -->
  Fedoraユーザーの方へ：
  ```bash
  sudo dnf install alsa-lib-devel
  ```

  <!-- For Debian/Ubuntu users: -->
  Debian/Ubuntuユーザーの方へ：
  ```bash
  sudo apt-get install libasound2-dev
  ```

  <!-- For Arch users: -->
  Archユーザー向け：
  ```bash
  sudo pacman -S alsa-lib
  ```

- **curl lib dev package**

  <!-- Nannou depends on the `curl-sys` crate. Some Linux distributions use　LibreSSL instead of OpenSSL (such as AlpineLinux, Voidlinux, possibly[others](https://en.wikipedia.org/wiki/LibreSSL#Adoption) if manually　installed). -->
  Nannou は `curl-sys` クレートに依存しています。Linuxディストリビューションの中には、OpenSSLの代わりにLibreSSLを使うものがあります（AlpineLinux、Voidlinux、手動でインストールした場合は[その他](https://en.wikipedia.org/wiki/LibreSSL#Adoption)など）。

- **xcb**

  <!-- The XCB library provides inter-operability with Xlib. -->
  XCBライブラリーはXlibとの相互運用性を提供する。

  <!-- For Debian/Ubuntu users: -->
  Debian/Ubuntuユーザーの方へ：
  ```bash
  sudo apt install libxcb-shape0-dev libxcb-xfixes0-dev
  ```

  <!-- You might also need `python3` for the `xcb` crate's build script. -->
  また、`xcb`クレートのビルドスクリプトには `python3` が必要かもしれない。

- **vulkan**

  <!-- Installing Vulkan support on Linux is generally quite easy using your distro's package manager. That said, there may be different driver options to consider depending on your graphics card and tolerance for proprietary software. The following are rough guidelines on how to get going quickly, however if you are at all concerned with finding the approach that suits you best we recommend searching for vulkan driver installation for your graphics card on your distro. -->
  LinuxへのVulkanサポートのインストールは、一般的にディストロのパッケージマネージャを使用して非常に簡単です。とはいえ、お使いのグラフィックカードやプロプライエタリなソフトウェアに対する耐性によって、考慮すべきドライバオプションは異なるかもしれません。以下は、手っ取り早く始めるための大まかなガイドラインですが、自分に合った方法を見つけることに少しでも不安があるのであれば、お使いのディストロでグラフィックカードのvulkanドライバインストールを検索することをお勧めします。

  <!-- For Fedora with AMD graphic cards: -->
  AMDグラフィックカードを搭載したFedora用：
  ```bash
  sudo dnf install vulkan vulkan-info
  ```

  <!-- For Fedora with NVIDIA graphic cards:
  Add the proprietary drivers -->
  NVIDIAグラフィックカード搭載Fedora用：
  プロプライエタリドライバを追加する
  ```bash
  sudo dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
  ```
  <!-- and run -->
  そして
  ```bash
  sudo dnf install xorg-x11-drv-nvidia akmod-nvidia vulkan-tools
  ```

  <!-- For Debian with AMD or Intel graphic cards: -->
  AMD または Intel グラフィックカード搭載の Debian 用：
  ```bash
  sudo apt-get install libvulkan1 mesa-vulkan-drivers vulkan-utils
  ```

  <!-- For Debian with NVIDIA graphic cards: -->
  NVIDIA グラフィックカード搭載 Debian 用：
  ```bash
  sudo apt-get install vulkan-tools
  ```

  <!-- Or, on older versions (pre-Buster i.e., < 10): -->
  あるいは、古いバージョン（バスター以前、つまり10未満）：
  ```bash
  sudo apt-get install vulkan-utils
  ```

  <!-- For Ubuntu users with AMD or Intel graphic cards: -->
  AMDまたはIntelのグラフィックカードを使用しているUbuntuユーザー向け：
  <!-- Add a PPA for the latest drivers -->
  最新ドライバーのPPAを追加する
  ```bash
  sudo add-apt-repository ppa:oibaf/graphics-drivers
  sudo apt-get update
  sudo apt-get upgrade
  ```
  <!-- and run -->
  そして
  ```bash
  sudo apt-get install libvulkan1 mesa-vulkan-drivers vulkan-utils
  ```

  <!-- For Ubuntu users with NVIDIA graphic cards: -->
  NVIDIAグラフィックカードを使用しているUbuntuユーザー向け：
  <!-- Add a PPA for the latest drivers -->
  最新ドライバーのPPAを追加する
  ```bash
  sudo add-apt-repository ppa:graphics-drivers/ppa
  sudo apt-get update
  sudo apt-get upgrade
  ```
  <!-- and run -->
  そして
  ```bash
  sudo apt-get install nvidia-graphics-drivers-396 nvidia-settings vulkan vulkan-utils
  ```

  <!-- For Arch with AMD graphic cards: -->
  AMDグラフィックカード搭載のアーチ用：
  ```bash
  sudo pacman -S vulkan-radeon lib32-vulkan-radeon
  ```

  <!-- For Arch with Intel graphics card: -->
  Intelグラフィックスカード搭載のArch用：
  ```bash
  sudo pacman -S vulkan-intel
  ```

  <!-- For Arch with NVIDIA graphic cards: -->
  NVIDIAグラフィックカード搭載アーチ用：
  ```bash
  sudo pacman -S nvidia lib32-nvidia-utils
  ```

  <!-- For Gentoo run: -->
  Gentooの場合：
  ```bash
  sudo emerge --ask --verbose dev-util/vulkan-tools dev-util/vulkan-headers
  ```

<!-- OK, we should now be ready to install Rust! -->
これでRustをインストールする準備ができた！
