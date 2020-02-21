---
title: 執行多樣化選擇的單元測試
description: 如何在 .NET Core 中使用篩選運算式搭配 dotnet 測試命令執行多樣化選擇的單元測試。
author: smadala
ms.date: 03/22/2017
ms.openlocfilehash: b9156300587215e68c01c609e298dbc1a2c53d11
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543504"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="e4cf1-103">執行多樣化選擇的單元測試</span><span class="sxs-lookup"><span data-stu-id="e4cf1-103">Running selective unit tests</span></span>

<span data-ttu-id="e4cf1-104">透過 .NET Core 中的 `dotnet test` 命令，您可以使用篩選運算式來執行選擇性測試。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-104">With the `dotnet test` command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="e4cf1-105">本文示範如何篩選所要執行的測試。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-105">This article demonstrates how to filter which test are run.</span></span> <span data-ttu-id="e4cf1-106">下列範例使用`dotnet test`。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="e4cf1-107">若要使用`vstest.console.exe`，請以取代 `--filter` 取代 `--testcasefilter:`。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

> [!NOTE]
> <span data-ttu-id="e4cf1-108">在 `*nix` 上使用包含驚嘆號（！）的篩選需要進行轉義，因為 `!` 是保留的。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-108">Using filters that include exclamation mark (!) on `*nix` requires escaping since `!` is reserved.</span></span> <span data-ttu-id="e4cf1-109">例如，如果命名空間包含 IntegrationTests： `dotnet test --filter FullyQualifiedName\!~IntegrationTests`，此篩選會略過所有測試。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-109">For example, this filter skips all tests if the namespace contains IntegrationTests: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.</span></span>
> <span data-ttu-id="e4cf1-110">請記下驚嘆號前面的反斜線。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-110">Note the backslash that precedes the exclamation mark.</span></span>

## <a name="mstest"></a><span data-ttu-id="e4cf1-111">MSTest</span><span class="sxs-lookup"><span data-stu-id="e4cf1-111">MSTest</span></span>

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

| <span data-ttu-id="e4cf1-112">運算是</span><span class="sxs-lookup"><span data-stu-id="e4cf1-112">Expression</span></span> | <span data-ttu-id="e4cf1-113">結果</span><span class="sxs-lookup"><span data-stu-id="e4cf1-113">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="e4cf1-114">執行 `FullyQualifiedName` 包含 `Method` 的測試。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-114">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="e4cf1-115">`vstest 15.1+` 提供此測試。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-115">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="e4cf1-116">執行名稱包含 `TestMethod1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-116">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="e4cf1-117">執行類別為 `MSTestNamespace.UnitTest1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-117">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="e4cf1-118">**注意︰** `ClassName`值應會有命名空間，所以 `ClassName=UnitTest1` 將無法運作。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-118">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="e4cf1-119">執行 `MSTestNamespace.UnitTest1.TestMethod1` 以外的所有測試。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-119">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="e4cf1-120">執行標示有 `[TestCategory("CategoryA")]` 註釋的測試。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-120">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="e4cf1-121">執行標示有 `[Priority(2)]` 註釋的測試。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-121">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="e4cf1-122">**使用條件式運算子 | 與 &amp;**</span><span class="sxs-lookup"><span data-stu-id="e4cf1-122">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="e4cf1-123">運算是</span><span class="sxs-lookup"><span data-stu-id="e4cf1-123">Expression</span></span> | <span data-ttu-id="e4cf1-124">結果</span><span class="sxs-lookup"><span data-stu-id="e4cf1-124">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="e4cf1-125">執行 `UnitTest1` 在 `FullyQualifiedName`**或**`TestCategory` `CategoryA`中的測試。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-125">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="e4cf1-126">在 `FullyQualifiedName` 中執行具有 `UnitTest1` 的測試 **，並**`CategoryA``TestCategory`。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-126">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="e4cf1-127">執行測試，其中包含 `UnitTest1` 的 `FullyQualifiedName` **，且**`TestCategory` `CategoryA`**或**`Priority` 為1。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-127">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="e4cf1-128">xUnit</span><span class="sxs-lookup"><span data-stu-id="e4cf1-128">xUnit</span></span>

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

| <span data-ttu-id="e4cf1-129">運算是</span><span class="sxs-lookup"><span data-stu-id="e4cf1-129">Expression</span></span> | <span data-ttu-id="e4cf1-130">結果</span><span class="sxs-lookup"><span data-stu-id="e4cf1-130">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="e4cf1-131">僅執行 `XUnitNamespace.TestClass1.Test1` 這一項測試。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-131">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="e4cf1-132">執行 `XUnitNamespace.TestClass1.Test1` 以外的所有測試。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-132">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="e4cf1-133">執行顯示名稱包含 `TestClass1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-133">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="e4cf1-134">在程式碼範例中，所定義具有索引鍵 `Category` 及 `Priority` 的特徵可用於篩選。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-134">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="e4cf1-135">運算是</span><span class="sxs-lookup"><span data-stu-id="e4cf1-135">Expression</span></span> | <span data-ttu-id="e4cf1-136">結果</span><span class="sxs-lookup"><span data-stu-id="e4cf1-136">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="e4cf1-137">執行 `FullyQualifiedName` 包含 `XUnit` 的測試。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-137">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="e4cf1-138">`vstest 15.1+` 提供此測試。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-138">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="e4cf1-139">執行包含 `[Trait("Category", "CategoryA")]` 的測試。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-139">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="e4cf1-140">**使用條件式運算子 | 與 &amp;**</span><span class="sxs-lookup"><span data-stu-id="e4cf1-140">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="e4cf1-141">運算是</span><span class="sxs-lookup"><span data-stu-id="e4cf1-141">Expression</span></span> | <span data-ttu-id="e4cf1-142">結果</span><span class="sxs-lookup"><span data-stu-id="e4cf1-142">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="e4cf1-143">執行 `TestClass1` 在 `FullyQualifiedName`**或**`Category` `CategoryA`中的測試。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-143">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="e4cf1-144">在 `FullyQualifiedName` 中執行具有 `TestClass1` 的測試 **，並**`CategoryA``Category`。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-144">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="e4cf1-145">執行測試，其中包含 `TestClass1` 的 `FullyQualifiedName` **，且**`Category` `CategoryA`**或**`Priority` 為1。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-145">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="e4cf1-146">NUnit</span><span class="sxs-lookup"><span data-stu-id="e4cf1-146">NUnit</span></span>

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

| <span data-ttu-id="e4cf1-147">運算是</span><span class="sxs-lookup"><span data-stu-id="e4cf1-147">Expression</span></span> | <span data-ttu-id="e4cf1-148">結果</span><span class="sxs-lookup"><span data-stu-id="e4cf1-148">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="e4cf1-149">執行 `FullyQualifiedName` 包含 `Method` 的測試。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-149">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="e4cf1-150">`vstest 15.1+` 提供此測試。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-150">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="e4cf1-151">執行名稱包含 `TestMethod1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-151">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="e4cf1-152">執行類別為 `NUnitNamespace.UnitTest1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-152">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="e4cf1-153">執行 `NUnitNamespace.UnitTest1.TestMethod1` 以外的所有測試。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-153">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="e4cf1-154">執行標示有 `[Category("CategoryA")]` 註釋的測試。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-154">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="e4cf1-155">執行標示有 `[Priority(2)]` 註釋的測試。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-155">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="e4cf1-156">**使用條件式運算子 | 與 &amp;**</span><span class="sxs-lookup"><span data-stu-id="e4cf1-156">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="e4cf1-157">運算是</span><span class="sxs-lookup"><span data-stu-id="e4cf1-157">Expression</span></span> | <span data-ttu-id="e4cf1-158">結果</span><span class="sxs-lookup"><span data-stu-id="e4cf1-158">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="e4cf1-159">執行 `UnitTest1` 在 `FullyQualifiedName`**或**`TestCategory` `CategoryA`中的測試。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-159">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="e4cf1-160">在 `FullyQualifiedName` 中執行具有 `UnitTest1` 的測試 **，並**`CategoryA``TestCategory`。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-160">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="e4cf1-161">執行測試，其中包含 `UnitTest1` 的 `FullyQualifiedName` **，且**`TestCategory` `CategoryA`**或**`Priority` 為1。</span><span class="sxs-lookup"><span data-stu-id="e4cf1-161">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |
