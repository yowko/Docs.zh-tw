---
title: 作法：篩選項目名稱 (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: b1437b4a-48aa-4546-834a-d6d3ab015fe1
ms.openlocfilehash: ccb768030e10d73b839df71093a27ff11b918650
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394333"
---
# <a name="how-to-filter-on-element-names-linq-to-xml-visual-basic"></a><span data-ttu-id="d24b7-102">如何：篩選元素名稱（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="d24b7-102">How to: Filter on Element Names (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="d24b7-103">當您呼叫可傳回 <xref:System.Collections.Generic.IEnumerable%601> 之 <xref:System.Xml.Linq.XElement> 的其中一個方法時，您可以篩選項目名稱。</span><span class="sxs-lookup"><span data-stu-id="d24b7-103">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d24b7-104">範例</span><span class="sxs-lookup"><span data-stu-id="d24b7-104">Example</span></span>  
 <span data-ttu-id="d24b7-105">這個範例會擷取子代 (Descendant) 的集合，而且該集合會篩選成僅包含具有指定之名稱的子代。</span><span class="sxs-lookup"><span data-stu-id="d24b7-105">This example retrieves a collection of descendants that is filtered to contain only descendants with the specified name.</span></span>  
  
 <span data-ttu-id="d24b7-106">此範例使用下列 XML 文件︰[範例 XML 檔：典型採購訂單 (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="d24b7-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim items As IEnumerable(Of XElement) = _  
    From el In po...<ProductName> _  
    Select el  
For Each prdName As XElement In items  
    Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)  
Next  
```  
  
 <span data-ttu-id="d24b7-107">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="d24b7-107">This code produces the following output:</span></span>  
  
```console  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 <span data-ttu-id="d24b7-108">其他傳回 <xref:System.Collections.Generic.IEnumerable%601> 集合之 <xref:System.Xml.Linq.XElement> 的方法都依照相同的模式。</span><span class="sxs-lookup"><span data-stu-id="d24b7-108">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="d24b7-109">它們的簽章類似於 <xref:System.Xml.Linq.XContainer.Elements%2A> 及 <xref:System.Xml.Linq.XContainer.Descendants%2A>。</span><span class="sxs-lookup"><span data-stu-id="d24b7-109">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="d24b7-110">下列是具有類似方法簽章之方法的完整清單：</span><span class="sxs-lookup"><span data-stu-id="d24b7-110">The following is the complete list of methods that have similar method signatures:</span></span>  
  
- <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
- <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a><span data-ttu-id="d24b7-111">範例</span><span class="sxs-lookup"><span data-stu-id="d24b7-111">Example</span></span>  
 <span data-ttu-id="d24b7-112">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="d24b7-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="d24b7-113">如需詳細資訊，請參閱[命名空間總覽（LINQ to XML）（Visual Basic）](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="d24b7-113">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="d24b7-114">此範例使用下列 XML 文件︰[範例 XML 檔：命名空間中的典型採購訂單](sample-xml-file-typical-purchase-order-in-a-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="d24b7-114">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim items As IEnumerable(Of XElement) = _  
            From el In po...<aw:ProductName> _  
            Select el  
        For Each prdName As XElement In items  
            Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="d24b7-115">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="d24b7-115">This code produces the following output:</span></span>  
  
```console  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a><span data-ttu-id="d24b7-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d24b7-116">See also</span></span>

- [<span data-ttu-id="d24b7-117">LINQ to XML 軸 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d24b7-117">LINQ to XML Axes (Visual Basic)</span></span>](linq-to-xml-axes.md)
