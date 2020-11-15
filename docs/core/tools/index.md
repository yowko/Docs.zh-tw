---
title: .NET CLI
titleSuffix: ''
description: .NET CLI 和其功能的總覽。
ms.topic: overview
ms.date: 02/13/2020
ms.openlocfilehash: 6a12e2d16afe36092c10e14a7465fa3bdbb23f32
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "94633852"
---
# <a name="net-cli-overview"></a>.NET CLI 總覽

本文 **適用于：** ✔️ .net CORE 2.1 SDK 和更新版本

.NET 命令列介面 (CLI) 是用於開發、建立、執行和發佈 .NET 應用程式的跨平臺工具鏈。

.Net CLI 隨附于 [.NET SDK](../sdk.md)。 若要瞭解如何安裝 .NET SDK，請參閱 [安裝 .Net Core](../install/windows.md)。

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
- [`tool restore`](global-tools.md#install-a-local-tool) 自 .NET Core SDK 3.0 起提供。
- [`tool run`](global-tools.md#invoke-a-local-tool) 自 .NET Core SDK 3.0 起提供。
- [`tool uninstall`](dotnet-tool-uninstall.md)

工具是從 NuGet 套件安裝的主控台應用程式，會從命令提示字元叫用。 您可以自行撰寫工具或安裝協力廠商所撰寫的工具。 工具也稱為「通用工具」、「工具路徑工具」和「本機工具」。 如需詳細資訊，請參閱 [.net 工具總覽](global-tools.md)。

## <a name="command-structure"></a>命令結構

CLI 命令結構包含[驅動程式 ("dotnet")](#driver)、[命令](#command)，以及可能的命令[引數](#arguments)及[選項](#options)。 您可以在大部分的 CLI 作業中看到此模式，例如從名稱為 *my_app* 的目錄執行以下命令，以建立新的主控台應用程式並從命令列執行它：

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a>驅動程式

驅動器的名稱是 [dotnet](dotnet.md)，且有兩個責任：執行[相依於架構的應用程式](../deploying/index.md)或執行命令。

若要執行相依於架構的應用程式，請在驅動器之後指定應用程式，例如 `dotnet /path/to/my_app.dll`。 從應用程式的 DLL 所在的資料夾執行該命令時，只要執行 `dotnet my_app.dll` 即可。 如果您想要使用特定版本的 .NET 執行時間，請使用 `--fx-version <VERSION>` 選項 (參閱 [dotnet 命令](dotnet.md) 參考) 。

當您提供命令給驅動器時，`dotnet.exe` 會啟動 CLI 命令執行程序。 例如：

```dotnetcli
dotnet build
```

首先，驅動器會決定要使用的 SDK 版本。 如果檔案沒有 [global.js](global-json.md) ，則會使用最新版本的 SDK。 這可能是預覽版或穩定的版本，視兩者中何者版本最新。  確定 SDK 版本之後，就會開始執行命令。

### <a name="command"></a>命令

此命令會執行動作。 例如，`dotnet build` 會建置程式碼。 `dotnet publish` 會發佈程式碼。 命令是使用 `dotnet {command}` 慣例實作為主控台應用程式。

### <a name="arguments"></a>引數

您在命令列上傳遞的引數即為叫用命令的引數。 例如，當您執行時 `dotnet publish my_app.csproj` ， `my_app.csproj` 引數會指出要發行的專案，並傳遞至 `publish` 命令。

### <a name="options"></a>選項

您在命令列上傳遞的選項即為叫用命令的選項。 例如，當您執行時 `dotnet publish --output /build_output` ， `--output` 選項和其值會傳遞至 `publish` 命令。

## <a name="see-also"></a>另請參閱

- [dotnet/sdk GitHub 存放庫](https://github.com/dotnet/sdk/)
- [.NET 安裝指南](../install/windows.md)
