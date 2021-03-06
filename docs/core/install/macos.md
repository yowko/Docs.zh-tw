---
title: 在 macOS 上安裝 .NET
description: 瞭解您可以在哪些版本的 macOS 上安裝 .NET。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: b1434938a8e8e81da81e495a6b99e6c99467aae1
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009354"
---
# <a name="install-net-on-macos"></a>在 macOS 上安裝 .NET

> [!div class="op_single_selector"]
>
> - [在 Windows 上安裝](windows.md)
> - [在 macOS 上安裝](macos.md)
> - [安裝在 Linux 上](linux.md)

在本文中，您將瞭解如何在 macOS 上安裝 .NET。 .NET 是由執行時間和 SDK 所組成。 執行時間是用來執行 .NET 應用程式，且不一定會包含在應用程式中。 SDK 是用來建立 .NET 應用程式和程式庫。 .NET 執行時間一律會與 SDK 一起安裝。

.NET 的最新版本為5.0。

> [!div class="button"]
> [下載 .NET Core](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a>支援的版本

下表列出目前支援的 .NET 版本，以及其支援的 macOS 版本。 這些版本仍可支援 .Net 的版本，以 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。

- ✔️表示仍支援 .NET Core 的版本。
- ❌表示不支援 .Net Core 的版本。

| 作業系統          | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|---------------------------|---------------|---------------|----------------|
| macOS 11.0 "Big Sur"        | ✔️ 2.1 ([版本][release-notes-21] 資訊)  | ✔️ 3.1 ([版本][release-notes-31] 資訊)  | ✔️ 5.0 ([版本][release-notes-50] 資訊)  |
| macOS 10.15 "Catalina"    | ✔️ 2.1 ([版本][release-notes-21] 資訊)  | ✔️ 3.1 ([版本][release-notes-31] 資訊)  | ✔️ 5.0 ([版本][release-notes-50] 資訊)  |
| macOS 10.14 "Mojave"      | ✔️ 2.1 ([版本][release-notes-21] 資訊)  | ✔️ 3.1 ([版本][release-notes-31] 資訊)  | ✔️ 5.0 ([版本][release-notes-50] 資訊)  |
| macOS 10.13 "High Sierra" | ✔️ 2.1 ([版本][release-notes-21] 資訊)  | ✔️ 3.1 ([版本][release-notes-31] 資訊)  | ✔️ 5.0 ([版本][release-notes-50] 資訊)  |
| macOS 10.12 "Sierra"      | ✔️ 2.1 ([版本][release-notes-21] 資訊)  | ❌ 3.1 ([版本][release-notes-31] 資訊)  | ❌ 5.0 ([版本][release-notes-50] 資訊)  |

## <a name="unsupported-releases"></a>不支援的版本

不再支援下列 .NET 版本 ❌ 。 這些內容的下載仍會保持發佈：

- 3.0 ([版本][release-notes-30] 資訊) 
- 2.2 ([版本][release-notes-22] 資訊) 
- 2.0 ([版本][release-notes-20] 資訊) 

## <a name="runtime-information"></a>執行時間資訊

執行時間是用來執行以 .NET 建立的應用程式。 當應用程式作者發佈應用程式時，他們可以在其應用程式中包含執行時間。 如果未包含執行時間，則會由使用者自行安裝執行時間。

您可以在 macOS 上安裝三個不同的執行時間：

*ASP.NET Core 執行時間*\
執行 ASP.NET Core 應用程式。 包含 .NET 執行時間。

*.NET 執行時間*\
此執行時間是最簡單的執行時間，不包含任何其他執行時間。 強烈建議您安裝 *ASP.NET Core 運行* 時間，以獲得與 .net 應用程式的最佳相容性。

> [!div class="button"]
> [下載 .NET 執行時間](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a>SDK 資訊

SDK 可用來建立及發佈 .NET 應用程式和程式庫。 安裝 SDK 同時包含 [運行](#runtime-information)時間： ASP.NET CORE 和 .net。

## <a name="dependencies"></a>相依性

下列 macOS 版本支援 .NET：

> [!NOTE]
> `+`符號表示最小版本。

| .NET Core 版本 | macOS                 | 架構 | 詳細資訊    |
| ----------------- | --------------------- | --------------| --- |
| 5.0               | 高塞拉里昂 (10.13 +)   | x64 | [詳細資訊](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md) |
| 3.1               | 高塞拉里昂 (10.13 +)   | x64 | [詳細資訊](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| 3.0               | 高塞拉里昂 (10.13 +)   | x64 | [詳細資訊](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| 2.2               | 10.12 +) 的塞拉里昂 (       | x64 | [詳細資訊](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| 2.1               | 10.12 +) 的塞拉里昂 (       | x64 | [詳細資訊](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

從 macOS Catalina () 10.15 版開始，在2019年6月1日之後，以開發人員識別碼散發的所有軟體都必須公證。 這項需求適用于 .NET 執行時間、.NET SDK 和使用 .NET 建立的軟體。

.NET 5.0 和 .NET Core 3.1、3.0 和2.1 的執行時間和 SDK 安裝程式，自2020年2月18日起已公證。 先前發行的版本不會公證。 如果您執行非公證應用程式，您會看到類似下圖的錯誤：

![macOS Catalina 公證警示](media/dependencies/macos-notarized-pkg-warning.png)

如需強制執行公證如何影響 .NET (和您的 .NET 應用程式) 的詳細資訊，請參閱 [使用 MacOS Catalina 公證](macos-notarization-issues.md)。

## <a name="libgdiplus"></a>libgdiplus

使用 *system.object* 的 .net 應用程式需要安裝 libgdiplus。

取得 libgdiplus 的簡單方法是使用 macOS 的 [Homebrew ( "brew" ) ](https://brew.sh/) 套件管理員。 安裝 *brew* 之後，請在終端機 (命令) 提示字元中執行下列命令，以安裝 libgdiplus：

```console
brew update
brew install mono-libgdiplus
```

## <a name="install-with-an-installer"></a>使用安裝程式安裝

macOS 具有可用於安裝 .NET 5.0 SDK 的獨立安裝程式：

- [x64 (64 位) Cpu](https://dotnet.microsoft.com/download/dotnet-core/5.0)

## <a name="download-and-manually-install"></a>下載並手動安裝

<!-- Note, this content is taken from includes/linux-install-manual.md but changed for macOS. Any fixes should be applied there too, though content may be different -->

除了 .NET 的 macOS 安裝程式之外，您還可以下載並手動安裝 SDK 和執行時間。 手動安裝通常會做為持續整合測試的一部分來執行。 針對開發人員或使用者，通常最好是使用 [安裝程式](https://dotnet.microsoft.com/download/dotnet-core)。

如果您安裝的是 .NET SDK，就不需要安裝對應的執行時間。 首先，從下列其中一個網站下載 SDK 或執行時間的 **二進位** 版本：

- ✔️ [.net 5.0 下載](https://dotnet.microsoft.com/download/dotnet/5.0)
- ✔️ [.Net Core 3.1 下載](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- ✔️ [.Net Core 2.1 下載](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [所有 .NET Core 下載](https://dotnet.microsoft.com/download/dotnet-core)

接下來，將下載的檔案解壓縮，並使用 `export` 命令設定 .net 所使用的變數，然後確定 .net 是在 PATH 中。

若要將執行時間解壓縮，並讓 .NET CLI 命令可在終端機上使用，請先下載 .NET 二進位版本。 然後，開啟終端機，並從儲存檔案的目錄執行下列命令。 保存檔案名稱可能會因您所下載的內容而有所不同。

**使用下列命令，將執行時間解壓縮**：

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-5.0.0-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

**使用下列命令將 SDK 解壓縮**：

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-5.0.100-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> 上述 `export` 命令只會讓執行的終端機會話提供 .NET CLI 命令。
>
> 您可以編輯 shell 設定檔，以永久新增命令。 Linux 有一些不同的 shell 可用，而且每個都有不同的設定檔。 例如：
>
> - **Bash Shell**： *~/.bash_profile*， *~/.bashrc*
> - **Korn Shell**： *~/.kshrc* 或 *. profile*
> - **Z Shell**： *~/.zshrc* 或 *. zprofile*
>
> 編輯您 shell 的適當原始程式檔，並新增 `:$HOME/dotnet` 至現有語句的結尾 `PATH` 。 如果未 `PATH` 包含任何語句，請使用加入新的一行 `export PATH=$PATH:$HOME/dotnet` 。
>
> 此外，新增 `export DOTNET_ROOT=$HOME/dotnet` 至檔案結尾。

這種方法可讓您將不同的版本安裝到不同的位置，並明確地選擇哪個應用程式要使用哪一個版本。

## <a name="install-with-visual-studio-for-mac"></a>使用 Visual Studio for Mac 安裝

Visual Studio for Mac 在選取 **.net** 工作負載時安裝 .net SDK。 若要開始在 macOS 上進行 .NET 程式開發，請參閱 [安裝適用于 Mac 的 Visual Studio 2019](/visualstudio/mac/installation)。

| .NET SDK 版本      | Visual Studio 版本                      |
| --------------------- | ------------------------------------------ |
| 5.0                   | 適用于 Mac 8.8 版或更高版本的 Visual Studio 2019。 |
| 3.1                   | 適用于 Mac 8.4 版或更高版本的 Visual Studio 2019。 |
| 2.1                   | 適用于 Mac 8.0 版或更高版本的 Visual Studio 2019。 |

[![macOS Visual Studio 2019 for Mac with .NET 工作負載功能](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)

## <a name="install-alongside-visual-studio-code"></a>隨 Visual Studio Code 一起安裝

Visual Studio Code 是一種功能強大且輕量的原始程式碼編輯器，可在您的桌面上執行。 Visual Studio Code 適用于 Windows、macOS 和 Linux。

雖然 Visual Studio Code 不會隨附像 Visual Studio 這樣的自動化 .NET 安裝程式，但新增 .NET 支援很簡單。

01. [下載並安裝 Visual Studio Code](https://code.visualstudio.com/Download)。
01. [下載並安裝 .NET SDK](https://dotnet.microsoft.com/download/dotnet-core)。
01. [從 Visual Studio Code Marketplace 安裝 c # 擴充](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)功能。

## <a name="install-with-bash-automation"></a>使用 bash automation 安裝

[Dotnet 安裝腳本](../tools/dotnet-install-script.md)是用於執行時間的自動化和非系統管理員安裝。 您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載腳本。

腳本預設會安裝最新 [長期支援 (LTS) ](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 版本，也就是 .net Core 3.1。 您可以藉由指定參數來選擇特定版本 `current` 。 包含 `runtime` 參數以安裝執行時間。 否則，腳本會安裝 [SDK](./windows.md)。

```bash
./dotnet-install.sh --channel 5.0 --runtime aspnetcore
```

> [!NOTE]
> 上一個命令會安裝 ASP.NET Core 執行時間，以取得最大相容性。 ASP.NET Core 執行時間也包含標準的 .NET 執行時間。

## <a name="docker"></a>Docker

容器可提供輕量的方式，將您的應用程式與主機系統的其餘部分隔離。 相同電腦上的容器只會共用核心，並使用提供給您應用程式的資源。

.NET 可以在 Docker 容器中執行。 官方 .NET Docker 映射會發佈至 Microsoft Container Registry (MCR) 並可在 [microsoft .Net Core Docker Hub 存放庫](https://hub.docker.com/_/microsoft-dotnet/)中找到。 每個存放庫都包含您可以使用的 .NET (SDK 或執行階段) 與作業系統不同組合的映像。

Microsoft 會提供針對特定案例量身訂做的映像。 例如，[ASP.NET Core 存放庫](https://hub.docker.com/_/microsoft-dotnet-aspnet) \(英文\) 可提供為了在生產環境中執行 ASP.NET Core 應用程式而建置的映像。

如需在 Docker 容器中使用 .NET Core 的詳細資訊，請參閱 [.net 和 Docker 簡介](../docker/introduction.md) 和 [範例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)。

## <a name="next-steps"></a>後續步驟

- [如何檢查是否已安裝 .Net Core](how-to-detect-installed-versions.md?pivots=os-macos)。
- 使用[MacOS Catalina 公證](macos-notarization-issues.md)。
- [教學課程：開始使用 macOS](../tutorials/with-visual-studio-mac.md)。
- [教學課程：使用 Visual Studio Code 建立新的應用程式](../tutorials/with-visual-studio-code.md)。
- [教學課程：將 .Net Core 應用程式](../docker/build-container.md)。

[release-notes-21]: https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md
[release-notes-31]: https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md
[release-notes-50]: https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md
[release-notes-20]: https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md
[release-notes-22]: https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md
[release-notes-30]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md
