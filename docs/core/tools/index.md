---
title: .NET Core CLI
titleSuffix: ''
description: .NET 核心 CLI 及其功能的概述。
ms.date: 02/13/2020
ms.openlocfilehash: ac5988bacbef41326f2501a2cff6c3f5aa0be798
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80110837"
---
# <a name="net-core-cli-overview"></a>.NET Core CLI 概觀

**本文適用于：✔️** .NET 核心 2.1 SDK 和更高版本

.NET Core 命令列介面 （CLI） 是一個跨平臺工具鏈，用於開發、構建、運行和發佈 .NET Core 應用程式。

.NET 核心 CLI 包含在[.NET 核心 SDK](../sdk.md)中。 要瞭解如何安裝 .NET 核心 SDK，請參閱[安裝 .NET 核心 SDK](../install/sdk.md)。

## <a name="cli-commands"></a>CLI 命令

預設會安裝下列命令：

### <a name="basic-commands"></a>基本命令

- [`new`](dotnet-new.md)
- [`restore`](dotnet-restore.md)
- [`build`](dotnet-build.md)
- [`publish`](dotnet-publish.md)
- [`run`](dotnet-run.md)
- [`test`](dotnet-test.md)
- [`vstest`](dotnet-vstest.md)
- [`pack`](dotnet-pack.md)
- [`migrate`](dotnet-migrate.md)
- [`clean`](dotnet-clean.md)
- [`sln`](dotnet-sln.md)
- [`help`](dotnet-help.md)
- [`store`](dotnet-store.md)

### <a name="project-modification-commands"></a>專案修改命令

- [`add package`](dotnet-add-package.md)
- [`add reference`](dotnet-add-reference.md)
- [`remove package`](dotnet-remove-package.md)
- [`remove reference`](dotnet-remove-reference.md)
- [`list reference`](dotnet-list-reference.md)

### <a name="advanced-commands"></a>進階命令

- [`nuget delete`](dotnet-nuget-delete.md)
- [`nuget locals`](dotnet-nuget-locals.md)
- [`nuget push`](dotnet-nuget-push.md)
- [`msbuild`](dotnet-msbuild.md)
- [`dotnet install script`](dotnet-install-script.md)

### <a name="tool-management-commands"></a>工具管理命令

- [`tool install`](dotnet-tool-install.md)
- [`tool list`](dotnet-tool-list.md)
- [`tool update`](dotnet-tool-update.md)
- [`tool restore`](global-tools.md#install-a-local-tool)自 .NET 核心 SDK 3.0 起可用。
- [`tool run`](global-tools.md#invoke-a-local-tool)自 .NET 核心 SDK 3.0 起可用。
- [`tool uninstall`](dotnet-tool-uninstall.md)

工具是從 NuGet 包安裝並從命令提示符調用的主控台應用程式。 您可以自己編寫工具或安裝由協力廠商編寫的工具。 工具也稱為全域工具、刀具路徑工具和本地工具。 有關詳細資訊，請參閱[.NET 核心工具概述](global-tools.md)。

## <a name="command-structure"></a>命令結構

CLI 命令結構包含[驅動程式 ("dotnet")](#driver)、[命令](#command)，以及可能的命令[引數](#arguments)及[選項](#options)。 您可以在大部分的 CLI 作業中看到此模式，例如從名稱為 *my_app* 的目錄執行以下命令，以建立新的主控台應用程式並從命令列執行它：

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a>驅動程式

驅動器的名稱是 [dotnet](dotnet.md)，且有兩個責任：執行[相依於架構的應用程式](../deploying/index.md)或執行命令。

若要執行相依於架構的應用程式，請在驅動器之後指定應用程式，例如 `dotnet /path/to/my_app.dll`。 從應用程式的 DLL 所在的資料夾執行該命令時，只要執行 `dotnet my_app.dll` 即可。 若要使用特定版本的 .NET Core 執行階段，請使用 `--fx-version <VERSION>` 選項 (請參閱 [dotnet 命令](dotnet.md) 參考)。

當您提供命令給驅動器時，`dotnet.exe` 會啟動 CLI 命令執行程序。 例如：

```dotnetcli
dotnet build
```

首先，驅動器會決定要使用的 SDK 版本。 如果沒有[全域.json](global-json.md)檔，則使用可用的 SDK 的最新版本。 這可能是預覽版或穩定的版本，視兩者中何者版本最新。  確定 SDK 版本之後，就會開始執行命令。

### <a name="command"></a>Command

此命令會執行動作。 例如，`dotnet build` 會建置程式碼。 `dotnet publish` 會發佈程式碼。 命令是使用 `dotnet {command}` 慣例實作為主控台應用程式。

### <a name="arguments"></a>引數

您在命令列上傳遞的引數即為叫用命令的引數。 例如，執行`dotnet publish my_app.csproj`時，`my_app.csproj`參數指示要發佈的專案，並將其傳遞給命令。 `publish`

### <a name="options"></a>選項。

您在命令列上傳遞的選項即為叫用命令的選項。 例如，執行 時`dotnet publish --output /build_output`，`--output`選項及其值將傳遞給命令。 `publish`

## <a name="see-also"></a>另請參閱

- [點網/sdk GitHub 存儲庫](https://github.com/dotnet/sdk/)
- [.NET core 安裝指南 (英文)](../install/sdk.md)
