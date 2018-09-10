---
title: 執行多樣化選擇的單元測試
description: 示範如何使用篩選運算式搭配 dotnet 測試命令執行多樣化選擇的單元測試。
author: smadala
ms.author: mairaw
ms.date: 03/22/2017
ms.openlocfilehash: 428e31014f5d8d487deb7c4b4317ebcef13c294d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517216"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="ceb46-103">執行多樣化選擇的單元測試</span><span class="sxs-lookup"><span data-stu-id="ceb46-103">Running selective unit tests</span></span>

<span data-ttu-id="ceb46-104">下列範例使用`dotnet test`。</span><span class="sxs-lookup"><span data-stu-id="ceb46-104">The following examples use `dotnet test`.</span></span> <span data-ttu-id="ceb46-105">若要使用`vstest.console.exe`，請以取代 `--testcasefilter:` 取代 `--filter `。</span><span class="sxs-lookup"><span data-stu-id="ceb46-105">If you're using `vstest.console.exe`, replace `--filter ` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="ceb46-106">MSTest</span><span class="sxs-lookup"><span data-stu-id="ceb46-106">MSTest</span></span>

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace MSTestNamespace
{
    [TestClass]
    public class UnitTest1
    {
        [TestCategory("CategoryA")]
        [Priority(1)]
        [TestMethod]
        public void TestMethod1()
        {
        }

        [Priority(2)]
        [TestMethod]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="ceb46-107">運算式</span><span class="sxs-lookup"><span data-stu-id="ceb46-107">Expression</span></span> | <span data-ttu-id="ceb46-108">結果</span><span class="sxs-lookup"><span data-stu-id="ceb46-108">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="ceb46-109">執行 `FullyQualifiedName` 包含 `Method` 的測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-109">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="ceb46-110">`vstest 15.1+` 提供此測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-110">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="ceb46-111">執行名稱包含 `TestMethod1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-111">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="ceb46-112">執行類別為 `MSTestNamespace.UnitTest1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-112">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="ceb46-113">**注意︰**`ClassName`值應會有命名空間，所以 `ClassName=UnitTest1` 將無法運作。</span><span class="sxs-lookup"><span data-stu-id="ceb46-113">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="ceb46-114">執行 `MSTestNamespace.UnitTest1.TestMethod1` 以外的所有測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-114">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="ceb46-115">執行標示有 `[TestCategory("CategoryA")]` 註釋的測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-115">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="ceb46-116">執行標示有 `[Priority(2)]` 註釋的測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-116">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="ceb46-117">**使用條件式運算子 | 與 &amp;**</span><span class="sxs-lookup"><span data-stu-id="ceb46-117">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="ceb46-118">運算式</span><span class="sxs-lookup"><span data-stu-id="ceb46-118">Expression</span></span> | <span data-ttu-id="ceb46-119">結果</span><span class="sxs-lookup"><span data-stu-id="ceb46-119">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="ceb46-120">執行 `FullyQualifiedName` **或** `TestCategory` 中之 `UnitTest1` 為 `CategoryA` 的測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-120">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="ceb46-121">執行 `FullyQualifiedName` **及** `TestCategory` 中之 `UnitTest1` 為 `CategoryA` 的測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-121">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="ceb46-122">執行 `FullyQualifiedName` 所含之 `UnitTest1` **及** `TestCategory` 為 `CategoryA` **或** `Priority` 為 1 的測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-122">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="ceb46-123">xUnit</span><span class="sxs-lookup"><span data-stu-id="ceb46-123">xUnit</span></span>

```csharp
using Xunit;

namespace XUnitNamespace
{
    public class TestClass1
    {
        [Trait("Category", "CategoryA")]
        [Trait("Priority", "1")]
        [Fact]
        public void Test1()
        {
        }

        [Trait("Priority", "2")]
        [Fact]
        public void Test2()
        {
        }
    }
}
```

| <span data-ttu-id="ceb46-124">運算式</span><span class="sxs-lookup"><span data-stu-id="ceb46-124">Expression</span></span> | <span data-ttu-id="ceb46-125">結果</span><span class="sxs-lookup"><span data-stu-id="ceb46-125">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="ceb46-126">僅執行 `XUnitNamespace.TestClass1.Test1` 這一項測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-126">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="ceb46-127">執行 `XUnitNamespace.TestClass1.Test1` 以外的所有測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-127">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="ceb46-128">執行顯示名稱包含 `TestClass1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-128">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="ceb46-129">在程式碼範例中，所定義具有索引鍵 `Category` 及 `Priority` 的特徵可用於篩選。</span><span class="sxs-lookup"><span data-stu-id="ceb46-129">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="ceb46-130">運算式</span><span class="sxs-lookup"><span data-stu-id="ceb46-130">Expression</span></span> | <span data-ttu-id="ceb46-131">結果</span><span class="sxs-lookup"><span data-stu-id="ceb46-131">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="ceb46-132">執行 `FullyQualifiedName` 包含 `XUnit` 的測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-132">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="ceb46-133">`vstest 15.1+` 提供此測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-133">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="ceb46-134">執行包含 `[Trait("Category", "CategoryA")]` 的測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-134">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="ceb46-135">**使用條件式運算子 | 與 &amp;**</span><span class="sxs-lookup"><span data-stu-id="ceb46-135">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="ceb46-136">運算式</span><span class="sxs-lookup"><span data-stu-id="ceb46-136">Expression</span></span> | <span data-ttu-id="ceb46-137">結果</span><span class="sxs-lookup"><span data-stu-id="ceb46-137">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="ceb46-138">執行 `FullyQualifiedName` **或** `Category` 中之 `TestClass1` 為 `CategoryA` 的測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-138">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="ceb46-139">執行 `FullyQualifiedName` **及** `Category` 中之 `TestClass1` 為 `CategoryA` 的測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-139">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="ceb46-140">執行 `FullyQualifiedName` 所含之 `TestClass1` **及** `Category` 為 `CategoryA` **或** `Priority` 為 1 的測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-140">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="ceb46-141">NUnit</span><span class="sxs-lookup"><span data-stu-id="ceb46-141">NUnit</span></span>

```csharp
using NUnit.Framework;

namespace NUnitNamespace
{
    public class UnitTest1
    {
        [Category("CategoryA")]
        [Property("Priority", 1)]
        [Test]
        public void TestMethod1()
        {
        }

        [Property("Priority", 2)]
        [Test]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="ceb46-142">運算式</span><span class="sxs-lookup"><span data-stu-id="ceb46-142">Expression</span></span> | <span data-ttu-id="ceb46-143">結果</span><span class="sxs-lookup"><span data-stu-id="ceb46-143">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="ceb46-144">執行 `FullyQualifiedName` 包含 `Method` 的測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-144">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="ceb46-145">`vstest 15.1+` 提供此測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-145">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="ceb46-146">執行名稱包含 `TestMethod1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-146">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="ceb46-147">執行類別為 `NUnitNamespace.UnitTest1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-147">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="ceb46-148">執行 `NUnitNamespace.UnitTest1.TestMethod1` 以外的所有測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-148">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="ceb46-149">執行標示有 `[Category("CategoryA")]` 註釋的測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-149">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="ceb46-150">執行標示有 `[Priority(2)]` 註釋的測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-150">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="ceb46-151">**使用條件式運算子 | 與 &amp;**</span><span class="sxs-lookup"><span data-stu-id="ceb46-151">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="ceb46-152">運算式</span><span class="sxs-lookup"><span data-stu-id="ceb46-152">Expression</span></span> | <span data-ttu-id="ceb46-153">結果</span><span class="sxs-lookup"><span data-stu-id="ceb46-153">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="ceb46-154">執行 `FullyQualifiedName` **或** `TestCategory` 中之 `UnitTest1` 為 `CategoryA` 的測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-154">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="ceb46-155">執行 `FullyQualifiedName` **及** `TestCategory` 中之 `UnitTest1` 為 `CategoryA` 的測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-155">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="ceb46-156">執行 `FullyQualifiedName` 所含之 `UnitTest1` **及** `TestCategory` 為 `CategoryA` **或** `Priority` 為 1 的測試。</span><span class="sxs-lookup"><span data-stu-id="ceb46-156">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |
