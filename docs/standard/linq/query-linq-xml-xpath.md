---
title: 如何使用 XPath 查詢 LINQ to XML-LINQ to XML
description: 瞭解可讓您使用 XPath 查詢 XML 樹狀結構的擴充方法。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
ms.openlocfilehash: 8189bcdd38f9242a5890837633bbec4e7f2fc601
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552741"
---
# <a name="how-to-query-linq-to-xml-using-xpath-linq-to-xml"></a>如何使用 XPath (LINQ to XML 查詢 LINQ to XML) 

本文將介紹可讓您使用 XPath 查詢 XML 樹狀結構的擴充方法。 如需有關使用這些擴充方法的詳細資訊，請參閱 <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>。

> [!NOTE]
> 除非您有非常明確的使用 XPath 查詢原因，例如廣泛使用舊版程式碼，所以不建議使用 XPath 搭配 LINQ to XML。 XPath 查詢將不會執行，也不會執行 LINQ to XML 查詢。

## <a name="example"></a>範例

下列範例會建立小型 XML 樹狀結構，並使用 <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> 來選取一組項目。

```csharp
XElement root = new XElement("Root",
    new XElement("Child1", 1),
    new XElement("Child1", 2),
    new XElement("Child1", 3),
    new XElement("Child2", 4),
    new XElement("Child2", 5),
    new XElement("Child2", 6)
);
IEnumerable<XElement> list = root.XPathSelectElements("./Child2");
foreach (XElement el in list)
    Console.WriteLine(el);
```

```vb
Dim root As XElement = _
    <Root>
        <Child1>1</Child1>
        <Child1>2</Child1>
        <Child1>3</Child1>
        <Child2>4</Child2>
        <Child2>5</Child2>
        <Child2>6</Child2>
    </Root>

Dim list As IEnumerable(Of XElement) = root.XPathSelectElements("./Child2")
For Each el As XElement In list
    Console.WriteLine(el)
Next
```

這個範例會產生下列輸出：

```xml
<Child2>4</Child2>
<Child2>5</Child2>
<Child2>6</Child2>
```
