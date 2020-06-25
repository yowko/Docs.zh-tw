---
title: 移除 .NET Core 執行階段和 SDK
description: 本文說明如何判斷目前所安裝的 .NET Core 執行階段和 SDK 版本，然後如何在 Windows、Mac 及 Linux 上移除它們。
author: adegeo
ms.author: adegeo
ms.date: 04/28/2020
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 1e4a846cf5e3d0209f5ade873520ef64abc12e7c
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324646"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a>如何移除 .NET Core 執行階段和 SDK

隨時間下來，當您安裝 .NET Core 執行階段和 SDK 的更新版本時，您可能想要從電腦移除過期的 .NET Core 版本。 移除舊版執行階段可能會變更選為執行共用架構應用程式的執行階段，如 [.NET Core 版本選取](../versions/selection.md)一文所述。

## <a name="should-i-remove-a-version"></a>我是否應該移除某個版本？

[.NET Core 版本選取](../versions/selection.md)行為及不同更新之間的 .NET Core 執行階段相容性，可讓您安全地移除舊版。 .NET Core 執行階段更新在主要版本「範圍」內 (例如 1.x 和 2.x) 是相容的。 此外，較新版本的 .NET Core SDK 通常能夠繼續以相容的方式，來建置以舊版執行階段為目標的應用程式。

一般而言，您只需要最新的 SDK，以及您應用程式所需之執行階段的最新修補版本。 您可能想要保留舊版 SDK 或執行階段版本的實例，包括維護應用程式*project.js*。 除非您的應用程式有特定理由需要舊版 SDK 或執行階段，否則您可以安全地移除舊版。

## <a name="determine-what-is-installed"></a>判斷已安裝的項目

從 .NET Core 2.1 開始，.NET CLI 可讓您選擇使用電腦上安裝的 SDK 和執行階段版本清單。  使用 [`dotnet --list-sdks`](../tools/dotnet.md#options) 查看電腦上安裝的 sdk 清單。 使用 [`dotnet --list-runtimes`](../tools/dotnet.md#options) 查看電腦上安裝的執行時間清單。 如需詳細資訊，請參閱[如何檢查是否已安裝 .Net Core](how-to-detect-installed-versions.md)。

## <a name="uninstall-net-core"></a>卸載 .NET Core

::: zone pivot="os-windows"

.NET Core 使用 Windows**應用程式 & 功能**] 對話方塊來移除 .net Core 執行時間和 SDK 的版本。 下圖顯示 [**應用程式 & 功能**] 對話方塊。 您可以搜尋**core sdk**來篩選並顯示已安裝的 .net core 版本。

![用以移除 .NET Core 的 [新增/移除程式]](./media/remove-runtime-sdk-versions/programs-and-features.png)

選取您想要從電腦移除的任意版本，然後按一下 [解除安裝]****。

::: zone-end

::: zone pivot="os-linux"

在 Linux 上解除安裝 .NET Core (SDK 或執行階段) 有更多選項。 解除安裝 .NET Core 的最佳方式是對照您用來安裝 .NET Core 的動作。 細節會依您選擇的版本和安裝方法而異。

> [!IMPORTANT]
> 針對 Red Hat 安裝，請參閱 [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) (Red Hat 入門指南)，取得安裝和解除安裝 .NET Core 的資訊。

從 .NET Core 2.1 開始，使用套件管理員進行升級時，不需要卸載 .NET Core SDK。 套件管理員 `update` 或 `refresh` 命令會在成功安裝新版本之後，自動移除舊版本。

如果您使用套件管理員來安裝 .NET Core，您可以使用該相同的套件管理員來解除安裝 .NET SDK 或執行階段。 .NET Core 安裝支援最熱門的套件管理員。 如需您環境中的確切語法，請參閱散發套件管理員的檔：

- [apt-get(8)](https://linux.die.net/man/8/apt-get) 適用於 Debian 型系統，包括 Ubuntu。
- [yum(8)](https://linux.die.net/man/8/yum) 適用於 Fedora、CentOS 和 Oracle Linux。
- [zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) 適用於 openSUSE 和 SUSE Linux Enterprise System (SLES)。
- [dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) 適用於 Fedora。

在絕大多數的情況下，移除套件的命令是 `remove`。

對於大多數套件管理員，.NET Core SDK 安裝的套件名稱是 `dotnet-sdk`，後面接著版本號碼。 從 .NET Core SDK 2.1.300 版和執行階段 `2.1` 版開始，只需要主要和次要版本號碼：例如，.NET Core SDK 2.1.300 版可用套件 `dotnet-sdk-2.1` 參考。 舊版需要整個版本字串：例如，.NET Core SDK 2.1.200 版需要 `dotnet-sdk-2.1.200`。

針對只安裝執行階段但未安裝 SDK 的電腦，套件名稱是 `dotnet-runtime-<version>` (適用於 .NET Core 執行階段) 和 `aspnetcore-runtime-<version>` (適用於整個執行階段堆疊)。

早于2.0 的 .NET Core 安裝在使用套件管理員卸載 SDK 時，並未卸載主機應用程式。 請使用 `apt-get`，命令如下：

```bash
apt-get remove dotnet-host
```

請注意，沒有附加至的版本 `dotnet-host` 。

如果您使用 tarball 安裝，則必須使用手動方法移除 .NET Core。

在 Linux 上，您必須移除已建立版本的目錄，分別移除 Sdk 和執行時間。 移除它們會從磁片中刪除 SDK 和執行時間。 例如，若要移除 1.0.1 SDK 和執行階段，您可以使用下列 bash 命令：

```bash
version="1.0.1"
sudo rm -rf /usr/local/share/dotnet/sdk/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.All/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/$version
sudo rm -rf /usr/local/share/dotnet/host/fxr/$version
```

SDK 和執行階段的父目錄會列於 `dotnet --list-sdks` 和 `dotnet --list-runtimes` 命令輸出，如前述表格所示。

::: zone-end

::: zone pivot="os-macos"

在 Mac 上，您必須移除已建立版本的目錄，分別移除 Sdk 和執行時間。 移除它們會從磁片中刪除 SDK 和執行時間。 例如，若要移除 1.0.1 SDK 和執行階段，您可以使用下列 bash 命令：

```bash
version="1.0.1"
sudo rm -rf /usr/local/share/dotnet/sdk/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.All/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/$version
sudo rm -rf /usr/local/share/dotnet/host/fxr/$version
```

SDK 和執行階段的父目錄會列於 `dotnet --list-sdks` 和 `dotnet --list-runtimes` 命令輸出，如前述表格所示。

::: zone-end

## <a name="net-core-uninstall-tool"></a>.NET Core 解除安裝工具

[.Net Core 卸載工具](../additional-tools/uninstall-tool.md)（ `dotnet-core-uninstall` ）可讓您從系統中移除 .net Core sdk 和執行時間。 有一組選項可用來指定應該卸載的版本。

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a>Visual Studio .NET Core SDK 版本的相依性

在 Visual Studio 2019 16.3 版之前，Visual Studio 安裝程式，稱為獨立 .NET Core SDK 安裝程式。 因此，SDK 版本會顯示在 [Windows**應用程式 & 功能**] 對話方塊中。 移除 Visual Studio 使用獨立安裝程式所安裝的 .NET Core Sdk 可能會中斷 Visual Studio。 如果 Visual Studio 在卸載 Sdk 之後發生問題，請在該特定版本的 Visual Studio 上執行 [修復]。 下表顯示 .NET Core SDK 版本的部分 Visual Studio 相依性：

| Visual Studio 版本           | .NET Core SDK 版本          |
|---------------------------------|--------------------------------|
| Visual Studio 2019 16.2 版 | .NET Core SDK 2.2.4 xx，2.1.8 xx |
| Visual Studio 2019 16.1 版 | .NET Core SDK 2.2.3 xx，2.1.7 xx |
| Visual Studio 2019 16.0 版 | .NET Core SDK 2.2.2 xx，2.1.6 xx |
| Visual Studio 2017 15.9 版 | .NET Core SDK 2.2.1 xx，2.1.5 xx |
| Visual Studio 2017 15.8 版 | .NET Core SDK 2.1.4 xx          |

從 Visual Studio 2019 16.3 版開始，Visual Studio 會負責自己的 .NET Core SDK 複本。 基於這個理由，您不會再于 [**應用程式 & 功能**] 對話方塊中看到這些 SDK 版本。

## <a name="remove-the-nuget-fallback-folder"></a>移除 NuGet fallback 資料夾

在 .NET Core 3.0 SDK 之前，.NET Core SDK 安裝程式會使用名為*NuGetFallbackFolder*的資料夾來儲存 NuGet 套件的快取。 此快取是在作業期間使用，例如 `dotnet restore` 或 `dotnet build /t:Restore` 。 *NuGetFallbackFolder*位於 Windows 上的*C:\Program Files\dotnet\sdk*和 macOS 上的 */usr/local/share/dotnet/sdk* 。

如果有下列情況，您可能會想要移除此資料夾：

- 您只是使用 .NET Core 3.0 SDK 或更新版本進行開發。
- 您正在使用3.0 之前的 .NET Core SDK 版本進行開發，但您可以在線上工作。

如果您想要移除 NuGet fallback 資料夾，可以將它刪除，但是您需要系統管理員許可權才能執行此動作。

不建議刪除*dotnet*資料夾。 這麼做會移除您先前安裝的任何通用工具。 此外，在 Windows 上：

- 您將會中斷 Visual Studio 2019 16.3 版和更新版本。 您可以執行**Repair**來復原。
- 如果 [**應用程式 & 功能**] 對話方塊中有 .NET Core SDK 專案，則它們會是孤立的。
