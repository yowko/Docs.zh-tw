---
title: 在 macOS 上安裝 .NET Core
description: 瞭解您可以在哪些版本的 macOS 上安裝 .NET Core。
author: adegeo
ms.author: adegeo
ms.date: 06/25/2020
ms.openlocfilehash: bb1a0fa24e2f6e8850cbe59378793ff846f04ba9
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85804481"
---
# <a name="install-net-core-on-macos"></a>在 macOS 上安裝 .NET Core

> [!div class="op_single_selector"]
>
> - [在 Windows 上安裝](windows.md)
> - [在 macOS 上安裝](macos.md)
> - [在 Linux 上安裝](linux.md)

在本文中，您將瞭解如何在 macOS 上安裝 .NET Core。 .NET Core 是由執行時間和 SDK 所組成。 執行時間是用來執行 .NET Core 應用程式，且不一定會包含在應用程式中。 SDK 可用來建立 .NET Core 應用程式和程式庫。 .NET Core 執行時間一律會與 SDK 一起安裝。

.NET Core 的最新版本為3.1。

[下載 .NET Core。](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a>支援的版本

下表列出目前支援的 .NET Core 版本，以及支援的 macOS 版本。 這些版本仍可支援[.Net Core 版本達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。

- ✔️表示仍然支援 .NET Core 的版本。
- ❌表示不支援 .Net Core 的版本。

| 作業系統          | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview |
|---------------------------|---------------|---------------|----------------|
| macOS 10.15 "Catalina"    | ✔️2.1 （[版本][release-notes-21]資訊） | ✔️3.1 （[版本][release-notes-31]資訊） | ✔️ 5.0 Preview （[版本][release-notes-50]資訊） |
| macOS 10.14 "Mojave"      | ✔️2.1 （[版本][release-notes-21]資訊） | ✔️3.1 （[版本][release-notes-31]資訊） | ✔️ 5.0 Preview （[版本][release-notes-50]資訊） |
| macOS 10.13 「高塞拉里昂」 | ✔️2.1 （[版本][release-notes-21]資訊） | ✔️3.1 （[版本][release-notes-31]資訊） | ✔️ 5.0 Preview （[版本][release-notes-50]資訊） |
| macOS 10.12 "Sierra"      | ✔️2.1 （[版本][release-notes-21]資訊） | ❌3.1 （[版本][release-notes-31]資訊） | ❌5.0 Preview （[版本][release-notes-50]資訊） |

## <a name="unsupported-releases"></a>不支援的版本

已不再支援下列 .NET Core 版本 ❌ 。 這些下載仍會保持發佈：

- 3.0 （[版本][release-notes-30]資訊）
- 2.2 （[版本][release-notes-22]資訊）
- 2.0 （[版本][release-notes-20]資訊）

## <a name="runtime-information"></a>執行時間資訊

執行時間是用來執行使用 .NET Core 所建立的應用程式。 當應用程式作者發行應用程式時，他們可以將執行時間包含在其應用程式中。 如果它們不包含執行時間，則會由使用者自行安裝執行時間。

您可以在 macOS 上安裝三種不同的執行時間：

*ASP.NET Core 執行時間*\
執行 ASP.NET Core 應用程式。 包含 .NET Core 執行時間。

*.NET Core 執行時間*\
此執行時間是最簡單的執行時間，不包含任何其他執行時間。 強烈建議您安裝*ASP.NET Core 運行*時間，以與 .net Core 應用程式達到最佳的相容性。

[下載 .NET Core 執行時間。](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a>SDK 資訊

SDK 可用來建立及發佈 .NET Core 應用程式和程式庫。 安裝 SDK 同時包含[運行](#runtime-information)時間： ASP.NET CORE 和 .net Core。

[下載 .NET Core SDK。](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="dependencies"></a>相依性

下列 macOS 版本支援 .NET Core：

> [!NOTE]
> `+`代表最小版本的符號。

| .NET Core 版本 | macOS                 | 架構 |     |
| ----------------- | --------------------- | --------------| --- |
| 3.1               | 高塞拉里昂（10.13 +）  | x64 | [詳細資訊](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| 3.0               | 高塞拉里昂（10.13 +）  | x64 | [詳細資訊](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| 2.2               | 塞拉里昂（10.12 +）       | x64 | [詳細資訊](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| 2.1               | 塞拉里昂（10.12 +）       | x64 | [詳細資訊](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

從 macOS Catalina （版本10.15）開始，在2019年6月1日之後以開發人員識別碼散發的所有軟體都必須是公證。 這項需求適用于 .NET core 執行時間、.NET Core SDK 和使用 .NET Core 所建立的軟體。

從2020年2月18日起，已公證 .NET Core （執行時間和 SDK）版本3.1、3.0 和2.1 的安裝程式。 先前發行的版本不會公證。 如果您執行非公證應用程式，您會看到類似下圖的錯誤：

![macOS Catalina notarization 警示](media/dependencies/macos-notarized-pkg-warning.png)

如需強制執行 notarization 如何影響 .NET Core （和您的 .NET Core 應用程式）的詳細資訊，請參閱[使用 MacOS Catalina notarization](macos-notarization-issues.md)。

## <a name="libgdiplus"></a>libgdiplus

使用*system.web*元件的 .net Core 應用程式需要安裝 libgdiplus。

取得 libgdiplus 的簡單方式是使用 macOS 的[Homebrew （"brew"）](https://brew.sh/)套件管理員。 安裝*brew*之後，請在終端機（命令）提示字元中執行下列命令，以安裝 libgdiplus：

```console
brew update
brew install mono-libgdiplus
```

## <a name="install-with-an-installer"></a>使用安裝程式安裝

macOS 具有可用於安裝 .NET Core 3.1 SDK 的獨立安裝程式：

- [x64 （64位） Cpu](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a>下載並手動安裝

<!-- Note, this content is taken from includes/linux-install-manual.md but changed for macOS. Any fixes should be applied there too, though content may be different -->

除了適用于 .NET Core 的 macOS 安裝程式之外，您還可以下載並手動安裝 SDK 和執行時間。 手動安裝通常是做為持續整合測試的一部分來執行。 對於開發人員或使用者，通常最好是使用[安裝程式](https://dotnet.microsoft.com/download/dotnet-core)。

如果您安裝 .NET Core SDK，就不需要安裝對應的執行時間。 首先，從下列其中一個網站下載 SDK 或執行時間的**二進位**版本：

- ✔️ [.net 5.0 preview 下載](https://dotnet.microsoft.com/download/dotnet/5.0)
- ✔️ [.Net Core 3.1 下載](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- ✔️ [.Net Core 2.1 下載](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [所有 .NET Core 下載](https://dotnet.microsoft.com/download/dotnet-core)

接下來，將下載的檔案解壓縮，並使用 `export` 命令來設定 .Net core 所使用的變數，然後確保 .Net core 在 PATH 中。

若要將執行時間解壓縮，並在終端機上提供 .NET Core CLI 命令，請先下載 .NET Core 二進位版本。 然後，開啟終端機，並從儲存檔案的目錄執行下列命令。 封存檔案名稱可能會根據您下載的內容而有所不同。

**使用下列命令來解壓縮運行**時間：

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-3.1.5-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

**使用下列命令來解壓縮 SDK**：

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-3.1.301-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> 上述 `export` 命令只會對其執行所在的終端機會話提供 .NET Core CLI 命令。
>
> 您可以編輯您的 shell 設定檔，以永久新增命令。 有許多不同的 shell 可供 Linux 使用，而且每個都有不同的設定檔。 例如：
>
> - **Bash Shell**： *~/. bash_profile*， *~/.bashrc*
> - **Korn Shell**： *~/.kshrc*或 *. profile*
> - **Z Shell**： *~/.zshrc*或 *. zprofile*
>
> 為您的 shell 編輯適當的原始程式檔，並將新增 `:$HOME/dotnet` 至現有 `PATH` 語句的結尾。 如果未 `PATH` 包含任何語句，請加入具有的新行 `export PATH=$PATH:$HOME/dotnet` 。
>
> 此外，將新增 `export DOTNET_ROOT=$HOME/dotnet` 至檔案結尾。

這種方法可讓您將不同的版本安裝到不同的位置，並明確選擇哪一個應用程式要使用哪一個。

## <a name="install-with-visual-studio-for-mac"></a>使用 Visual Studio for Mac 安裝

Visual Studio for Mac 在選取 [ **.Net Core** ] 工作負載時安裝 .NET Core SDK。 若要開始在 macOS 上使用 .NET Core 開發，請參閱[安裝適用于 Mac 的 Visual Studio 2019](/visualstudio/mac/installation)。 針對最新版本 .NET Core 3.1，您必須使用 Visual Studio for Mac 8.4 Preview。

[![使用 .NET Core 工作負載功能的 macOS Visual Studio 2019 for Mac](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)

## <a name="install-alongside-visual-studio-code"></a>與 Visual Studio Code 一起安裝

Visual Studio Code 是一種功能強大且輕量的原始程式碼編輯器，可在您的桌面上執行。 Visual Studio Code 適用于 Windows、macOS 和 Linux。

雖然 Visual Studio Code 不會隨附像 Visual Studio 這樣的自動化 .NET Core 安裝程式，但新增 .NET Core 支援十分簡單。

01. [下載並安裝 Visual Studio Code](https://code.visualstudio.com/Download)。
01. [下載並安裝 .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core)。
01. [從 Visual Studio Code Marketplace 安裝 c # 擴充](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)功能。

## <a name="install-with-bash-automation"></a>使用 bash automation 進行安裝

[Dotnet-install 腳本](../tools/dotnet-install-script.md)是用於執行時間的自動化和非系統管理員安裝。 您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載此腳本。

腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 3.1。 您可以藉由指定參數來選擇特定版本 `current` 。 包含用 `runtime` 來安裝執行時間的參數。 否則，腳本會安裝[SDK](sdk.md)。

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> 上述命令會安裝 ASP.NET Core 執行時間，以達到最大相容性。 ASP.NET Core 執行時間也包含標準的 .NET Core 執行時間。

## <a name="docker"></a>Docker

容器提供輕量的方式，將您的應用程式與主機系統的其餘部分隔離。 相同電腦上的容器只會共用核心，並使用提供給您應用程式的資源。

.NET Core 可以在 Docker 容器中執行。 官方 .NET Core Docker 映像會發佈至 Microsoft 容器登錄 (MCR)，並且可在 [Microsoft.NET Core Docker Hub 存放庫](https://hub.docker.com/_/microsoft-dotnet-core/) \(英文\) 中找到。 每個存放庫都包含您可以使用的 .NET (SDK 或執行階段) 與作業系統不同組合的映像。

Microsoft 會提供針對特定案例量身訂做的映像。 例如，[ASP.NET Core 存放庫](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) \(英文\) 可提供為了在生產環境中執行 ASP.NET Core 應用程式而建置的映像。

如需在 Docker 容器中使用 .NET Core 的詳細資訊，請參閱[.net 和 Docker 簡介](../docker/introduction.md)和[範例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)。

## <a name="next-steps"></a>後續步驟

- [如何檢查是否已安裝 .Net Core](how-to-detect-installed-versions.md?pivots=os-macos)。
- 使用[MacOS Catalina notarization](macos-notarization-issues.md)。
- [教學課程：開始使用 macOS](../tutorials/using-on-mac-vs.md)。
- [教學課程：使用 Visual Studio Code 建立新的應用程式](../tutorials/with-visual-studio-code.md)。
- [教學課程：容器化 .Net Core 應用程式](../docker/build-container.md)。

[release-notes-21]: https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md
[release-notes-31]: https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md
[release-notes-50]: https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md
[release-notes-20]: https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md
[release-notes-22]: https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md
[release-notes-30]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md
