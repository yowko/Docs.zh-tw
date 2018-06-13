---
title: 執行多樣化選擇的單元測試
description: 示範如何使用篩選運算式搭配 dotnet 測試命令執行多樣化選擇的單元測試。
author: smadala
ms.author: mairaw
ms.date: 03/22/2017
ms.openlocfilehash: caea91e9884dba6bc07a7ef6a99699e43d23399c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33210830"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="53601-103">執行多樣化選擇的單元測試</span><span class="sxs-lookup"><span data-stu-id="53601-103">Running selective unit tests</span></span>

<span data-ttu-id="53601-104">下列範例使用`dotnet test`。</span><span class="sxs-lookup"><span data-stu-id="53601-104">The following examples use `dotnet test`.</span></span> <span data-ttu-id="53601-105">若要使用`vstest.console.exe`，請以取代 `--testcasefilter:` 取代 `--filter `。</span><span class="sxs-lookup"><span data-stu-id="53601-105">If you're using `vstest.console.exe`, replace `--filter ` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="53601-106">MSTest</span><span class="sxs-lookup"><span data-stu-id="53601-106">MSTest</span></span>

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

| <span data-ttu-id="53601-107">運算式</span><span class="sxs-lookup"><span data-stu-id="53601-107">Expression</span></span> | <span data-ttu-id="53601-108">結果</span><span class="sxs-lookup"><span data-stu-id="53601-108">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="53601-109">執行 `FullyQualifiedName` 包含 `Method` 的測試。</span><span class="sxs-lookup"><span data-stu-id="53601-109">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="53601-110">`vstest 15.1+` 提供此測試。</span><span class="sxs-lookup"><span data-stu-id="53601-110">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="53601-111">執行名稱包含 `TestMethod1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="53601-111">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTestClass1` | <span data-ttu-id="53601-112">執行類別為 `MSTestNamespace.UnitTestClass1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="53601-112">Runs tests which are in class `MSTestNamespace.UnitTestClass1`.</span></span><br><span data-ttu-id="53601-113">**注意︰**`ClassName`值應會有命名空間，所以 `ClassName=UnitTestClass1` 將無法運作。</span><span class="sxs-lookup"><span data-stu-id="53601-113">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTestClass1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTestClass1.TestMethod1` | <span data-ttu-id="53601-114">執行 `MSTestNamespace.UnitTestClass1.TestMethod1` 以外的所有測試。</span><span class="sxs-lookup"><span data-stu-id="53601-114">Runs all tests except `MSTestNamespace.UnitTestClass1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="53601-115">執行標示有 `[TestCategory("CategoryA")]` 註釋的測試。</span><span class="sxs-lookup"><span data-stu-id="53601-115">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=3` | <span data-ttu-id="53601-116">執行標示有 `[Priority(3)]` 註釋的測試。</span><span class="sxs-lookup"><span data-stu-id="53601-116">Runs tests which are annotated with `[Priority(3)]`.</span></span><br><span data-ttu-id="53601-117">**注意︰因為** `Priority~3` 不是字串，所以是無效的值。</span><span class="sxs-lookup"><span data-stu-id="53601-117">**Note:** `Priority~3` is an invalid value, as it isn't a string.</span></span> |

<span data-ttu-id="53601-118">**使用條件式運算子 | 與 &amp;**</span><span class="sxs-lookup"><span data-stu-id="53601-118">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="53601-119">運算式</span><span class="sxs-lookup"><span data-stu-id="53601-119">Expression</span></span> | <span data-ttu-id="53601-120">結果</span><span class="sxs-lookup"><span data-stu-id="53601-120">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTestClass1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="53601-121">執行 `FullyQualifiedName` **或** `TestCategory` 中之 `UnitTestClass1` 為 `CategoryA` 的測試。</span><span class="sxs-lookup"><span data-stu-id="53601-121">Runs tests which have `UnitTestClass1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA"` | <span data-ttu-id="53601-122">執行 `FullyQualifiedName` **及** `TestCategory` 中之 `UnitTestClass1` 為 `CategoryA` 的測試。</span><span class="sxs-lookup"><span data-stu-id="53601-122">Runs tests which have `UnitTestClass1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="53601-123">執行 `FullyQualifiedName` 所含之 `UnitTestClass1` **及** `TestCategory` 為 `CategoryA` **或** `Priority` 為 1 的測試。</span><span class="sxs-lookup"><span data-stu-id="53601-123">Runs tests which have either `FullyQualifiedName` containing `UnitTestClass1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="53601-124">xUnit</span><span class="sxs-lookup"><span data-stu-id="53601-124">xUnit</span></span>

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

| <span data-ttu-id="53601-125">運算式</span><span class="sxs-lookup"><span data-stu-id="53601-125">Expression</span></span> | <span data-ttu-id="53601-126">結果</span><span class="sxs-lookup"><span data-stu-id="53601-126">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="53601-127">僅執行 `XUnitNamespace.TestClass1.Test1` 這一項測試。</span><span class="sxs-lookup"><span data-stu-id="53601-127">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="53601-128">執行 `XUnitNamespace.TestClass1.Test1` 以外的所有測試。</span><span class="sxs-lookup"><span data-stu-id="53601-128">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="53601-129">執行顯示名稱包含 `TestClass1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="53601-129">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="53601-130">在程式碼範例中，所定義具有索引鍵 `Category` 及 `Priority` 的特徵可用於篩選。</span><span class="sxs-lookup"><span data-stu-id="53601-130">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="53601-131">運算式</span><span class="sxs-lookup"><span data-stu-id="53601-131">Expression</span></span> | <span data-ttu-id="53601-132">結果</span><span class="sxs-lookup"><span data-stu-id="53601-132">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="53601-133">執行 `FullyQualifiedName` 包含 `XUnit` 的測試。</span><span class="sxs-lookup"><span data-stu-id="53601-133">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="53601-134">`vstest 15.1+` 提供此測試。</span><span class="sxs-lookup"><span data-stu-id="53601-134">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=bvt` | <span data-ttu-id="53601-135">執行包含 `[Trait("Category", "bvt")]` 的測試。</span><span class="sxs-lookup"><span data-stu-id="53601-135">Runs tests which have `[Trait("Category", "bvt")]`.</span></span> |

<span data-ttu-id="53601-136">**使用條件式運算子 | 與 &amp;**</span><span class="sxs-lookup"><span data-stu-id="53601-136">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="53601-137">運算式</span><span class="sxs-lookup"><span data-stu-id="53601-137">Expression</span></span> | <span data-ttu-id="53601-138">結果</span><span class="sxs-lookup"><span data-stu-id="53601-138">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=Nightly"</code> | <span data-ttu-id="53601-139">執行 `FullyQualifiedName` **或** `Category` 中之 `TestClass1` 為 `Nightly` 的測試。</span><span class="sxs-lookup"><span data-stu-id="53601-139">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `Nightly`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=Nightly"` | <span data-ttu-id="53601-140">執行 `FullyQualifiedName` **及** `Category` 中之 `TestClass1` 為 `Nightly` 的測試。</span><span class="sxs-lookup"><span data-stu-id="53601-140">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `Nightly`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=Nightly)&#124;Priority=1"</code> | <span data-ttu-id="53601-141">執行 `FullyQualifiedName` 所含之 `TestClass1` **及** `Category` 為 `CategoryA` **或** `Priority` 為 1 的測試。</span><span class="sxs-lookup"><span data-stu-id="53601-141">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |
