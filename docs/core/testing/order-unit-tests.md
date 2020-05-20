---
title: 訂單單元測試
description: 瞭解如何使用 .NET Core 訂購單元測試。
author: IEvangelist
ms.date: 05/18/2020
zone_pivot_groups: unit-testing-framework-set-one
ms.openlocfilehash: ce0d01c924075ffcc9ad49ef8aca49222c10c921
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83704556"
---
# <a name="order-unit-tests"></a><span data-ttu-id="d690d-103">訂單單元測試</span><span class="sxs-lookup"><span data-stu-id="d690d-103">Order unit tests</span></span>

<span data-ttu-id="d690d-104">有時候，您可能會想要以特定循序執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="d690d-104">Occasionally, you may want to have unit tests run in a specific order.</span></span> <span data-ttu-id="d690d-105">在理想的情況下，單元測試執行的順序並_不_重要，而且[最佳做法](unit-testing-best-practices.md)是避免排序單元測試。</span><span class="sxs-lookup"><span data-stu-id="d690d-105">Ideally, the order in which unit tests run should _not_ matter, and it is [best practice](unit-testing-best-practices.md) to avoid ordering unit tests.</span></span> <span data-ttu-id="d690d-106">無論如何，都可能需要這麼做。</span><span class="sxs-lookup"><span data-stu-id="d690d-106">Regardless, there may be a need to do so.</span></span> <span data-ttu-id="d690d-107">在此情況下，本文示範如何排序測試回合。</span><span class="sxs-lookup"><span data-stu-id="d690d-107">In that case, this article demonstrates how to order test runs.</span></span>

<span data-ttu-id="d690d-108">如果您想要流覽原始程式碼，請參閱[訂購 .Net Core 單元測試](/samples/dotnet/samples/order-unit-tests-cs)範例存放庫。</span><span class="sxs-lookup"><span data-stu-id="d690d-108">If you prefer to browse the source code, see the [order .NET Core unit tests](/samples/dotnet/samples/order-unit-tests-cs) sample repository.</span></span>

> [!TIP]
> <span data-ttu-id="d690d-109">除了本文所述的排序功能以外，請考慮[使用 Visual Studio 來建立自訂播放清單](/visualstudio/test/run-unit-tests-with-test-explorer?view=vs-2019#create-custom-playlists)，做為替代方案。</span><span class="sxs-lookup"><span data-stu-id="d690d-109">In addition to the ordering capabilities outlined in this article, consider [creating custom playlists with Visual Studio](/visualstudio/test/run-unit-tests-with-test-explorer?view=vs-2019#create-custom-playlists) as an alternative.</span></span>

:::zone pivot="mstest"

## <a name="order-alphabetically"></a><span data-ttu-id="d690d-110">依字母順序排列</span><span class="sxs-lookup"><span data-stu-id="d690d-110">Order alphabetically</span></span>

<span data-ttu-id="d690d-111">透過 MSTest，測試會依其測試名稱自動排序。</span><span class="sxs-lookup"><span data-stu-id="d690d-111">With MSTest, tests are automatically ordered by their test name.</span></span>

> [!NOTE]
> <span data-ttu-id="d690d-112">名為的測試 `Test14` 會在之前執行， `Test2` 即使該數位 `2` 小於 `14` 。</span><span class="sxs-lookup"><span data-stu-id="d690d-112">A test named `Test14` will run before `Test2` even though the number  `2` is less than `14`.</span></span> <span data-ttu-id="d690d-113">這是因為測試名稱順序會使用測試的文字名稱。</span><span class="sxs-lookup"><span data-stu-id="d690d-113">This is because, test name ordering uses the text name of the test.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/MSTest.Project/ByAlphabeticalOrder.cs":::

:::zone-end
:::zone pivot="xunit"

<span data-ttu-id="d690d-114">XUnit 測試架構可讓您更精確地控制測試回合順序。</span><span class="sxs-lookup"><span data-stu-id="d690d-114">The xUnit test framework allows for more granularity and control of test run order.</span></span> <span data-ttu-id="d690d-115">您會執行 `ITestCaseOrderer` 和 `ITestCollectionOrderer` 介面，以控制類別或測試集合的測試案例順序。</span><span class="sxs-lookup"><span data-stu-id="d690d-115">You implement the `ITestCaseOrderer` and `ITestCollectionOrderer` interfaces to control the order of test cases for a class, or test collections.</span></span>

## <a name="order-by-test-case-alphabetically"></a><span data-ttu-id="d690d-116">依字母順序排序測試案例</span><span class="sxs-lookup"><span data-stu-id="d690d-116">Order by test case alphabetically</span></span>

<span data-ttu-id="d690d-117">若要依其方法名稱排序測試案例，請執行 `ITestCaseOrderer` 並提供排序機制。</span><span class="sxs-lookup"><span data-stu-id="d690d-117">To order test cases by their method name, you implement the `ITestCaseOrderer` and provide an ordering mechanism.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/AlphabeticalOrderer.cs":::

<span data-ttu-id="d690d-118">然後在測試類別中，使用來設定測試案例順序 `TestCaseOrdererAttribute` 。</span><span class="sxs-lookup"><span data-stu-id="d690d-118">Then in a test class you set the test case order with the `TestCaseOrdererAttribute`.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByAlphabeticalOrder.cs":::

## <a name="order-by-collection-alphabetically"></a><span data-ttu-id="d690d-119">依字母順序排序</span><span class="sxs-lookup"><span data-stu-id="d690d-119">Order by collection alphabetically</span></span>

<span data-ttu-id="d690d-120">若要依顯示名稱排序測試集合，請執行 `ITestCollectionOrderer` 並提供排序機制。</span><span class="sxs-lookup"><span data-stu-id="d690d-120">To order test collections by their display name, you implement the `ITestCollectionOrderer` and provide an ordering mechanism.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/DisplayNameOrderer.cs":::

<span data-ttu-id="d690d-121">由於測試集合可能會以平行方式執行，因此您必須使用明確地停用集合的測試平行化 `CollectionBehaviorAttribute` 。</span><span class="sxs-lookup"><span data-stu-id="d690d-121">Since test collections potentially run in parallel, you must explicitly disable test parallelization of the collections with the `CollectionBehaviorAttribute`.</span></span> <span data-ttu-id="d690d-122">然後指定的實作為 `TestCollectionOrdererAttribute` 。</span><span class="sxs-lookup"><span data-stu-id="d690d-122">Then specify the implementation to the `TestCollectionOrdererAttribute`.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByDisplayName.cs":::

## <a name="order-by-custom-attribute"></a><span data-ttu-id="d690d-123">依自訂屬性排序</span><span class="sxs-lookup"><span data-stu-id="d690d-123">Order by custom attribute</span></span>

<span data-ttu-id="d690d-124">若要使用自訂屬性來排序 xUnit 測試，您必須先有屬性需要依賴。</span><span class="sxs-lookup"><span data-stu-id="d690d-124">To order xUnit tests with custom attributes, you first need an attribute to rely on.</span></span> <span data-ttu-id="d690d-125">定義，如下 `TestPriorityAttribute` 所示：</span><span class="sxs-lookup"><span data-stu-id="d690d-125">Define a `TestPriorityAttribute` as follows:</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Attributes/TestPriorityAttribute.cs":::

<span data-ttu-id="d690d-126">接下來，請考慮下列 `PriorityOrderer` 介面的執行 `ITestCaseOrderer` 。</span><span class="sxs-lookup"><span data-stu-id="d690d-126">Next, consider the following `PriorityOrderer` implementation of the `ITestCaseOrderer` interface.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/PriorityOrderer.cs":::

<span data-ttu-id="d690d-127">然後在測試類別中，將測試案例順序的設定 `TestCaseOrdererAttribute` 為 `PriorityOrderer` 。</span><span class="sxs-lookup"><span data-stu-id="d690d-127">Then in a test class you set the test case order with the `TestCaseOrdererAttribute` to the `PriorityOrderer`.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByPriorityOrder.cs":::

:::zone-end
:::zone pivot="nunit"

## <a name="order-by-priority"></a><span data-ttu-id="d690d-128">Order by 優先順序</span><span class="sxs-lookup"><span data-stu-id="d690d-128">Order by priority</span></span>

<span data-ttu-id="d690d-129">為了明確地排序測試，NUnit 提供 [`OrderAttribute`](https://github.com/nunit/docs/wiki/Order-Attribute) 。</span><span class="sxs-lookup"><span data-stu-id="d690d-129">To order tests explicitly, NUnit provides an [`OrderAttribute`](https://github.com/nunit/docs/wiki/Order-Attribute).</span></span> <span data-ttu-id="d690d-130">具有這個屬性的測試會在沒有的測試之前啟動。</span><span class="sxs-lookup"><span data-stu-id="d690d-130">Tests with this attribute are started before tests without.</span></span> <span data-ttu-id="d690d-131">順序值是用來決定執行單元測試的順序。</span><span class="sxs-lookup"><span data-stu-id="d690d-131">The order value is used to determined the order to run the unit tests.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/NUnit.TestProject/ByOrder.cs":::

:::zone-end

## <a name="next-steps"></a><span data-ttu-id="d690d-132">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d690d-132">Next Steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d690d-133">單元測試最佳做法</span><span class="sxs-lookup"><span data-stu-id="d690d-133">Unit testing best practices</span></span>](unit-testing-best-practices.md)
