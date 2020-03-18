---
title: .NET 核心工具
description: 如何安裝、使用、更新和刪除 .NET 核心工具。 涵蓋全域工具、刀具路徑工具和本地工具。
author: KathleenDollard
ms.date: 02/12/2020
ms.openlocfilehash: 2f0101c6385c41eda49bcb2458428c1f14552617
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847779"
---
# <a name="how-to-manage-net-core-tools"></a>如何管理 .NET 核心工具

**本文適用于：✔️** .NET 核心 2.1 SDK 和更高版本

.NET Core 工具是包含主控台應用程式的特殊 NuGet 包。 可通過以下方式在機器上安裝工具：

* 作為一個全域工具。

  工具二進位檔案安裝在添加到 PATH 環境變數的預設目錄中。 可以從電腦上的任何目錄調用該工具，而無需指定其位置。 工具的一個版本用於電腦上的所有目錄。

* 作為自訂位置的全域工具（也稱為工具路徑工具）。

  工具二進位檔案安裝在您指定的位置。 可以從安裝目錄中調用該工具，也可以通過向目錄提供命令名稱或將目錄添加到 PATH 環境變數來調用該工具。 工具的一個版本用於電腦上的所有目錄。

* 作為本地工具（適用于 .NET 核心 SDK 3.0 及更高版本）。

  工具二進位檔案安裝在預設目錄中。 從安裝目錄或其任何子目錄調用該工具。 不同的目錄可以使用同一工具的不同版本。
  
  .NET CLI 使用清單檔來跟蹤哪些工具作為目錄的本地安裝。 當清單檔保存在原始程式碼存儲庫的根目錄中時，參與者可以克隆存儲庫並調用單個 .NET Core CLI 命令，該命令安裝清單檔中列出的所有工具。

> [!IMPORTANT]
> .NET 核心工具完全信任運行。 除非信任作者，否則不要安裝 .NET Core 工具。

## <a name="find-a-tool"></a>查找工具

目前，.NET Core 沒有工具搜索功能。 以下是查找工具的一些方法：

* 請參閱[natemcmaster/點網工具](https://github.com/natemcmaster/dotnet-tools)GitHub 存儲庫中的工具清單。
* 使用[工具獲取](https://www.toolget.net/)搜索 .NET 工具。
* 在[dotnet/aspnetcore GitHub 存儲庫的工具目錄中](https://github.com/dotnet/aspnetcore/tree/master/src/Tools)，請參閱 ASP.NET核心團隊創建的工具的原始程式碼。
* 瞭解[.NET 核心點網診斷工具](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools)的診斷工具。
* 搜索[NuGet](https://www.nuget.org)網站。 但是，NuGet 網站還沒有一個功能，允許您只搜索工具組。

## <a name="check-the-author-and-statistics"></a>檢查作者和統計資料

由於 .NET Core 工具完全信任運行，並且全域工具被添加到 PATH 環境變數中，因此它們可能非常強大。 請不要下載來自不信任人員的工具。

如果此工具裝載在 NuGet 上，您可以搜尋工具來檢查作者和統計資料。

## <a name="install-a-global-tool"></a>安裝全域工具

要將工具安裝為全域工具，請使用`-g`[dotnet 工具安裝](dotnet-tool-install.md)的 或`--global`選項，如以下示例所示：

```dotnetcli
dotnet tool install -g dotnetsay
```

輸出顯示用於調用工具和安裝的版本的命令，類似于以下示例：

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
```

工具二進位檔案的預設位置取決於作業系統：

| OS          | Path                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

首次運行 SDK 時，此位置將添加到使用者的路徑中，因此可以從任何目錄調用全域工具，而無需指定工具位置。

工具訪問是特定于使用者的，而不是電腦全域。 全域工具僅對安裝該工具的使用者可用。

### <a name="install-a-global-tool-in-a-custom-location"></a>在自訂位置安裝全域工具

要將工具作為全域工具安裝在自訂位置，請使用`--tool-path`[dotnet 工具安裝](dotnet-tool-install.md)選項，如以下示例所示。

在 Windows 上：

```dotnetcli
dotnet tool install dotnetsay --tool-path c:\dotnet-tools
```

在 Linux 或 macOS 上：

```dotnetcli
dotnet tool install dotnetsay --tool-path ~/bin
```

.NET 核心 SDK 不會自動將此位置添加到 PATH 環境變數。 要[調用工具路徑工具](#invoke-a-tool-path-tool)，您必須使用以下方法之一確保該命令可用：

* 將安裝目錄添加到 PATH 環境變數。
* 調用工具時指定工具的完整路徑。
* 從安裝目錄中調用該工具。

## <a name="install-a-local-tool"></a>安裝本地工具

**適用于 .NET 核心 3.0 SDK 及更高版本。**

要僅安裝用於本地訪問的工具（對於目前的目錄和子目錄），必須將其添加到工具清單檔中。 要創建工具清單檔，請運行以下`dotnet new tool-manifest`命令：

```dotnetcli
dotnet new tool-manifest
```

此命令在 *.config*目錄下創建名為*dotnet-tools.json*的清單檔。 要向清單檔添加本地工具，請使用[dotnet 工具安裝](dotnet-tool-install.md)命令並**省略**和`--global``--tool-path`選項，如以下示例所示：

```dotnetcli
dotnet tool install dotnetsay
```

命令輸出顯示新安裝的工具位於哪個清單檔，類似于以下示例：

```console
You can invoke the tool from this directory using the following command:
dotnet tool run dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
Entry is added to the manifest file /home/name/botsay/.config/dotnet-tools.json.
```

下面的示例顯示了一個已安裝兩個本地工具的清單檔：

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "botsay": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    },
    "dotnetsay": {
      "version": "2.1.3",
      "commands": [
        "dotnetsay"
      ]
    }
  }
}
```

通常將本地工具添加到存儲庫的根目錄。 將清單檔簽入存儲庫後，從存儲庫簽出代碼的開發人員將獲得最新的清單檔。 要安裝清單檔中列出的所有工具，它們運行以下`dotnet tool restore`命令：

```dotnetcli
dotnet tool restore
```

輸出指示已還原的工具：

```console
Tool 'botsay' (version '1.0.0') was restored. Available commands: botsay
Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
Restore was successful.
```

## <a name="install-a-specific-tool-version"></a>安裝特定的工具版本

要安裝預發佈版本或工具的特定版本，請使用`--version`選項指定版本號，如以下示例所示：

```dotnetcli
dotnet tool install dotnetsay --version 2.1.3
```

## <a name="use-a-tool"></a>使用工具

用於調用工具的命令可能與安裝的包的名稱不同。 要顯示當前使用者電腦上當前安裝的所有工具，請使用[dotnet 工具清單](dotnet-tool-list.md)命令：

```dotnetcli
dotnet tool list
```

輸出顯示每個工具的版本和命令，類似于以下示例：

```console
Package Id      Version      Commands       Manifest
-------------------------------------------------------------------------------------------
botsay          1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
dotnetsay       2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
```

如本示例所示，清單顯示本地工具。 要查看全域工具，請使用 選項`--global`，要查看工具路徑工具，請使用 選項`--tool-path`。

### <a name="invoke-a-global-tool"></a>調用全域工具

對於全域工具，請使用工具命令本身。 例如，如果命令是`dotnetsay`或`dotnet-doc`，則用於調用 命令：

```console
dotnetsay
dotnet-doc
```

如果命令以首碼`dotnet-`開頭，則調用該工具的另一種方法是使用 命令`dotnet`並省略工具命令首碼。 例如，如果命令為`dotnet-doc`，以下命令將調用該工具：

```dotnetcli
dotnet doc
```

但是，在以下方案中，不能使用 命令`dotnet`調用全域工具：

* 全域工具和本地工具具有相同的命令，該命令由 預`dotnet-`定。
* 您希望從本地工具範圍內的目錄中調用全域工具。

在這種情況下，`dotnet doc`並`dotnet dotnet-doc`調用本地工具。 要調用全域工具，請自行使用 命令：

```dotnetcli
dotnet-doc
```

### <a name="invoke-a-tool-path-tool"></a>調用工具路徑工具

要調用使用`tool-path`option 安裝的全域工具，請確保該命令可用，如[本文前面](#install-a-global-tool-in-a-custom-location)所述。

### <a name="invoke-a-local-tool"></a>調用本地工具

要調用本地工具，必須從安裝目錄中使用`dotnet`該命令。 您可以使用長表單 （`dotnet tool run <COMMAND_NAME>`） 或短表單 （`dotnet <COMMAND_NAME>`），如以下示例所示：

```dotnetcli
dotnet tool run dotnetsay
dotnet dotnetsay
```

如果命令被預綴于`dotnet-`，則可以在調用該工具時包括或省略首碼。 例如，如果命令為`dotnet-doc`，以下任何示例都調用本地工具：

```dotnetcli
dotnet tool run dotnet-doc
dotnet dotnet-doc
dotnet doc
```

## <a name="update-a-tool"></a>更新工具

更新工具涉及卸載和重新安裝它與最新的穩定版本。 要更新工具，請使用[dotnet 工具更新](dotnet-tool-update.md)命令，該選項與安裝該工具的選項相同：

```dotnetcli
dotnet tool update --global <packagename>
dotnet tool update --tool-path <packagename>
dotnet tool update <packagename>
```

對於本地工具，SDK 通過查找目前的目錄和父目錄查找包含包 ID 的第一個清單檔。 如果任何清單檔中沒有此類包 ID，SDK 會向最近的清單檔添加新條目。

## <a name="uninstall-a-tool"></a>卸載工具

使用[dotnet 工具卸載](dotnet-tool-uninstall.md)命令，使用與安裝該工具相同的選項移除工具：

```dotnetcli
dotnet tool uninstall --global <packagename>
dotnet tool uninstall --tool-path<packagename>
dotnet tool uninstall <packagename>
```

對於本地工具，SDK 通過查找目前的目錄和父目錄查找包含包 ID 的第一個清單檔。

## <a name="get-help-and-troubleshoot"></a>獲取説明和故障排除

要獲取可用`dotnet tool`命令的清單，請輸入以下命令：

```dotnetcli
dotnet tool --help
```

要獲取工具使用說明，請輸入以下命令之一或查看該工具的網站：

```dotnetcli
<command> --help
dotnet <command> --help
```

如果工具無法安裝或運行，請參閱[疑難排解 .NET Core 工具使用問題](troubleshoot-usage-issues.md)。

## <a name="see-also"></a>另請參閱

- [教程：使用 .NET 核心 CLI 創建 .NET 核心工具](global-tools-how-to-create.md)
- [教程：使用 .NET 核心 CLI 安裝和使用 .NET 核心全域工具](global-tools-how-to-use.md)
- [教程：使用 .NET 核心 CLI 安裝和使用 .NET 核心本地工具](local-tools-how-to-use.md)
