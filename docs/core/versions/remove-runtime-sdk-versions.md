---
title: 移除 .NET Core 執行階段和 SDK
description: 本文說明如何判斷目前所安裝的 .NET Core 執行階段和 SDK 版本，然後如何在 Windows、Mac 及 Linux 上移除它們。
ms.date: 12/17/2019
author: billwagner
ms.author: wiwagn
ms.custom: updateeachrelease
ms.openlocfilehash: 71c11825981c6259a779e1ac8f947a41618e922d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398836"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a>如何移除 .NET Core 執行階段和 SDK

隨時間下來，當您安裝 .NET Core 執行階段和 SDK 的更新版本時，您可能想要從電腦移除過期的 .NET Core 版本。 移除舊版執行階段可能會變更選為執行共用架構應用程式的執行階段，如 [.NET Core 版本選取](selection.md)一文所述。

## <a name="should-i-remove-a-version"></a>我是否應該移除某個版本？

[.NET Core 版本選取](selection.md)行為及不同更新之間的 .NET Core 執行階段相容性，可讓您安全地移除舊版。 .NET Core 執行階段更新在主要版本「範圍」內 (例如 1.x 和 2.x) 是相容的。 此外，較新版本的 .NET Core SDK 通常能夠繼續以相容的方式，來建置以舊版執行階段為目標的應用程式。

一般而言，您只需要最新的 SDK，以及您應用程式所需之執行階段的最新修補版本。 保留較舊的 SDK 或執行階段版本的實例包括維護基於**project.json**的應用程式。 除非您的應用程式有特定理由需要舊版 SDK 或執行階段，否則您可以安全地移除舊版。

## <a name="determine-what-is-installed"></a>判斷已安裝的項目

從 .NET Core 2.1 開始，.NET CLI 可讓您選擇使用電腦上安裝的 SDK 和執行階段版本清單。  用於[`dotnet --list-sdks`](../tools/dotnet.md#options)查看電腦上安裝的 SDK 清單。 用於[`dotnet --list-runtimes`](../tools/dotnet.md#options)查看電腦上安裝的運行時清單。 下列文字顯示 Windows、macOS 或 Linux 的一般輸出：

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

通過運行以下命令：

```dotnetcli
dotnet --list-sdks
```

您將獲得類似于以下內容的輸出：

```console
2.1.200-preview-007474 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007480 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007509 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007570 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007576 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007587 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007589 [C:\Program Files\dotnet\sdk]
2.1.200 [C:\Program Files\dotnet\sdk]
2.1.201 [C:\Program Files\dotnet\sdk]
2.1.202 [C:\Program Files\dotnet\sdk]
2.1.300-preview2-008533 [C:\Program Files\dotnet\sdk]
2.1.300 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009063 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009088 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009171 [C:\Program Files\dotnet\sdk]
```

通過運行以下命令：

```dotnetcli
dotnet --list-runtimes
```

您將獲得類似于以下內容的輸出：

```console
Microsoft.AspNetCore.All 2.1.0-preview2-final [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.0.6 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.7 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.9 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
```

# <a name="linux"></a>[Linux](#tab/linux)

通過運行以下命令：

```dotnetcli
dotnet --list-sdks
```

您將獲得類似于以下內容的輸出：

```console
1.0.1 [/usr/share/dotnet/sdk]
1.0.4 [/usr/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/share/dotnet/sdk]
2.0.0 [/usr/share/dotnet/sdk]
2.1.4 [/usr/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/share/dotnet/sdk]
2.1.300 [/usr/share/dotnet/sdk]
2.1.301 [/usr/share/dotnet/sdk]
```

通過運行以下命令：

```dotnetcli
dotnet --list-runtimes
```

您將獲得類似于以下內容的輸出：

```console
Microsoft.AspNetCore.All 2.1.0-preview2-final [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 1.0.4 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.0.5 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.1 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.2 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview1-002111-00 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview2-25407-01 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.5 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
```

# <a name="macos"></a>[macOS](#tab/macos)

通過運行以下命令：

```dotnetcli
dotnet --list-sdks
```

您將獲得類似于以下內容的輸出：

```console
1.0.1 [/usr/local/share/dotnet/sdk]
1.0.4 [/usr/local/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/local/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/local/share/dotnet/sdk]
2.0.0 [/usr/local/share/dotnet/sdk]
2.1.4 [/usr/local/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/local/share/dotnet/sdk]
2.1.300 [/usr/local/share/dotnet/sdk]
2.1.301 [/usr/local/share/dotnet/sdk]
```

通過運行以下命令：

```dotnetcli
dotnet --list-runtimes
```

您將獲得類似于以下內容的輸出：

```console
Microsoft.AspNetCore.All 2.1.0-preview2-final [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 1.0.4 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.0.5 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.1 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.2 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview1-002111-00 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview2-25407-01 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.5 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
```

---

## <a name="uninstall-net-core"></a>卸載 .NET 核心

# <a name="windows"></a>[Windows](#tab/windows)

.NET Core 使用 Windows [新增/移除程式]**** 對話方塊來移除 .NET Core 執行階段和 SDK 版本。 下圖顯示 [新增/移除程式]**** 對話方塊，其中已安裝數個 .NET 執行階段和 SDK 版本。

![用以移除 .NET Core 的 [新增/移除程式]](./media/remove-runtime-sdk-versions/programs-and-features.png)

選取您想要從電腦移除的任意版本，然後按一下 [解除安裝]****。

# <a name="linux"></a>[Linux](#tab/linux)

在 Linux 上解除安裝 .NET Core (SDK 或執行階段) 有更多選項。 解除安裝 .NET Core 的最佳方式是對照您用來安裝 .NET Core 的動作。 細節會依您選擇的版本和安裝方法而異。

> [!IMPORTANT]
> 針對 Red Hat 安裝，請參閱 [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) (Red Hat 入門指南)，取得安裝和解除安裝 .NET Core 的資訊。

從 .NET Core 2.1 開始，使用包管理器升級 .NET Core SDK 時無需卸載它。 套件管理員 `update` 或 `refresh` 命令會在成功安裝新版本之後，自動移除舊版本。

如果您使用套件管理員來安裝 .NET Core，您可以使用該相同的套件管理員來解除安裝 .NET SDK 或執行階段。 .NET Core 安裝支援最熱門的套件管理員。 請參閱版本的套件管理員文件，了解環境的精確語法：

- [apt-get(8)](https://linux.die.net/man/8/apt-get) 適用於 Debian 型系統，包括 Ubuntu。
- [yum(8)](https://linux.die.net/man/8/yum) 適用於 Fedora、CentOS 和 Oracle Linux。
- [zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) 適用於 openSUSE 和 SUSE Linux Enterprise System (SLES)。
- [dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) 適用於 Fedora。

在絕大多數的情況下，移除套件的命令是 `remove`。

對於大多數套件管理員，.NET Core SDK 安裝的套件名稱是 `dotnet-sdk`，後面接著版本號碼。 從 .NET Core SDK 2.1.300 版和執行階段 `2.1` 版開始，只需要主要和次要版本號碼：例如，.NET Core SDK 2.1.300 版可用套件 `dotnet-sdk-2.1` 參考。 舊版需要整個版本字串：例如，.NET Core SDK 2.1.200 版需要 `dotnet-sdk-2.1.200`。

針對只安裝執行階段但未安裝 SDK 的電腦，套件名稱是 `dotnet-runtime-<version>` (適用於 .NET Core 執行階段) 和 `aspnetcore-runtime-<version>` (適用於整個執行階段堆疊)。

.NET Core 安裝早于 2.0 時，使用包管理器卸載 SDK 時未卸載主機應用程式。 請使用 `apt-get`，命令如下：

```bash
apt-get remove dotnet-host
```

請注意，沒有附加到`dotnet-host`的版本。

如果您使用 tarball 安裝，則必須使用手動方法移除 .NET Core。

您可以透過移除含有該版本的目錄，來個別移除 SDK 和執行階段。 例如，若要移除 1.0.1 SDK 和執行階段，您可以使用下列 bash 命令：

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

SDK 和執行階段的父目錄會列於 `dotnet --list-sdks` 和 `dotnet --list-runtimes` 命令輸出，如前述表格所示。

# <a name="macos"></a>[macOS](#tab/macos)

在 Mac 上，您必須透過移除含有該版本的目錄，來個別移除 SDK 和執行階段。 例如，若要移除 1.0.1 SDK 和執行階段，您可以使用下列 bash 命令：

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

SDK 和執行階段的父目錄會列於 `dotnet --list-sdks` 和 `dotnet --list-runtimes` 命令輸出，如前述表格所示。

---

## <a name="net-core-uninstall-tool"></a>.NET Core 解除安裝工具

[.NET 核心卸載工具](../additional-tools/uninstall-tool.md)（`dotnet-core-uninstall`） 允許您從系統中刪除 .NET 核心 SDK 和運行時。 選項組合可用於指定應卸載哪些版本。

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a>對 .NET 核心 SDK 版本的視覺化工作室依賴

在 Visual Studio 2019 版本 16.3 之前，Visual Studio 安裝程式稱為獨立的 .NET 酷睿 SDK 安裝程式。 因此，SDK 版本將顯示在 Windows**添加/刪除程式**對話方塊中。 刪除 Visual Studio 使用獨立安裝程式安裝的 .NET 核心 SDK 可能會中斷 Visual Studio。 如果卸載 SDK 後 Visual Studio 出現問題，請對該特定版本的 Visual Studio 運行修復。 下表顯示了 .NET Core SDK 版本的一些 Visual Studio 依賴項：

| Visual Studio 版本 | .NET 核心 SDK 版本 |
| -- | -- |
| Visual Studio 2019 16.2 版 | .NET 核心 SDK 2.2.4xx， 2.1.8xx |
| Visual Studio 2019 16.1 版 | .NET 核心 SDK 2.2.3xx， 2.1.7xx |
| 視覺工作室 2019 版本 16.0 | .NET 核心 SDK 2.2.2xx， 2.1.6xx |
| 視覺工作室 2017 版本 15.9 | .NET 核心 SDK 2.2.1xx， 2.1.5xx |
| Visual Studio 2017 15.8 版 | .NET 核心 SDK 2.1.4xx |

從 Visual Studio 2019 版本 16.3 開始，Visual Studio 負責自己的 .NET 核心 SDK 副本。 因此，您不再在 **"添加/刪除程式"** 對話方塊中看到這些 SDK 版本。

## <a name="remove-the-nuget-fallback-folder"></a>刪除 NuGet 回退資料夾

在 .NET Core 3.0 SDK 之前，.NET Core SDK 安裝程式使用*NuGetFallbackFolder*存儲 NuGet 包的緩存。 此緩存在操作（如`dotnet restore`或`dotnet build /t:Restore`） 時使用。 位於`NuGetFallbackFolder`Windows 上的*C：*程式檔\dotnet_sdk，* 位於 macOS 上的 */usr/local/share/點網/sdk。*

您可能希望刪除此資料夾，如果：

* 您只使用 .NET Core 3.0 SDK 或更高版本進行開發。
* 您正在使用早于 3.0 的 .NET Core SDK 版本進行開發，但您可以連線工作，並且速度可能會變慢一次。

如果要刪除 NuGet 回退資料夾，可以將其刪除，但需要管理員許可權才能刪除。

不建議刪除*dotnet*資料夾。 這樣做將刪除以前安裝的任何全域工具。 此外，在 Windows 上：

- 您將打破 Visual Studio 2019 版本 16.3 和更高版本。 您可以運行 **"修復"** 以恢復。
- 如果在 **"添加/刪除程式"** 對話方塊中有 .NET 核心 SDK 條目，則這些條目將孤立化。
