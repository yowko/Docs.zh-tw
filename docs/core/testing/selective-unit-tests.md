---
title: "執行多樣化選擇的單元測試"
description: "示範如何使用篩選運算式搭配 dotnet 測試命令執行多樣化選擇的單元測試。"
keywords: ".NET, .NET Core, 單元測試, 多樣化選擇的測試"
author: smadala
ms.author: mairaw
ms.date: 03/22/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 13d01272-bbf8-456c-a97a-560001d1a7f2
ms.openlocfilehash: af832d04d2cba530a93710a90701ab119a66deef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="4b067-104">執行多樣化選擇的單元測試</span><span class="sxs-lookup"><span data-stu-id="4b067-104">Running selective unit tests</span></span>

<span data-ttu-id="4b067-105">下列範例使用`dotnet test`。</span><span class="sxs-lookup"><span data-stu-id="4b067-105">The following examples use `dotnet test`.</span></span> <span data-ttu-id="4b067-106">若要使用`vstest.console.exe`，請以取代 `--testcasefilter:` 取代 `--filter `。</span><span class="sxs-lookup"><span data-stu-id="4b067-106">If you're using `vstest.console.exe`, replace `--filter ` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="4b067-107">MSTest</span><span class="sxs-lookup"><span data-stu-id="4b067-107">MSTest</span></span>

```csharp
namespace MSTestNamespace
{
    using Microsoft.VisualStudio.TestTools.UnitTesting;

    [TestClass]
    public class UnitTestClass1
    {
        [Priority(2)]
        [TestMethod]
        public void TestMethod1()
        {
        }

        [TestCategory("CategoryA")]
        [Priority(3)]
        [TestMethod]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="4b067-108">運算式</span><span class="sxs-lookup"><span data-stu-id="4b067-108">Expression</span></span> | <span data-ttu-id="4b067-109">結果</span><span class="sxs-lookup"><span data-stu-id="4b067-109">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="4b067-110">執行 `FullyQualifiedName` 包含 `Method` 的測試。</span><span class="sxs-lookup"><span data-stu-id="4b067-110">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="4b067-111">`vstest 15.1+` 提供此測試。</span><span class="sxs-lookup"><span data-stu-id="4b067-111">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="4b067-112">執行名稱包含 `TestMethod1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="4b067-112">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTestClass1` | <span data-ttu-id="4b067-113">執行類別為 `MSTestNamespace.UnitTestClass1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="4b067-113">Runs tests which are in class `MSTestNamespace.UnitTestClass1`.</span></span><br><span data-ttu-id="4b067-114">**注意︰**`ClassName`值應會有命名空間，所以 `ClassName=UnitTestClass1` 將無法運作。</span><span class="sxs-lookup"><span data-stu-id="4b067-114">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTestClass1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTestClass1.TestMethod1` | <span data-ttu-id="4b067-115">執行 `MSTestNamespace.UnitTestClass1.TestMethod1` 以外的所有測試。</span><span class="sxs-lookup"><span data-stu-id="4b067-115">Runs all tests except `MSTestNamespace.UnitTestClass1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="4b067-116">執行標示有 `[TestCategory("CategoryA")]` 註釋的測試。</span><span class="sxs-lookup"><span data-stu-id="4b067-116">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=3` | <span data-ttu-id="4b067-117">執行標示有 `[Priority(3)]` 註釋的測試。</span><span class="sxs-lookup"><span data-stu-id="4b067-117">Runs tests which are annotated with `[Priority(3)]`.</span></span><br><span data-ttu-id="4b067-118">**注意︰因為** `Priority~3` 不是字串，所以是無效的值。</span><span class="sxs-lookup"><span data-stu-id="4b067-118">**Note:** `Priority~3` is an invalid value, as it isn't a string.</span></span> |

<span data-ttu-id="4b067-119">**使用條件式運算子 | 與 &amp;**</span><span class="sxs-lookup"><span data-stu-id="4b067-119">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="4b067-120">運算式</span><span class="sxs-lookup"><span data-stu-id="4b067-120">Expression</span></span> | <span data-ttu-id="4b067-121">結果</span><span class="sxs-lookup"><span data-stu-id="4b067-121">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTestClass1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="4b067-122">執行 `FullyQualifiedName` **或** `TestCategory` 中之 `UnitTestClass1` 為 `CategoryA` 的測試。</span><span class="sxs-lookup"><span data-stu-id="4b067-122">Runs tests which have `UnitTestClass1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA"` | <span data-ttu-id="4b067-123">執行 `FullyQualifiedName` **及** `TestCategory` 中之 `UnitTestClass1` 為 `CategoryA` 的測試。</span><span class="sxs-lookup"><span data-stu-id="4b067-123">Runs tests which have `UnitTestClass1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="4b067-124">執行 `FullyQualifiedName` 所含之 `UnitTestClass1` **及** `TestCategory` 為 `CategoryA` **或** `Priority` 為 1 的測試。</span><span class="sxs-lookup"><span data-stu-id="4b067-124">Runs tests which have either `FullyQualifiedName` containing `UnitTestClass1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="4b067-125">xUnit</span><span class="sxs-lookup"><span data-stu-id="4b067-125">xUnit</span></span>

```csharp
namespace XUnitNamespace
{
    public class TestClass1
    {
        [Trait("Category", "bvt")]
        [Trait("Priority", "1")]
        [Fact]
        public void foo()
        {
        }

        [Trait("Category", "Nightly")]
        [Trait("Priority", "2")]
        [Fact]
        public void bar()
        {
        }
    }
}
```

| <span data-ttu-id="4b067-126">運算式</span><span class="sxs-lookup"><span data-stu-id="4b067-126">Expression</span></span> | <span data-ttu-id="4b067-127">結果</span><span class="sxs-lookup"><span data-stu-id="4b067-127">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="4b067-128">僅執行 `XUnitNamespace.TestClass1.Test1` 這一項測試。</span><span class="sxs-lookup"><span data-stu-id="4b067-128">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="4b067-129">執行 `XUnitNamespace.TestClass1.Test1` 以外的所有測試。</span><span class="sxs-lookup"><span data-stu-id="4b067-129">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="4b067-130">執行顯示名稱包含 `TestClass1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="4b067-130">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="4b067-131">在程式碼範例中，所定義具有索引鍵 `Category` 及 `Priority` 的特徵可用於篩選。</span><span class="sxs-lookup"><span data-stu-id="4b067-131">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="4b067-132">運算式</span><span class="sxs-lookup"><span data-stu-id="4b067-132">Expression</span></span> | <span data-ttu-id="4b067-133">結果</span><span class="sxs-lookup"><span data-stu-id="4b067-133">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="4b067-134">執行 `FullyQualifiedName` 包含 `XUnit` 的測試。</span><span class="sxs-lookup"><span data-stu-id="4b067-134">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="4b067-135">`vstest 15.1+` 提供此測試。</span><span class="sxs-lookup"><span data-stu-id="4b067-135">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=bvt` | <span data-ttu-id="4b067-136">執行包含 `[Trait("Category", "bvt")]` 的測試。</span><span class="sxs-lookup"><span data-stu-id="4b067-136">Runs tests which have `[Trait("Category", "bvt")]`.</span></span> |

<span data-ttu-id="4b067-137">**使用條件式運算子 | 與 &amp;**</span><span class="sxs-lookup"><span data-stu-id="4b067-137">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="4b067-138">運算式</span><span class="sxs-lookup"><span data-stu-id="4b067-138">Expression</span></span> | <span data-ttu-id="4b067-139">結果</span><span class="sxs-lookup"><span data-stu-id="4b067-139">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=Nightly"</code> | <span data-ttu-id="4b067-140">執行 `FullyQualifiedName` **或** `Category` 中之 `TestClass1` 為 `Nightly` 的測試。</span><span class="sxs-lookup"><span data-stu-id="4b067-140">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `Nightly`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=Nightly"` | <span data-ttu-id="4b067-141">執行 `FullyQualifiedName` **及** `Category` 中之 `TestClass1` 為 `Nightly` 的測試。</span><span class="sxs-lookup"><span data-stu-id="4b067-141">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `Nightly`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=Nightly)&#124;Priority=1"</code> | <span data-ttu-id="4b067-142">執行 `FullyQualifiedName` 所含之 `TestClass1` **及** `Category` 為 `CategoryA` **或** `Priority` 為 1 的測試。</span><span class="sxs-lookup"><span data-stu-id="4b067-142">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |
