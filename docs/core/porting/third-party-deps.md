---
title: 分析相依性以將程式碼移植到 .NET Core
description: 了解如何分析外部相依性，以將您的專案從 .NET Framework 移植到 .NET Core。
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: 2aa09e551a99358d3a6961fafcfc0aa8dbd976b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398962"
---
# <a name="analyze-your-dependencies-to-port-code-to-net-core"></a>分析您的相依性以將程式碼移植到 .NET Core

要將程式碼移植到 .NET Core 或 .NET Standard，您必須了解您的相依性。 外部依賴項是您在專案中引用的`.dll`NuGet 包或檔，但您自己不構建。

## <a name="migrate-your-nuget-packages-to-packagereference"></a>將 NuGet 包遷移到`PackageReference`

.NET Core 使用 [PackageReference](/nuget/consume-packages/package-references-in-project-files) 來指定套件相依性。 如果您使用[包.config](/nuget/reference/packages-config)在專案中指定包，請將其轉換為`PackageReference`格式，因為`packages.config`.NET Core 中不受支援。

要瞭解如何遷移，請參閱[從包遷移.config 到包參考](/nuget/reference/migrate-packages-config-to-package-reference)"一文。

## <a name="upgrade-your-nuget-packages"></a>升級您的 NuGet 套裝軟體

將專案遷移到`PackageReference`格式後，請驗證封裝是否與 .NET Core 相容。

首先，將包升級到最新版本。 這可以通過 Visual Studio 中的 NuGet 包管理器 UI 來完成。 包依賴項的較新版本很可能已與 .NET Core 相容。

## <a name="analyze-your-package-dependencies"></a>分析包依賴項

如果您尚未驗證已轉換和升級的包依賴項是否在 .NET Core 上工作，則可以通過幾種方式實現這一點：

### <a name="analyze-nuget-packages-using-nugetorg"></a>使用 nuget.org 分析 NuGet 套件

您可以在包頁的 **"依賴關係"** 部分下看到每個包在[nuget.org](https://www.nuget.org/)上支援的目標框架程式 （TfMs）。

儘管使用網站是驗證相容性的更簡單的方法，但網站上並非所有包都提供**依賴項**資訊。

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a>使用 NuGet 套件總管分析 NuGet 套件

NuGet 套件本身是一組包含平台特定組件的資料夾。 檢查包內是否有包含相容程式集的資料夾。

檢查 NuGet 包資料夾的最簡單方法是使用[NuGet 包資源管理器](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer)工具。 安裝後，您可以使用下列步驟來查看資料夾名稱：

1. 開啟 NuGet 套件總管。
2. 按一下 [Open package from online feed] (從線上摘要開啟套件)****。
3. 搜尋封裝的名稱。
4. 從搜尋結果選取套件名稱，然後按一下 [開啟]****。
5. 展開右邊的 *lib* 資料夾，並查看資料夾名稱。

使用以下模式之一查找名稱的資料夾：`netstandardX.Y`或`netcoreappX.Y`。

這些值是對應至 [.NET Standard](../../standard/net-standard.md)、.NET Core 以及與 .NET Core 相容之傳統可攜式類別庫 (PCL) 設定檔版本的[目標 Framework Moniker (TFM)](../../standard/frameworks.md)。

> [!IMPORTANT]
> 查看套件支援的 TFM 時，請注意，`netcoreapp*` 雖然相容，但只適用於 .NET Core 專案而不適用於 .NET Standard 專案。
> 其他 .NET Core 應用程式只可取用以 `netcoreapp*` (而不是 `netstandard*`) 為目標的程式庫。

## <a name="net-framework-compatibility-mode"></a>.NET Framework 相容性模式

分析 NuGet 包後，您可能會發現它們僅針對 .NET 框架。

從 .NET Standard 2.0 開始，引進了 .NET Framework 相容性模式。 此相容性模式可讓 .NET Standard 和 .NET Core 專案參考 .NET Framework 程式庫。 並非所有專案都適合參考 .NET Framework 程式庫 (例如，如果程式庫使用 Windows Presentation Foundation (WPF) API)，但它確實會解決許多移植案例。

當您在專案中引用針對 .NET 框架的 NuGet 包時，例如[Huitian.PowerCollections，](https://www.nuget.org/packages/Huitian.PowerCollections)您會收到類似于以下示例的包回退警告[（NU1701）：](/nuget/reference/errors-and-warnings/nu1701)

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

當您新增套件及每次建置時，都會顯示該警告，以確定您會隨專案測試該套件。 如果專案按預期工作，則可以通過在 Visual Studio 中編輯包屬性或在喜愛的代碼編輯器中手動編輯專案檔案來禁止該警告。

若要透過編輯專案檔來隱藏警告，請尋找您要隱藏警告之套件的 `PackageReference` 項目，然後新增 `NoWarn` 屬性。 `NoWarn` 屬性接受所有警告識別碼的逗號分隔清單。 下列範例示範如何透過手動編輯專案檔，來隱藏 `Huitian.PowerCollections` 套件的 `NU1701` 警告：

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

如需如何在 Visual Studio 中隱藏編譯器警告的詳細資訊，請參閱[隱藏 NuGet 套件的警告](/visualstudio/ide/how-to-suppress-compiler-warnings#suppress-warnings-for-nuget-packages)。

## <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>NuGet 封裝相依性在 .NET Core 上不執行時該怎麼辦

如果您依賴的 NuGet 套件在 .NET Core 上不執行，您可以做幾件事：

- 如果專案是開放原始碼並裝載在 GitHub 等位置，您可以直接連絡開發人員。
- 您可以直接在[nuget.org](https://www.nuget.org/)上聯繫作者。搜索包，然後按一下包頁面左側的 **"聯繫擁有者**"。
- 您可以搜尋在 .NET Core 上執行並與您所用套件達成相同工作的其他套件。
- 您可以嘗試自行撰寫封裝執行工作的程式碼。
- 您可以變更應用程式的功能，消除封裝的相依性，至少等到有可用的相容版本封裝。

請記住，開放原始碼專案維護者和 NuGet 套件發行者通常是志工。 他們因關心特定領域而參與並免費提供服務，而且通常會有不同的日間工作。 聯繫他們要求 .NET 核心支援時，請注意這一點。

如果無法通過這些選項解決您的問題，則可能必須稍後移植到 .NET Core。

.NET 小組希望知道哪些程式庫最重要，是 .NET Core 要支援的對象。 您可以傳送電子郵件至 dotnet@microsoft.com 討論您想使用的程式庫。

## <a name="analyze-dependencies-that-arent-nuget-packages"></a>分析不是 NuGet 套件的相依性

您可能有不是 NuGet 套件的相依性，例如檔案系統中的 DLL。 判斷該相依性可攜性的唯一方法，是執行 [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport) 工具。 該工具分析以 .NET 框架為目標的程式集，並標識無法移植到其他 .NET 平臺（如 .NET Core）的 API。 您可以將此工具當作主控台應用程式或 [Visual Studio 延伸模組](../../standard/analyzers/portability-analyzer.md)來執行。

## <a name="next-steps"></a>後續步驟

>[!div class="nextstepaction"]
>[移植程式庫](libraries.md)
