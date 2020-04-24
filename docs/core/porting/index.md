---
title: 從 .NET Framework 移植到 .NET Core
description: 了解移植程序，並探索可協助將 .NET Framework 移植到 .NET Core 的工具。
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: 499632791e85f4ede87668775ad48407c6988095
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135577"
---
# <a name="overview-of-porting-from-net-framework-to-net-core"></a>從 .NET Framework 移植到 .NET Core 的總覽

您的程式碼可能目前是在您想要移植到 .NET Core 的 .NET Framework 上執行。 本文提供：

* 移植程式的總覽。
* 當您將程式碼移植到 .NET Core 時，您可能會覺得有用的工具清單。

## <a name="overview-of-the-porting-process"></a>移轉程序概觀

從許多專案的 .NET Framework 移植到 .NET Core （或 .NET Standard）相當簡單。 有一些必要的變更，但其中有許多會遵循下面所述的模式。 應用程式模型可在 .NET Core 中使用的專案（例如程式庫、主控台應用程式和桌面應用程式）通常只需要少量變更。 需要新應用程式模型的專案（例如移至 ASP.NET 的 ASP.NET Core）需要更多工作，但許多模式具有可在轉換期間使用的類比。 本檔應協助識別使用者所採用的主要策略，以成功地將其程式碼基底轉換成目標 .NET Standard 或 .NET Core，並可解決兩個層級的轉換：整個方案和特定專案。 如需應用程式模型特定轉換的指示，請參閱底部的連結。

我們建議您在將專案移植到 .NET Core 時，使用下列進程。 每個步驟都會介紹行為變更的可能位置，因此請確定您已充分測試程式庫或應用程式，然後再繼續進行後續步驟。 第一個步驟是讓您的專案準備好切換到 .NET Standard 或 .NET Core。 如果您有單元測試，最好先進行轉換，讓您可以繼續測試您正在處理的產品中的變更。 由於移植到 .NET Core 是您程式碼基底的重大變更，因此強烈建議您移植測試專案，讓您可以在將程式碼移植到時執行測試。 MSTest、xUnit 和 NUnit 全都適用于 .NET Core。

## <a name="getting-started"></a>開始使用

下列工具將在整個程式中使用：

- Visual Studio 2019
- 下載[.net 可攜性分析器](../../standard/analyzers/portability-analyzer.md)
- _選擇性_安裝[dotnet try-convert](https://github.com/dotnet/try-convert)

## <a name="porting-a-solution"></a>移植解決方案

當方案中有多個專案時，移植看起來會比較複雜，因為您必須以特定連續處理專案。 轉換程式應該是最下層的方法，其中與方案中的其他專案沒有相依性的專案會先轉換，並繼續進行整個解決方案。

為了識別應該遷移的訂單專案，您可以使用下列工具：

- [Visual Studio 中](/visualstudio/modeling/create-layer-diagrams-from-your-code)的相依性圖表可以在方案中建立程式碼的導向圖形。
- 執行`msbuild _SolutionPath_ /t:GenerateRestoreGraphFile /p:RestoreGraphOutputPath=graph.dg.json`以產生包含專案參考清單的 json 檔。

## <a name="per-project-steps"></a>每個專案步驟

將您的專案移植到 .NET Core 時，建議您使用下列進程：

1. 使用`packages.config` [Visual Studio 中的轉換工具](/nuget/consume-packages/migrate-packages-config-to-package-reference)，將所有相依性轉換為[PackageReference](/nuget/consume-packages/package-references-in-project-files)格式。

   此步驟牽涉到從舊版`packages.config`格式轉換您的相依性。 `packages.config`無法在 .NET Core 上使用，因此如果您有封裝相依性，就需要進行這項轉換。 它也只需要您直接在專案中使用的相依性，如此可減少您必須管理的相依性，讓後續步驟更容易。

1. 將您的專案檔案轉換成新的 SDK 樣式檔案結構。 您可以為 .NET Core 建立新的專案，並複製原始程式檔，或嘗試使用工具轉換現有的專案檔。

   .NET Core 使用簡化的（和不同的）[專案檔案格式](../tools/csproj.md)，而不是 .NET Framework。 您必須將專案檔轉換成此格式才能繼續。 此專案樣式可讓您同時以 .NET Framework 為目標，此時您仍會想要鎖定目標。

   您可以使用 dotnet 的 [[嘗試轉換](https://github.com/dotnet/try-convert)] 工具，嘗試將一個作業中較小的方案或個別專案移植到 .net Core 專案檔案格式。 `dotnet try-convert`不保證適用于您的所有專案，而且可能會對您所依賴的行為造成細微的變更。 使用它做為自動化可自動化之基本事項的_起點_。 這不是可供遷移專案的保證解決方案，因為相較于舊樣式的專案檔，SDK 樣式專案所使用的目標有許多差異。

1. 將您想要移植到 .NET Framework 目標的所有專案，都設為4.7.2 或更高。

   此步驟可確保當 .NET Core 無法支援特定 API 時，您可以使用 .NET Framework 特定目標的 API 替代方案。

1. 將所有相依性更新為最新版本。 專案可能使用較舊版本的程式庫，但可能沒有 .NET Standard 支援。 不過，較新的版本可以使用簡單的參數來支援它。 如果程式庫中有重大變更，這可能需要變更程式碼。

1. 使用[.net 可攜性分析器](../../standard/analyzers/portability-analyzer.md)來分析您的元件，並查看它們是否可移植到 .net Core。

   .NET 可攜性分析器工具會分析已編譯的元件，並產生報表。 此報告會顯示高階的可攜性摘要，以及您所使用的每個 API 在 NET Core 上無法取得的明細。 使用此工具時，只會提交您要轉換的個別專案，以專注于可能需要的 API 變更。 許多 Api 在 .NET Core 中都具有對等的可用性，您會想要切換到此功能。

   讀取分析器所產生的報表時，重要資訊是實際使用的 Api，而不一定是目標平臺支援的百分比。 許多 Api 在 .NET Standard/核心中都有相同的選項，因此，若要瞭解您的程式庫或應用程式所需的 API，將有助於判斷可攜性的含意。

   在某些情況下，Api 不是相等的，您必須對平臺執行一些編譯器預處理器指示詞`#if NET45`（例如）。 此時，您的專案仍會以 .NET Framework 為目標。 針對上述每個目標案例，建議使用已知的條件，並可視為案例。  例如，.NET Core 中的 AppDomain 支援有限，但在載入和卸載元件的案例中，有一個新的 API 無法在 .NET Core 中使用。 在程式碼中處理這種情況的常見方式如下：

   ```csharp
   #if FEATURE_APPDOMAIN_LOADING
   // Code that uses appdomains
   #elif FEATURE_ASSEMBLY_LOAD_CONTEXT
   // Code that uses assembly load context
   #else
   #error Unsupported platform
   #endif
   ```

1. 將[.NET API 分析器](../../standard/analyzers/api-analyzer.md)安裝到您的專案，以識別在<xref:System.PlatformNotSupportedException>某些平臺上擲回的 api，以及一些其他潛在的相容性問題。

   這項工具與可攜性分析器類似，但不會分析程式碼是否可以在 .NET Core 上建立，而是會分析您是否使用 API，這種方式<xref:System.PlatformNotSupportedException>會在執行時間擲回。 雖然這在您從 .NET Framework 4.7.2 或更高版本中移動時並不常見，但仍可進行檢查。 如需有關在 .NET Core 上擲回例外狀況之 Api 的詳細資訊，請參閱[在 .Net core 上一律會擲回例外狀況的 api](../compatibility/unsupported-apis.md)。

1. 此時，您可以切換為以 .NET Core 為目標（通常適用于應用程式）或 .NET Standard （適用于程式庫）。

   .NET Core 和 .NET Standard 之間的選擇主要取決於專案的執行位置。 如果它是其他應用程式所使用或透過 NuGet 散發的程式庫，則喜好設定通常會以 .NET Standard 為目標。 不過，基於效能或其他原因，可能會有僅適用于 .NET Core 的 Api。如果是這種情況，您應該將 .NET Core 的目標設為可能有 .NET Standard 的組建，而且效能或 funcitonality 也會降低。 藉由以 .NET Standard 為目標，專案將可在新的平臺上執行（例如 WebAssembly）。 如果專案相依于特定的應用程式架構（例如 ASP.NET Core），則目標會受到相依性支援的限制。

   如果 .NET Framework 或 .NET Standard 的條件式編譯器代碼沒有預處理器指示詞，這就像在專案檔中尋找下列簡單：

   ```xml
   <TargetFramework>net472</TargetFramework>
   ```

   並將它切換到所需的架構。 針對 .NET Core 3.1，這會是：

   ```xml
   <TargetFramework>netcoreapp3.1</TargetFramework>
   ```

   不過，如果這是您基於某些原因而想要繼續支援 .NET Framework 特定組建的程式庫，您可以將它取代為下列內容，以將其設為[多目標](../../standard/library-guidance/cross-platform-targeting.md)：

   ```xml
   <TargetFrameworks>net472;netstandard2.0</TargetFrameworks>
   ```

   如果您使用的是 Windows 特定 Api （例如登錄存取），您應該安裝[Windows 相容性套件](./windows-compat-pack.md)。

## <a name="next-steps"></a>後續步驟

>[!div class="nextstepaction"]
>[分析](third-party-deps.md)相依性[套件 NuGet 封裝](../deploying/creating-nuget-packages.md)
>[ASP.NET 以 ASP.NET Core 遷移](/aspnet/core/migration/proper-to-2x)
>
