---
title: 移植到 .NET Core - 分析協力廠商相依性
description: 了解如何分析協力廠商相依性，以將您的專案從 .NET Framework 移植到 .NET Core。
author: cartermp
ms.author: mairaw
ms.date: 02/15/2018
ms.openlocfilehash: 06d8d36d8369680c54af4d16513b2b871b57079c
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46000995"
---
# <a name="analyze-your-third-party-dependencies"></a>分析協力廠商相依性

如果您想要將程式碼移植到 .NET Core 或 .NET Standard，移植程序的第一個步驟是了解您的協力廠商相依性。 協力廠商相依性是您在專案中參考的 [NuGet 套件](#analyze-referenced-nuget-packages-on-your-project)或 [DLL](#analyze-dependencies-that-arent-nuget-packages)。 評估每個相依性，並針對與 .NET Core 不相容的相依性開發應變計劃。 本文示範如何判斷相依性是否與 .NET Core 相容。

## <a name="analyze-referenced-nuget-packages-in-your-project"></a>分析專案中參考的 NuGet 套件

如果您在專案中參考 NuGet 套件，您需要確認其是否與 .NET Core 相容。
有兩種方法可達成該目標：

* [使用 NuGet 套件總管應用程式](#analyze-nuget-packages-using-nuget-package-explorer) (最可靠的方法)。
* [使用 nuget.org 網站](#analyze-nuget-packages-using-nugetorg)。

分析套件之後，如果這些套件與 .NET Core 不相容並只以 .NET Framework 為目標，您可以檢查 [.NET Framework 相容性模式](#net-framework-compatibility-mode)是否可以協助您的移植程序。

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a>使用 NuGet 套件總管分析 NuGet 套件

NuGet 套件本身是一組包含平台特定組件的資料夾。 因此，您需要檢查套件中是否有包含相容組件的資料夾。

使用 [NuGet 套件總管](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer)工具是檢查 NuGet 套件資料夾的最簡單方式。 安裝後，您可以使用下列步驟來查看資料夾名稱：

1. 開啟 NuGet 套件總管。
2. 按一下 [Open package from online feed] (從線上摘要開啟套件)。
3. 搜尋封裝的名稱。
4. 從搜尋結果選取套件名稱，然後按一下 [開啟]。
5. 展開右邊的 *lib* 資料夾，並查看資料夾名稱。

尋找具有下列任何名稱的資料夾：

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netstandard2.0
netcoreapp1.0
netcoreapp1.1
netcoreapp2.0
netcoreapp2.1
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

這些值是對應至 [.NET Standard](../../standard/net-standard.md)、.NET Core 以及與 .NET Core 相容之傳統可攜式類別庫 (PCL) 設定檔版本的[目標 Framework Moniker (TFM)](../../standard/frameworks.md)。

> [!IMPORTANT]
> 查看套件支援的 TFM 時，請注意，`netcoreapp*` 雖然相容，但只適用於 .NET Core 專案而不適用於 .NET Standard 專案。
> 其他 .NET Core 應用程式只可取用以 `netcoreapp*` (而不是 `netstandard*`) 為目標的程式庫。

還有在 .NET Core 發行前版本中使用的一些舊版 TFM 也可能是相容的：

```
dnxcore50
dotnet5.0
dotnet5.1
dotnet5.2
dotnet5.3
dotnet5.4
dotnet5.5
```

雖然這些 TFM 可能適合您的程式碼使用，但不保證相容性。 有這些 TFM 的封裝過去是使用發行前版本的 .NET Core 封裝建置的。 記下使用這些 TFM 的套件何時 (或是否) 更新為以 .NET Standard 為基礎。

> [!NOTE]
> 若要使用以傳統 PCL 或發行前版本 .NET Core 目標為目標的套件，您必須在專案檔案中使用 `PackageTargetFallback` MSBuild 項目。
> 如需此 MSBuild 項目的詳細資訊，請參閱 [`PackageTargetFallback`](../tools/csproj.md#packagetargetfallback)。

### <a name="analyze-nuget-packages-using-nugetorg"></a>使用 nuget.org 分析 NuGet 套件

或者，您可以在 [nuget.org](https://www.nuget.org/) 上，於套件頁面的 [相依性] 區段下，查看每個套件支援的 TFM。

雖然使用網站是確認相容性的較簡單方法，但網站上不會提供所有套件的**相依性**資訊。

### <a name="net-framework-compatibility-mode"></a>.NET Framework 相容性模式

分析 NuGet 套件之後，您可能會發現這些套件只會以 .NET Framework 為目標，如同大多數 NuGet 套件一樣。

從 .NET Standard 2.0 開始，引進了 .NET Framework 相容性模式。 此相容性模式可讓 .NET Standard 和 .NET Core 專案參考 .NET Framework 程式庫。 並非所有專案都適合參考 .NET Framework 程式庫 (例如，如果程式庫使用 Windows Presentation Foundation (WPF) API)，但它確實會解決許多移植案例。

當您在專案中參考以 .NET Framework 為目標的 NuGet 套件時 (例如 [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections))，您會收到類似下列範例的套件後援警告 ([NU1701](/nuget/reference/errors-and-warnings#nu1701))：

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

當您新增套件及每次建置時，都會顯示該警告，以確定您會隨專案測試該套件。 如果您的專案如預期般運作，您可以在 Visual Studio 中編輯套件屬性，或在您慣用的程式碼編輯器中以手動方式編輯專案檔，來隱藏該警告。

若要透過編輯專案檔來隱藏警告，請尋找您要隱藏警告之套件的 `PackageReference` 項目，然後新增 `NoWarn` 屬性。 `NoWarn` 屬性接受所有警告識別碼的逗號分隔清單。 下列範例示範如何透過手動編輯專案檔，來隱藏 `Huitian.PowerCollections` 套件的 `NU1701` 警告：

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

如需如何在 Visual Studio 中隱藏編譯器警告的詳細資訊，請參閱[隱藏 NuGet 套件的警告](/visualstudio/ide/how-to-suppress-compiler-warnings#suppressing-warnings-for-nuget-packages)。

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>NuGet 封裝相依性在 .NET Core 上不執行時該怎麼辦

如果您依賴的 NuGet 套件在 .NET Core 上不執行，您可以做幾件事：

1. 如果專案是開放原始碼並裝載在 GitHub 等位置，您可以直接連絡開發人員。
2. 您可以在 [nuget.org](https://www.nuget.org/) 上直接連絡作者。搜尋套件，然後按一下套件頁面左邊的 [Contact Owners] (連絡擁有者)。
3. 您可以搜尋在 .NET Core 上執行並與您所用套件達成相同工作的其他套件。
4. 您可以嘗試自行撰寫封裝執行工作的程式碼。
5. 您可以變更應用程式的功能，消除封裝的相依性，至少等到有可用的相容版本封裝。

請記住，開放原始碼專案維護者和 NuGet 套件發行者通常是志工。 他們因關心特定領域而參與並免費提供服務，而且通常會有不同的日間工作。 因此連絡他們以取得 .NET Core 支援時請留意。

如果上述任何方法都無法解決您的問題，稍後可能必須移植到 .NET Core。

.NET 小組希望知道哪些程式庫最重要，是 .NET Core 要支援的對象。 您可以傳送電子郵件至 dotnet@microsoft.com 討論您想使用的程式庫。

## <a name="analyze-dependencies-that-arent-nuget-packages"></a>分析不是 NuGet 套件的相依性

您可能有不是 NuGet 套件的相依性，例如檔案系統中的 DLL。 判斷該相依性可攜性的唯一方法，是執行 [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport) 工具。 此工具可以分析以 .NET Framework 為目標的組件，並識別不可移植到其他 .NET 平台 (例如 .NET Core) 的 API。 您可以將此工具當作主控台應用程式或 [Visual Studio 延伸模組](../../standard/analyzers/portability-analyzer.md)來執行。

## <a name="next-steps"></a>後續步驟

如要移轉程式庫，請參閱 [Porting to .NET Core - Libraries](libraries.md) (移轉至 .NET Core - 程式庫)。
