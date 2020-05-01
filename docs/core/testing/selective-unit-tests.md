---
title: 執行多樣化選擇的單元測試
description: 如何在 .NET Core 中使用篩選運算式搭配 dotnet 測試命令執行多樣化選擇的單元測試。
author: smadala
ms.date: 04/29/2020
ms.openlocfilehash: e66455b5ac012114c45d998fae11da7ee769fbe2
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624913"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="d6553-103">執行多樣化選擇的單元測試</span><span class="sxs-lookup"><span data-stu-id="d6553-103">Running selective unit tests</span></span>

<span data-ttu-id="d6553-104">透過 .NET Core 中的 `dotnet test` 命令，您可以使用篩選運算式來執行選擇性測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-104">With the `dotnet test` command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="d6553-105">本文示範如何篩選所要執行的測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-105">This article demonstrates how to filter which test are run.</span></span> <span data-ttu-id="d6553-106">下列範例使用`dotnet test`。</span><span class="sxs-lookup"><span data-stu-id="d6553-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="d6553-107">若要使用`vstest.console.exe`，請以取代 `--testcasefilter:` 取代 `--filter`。</span><span class="sxs-lookup"><span data-stu-id="d6553-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

## <a name="character-escaping"></a><span data-ttu-id="d6553-108">字元轉義</span><span class="sxs-lookup"><span data-stu-id="d6553-108">Character escaping</span></span>

<span data-ttu-id="d6553-109">在上`*nix`使用包含驚嘆號（！）的篩選時，需要`!`進行轉義，因為是保留的。</span><span class="sxs-lookup"><span data-stu-id="d6553-109">Using filters that include exclamation mark (!) on `*nix` requires escaping since `!` is reserved.</span></span> <span data-ttu-id="d6553-110">例如，如果命名空間包含 IntegrationTests： `dotnet test --filter FullyQualifiedName\!~IntegrationTests`，則此篩選會略過所有測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-110">For example, this filter skips all tests if the namespace contains IntegrationTests: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.</span></span>
<span data-ttu-id="d6553-111">請記下驚嘆號前面的反斜線。</span><span class="sxs-lookup"><span data-stu-id="d6553-111">Note the backslash that precedes the exclamation mark.</span></span>

<span data-ttu-id="d6553-112">對於`FullyQualifiedName`包含泛型型別參數之逗號的值，請使用來將`%2C`逗號換成。</span><span class="sxs-lookup"><span data-stu-id="d6553-112">For `FullyQualifiedName` values that include a comma for generic type parameters, escape the comma with `%2C`.</span></span> <span data-ttu-id="d6553-113">例如：</span><span class="sxs-lookup"><span data-stu-id="d6553-113">For example:</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName=MyNamespace.MyTestsClass<ParameterType1%2CParameterType2>.MyTestMethod"
```

## <a name="mstest"></a><span data-ttu-id="d6553-114">MSTest</span><span class="sxs-lookup"><span data-stu-id="d6553-114">MSTest</span></span>

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

| <span data-ttu-id="d6553-115">運算是</span><span class="sxs-lookup"><span data-stu-id="d6553-115">Expression</span></span> | <span data-ttu-id="d6553-116">結果</span><span class="sxs-lookup"><span data-stu-id="d6553-116">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="d6553-117">執行 `FullyQualifiedName` 包含 `Method` 的測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-117">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="d6553-118">`vstest 15.1+` 提供此測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-118">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="d6553-119">執行名稱包含 `TestMethod1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-119">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="d6553-120">執行類別為 `MSTestNamespace.UnitTest1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-120">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="d6553-121">**注意︰**`ClassName`值應會有命名空間，所以 `ClassName=UnitTest1` 將無法運作。</span><span class="sxs-lookup"><span data-stu-id="d6553-121">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="d6553-122">執行 `MSTestNamespace.UnitTest1.TestMethod1` 以外的所有測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-122">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="d6553-123">執行標示有 `[TestCategory("CategoryA")]` 註釋的測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-123">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="d6553-124">執行標示有 `[Priority(2)]` 註釋的測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-124">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="d6553-125">**使用條件式運算子 | 與 &amp;**</span><span class="sxs-lookup"><span data-stu-id="d6553-125">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="d6553-126">運算是</span><span class="sxs-lookup"><span data-stu-id="d6553-126">Expression</span></span> | <span data-ttu-id="d6553-127">結果</span><span class="sxs-lookup"><span data-stu-id="d6553-127">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="d6553-128">執行 `FullyQualifiedName` **或** `TestCategory` 中之 `UnitTest1` 為 `CategoryA` 的測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-128">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="d6553-129">執行 `FullyQualifiedName` **及** `TestCategory` 中之 `UnitTest1` 為 `CategoryA` 的測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-129">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="d6553-130">執行 `FullyQualifiedName` 所含之 `UnitTest1` **及** `TestCategory` 為 `CategoryA` **或** `Priority` 為 1 的測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-130">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="d6553-131">xUnit</span><span class="sxs-lookup"><span data-stu-id="d6553-131">xUnit</span></span>

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

| <span data-ttu-id="d6553-132">運算是</span><span class="sxs-lookup"><span data-stu-id="d6553-132">Expression</span></span> | <span data-ttu-id="d6553-133">結果</span><span class="sxs-lookup"><span data-stu-id="d6553-133">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="d6553-134">僅執行 `XUnitNamespace.TestClass1.Test1` 這一項測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-134">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="d6553-135">執行 `XUnitNamespace.TestClass1.Test1` 以外的所有測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-135">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="d6553-136">執行顯示名稱包含 `TestClass1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-136">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="d6553-137">在程式碼範例中，所定義具有索引鍵 `Category` 及 `Priority` 的特徵可用於篩選。</span><span class="sxs-lookup"><span data-stu-id="d6553-137">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="d6553-138">運算是</span><span class="sxs-lookup"><span data-stu-id="d6553-138">Expression</span></span> | <span data-ttu-id="d6553-139">結果</span><span class="sxs-lookup"><span data-stu-id="d6553-139">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="d6553-140">執行 `FullyQualifiedName` 包含 `XUnit` 的測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-140">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="d6553-141">`vstest 15.1+` 提供此測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-141">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="d6553-142">執行包含 `[Trait("Category", "CategoryA")]` 的測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-142">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="d6553-143">**使用條件式運算子 | 與 &amp;**</span><span class="sxs-lookup"><span data-stu-id="d6553-143">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="d6553-144">運算是</span><span class="sxs-lookup"><span data-stu-id="d6553-144">Expression</span></span> | <span data-ttu-id="d6553-145">結果</span><span class="sxs-lookup"><span data-stu-id="d6553-145">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="d6553-146">執行 `FullyQualifiedName` **或** `Category` 中之 `TestClass1` 為 `CategoryA` 的測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-146">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="d6553-147">執行 `FullyQualifiedName` **及** `Category` 中之 `TestClass1` 為 `CategoryA` 的測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-147">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="d6553-148">執行 `FullyQualifiedName` 所含之 `TestClass1` **及** `Category` 為 `CategoryA` **或** `Priority` 為 1 的測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-148">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="d6553-149">NUnit</span><span class="sxs-lookup"><span data-stu-id="d6553-149">NUnit</span></span>

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

| <span data-ttu-id="d6553-150">運算是</span><span class="sxs-lookup"><span data-stu-id="d6553-150">Expression</span></span> | <span data-ttu-id="d6553-151">結果</span><span class="sxs-lookup"><span data-stu-id="d6553-151">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="d6553-152">執行 `FullyQualifiedName` 包含 `Method` 的測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-152">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="d6553-153">`vstest 15.1+` 提供此測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-153">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="d6553-154">執行名稱包含 `TestMethod1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-154">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="d6553-155">執行類別為 `NUnitNamespace.UnitTest1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-155">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="d6553-156">執行 `NUnitNamespace.UnitTest1.TestMethod1` 以外的所有測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-156">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="d6553-157">執行標示有 `[Category("CategoryA")]` 註釋的測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-157">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="d6553-158">執行標示有 `[Priority(2)]` 註釋的測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-158">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="d6553-159">**使用條件式運算子 | 與 &amp;**</span><span class="sxs-lookup"><span data-stu-id="d6553-159">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="d6553-160">運算是</span><span class="sxs-lookup"><span data-stu-id="d6553-160">Expression</span></span> | <span data-ttu-id="d6553-161">結果</span><span class="sxs-lookup"><span data-stu-id="d6553-161">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="d6553-162">執行 `FullyQualifiedName` **或** `TestCategory` 中之 `UnitTest1` 為 `CategoryA` 的測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-162">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="d6553-163">執行 `FullyQualifiedName` **及** `TestCategory` 中之 `UnitTest1` 為 `CategoryA` 的測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-163">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="d6553-164">執行 `FullyQualifiedName` 所含之 `UnitTest1` **及** `TestCategory` 為 `CategoryA` **或** `Priority` 為 1 的測試。</span><span class="sxs-lookup"><span data-stu-id="d6553-164">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

<span data-ttu-id="d6553-165">如需詳細資訊，請參閱[TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md)。</span><span class="sxs-lookup"><span data-stu-id="d6553-165">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>
