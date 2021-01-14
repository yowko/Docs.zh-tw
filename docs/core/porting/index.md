---
title: 從 .NET Framework 移植到 .NET Core
description: 了解移植程序，並探索可協助將 .NET Framework 移植到 .NET Core 的工具。
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: 247e709ac6898a6a89318626e3aa9a2a8e239a9a
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189931"
---
# <a name="overview-of-porting-from-net-framework-to-net-core"></a>從 .NET Framework 移植到 .NET Core 的總覽

您的程式碼目前可能是在您想要移植到 .NET Core 的 .NET Framework 上執行。 本文提供：

* 移植流程的總覽。
* 當您將程式碼移植到 .NET Core 時，可能會覺得有用的工具清單。

## <a name="overview-of-the-porting-process"></a>移轉程序概觀

從許多專案的 .NET Framework 移植到 .NET Core (或 .NET Standard) 相當簡單。 有一些需要的變更，但其中有許多變更都遵循如下所述的模式。 應用程式模型可在 .NET Core (（例如程式庫、主控台應用) 程式和桌面應用程式）中使用的專案，通常不需要太多變更。 需要新應用程式模型的專案，例如移至 ASP.NET 的 ASP.NET Core，需要更多工作，但許多模式都具有可在轉換期間使用的類比。 本檔應有助於找出使用者已運用的主要策略，以順利將其程式碼基底轉換成目標 .NET Standard 或 .NET Core，並且將在兩個層級解決轉換：整個方案和專案專屬。 請參閱底部的連結，以取得應用程式模型特定轉換的指示。

建議您在將專案移植到 .NET Core 時使用下列程式。 上述每個步驟都引進了可能的行為變更位置，因此請確定您已充分測試您的程式庫或應用程式，再繼續進行後續步驟。 第一個步驟是讓您的專案準備好切換至 .NET Standard 或 .NET Core。 如果您有單元測試，最好先進行轉換，讓您可以繼續在您正在處理的產品中測試變更。 因為移植到 .NET Core 是程式碼基底的重大變更，所以強烈建議您移植測試專案，讓您可以在移植程式碼時執行測試。 MSTest、xUnit 和 NUnit 全都適用于 .NET Core。

## <a name="getting-started"></a>開始使用

整個過程中將會使用下列工具：

- Visual Studio 2019
- 下載 [.net 可攜性分析器](../../standard/analyzers/portability-analyzer.md)
- _選擇性_ 安裝 [dotnet try-convert](https://github.com/dotnet/try-convert)

## <a name="porting-a-solution"></a>移植方案

當方案中有多個專案時，移植起來可能更複雜，因為您必須以特定連續處理專案。 轉換程式應該是最新的方法，在此方法中，與方案中其他專案沒有相依性的專案會先進行轉換，然後繼續整個方案。

您可以使用下列工具，找出應遷移的訂單專案：

- [Visual Studio 中](/visualstudio/modeling/create-layer-diagrams-from-your-code) 的相依性圖表可以在方案中建立程式碼的有向圖形。
- 執行 `msbuild _SolutionPath_ /t:GenerateRestoreGraphFile /p:RestoreGraphOutputPath=graph.dg.json` 以產生 json 檔，其中包含專案參考清單。
- 使用參數執行 [.net 可攜性分析器](../../standard/analyzers/portability-analyzer.md) `-r DGML` ，以取出元件的相依性圖表。 如需詳細資訊，請參閱[這裡](../../standard/analyzers/portability-analyzer.md#solution-wide-view)。

擁有相依性資訊之後，您就可以使用該資訊從分葉節點啟動，並在下一節中使用這些步驟來完成相依性樹狀結構的工作。

## <a name="per-project-steps"></a>每個專案的步驟

建議您在將專案移植到 .NET Core 時使用下列程式：

1. `packages.config`使用[Visual Studio 中的轉換工具](/nuget/consume-packages/migrate-packages-config-to-package-reference)，將您所有的相依性轉換成[PackageReference](/nuget/consume-packages/package-references-in-project-files)格式。

   此步驟牽涉到從舊版格式轉換您的相依性 `packages.config` 。 `packages.config` 不適用於 .NET Core，所以如果您有套件相依性，就需要進行這項轉換。 它也只需要您直接在專案中使用的相依性，讓您可以藉由減少必須管理的相依性數目來更輕鬆地進行後續步驟。

1. 將您的專案檔轉換成新的 SDK 樣式檔案結構。 您可以建立適用于 .NET Core 的新專案並複製原始程式檔，或嘗試使用工具來轉換現有的專案檔。

   .NET Core 使用簡化的 (和不同的) [專案檔案格式](../project-sdk/overview.md) ，而非 .NET Framework。 您必須將專案檔案轉換成此格式才能繼續。 此專案樣式也可讓您以 .NET Framework 為目標，此時您仍會想要鎖定目標。

   您可以使用 dotnet 的 [ [嘗試轉換](https://github.com/dotnet/try-convert) ] 工具，嘗試將一項作業中較小的解決方案或個別專案移植到 .net Core 專案檔案格式。 `dotnet try-convert` 不保證適用于您所有的專案，而且可能會導致您相依的行為有細微的變更。 您可以使用它做為自動化可自動化之基本專案的 _起點_ 。 這不是遷移專案的保證解決方案，因為與舊樣式專案檔相較之下，SDK 樣式專案所使用的目標有許多差異。

1. 將您想要移植的所有專案重定為目標 .NET Framework 4.7.2 或更高。

   此步驟可確保當 .NET Core 無法支援特定 API 時，您可以使用 .NET Framework 特定目標的 API 替代方案。

1. 將所有相依性更新為最新版本。 專案可能使用較舊版本的程式庫，這些程式庫可能沒有 .NET Standard 支援。 不過，較新的版本可以使用簡單的參數來支援它。 如果程式庫中有重大變更，則可能需要變更程式碼。

1. 使用 [.net 可攜性分析器](../../standard/analyzers/portability-analyzer.md) 來分析您的元件，並查看它們是否可移植到 .net Core。

   .NET 可攜性分析器工具會分析已編譯的元件，並產生報表。 這份報表會顯示高階可攜性摘要，以及您所使用的每個 API 的細目（無法在 .NET Core 上取得）。 使用此工具時，請只提交您要轉換的個別專案，以專注于可能需要的 API 變更。 許多 Api 在 .NET Core 中都有對等的可用性，而您會想要切換至這些 Api。

   讀取分析器所產生的報表時，重要的資訊是正在使用的實際 Api，而不一定是對目標平臺的支援百分比。 許多 Api 在 .NET Standard/核心中都有對等的選項，因此瞭解您的程式庫或應用程式需要 API 的案例將有助於判斷可攜性的含意。

   在某些情況下，Api 不是相等的，您必須進行一些編譯器預處理器指示詞 (也就是 `#if NET45`) 特殊案例的平臺。 至此，您的專案仍會以 .NET Framework 為目標。 針對上述每個案例，建議使用可視為案例的知名條件。  例如，.NET Core 中的 AppDomain 支援有限，但在載入和卸載元件的案例中，有一個新的 API 無法在 .NET Core 中使用。 在程式碼中處理此問題的常見方式如下：

   ```csharp
   #if FEATURE_APPDOMAIN_LOADING
   // Code that uses appdomains
   #elif FEATURE_ASSEMBLY_LOAD_CONTEXT
   // Code that uses assembly load context
   #else
   #error Unsupported platform
   #endif
   ```

1. 在您的專案中安裝 [.NET API 分析器](../../standard/analyzers/api-analyzer.md) ，以識別 <xref:System.PlatformNotSupportedException> 在某些平臺上擲回的 api，以及一些其他潛在的相容性問題。

   這項工具與可攜性分析器類似，但不是分析程式碼是否可在 .NET Core 上建立，而是會分析您是否使用 API，其會在 <xref:System.PlatformNotSupportedException> 執行時間擲回。 雖然這在您要從 .NET Framework 4.7.2 或更高版本中移動時並不常見，但最好是檢查。 如需在 .NET Core 上擲回例外狀況之 Api 的詳細資訊，請參閱 [在 .Net core 上一律會擲回例外狀況的 api](../compatibility/unsupported-apis.md)。

1. 至此，您可以切換為以 .NET Core 為目標， (通常適用于應用程式) 或 .NET Standard (適用于程式庫) 。

   在 .NET Core 和 .NET Standard 之間的選擇，主要取決於將執行專案的位置。 如果是其他應用程式將取用或透過 NuGet 散發的程式庫，則喜好設定通常會以 .NET Standard 為目標。 不過，基於效能或其他原因，可能會有僅適用于 .NET Core 的 Api;如果是這種情況，則應該將 .NET Core 設為目標，可能會有 .NET Standard 的組建，而且效能或功能也會降低。 藉由將 .NET Standard 設為目標，專案就可以在新的平臺上執行， (例如 WebAssembly) 。 如果專案相依于特定的應用程式架構 (例如 ASP.NET Core) ，則目標將受到相依性支援的限制。

   若 .NET Framework 或 .NET Standard 中沒有適用于條件式編譯器代碼的預處理器指示詞，就像在專案檔中尋找下列專案一樣簡單：

   ```xml
   <TargetFramework>net472</TargetFramework>
   ```

   並將它切換到所需的架構。 針對 .NET Core 3.1，這會是：

   ```xml
   <TargetFramework>netcoreapp3.1</TargetFramework>
   ```

   但是，如果這是您想要繼續支援 .NET Framework 特定組建的程式庫，您可以將它取代為下列內容，以 [多目標](../../standard/library-guidance/cross-platform-targeting.md) ：

   ```xml
   <TargetFrameworks>net472;netstandard2.0</TargetFrameworks>
   ```

   如果您使用 Windows 特定 Api (例如登錄存取) ，請安裝 [Windows 相容性套件](./windows-compat-pack.md)。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [分析相依性](third-party-deps.md) 
> [封裝 NuGet 套件](../deploying/creating-nuget-packages.md)

## <a name="see-also"></a>另請參閱

- [ASP.NET 至 ASP.NET Core 遷移](/aspnet/core/migration/proper-to-2x)
- [將 WPF 應用程式遷移至 .NET Core](/dotnet/desktop/wpf/migration/convert-project-from-net-framework)
- [將 .NET Framework Windows Forms 應用程式遷移至 .NET](/dotnet/desktop/winforms/migration/?view=netdesktop-5.0&preserve-view=true)
