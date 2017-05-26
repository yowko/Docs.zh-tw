---
title: ".NET Core 中的單元測試 | Microsoft Docs"
description: ".NET Core 的單元測試"
keywords: .NET, .NET Core
author: ardalis
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 815ac74c-4bd9-4a94-a87c-78288b27c0e2
ms.translationtype: Human Translation
ms.sourcegitcommit: 4437ce5d344cf06d30e31911def6287999fc6ffc
ms.openlocfilehash: 4983af5386efc6b713f10f200687535b7dc36a11
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---

# <a name="unit-testing-in-net-core"></a>.NET Core 的單元測試

.NET Core 在設計時就已將可測試性納入考量，因此您可以更輕鬆地針對應用程式建立單元測試。 這篇文章簡短介紹單元測試，以及它們和其他種類測試之間的差異。 連結的資源會示範如何將測試專案新增至您的解決方案，然後使用命令列或 Visual Studio 來執行單元測試。

## <a name="getting-started-with-testing"></a>開始測試
 
最理想的方法是使用自動化的測試套件，以確保軟體應用程式按照作者想要的結果執行。 軟體應用程式測試的種類繁多，包括整合測試、Web 測試、負載測試等等。 單元測試是其中最基層的測試，可用來測試個別的軟體元件或方法。 單元測試應該只測試開發人員控制項內的程式碼，而不應針對基礎結構考量進行測試，例如資料庫、檔案系統或網路資源。 單元測試可能會使用[測試導向開發 (TDD)](http://deviq.com/test-driven-development/) 來進行寫入，或新增到現有的程式碼，以確認其正確性。 不論何種情況，單元測試應該是小型、妥善具名且可快速完成，因為在將變更推送到專案的共用程式碼存放庫之前，您可能需要先執行數百次的單元測試。

> [!NOTE]
> 開發人員經常必須絞盡腦汁才能想出適合其測試類別和方法的名稱。 因此，ASP.NET 產品團隊會遵循[這些慣例](https://github.com/aspnet/Home/wiki/Engineering-guidelines#unit-tests-and-functional-tests)以做為起點。

在撰寫單元測試時，務必小心不要在基礎結構中導入相依性。 這些相依性通常會讓測試速度更慢，而且更不可靠，因此應該將其保留到整合測試時進行。 您可以遵循 [Explicit Dependencies Principle](http://deviq.com/explicit-dependencies-principle/) (明確相依性準則) 的內容，在應用程式程式碼中避免這些隱藏的相依性，並使用 [Dependency Injection](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/dependency-injection) (相依性注入) 來要求架構的相依性。 您也可以將單元測試保存在整合測試以外的個別專案中，並確保您的單元測試專案不會參考基礎結構套件，或不具有基礎結構套件的相依性。

進一步了解 .NET Core 專案的單元測試：

* 請參閱這份[使用 xUnit 和 .NET CLI 建立單元測試的逐步解說](unit-testing-with-dotnet-test.md)。 
* XUnit 小組已撰寫本教學課程以說明[如何在 .NET Core 和 Visual Studio 中搭配使用 xUnit](http://xunit.github.io/docs/getting-started-dotnet-core.html)。
* 如果您偏好使用 MSTest，請參閱這份[使用 MSTest 和 .NET CLI 建立單元測試的逐步解說](unit-testing-with-mstest.md)。
* 如需如何使用選擇性單元測試篩選的其他資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。

