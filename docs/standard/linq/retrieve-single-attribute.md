---
title: 如何取出單一屬性-LINQ to XML
description: 取得屬性名稱，以抓取專案的單一屬性。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: a8a56ec62275f2376d19d7fc9090414b74fc77ad
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552708"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml"></a><span data-ttu-id="30ed0-103">如何擷取單一屬性 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="30ed0-103">How to retrieve a single attribute (LINQ to XML)</span></span>

<span data-ttu-id="30ed0-104">本文說明如何在指定屬性名稱的情況下，取得元素的單一屬性。</span><span class="sxs-lookup"><span data-stu-id="30ed0-104">This article explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="30ed0-105">這在撰寫您要尋找具有特定屬性之項目的查詢運算式時，相當實用。</span><span class="sxs-lookup"><span data-stu-id="30ed0-105">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>

<span data-ttu-id="30ed0-106"><xref:System.Xml.Linq.XElement.Attribute%2A> 類別的 <xref:System.Xml.Linq.XElement> 方法會傳回具有指定之名稱的 <xref:System.Xml.Linq.XAttribute>。</span><span class="sxs-lookup"><span data-stu-id="30ed0-106">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>

## <a name="example-retrieve-attribute-values-given-the-element-and-attribute-names"></a><span data-ttu-id="30ed0-107">範例：提供專案和屬性名稱來取得屬性值</span><span class="sxs-lookup"><span data-stu-id="30ed0-107">Example: Retrieve attribute values, given the element and attribute names</span></span>

<span data-ttu-id="30ed0-108">下列範例會使用 <xref:System.Xml.Linq.XElement> 方法來建立名為的專案 `PhoneNumbers` 。</span><span class="sxs-lookup"><span data-stu-id="30ed0-108">The following example uses the <xref:System.Xml.Linq.XElement> method to create an element named `PhoneNumbers`.</span></span> <span data-ttu-id="30ed0-109">然後，它會尋找名為的所有子系元素 `Phone` ，並為每個專案使用 <xref:System.Xml.Linq.XElement.Attribute%2A> 方法來取得和輸出名為的屬性值 `type` ：</span><span class="sxs-lookup"><span data-stu-id="30ed0-109">It then finds all the descendant elements named `Phone` and, for each, uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method to obtain and output the value of the attribute named `type`:</span></span>

```csharp
XElement cust = new XElement("PhoneNumbers",
    new XElement("Phone",
        new XAttribute("type", "home"),
        "555-555-5555"),
    new XElement("Phone",
        new XAttribute("type", "work"),
        "555-555-6666")
);
IEnumerable<XElement> elList =
    from el in cust.Descendants("Phone")
    select el;
foreach (XElement el in elList)
    Console.WriteLine((string)el.Attribute("type"));
```

```vb
Dim cust As XElement = <PhoneNumbers>
                           <Phone type="home">555-555-5555</Phone>
                           <Phone type="work">555-555-6666</Phone>
                       </PhoneNumbers>
Dim elList = From el In cust...<Phone>
For Each e As XElement In elList
    Console.WriteLine(e.@type)
Next
```

<span data-ttu-id="30ed0-110">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="30ed0-110">This example produces the following output:</span></span>

```output
home
work
```

## <a name="example-retrieve-an-attribute-value-with-a-cast"></a><span data-ttu-id="30ed0-111">範例：使用 cast 取得屬性值</span><span class="sxs-lookup"><span data-stu-id="30ed0-111">Example: Retrieve an attribute value with a cast</span></span>

<span data-ttu-id="30ed0-112">您可以藉由轉換屬性來取得它的值，就像使用 <xref:System.Xml.Linq.XElement> 物件一樣。</span><span class="sxs-lookup"><span data-stu-id="30ed0-112">You can retrieve the value of an attribute by casting it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="30ed0-113">下列範例為其示範：</span><span class="sxs-lookup"><span data-stu-id="30ed0-113">The following example demonstrates this:</span></span>

```csharp
XElement cust = new XElement("PhoneNumbers",
    new XElement("Phone",
        new XAttribute("type", "home"),
        "555-555-5555"),
    new XElement("Phone",
        new XAttribute("type", "work"),
        "555-555-6666")
);
IEnumerable<XElement> elList =
    from el in cust.Descendants("Phone")
    select el;
foreach (XElement el in elList)
    Console.WriteLine((string)el.Attribute("type"));
```

```vb
Dim cust As XElement = <PhoneNumbers>
                           <Phone type="home">555-555-5555</Phone>
                           <Phone type="work">555-555-6666</Phone>
                       </PhoneNumbers>
Dim elList As IEnumerable(Of XElement) = _
    From el In cust...<Phone> _
    Select el
For Each el As XElement In elList
    Console.WriteLine(el.@type)
Next
```

<span data-ttu-id="30ed0-114">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="30ed0-114">This example produces the following output:</span></span>

```output
home
work
```

<span data-ttu-id="30ed0-115">LINQ to XML 將類別的明確轉換運算子提供 <xref:System.Xml.Linq.XAttribute> 給 `string` 、、、、、、、、、、、、、、、、、、、、、、、、、、、、 `bool` `bool?` `int` `int?` `uint` `uint?` `long` `long?` `ulong` `ulong?` `float` `float?` `double` `double?` `decimal` `decimal?` `DateTime` `DateTime?` `TimeSpan` `TimeSpan?` `GUID` 和 `GUID?` 。</span><span class="sxs-lookup"><span data-stu-id="30ed0-115">LINQ to XML provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>

## <a name="example-cast-for-an-attribute-in-a-namespace"></a><span data-ttu-id="30ed0-116">範例：轉換命名空間中的屬性</span><span class="sxs-lookup"><span data-stu-id="30ed0-116">Example: Cast for an attribute in a namespace</span></span>

<span data-ttu-id="30ed0-117">下列範例顯示命名空間中之屬性的相同程式碼。</span><span class="sxs-lookup"><span data-stu-id="30ed0-117">The following example shows the same code for an attribute that's in a namespace.</span></span> <span data-ttu-id="30ed0-118">如需詳細資訊，請參閱 [命名空間總覽](namespaces-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="30ed0-118">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement cust = new XElement(aw + "PhoneNumbers",
    new XElement(aw + "Phone",
        new XAttribute(aw + "type", "home"),
        "555-555-5555"),
    new XElement(aw + "Phone",
        new XAttribute(aw + "type", "work"),
        "555-555-6666")
);
IEnumerable<XElement> elList =
    from el in cust.Descendants(aw + "Phone")
    select el;
foreach (XElement el in elList)
    Console.WriteLine((string)el.Attribute(aw + "type"));
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim cust As XElement = _
            <aw:PhoneNumbers>
                <aw:Phone aw:type="home">555-555-5555</aw:Phone>
                <aw:Phone aw:type="work">555-555-6666</aw:Phone>
            </aw:PhoneNumbers>
        Dim elList As IEnumerable(Of XElement) = _
            From el In cust...<aw:Phone> _
            Select el
        For Each el As XElement In elList
            Console.WriteLine(el.@aw:type)
        Next
    End Sub
End Module
```

<span data-ttu-id="30ed0-119">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="30ed0-119">This example produces the following output:</span></span>

```output
home
work
```

## <a name="see-also"></a><span data-ttu-id="30ed0-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30ed0-120">See also</span></span>

- [<span data-ttu-id="30ed0-121">LINQ to XML 軸總覽</span><span class="sxs-lookup"><span data-stu-id="30ed0-121">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
