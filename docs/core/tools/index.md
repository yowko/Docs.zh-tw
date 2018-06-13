---
title: .NET Core 命令列介面 (Command-Line Interface, CLI) 工具
description: .NET Core 命令列介面 (CLI) 工具與功能概觀。
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.openlocfilehash: e6519ef560026899344c7fc36d91c2409cf1df9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217928"
---
# <a name="net-core-command-line-interface-cli-tools"></a>.NET Core 命令列介面 (CLI) 工具

.NET Core 命令列介面 (CLI) 是新的跨平台工具鏈，適用於開發 .NET 應用程式。 CLI 是整合式開發環境 (IDE)、編輯器和建置 Orchestrator 等高層級工具所依靠的基礎。

## <a name="installation"></a>安裝

使用原生安裝程式或使用安裝殼層指令碼：

* 原生安裝程式主要用於開發人員的電腦，並且使用每個受支援平台的原生安裝機制，例如 Ubuntu 上的 DEB 套件，或 Windows 上的 MSI 套件組合。 這些安裝程式安裝及設定的環境可供開發人員立即使用，但他們會需要電腦的系統管理權限。 您可以檢視 [.NET Core 安裝指南 (英文)](https://aka.ms/dotnetcoregs) 上的安裝指示。
* 殼層指令碼主要用於設定組建伺服器，或者當您想要安裝工具，但沒有系統管理權限時也可以使用。 安裝指令碼不會在電腦上安裝必要的項目，所以您必須手動安裝這些項目。 如需詳細資訊，請參閱[安裝指令碼參考主題](dotnet-install-script.md)。 如需如何在持續整合 (CI) 組建伺服器上設定 CLI 的詳細資訊，請參閱[在持續整合 (CI) 中使用 .NET Core SDK 和工具](using-ci-with-cli.md)。

根據預設，CLI 會以並存 (Side-By-Side, SxS) 的形式安裝，因此一部電腦上可以同時存在多個版本的 CLI 工具。 [驅動器](#driver)一節詳細說明如何在已安裝多個版本的電腦上判斷所使用的版本。

## <a name="cli-commands"></a>CLI 命令

預設會安裝下列命令：

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

**基本命令**

* [new](dotnet-new.md)
* [restore](dotnet-restore.md)
* [build](dotnet-build.md)
* [publish](dotnet-publish.md)
* [run](dotnet-run.md)
* [test](dotnet-test.md)
* [vstest](dotnet-vstest.md)
* [pack](dotnet-pack.md)
* [migrate](dotnet-migrate.md)
* [clean](dotnet-clean.md)
* [sln](dotnet-sln.md)
* [help](dotnet-help.md)
* [store](dotnet-store.md)

**專案修改命令**

* [add package](dotnet-add-package.md)
* [add reference](dotnet-add-reference.md)
* [remove package](dotnet-remove-package.md)
* [remove reference](dotnet-remove-reference.md)
* [list reference](dotnet-list-reference.md)

**進階命令**

* [nuget delete](dotnet-nuget-delete.md)
* [nuget locals](dotnet-nuget-locals.md)
* [nuget push](dotnet-nuget-push.md)
* [msbuild](dotnet-msbuild.md)
* [dotnet install script](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**基本命令**

* [new](dotnet-new.md)
* [restore](dotnet-restore.md)
* [build](dotnet-build.md)
* [publish](dotnet-publish.md)
* [run](dotnet-run.md)
* [test](dotnet-test.md)
* [vstest](dotnet-vstest.md)
* [pack](dotnet-pack.md)
* [migrate](dotnet-migrate.md)
* [clean](dotnet-clean.md)
* [sln](dotnet-sln.md)

**專案修改命令**

* [add package](dotnet-add-package.md)
* [add reference](dotnet-add-reference.md)
* [remove package](dotnet-remove-package.md)
* [remove reference](dotnet-remove-reference.md)
* [list reference](dotnet-list-reference.md)

**進階命令**

* [nuget delete](dotnet-nuget-delete.md)
* [nuget locals](dotnet-nuget-locals.md)
* [nuget push](dotnet-nuget-push.md)
* [msbuild](dotnet-msbuild.md)
* [dotnet install script](dotnet-install-script.md)

---

CLI 採用擴充性模型，可讓您為專案指定額外工具。 如需詳細資訊，請參閱 [.NET Core CLI 擴充性模型](extensibility.md)主題。

## <a name="command-structure"></a>命令結構

CLI 命令結構包含[驅動程式 ("dotnet")](#driver)、[命令 (或「指令」)](#command-verb)，以及可能的命令[引數](#arguments)及[選項](#options)。 您可以在大部分的 CLI 作業中看到此模式，例如從名稱為 *my_app* 的目錄執行以下命令，以建立新的主控台應用程式並從命令列執行它：

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```console
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```console
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```


---

### <a name="driver"></a>驅動器

驅動器的名稱是 [dotnet](dotnet.md)，且有兩個責任：執行[相依於架構的應用程式](../deploying/index.md)或執行命令。 唯獨啟動應用程式時會不搭配命令使用 `dotnet`。

若要執行相依於架構的應用程式，請在驅動器之後指定應用程式，例如 `dotnet /path/to/my_app.dll`。 從應用程式的 DLL 所在的資料夾執行該命令時，只要執行 `dotnet my_app.dll` 即可。

當您提供命令給驅動器時，`dotnet.exe` 會啟動 CLI 命令執行程序。 首先，驅動器會決定要使用的 SDK 版本。 如果命令選項中未指定版本，則驅動器會使用可用的最新版本。 若要指定已安裝之最新版本以外的版本，請使用 `--fx-version <VERSION>` 選項 (請參閱 [dotnet 命令](dotnet.md)參考)。 決定 SDK 版本之後，驅動器會執行命令。

### <a name="command-verb"></a>命令 (「動詞」)

命令 (或「動詞」) 只是執行動作的命令。 例如，`dotnet build` 會建置程式碼。 `dotnet publish` 會發行程式碼。 命令是使用 `dotnet {verb}` 慣例實作為主控台應用程式。

### <a name="arguments"></a>引數

您在命令列上傳遞的引數即為叫用命令的引數。 例如當您執行 `dotnet publish my_app.csproj` 時，`my_app.csproj` 引數表示要發佈的專案，並且會傳遞給 `publish` 命令。

### <a name="options"></a>選項

您在命令列上傳遞的選項即為叫用命令的選項。 例如當您執行 `dotnet publish --output /build_output`，`--output` 選項及其值會傳遞給 `publish` 命令。 

## <a name="migration-from-projectjson"></a>從 project.json 移轉

如果您使用 Preview 2 工具來產生 *project.json* 型專案，請參閱 [dotnet migrate](dotnet-migrate.md) 主題，來取得移轉專案至 MSBuild/*.csproj* 以搭配發行工具使用的詳細資訊。 對於在 Preview 2 工具發行之前建立的 .NET Core 專案，請依照[從 DNX 移轉到 .NET Core CLI (project.json)](../migration/from-dnx.md) 中的指導，手動更新專案，然後再使用 `dotnet migrate` 或直接升級您的專案。

## <a name="see-also"></a>另請參閱

 [dotnet/CLI GitHub 存放庫 (英文)](https://github.com/dotnet/cli/)  
 [.NET core 安裝指南 (英文)](https://aka.ms/dotnetcoregs)  
