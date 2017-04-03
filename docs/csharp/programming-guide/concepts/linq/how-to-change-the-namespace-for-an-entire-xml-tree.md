---
title: "如何：變更整個 XML 樹狀結構的命名空間 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 1584ff3b-c77d-4241-ab62-80adfb7bfc1b
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1ce710355e410e123fb9c4129e8d7bf339d5beff
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-change-the-namespace-for-an-entire-xml-tree-c"></a>如何：變更整個 XML 樹狀結構的命名空間 (C#)
您有時候必須以程式設計的方式，變更項目或屬性的命名空間。 LINQ to XML 可以簡化這個程序。 <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=fullName> 屬性可被設定。 <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=fullName> 屬性無法設定，但您可以輕鬆將屬性複製到 <xref:System.Collections.Generic.List%601?displayProperty=fullName>、移除現有的屬性，然後新增所需新命名空間中的新屬性。  
  
 如需詳細資訊，請參閱[處理 XML 命名空間 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [修改 XML 樹狀結構 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
