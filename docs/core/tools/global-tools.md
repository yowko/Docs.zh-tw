---
title: " .NET Core 工具"
description: 如何安裝、使用、更新和移除 .NET Core 工具。 涵蓋通用工具、工具路徑工具和本機工具。
author: KathleenDollard
ms.topic: how-to
ms.date: 02/12/2020
ms.openlocfilehash: 00c0317fcfc4da0e7205c23faa7b355c20882ec9
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062726"
---
# <a name="how-to-manage-net-core-tools"></a>如何管理 .NET Core 工具

**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本

.NET Core 工具是特殊的 NuGet 套件，其中包含主控台應用程式。 您可以透過下列方式將工具安裝在您的電腦上：

* 作為通用工具。

  工具二進位檔會安裝在新增至 PATH 環境變數的預設目錄中。 您可以從電腦上的任何目錄叫用此工具，而不需要指定其位置。 其中一個工具版本會用於電腦上的所有目錄。

* 做為自訂位置中的全域工具 (也稱為工具路徑工具) 。

  工具二進位檔會安裝在您指定的位置。 您可以從安裝目錄叫用此工具，或使用命令名稱提供目錄，或將目錄加入 PATH 環境變數中。 其中一個工具版本會用於電腦上的所有目錄。

* 作為本機工具 (適用于 .NET Core SDK 3.0 和更新版本) 。

  工具二進位檔會安裝在預設目錄中。 您可以從安裝目錄或其任何子目錄叫用此工具。 不同的目錄可以使用相同工具的不同版本。
  
  .NET CLI 會使用資訊清單檔案來追蹤哪些工具會以本機方式安裝到目錄。 當資訊清單檔案儲存在原始程式碼存放庫的根目錄時，參與者可以複製存放庫，並叫用單一 .NET Core CLI 命令，以安裝資訊清單檔案中列出的所有工具。

> [!IMPORTANT]
> .NET Core 工具會以完全信任的方式執行。 除非您信任作者，否則請勿安裝 .NET Core 工具。

## <a name="find-a-tool"></a>尋找工具

目前，.NET Core 沒有工具搜尋功能。 以下是尋找工具的一些方法：

* 使用 [.NET 工具] 套件類型篩選來搜尋[NuGet](https://www.nuget.org)網站。 如需詳細資訊，請參閱[尋找及選擇套件](/nuget/consume-packages/finding-and-choosing-packages)。
* 請參閱[natemcmaster/dotnet 工具](https://github.com/natemcmaster/dotnet-tools)GitHub 存放庫中的工具清單。
* 使用[ToolGet](https://www.toolget.net/)來搜尋 .net 工具。
* 請參閱[dotnet/Aspnetcore GitHub 存放庫的 tools 目錄](https://github.com/dotnet/aspnetcore/tree/master/src/Tools)中，由 ASP.NET Core 小組所建立之工具的原始程式碼。
* 深入瞭解[.Net Core dotnet 診斷工具](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools)的診斷工具。

## <a name="check-the-author-and-statistics"></a>檢查作者和統計資料

由於 .NET Core 工具會以完全信任的方式執行，且會將通用工具加入 PATH 環境變數中，因此可以非常強大。 請不要下載來自不信任人員的工具。

如果此工具裝載在 NuGet 上，您可以搜尋工具來檢查作者和統計資料。

## <a name="install-a-global-tool"></a>安裝通用工具

若要將工具安裝為全域工具，請使用 `-g` `--global` [dotnet 工具安裝](dotnet-tool-install.md)的或選項，如下列範例所示：

```dotnetcli
dotnet tool install -g dotnetsay
```

輸出會顯示用來叫用工具的命令，以及安裝的版本，類似于下列範例：

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
```

工具二進位檔的預設位置取決於作業系統：

| OS          | 路徑                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

此位置會在 SDK 第一次執行時新增至使用者的路徑，因此可以從任何目錄叫用全域工具，而不需指定工具位置。

工具存取是使用者特定的，而不是電腦全域。 通用工具僅適用于已安裝此工具的使用者。

### <a name="install-a-global-tool-in-a-custom-location"></a>在自訂位置安裝通用工具

若要在自訂位置將工具安裝為全域工具，請使用 `--tool-path` [dotnet 工具安裝](dotnet-tool-install.md)選項，如下列範例所示。

在 Windows 上：

```dotnetcli
dotnet tool install dotnetsay --tool-path c:\dotnet-tools
```

在 Linux 或 macOS 上：

```dotnetcli
dotnet tool install dotnetsay --tool-path ~/bin
```

.NET Core SDK 不會自動將此位置新增至 PATH 環境變數。 若要叫用[工具路徑工具](#invoke-a-tool-path-tool)，您必須使用下列其中一種方法來確定命令是否可用：

* 將安裝目錄新增至 PATH 環境變數。
* 當您叫用它時，請指定該工具的完整路徑。
* 從安裝目錄中叫用工具。

## <a name="install-a-local-tool"></a>安裝本機工具

**適用于 .NET Core 3.0 SDK 和更新版本。**

若要針對目前目錄和) 子目錄安裝僅限本機存取的工具 (，必須將它新增至工具資訊清單檔。 若要建立工具資訊清單檔，請執行 `dotnet new tool-manifest` 命令：

```dotnetcli
dotnet new tool-manifest
```

此命令會在 *.config*目錄下建立名為*dotnet-tools.js*的資訊清單檔。 若要將本機工具新增至資訊清單檔，請使用[dotnet tool install](dotnet-tool-install.md)命令並**省略** `--global` 和 `--tool-path` 選項，如下列範例所示：

```dotnetcli
dotnet tool install dotnetsay
```

命令輸出會顯示新安裝工具所在的資訊清單檔，類似于下列範例：

```console
You can invoke the tool from this directory using the following command:
dotnet tool run dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
Entry is added to the manifest file /home/name/botsay/.config/dotnet-tools.json.
```

下列範例顯示已安裝兩個本機工具的資訊清單檔案：

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

您通常會將本機工具新增至存放庫的根目錄。 將資訊清單檔案簽入存放庫之後，從存放庫簽出程式碼的開發人員會取得最新的資訊清單檔案。 若要安裝資訊清單檔案中列出的所有工具，請執行 `dotnet tool restore` 下列命令：

```dotnetcli
dotnet tool restore
```

輸出會指出哪些工具已還原：

```console
Tool 'botsay' (version '1.0.0') was restored. Available commands: botsay
Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
Restore was successful.
```

## <a name="install-a-specific-tool-version"></a>安裝特定的工具版本

若要安裝發行前版本或特定版本的工具，請使用選項來指定版本號碼 `--version` ，如下列範例所示：

```dotnetcli
dotnet tool install dotnetsay --version 2.1.3
```

## <a name="use-a-tool"></a>使用工具

您用來叫用工具的命令可能與您安裝的封裝名稱不同。 若要顯示目前使用者在電腦上所安裝的所有工具，請使用[dotnet tool list](dotnet-tool-list.md)命令：

```dotnetcli
dotnet tool list
```

輸出會顯示每個工具的版本和命令，與下列範例類似：

```console
Package Id      Version      Commands       Manifest
-------------------------------------------------------------------------------------------
botsay          1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
dotnetsay       2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
```

如本範例所示，此清單會顯示本機工具。 若要查看通用工具，請使用 `--global` 選項，若要查看工具路徑工具，請使用 `--tool-path` 選項。

### <a name="invoke-a-global-tool"></a>叫用全域工具

針對通用工具，請單獨使用工具命令。 例如，如果命令為 `dotnetsay` 或 `dotnet-doc` ，這就是您用來叫用命令的內容：

```console
dotnetsay
dotnet-doc
```

如果命令的開頭為前置詞 `dotnet-` ，則叫用此工具的另一種方法是使用 `dotnet` 命令，並省略工具命令前置詞。 例如，如果命令為 `dotnet-doc` ，則下列命令會叫用工具：

```dotnetcli
dotnet doc
```

不過，在下列案例中，您無法使用 `dotnet` 命令來叫用通用工具：

* 全域工具和本機工具的前面會加上相同的命令 `dotnet-` 。
* 您想要從本機工具範圍內的目錄叫用全域工具。

在此案例中，和會叫用 `dotnet doc` `dotnet dotnet-doc` 本機工具。 若要叫用全域工具，請使用命令本身：

```dotnetcli
dotnet-doc
```

### <a name="invoke-a-tool-path-tool"></a>叫用工具路徑工具

若要叫用使用選項安裝的全域工具 `tool-path` ，請確定命令可用，如[本文稍早](#install-a-global-tool-in-a-custom-location)所述。

### <a name="invoke-a-local-tool"></a>叫用本機工具

若要叫用本機工具，您必須 `dotnet` 從安裝目錄中使用命令。 您可以使用完整格式的 (`dotnet tool run <COMMAND_NAME>`) 或簡短形式的 (`dotnet <COMMAND_NAME>`) ，如下列範例所示：

```dotnetcli
dotnet tool run dotnetsay
dotnet dotnetsay
```

如果命令前面加 `dotnet-` 上，您可以在叫用工具時包含或省略前置詞。 例如，如果命令為 `dotnet-doc` ，下列任何一個範例都會叫用本機工具：

```dotnetcli
dotnet tool run dotnet-doc
dotnet dotnet-doc
dotnet doc
```

## <a name="update-a-tool"></a>更新工具

更新工具時，需要使用最新的穩定版本卸載並重新安裝它。 若要更新工具，請使用[dotnet tool update](dotnet-tool-update.md)命令，並搭配您用來安裝工具的相同選項：

```dotnetcli
dotnet tool update --global <packagename>
dotnet tool update --tool-path <packagename>
dotnet tool update <packagename>
```

針對本機工具，SDK 會藉由查看目前的目錄和上層目錄，尋找包含封裝識別碼的第一個資訊清單檔案。 如果沒有任何資訊清單檔中的封裝識別碼，SDK 會將新專案新增至最接近的資訊清單檔案。

## <a name="uninstall-a-tool"></a>卸載工具

使用 [ [dotnet 工具](dotnet-tool-uninstall.md)] [卸載] 命令，並使用您用來安裝工具的相同選項來移除工具：

```dotnetcli
dotnet tool uninstall --global <packagename>
dotnet tool uninstall --tool-path <packagename>
dotnet tool uninstall <packagename>
```

針對本機工具，SDK 會藉由查看目前的目錄和上層目錄，尋找包含封裝識別碼的第一個資訊清單檔案。

## <a name="get-help-and-troubleshoot"></a>取得協助和疑難排解

若要取得可用命令的清單 `dotnet tool` ，請輸入下列命令：

```dotnetcli
dotnet tool --help
```

若要取得工具使用方式的指示，請輸入下列其中一個命令，或查看工具的網站：

```dotnetcli
<command> --help
dotnet <command> --help
```

如果工具無法安裝或執行，請參閱針對[.Net Core 工具使用問題進行疑難排解](troubleshoot-usage-issues.md)。

## <a name="see-also"></a>另請參閱

- [教學課程：使用 .NET Core CLI 建立 .NET Core 工具](global-tools-how-to-create.md)
- [教學課程：使用 .NET Core CLI 安裝和使用 .NET Core 通用工具](global-tools-how-to-use.md)
- [教學課程：使用 .NET Core CLI 安裝和使用 .NET Core 本機工具](local-tools-how-to-use.md)
