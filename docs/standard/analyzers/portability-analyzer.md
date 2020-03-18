---
title: .NET Portability Analyzer - .NET
description: 了解如何使用.NET Portability Analyzer 工具來評估程式碼移植到不同 .NET 實作之間的可行性，包括 .NET Core、.NET Standard、UWP 和 Xamarin。
ms.date: 09/13/2019
ms.technology: dotnet-standard
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.openlocfilehash: e0a5c791926b36fe5a35c5446471c3dcdb75cd7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "72774382"
---
# <a name="the-net-portability-analyzer"></a>.NET Portability Analyzer

要讓您的程式庫支援多平台？ 想要瞭解要使 .NET 框架應用程式在 .NET Core 上運行需要多少工作？ [.NET 可攜性分析器](https://github.com/microsoft/dotnet-apiport)是一種工具，用於分析程式集，並提供有關 .NET API 的詳細報告，這些 API 缺少應用程式或庫在指定的目標 .NET 平臺上可移植。 可攜性分析器作為視覺化[Studio 擴展提供](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)，它分析每個專案的一個程式集，並作為[ApiPort 主控台應用程式](https://aka.ms/apiportdownload)，按指定的檔或目錄分析程式集。

將專案轉換為目標新平臺（如 .NET Core）後，可以使用基於 Roslyn 的 API[分析器工具](api-analyzer.md)來標識引發<xref:System.PlatformNotSupportedException>異常和其他相容性問題的 API。

## <a name="common-targets"></a>常見目標

- [.NET core](../../core/index.md)︰具有模組化的設計，採用並存，並且適合在跨平台的情況下使用。 並存可讓您採用新的 .NET Core 版本，而不會中斷其他應用程式。 如果您的目標，是要將應用程式移植到 .NET Core 來支援跨平台，這是建議的目標。
- .[NET 標準](../../standard/net-standard.md)： 包括所有 .NET 實現上可用的 .NET 標準 API。 如果您的目標，是讓程式庫在所有支援 .NET 的平台上執行，這是建議的目標。
- [ASP.NET核心](/aspnet/core)：建立在 .NET 核心之上的現代 Web 框架。 如果您的目標，是要將 Web 應用程式移植到 .NET Core 來支援多平台，這是建議的目標。
- .NET 核心 +[平臺擴展](../../core/porting/windows-compat-pack.md)： 除了 Windows 相容性包之外，還包括 .NET 核心 API，它提供了許多 .NET 框架可用的技術。 如需將您的應用程式從 .NET Framework 移植到 Windows 上的 .NET Core，這是建議的目標。
- .NET 標準 +[平臺擴展](../../core/porting/windows-compat-pack.md)：除了 Windows 相容性包外，還包括 .NET 標準 API，該包提供了許多 .NET 框架可用的技術。 如需將您的程式庫從 .NET Framework 移植到 Windows 上的 .NET Core，這是建議的目標。

## <a name="how-to-use-the-net-portability-analyzer"></a>如何使用 .NET 可攜性分析器

若要開始在 Visual Studio 中使用 .NET 可攜性分析器，您必須從 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) 下載及安裝此延伸模組。 它適用於 Visual Studio 2017 和更新版本。 您可以通過**分析** > **可攜性分析器設置**在 Visual Studio 中配置它，並選擇目標平臺，即要評估當前程式集構建的平臺/版本的可攜性差距的 .NET 平臺/版本。

![可攜性分析器的螢幕截圖。](./media/portability-analyzer/portability-screenshot.png)

您也可以使用 ApiPort 主控台應用程式，可從 [ApiPort 存放庫](https://aka.ms/apiportdownload)下載。 您可以使用 `listTargets` 命令選項來顯示可用的目標清單，然後指定 `-t` 或 `--target` 命令選項來挑選目標平台。

### <a name="analyze-portability"></a>分析可攜性
若要在 Visual Studio 中分析整個專案，在 [方案總管]**** 中以滑鼠右鍵按一下您的專案，然後選取 [分析組件可攜性]****。 否則，請移至 [分析]**** 功能表，然後選取 [Analyze Assembly Portability] (分析組件可攜性)****。 從這裡選取專案的可執行檔或 DLL。

![解決方案資源管理器中的可攜性分析器螢幕截圖。](./media/portability-analyzer/portability-solution-explorer.png)

您也可以使用 [ApiPort 主控台應用程式](https://aka.ms/apiportdownload)。

- 輸入下列命令分析目前的目錄︰`ApiPort.exe analyze -f .`
- 若要分析特定的 .dll 檔案清單，請輸入下列命令︰`ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`
- 執行 `ApiPort.exe -?` 以取得詳細說明

建議您納入所有您擁有並想要移植的相關 exe 與 dll 檔案，並排除應用程式所依賴，但您未擁有也無法移植的檔案。 這會提供您最相關的可攜性報告。

### <a name="view-and-interpret-portability-result"></a>檢視並解譯可攜性結果

只有目標平台不支援的 API 會顯示在報表中。
在 Visual Studio 執行分析之後，您會看到 .NET 可攜性報表檔案連結。 如果您使用 [ApiPort 主控台應用程式](https://aka.ms/apiportdownload)，您的 .NET 可攜性報表會儲存為您指定格式的檔案。 預設會在您目前的目錄中儲存為 Excel 檔案 (*.xlsx*)。

#### <a name="portability-summary"></a>可攜性摘要

![可攜性摘要的螢幕截圖。](./media/portability-analyzer/api-catalog-portablility-summary.png)

此報表顯示的可攜性摘要區段，會顯示該次執行中每個組件的可攜性百分比。 在上述範例中，71.24% 用於 `svcutil` 應用程式中的 .NET Framework API 可在 .NET Core + 平台延伸模組中取得。 如果您對多個組件執行 .NET 可攜性分析工具，每個組件都應該在可攜性摘要報告中具有一個資料列。

#### <a name="details"></a>詳細資料

![可攜性詳細資訊的螢幕截圖。](./media/portability-analyzer/api-catalog-portablility-details.png)

"**詳細資訊**"部分列出了任何選定的**目標平臺**中缺少的 API。

- 目標類型：類型缺少目標平台的 API
- 目標成員：目標平台缺少方法
- 組件名稱：缺少之 API 所在的 .NET Framework 組件。
- 每個選定的目標平臺都是一個列，如".NET 核心"："不支援"值表示此目標平臺上不支援 API。
- 建議的變更：建議變更 API 或技術。 目前，許多 API 的此欄位為空白或過期。 因為 API 太多，導致我們難以繼續。 我們將尋找替代解決方案，來為客戶提供有用的資訊。

#### <a name="missing-assemblies"></a>缺少的組件

![缺少程式集的螢幕截圖。](./media/portability-analyzer/api-catalog-missing-assemblies.png)

您可在報表中找到缺少的組件區段。 該區段會告訴您這份組件清單由已分析的組件所參考，但未進行分析。 如果是您自己擁有的組件，請將其納入 API 可攜性分析器中執行，以便您可為其取得 API 層級的詳細可攜性報告。 如果是第三方程式庫，請查看是否有支援您目標平台的較新版本。 如果有，請考慮改用較新版本。 最後，您會預期這份清單包含您應用程式所依賴的所有第三方組件，並確認它們有支援您目標平台的版本。

如需 .NET Portability Analyzer 的詳細資訊，請瀏覽 [GitHub 文件](https://github.com/Microsoft/dotnet-apiport#documentation)和 Channel 9 影片 [Brief Look at the .NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) (.NET Portability Analyzer 簡介)。
