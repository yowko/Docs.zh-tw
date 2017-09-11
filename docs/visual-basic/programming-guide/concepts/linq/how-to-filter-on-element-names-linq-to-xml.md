---
title: "如何︰ 篩選項目名稱 (LINQ to XML) (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: b1437b4a-48aa-4546-834a-d6d3ab015fe1
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 07f7867b0fc5cf79ba5ce06f95b07b5c538e83d3
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-filter-on-element-names-linq-to-xml-visual-basic"></a><span data-ttu-id="8b45a-102">如何︰ 篩選項目名稱 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b45a-102">How to: Filter on Element Names (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="8b45a-103">當您呼叫其中一個方法會傳回<xref:System.Collections.Generic.IEnumerable%601>的<xref:System.Xml.Linq.XElement>，您可以篩選項目的名稱。</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="8b45a-103">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b45a-104">範例</span><span class="sxs-lookup"><span data-stu-id="8b45a-104">Example</span></span>  
 <span data-ttu-id="8b45a-105">這個範例會擷取子代 (Descendant) 的集合，而且該集合會篩選成僅包含具有指定之名稱的子代。</span><span class="sxs-lookup"><span data-stu-id="8b45a-105">This example retrieves a collection of descendants that is filtered to contain only descendants with the specified name.</span></span>  
  
 <span data-ttu-id="8b45a-106">這個範例會使用下列 XML 文件︰[範例 XML 檔︰ 典型採購訂單 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="8b45a-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
<span data-ttu-id="8b45a-107"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="8b45a-107"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="8b45a-108">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="8b45a-108">This code produces the following output:</span></span>  
  
<span data-ttu-id="8b45a-109"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="8b45a-109"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="8b45a-110">其他的方法會傳回<xref:System.Collections.Generic.IEnumerable%601>的<xref:System.Xml.Linq.XElement>集合依循相同的模式。</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="8b45a-110">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="8b45a-111">它們的簽章會類似於<xref:System.Xml.Linq.XContainer.Elements%2A>與<xref:System.Xml.Linq.XContainer.Descendants%2A>。</xref:System.Xml.Linq.XContainer.Descendants%2A> </xref:System.Xml.Linq.XContainer.Elements%2A></span><span class="sxs-lookup"><span data-stu-id="8b45a-111">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="8b45a-112">下列是具有類似方法簽章之方法的完整清單：</span><span class="sxs-lookup"><span data-stu-id="8b45a-112">The following is the complete list of methods that have similar method signatures:</span></span>  
  
-   <span data-ttu-id="8b45a-113"><xref:System.Xml.Linq.XNode.Ancestors%2A></xref:System.Xml.Linq.XNode.Ancestors%2A></span><span class="sxs-lookup"><span data-stu-id="8b45a-113"><xref:System.Xml.Linq.XNode.Ancestors%2A></span></span>  
  
-   <span data-ttu-id="8b45a-114"><xref:System.Xml.Linq.XContainer.Descendants%2A></xref:System.Xml.Linq.XContainer.Descendants%2A></span><span class="sxs-lookup"><span data-stu-id="8b45a-114"><xref:System.Xml.Linq.XContainer.Descendants%2A></span></span>  
  
-   <span data-ttu-id="8b45a-115"><xref:System.Xml.Linq.XContainer.Elements%2A></xref:System.Xml.Linq.XContainer.Elements%2A></span><span class="sxs-lookup"><span data-stu-id="8b45a-115"><xref:System.Xml.Linq.XContainer.Elements%2A></span></span>  
  
-   <span data-ttu-id="8b45a-116"><xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A></xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A></span><span class="sxs-lookup"><span data-stu-id="8b45a-116"><xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A></span></span>  
  
-   <span data-ttu-id="8b45a-117"><xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A></xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A></span><span class="sxs-lookup"><span data-stu-id="8b45a-117"><xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A></span></span>  
  
-   <span data-ttu-id="8b45a-118"><xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A></xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A></span><span class="sxs-lookup"><span data-stu-id="8b45a-118"><xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A></span></span>  
  
-   <span data-ttu-id="8b45a-119"><xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A></xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A></span><span class="sxs-lookup"><span data-stu-id="8b45a-119"><xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A></span></span>  
  
## <a name="example"></a><span data-ttu-id="8b45a-120">範例</span><span class="sxs-lookup"><span data-stu-id="8b45a-120">Example</span></span>  
 <span data-ttu-id="8b45a-121">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="8b45a-121">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="8b45a-122">如需詳細資訊，請參閱[處理 XML 命名空間 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="8b45a-122">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="8b45a-123">這個範例會使用下列 XML 文件︰[範例 XML 檔︰ 命名空間中的典型採購訂單](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="8b45a-123">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="8b45a-124">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="8b45a-124">This code produces the following output:</span></span>  
  
```  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a><span data-ttu-id="8b45a-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b45a-125">See Also</span></span>  
 [<span data-ttu-id="8b45a-126">LINQ to XML 軸心方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b45a-126">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
