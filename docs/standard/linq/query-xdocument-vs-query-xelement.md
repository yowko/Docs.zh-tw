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
# <a name="query-an-xdocument-vs-query-an-xelement-linq-to-xml"></a><span data-ttu-id="675c3-103">查詢 `XDocument` 與查詢 `XElement` (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="675c3-103">Query an `XDocument` vs. query an `XElement` (LINQ to XML)</span></span>

<span data-ttu-id="675c3-104">當您透過載入檔時，您所撰寫的查詢會與您透過 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> 載入時所撰寫的 slighty 不同 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="675c3-104">The query you write when you load a document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> differs slighty from what you write when you load via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span></span>

## <a name="comparison-of-xdocumentload-and-xelementload"></a><span data-ttu-id="675c3-105">與的比較 `XDocument.Load``XElement.Load`</span><span class="sxs-lookup"><span data-stu-id="675c3-105">Comparison of `XDocument.Load` and `XElement.Load`</span></span>

<span data-ttu-id="675c3-106">當您透過 <xref:System.Xml.Linq.XElement>，將 XML 文件載入到 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> 時，XML 樹狀結構根目錄的 <xref:System.Xml.Linq.XElement> 會包含已載入之文件的根項目。</span><span class="sxs-lookup"><span data-stu-id="675c3-106">When you load an XML document into an <xref:System.Xml.Linq.XElement> via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, the <xref:System.Xml.Linq.XElement> at the root of the XML tree contains the root element of the loaded document.</span></span> <span data-ttu-id="675c3-107">不過，當您透過 <xref:System.Xml.Linq.XDocument>，將相同的 XML 文件載入到 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> 時，樹狀目錄的根目錄為 <xref:System.Xml.Linq.XDocument> 節點，而已載入之文件的根項目為允許 <xref:System.Xml.Linq.XElement> 之子系 <xref:System.Xml.Linq.XDocument> 節點的項目。</span><span class="sxs-lookup"><span data-stu-id="675c3-107">However, when you load the same XML document into an <xref:System.Xml.Linq.XDocument> via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, the root of the tree is an <xref:System.Xml.Linq.XDocument> node, and the root element of the loaded document is the one allowed child <xref:System.Xml.Linq.XElement> node of the <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="675c3-108">LINQ to XML 軸的運作相對於根節點。</span><span class="sxs-lookup"><span data-stu-id="675c3-108">The LINQ to XML axes operate relative to the root node.</span></span>

## <a name="example-load-an-xml-tree-using-xelementload-then-query-for-child-elements"></a><span data-ttu-id="675c3-109">範例：使用載入 XML 樹狀結構 `XElement.Load` ，然後查詢子項目</span><span class="sxs-lookup"><span data-stu-id="675c3-109">Example: Load an XML tree using `XElement.Load`, then query for child elements</span></span>

<span data-ttu-id="675c3-110">這個第一個範例會使用 <xref:System.Xml.Linq.XElement.Load%2A> 載入 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="675c3-110">This first example loads an XML tree using <xref:System.Xml.Linq.XElement.Load%2A>.</span></span> <span data-ttu-id="675c3-111">接著，它會針對樹狀結構根目錄的子項目進行查詢。</span><span class="sxs-lookup"><span data-stu-id="675c3-111">It then queries for the child elements of the root of the tree.</span></span>

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

<span data-ttu-id="675c3-112">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="675c3-112">This example produces the following output:</span></span>

```output
Querying tree loaded with XElement.Load
----
<Child1>1</Child1>
<Child2>2</Child2>
<Child3>3</Child3>
```

## <a name="example-load-an-xml-tree-using-xdocumentload-then-query-for-child-elements"></a><span data-ttu-id="675c3-113">範例：使用載入 XML 樹狀結構 `XDocument.Load` ，然後查詢子項目</span><span class="sxs-lookup"><span data-stu-id="675c3-113">Example: Load an XML tree using `XDocument.Load`, then query for child elements</span></span>

<span data-ttu-id="675c3-114">下一個範例與上述範例相同，但 XML 樹狀結構已載入至 <xref:System.Xml.Linq.XDocument> ，而不是 <xref:System.Xml.Linq.XElement> 。</span><span class="sxs-lookup"><span data-stu-id="675c3-114">The next example does the same as the one above, but the XML tree has been loaded into an <xref:System.Xml.Linq.XDocument>, rather than an <xref:System.Xml.Linq.XElement>.</span></span>

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

<span data-ttu-id="675c3-115">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="675c3-115">This example produces the following output:</span></span>

```output
Querying tree loaded with XDocument.Load
----
<Root>
  <Child1>1</Child1>
  <Child2>2</Child2>
  <Child3>3</Child3>
</Root>
```

<span data-ttu-id="675c3-116">請注意，相同的查詢會傳回一個 `Root` 節點，而非三個子節點。</span><span class="sxs-lookup"><span data-stu-id="675c3-116">Notice that the same query returned the one `Root` node instead of the three child nodes.</span></span>

<span data-ttu-id="675c3-117">其中一個處理方法為，在存取座標軸方法之前，先使用 <xref:System.Xml.Linq.XDocument.Root%2A> 屬性，如下所示：</span><span class="sxs-lookup"><span data-stu-id="675c3-117">One approach to dealing with this is to use the <xref:System.Xml.Linq.XDocument.Root%2A> property before accessing the axes methods, as follows:</span></span>

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

<span data-ttu-id="675c3-118">這個查詢現在會以查詢樹狀結構根目錄 <xref:System.Xml.Linq.XElement> 的相同方式執行。</span><span class="sxs-lookup"><span data-stu-id="675c3-118">This query now performs in the same way as the query on the tree rooted in <xref:System.Xml.Linq.XElement>.</span></span>

<span data-ttu-id="675c3-119">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="675c3-119">This example produces the following output:</span></span>

```output
Querying tree loaded with XDocument.Load
----
<Child1>1</Child1>
<Child2>2</Child2>
<Child3>3</Child3>
```
