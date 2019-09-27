---
title: .NET Core 通用工具
description: 說明何為 .NET Core 通用工具以及它們可用之 .NET Core CLI 命令的概觀。
author: KathleenDollard
ms.date: 05/29/2018
ms.custom: seodec18
ms.openlocfilehash: 40a0aabcf523e8dac9a3ad226064bbb3c1b3ce5b
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332013"
---
# <a name="net-core-global-tools-overview"></a>.NET Core 通用工具概觀

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

.NET Core 通用工具是包含主控台應用程式的特殊 NuGet 套件。 通用工具可以安裝在您電腦上的預設位置 (其包含在 PATH 環境變數中) 或自訂位置。

如果您想要使用 .NET Core 通用工具：

* 尋找工具的相關資訊 (通常是網站或 GitHub 網頁)。
* 檢查首頁中作者和統計資料的摘要 (通常是 NuGet.org)。
* 安裝工具。
* 呼叫工具。
* 更新工具。
* 解除安裝工具。

> [!IMPORTANT]
> .NET Core 通用工具會顯示在您的路徑中，並且在完全信任環境下執行。 除非您信任作者，否則請勿安裝 .NET Core 通用工具。

## <a name="find-a-net-core-global-tool"></a>尋找 .NET Core 通用工具

目前，.NET Core 命令列介面 (CLI) 中沒有通用工具搜尋功能。

您可以在 [NuGet](https://www.nuget.org) 上找到 .NET Core 通用工具。 不過，NuGet 尚未允許您專門搜尋 .NET Core 通用工具。

您也可以在部落格文章或 [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub 存放庫中找到工具建議。

還可以在 [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub 存放庫中看到 ASP.NET 小組所建立之通用工具的原始程式碼。

## <a name="check-the-author-and-statistics"></a>檢查作者和統計資料

由於 .NET Core 通用工具在完全信任環境下執行，而且通常是安裝在您的路徑上，它們可以發揮極為強大的功能。 請不要下載來自不信任人員的工具。

如果此工具裝載在 NuGet 上，您可以搜尋工具來檢查作者和統計資料。

## <a name="install-a-global-tool"></a>安裝通用工具

若要安裝通用工具，您可以使用 [dotnet tool install](dotnet-tool-install.md) .NET Core CLI 命令。 下列範例會示範如何在預設位置安裝通用工具：

```dotnetcli
dotnet tool install -g dotnetsay
```

如果無法安裝此工具，則會顯示錯誤訊息。 請確認正在檢查您所預期的摘要。

如果您要嘗試安裝發行前版本或特定版本的工具，可以使用下列格式指定版本號碼：

```dotnetcli
dotnet tool install -g <package-name> --version <version-number>
```

如果安裝成功，則會顯示一則訊息，其中顯示用來呼叫此工具的命令以及安裝的版本，類似於下例範例：

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

通用工具可以安裝在預設目錄或特定位置中。 預設目錄如下：

| OS          | `Path`                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

第一次執行 SDK　時，這些位置會新增至使用者的路徑，因此可以直接呼叫安裝在該處的通用工具。

請注意，通用工具是使用者特定工具，而不是電腦全域工具。 使用者特定表示您無法安裝可供電腦上所有使用者使用的通用工具。 此工具只適用於已安裝工具的每個使用者設定檔。

通用工具也可以安裝在特定目錄中。 安裝在特定目錄時，使用者必須確保命令可用，方法是在路徑中包含該目錄、使用指定的目錄呼叫命令，或從指定的目錄中呼叫工具。
在此情況下，.NET Core CLI 不會將這個位置自動新增至 PATH 環境變數。

## <a name="use-the-tool"></a>使用工具

安裝此工具之後，您可以使用其命令進行呼叫。 請注意，命令可能無法與套件名稱相同。

如果命令是 `dotnetsay`，呼叫時請使用：

```console
dotnetsay
```

如果工具作者想要工具顯示在 `dotnet` 提示的內容中，他們可能會以稱為 `dotnet <command>` 的方式進行撰寫，例如：

```dotnetcli
dotnet doc
```

您可以藉由使用 [dotnet tool list](dotnet-tool-list.md) 命令列出已安裝的套件，了解已安裝的通用工具套件中包含哪些工具。

您也可以在工具的網站中，或鍵入下列其中一個命令來尋找使用方式指示：

```console
<command> --help
dotnet <command> --help
```

## <a name="other-cli-commands"></a>其他 CLI 命令

.NET Core SDK 包含其他支援 .NET Core 通用工具的命令。 請使用任何 `dotnet tool` 命令搭配下列其中一個選項：

* `--global` 或 `-g` 指定命令適用於使用者範圍通用工具。
* `--tool-path` 指定通用工具的自訂位置。

若要查看哪些命令適用於通用工具：

```dotnetcli
dotnet tool --help
```

更新通用工具需要解除安裝再使用最新的穩定版本重新安裝。 若要更新通用工具，請使用 [dotnet tool update](dotnet-tool-update.md) 命令：

```dotnetcli
dotnet tool update -g <packagename>
```

使用 [dotnet tool uninstall](dotnet-tool-uninstall.md) 移除通用工具：

```dotnetcli
dotnet tool uninstall -g <packagename>
```

若要顯示電腦上目前已安裝的所有通用工具，以及它們的版本和命令，請使用 [dotnet tool list](dotnet-tool-list.md) 命令：

```dotnetcli
dotnet tool list -g
```

## <a name="see-also"></a>另請參閱

* [針對 .NET Core 工具使用問題進行疑難排解](troubleshoot-usage-issues.md)
