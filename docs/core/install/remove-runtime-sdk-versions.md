---
title: 移除 .NET 執行時間和 SDK
description: 本文說明如何判斷目前已安裝的 .NET 執行時間和 SDK 版本，以及如何在 Windows、Mac 和 Linux 上移除它們。
author: adegeo
ms.author: adegeo
ms.date: 11/20/2020
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: f07a9acdc5be310d38da18602dde2ebf678e9a1b
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031718"
---
# <a name="how-to-remove-the-net-runtime-and-sdk"></a>如何移除 .NET 執行時間和 SDK

經過一段時間後，當您安裝 .NET 執行時間和 SDK 的更新版本時，您可能會想要從您的電腦移除過時的 .NET 版本。 移除舊版執行時間可能會變更選擇執行共用 framework 應用程式的執行時間，如 [.net 版本選取](../versions/selection.md)專案中所述。

## <a name="should-i-remove-a-version"></a>我是否應該移除某個版本？

[.Net 版本的選取](../versions/selection.md)行為和 .net 之間的 .net 執行時間相容性，可讓您安全地移除先前的版本。 .NET 執行時間更新在主要版本 **波段** （例如1.x 和2.x）中相容。 此外，較新版本的 .NET SDK 通常會維持能夠以相容的方式來建立以舊版執行時間為目標的應用程式。

一般而言，您只需要最新的 SDK，以及您應用程式所需之執行階段的最新修補版本。 您可能想要保留舊版 SDK 或執行階段版本的實例，包括維護 *project.js的* 應用程式。 除非您的應用程式有特定理由需要舊版 SDK 或執行階段，否則您可以安全地移除舊版。

## <a name="determine-what-is-installed"></a>判斷已安裝的項目

.NET CLI 有一些選項，可讓您用來列出電腦上安裝的 SDK 和執行階段版本。  使用 [`dotnet --list-sdks`](../tools/dotnet.md#options) 以查看電腦上安裝的 sdk 清單。 使用 [`dotnet --list-runtimes`](../tools/dotnet.md#options) 以查看電腦上安裝的執行時間清單。 如需詳細資訊，請參閱 [如何檢查是否已安裝 .net](how-to-detect-installed-versions.md)。

## <a name="uninstall-net"></a>卸載 .NET

::: zone pivot="os-windows"

.NET 會使用 Windows **應用程式 & 功能** ] 對話方塊來移除 .net 執行時間和 SDK 的版本。 下圖顯示 [ **應用程式 & 功能** ] 對話方塊。 您可以搜尋 **核心 sdk** 或 **.net sdk** ，以篩選和顯示已安裝的 .net 版本。

![新增/移除程式以移除 .NET](./media/remove-runtime-sdk-versions/programs-and-features.png)

選取您想要從電腦移除的任意版本，然後按一下 [解除安裝]。

::: zone-end

::: zone pivot="os-linux"

有更多選項可將 .NET (SDK 或 Linux 上的執行時間) 卸載。 卸載 .NET 的最佳方式是鏡像您用來安裝 .NET 的動作。 細節會依您選擇的版本和安裝方法而異。

> [!IMPORTANT]
> 針對 Red Hat 安裝，請參閱 [.net 的 Red Hat 產品檔](https://access.redhat.com/documentation/en-us/net/5.0/)。

除非您要從預覽版本升級，否則不需要在使用套件管理員升級 .NET SDK 時卸載 .NET SDK。 套件管理員 `update` 或 `refresh` 命令會在成功安裝新版本之後，自動移除舊版本。 如果您已安裝預覽版本，請將它卸載。

如果您使用套件管理員安裝 .NET，請使用相同的套件管理員來卸載 .NET SDK 或執行時間。 .NET 安裝支援最熱門的封裝管理員。 請參閱散發套件管理員的檔，以瞭解您環境中的精確語法：

- [apt-get(8)](https://linux.die.net/man/8/apt-get) 適用於 Debian 型系統，包括 Ubuntu。
- [yum(8)](https://linux.die.net/man/8/yum) 適用於 Fedora、CentOS 和 Oracle Linux。
- [zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) 適用於 openSUSE 和 SUSE Linux Enterprise System (SLES)。
- [dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) 適用於 Fedora。

在絕大多數的情況下，移除套件的命令是 `remove`。

大部分套件管理員的 .NET SDK 安裝封裝名稱是 `dotnet-sdk` ，後面接著版本號碼。 從 .NET SDK 的版本2.1.300 和執行時間的版本開始 `2.1` ，只需要主要和次要版本號碼：例如，您可以將 .NET SDK 版本2.1.300 參考為套件 `dotnet-sdk-2.1` 。 先前的版本需要整個版本字串：例如， `dotnet-sdk-2.1.200` .NET SDK 的版本2.1.200 需要此版本。

對於僅安裝執行時間（而不是 SDK）的電腦，套件名稱適用 `dotnet-runtime-<version>` 于 .net 執行時間和 `aspnetcore-runtime-<version>` 整個執行時間堆疊。

> [!TIP]
> 使用套件管理員卸載 SDK 時，早于2.0 的 .NET Core 安裝不會卸載主機應用程式。 請使用 `apt-get`，命令如下：
>
> ```bash
> apt-get remove dotnet-host
> ```
>
> 沒有任何版本附加至 `dotnet-host` 。

如果您使用 tarball 安裝，則必須使用手動方法來移除 .NET。

在 Linux 上，您必須移除已建立版本的目錄，來個別移除 Sdk 和執行時間。 移除它們會從磁片刪除 SDK 和執行時間。 例如，若要移除 1.0.1 SDK 和執行階段，您可以使用下列 bash 命令：

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

在 Mac 上，您必須移除已建立版本的目錄，來個別移除 Sdk 和執行時間。 移除它們會從磁片刪除 SDK 和執行時間。 例如，若要移除 1.0.1 SDK 和執行階段，您可以使用下列 bash 命令：

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

## <a name="net-uninstall-tool"></a>.NET 卸載工具

[.Net 卸載工具](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) 可讓您從系統移除 .net sdk 和執行時間。 選項的集合可以用來指定應該卸載的版本。

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a>.NET Core SDK 版本的 Visual Studio 相依性

在 Visual Studio 2019 16.3 版之前，Visual Studio 安裝程式，稱為獨立 .NET Core SDK 安裝程式。 因此，SDK 版本會出現在 [Windows **應用程式 & 功能** ] 對話方塊中。 使用獨立安裝程式移除 Visual Studio 所安裝的 .NET Core Sdk 可能會中斷 Visual Studio。 如果 Visual Studio 在卸載 Sdk 之後遇到問題，請在該特定版本的 Visual Studio 上執行 Repair。 下表顯示 .NET Core SDK 版本的部分 Visual Studio 相依性：

| Visual Studio 版本           | .NET Core SDK 版本          |
|---------------------------------|--------------------------------|
| Visual Studio 2019 16.2 版 | .NET Core SDK 2.2.4 xx，2.1.8 xx |
| Visual Studio 2019 16.1 版 | .NET Core SDK 2.2.3 xx，2.1.7 xx |
| Visual Studio 2019 16.0 版 | .NET Core SDK 2.2.2 xx、2.1.6 xx |
| Visual Studio 2017 15.9 版 | .NET Core SDK 2.2.1 xx，2.1.5 xx |
| Visual Studio 2017 15.8 版 | .NET Core SDK 2.1.4 xx          |

從 Visual Studio 2019 16.3 版開始，Visual Studio 負責自己的 .NET SDK 複本。 基於這個理由，您不會再于 [ **應用程式 & 功能** ] 對話方塊中看到這些 SDK 版本。

## <a name="remove-the-nuget-fallback-folder"></a>移除 NuGet fallback 資料夾

在 .NET Core 3.0 SDK 之前，.NET Core SDK 安裝程式會使用名為 *NuGetFallbackFolder* 的資料夾來儲存 NuGet 套件的快取。 此快取是在作業期間使用，例如 `dotnet restore` 或 `dotnet build /t:Restore` 。 *NuGetFallbackFolder* 位於 Windows 上的 *C:\Program Files\dotnet\sdk* 和 macOS 上的 */usr/local/share/dotnet/sdk* 。

如果有下列情況，您可能會想要移除此資料夾：

- 您只是使用 .NET Core 3.0 SDK 或 .NET 5.0 或更新版本進行開發。
- 您是使用早于3.0 的 .NET Core SDK 版本進行開發，但您可以在線上工作。

如果您想要移除 NuGet 回溯資料夾，您可以將其刪除，但需要系統管理員許可權才能完成此動作。

不建議刪除 *dotnet* 資料夾。 這麼做會移除先前安裝的所有通用工具。 此外，在 Windows 上：

- 您將會中斷 Visual Studio 2019 16.3 版和更新版本。 您可以執行 **Repair** 來復原。
- 如果 [ **應用程式 & 功能** ] 對話方塊中有 .NET Core SDK 專案，它們會是孤立的。
