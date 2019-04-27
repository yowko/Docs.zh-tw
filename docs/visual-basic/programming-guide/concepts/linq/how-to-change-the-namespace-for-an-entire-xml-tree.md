---
title: HOW TO：變更整個 XML 樹狀結構 (Visual Basic) 的命名空間
ms.date: 07/20/2015
ms.assetid: 1837324b-5cb5-4fa8-95b9-3071efa0f913
ms.openlocfilehash: 5a5926583990e3abda49ceaee4786a2158275a3b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61855007"
---
# <a name="how-to-change-the-namespace-for-an-entire-xml-tree-visual-basic"></a><span data-ttu-id="36f63-102">HOW TO：變更整個 XML 樹狀結構 (Visual Basic) 的命名空間</span><span class="sxs-lookup"><span data-stu-id="36f63-102">How to: Change the Namespace for an Entire XML Tree (Visual Basic)</span></span>
<span data-ttu-id="36f63-103">您有時候必須以程式設計的方式，變更項目或屬性的命名空間。</span><span class="sxs-lookup"><span data-stu-id="36f63-103">You sometimes have to programmatically change the namespace for an element or an attribute.</span></span> <span data-ttu-id="36f63-104">LINQ to XML 可以簡化這個程序。</span><span class="sxs-lookup"><span data-stu-id="36f63-104">LINQ to XML makes this easy.</span></span> <span data-ttu-id="36f63-105">您可以設定 <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="36f63-105">The <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> property can be set.</span></span> <span data-ttu-id="36f63-106">您無法設定 <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> 屬性 (Property)，但是您可以輕易地將屬性 (Attribute) 複製到 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>、移除現有的屬性 (Attribute)，然後加入所需之新命名空間中的新屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="36f63-106">The <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> property cannot be set, but you can easily copy the attributes into a <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, remove the existing attributes, and then add new attributes that are in the new desired namespace.</span></span>  
  
 <span data-ttu-id="36f63-107">如需詳細資訊，請參閱 <<c0> [ 處理 XML 命名空間 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="36f63-107">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="36f63-108">範例</span><span class="sxs-lookup"><span data-stu-id="36f63-108">Example</span></span>  
 <span data-ttu-id="36f63-109">下列程式碼會在沒有命名空間中建立兩個 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="36f63-109">The following code creates two XML trees in no namespace.</span></span> <span data-ttu-id="36f63-110">接著，它會變更每個樹狀結構的命名空間，然後將這些命名空間結合成單一樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="36f63-110">It then changes the namespace of each of the trees, and combines them into a single tree.</span></span>  
  
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
' change the namespace of every element and attribute in the first tree  
For Each el As XElement In tree1.DescendantsAndSelf  
    el.Name = aw.GetName(el.Name.LocalName)  
    Dim atList As List(Of XAttribute) = el.Attributes().ToList()  
    el.Attributes().Remove()  
    For Each at As XAttribute In atList  
        el.Add(New XAttribute(aw.GetName(at.Name.LocalName), at.Value))  
    Next  
Next  
' change the namespace of every element and attribute in the second tree  
For Each el As XElement In tree2.DescendantsAndSelf()  
    el.Name = ad.GetName(el.Name.LocalName)  
    Dim atList As List(Of XAttribute) = el.Attributes().ToList()  
    el.Attributes().Remove()  
    For Each at As XAttribute In atList  
        el.Add(New XAttribute(ad.GetName(at.Name.LocalName), at.Value))  
    Next  
Next  
' add attribute namespaces so that the tree will be serialized with  
' the aw and ad namespace prefixes  
tree1.Add( _  
    New XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com") _  
)  
tree2.Add( _  
    New XAttribute(XNamespace.Xmlns + "ad", "http://www.adatum.com") _  
)  
' create a new composite tree  
Dim root As XElement = _  
    <Root>  
        <%= tree1 %>  
        <%= tree2 %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="36f63-111">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="36f63-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="36f63-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36f63-112">See also</span></span>

- [<span data-ttu-id="36f63-113">修改 XML 樹狀結構 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36f63-113">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
