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
# <a name="running-selective-unit-tests"></a>執行多樣化選擇的單元測試

下列範例使用`dotnet test`。 若要使用`vstest.console.exe`，請以取代 `--testcasefilter:` 取代 `--filter `。

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

| 運算式 | 結果 |
| ---------- | ------ |
| `dotnet test --filter Method` | 執行 `FullyQualifiedName` 包含 `Method` 的測試。 `vstest 15.1+` 提供此測試。 |
| `dotnet test --filter Name~TestMethod1` | 執行名稱包含 `TestMethod1` 的測試。 |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | 執行類別為 `MSTestNamespace.UnitTest1` 的測試。<br>**注意︰**`ClassName`值應會有命名空間，所以 `ClassName=UnitTest1` 將無法運作。 |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | 執行 `MSTestNamespace.UnitTest1.TestMethod1` 以外的所有測試。 |
| `dotnet test --filter TestCategory=CategoryA` | 執行標示有 `[TestCategory("CategoryA")]` 註釋的測試。 |
| `dotnet test --filter Priority=2` | 執行標示有 `[Priority(2)]` 註釋的測試。<br>

**使用條件式運算子 | 與 &amp;**

| 運算式 | 結果 |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | 執行 `FullyQualifiedName` **或** `TestCategory` 中之 `UnitTest1` 為 `CategoryA` 的測試。 |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | 執行 `FullyQualifiedName` **及** `TestCategory` 中之 `UnitTest1` 為 `CategoryA` 的測試。 |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | 執行 `FullyQualifiedName` 所含之 `UnitTest1` **及** `TestCategory` 為 `CategoryA` **或** `Priority` 為 1 的測試。 |

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

| 運算式 | 結果 |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | 僅執行 `XUnitNamespace.TestClass1.Test1` 這一項測試。 |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | 執行 `XUnitNamespace.TestClass1.Test1` 以外的所有測試。 |
| `dotnet test --filter DisplayName~TestClass1` | 執行顯示名稱包含 `TestClass1` 的測試。 |

在程式碼範例中，所定義具有索引鍵 `Category` 及 `Priority` 的特徵可用於篩選。

| 運算式 | 結果 |
| ---------- | ------ |
| `dotnet test --filter XUnit` | 執行 `FullyQualifiedName` 包含 `XUnit` 的測試。  `vstest 15.1+` 提供此測試。 |
| `dotnet test --filter Category=CategoryA` | 執行包含 `[Trait("Category", "CategoryA")]` 的測試。 |

**使用條件式運算子 | 與 &amp;**

| 運算式 | 結果 |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | 執行 `FullyQualifiedName` **或** `Category` 中之 `TestClass1` 為 `CategoryA` 的測試。 |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | 執行 `FullyQualifiedName` **及** `Category` 中之 `TestClass1` 為 `CategoryA` 的測試。 |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | 執行 `FullyQualifiedName` 所含之 `TestClass1` **及** `Category` 為 `CategoryA` **或** `Priority` 為 1 的測試。 |

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

| 運算式 | 結果 |
| ---------- | ------ |
| `dotnet test --filter Method` | 執行 `FullyQualifiedName` 包含 `Method` 的測試。 `vstest 15.1+` 提供此測試。 |
| `dotnet test --filter Name~TestMethod1` | 執行名稱包含 `TestMethod1` 的測試。 |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | 執行類別為 `NUnitNamespace.UnitTest1` 的測試。<br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | 執行 `NUnitNamespace.UnitTest1.TestMethod1` 以外的所有測試。 |
| `dotnet test --filter TestCategory=CategoryA` | 執行標示有 `[Category("CategoryA")]` 註釋的測試。 |
| `dotnet test --filter Priority=2` | 執行標示有 `[Priority(2)]` 註釋的測試。<br>

**使用條件式運算子 | 與 &amp;**

| 運算式 | 結果 |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | 執行 `FullyQualifiedName` **或** `TestCategory` 中之 `UnitTest1` 為 `CategoryA` 的測試。 |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | 執行 `FullyQualifiedName` **及** `TestCategory` 中之 `UnitTest1` 為 `CategoryA` 的測試。 |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | 執行 `FullyQualifiedName` 所含之 `UnitTest1` **及** `TestCategory` 為 `CategoryA` **或** `Priority` 為 1 的測試。 |
