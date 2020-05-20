---
title: 執行選擇性單元測試
description: 如何在 .NET Core 中使用篩選運算式搭配 dotnet 測試命令執行多樣化選擇的單元測試。
author: smadala
ms.date: 05/18/2020
zone_pivot_groups: unit-testing-framework-set-one
ms.openlocfilehash: 6a6bbb0687742d1e3288d64fb88f6825dc678e28
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702988"
---
# <a name="run-selective-unit-tests"></a><span data-ttu-id="01586-103">執行選擇性單元測試</span><span class="sxs-lookup"><span data-stu-id="01586-103">Run selective unit tests</span></span>

<span data-ttu-id="01586-104">使用 [`dotnet test`](../tools/dotnet-test.md) .Net Core 中的命令，您可以使用篩選運算式來執行選擇性測試。</span><span class="sxs-lookup"><span data-stu-id="01586-104">With the [`dotnet test`](../tools/dotnet-test.md) command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="01586-105">本文示範如何篩選要執行的測試。</span><span class="sxs-lookup"><span data-stu-id="01586-105">This article demonstrates how to filter which tests are run.</span></span> <span data-ttu-id="01586-106">下列範例使用`dotnet test`。</span><span class="sxs-lookup"><span data-stu-id="01586-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="01586-107">若要使用`vstest.console.exe`，請以取代 `--testcasefilter:` 取代 `--filter`。</span><span class="sxs-lookup"><span data-stu-id="01586-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

## <a name="character-escaping"></a><span data-ttu-id="01586-108">字元轉義</span><span class="sxs-lookup"><span data-stu-id="01586-108">Character escaping</span></span>

<span data-ttu-id="01586-109">使用包含驚嘆號的篩選準則 `!` `*nix` 時，需要進行轉義，因為 `!` 是保留的。</span><span class="sxs-lookup"><span data-stu-id="01586-109">Using filters that include exclamation mark `!` on `*nix` requires escaping since `!` is reserved.</span></span> <span data-ttu-id="01586-110">例如，如果命名空間包含 IntegrationTests，此篩選會略過所有測試：</span><span class="sxs-lookup"><span data-stu-id="01586-110">For example, this filter skips all tests if the namespace contains IntegrationTests:</span></span>

```dotnetcli
dotnet test --filter FullyQualifiedName\!~IntegrationTests
```

> [!IMPORTANT]
> <span data-ttu-id="01586-111">反斜線的前面會加上驚嘆號，表示它是一個逸出字元 `\!` 。</span><span class="sxs-lookup"><span data-stu-id="01586-111">The backslash precedes the exclamation mark to indicate it is an escaped character `\!`.</span></span>

<span data-ttu-id="01586-112">對於 `FullyQualifiedName` 包含泛型型別參數之逗號的值，請使用來將逗號換成 `%2C` 。</span><span class="sxs-lookup"><span data-stu-id="01586-112">For `FullyQualifiedName` values that include a comma for generic type parameters, escape the comma with `%2C`.</span></span> <span data-ttu-id="01586-113">例如：</span><span class="sxs-lookup"><span data-stu-id="01586-113">For example:</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName=MyNamespace.MyTestsClass<ParameterType1%2CParameterType2>.MyTestMethod"
```

:::zone pivot="mstest"

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace MSTestNamespace
{
    [TestClass]
    public class UnitTest1
    {
        [TestMethod, Priority(1), TestCategory("CategoryA")]
        public void TestMethod1()
        {
        }

        [TestMethod, Priority(2)]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="01586-114">運算式</span><span class="sxs-lookup"><span data-stu-id="01586-114">Expression</span></span> | <span data-ttu-id="01586-115">結果</span><span class="sxs-lookup"><span data-stu-id="01586-115">Result</span></span> |
|--|--|
| `dotnet test --filter Method` | <span data-ttu-id="01586-116">執行 <xref:System.Reflection.Module.FullyQualifiedName> 包含 `Method` 的測試。</span><span class="sxs-lookup"><span data-stu-id="01586-116">Runs tests whose <xref:System.Reflection.Module.FullyQualifiedName> contains `Method`.</span></span> <span data-ttu-id="01586-117">`vstest 15.1+` 提供此測試。</span><span class="sxs-lookup"><span data-stu-id="01586-117">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="01586-118">執行名稱包含 `TestMethod1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="01586-118">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="01586-119">執行類別中的測試 `MSTestNamespace.UnitTest1` 。</span><span class="sxs-lookup"><span data-stu-id="01586-119">Runs tests that are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="01586-120">**注意︰**`ClassName`值應會有命名空間，所以 `ClassName=UnitTest1` 將無法運作。</span><span class="sxs-lookup"><span data-stu-id="01586-120">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="01586-121">執行 `MSTestNamespace.UnitTest1.TestMethod1` 以外的所有測試。</span><span class="sxs-lookup"><span data-stu-id="01586-121">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="01586-122">執行以標注的測試 `[TestCategory("CategoryA")]` 。</span><span class="sxs-lookup"><span data-stu-id="01586-122">Runs tests that are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="01586-123">執行以標注的測試 `[Priority(2)]` 。</span><span class="sxs-lookup"><span data-stu-id="01586-123">Runs tests that are annotated with `[Priority(2)]`.</span></span> |

<span data-ttu-id="01586-124">使用條件運算子和的 `|` 範例 `&` ：</span><span class="sxs-lookup"><span data-stu-id="01586-124">Examples using the conditional operators `|` and `&`:</span></span>

<span data-ttu-id="01586-125">若要 `UnitTest1` 在 <xref:System.Reflection.Module.FullyQualifiedName> **或**中執行具有的測試 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> `"CategoryA"` 。</span><span class="sxs-lookup"><span data-stu-id="01586-125">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **or** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> is `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

<span data-ttu-id="01586-126">執行中具有的測試， `UnitTest1` <xref:System.Reflection.Module.FullyQualifiedName> **並**具有 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> 的 `"CategoryA"` 。</span><span class="sxs-lookup"><span data-stu-id="01586-126">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **and** have a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

<span data-ttu-id="01586-127">若要執行的測試 <xref:System.Reflection.Module.FullyQualifiedName> 包含 `UnitTest1` **，而且**具有 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> 的， `"CategoryA"` **或**具有的 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute> 優先順序為 `1` 。</span><span class="sxs-lookup"><span data-stu-id="01586-127">To run tests that have either <xref:System.Reflection.Module.FullyQualifiedName> containing `UnitTest1` **and** have a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> of `"CategoryA"` **or** have a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute> with a priority of `1`.</span></span>

```dotnetcli
dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)|Priority=1"
```

:::zone-end
:::zone pivot="xunit"

```csharp
using Xunit;

namespace XUnitNamespace
{
    public class TestClass1
    {
        [Fact, Trait("Priority", "1"), Trait("Category", "CategoryA")]
        public void Test1()
        {
        }

        [Fact, Trait("Priority", "2")]
        public void Test2()
        {
        }
    }
}
```

| <span data-ttu-id="01586-128">運算式</span><span class="sxs-lookup"><span data-stu-id="01586-128">Expression</span></span> | <span data-ttu-id="01586-129">結果</span><span class="sxs-lookup"><span data-stu-id="01586-129">Result</span></span> |
|--|--|
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="01586-130">僅執行 `XUnitNamespace.TestClass1.Test1` 這一項測試。</span><span class="sxs-lookup"><span data-stu-id="01586-130">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="01586-131">執行 `XUnitNamespace.TestClass1.Test1` 以外的所有測試。</span><span class="sxs-lookup"><span data-stu-id="01586-131">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="01586-132">執行顯示名稱包含 `TestClass1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="01586-132">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="01586-133">在程式碼範例中，所定義具有索引鍵 `"Category"` 及 `"Priority"` 的特徵可用於篩選。</span><span class="sxs-lookup"><span data-stu-id="01586-133">In the code example, the defined traits with keys `"Category"` and `"Priority"` can be used for filtering.</span></span>

| <span data-ttu-id="01586-134">運算式</span><span class="sxs-lookup"><span data-stu-id="01586-134">Expression</span></span> | <span data-ttu-id="01586-135">結果</span><span class="sxs-lookup"><span data-stu-id="01586-135">Result</span></span> |
|--|--|
| `dotnet test --filter XUnit` | <span data-ttu-id="01586-136">執行 <xref:System.Reflection.Module.FullyQualifiedName> 包含 `XUnit` 的測試。</span><span class="sxs-lookup"><span data-stu-id="01586-136">Runs tests whose <xref:System.Reflection.Module.FullyQualifiedName> contains `XUnit`.</span></span>  <span data-ttu-id="01586-137">`vstest 15.1+` 提供此測試。</span><span class="sxs-lookup"><span data-stu-id="01586-137">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="01586-138">執行具有的測試 `[Trait("Category", "CategoryA")]` 。</span><span class="sxs-lookup"><span data-stu-id="01586-138">Runs tests that have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="01586-139">使用條件運算子和的 `|` 範例 `&` ：</span><span class="sxs-lookup"><span data-stu-id="01586-139">Examples using the conditional operators `|` and `&`:</span></span>

<span data-ttu-id="01586-140">若要執行 `TestClass1` 在其或中具有索引 <xref:System.Reflection.Module.FullyQualifiedName> **or** `Trait` 鍵為 `"Category"` 且值為的測試 `"CategoryA"` 。</span><span class="sxs-lookup"><span data-stu-id="01586-140">To run tests that have `TestClass1` in their <xref:System.Reflection.Module.FullyQualifiedName> **or** have a `Trait` with a key of `"Category"` and value of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1|Category=CategoryA"
```

<span data-ttu-id="01586-141">若要在其中執行具有的測試， `TestClass1` <xref:System.Reflection.Module.FullyQualifiedName> **並**具有索引 `Trait` 鍵為 `"Category"` 且值為的 `"CategoryA"` 。</span><span class="sxs-lookup"><span data-stu-id="01586-141">To run tests that have `TestClass1` in their <xref:System.Reflection.Module.FullyQualifiedName> **and** have a `Trait` with a key of `"Category"` and value of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"
```

<span data-ttu-id="01586-142">若要執行的測試 <xref:System.Reflection.Module.FullyQualifiedName> 包含 `TestClass1` **，且**具有索引 `Trait` 鍵為 `"Category"` 且值為， `"CategoryA"` **或**具有索引 `Trait` 鍵 `"Priority"` 和值的 `1` 。</span><span class="sxs-lookup"><span data-stu-id="01586-142">To run tests that have either <xref:System.Reflection.Module.FullyQualifiedName> containing `TestClass1` **and** have a `Trait` with a key of `"Category"` and value of `"CategoryA"` **or** have a `Trait` with a key of `"Priority"` and value of `1`.</span></span>

```dotnetcli
dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)|Priority=1"
```

:::zone-end
:::zone pivot="nunit"

```csharp
using NUnit.Framework;

namespace NUnitNamespace
{
    public class UnitTest1
    {
        [Test, Property("Priority", 1), Category("CategoryA")]
        public void TestMethod1()
        {
        }

        [Test, Property("Priority", 2)]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="01586-143">運算式</span><span class="sxs-lookup"><span data-stu-id="01586-143">Expression</span></span> | <span data-ttu-id="01586-144">結果</span><span class="sxs-lookup"><span data-stu-id="01586-144">Result</span></span> |
|--|--|
| `dotnet test --filter Method` | <span data-ttu-id="01586-145">執行 <xref:System.Reflection.Module.FullyQualifiedName> 包含 `Method` 的測試。</span><span class="sxs-lookup"><span data-stu-id="01586-145">Runs tests whose <xref:System.Reflection.Module.FullyQualifiedName> contains `Method`.</span></span> <span data-ttu-id="01586-146">`vstest 15.1+` 提供此測試。</span><span class="sxs-lookup"><span data-stu-id="01586-146">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="01586-147">執行名稱包含 `TestMethod1` 的測試。</span><span class="sxs-lookup"><span data-stu-id="01586-147">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="01586-148">執行類別中的測試 `NUnitNamespace.UnitTest1` 。</span><span class="sxs-lookup"><span data-stu-id="01586-148">Runs tests that are in class `NUnitNamespace.UnitTest1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="01586-149">執行 `NUnitNamespace.UnitTest1.TestMethod1` 以外的所有測試。</span><span class="sxs-lookup"><span data-stu-id="01586-149">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="01586-150">執行以標注的測試 `[Category("CategoryA")]` 。</span><span class="sxs-lookup"><span data-stu-id="01586-150">Runs tests that are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="01586-151">執行以標注的測試 `[Priority(2)]` 。</span><span class="sxs-lookup"><span data-stu-id="01586-151">Runs tests that are annotated with `[Priority(2)]`.</span></span> |

<span data-ttu-id="01586-152">使用條件運算子和的 `|` 範例 `&` ：</span><span class="sxs-lookup"><span data-stu-id="01586-152">Examples using the conditional operators `|` and `&`:</span></span>

<span data-ttu-id="01586-153">若要執行 `UnitTest1` 在其 <xref:System.Reflection.Module.FullyQualifiedName> **或**中具有的測試 `Category` `"CategoryA"` 。</span><span class="sxs-lookup"><span data-stu-id="01586-153">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **or** have a `Category` of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

<span data-ttu-id="01586-154">執行中具有的測試， `UnitTest1` <xref:System.Reflection.Module.FullyQualifiedName> **並**具有 `Category` 的 `"CategoryA"` 。</span><span class="sxs-lookup"><span data-stu-id="01586-154">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **and** have a `Category` of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

<span data-ttu-id="01586-155">若要執行具有包含之的測試， <xref:System.Reflection.Module.FullyQualifiedName> `UnitTest1` **並**具有 `Category` 的， `"CategoryA"` **或**具有 `Property` `"Priority"` 的 `1` 。</span><span class="sxs-lookup"><span data-stu-id="01586-155">To run tests that have either a <xref:System.Reflection.Module.FullyQualifiedName> containing `UnitTest1` **and** have a `Category` of `"CategoryA"` **or** have a `Property` with a `"Priority"` of `1`.</span></span>

```dotnetcli
dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)|Priority=1"
```

<span data-ttu-id="01586-156">如需詳細資訊，請參閱[TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md)。</span><span class="sxs-lookup"><span data-stu-id="01586-156">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>

:::zone-end

## <a name="see-also"></a><span data-ttu-id="01586-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01586-157">See also</span></span>

- [<span data-ttu-id="01586-158">dotnet test</span><span class="sxs-lookup"><span data-stu-id="01586-158">dotnet test</span></span>](../tools/dotnet-test.md)
- [<span data-ttu-id="01586-159">dotnet 測試--篩選</span><span class="sxs-lookup"><span data-stu-id="01586-159">dotnet test --filter</span></span>](../tools/dotnet-test.md#filter-option-details)

## <a name="next-steps"></a><span data-ttu-id="01586-160">後續步驟</span><span class="sxs-lookup"><span data-stu-id="01586-160">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="01586-161">訂單單元測試</span><span class="sxs-lookup"><span data-stu-id="01586-161">Order unit tests</span></span>](order-unit-tests.md)
