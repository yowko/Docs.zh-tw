---
title: 排序單元測試
description: 瞭解如何使用 .NET Core 訂購單元測試。
author: IEvangelist
ms.author: dapine
ms.date: 05/18/2020
zone_pivot_groups: unit-testing-framework-set-one
ms.openlocfilehash: eb426b790e0623b0cf233a763e93d2bd501b8034
ms.sourcegitcommit: 4ad2f8920251f3744240c3b42a443ffbe0a46577
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/08/2020
ms.locfileid: "86100817"
---
# <a name="order-unit-tests"></a>排序單元測試

有時候，您可能會想要以特定循序執行單元測試。 在理想的情況下，單元測試執行的順序並_不_重要，而且[最佳做法](unit-testing-best-practices.md)是避免排序單元測試。 無論如何，都可能需要這麼做。 在此情況下，本文示範如何排序測試回合。

如果您想要流覽原始程式碼，請參閱[訂購 .Net Core 單元測試](/samples/dotnet/samples/order-unit-tests-cs)範例存放庫。

> [!TIP]
> 除了本文所述的排序功能以外，請考慮[使用 Visual Studio 來建立自訂播放清單](/visualstudio/test/run-unit-tests-with-test-explorer?view=vs-2019#create-custom-playlists)，做為替代方案。

:::zone pivot="mstest"

## <a name="order-alphabetically"></a>依字母順序排列

透過 MSTest，測試會依其測試名稱自動排序。

> [!NOTE]
> 名為的測試 `Test14` 會在之前執行， `Test2` 即使該數位 `2` 小於 `14` 。 這是因為測試名稱順序會使用測試的文字名稱。

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/MSTest.Project/ByAlphabeticalOrder.cs":::

:::zone-end
:::zone pivot="xunit"

XUnit 測試架構可讓您更精確地控制測試回合順序。 您會執行 `ITestCaseOrderer` 和 `ITestCollectionOrderer` 介面，以控制類別或測試集合的測試案例順序。

## <a name="order-by-test-case-alphabetically"></a>依字母順序排序測試案例

若要依其方法名稱排序測試案例，請執行 `ITestCaseOrderer` 並提供排序機制。

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/AlphabeticalOrderer.cs":::

然後在測試類別中，使用來設定測試案例順序 `TestCaseOrdererAttribute` 。

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByAlphabeticalOrder.cs":::

## <a name="order-by-collection-alphabetically"></a>依字母順序排序

若要依顯示名稱排序測試集合，請執行 `ITestCollectionOrderer` 並提供排序機制。

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/DisplayNameOrderer.cs":::

由於測試集合可能會以平行方式執行，因此您必須使用明確地停用集合的測試平行化 `CollectionBehaviorAttribute` 。 然後指定的實作為 `TestCollectionOrdererAttribute` 。

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByDisplayName.cs":::

## <a name="order-by-custom-attribute"></a>依自訂屬性排序

若要使用自訂屬性來排序 xUnit 測試，您必須先有屬性需要依賴。 定義，如下 `TestPriorityAttribute` 所示：

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Attributes/TestPriorityAttribute.cs":::

接下來，請考慮下列 `PriorityOrderer` 介面的執行 `ITestCaseOrderer` 。

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/PriorityOrderer.cs":::

然後在測試類別中，將測試案例順序的設定 `TestCaseOrdererAttribute` 為 `PriorityOrderer` 。

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByPriorityOrder.cs":::

:::zone-end
:::zone pivot="nunit"

## <a name="order-by-priority"></a>Order by 優先順序

為了明確地排序測試，NUnit 提供 [`OrderAttribute`](https://github.com/nunit/docs/wiki/Order-Attribute) 。 具有這個屬性的測試會在沒有的測試之前啟動。 順序值是用來決定執行單元測試的順序。

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/NUnit.TestProject/ByOrder.cs":::

:::zone-end

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [單元測試程式碼涵蓋範圍](unit-testing-code-coverage.md)
