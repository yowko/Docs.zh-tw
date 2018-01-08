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
ms.workload: dotnetcore
ms.openlocfilehash: a650e971afd63171b0cc12f679d81bc222a609a5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="2fd44-104">執行多樣化選擇的單元測試</span><span class="sxs-lookup"><span data-stu-id="2fd44-104">Running selective unit tests</span></span>

<span data-ttu-id="2fd44-105">下列範例使用`dotnet test`。</span><span class="sxs-lookup"><span data-stu-id="2fd44-105">The following examples use `dotnet test`.</span></span> <span data-ttu-id="2fd44-106">若要使用`vstest.console.exe`，請以取代 `--testcasefilter:` 取代 `--filter `。</span><span class="sxs-lookup"><span data-stu-id="2fd44-106">If you're using `vstest.console.exe`, replace `--filter ` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="2fd44-107">MSTest</span><span class="sxs-lookup"><span data-stu-id="2fd44-107">MSTest</span></span>

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

| <span data-ttu-id="2fd44-108">運算式</span><span class="sxs-lookup"><span data-stu-id="2fd44-108">Expression</span></span> | <span data-ttu-id="2fd44-109">結果</span><span class="sxs-lookup"><span data-stu-id="2fd44-109">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="2fd44-110">執行 `FullyQualifiedName` 包含 `Method` 的測試。</span><span class="sxs-lookup"><span data-stu-id="2fd44-110">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="2fd44-111">`vstest 15.1+` 提供此測試。</span><span class="sxs-lookup"><span data-stu-id="2fd44-111">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="2fd44-112">執行名稱包含 `TestMethod1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="2fd44-112">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTestClass1` | <span data-ttu-id="2fd44-113">執行類別為 `MSTestNamespace.UnitTestClass1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="2fd44-113">Runs tests which are in class `MSTestNamespace.UnitTestClass1`.</span></span><br><span data-ttu-id="2fd44-114">**注意︰**`ClassName`值應會有命名空間，所以 `ClassName=UnitTestClass1` 將無法運作。</span><span class="sxs-lookup"><span data-stu-id="2fd44-114">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTestClass1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTestClass1.TestMethod1` | <span data-ttu-id="2fd44-115">執行 `MSTestNamespace.UnitTestClass1.TestMethod1` 以外的所有測試。</span><span class="sxs-lookup"><span data-stu-id="2fd44-115">Runs all tests except `MSTestNamespace.UnitTestClass1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="2fd44-116">執行標示有 `[TestCategory("CategoryA")]` 註釋的測試。</span><span class="sxs-lookup"><span data-stu-id="2fd44-116">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=3` | <span data-ttu-id="2fd44-117">執行標示有 `[Priority(3)]` 註釋的測試。</span><span class="sxs-lookup"><span data-stu-id="2fd44-117">Runs tests which are annotated with `[Priority(3)]`.</span></span><br><span data-ttu-id="2fd44-118">**注意︰因為** `Priority~3` 不是字串，所以是無效的值。</span><span class="sxs-lookup"><span data-stu-id="2fd44-118">**Note:** `Priority~3` is an invalid value, as it isn't a string.</span></span> |

<span data-ttu-id="2fd44-119">**使用條件式運算子 | 與 &amp;**</span><span class="sxs-lookup"><span data-stu-id="2fd44-119">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="2fd44-120">運算式</span><span class="sxs-lookup"><span data-stu-id="2fd44-120">Expression</span></span> | <span data-ttu-id="2fd44-121">結果</span><span class="sxs-lookup"><span data-stu-id="2fd44-121">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTestClass1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="2fd44-122">執行 `FullyQualifiedName` **或** `TestCategory` 中之 `UnitTestClass1` 為 `CategoryA` 的測試。</span><span class="sxs-lookup"><span data-stu-id="2fd44-122">Runs tests which have `UnitTestClass1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA"` | <span data-ttu-id="2fd44-123">執行 `FullyQualifiedName` **及** `TestCategory` 中之 `UnitTestClass1` 為 `CategoryA` 的測試。</span><span class="sxs-lookup"><span data-stu-id="2fd44-123">Runs tests which have `UnitTestClass1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="2fd44-124">執行 `FullyQualifiedName` 所含之 `UnitTestClass1` **及** `TestCategory` 為 `CategoryA` **或** `Priority` 為 1 的測試。</span><span class="sxs-lookup"><span data-stu-id="2fd44-124">Runs tests which have either `FullyQualifiedName` containing `UnitTestClass1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="2fd44-125">xUnit</span><span class="sxs-lookup"><span data-stu-id="2fd44-125">xUnit</span></span>

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

| <span data-ttu-id="2fd44-126">運算式</span><span class="sxs-lookup"><span data-stu-id="2fd44-126">Expression</span></span> | <span data-ttu-id="2fd44-127">結果</span><span class="sxs-lookup"><span data-stu-id="2fd44-127">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="2fd44-128">僅執行 `XUnitNamespace.TestClass1.Test1` 這一項測試。</span><span class="sxs-lookup"><span data-stu-id="2fd44-128">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="2fd44-129">執行 `XUnitNamespace.TestClass1.Test1` 以外的所有測試。</span><span class="sxs-lookup"><span data-stu-id="2fd44-129">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="2fd44-130">執行顯示名稱包含 `TestClass1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="2fd44-130">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="2fd44-131">在程式碼範例中，所定義具有索引鍵 `Category` 及 `Priority` 的特徵可用於篩選。</span><span class="sxs-lookup"><span data-stu-id="2fd44-131">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="2fd44-132">運算式</span><span class="sxs-lookup"><span data-stu-id="2fd44-132">Expression</span></span> | <span data-ttu-id="2fd44-133">結果</span><span class="sxs-lookup"><span data-stu-id="2fd44-133">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="2fd44-134">執行 `FullyQualifiedName` 包含 `XUnit` 的測試。</span><span class="sxs-lookup"><span data-stu-id="2fd44-134">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="2fd44-135">`vstest 15.1+` 提供此測試。</span><span class="sxs-lookup"><span data-stu-id="2fd44-135">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=bvt` | <span data-ttu-id="2fd44-136">執行包含 `[Trait("Category", "bvt")]` 的測試。</span><span class="sxs-lookup"><span data-stu-id="2fd44-136">Runs tests which have `[Trait("Category", "bvt")]`.</span></span> |

<span data-ttu-id="2fd44-137">**使用條件式運算子 | 與 &amp;**</span><span class="sxs-lookup"><span data-stu-id="2fd44-137">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="2fd44-138">運算式</span><span class="sxs-lookup"><span data-stu-id="2fd44-138">Expression</span></span> | <span data-ttu-id="2fd44-139">結果</span><span class="sxs-lookup"><span data-stu-id="2fd44-139">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=Nightly"</code> | <span data-ttu-id="2fd44-140">執行 `FullyQualifiedName` **或** `Category` 中之 `TestClass1` 為 `Nightly` 的測試。</span><span class="sxs-lookup"><span data-stu-id="2fd44-140">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `Nightly`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=Nightly"` | <span data-ttu-id="2fd44-141">執行 `FullyQualifiedName` **及** `Category` 中之 `TestClass1` 為 `Nightly` 的測試。</span><span class="sxs-lookup"><span data-stu-id="2fd44-141">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `Nightly`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=Nightly)&#124;Priority=1"</code> | <span data-ttu-id="2fd44-142">執行 `FullyQualifiedName` 所含之 `TestClass1` **及** `Category` 為 `CategoryA` **或** `Priority` 為 1 的測試。</span><span class="sxs-lookup"><span data-stu-id="2fd44-142">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |
