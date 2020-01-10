---
title: 執行多樣化選擇的單元測試
description: 如何在 .NET Core 中使用篩選運算式搭配 dotnet 測試命令執行多樣化選擇的單元測試。
author: smadala
ms.date: 03/22/2017
ms.openlocfilehash: 57428dad2de6c2507ca2cdc42e3df9e83a1edd69
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715452"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="2cce4-103">執行多樣化選擇的單元測試</span><span class="sxs-lookup"><span data-stu-id="2cce4-103">Running selective unit tests</span></span>

<span data-ttu-id="2cce4-104">透過 .NET Core 中的 `dotnet test` 命令，您可以使用篩選運算式來執行選擇性測試。</span><span class="sxs-lookup"><span data-stu-id="2cce4-104">With the `dotnet test` command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="2cce4-105">本文示範如何篩選所要執行的測試。</span><span class="sxs-lookup"><span data-stu-id="2cce4-105">This article demonstrates how to filter which test are run.</span></span> <span data-ttu-id="2cce4-106">下列範例使用`dotnet test`。</span><span class="sxs-lookup"><span data-stu-id="2cce4-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="2cce4-107">若要使用`vstest.console.exe`，請以取代 `--testcasefilter:` 取代 `--filter`。</span><span class="sxs-lookup"><span data-stu-id="2cce4-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="2cce4-108">MSTest</span><span class="sxs-lookup"><span data-stu-id="2cce4-108">MSTest</span></span>

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

| <span data-ttu-id="2cce4-109">運算式</span><span class="sxs-lookup"><span data-stu-id="2cce4-109">Expression</span></span> | <span data-ttu-id="2cce4-110">結果</span><span class="sxs-lookup"><span data-stu-id="2cce4-110">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="2cce4-111">執行 `FullyQualifiedName` 包含 `Method` 的測試。</span><span class="sxs-lookup"><span data-stu-id="2cce4-111">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="2cce4-112">`vstest 15.1+` 提供此測試。</span><span class="sxs-lookup"><span data-stu-id="2cce4-112">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="2cce4-113">執行名稱包含 `TestMethod1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="2cce4-113">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="2cce4-114">執行類別為 `MSTestNamespace.UnitTest1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="2cce4-114">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="2cce4-115">**注意︰** `ClassName`值應會有命名空間，所以 `ClassName=UnitTest1` 將無法運作。</span><span class="sxs-lookup"><span data-stu-id="2cce4-115">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="2cce4-116">執行 `MSTestNamespace.UnitTest1.TestMethod1` 以外的所有測試。</span><span class="sxs-lookup"><span data-stu-id="2cce4-116">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="2cce4-117">執行標示有 `[TestCategory("CategoryA")]` 註釋的測試。</span><span class="sxs-lookup"><span data-stu-id="2cce4-117">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="2cce4-118">執行標示有 `[Priority(2)]` 註釋的測試。</span><span class="sxs-lookup"><span data-stu-id="2cce4-118">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="2cce4-119">**使用條件式運算子 | 與 &amp;**</span><span class="sxs-lookup"><span data-stu-id="2cce4-119">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="2cce4-120">運算式</span><span class="sxs-lookup"><span data-stu-id="2cce4-120">Expression</span></span> | <span data-ttu-id="2cce4-121">結果</span><span class="sxs-lookup"><span data-stu-id="2cce4-121">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="2cce4-122">執行 `UnitTest1` 在 `FullyQualifiedName`**或**`TestCategory` `CategoryA`中的測試。</span><span class="sxs-lookup"><span data-stu-id="2cce4-122">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="2cce4-123">在 `FullyQualifiedName` 中執行具有 `UnitTest1` 的測試 **，並**`CategoryA``TestCategory`。</span><span class="sxs-lookup"><span data-stu-id="2cce4-123">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="2cce4-124">執行測試，其中包含 `UnitTest1` 的 `FullyQualifiedName` **，且**`TestCategory` `CategoryA`**或**`Priority` 為1。</span><span class="sxs-lookup"><span data-stu-id="2cce4-124">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="2cce4-125">xUnit</span><span class="sxs-lookup"><span data-stu-id="2cce4-125">xUnit</span></span>

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

| <span data-ttu-id="2cce4-126">運算式</span><span class="sxs-lookup"><span data-stu-id="2cce4-126">Expression</span></span> | <span data-ttu-id="2cce4-127">結果</span><span class="sxs-lookup"><span data-stu-id="2cce4-127">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="2cce4-128">僅執行 `XUnitNamespace.TestClass1.Test1` 這一項測試。</span><span class="sxs-lookup"><span data-stu-id="2cce4-128">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="2cce4-129">執行 `XUnitNamespace.TestClass1.Test1` 以外的所有測試。</span><span class="sxs-lookup"><span data-stu-id="2cce4-129">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="2cce4-130">執行顯示名稱包含 `TestClass1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="2cce4-130">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="2cce4-131">在程式碼範例中，所定義具有索引鍵 `Category` 及 `Priority` 的特徵可用於篩選。</span><span class="sxs-lookup"><span data-stu-id="2cce4-131">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="2cce4-132">運算式</span><span class="sxs-lookup"><span data-stu-id="2cce4-132">Expression</span></span> | <span data-ttu-id="2cce4-133">結果</span><span class="sxs-lookup"><span data-stu-id="2cce4-133">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="2cce4-134">執行 `FullyQualifiedName` 包含 `XUnit` 的測試。</span><span class="sxs-lookup"><span data-stu-id="2cce4-134">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="2cce4-135">`vstest 15.1+` 提供此測試。</span><span class="sxs-lookup"><span data-stu-id="2cce4-135">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="2cce4-136">執行包含 `[Trait("Category", "CategoryA")]` 的測試。</span><span class="sxs-lookup"><span data-stu-id="2cce4-136">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="2cce4-137">**使用條件式運算子 | 與 &amp;**</span><span class="sxs-lookup"><span data-stu-id="2cce4-137">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="2cce4-138">運算式</span><span class="sxs-lookup"><span data-stu-id="2cce4-138">Expression</span></span> | <span data-ttu-id="2cce4-139">結果</span><span class="sxs-lookup"><span data-stu-id="2cce4-139">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="2cce4-140">執行 `TestClass1` 在 `FullyQualifiedName`**或**`Category` `CategoryA`中的測試。</span><span class="sxs-lookup"><span data-stu-id="2cce4-140">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="2cce4-141">在 `FullyQualifiedName` 中執行具有 `TestClass1` 的測試 **，並**`CategoryA``Category`。</span><span class="sxs-lookup"><span data-stu-id="2cce4-141">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="2cce4-142">執行測試，其中包含 `TestClass1` 的 `FullyQualifiedName` **，且**`Category` `CategoryA`**或**`Priority` 為1。</span><span class="sxs-lookup"><span data-stu-id="2cce4-142">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="2cce4-143">NUnit</span><span class="sxs-lookup"><span data-stu-id="2cce4-143">NUnit</span></span>

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

| <span data-ttu-id="2cce4-144">運算式</span><span class="sxs-lookup"><span data-stu-id="2cce4-144">Expression</span></span> | <span data-ttu-id="2cce4-145">結果</span><span class="sxs-lookup"><span data-stu-id="2cce4-145">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="2cce4-146">執行 `FullyQualifiedName` 包含 `Method` 的測試。</span><span class="sxs-lookup"><span data-stu-id="2cce4-146">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="2cce4-147">`vstest 15.1+` 提供此測試。</span><span class="sxs-lookup"><span data-stu-id="2cce4-147">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="2cce4-148">執行名稱包含 `TestMethod1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="2cce4-148">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="2cce4-149">執行類別為 `NUnitNamespace.UnitTest1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="2cce4-149">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="2cce4-150">執行 `NUnitNamespace.UnitTest1.TestMethod1` 以外的所有測試。</span><span class="sxs-lookup"><span data-stu-id="2cce4-150">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="2cce4-151">執行標示有 `[Category("CategoryA")]` 註釋的測試。</span><span class="sxs-lookup"><span data-stu-id="2cce4-151">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="2cce4-152">執行標示有 `[Priority(2)]` 註釋的測試。</span><span class="sxs-lookup"><span data-stu-id="2cce4-152">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="2cce4-153">**使用條件式運算子 | 與 &amp;**</span><span class="sxs-lookup"><span data-stu-id="2cce4-153">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="2cce4-154">運算式</span><span class="sxs-lookup"><span data-stu-id="2cce4-154">Expression</span></span> | <span data-ttu-id="2cce4-155">結果</span><span class="sxs-lookup"><span data-stu-id="2cce4-155">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="2cce4-156">執行 `UnitTest1` 在 `FullyQualifiedName`**或**`TestCategory` `CategoryA`中的測試。</span><span class="sxs-lookup"><span data-stu-id="2cce4-156">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="2cce4-157">在 `FullyQualifiedName` 中執行具有 `UnitTest1` 的測試 **，並**`CategoryA``TestCategory`。</span><span class="sxs-lookup"><span data-stu-id="2cce4-157">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="2cce4-158">執行測試，其中包含 `UnitTest1` 的 `FullyQualifiedName` **，且**`TestCategory` `CategoryA`**或**`Priority` 為1。</span><span class="sxs-lookup"><span data-stu-id="2cce4-158">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |
