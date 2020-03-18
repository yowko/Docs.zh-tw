---
title: 從 project.json 進行的 .NET Core 移轉
description: 了解如何使用 project.json 來移轉舊版 .NET Core 專案
ms.date: 07/19/2017
ms.openlocfilehash: 8a9dc05c82fd5476a70ee36a294a287abbfb68c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "77450683"
---
# <a name="migrating-net-core-projects-from-projectjson"></a>從 project.json 移轉 .NET Core 專案

本文檔介紹 .NET Core 專案的以下三個遷移方案：

1. [從 *project.json* 的有效最新結構描述移轉至 *csproj*](#migration-from-projectjson-to-csproj)
2. [從 DNX 移轉至 csproj](#migration-from-dnx-to-csproj)
3. [從 RC3 和舊版 .NET Core csproj 專案移轉至最終格式](#migration-from-earlier-net-core-csproj-formats-to-rtm-csproj)

本文檔僅適用于使用 project.json 的舊 .NET Core 專案。 它不適用於從 .NET 框架遷移到 .NET 核心。

## <a name="migration-from-projectjson-to-csproj"></a>從 project.json 移轉至 csproj

您可以使用下列其中一種方法從 *project.json* 移轉至 *.csproj*：

- [Visualstudio](#visual-studio)
- [dotnet migrate 命令列工具](#dotnet-migrate)

這兩種方法使用相同的基礎引擎來移轉專案，因此結果會相同。 在大多數情況下，使用這兩種方法之一將*project.json*遷移到*csproj*是唯一需要的方法，並且無需進一步手動編輯專案檔案。 所產生的 *.csproj* 檔案將會以包含目錄的相同名稱命名。

### <a name="visual-studio"></a>Visual Studio

當您在 Visual Studio 2017 或 Visual Studio 2019 版本 16.2 和更早版本中打開引用 *.xproj*檔的 *.xproj*檔時，將顯示**單向升級**對話方塊。 此對話方塊會顯示要移轉的專案。 如果打開解決方案檔，將列出解決方案檔中指定的所有專案。 檢閱要移轉的專案清單，然後選取 [確定]****。

![[單向升級] 對話方塊顯示要移轉的專案清單](media/one-way-upgrade.jpg)

視覺化工作室會自動遷移所選項目。 遷移解決方案時，如果未選擇所有專案，則會出現相同的對話方塊，要求您從該解決方案升級其餘專案。 移轉專案之後，您可以用滑鼠右鍵按一下方案總管**** 視窗中的專案，然後選取 [編輯\<專案名稱>.csproj]**** 來查看及修改其內容。

*Backup*已遷移的檔（project.json、global.json、.xproj 和解決方案檔）將移動到備份檔案夾。* * *global.json* *.xproj* 遷移的解決方案檔升級到 Visual Studio 2017 或 Visual Studio 2019，您將無法在 Visual Studio 2015 或早期版本中打開該解決方案檔。 包含遷移報告名為*UpgradeLog.htm*的檔也會自動儲存和打開。

> [!IMPORTANT]
> 在 Visual Studio 2019 版本 16.3 及更高版本中，您不能載入或遷移 *.xproj*檔。 此外，Visual Studio 2015 不提供遷移 *.xproj*檔的能力。 如果您使用的是這些 Visual Studio 版本之一，請安裝合適的 Visual Studio 版本，或者使用接下來介紹的命令列遷移工具。

### <a name="dotnet-migrate"></a>dotnet migrate

在命令列方案中，可以使用 命令[`dotnet migrate`](../tools/dotnet-migrate.md)。 它按此順序遷移專案、解決方案或一組資料夾，具體取決於找到哪些資料夾。 當您移轉專案時，會移轉專案及其所有相依性。

已遷移的檔 *（project.json、global.json*和*global.json* *.xproj）* 將移動到*備份*資料夾。

> [!NOTE]
> 如果使用 Visual Studio 代碼，該`dotnet migrate`命令不會修改特定于 Visual Studio 代碼的檔，如*任務.* 這些檔案必須以手動方式變更。
> 如果您使用的是 Visual Studio 以外的編輯器或整合式開發環境 （IDE），則也是如此。

有關*專案.json*和 *.csproj*格式的比較，請參閱[project.json 和 csproj 屬性之間的映射](../tools/project-json-to-csproj.md)。

如果您收到錯誤：

> 找不到可執行檔匹配命令點網遷移

執行 `dotnet --version` 以查看您所使用的版本。 [`dotnet migrate`](../tools/dotnet-migrate.md)在 .NET Core SDK 1.0.0 中引入，並在版本 3.0.100 中刪除。
如果當前或父目錄中有一個*global.json*檔，並且它指定的版本超出此範圍，`sdk`則將出現此錯誤。

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
- 如果專案中有`Microsoft.NETCore.App`或`NETStandard.Library``<PackageReference>`專案，則應刪除它們。 這些套件參考是[由 SDK 所隱含](https://aka.ms/sdkimplicitrefs)。
- 如果元素`Microsoft.NET.Sdk``<PackageReference>`存在，請將其刪除。 SDK 參考是來自 `<Project>` 項目上的 `Sdk` 屬性。
- 刪除[SDK 隱含的](../project-sdk/overview.md#default-compilation-includes) [globs。](https://en.wikipedia.org/wiki/Glob_(programming)) 在您的專案中留下這些 Glob 會在建置時造成錯誤，因為編譯項目將會重複。

完成這些步驟之後，您的專案應該會與 RTM .NET Core csproj 格式完全相容。

如需從舊的 csproj 格式移轉至新格式的前後範例，請參閱 .NET 部落格上的 [Updating Visual Studio 2017 RC - .NET Core Tooling improvements](https://devblogs.microsoft.com/dotnet/updating-visual-studio-2017-rc-net-core-tooling-improvements/) (更新 Visual Studio 2017 RC - .NET Core 工具改進) 文章。

## <a name="see-also"></a>另請參閱

- [移植、遷移和升級視覺化工作室專案](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)
