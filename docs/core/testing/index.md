---
title: .NET Core 的單元測試
description: .NET Core 與 .NET Standard 專案中的單元測試。
author: ardalis
ms.author: wiwagn
ms.date: 08/30/2017
ms.openlocfilehash: fe0807f93396466df7ed7d01dbb7a83e39c67770
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131270"
---
# <a name="unit-testing-in-net-core-and-net-standard"></a>.NET Core 與 .NET Standard 中的單元測試

.NET Core 使單元測試的建立便得更加輕鬆。 本文會介紹單元測試，並示範它們和其他種類測試之間的差異。 接近頁面底部的連結資源，會向您示範如何將測試專案新增到解決方案。 在您設定好測試專案後，就能使用命令列或 Visual Studio 來執行單元測試。

.NET Core 2.0 和最新的版本均支援 [.NET Standard 2.0](../../standard/net-standard.md)，而我們將使用它的程式庫來示範單元測試。

您可以使用適用於 C#、F# 和 Visual Basic 的內建 .NET Core 2.0 及更新的單元測試專案範本，作為您個人專案的起點。

## <a name="what-are-unit-tests"></a>什麼是單元測試？

使用自動化測試是很好的方式，這種方式能確保應用程式按照作者想要的結果執行。 軟體應用程式的測試有多種類型。 其中包括整合測試、Web 測試、負載測試等等。 **單元測試**會測試個別軟體元件和方法。 單元測試應該只在開發人員的控制下用於測試程式碼， 而不應用來測試基礎結構考量。 基礎結構考量包括資料庫、檔案系統和網路資源。 

此外，也請記得撰寫測試時可採用最佳做法。 舉例來說，[測試驅動開發 (TDD)](https://deviq.com/test-driven-development/) 可在撰寫單元測試前，用在單元測試要檢查的程式碼上。 使用 TDD 就像是在寫書之前打好草稿。 它的目標是協助開發人員撰寫更簡單、更易讀且更有效率的程式碼。 

> [!NOTE]
> ASP.NET 小組遵循了[這些慣例](https://github.com/aspnet/Home/wiki/Engineering-guidelines#unit-tests-and-functional-tests)，來協助開發人員為測試類型與方法下個好名稱。

請試著不要在撰寫單元測試時於基礎結構導入相依性。 相依性會導致測試變慢且不穩定，它們應該留給整合測試使用。 您可以遵循 [Explicit Dependencies Principle](https://deviq.com/explicit-dependencies-principle/) (明確相依性準則) 的內容，並使用 [Dependency Injection](/aspnet/core/fundamentals/dependency-injection) (相依性注入)，來在應用程式中避免這些相依性。 您也可以將單元測試保留在個別專案中，和您的整合測試分開。 這能確保您的單元測試專案不會對基礎結構套件具有參考或相依性。

.NET Core 專案單元測試的詳細資訊：

以下語言支援 .NET Core 單元測試專案：
* [C#](../../csharp/index.md)
* [F#](../../fsharp/index.md)
* [Visual Basic](../../visual-basic/index.md) 

您也可以選擇使用：
* [xUnit](https://xunit.github.io) 
* [NUnit](https://nunit.org)
* [MSTest](https://github.com/Microsoft/vstest-docs)

您可以從以下逐步解說學到更多：

* 使用 [*xUnit* 與 *C#* 搭配 .NET Core CLI](unit-testing-with-dotnet-test.md) 來建立單元測試。
* 使用 [*NUnit* 及 *C#* 搭配 .NET Core CLI](unit-testing-with-nunit.md) 建立單元測試。
* 使用 [*MSTest* 與 *C#* 搭配 .NET Core CLI](unit-testing-with-mstest.md) 來建立單元測試。
* 使用 [*xUnit* 與 *F#* 搭配 .NET Core CLI](unit-testing-fsharp-with-dotnet-test.md) 來建立單元測試。
* 使用 [*NUnit* 及 *#* 搭配 .NET Core CLI](unit-testing-fsharp-with-nunit.md) 建立單元測試。
* 使用 [*MSTest* 與 *F#* 搭配 .NET Core CLI](unit-testing-fsharp-with-mstest.md) 來建立單元測試。
* 使用 [*xUnit* 與 *Visual Basic* 搭配 .NET Core CLI](unit-testing-visual-basic-with-dotnet-test.md) 來建立單元測試。
* 使用 [*Unit* 及 *Visual Basic* 搭配 .NET Core CLI](unit-testing-visual-basic-with-nunit.md) 來建立單元測試。
* 使用 [*MSTest* 與 *Visual Basic* 搭配 .NET Core CLI](unit-testing-visual-basic-with-mstest.md) 來建立單元測試。

您可以從以下文章學到更多：

* Visual Studio Enterprise 為 .NET Core 提供了絕佳的測試工具。 若要深入了解，可參閱[即時單元測試](/visualstudio/test/live-unit-testing)或[程式碼涵蓋範圍](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage)。
* 如需如何執行選擇性單元測試的詳細資訊，請參閱[執行選擇性單元測試](selective-unit-tests.md)或[使用 Visual Studio 來包含及排除測試](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods)。
* [如何搭配 xUnit 使用 .NET Core 和 Visual Studio](https://xunit.github.io/docs/getting-started-dotnet-core.html)。
