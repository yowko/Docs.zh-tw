---
title: '如何變更整個 XML 樹狀結構的命名空間（c #）'
description: '瞭解如何以程式設計方式變更 c # 中 LINQ to XML 之專案或屬性的命名空間。'
ms.date: 07/20/2015
ms.assetid: 1584ff3b-c77d-4241-ab62-80adfb7bfc1b
ms.openlocfilehash: 0bf4c9d8f3cf569f14b654dfd0c4291a7eb647df
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105367"
---
# <a name="how-to-change-the-namespace-for-an-entire-xml-tree-c"></a>如何變更整個 XML 樹狀結構的命名空間（c #）
您有時候必須以程式設計的方式，變更項目或屬性的命名空間。 LINQ to XML 可以簡化這個程序。 您可以設定 <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> 屬性。 您無法設定 <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> 屬性 (Property)，但是您可以輕易地將屬性 (Attribute) 複製到 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>、移除現有的屬性 (Attribute)，然後加入所需之新命名空間中的新屬性 (Attribute)。  
  
 如需詳細資訊，請參閱[命名空間概觀 (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。  
  
## <a name="example"></a>範例  
 下列程式碼會在沒有命名空間中建立兩個 XML 樹狀結構。 接著，它會變更每個樹狀結構的命名空間，然後將這些命名空間結合成單一樹狀結構。  
  
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
// change the namespace of every element and attribute in the first tree  
foreach (XElement el in tree1.DescendantsAndSelf())  
{  
    el.Name = aw.GetName(el.Name.LocalName);  
    List<XAttribute> atList = el.Attributes().ToList();  
    el.Attributes().Remove();  
    foreach (XAttribute at in atList)  
        el.Add(new XAttribute(aw.GetName(at.Name.LocalName), at.Value));  
}  
// change the namespace of every element and attribute in the second tree  
foreach (XElement el in tree2.DescendantsAndSelf())  
{  
    el.Name = ad.GetName(el.Name.LocalName);  
    List<XAttribute> atList = el.Attributes().ToList();  
    el.Attributes().Remove();  
    foreach (XAttribute at in atList)  
        el.Add(new XAttribute(ad.GetName(at.Name.LocalName), at.Value));  
}  
// add attribute namespaces so that the tree will be serialized with  
// the aw and ad namespace prefixes  
tree1.Add(  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com")  
);  
tree2.Add(  
    new XAttribute(XNamespace.Xmlns + "ad", "http://www.adatum.com")  
);  
// create a new composite tree  
XElement root = new XElement("Root",  
    tree1,  
    tree2  
);  
Console.WriteLine(root);  
```  
  
 這個範例會產生下列輸出：  
  
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
