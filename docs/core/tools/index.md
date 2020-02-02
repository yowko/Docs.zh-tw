---
title: .NET Core CLI
titleSuffix: ''
description: .NET Core CLI 及其功能的總覽。
ms.date: 08/14/2017
ms.openlocfilehash: b0a8e0dd8cf77bb6f7567c27e9972f62515ec0f2
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920487"
---
# <a name="net-core-cli-overview"></a>.NET Core CLI 總覽

.NET Core 命令列介面（CLI）是用於開發、建立、執行和發佈 .NET Core 應用程式的跨平臺工具鏈。

.NET Core CLI 包含在[.NET Core SDK](../sdk.md)中。 若要瞭解如何安裝 .NET Core SDK，請參閱[安裝 .NET Core SDK](../install/sdk.md)。

## <a name="cli-commands"></a>CLI 命令

預設會安裝下列命令：

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

**基本命令**

- [new](dotnet-new.md)
- [restore](dotnet-restore.md)
- [build](dotnet-build.md)
- [publish](dotnet-publish.md)
- [run](dotnet-run.md)
- [test](dotnet-test.md)
- [vstest](dotnet-vstest.md)
- [pack](dotnet-pack.md)
- [migrate](dotnet-migrate.md)
- [clean](dotnet-clean.md)
- [sln](dotnet-sln.md)
- [help](dotnet-help.md)
- [store](dotnet-store.md)

**專案修改命令**

- [add package](dotnet-add-package.md)
- [add reference](dotnet-add-reference.md)
- [remove package](dotnet-remove-package.md)
- [remove reference](dotnet-remove-reference.md)
- [list reference](dotnet-list-reference.md)

**進階命令**

- [nuget delete](dotnet-nuget-delete.md)
- [nuget locals](dotnet-nuget-locals.md)
- [nuget push](dotnet-nuget-push.md)
- [msbuild](dotnet-msbuild.md)
- [dotnet install script](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**基本命令**

- [new](dotnet-new.md)
- [restore](dotnet-restore.md)
- [build](dotnet-build.md)
- [publish](dotnet-publish.md)
- [run](dotnet-run.md)
- [test](dotnet-test.md)
- [vstest](dotnet-vstest.md)
- [pack](dotnet-pack.md)
- [migrate](dotnet-migrate.md)
- [clean](dotnet-clean.md)
- [sln](dotnet-sln.md)

**專案修改命令**

- [add package](dotnet-add-package.md)
- [add reference](dotnet-add-reference.md)
- [remove package](dotnet-remove-package.md)
- [remove reference](dotnet-remove-reference.md)
- [list reference](dotnet-list-reference.md)

**進階命令**

- [nuget delete](dotnet-nuget-delete.md)
- [nuget locals](dotnet-nuget-locals.md)
- [nuget push](dotnet-nuget-push.md)
- [msbuild](dotnet-msbuild.md)
- [dotnet install script](dotnet-install-script.md)

---

CLI 採用擴充性模型，可讓您為專案指定額外工具。 如需詳細資訊，請參閱 [.NET Core CLI 擴充性模型](extensibility.md)主題。

## <a name="command-structure"></a>命令結構

CLI 命令結構包含[驅動程式 ("dotnet")](#driver)、[命令](#command)，以及可能的命令[引數](#arguments)及[選項](#options)。 您可以在大部分的 CLI 作業中看到此模式，例如從名稱為 *my_app* 的目錄執行以下命令，以建立新的主控台應用程式並從命令列執行它：

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```dotnetcli
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

---

### <a name="driver"></a>驅動器

驅動器的名稱是 [dotnet](dotnet.md)，且有兩個責任：執行[相依於架構的應用程式](../deploying/index.md)或執行命令。 

若要執行相依於架構的應用程式，請在驅動器之後指定應用程式，例如 `dotnet /path/to/my_app.dll`。 從應用程式的 DLL 所在的資料夾執行該命令時，只要執行 `dotnet my_app.dll` 即可。 若要使用特定版本的 .NET Core 執行階段，請使用 `--fx-version <VERSION>` 選項 (請參閱 [dotnet 命令](dotnet.md) 參考)。

當您提供命令給驅動器時，`dotnet.exe` 會啟動 CLI 命令執行程序。 例如：

```dotnetcli
dotnet build
```

首先，驅動器會決定要使用的 SDK 版本。 若沒有 ['global.json'](global-json.md)，將會使用最新可用版本的 SDK。 這可能是預覽版或穩定的版本，視兩者中何者版本最新。  確定 SDK 版本之後，就會開始執行命令。

### <a name="command"></a>命令

此命令會執行動作。 例如，`dotnet build` 會建置程式碼。 `dotnet publish` 會發佈程式碼。 命令是使用 `dotnet {command}` 慣例實作為主控台應用程式。

### <a name="arguments"></a>Arguments

您在命令列上傳遞的引數即為叫用命令的引數。 例如當您執行 `dotnet publish my_app.csproj` 時，`my_app.csproj` 引數表示要發佈的專案，並且會傳遞給 `publish` 命令。

### <a name="options"></a>選項

您在命令列上傳遞的選項即為叫用命令的選項。 例如當您執行 `dotnet publish --output /build_output`，`--output` 選項及其值會傳遞給 `publish` 命令。

## <a name="migration-from-projectjson"></a>從 project.json 移轉

如果您使用 Preview 2 工具來產生 *project.json* 型專案，請參閱 [dotnet migrate](dotnet-migrate.md) 主題，來取得移轉專案至 MSBuild/ *.csproj* 以搭配發行工具使用的詳細資訊。 對於在 Preview 2 工具發行之前建立的 .NET Core 專案，請依照[從 DNX 移轉到 .NET Core CLI (project.json)](../migration/from-dnx.md) 中的指導，手動更新專案，然後再使用 `dotnet migrate` 或直接升級您的專案。

## <a name="see-also"></a>請參閱

- [dotnet/sdk GitHub 存放庫](https://github.com/dotnet/sdk/)
- [.NET core 安裝指南 (英文)](https://aka.ms/dotnetcoregs)
