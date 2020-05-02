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
# <a name="run-selective-unit-tests"></a>執行選擇性單元測試

透過 .NET Core 中的 `dotnet test` 命令，您可以使用篩選運算式來執行選擇性測試。 本文示範如何篩選要執行的測試。 下列範例使用`dotnet test`。 若要使用`vstest.console.exe`，請以取代 `--testcasefilter:` 取代 `--filter`。

## <a name="character-escaping"></a>字元轉義

在上`*nix`使用包含驚嘆號（！）的篩選時，需要`!`進行轉義，因為是保留的。 例如，如果命名空間包含 IntegrationTests： `dotnet test --filter FullyQualifiedName\!~IntegrationTests`，則此篩選會略過所有測試。
請記下驚嘆號前面的反斜線。

對於`FullyQualifiedName`包含泛型型別參數之逗號的值，請使用來將`%2C`逗號換成。 例如：

```dotnetcli
dotnet test --filter "FullyQualifiedName=MyNamespace.MyTestsClass<ParameterType1%2CParameterType2>.MyTestMethod"
```

## <a name="mstest"></a>MSTest

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

| 運算是 | 結果 |
| ---------- | ------ |
| `dotnet test --filter Method` | 執行 `FullyQualifiedName` 包含 `Method` 的測試。 `vstest 15.1+` 提供此測試。 |
| `dotnet test --filter Name~TestMethod1` | 執行名稱包含 `TestMethod1` 的測試。 |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | 執行類別`MSTestNamespace.UnitTest1`中的測試。<br>**注意︰**`ClassName`值應會有命名空間，所以 `ClassName=UnitTest1` 將無法運作。 |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | 執行 `MSTestNamespace.UnitTest1.TestMethod1` 以外的所有測試。 |
| `dotnet test --filter TestCategory=CategoryA` | 執行以`[TestCategory("CategoryA")]`標注的測試。 |
| `dotnet test --filter Priority=2` | 執行以`[Priority(2)]`標注的測試。<br>

**使用條件式運算子 | 與 &amp;**

| 運算是 | 結果 |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | `UnitTest1`執行中`FullyQualifiedName`具有**或** `TestCategory`的測試。 `CategoryA` |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | `UnitTest1`執行中`FullyQualifiedName`的測試，**且** `TestCategory`為`CategoryA`。 |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | 執行`FullyQualifiedName`包含`UnitTest1` **且** `TestCategory`為`CategoryA` **or**或`Priority`為1的測試。 |

## <a name="xunit"></a>xUnit

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

| 運算是 | 結果 |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | 僅執行 `XUnitNamespace.TestClass1.Test1` 這一項測試。 |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | 執行 `XUnitNamespace.TestClass1.Test1` 以外的所有測試。 |
| `dotnet test --filter DisplayName~TestClass1` | 執行顯示名稱包含 `TestClass1` 的測試。 |

在程式碼範例中，所定義具有索引鍵 `Category` 及 `Priority` 的特徵可用於篩選。

| 運算是 | 結果 |
| ---------- | ------ |
| `dotnet test --filter XUnit` | 執行 `FullyQualifiedName` 包含 `XUnit` 的測試。  `vstest 15.1+` 提供此測試。 |
| `dotnet test --filter Category=CategoryA` | 執行具有`[Trait("Category", "CategoryA")]`的測試。 |

**使用條件式運算子 | 與 &amp;**

| 運算是 | 結果 |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | `TestClass1`執行中`FullyQualifiedName`具有**或** `Category`的測試。 `CategoryA` |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | `TestClass1`執行中`FullyQualifiedName`的測試，**且** `Category`為`CategoryA`。 |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | 執行`FullyQualifiedName`包含`TestClass1` **且** `Category`為`CategoryA` **or**或`Priority`為1的測試。 |

## <a name="nunit"></a>NUnit

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

| 運算是 | 結果 |
| ---------- | ------ |
| `dotnet test --filter Method` | 執行 `FullyQualifiedName` 包含 `Method` 的測試。 `vstest 15.1+` 提供此測試。 |
| `dotnet test --filter Name~TestMethod1` | 執行名稱包含 `TestMethod1` 的測試。 |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | 執行類別`NUnitNamespace.UnitTest1`中的測試。<br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | 執行 `NUnitNamespace.UnitTest1.TestMethod1` 以外的所有測試。 |
| `dotnet test --filter TestCategory=CategoryA` | 執行以`[Category("CategoryA")]`標注的測試。 |
| `dotnet test --filter Priority=2` | 執行以`[Priority(2)]`標注的測試。<br>

**使用條件式運算子 | 與 &amp;**

| 運算是 | 結果 |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | `UnitTest1`執行中`FullyQualifiedName`具有**或** `TestCategory`的測試。 `CategoryA` |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | `UnitTest1`執行中`FullyQualifiedName`的測試，**且** `TestCategory`為`CategoryA`。 |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | 執行`FullyQualifiedName`包含`UnitTest1` **且** `TestCategory`為`CategoryA` **or**或`Priority`為1的測試。 |

如需詳細資訊，請參閱[TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md)。
