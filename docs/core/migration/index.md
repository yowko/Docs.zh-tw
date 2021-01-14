---
title: 從 project.json 進行的 .NET Core 移轉
description: 了解如何使用 project.json 來移轉舊版 .NET Core 專案
ms.date: 07/19/2017
ms.openlocfilehash: 28da1723ed91d169305c2865c5346b8ce6e0b3d1
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189699"
---
# <a name="migrating-net-core-projects-from-projectjson"></a>從 project.json 移轉 .NET Core 專案

本檔涵蓋下列三個 .NET Core 專案的遷移案例：

1. [從 *project.json* 的有效最新結構描述移轉至 *csproj*](#migration-from-projectjson-to-csproj)
2. [從 DNX 移轉至 csproj](#migration-from-dnx-to-csproj)
3. [從 RC3 和舊版 .NET Core csproj 專案移轉至最終格式](#migration-from-earlier-net-core-csproj-formats-to-rtm-csproj)

本檔僅適用于使用 project.json 的舊版 .NET Core 專案。 它並不適用于從 .NET Framework 遷移至 .NET Core。

## <a name="migration-from-projectjson-to-csproj"></a>從 project.json 移轉至 csproj

您可以使用下列其中一種方法從 *project.json* 移轉至 *.csproj*：

- [Visual Studio](#visual-studio)
- [dotnet migrate 命令列工具](#dotnet-migrate)

這兩種方法使用相同的基礎引擎來移轉專案，因此結果會相同。 在大部分的情況下，使用下列兩種方法之一將 *project.js* 遷移至 *.csproj* 是唯一需要的專案，而且不需要進一步手動編輯專案檔。 所產生的 *.csproj* 檔案將會以包含目錄的相同名稱命名。

### <a name="visual-studio"></a>Visual Studio

當您開啟 *xproj* 檔或參考 *xproj* 檔案的方案檔時 Visual Studio 2017 或 Visual Studio 2019 16.2 版及更早版本中，會出現 **單向升級** 對話方塊。 此對話方塊會顯示要移轉的專案。 如果您開啟方案檔，則會列出方案檔中指定的所有專案。 檢閱要移轉的專案清單，然後選取 [確定]。

![[單向升級] 對話方塊顯示要移轉的專案清單](media/one-way-upgrade.jpg)

Visual Studio 會自動遷移選取的專案。 在遷移方案時，如果您未選擇所有專案，則會出現相同的對話方塊，要求您從該方案升級其餘專案。 在遷移專案之後，您可以在 [ **方案總管** ] 視窗中的專案上按一下滑鼠右鍵，然後選取 [ **編輯 \<project name> .csproj**]，以查看並修改其內容。

已遷移 (*project.js* 的檔案、 *global.json*、 *xproj* 和方案檔) 都會移至 *備份* 資料夾。 遷移的解決方案檔會升級為 Visual Studio 2017 或 Visual Studio 2019，您將無法在 Visual Studio 2015 或更早版本中開啟該方案檔。 包含遷移報表的名稱為 *UpgradeLog.htm* 的檔案也會自動儲存並開啟。

> [!IMPORTANT]
> 在 Visual Studio 2019 16.3 版和更新版本中，您無法載入或遷移 *xproj* 檔。 此外，Visual Studio 2015 不提供遷移 *xproj* 檔案的能力。 如果您使用其中一個 Visual Studio 版本，請安裝適當版本的 Visual Studio，或使用接下來所述的命令列遷移工具。

### <a name="dotnet-migrate"></a>dotnet migrate

在命令列案例中，您可以使用 [`dotnet migrate`](../tools/dotnet-migrate.md) 命令。 它會根據找到的專案、方案或一組資料夾，以該順序遷移專案、方案或資料夾。 當您移轉專案時，會移轉專案及其所有相依性。

已遷移 (*project.json*、 *global.json* 和 *. xproj*) 的檔案會移至 *備份* 資料夾。

> [!NOTE]
> 如果您使用 Visual Studio Code，此 `dotnet migrate` 命令不會修改 Visual Studio Code 特定的檔案，例如 *tasks.js*。 這些檔案必須以手動方式變更。
> 如果您要使用編輯器或整合式開發環境 (IDE) 而非 Visual Studio，也是如此。

請參閱 [project.json 與 .csproj 屬性之間的對應](../tools/project-json-to-csproj.md) ，以進行 *project.json* 與 *.csproj* 格式的比較。

如果您收到錯誤：

> 找不到符合命令 dotnet 的可執行檔-遷移

執行 `dotnet --version` 以查看您所使用的版本。 [`dotnet migrate`](../tools/dotnet-migrate.md) 是在 .NET Core SDK 1.0.0 中引進，並在版本3.0.100 中移除。
如果目前或父目錄中的檔案有 *global.js* ，且所 `sdk` 指定的版本不在此範圍內，您將會收到這個錯誤。

## <a name="migration-from-dnx-to-csproj"></a>從 DNX 移轉至 csproj

如果您仍使用 DNX 進行 .NET Core 程式開發，則應分兩階段完成您的移轉程序：

1. 使用[現有的 DNX 移轉指引](from-dnx.md)，從 DNX 移轉至啟用 project-json 的 CLI。
2. 遵循上一節中的步驟，從 *project.json* 移轉至 *.csproj*。

> [!NOTE]
> DNX 已在 .NET Core CLI 的 Preview 1 版期間正式被取代。

## <a name="migration-from-earlier-net-core-csproj-formats-to-rtm-csproj"></a>從舊版 .NET Core csproj 格式移轉至 RTM csproj

每次工具有新的發行前版本，都會變更及改進 .NET Core csproj 格式。 目前沒有工具可將您的專案檔從舊版 csproj 移轉至最新版本，因此您必須手動編輯專案檔。 實際步驟取決於您要移轉的專案檔版本。 以下是根據版本間所發生之變更所要考量的一些指引：

- 從 `<Project>` 項目移除工具版本屬性 (如果存在的話)。
- 從 `<Project>` 項目移除 XML 命名空間 (`xmlns`)。
- 如果不存在，則將 `Sdk` 屬性新增至 `<Project>` 項目，並將它設定為 `Microsoft.NET.Sdk` 或 `Microsoft.NET.Sdk.Web`。 這個屬性會指定專案使用可用的 SDK。 `Microsoft.NET.Sdk.Web` 適用於 Web 應用程式。
- 移除專案頂端和底部的 `<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />` 和 `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` 陳述式。 這些 import 陳述式是由 SDK 所隱含，因此專案中不需要有這些陳述式。
- 如果您的 `Microsoft.NETCore.App` 專案中有或專案 `NETStandard.Library` `<PackageReference>` ，則應該移除它們。 這些套件參考是[由 SDK 所隱含](../project-sdk/overview.md)。
- 移除專案 `Microsoft.NET.Sdk` `<PackageReference>` （如果有的話）。 SDK 參考是來自 `<Project>` 項目上的 `Sdk` 屬性。
- 移除[SDK 所隱含](../project-sdk/overview.md#default-includes-and-excludes)的[glob](https://en.wikipedia.org/wiki/Glob_(programming)) 。 在您的專案中留下這些 Glob 會在建置時造成錯誤，因為編譯項目將會重複。

完成這些步驟之後，您的專案應該會與 RTM .NET Core csproj 格式完全相容。

如需從舊的 csproj 格式移轉至新格式的前後範例，請參閱 .NET 部落格上的 [Updating Visual Studio 2017 RC - .NET Core Tooling improvements](https://devblogs.microsoft.com/dotnet/updating-visual-studio-2017-rc-net-core-tooling-improvements/) (更新 Visual Studio 2017 RC - .NET Core 工具改進) 文章。

## <a name="see-also"></a>另請參閱

- [移植、遷移及升級 Visual Studio 專案](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)
