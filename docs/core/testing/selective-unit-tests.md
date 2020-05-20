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
# <a name="run-selective-unit-tests"></a>執行選擇性單元測試

使用 [`dotnet test`](../tools/dotnet-test.md) .Net Core 中的命令，您可以使用篩選運算式來執行選擇性測試。 本文示範如何篩選要執行的測試。 下列範例使用`dotnet test`。 若要使用`vstest.console.exe`，請以取代 `--testcasefilter:` 取代 `--filter`。

## <a name="character-escaping"></a>字元轉義

使用包含驚嘆號的篩選準則 `!` `*nix` 時，需要進行轉義，因為 `!` 是保留的。 例如，如果命名空間包含 IntegrationTests，此篩選會略過所有測試：

```dotnetcli
dotnet test --filter FullyQualifiedName\!~IntegrationTests
```

> [!IMPORTANT]
> 反斜線的前面會加上驚嘆號，表示它是一個逸出字元 `\!` 。

對於 `FullyQualifiedName` 包含泛型型別參數之逗號的值，請使用來將逗號換成 `%2C` 。 例如：

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

| 運算式 | 結果 |
|--|--|
| `dotnet test --filter Method` | 執行 <xref:System.Reflection.Module.FullyQualifiedName> 包含 `Method` 的測試。 `vstest 15.1+` 提供此測試。 |
| `dotnet test --filter Name~TestMethod1` | 執行名稱包含 `TestMethod1` 的測試。 |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | 執行類別中的測試 `MSTestNamespace.UnitTest1` 。<br>**注意︰**`ClassName`值應會有命名空間，所以 `ClassName=UnitTest1` 將無法運作。 |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | 執行 `MSTestNamespace.UnitTest1.TestMethod1` 以外的所有測試。 |
| `dotnet test --filter TestCategory=CategoryA` | 執行以標注的測試 `[TestCategory("CategoryA")]` 。 |
| `dotnet test --filter Priority=2` | 執行以標注的測試 `[Priority(2)]` 。 |

使用條件運算子和的 `|` 範例 `&` ：

若要 `UnitTest1` 在 <xref:System.Reflection.Module.FullyQualifiedName> **或**中執行具有的測試 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> `"CategoryA"` 。

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

執行中具有的測試， `UnitTest1` <xref:System.Reflection.Module.FullyQualifiedName> **並**具有 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> 的 `"CategoryA"` 。

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

若要執行的測試 <xref:System.Reflection.Module.FullyQualifiedName> 包含 `UnitTest1` **，而且**具有 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> 的， `"CategoryA"` **或**具有的 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute> 優先順序為 `1` 。

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

| 運算式 | 結果 |
|--|--|
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | 僅執行 `XUnitNamespace.TestClass1.Test1` 這一項測試。 |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | 執行 `XUnitNamespace.TestClass1.Test1` 以外的所有測試。 |
| `dotnet test --filter DisplayName~TestClass1` | 執行顯示名稱包含 `TestClass1` 的測試。 |

在程式碼範例中，所定義具有索引鍵 `"Category"` 及 `"Priority"` 的特徵可用於篩選。

| 運算式 | 結果 |
|--|--|
| `dotnet test --filter XUnit` | 執行 <xref:System.Reflection.Module.FullyQualifiedName> 包含 `XUnit` 的測試。  `vstest 15.1+` 提供此測試。 |
| `dotnet test --filter Category=CategoryA` | 執行具有的測試 `[Trait("Category", "CategoryA")]` 。 |

使用條件運算子和的 `|` 範例 `&` ：

若要執行 `TestClass1` 在其或中具有索引 <xref:System.Reflection.Module.FullyQualifiedName> **or** `Trait` 鍵為 `"Category"` 且值為的測試 `"CategoryA"` 。

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1|Category=CategoryA"
```

若要在其中執行具有的測試， `TestClass1` <xref:System.Reflection.Module.FullyQualifiedName> **並**具有索引 `Trait` 鍵為 `"Category"` 且值為的 `"CategoryA"` 。

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"
```

若要執行的測試 <xref:System.Reflection.Module.FullyQualifiedName> 包含 `TestClass1` **，且**具有索引 `Trait` 鍵為 `"Category"` 且值為， `"CategoryA"` **或**具有索引 `Trait` 鍵 `"Priority"` 和值的 `1` 。

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

| 運算式 | 結果 |
|--|--|
| `dotnet test --filter Method` | 執行 <xref:System.Reflection.Module.FullyQualifiedName> 包含 `Method` 的測試。 `vstest 15.1+` 提供此測試。 |
| `dotnet test --filter Name~TestMethod1` | 執行名稱包含 `TestMethod1` 的測試。 |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | 執行類別中的測試 `NUnitNamespace.UnitTest1` 。 |
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | 執行 `NUnitNamespace.UnitTest1.TestMethod1` 以外的所有測試。 |
| `dotnet test --filter TestCategory=CategoryA` | 執行以標注的測試 `[Category("CategoryA")]` 。 |
| `dotnet test --filter Priority=2` | 執行以標注的測試 `[Priority(2)]` 。 |

使用條件運算子和的 `|` 範例 `&` ：

若要執行 `UnitTest1` 在其 <xref:System.Reflection.Module.FullyQualifiedName> **或**中具有的測試 `Category` `"CategoryA"` 。

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

執行中具有的測試， `UnitTest1` <xref:System.Reflection.Module.FullyQualifiedName> **並**具有 `Category` 的 `"CategoryA"` 。

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

若要執行具有包含之的測試， <xref:System.Reflection.Module.FullyQualifiedName> `UnitTest1` **並**具有 `Category` 的， `"CategoryA"` **或**具有 `Property` `"Priority"` 的 `1` 。

```dotnetcli
dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)|Priority=1"
```

如需詳細資訊，請參閱[TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md)。

:::zone-end

## <a name="see-also"></a>另請參閱

- [dotnet test](../tools/dotnet-test.md)
- [dotnet 測試--篩選](../tools/dotnet-test.md#filter-option-details)

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [訂單單元測試](order-unit-tests.md)
