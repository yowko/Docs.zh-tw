---
title: 排除 .NET 核心工具使用問題
description: 在運行 .NET 核心工具和可能的解決方案時發現常見問題。
author: kdollard
ms.date: 02/14/2020
ms.openlocfilehash: ed6243f802c4d3ce56a742916a1a28676e3cd876
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146446"
---
# <a name="troubleshoot-net-core-tool-usage-issues"></a>排除 .NET 核心工具使用問題

在嘗試安裝或運行 .NET Core 工具時可能會遇到問題，該工具可以是全域工具或本地工具。 本文介紹了常見根本原因和一些可能的解決方案。

## <a name="installed-net-core-tool-fails-to-run"></a>已安裝 .NET 核心工具無法運行

當 .NET Core 工具無法運行時，您最有可能遇到以下問題之一：

* 找不到該工具的可執行檔。
* 找不到 .NET 核心運行時的正確版本。

### <a name="executable-file-not-found"></a>找不到可執行檔

如果未找到可執行檔，您將看到類似于以下內容的消息：

```console
Could not execute because the specified command or file was not found.
Possible reasons for this include:
  * You misspelled a built-in dotnet command.
  * You intended to execute a .NET Core program, but dotnet-xyz does not exist.
  * You intended to run a global tool, but a dotnet-prefixed executable with this name could not be found on the PATH.
```

可執行檔的名稱決定了如何調用該工具。 下表描述了格式：

| 可執行名稱格式  | 調用格式   |
|-------------------------|---------------------|
| `dotnet-<toolName>.exe` | `dotnet <toolName>` |
| `<toolName>.exe`        | `<toolName>`        |

* 全域工具

  全域工具可以安裝在預設目錄或特定位置。 預設目錄如下：

  | OS          | Path                          |
  |-------------|-------------------------------|
  | Linux/macOS | `$HOME/.dotnet/tools`         |
  | Windows     | `%USERPROFILE%\.dotnet\tools` |

  如果嘗試運行全域工具，請檢查電腦上的`PATH`環境變數是否包含安裝全域工具的路徑，以及可執行檔是否位於該路徑中。

  .NET 核心 CLI 嘗試在其首次使用時將預設位置添加到 PATH 環境變數。 但是，在某些情況下，位置可能無法自動添加到 PATH：

  * 如果您使用的是 Linux，並且已使用 *.tar.gz*檔安裝了 .NET Core SDK，而不是 apt-get 或 rpm。
  * 如果您使用的是 macOS 10.15"Catalina"或更高版本。
  * 如果您使用的是 macOS 10.14"Mojave"或早期版本，並且已安裝 .NET Core SDK 使用 *.tar.gz*檔而不是 *.pkg*。
  * 如果您安裝了 .NET Core 3.0 SDK，並且將`DOTNET_ADD_GLOBAL_TOOLS_TO_PATH`環境變數設置為`false`。
  * 如果您已安裝 .NET Core 2.2 SDK 或早期版本，並且將`DOTNET_SKIP_FIRST_TIME_EXPERIENCE`環境變數設置為`true`。

  在這些情況下，或者如果指定了`--tool-path`該選項，電腦上的`PATH`環境變數不會自動包含安裝全域工具的路徑。 在這種情況下，通過使用 shell 為更新`$HOME/.dotnet/tools``PATH`環境變數提供的任何方法將工具位置（例如 ，）追加到環境變數。 有關詳細資訊，請參閱[.NET 核心工具](global-tools.md)。

* 本機工具

  如果您嘗試運行本地工具，請驗證目前的目錄中是否有名為*dotnet-tools.json*的清單檔或其任何父目錄。 此檔還可以位於專案資料夾層次結構中任何位置的名為 *.config*的資料夾下，而不是根資料夾。 如果*dotnet 工具.json*存在，請打開它並檢查您嘗試運行的工具。 如果檔不包含 的`"isRoot": true`條目，則還會進一步檢查檔層次結構中的其他工具清單檔。

  如果嘗試運行使用指定路徑安裝的 .NET Core 工具，則需要在使用該工具時包括該路徑。 使用工具路徑安裝工具的示例包括：

  ```console
  ..\<toolDirectory>\dotnet-<toolName>
  ```

### <a name="runtime-not-found"></a>未找到運行時

.NET Core 工具是[依賴于框架的應用程式](../deploying/index.md#publish-runtime-dependent)，這意味著它們依賴于電腦上安裝的 .NET Core 運行時。 如果未找到預期的運行時，它們將遵循正常的 .NET Core 運行時前滾規則，例如：

* 應用程式會向前復原到指定的主要和次要版本的最高修補程式版本。
* 如果沒有匹配的主要版本號和次要版本號的匹配運行時，則使用下一個較高的次要版本。
* 預覽版本的執行階段之間或預覽版本和發行版本之間，不會進行向前復原。 因此，使用預覽版本創建的 .NET Core 工具必須由作者重新生成並重新發佈並重新安裝。

預設情況下，在兩種常見方案中不會發生前滾：

* 只有較低版本的運行時可用。 前滾僅選擇更高版本的運行時。
* 只有更高的主要執行階段版本可用。 前滾不會跨越主要版本邊界。

如果應用程式找不到適當的運行時，它將無法運行並報告錯誤。

您可以使用以下命令之一瞭解電腦上安裝了哪些 .NET Core 運行時：

```dotnetcli
dotnet --list-runtimes
dotnet --info
```

如果您認為該工具應支援當前安裝的執行階段版本，可以聯繫工具作者，看看他們是否可以更新版本號或多目標。 一旦他們重新編譯並重新發佈其工具組到 NuGet 與更新的版本號，您可以更新您的副本。 雖然這種情況不會發生，但最快的解決方案是安裝一個執行階段版本，該版本將與您嘗試運行的工具配合使用。 要下載特定的 .NET 酷睿執行階段版本，請訪問[.NET 核心下載頁面](https://dotnet.microsoft.com/download/dotnet-core)。

如果將 .NET Core SDK 安裝到非預設位置，則需要將環境變數`DOTNET_ROOT`設置為包含`dotnet`可執行檔的目錄。

## <a name="net-core-tool-installation-fails"></a>.NET 核心工具安裝失敗

安裝 .NET Core 全域或本地工具可能會失敗的原因有很多。 當工具安裝失敗時，您將看到類似于以下內容的消息：

```console
Tool '{0}' failed to install. This failure may have been caused by:

* You are attempting to install a preview release and did not use the --version option to specify the version.
* A package by this name was found, but it was not a .NET Core tool.
* The required NuGet feed cannot be accessed, perhaps because of an Internet connection problem.
* You mistyped the name of the tool.

For more reasons, including package naming enforcement, visit https://aka.ms/failure-installing-tool
```

為了説明診斷這些故障，NuGet 消息將直接顯示給使用者，以及上一條消息。 NuGet 消息可以説明您識別問題。

### <a name="package-naming-enforcement"></a>包命名強制

Microsoft 更改了對工具的包 ID 的指導，導致找不到許多具有預測名稱的工具。 新的指南是，所有 Microsoft 工具都預綴于"微軟"。 此首碼是保留的，只能用於使用 Microsoft 授權證書簽名的包。

在過渡期間，某些 Microsoft 工具將具有舊形式的包 ID，而其他工具將具有新形式：

```dotnetcli
dotnet tool install -g Microsoft.<toolName>
dotnet tool install -g <toolName>
```

更新包 ID 後，您需要更改為新的包 ID 以獲取最新更新。 使用簡化工具名稱的包將被棄用。

### <a name="preview-releases"></a>預覽版本

* 您正在嘗試安裝預覽版本，但沒有使用`--version`該選項來指定版本。

預覽中的 .NET 核心工具必須使用名稱的一部分進行指定，以指示它們處於預覽狀態。 您無需包括整個預覽。 假設版本號採用預期格式，則可以使用類似下面的示例：

```dotnetcli
dotnet tool install -g --version 1.1.0-pre <toolName>
```

### <a name="package-isnt-a-net-core-tool"></a>包不是 .NET 核心工具

* 找到此名稱的 NuGet 包，但它不是 .NET Core 工具。

如果您嘗試安裝 NuGet 包，該包是常規 NuGet 包，而不是 .NET Core 工具，您將看到類似于以下內容的錯誤：

> NU1212：不正確專案`<ToolName>`包組合。 DotnetTool 參考專案樣式只能包含 DotnetTool 類型的引用。

### <a name="nuget-feed-cant-be-accessed"></a>無法訪問 NuGet 源

* 無法訪問所需的 NuGet 源，可能是因為 Internet 連接問題。

工具安裝需要訪問包含工具組的 NuGet 源。 如果源不可用，它將失敗。 您可以使用 更改 源`nuget.config`，請求特定`nuget.config`檔，或使用`--add-source`交換器指定其他源。 預設情況下，NuGet 會為無法連接的任何源引發錯誤。 標誌`--ignore-failed-sources`可以跳過這些無法訪問的源。

### <a name="package-id-incorrect"></a>包 ID 不正確

* 鍵入工具的名稱錯誤。

失敗的一個常見原因是工具名稱不正確。 這可能是由於霧化，或者因為工具移動或被棄用。 對於NuGet.org上的工具，確保名稱正確的方法之一是在NuGet.org處搜索該工具並複製安裝命令。

## <a name="see-also"></a>另請參閱

* [.NET 核心工具](global-tools.md)
