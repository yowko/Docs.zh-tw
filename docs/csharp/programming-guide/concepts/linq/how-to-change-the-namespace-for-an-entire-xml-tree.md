---
title: "如何：變更整個 XML 樹狀結構的命名空間 (C#)"
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ffebf1bda275eb815ff3e15538fd69de6d3b0c1a
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-change-the-namespace-for-an-entire-xml-tree-c"></a><span data-ttu-id="f038b-102">如何：變更整個 XML 樹狀結構的命名空間 (C#)</span><span class="sxs-lookup"><span data-stu-id="f038b-102">How to: Change the Namespace for an Entire XML Tree (C#)</span></span>
<span data-ttu-id="f038b-103">您有時候必須以程式設計的方式，變更項目或屬性的命名空間。</span><span class="sxs-lookup"><span data-stu-id="f038b-103">You sometimes have to programmatically change the namespace for an element or an attribute.</span></span> <span data-ttu-id="f038b-104">LINQ to XML 可以簡化這個程序。</span><span class="sxs-lookup"><span data-stu-id="f038b-104">LINQ to XML makes this easy.</span></span> <span data-ttu-id="f038b-105">您可以設定 <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=fullName> 屬性。</span><span class="sxs-lookup"><span data-stu-id="f038b-105">The <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=fullName> property can be set.</span></span> <span data-ttu-id="f038b-106">您無法設定 <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=fullName> 屬性 (Property)，但是您可以輕易地將屬性 (Attribute) 複製到 <xref:System.Collections.Generic.List%601?displayProperty=fullName>、移除現有的屬性 (Attribute)，然後加入所需之新命名空間中的新屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="f038b-106">The <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=fullName> property cannot be set, but you can easily copy the attributes into a <xref:System.Collections.Generic.List%601?displayProperty=fullName>, remove the existing attributes, and then add new attributes that are in the new desired namespace.</span></span>  
  
 <span data-ttu-id="f038b-107">如需詳細資訊，請參閱[處理 XML 命名空間 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="f038b-107">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f038b-108">範例</span><span class="sxs-lookup"><span data-stu-id="f038b-108">Example</span></span>  
 <span data-ttu-id="f038b-109">下列程式碼會在沒有命名空間中建立兩個 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="f038b-109">The following code creates two XML trees in no namespace.</span></span> <span data-ttu-id="f038b-110">接著，它會變更每個樹狀結構的命名空間，然後將這些命名空間結合成單一樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="f038b-110">It then changes the namespace of each of the trees, and combines them into a single tree.</span></span>  
  
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
  
 <span data-ttu-id="f038b-111">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="f038b-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f038b-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f038b-112">See Also</span></span>  
 [<span data-ttu-id="f038b-113">修改 XML 樹狀結構 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f038b-113">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)

