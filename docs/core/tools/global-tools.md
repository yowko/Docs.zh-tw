---
title: .NET Core 通用工具
description: 說明何為 .NET Core 通用工具以及它們可用之 .NET Core CLI 命令的概觀。
author: KathleenDollard
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 077ffd53f1ba2988c80a637aaa109a66139736b0
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697088"
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

```console
dotnet tool install -g dotnetsay
```

如果無法安裝此工具，則會顯示錯誤訊息。 請確認正在檢查您所預期的摘要。

如果您要嘗試安裝發行前版本或特定版本的工具，可以使用下列格式指定版本號碼：

```console
dotnet tool install -g <package-name> --version <version-number>
```

如果安裝成功，則會顯示一則訊息，其中顯示用來呼叫此工具的命令以及安裝的版本，類似於下例範例：

```
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

通用工具可以安裝在預設目錄或特定位置中。 預設目錄如下：

| 作業系統          | 路徑                          |
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

```console
dotnet doc
```

您可以藉由使用 [dotnet tool list](dotnet-tool-list.md) 命令列出已安裝的套件，了解已安裝的通用工具套件中包含哪些工具。

您也可以在工具的網站中，或鍵入下列其中一個命令來尋找使用方式指示：

```console
<command> --help
dotnet <command> --help
```

### <a name="what-could-go-wrong"></a>可能會發生什麼問題

通用工具是[與架構相依的應用程式](../deploying/index.md#framework-dependent-deployments-fdd)，這表示它們會依賴電腦上安裝的 .NET Core 執行階段。 如果找不到預期的執行階段，則會遵循一般的 .NET Core 執行階段向前復原規則，例如：

* 應用程式會向前復原到指定的主要和次要版本的最高修補程式版本。
* 如果沒有與符合的主要和次要版本號碼相符的執行階段，則會使用下一個較高的次要版本。
* 預覽版本的執行階段之間或預覽版本和發行版本之間，不會進行向前復原。 因此，使用預覽版本所建立的通用工具必須重建、由作者重新發行，以及重新安裝。
* 在 .NET Core 2.1 Preview 1 中建立的通用工具可能會發生其他問題。 如需詳細資訊，請參閱 [.NET Core 2.1 Preview 2 的已知問題](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md)。

如果應用程式找不到適當的執行階段，則無法執行，並且會報告錯誤。

另一個可能發生的問題是：使用目前安裝的 .NET Core 執行階段，可能無法執行較早預覽期間所建立的通用工具。 您可以使用下列命令，查看您的電腦上安裝了哪些執行階段：

```console
dotnet --list-runtimes
```

請連絡通用工具的作者，確認他們是否可以重新編譯其工具套件，並以更新的版本號碼重新發行至 NuGet。 一旦他們更新 NuGet 上的套件之後，您就可以更新您的複本。

.NET Core CLI 會在第一次使用時，嘗試將預設位置新增至 PATH 環境變數。 不過，有幾種情況可能不會將位置自動新增至 PATH，例如：

* 如果您已設定 `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` 環境變數。
* 在 macOS 上，如果您已使用 *.tar.gz* 檔案 (而非 *.pkg*) 安裝 .NET Core SDK。
* 在 Linux 上，您需要編輯殼層環境檔案來設定 PATH。

## <a name="other-cli-commands"></a>其他 CLI 命令

.NET Core SDK 包含其他支援 .NET Core 通用工具的命令。 請使用任何 `dotnet tool` 命令搭配下列其中一個選項：

* `--global` 或 `-g` 指定命令適用於使用者範圍通用工具。
* `--tool-path` 指定通用工具的自訂位置。

若要查看哪些命令適用於通用工具：

```console
dotnet tool --help
```

更新通用工具需要解除安裝再使用最新的穩定版本重新安裝。 若要更新通用工具，請使用 [dotnet tool update](dotnet-tool-update.md) 命令：

```console
dotnet tool update -g <packagename>
```

使用 [dotnet tool uninstall](dotnet-tool-uninstall.md) 移除通用工具：

```console
dotnet tool uninstall -g <packagename>
```

若要顯示電腦上目前已安裝的所有通用工具，以及它們的版本和命令，請使用 [dotnet tool list](dotnet-tool-list.md) 命令：

```console
dotnet tool list -g
```