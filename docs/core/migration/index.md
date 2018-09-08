---
title: 將 .NET Core 移轉至 csproj 格式
description: 將 .NET Core project.json 移轉至 csproj
author: blackdwarf
ms.author: mairaw
ms.date: 07/19/2017
ms.openlocfilehash: da1995ed3b77cb802d1f3d04e6d741809de20927
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44201448"
---
# <a name="migrating-net-core-projects-to-the-csproj-format"></a>將 .NET Core 專案移轉至 .csproj 格式

本文將討論 .NET Core 專案的移轉案例，並將介紹下列三種移轉案例：

1. [從 *project.json* 的有效最新結構描述移轉至 *csproj*](#migration-from-projectjson-to-csproj)
2. [從 DNX 移轉至 csproj](#migration-from-dnx-to-csproj)
3. [從 RC3 和舊版 .NET Core csproj 專案移轉至最終格式](#migration-from-earlier-net-core-csproj-formats-to-rtm-csproj)

## <a name="migration-from-projectjson-to-csproj"></a>從 project.json 移轉至 csproj

您可以使用下列其中一種方法從 *project.json* 移轉至 *.csproj*：

- [Visual Studio 2017](#visual-studio-2017)
- [dotnet migrate 命令列工具](#dotnet-migrate)

這兩種方法使用相同的基礎引擎來移轉專案，因此結果會相同。 在大部分情況下，您只需要使用這兩種方式之一即可將 *project.json* 移轉至 *csproj*，而不需要進一步手動編輯專案檔。 所產生的 *.csproj* 檔案將會以包含目錄的相同名稱命名。

### <a name="visual-studio-2017"></a>Visual Studio 2017

當您開啟 *.xproj* 檔或參考 *.xproj* 檔的方案檔時，[單向升級] 對話方塊會隨即出現。 此對話方塊會顯示要移轉的專案。
如果您開啟方案檔，則會列出方案檔中指定的所有專案。 檢閱要移轉的專案清單，然後選取 [確定]。

![[單向升級] 對話方塊顯示要移轉的專案清單](media/one-way-upgrade.jpg)

Visual Studio 會自動移轉所選擇的專案。 移轉方案時，如果您未選擇所有專案，則會出現相同的對話方塊，請您升級該方案中的其餘專案。 移轉專案之後，您可以用滑鼠右鍵按一下方案總管視窗中的專案，然後選取 [編輯\<專案名稱>.csproj] 來查看及修改其內容。

已移轉的檔案 (*project.json*、*global.json*、*.xproj* 和方案檔) 將會移至「備份」資料夾。 移轉的方案檔將會升級為 Visual Studio 2017，您將無法在舊版 Visual Studio 中開啟該方案檔。
此外，也會儲存並自動開啟名為 *UpgradeLog.htm* 的檔案，其中包含移轉報告。

> [!IMPORTANT]
> Visual Studio 2015 中未提供此新工具，因此您無法使用該版 Visual Studio 來移轉專案。

### <a name="dotnet-migrate"></a>dotnet migrate

在命令列案例中，您可以使用 [`dotnet migrate`](../tools/dotnet-migrate.md) 命令。 它將會根據找到的先後順序，依序移轉專案、方案或一組資料夾。
當您移轉專案時，會移轉專案及其所有相依性。

已移轉的檔案 (*project.json*、*global.json* 和 *.xproj*) 將會移至「備份」資料夾。

> [!NOTE]
> 如果您使用 Visual Studio Code，`dotnet migrate` 命令不會修改 Visual Studio Code 特定的檔案，例如 `tasks.json`。 這些檔案必須以手動方式變更。
> 這也適用於使用 Project Ryder 或是 Visual Studio 以外的任何編輯器或整合式開發環境 (IDE) 的情況。

如需 project.json 和 csproj 格式的比較，請參閱 [project.json 與 csproj 屬性的對應](../tools/project-json-to-csproj.md)。

### <a name="common-issues"></a>常見問題

- 若您收到錯誤：「找不到符合命令 dotnet-migrate 的可執行檔」：

執行 `dotnet --version` 以查看您所使用的版本。 [`dotnet migrate`](../tools/dotnet-migrate.md) 需要 .NET Core CLI RC3 或更高版本。
如果您目前的目錄或父目錄中有 *global.json* 檔案且 `sdk` 版本設定為舊版，則會收到此錯誤。

## <a name="migration-from-dnx-to-csproj"></a>從 DNX 移轉至 csproj

如果您仍使用 DNX 進行 .NET Core 程式開發，則應分兩階段完成您的移轉程序：

1. 使用[現有的 DNX 移轉指引](from-dnx.md)，從 DNX 移轉至啟用 project-json 的 CLI。
2. 遵循上一節中的步驟，從 *project.json* 移轉至 *.csproj*。  

> [!NOTE]
> DNX 已在 .NET Core CLI 的 Preview 1 版期間正式被取代。

## <a name="migration-from-earlier-net-core-csproj-formats-to-rtm-csproj"></a>從舊版 .NET Core csproj 格式移轉至 RTM csproj

每次工具有新的發行前版本，都會變更及改進 .NET Core csproj 格式。 目前沒有工具可將您的專案檔從舊版 csproj 移轉至最新版本，因此您必須手動編輯專案檔。 實際步驟取決於您要移轉的專案檔版本。 以下是根據版本間所發生之變更所要考量的一些指引：

* 從 `<Project>` 項目移除工具版本屬性 (如果存在的話)。
* 從 `<Project>` 項目移除 XML 命名空間 (`xmlns`)。
* 如果不存在，則將 `Sdk` 屬性新增至 `<Project>` 項目，並將它設定為 `Microsoft.NET.Sdk` 或 `Microsoft.NET.Sdk.Web`。 這個屬性會指定專案使用可用的 SDK。 `Microsoft.NET.Sdk.Web` 適用於 Web 應用程式。
* 移除專案頂端和底部的 `<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />` 和 `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` 陳述式。 這些 import 陳述式是由 SDK 所隱含，因此專案中不需要有這些陳述式。
* 如果您的專案中有 `Microsoft.NETCore.App` 或 `NETStandard.Library` `<PackageReference>` 項目，則應該加以移除。 這些套件參考是[由 SDK 所隱含](https://aka.ms/sdkimplicitrefs)。
* 移除 `Microsoft.NET.Sdk` `<PackageReference>` 項目 (如果存在的話)。 SDK 參考是來自 `<Project>` 項目上的 `Sdk` 屬性。
* 移除 [SDK 所隱含](../tools/csproj.md#default-compilation-includes-in-net-core-projects)的 [glob](https://en.wikipedia.org/wiki/Glob_(programming))。 在您的專案中留下這些 Glob 會在建置時造成錯誤，因為編譯項目將會重複。

完成這些步驟之後，您的專案應該會與 RTM .NET Core csproj 格式完全相容。

如需從舊的 csproj 格式移轉至新格式的前後範例，請參閱 .NET 部落格上的 [Updating Visual Studio 2017 RC - .NET Core Tooling improvements](https://blogs.msdn.microsoft.com/dotnet/2016/12/12/updating-visual-studio-2017-rc-net-core-tooling-improvements/) (更新 Visual Studio 2017 RC - .NET Core 工具改進) 文章。

## <a name="see-also"></a>另請參閱

- [移植、移轉及升級 Visual Studio 專案](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)
