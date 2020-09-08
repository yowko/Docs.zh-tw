---
title: 如何變更整個 XML 樹狀結構的命名空間-LINQ to XML
description: 瞭解如何變更整個 XML 樹狀結構的命名空間。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 1584ff3b-c77d-4241-ab62-80adfb7bfc1b
ms.openlocfilehash: ac4eda71dd536ed2f940f1e86a0190ef337c386a
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552247"
---
# <a name="how-to-change-the-namespace-for-an-entire-xml-tree-linq-to-xml"></a><span data-ttu-id="86edf-103">如何變更整個 XML 樹狀結構的命名空間 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="86edf-103">How to change the namespace for an entire XML tree (LINQ to XML)</span></span>

<span data-ttu-id="86edf-104">您有時候必須以程式設計的方式，變更項目或屬性的命名空間。</span><span class="sxs-lookup"><span data-stu-id="86edf-104">You sometimes have to programmatically change the namespace for an element or an attribute.</span></span> <span data-ttu-id="86edf-105">LINQ to XML 可以簡化這個程序。</span><span class="sxs-lookup"><span data-stu-id="86edf-105">LINQ to XML makes this easy.</span></span> <span data-ttu-id="86edf-106">您可以設定 <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="86edf-106">The <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> property can be set.</span></span> <span data-ttu-id="86edf-107"><xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType>無法設定屬性，但您可以輕鬆地將屬性複製到 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> ，移除現有的屬性，然後加入新的所需命名空間中的新屬性。</span><span class="sxs-lookup"><span data-stu-id="86edf-107">The <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> property can't be set, but you can easily copy the attributes into a <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, remove the existing attributes, and then add new attributes that are in the new desired namespace.</span></span>

<span data-ttu-id="86edf-108">如需詳細資訊，請參閱 [命名空間總覽](namespaces-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="86edf-108">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

## <a name="example-create-two-xml-trees-change-the-namespaces-and-combine-the-trees"></a><span data-ttu-id="86edf-109">範例：建立兩個 XML 樹狀結構、變更命名空間，以及合併樹狀結構</span><span class="sxs-lookup"><span data-stu-id="86edf-109">Example: Create two XML trees, change the namespaces, and combine the trees</span></span>

<span data-ttu-id="86edf-110">下列程式碼會在沒有命名空間中建立兩個 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="86edf-110">The following code creates two XML trees in no namespace.</span></span> <span data-ttu-id="86edf-111">接著，它會變更每個樹狀結構的命名空間，然後將這些命名空間結合成單一樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="86edf-111">It then changes the namespace of each of the trees, and combines them into a single tree.</span></span>

```csharp
XElement tree1 = new XElement("Data",
    new XElement("Child", "content",
        new XAttribute("MyAttr", "content")
    )
);
XElement tree2 = new XElement("Data",
    new XElement("Child", "content",
        new XAttribute("MyAttr", "content")
    )
);
XNamespace aw = "http://www.adventure-works.com";
XNamespace ad = "http://www.adatum.com";
// Change the namespace of every element and attribute in the first tree.
foreach (XElement el in tree1.DescendantsAndSelf())
{
    el.Name = aw.GetName(el.Name.LocalName);
    List<XAttribute> atList = el.Attributes().ToList();
    el.Attributes().Remove();
    foreach (XAttribute at in atList)
        el.Add(new XAttribute(aw.GetName(at.Name.LocalName), at.Value));
}
// Change the namespace of every element and attribute in the second tree.
foreach (XElement el in tree2.DescendantsAndSelf())
{
    el.Name = ad.GetName(el.Name.LocalName);
    List<XAttribute> atList = el.Attributes().ToList();
    el.Attributes().Remove();
    foreach (XAttribute at in atList)
        el.Add(new XAttribute(ad.GetName(at.Name.LocalName), at.Value));
}
// Add attribute namespaces so that the tree will be serialized with
// the aw and ad namespace prefixes.
tree1.Add(
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com")
);
tree2.Add(
    new XAttribute(XNamespace.Xmlns + "ad", "http://www.adatum.com")
);
// Create a new composite tree.
XElement root = new XElement("Root",
    tree1,
    tree2
);
Console.WriteLine(root);
```

```vb
Dim tree1 As XElement = _
    <Data>
        <Child MyAttr="content">content</Child>
    </Data>
Dim tree2 As XElement = _
    <Data>
        <Child MyAttr="content">content</Child>
    </Data>
Dim aw As XNamespace = "http://www.adventure-works.com"
Dim ad As XNamespace = "http://www.adatum.com"
' Change the namespace of every element and attribute in the first tree.
For Each el As XElement In tree1.DescendantsAndSelf
    el.Name = aw.GetName(el.Name.LocalName)
    Dim atList As List(Of XAttribute) = el.Attributes().ToList()
    el.Attributes().Remove()
    For Each at As XAttribute In atList
        el.Add(New XAttribute(aw.GetName(at.Name.LocalName), at.Value))
    Next
Next
' Change the namespace of every element and attribute in the second tree.
For Each el As XElement In tree2.DescendantsAndSelf()
    el.Name = ad.GetName(el.Name.LocalName)
    Dim atList As List(Of XAttribute) = el.Attributes().ToList()
    el.Attributes().Remove()
    For Each at As XAttribute In atList
        el.Add(New XAttribute(ad.GetName(at.Name.LocalName), at.Value))
    Next
Next
' Add attribute namespaces so that the tree will be serialized with
' the aw and ad namespace prefixes.
tree1.Add( _
    New XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com") _
)
tree2.Add( _
    New XAttribute(XNamespace.Xmlns + "ad", "http://www.adatum.com") _
)
' Create a new composite tree.
Dim root As XElement = _
    <Root>
        <%= tree1 %>
        <%= tree2 %>
    </Root>
Console.WriteLine(root)
```

<span data-ttu-id="86edf-112">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="86edf-112">This example produces the following output:</span></span>

```xml
<Root>
  <aw:Data xmlns:aw="http://www.adventure-works.com">
    <aw:Child aw:MyAttr="content">content</aw:Child>
  </aw:Data>
  <ad:Data xmlns:ad="http://www.adatum.com">
    <ad:Child ad:MyAttr="content">content</ad:Child>
  </ad:Data>
</Root>
```
