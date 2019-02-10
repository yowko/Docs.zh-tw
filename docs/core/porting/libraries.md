---
title: 將程式庫移植到 .NET Core
description: 了解如何將程式庫專案從 .NET Framework 移植到 .NET Core。
author: cartermp
ms.date: 12/7/2018
ms.custom: seodec18
ms.openlocfilehash: 8190dcfd3ffed9051c7724752a19d88e7bef4f4d
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904693"
---
# <a name="port-net-framework-libraries-to-net-core"></a>將 .NET Framework 程式庫移植到 .NET Core

了解如何將.NET Framework 程式庫程式碼移植到 .NET Core，以執行跨平台並擴展使用它的應用程式的範圍。

## <a name="prerequisites"></a>必要條件

本文假設您已具備下列條件：

- 使用 Visual Studio 2017 或更新版本。
  - 舊版 Visual Studio 不支援 .NET Core
- 了解[建議的移植程序](index.md)。
- 已解決任何[協力廠商相依性](third-party-deps.md)問題。

您也應該進一步熟悉下列主題的內容：

[.NET Standard](~/docs/standard/net-standard.md)   
本主題描述計畫在所有 .NET 實作上提供的正式 .NET API 規格。

[套件、中繼套件和架構](~/docs/core/packages.md)   
本文討論 .NET Core 如何定義及使用套件，以及套件如何支援在多個 .NET 實作上執行的程式碼。

[使用跨平台工具開發程式庫](~/docs/core/tutorials/libraries.md)   
本主題說明如何使用跨平台 CLI 工具撰寫 .NET 的程式庫。

[適用於 .NET Core 之 *csproj* 格式的新增項目](~/docs/core/tools/csproj.md)   
本文概述從改為使用 *csproj* 和 MSBuild 時，新增至專案檔的變更。

[移植到 .NET Core - 分析協力廠商相依性](~/docs/core/porting/third-party-deps.md)   
本主題討論協力廠商相依性的可攜性，以及當某個 NuGet 套件相依性無法在 .NET Core 上執行時的解決方法。

## <a name="retargeting-your-net-framework-code-to-net-framework-472"></a>將您的 .NET Framework 程式碼目標重新設定為 .NET Framework 4.7.2

如果您的程式碼目標不是 .NET Framework 4.7.2，建議您將目標重新設定為 .NET Framework 4.7.2。 這可確保在 .NET Standard 不支援現有 API 的情況下，仍可以使用最新的 API 替代項目。

針對您想要移轉的每個 Visual Studio 專案，執行下列作業︰

1. 以滑鼠右鍵按一下專案並選取 [屬性]。
1. 在 [目標 Framework] 下拉式清單中，選取 [.NET Framework 4.7.2]。
1. 重新編譯您的專案。

因為您的專案現在是以 .NET Framework 4.7.2 為目標，請使用該版本的 .NET Framework 作為基礎移植程式碼。

## <a name="determining-the-portability-of-your-code"></a>判斷程式碼的可攜性

下一個步驟是執行 API 可攜性分析器 (ApiPort)，以產生可用於分析的可攜性報告。

請確定您了解 [API 可攜性分析器 (ApiPort)](../../standard/analyzers/portability-analyzer.md)，以及產生目標 .NET Core 之可攜性報告的方式。 作法因個人需求及品味而異。 以下是幾種不同的方法。 根據您的程式碼架構，可以混合使用這些方法的步驟。

### <a name="dealing-primarily-with-the-compiler"></a>主要以編譯器處理

這個方法大概最適合小型專案或不使用太多 .NET Framework API 的專案。 方法相當簡單︰

1. 對專案選擇性地執行 ApiPort。 如果執行 ApiPort，請透過報告取得需解決問題的相關知識。
1. 將所有程式碼全部複製到新的 .NET Core 專案。
1. 在參考可攜性報告 (若有產生) 的同時，持續解決編譯器錯誤，直到專案可完整編譯為止。

雖然此方法不夠有條理，但以程式碼為主的方法通常可以快速解決問題，而且可能是最適合小型專案或程式庫的方法。 只包含資料模型的專案可能最適合此方法。

### <a name="staying-on-the-net-framework-until-portability-issues-are-resolved"></a>留在 .NET Framework 直到解決可攜性問題

如果您偏好在整個程序期間執行編譯的程式碼，這就是最佳方法。 方法如下所示︰

1. 對專案執行 ApiPort。
1. 使用不同的可攜式 API 來解決問題。
1. 記下您無法使用直接替代方法的所有區域。
1. 為所有要移植的專案重複上述步驟，直到確定每個專案皆已準備好複製到新的 .NET Core 專案。
1. 將程式碼複製到新的 .NET Core 專案。
1. 解決您先前所記下沒有直接替代方法的問題。

這個謹慎的方法比處理編譯器錯誤更有條理，但仍相當著重在程式碼，並具備永遠有會執行編譯之程式碼的優點。 改用其他 API 仍無法解決的問題，其解決方式差異極大。 您可能現某些專案需要開發更完善的方案，下個方法中會加以說明。

### <a name="developing-a-comprehensive-plan-of-attack"></a>開發全面的攻擊計畫

這個方法可能最適合大型且更複雜的專案，因為可能必須重新建構程式碼或完全重寫特定區域的程式碼才能支援 .NET Core。 方法如下所示︰

1. 對專案執行 ApiPort。
1. 了解每個非可攜式類型是用在程式碼的何處，以及對整體可攜性有何影響。
   - 了解這些類型的性質。 它們是否數量很少但使用頻繁？ 它們是否數量很大但很少使用？ 使用集中還是分散在整個程式碼？
   - 是否容易隔離非可攜式的程式碼，以便更輕鬆地處理它？
   - 是否需要重構程式碼？
   - 對於非可攜式的類型，是否有替代的 API 可以完成相同的工作？ 例如，如果您使用的是 <xref:System.Net.WebClient> 類別，或許可以改用 <xref:System.Net.Http.HttpClient> 類別。
   - 是否有不同的可攜式 API 可用來完成工作，即使它不是直接替換項目？ 例如，如果您是使用 <xref:System.Xml.Schema.XmlSchema> 來剖析 XML，但不需要 XML 結構描述探索，則可以使用 <xref:System.Xml.Linq> API 並自行實作剖析，而不需依靠 API。
1. 如果有難以移轉的組件，暫時留在 .NET Framework 是否值得？ 以下是要考量的事項：
   - 程式庫中可能有一些功能與 .NET Core 不相容，因為它太過依賴 .NET Framework 或 Windows 特定的功能。 是否值得先不考慮該功能，改為暫時推出功能較少的程式庫 .NET Core 版本，直到有資源可供移植該功能？
   - 重構是否會有幫助？
1. 撰寫無法使用的 .NET Framework API 自有實作是否合理？
   可以考慮複製、修改及使用來自 [.NET Framework 參考來源](https://github.com/Microsoft/referencesource) \(英文\) 的程式碼。 參考來源程式碼是依據 [MIT 授權條款](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt) \(英文\) 授權，因此您有充分的權限可以將該來源做為自己程式碼的基礎。 您只需記得在程式碼中適當地將版權歸於 Microsoft。
1. 視需要對不同的專案重複此程序。
 
分析階段可能需要一些時間，視您的程式碼基底大小而定。 在這個階段花時間徹底了解所需的變更範圍並開發計畫，通常能為未來省下許多時間，特別是在您程式碼基底較為複雜的情況下。

您的計劃可能涉及在對程式碼基底進行重大變更時仍要以 .NET Framework 4.7.2 為目標，讓它成為前一種方法更有條理的版本。 執行計畫的方式須視程式碼基底而定。

### <a name="mixing-approaches"></a>混合方法

您可能會根據每個專案混用上述各種方法。 您應該做對您和程式碼基底而言最有意義的事。

## <a name="porting-your-tests"></a>移植測試

移轉程式碼後，確定一切正常運作的最佳方式，是在將程式碼移轉到 .NET Core 時測試程式碼。 若要這樣做，您必須使用能針對 .NET Core 建置並執行測試的測試架構。 目前有三個選項︰

- [xUnit](https://xunit.github.io/)
  * [快速入門](https://xunit.github.io/docs/getting-started-dotnet-core.html)
  * [將 MSTest 專案轉換成 xUnit 的工具](https://github.com/dotnet/codeformatter/tree/master/src/XUnitConverter)
- [NUnit](https://nunit.org/)
  * [快速入門](https://github.com/nunit/docs/wiki/Installation)
  * [關於從 MSTest 移轉至 NUnit 的部落格文章](https://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
- [MSTest](https://docs.microsoft.com/visualstudio/test/unit-test-basics)

## <a name="recommended-approach-to-porting"></a>建議的移植方法

不管如何，移植工作都會大幅取決於 .NET Framework 程式碼的架構方式。 移植程式碼的良好方式，是從程式庫的「基底」開始，也就是程式碼的基本元件。 它可能是資料模型，也可能是所有其他項目會直接或間接使用的基礎類別和方法。

1. 針對測試目前正在移植之程式庫層的測試專案進行移植。
1. 將程式庫的基底複製到新的 .NET Core 專案，然後選取您想要支援的 .NET Standard 版本。
1. 進行任何必要的變更，令程式碼執行編譯。 此工作有很大一部分可能會需要將 NuGet 套件相依性新增到 *csproj* 檔案中。
1. 執行測試並進行任何必要的調整。
1. 挑選要移植的下一層程式碼，並重複上述步驟。

如果您是從程式庫基底向外進行移植，並視需要測試每一層，移植將會是個系統化的程序，並將所有問題都隔離在單層的程式碼內。

>[!div class="step-by-step"]
>[下一步](project-structure.md)
