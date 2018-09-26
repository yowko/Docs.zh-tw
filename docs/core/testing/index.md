---
title: .NET Core 的單元測試
description: 單元測試從未如此輕鬆。 了解如何在 .NET Core 與 .NET Standard 專案中使用單元測試。
author: ardalis
ms.author: wiwagn
ms.date: 08/30/2017
ms.openlocfilehash: 4a1d880da796aac40da93ca2513b6163200ca3c1
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46004386"
---
# <a name="unit-testing-in-net-core-and-net-standard"></a>.NET Core 與 .NET Standard 中的單元測試

.NET Core 在設計時就已將可測試性納入考量，因此您可以更輕鬆地針對應用程式建立單元測試。 這篇文章簡短介紹單元測試，以及它們和其他種類測試之間的差異。 連結的資源會示範如何將測試專案加到您的方案，然後使用命令列或 Visual Studio 來執行單元測試。

.NET Core 2.0 支援 [.NET Standard 2.0](../../standard/net-standard.md)。 本節中用來示範單元測試的程式庫仰賴 .NET Standard，而且也能在其他專案類型中運作。

從 .NET Core 2.0 開始，我們就提供適用於 C#、F# 和 Visual Basic 的單元測試專案範本。

## <a name="getting-started-with-testing"></a>開始測試

最理想的方法是使用自動化的測試套件，以確保軟體應用程式按照作者想要的結果執行。 軟體應用程式測試的種類繁多，包括整合測試、Web 測試、負載測試等等。 測試個別軟體元件或方法的單元測試是最底層的測試。 單元測試應該只測試開發人員控制項內的程式碼，而不應針對基礎結構考量進行測試，例如資料庫、檔案系統或網路資源。 單元測試可能會使用[測試導向開發 (TDD)](http://deviq.com/test-driven-development/) 來進行寫入，或新增到現有的程式碼，以確認其正確性。 不論何種情況，單元測試應該是小型、妥善具名且可快速完成，因為在將變更推送到專案的共用程式碼存放庫之前，您可能需要先執行數百次的單元測試。

> [!NOTE]
> 開發人員經常必須絞盡腦汁才能想出適合其測試類別和方法的名稱。 因此，ASP.NET 產品團隊會遵循[這些慣例](https://github.com/aspnet/Home/wiki/Engineering-guidelines#unit-tests-and-functional-tests)以做為起點。

在撰寫單元測試時，務必小心不要在基礎結構中導入相依性。 這些相依性通常會讓測試速度更慢，而且更不可靠，因此應該將其保留到整合測試時進行。 您可以遵循 [Explicit Dependencies Principle](http://deviq.com/explicit-dependencies-principle/) (明確相依性準則) 的內容，在應用程式程式碼中避免這些隱藏的相依性，並使用 [Dependency Injection](/aspnet/core/fundamentals/dependency-injection) (相依性注入) 來要求架構的相依性。 您也可以將單元測試保存在整合測試以外的個別專案中，並確保您的單元測試專案不具基礎結構套件的參考及相依性。

進一步了解 .NET Core 專案的單元測試：

[C#](../../csharp/index.md)、[F#](../../fsharp/index.md) 與 [Visual Basic](../../visual-basic/index.md) 都支援適用於 .NET Core 的單元測試專案。 您也可以在 [xUnit](http://xunit.github.io)、[NUnit](http://nunit.org) 及 [MSTest](https://github.com/Microsoft/vstest-docs) 中選擇。

您可以在這些逐步解說中了解那些組合：

* 使用 [*xUnit* 與 *C#* 搭配 .NET Core CLI](unit-testing-with-dotnet-test.md) 來建立單元測試。
* 使用 [*NUnit* 及 *C#* 搭配 .NET Core CLI](unit-testing-with-nunit.md) 建立單元測試。
* 使用 [*MSTest* 與 *C#* 搭配 .NET Core CLI](unit-testing-with-mstest.md) 來建立單元測試。
* 使用 [*xUnit* 與 *F#* 搭配 .NET Core CLI](unit-testing-fsharp-with-dotnet-test.md) 來建立單元測試。
* 使用 [*NUnit* 及 *#* 搭配 .NET Core CLI](unit-testing-fsharp-with-nunit.md) 建立單元測試。
* 使用 [*MSTest* 與 *F#* 搭配 .NET Core CLI](unit-testing-fsharp-with-mstest.md) 來建立單元測試。
* 使用 [*xUnit* 與 *Visual Basic* 搭配 .NET Core CLI](unit-testing-visual-basic-with-dotnet-test.md) 來建立單元測試。
* 使用 [*Unit* 及 *Visual Basic* 搭配 .NET Core CLI](unit-testing-visual-basic-with-nunit.md) 來建立單元測試。
* 使用 [*MSTest* 與 *Visual Basic* 搭配 .NET Core CLI](unit-testing-visual-basic-with-mstest.md) 來建立單元測試。

您可以為您的類別庫與您的單元測試庫選擇不同的語言。 您可以透過混合並比對上面提及的逐步解說來了解如何進行。

* Visual Studio Enterprise 為 .NET Core 提供了絕佳的測試工具。 若要深入了解，可參閱[即時單元測試](/visualstudio/test/live-unit-testing)或[程式碼涵蓋範圍](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage)。
* 如需如何使用選擇性單元測試篩選的其他資訊與範例，請參閱[執行選擇性單元測試](selective-unit-tests.md)或[使用 Visual Studio 來包含及排除測試](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods)。
* xUnit 小組已撰寫教學課程，說明[如何使用 xUnit 搭配 .NET Core 和 Visual Studio](http://xunit.github.io/docs/getting-started-dotnet-core.html)。
