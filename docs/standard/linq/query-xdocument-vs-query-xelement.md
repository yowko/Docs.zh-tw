---
title: 查詢 XDocument 與查詢 System.xml.linq.xelement>-LINQ to XML
description: 針對 XDocument 載入的 XML 檔撰寫稍微不同的查詢。 load 和 System.xml.linq.xelement>。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 46221ff5-62ee-4de8-93ba-66465facb5c1
ms.openlocfilehash: 96d706bcc1871c9e420bafd984d08ca9616b5c18
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552740"
---
# <a name="query-an-xdocument-vs-query-an-xelement-linq-to-xml"></a>查詢 `XDocument` 與查詢 `XElement` (LINQ to XML) 

當您透過載入檔時，您所撰寫的查詢會與您透過 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> 載入時所撰寫的 slighty 不同 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> 。

## <a name="comparison-of-xdocumentload-and-xelementload"></a>與的比較 `XDocument.Load``XElement.Load`

當您透過 <xref:System.Xml.Linq.XElement>，將 XML 文件載入到 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> 時，XML 樹狀結構根目錄的 <xref:System.Xml.Linq.XElement> 會包含已載入之文件的根項目。 不過，當您透過 <xref:System.Xml.Linq.XDocument>，將相同的 XML 文件載入到 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> 時，樹狀目錄的根目錄為 <xref:System.Xml.Linq.XDocument> 節點，而已載入之文件的根項目為允許 <xref:System.Xml.Linq.XElement> 之子系 <xref:System.Xml.Linq.XDocument> 節點的項目。 LINQ to XML 軸的運作相對於根節點。

## <a name="example-load-an-xml-tree-using-xelementload-then-query-for-child-elements"></a>範例：使用載入 XML 樹狀結構 `XElement.Load` ，然後查詢子項目

這個第一個範例會使用 <xref:System.Xml.Linq.XElement.Load%2A> 載入 XML 樹狀結構。 接著，它會針對樹狀結構根目錄的子項目進行查詢。

```csharp
// Create a simple document and write it to a file
File.WriteAllText("Test.xml", @"<Root>
    <Child1>1</Child1>
    <Child2>2</Child2>
    <Child3>3</Child3>
</Root>");

Console.WriteLine("Querying tree loaded with XElement.Load");
Console.WriteLine("----");
XElement doc = XElement.Load("Test.xml");
IEnumerable<XElement> childList =
    from el in doc.Elements()
    select el;
foreach (XElement e in childList)
    Console.WriteLine(e);
```

```vb
' Create a simple document and  write it to a file
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _
    "    <Child1>1</Child1>" + Environment.NewLine + _
    "    <Child2>2</Child2>" + Environment.NewLine + _
    "    <Child3>3</Child3>" + Environment.NewLine + _
    "</Root>")

Console.WriteLine("Querying tree loaded with XElement.Load")
Console.WriteLine("----")
Dim doc As XElement = XElement.Load("Test.xml")
Dim childList As IEnumerable(Of XElement) = _
        From el In doc.Elements() _
        Select el
For Each e As XElement In childList
    Console.WriteLine(e)
Next
```

這個範例會產生下列輸出：

```output
Querying tree loaded with XElement.Load
----
<Child1>1</Child1>
<Child2>2</Child2>
<Child3>3</Child3>
```

## <a name="example-load-an-xml-tree-using-xdocumentload-then-query-for-child-elements"></a>範例：使用載入 XML 樹狀結構 `XDocument.Load` ，然後查詢子項目

下一個範例與上述範例相同，但 XML 樹狀結構已載入至 <xref:System.Xml.Linq.XDocument> ，而不是 <xref:System.Xml.Linq.XElement> 。

```csharp
// Create a simple document and write it to a file
File.WriteAllText("Test.xml", @"<Root>
    <Child1>1</Child1>
    <Child2>2</Child2>
    <Child3>3</Child3>
</Root>");

Console.WriteLine("Querying tree loaded with XDocument.Load");
Console.WriteLine("----");
XDocument doc = XDocument.Load("Test.xml");
IEnumerable<XElement> childList =
    from el in doc.Elements()
    select el;
foreach (XElement e in childList)
    Console.WriteLine(e);
```

```vb
' Create a simple document and  write it to a file
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _
    "    <Child1>1</Child1>" + Environment.NewLine + _
    "    <Child2>2</Child2>" + Environment.NewLine + _
    "    <Child3>3</Child3>" + Environment.NewLine + _
    "</Root>")

Console.WriteLine("Querying tree loaded with XDocument.Load")
Console.WriteLine("----")
Dim doc As XDocument = XDocument.Load("Test.xml")
Dim childList As IEnumerable(Of XElement) = _
        From el In doc.Elements() _
        Select el
For Each e As XElement In childList
    Console.WriteLine(e)
Next
```

這個範例會產生下列輸出：

```output
Querying tree loaded with XDocument.Load
----
<Root>
  <Child1>1</Child1>
  <Child2>2</Child2>
  <Child3>3</Child3>
</Root>
```

請注意，相同的查詢會傳回一個 `Root` 節點，而非三個子節點。

其中一個處理方法為，在存取座標軸方法之前，先使用 <xref:System.Xml.Linq.XDocument.Root%2A> 屬性，如下所示：

```csharp
// Create a simple document and write it to a file
File.WriteAllText("Test.xml", @"<Root>
    <Child1>1</Child1>
    <Child2>2</Child2>
    <Child3>3</Child3>
</Root>");

Console.WriteLine("Querying tree loaded with XDocument.Load");
Console.WriteLine("----");
XDocument doc = XDocument.Load("Test.xml");
IEnumerable<XElement> childList =
    from el in doc.Root.Elements()
    select el;
foreach (XElement e in childList)
    Console.WriteLine(e);
```

```vb
' Create a simple document and  write it to a file
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _
    "    <Child1>1</Child1>" + Environment.NewLine + _
    "    <Child2>2</Child2>" + Environment.NewLine + _
    "    <Child3>3</Child3>" + Environment.NewLine + _
    "</Root>")

Console.WriteLine("Querying tree loaded with XDocument.Load")
Console.WriteLine("----")
Dim doc As XDocument = XDocument.Load("Test.xml")
Dim childList As IEnumerable(Of XElement) = _
        From el In doc.Root.Elements() _
        Select el
For Each e As XElement In childList
    Console.WriteLine(e)
Next
```

這個查詢現在會以查詢樹狀結構根目錄 <xref:System.Xml.Linq.XElement> 的相同方式執行。

這個範例會產生下列輸出：

```output
Querying tree loaded with XDocument.Load
----
<Child1>1</Child1>
<Child2>2</Child2>
<Child3>3</Child3>
```
