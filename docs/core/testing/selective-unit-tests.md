---
title: 執行多樣化選擇的單元測試
description: 如何在 .NET Core 中使用篩選運算式搭配 dotnet 測試命令執行多樣化選擇的單元測試。
author: smadala
ms.date: 04/29/2020
ms.openlocfilehash: 50642126f3b470180ddd303ed4a2d2d90bfa5b8f
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728186"
---
# <a name="run-selective-unit-tests"></a><span data-ttu-id="2de4e-103">執行選擇性單元測試</span><span class="sxs-lookup"><span data-stu-id="2de4e-103">Run selective unit tests</span></span>

<span data-ttu-id="2de4e-104">透過 .NET Core 中的 `dotnet test` 命令，您可以使用篩選運算式來執行選擇性測試。</span><span class="sxs-lookup"><span data-stu-id="2de4e-104">With the `dotnet test` command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="2de4e-105">本文示範如何篩選要執行的測試。</span><span class="sxs-lookup"><span data-stu-id="2de4e-105">This article demonstrates how to filter which tests are run.</span></span> <span data-ttu-id="2de4e-106">下列範例使用`dotnet test`。</span><span class="sxs-lookup"><span data-stu-id="2de4e-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="2de4e-107">若要使用`vstest.console.exe`，請以取代 `--testcasefilter:` 取代 `--filter`。</span><span class="sxs-lookup"><span data-stu-id="2de4e-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

## <a name="character-escaping"></a><span data-ttu-id="2de4e-108">字元轉義</span><span class="sxs-lookup"><span data-stu-id="2de4e-108">Character escaping</span></span>

<span data-ttu-id="2de4e-109">在上`*nix`使用包含驚嘆號（！）的篩選時，需要`!`進行轉義，因為是保留的。</span><span class="sxs-lookup"><span data-stu-id="2de4e-109">Using filters that include exclamation mark (!) on `*nix` requires escaping since `!` is reserved.</span></span> <span data-ttu-id="2de4e-110">例如，如果命名空間包含 IntegrationTests： `dotnet test --filter FullyQualifiedName\!~IntegrationTests`，則此篩選會略過所有測試。</span><span class="sxs-lookup"><span data-stu-id="2de4e-110">For example, this filter skips all tests if the namespace contains IntegrationTests: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.</span></span>
<span data-ttu-id="2de4e-111">請記下驚嘆號前面的反斜線。</span><span class="sxs-lookup"><span data-stu-id="2de4e-111">Note the backslash that precedes the exclamation mark.</span></span>

<span data-ttu-id="2de4e-112">對於`FullyQualifiedName`包含泛型型別參數之逗號的值，請使用來將`%2C`逗號換成。</span><span class="sxs-lookup"><span data-stu-id="2de4e-112">For `FullyQualifiedName` values that include a comma for generic type parameters, escape the comma with `%2C`.</span></span> <span data-ttu-id="2de4e-113">例如：</span><span class="sxs-lookup"><span data-stu-id="2de4e-113">For example:</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName=MyNamespace.MyTestsClass<ParameterType1%2CParameterType2>.MyTestMethod"
```

## <a name="mstest"></a><span data-ttu-id="2de4e-114">MSTest</span><span class="sxs-lookup"><span data-stu-id="2de4e-114">MSTest</span></span>

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

| <span data-ttu-id="2de4e-115">運算是</span><span class="sxs-lookup"><span data-stu-id="2de4e-115">Expression</span></span> | <span data-ttu-id="2de4e-116">結果</span><span class="sxs-lookup"><span data-stu-id="2de4e-116">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="2de4e-117">執行 `FullyQualifiedName` 包含 `Method` 的測試。</span><span class="sxs-lookup"><span data-stu-id="2de4e-117">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="2de4e-118">`vstest 15.1+` 提供此測試。</span><span class="sxs-lookup"><span data-stu-id="2de4e-118">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="2de4e-119">執行名稱包含 `TestMethod1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="2de4e-119">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="2de4e-120">執行類別`MSTestNamespace.UnitTest1`中的測試。</span><span class="sxs-lookup"><span data-stu-id="2de4e-120">Runs tests that are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="2de4e-121">**注意︰**`ClassName`值應會有命名空間，所以 `ClassName=UnitTest1` 將無法運作。</span><span class="sxs-lookup"><span data-stu-id="2de4e-121">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="2de4e-122">執行 `MSTestNamespace.UnitTest1.TestMethod1` 以外的所有測試。</span><span class="sxs-lookup"><span data-stu-id="2de4e-122">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="2de4e-123">執行以`[TestCategory("CategoryA")]`標注的測試。</span><span class="sxs-lookup"><span data-stu-id="2de4e-123">Runs tests that are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="2de4e-124">執行以`[Priority(2)]`標注的測試。</span><span class="sxs-lookup"><span data-stu-id="2de4e-124">Runs tests that are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="2de4e-125">**使用條件式運算子 | 與 &amp;**</span><span class="sxs-lookup"><span data-stu-id="2de4e-125">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="2de4e-126">運算是</span><span class="sxs-lookup"><span data-stu-id="2de4e-126">Expression</span></span> | <span data-ttu-id="2de4e-127">結果</span><span class="sxs-lookup"><span data-stu-id="2de4e-127">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="2de4e-128">`UnitTest1`執行中`FullyQualifiedName`具有**或** `TestCategory`的測試。 `CategoryA`</span><span class="sxs-lookup"><span data-stu-id="2de4e-128">Runs tests that have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="2de4e-129">`UnitTest1`執行中`FullyQualifiedName`的測試，**且** `TestCategory`為`CategoryA`。</span><span class="sxs-lookup"><span data-stu-id="2de4e-129">Runs tests that have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="2de4e-130">執行`FullyQualifiedName`包含`UnitTest1` **且** `TestCategory`為`CategoryA` **or**或`Priority`為1的測試。</span><span class="sxs-lookup"><span data-stu-id="2de4e-130">Runs tests that have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="2de4e-131">xUnit</span><span class="sxs-lookup"><span data-stu-id="2de4e-131">xUnit</span></span>

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

| <span data-ttu-id="2de4e-132">運算是</span><span class="sxs-lookup"><span data-stu-id="2de4e-132">Expression</span></span> | <span data-ttu-id="2de4e-133">結果</span><span class="sxs-lookup"><span data-stu-id="2de4e-133">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="2de4e-134">僅執行 `XUnitNamespace.TestClass1.Test1` 這一項測試。</span><span class="sxs-lookup"><span data-stu-id="2de4e-134">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="2de4e-135">執行 `XUnitNamespace.TestClass1.Test1` 以外的所有測試。</span><span class="sxs-lookup"><span data-stu-id="2de4e-135">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="2de4e-136">執行顯示名稱包含 `TestClass1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="2de4e-136">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="2de4e-137">在程式碼範例中，所定義具有索引鍵 `Category` 及 `Priority` 的特徵可用於篩選。</span><span class="sxs-lookup"><span data-stu-id="2de4e-137">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="2de4e-138">運算是</span><span class="sxs-lookup"><span data-stu-id="2de4e-138">Expression</span></span> | <span data-ttu-id="2de4e-139">結果</span><span class="sxs-lookup"><span data-stu-id="2de4e-139">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="2de4e-140">執行 `FullyQualifiedName` 包含 `XUnit` 的測試。</span><span class="sxs-lookup"><span data-stu-id="2de4e-140">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="2de4e-141">`vstest 15.1+` 提供此測試。</span><span class="sxs-lookup"><span data-stu-id="2de4e-141">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="2de4e-142">執行具有`[Trait("Category", "CategoryA")]`的測試。</span><span class="sxs-lookup"><span data-stu-id="2de4e-142">Runs tests that have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="2de4e-143">**使用條件式運算子 | 與 &amp;**</span><span class="sxs-lookup"><span data-stu-id="2de4e-143">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="2de4e-144">運算是</span><span class="sxs-lookup"><span data-stu-id="2de4e-144">Expression</span></span> | <span data-ttu-id="2de4e-145">結果</span><span class="sxs-lookup"><span data-stu-id="2de4e-145">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="2de4e-146">`TestClass1`執行中`FullyQualifiedName`具有**或** `Category`的測試。 `CategoryA`</span><span class="sxs-lookup"><span data-stu-id="2de4e-146">Runs tests that have `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="2de4e-147">`TestClass1`執行中`FullyQualifiedName`的測試，**且** `Category`為`CategoryA`。</span><span class="sxs-lookup"><span data-stu-id="2de4e-147">Runs tests that have `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="2de4e-148">執行`FullyQualifiedName`包含`TestClass1` **且** `Category`為`CategoryA` **or**或`Priority`為1的測試。</span><span class="sxs-lookup"><span data-stu-id="2de4e-148">Runs tests that have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="2de4e-149">NUnit</span><span class="sxs-lookup"><span data-stu-id="2de4e-149">NUnit</span></span>

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

| <span data-ttu-id="2de4e-150">運算是</span><span class="sxs-lookup"><span data-stu-id="2de4e-150">Expression</span></span> | <span data-ttu-id="2de4e-151">結果</span><span class="sxs-lookup"><span data-stu-id="2de4e-151">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="2de4e-152">執行 `FullyQualifiedName` 包含 `Method` 的測試。</span><span class="sxs-lookup"><span data-stu-id="2de4e-152">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="2de4e-153">`vstest 15.1+` 提供此測試。</span><span class="sxs-lookup"><span data-stu-id="2de4e-153">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="2de4e-154">執行名稱包含 `TestMethod1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="2de4e-154">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="2de4e-155">執行類別`NUnitNamespace.UnitTest1`中的測試。</span><span class="sxs-lookup"><span data-stu-id="2de4e-155">Runs tests that are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="2de4e-156">執行 `NUnitNamespace.UnitTest1.TestMethod1` 以外的所有測試。</span><span class="sxs-lookup"><span data-stu-id="2de4e-156">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="2de4e-157">執行以`[Category("CategoryA")]`標注的測試。</span><span class="sxs-lookup"><span data-stu-id="2de4e-157">Runs tests that are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="2de4e-158">執行以`[Priority(2)]`標注的測試。</span><span class="sxs-lookup"><span data-stu-id="2de4e-158">Runs tests that are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="2de4e-159">**使用條件式運算子 | 與 &amp;**</span><span class="sxs-lookup"><span data-stu-id="2de4e-159">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="2de4e-160">運算是</span><span class="sxs-lookup"><span data-stu-id="2de4e-160">Expression</span></span> | <span data-ttu-id="2de4e-161">結果</span><span class="sxs-lookup"><span data-stu-id="2de4e-161">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="2de4e-162">`UnitTest1`執行中`FullyQualifiedName`具有**或** `TestCategory`的測試。 `CategoryA`</span><span class="sxs-lookup"><span data-stu-id="2de4e-162">Runs tests that have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="2de4e-163">`UnitTest1`執行中`FullyQualifiedName`的測試，**且** `TestCategory`為`CategoryA`。</span><span class="sxs-lookup"><span data-stu-id="2de4e-163">Runs tests that have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="2de4e-164">執行`FullyQualifiedName`包含`UnitTest1` **且** `TestCategory`為`CategoryA` **or**或`Priority`為1的測試。</span><span class="sxs-lookup"><span data-stu-id="2de4e-164">Runs tests that have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

<span data-ttu-id="2de4e-165">如需詳細資訊，請參閱[TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md)。</span><span class="sxs-lookup"><span data-stu-id="2de4e-165">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>
