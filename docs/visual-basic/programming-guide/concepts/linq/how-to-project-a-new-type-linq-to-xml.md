---
title: "如何︰ 投影新類型 (LINQ to XML) (Visual Basic) |Microsoft 文件"
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
ms.assetid: 8cfb24f5-89b2-4cfb-b85d-e7963f8f1845
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b0e3149ca2fb5e36ebc759421e9489cbfe3dde5f
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017


---
# <a name="how-to-project-a-new-type-linq-to-xml-visual-basic"></a><span data-ttu-id="722d6-102">如何︰ 投影新類型 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="722d6-102">How to: Project a New Type (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="722d6-103">本章節中的其他範例顯示的查詢會傳回結果，當做<xref:System.Collections.Generic.IEnumerable%601>的<xref:System.Xml.Linq.XElement>，<xref:System.Collections.Generic.IEnumerable%601>的`string`，和<xref:System.Collections.Generic.IEnumerable%601>的`int`。</xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.Generic.IEnumerable%601> </xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="722d6-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="722d6-104">這些是常見的結果型別，但這些型別不適用於每個案例。</span><span class="sxs-lookup"><span data-stu-id="722d6-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="722d6-105">在許多情況下，您會想要傳回查詢<xref:System.Collections.Generic.IEnumerable%601>某個其他型別的。</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="722d6-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="722d6-106">範例</span><span class="sxs-lookup"><span data-stu-id="722d6-106">Example</span></span>  
 <span data-ttu-id="722d6-107">此範例顯示如何具現化 `Select` 子句中的物件。</span><span class="sxs-lookup"><span data-stu-id="722d6-107">This example shows how to instantiate objects in the `Select` clause.</span></span> <span data-ttu-id="722d6-108">此程式碼會先利用建構函式定義新的類別，然後修改 `Select` 陳述式，讓運算式成為新類別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="722d6-108">The code first defines a new class with a constructor, and then modifies the `Select` statement so that the expression is a new instance of the new class.</span></span>  
  
 <span data-ttu-id="722d6-109">這個範例會使用下列 XML 文件︰[範例 XML 檔︰ 典型採購訂單 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="722d6-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Public Class NameQty  
    Public name As String  
    Public qty As Integer  
    Public Sub New(ByVal n As String, ByVal q As Integer)  
        name = n  
        qty = q  
    End Sub  
End Class  
  
Public Class Program  
    Shared Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
  
        Dim nqList As IEnumerable(Of NameQty) = _  
            From n In po...<Item> _  
            Select New NameQty( _  
                n.<ProductName>.Value, CInt(n.<Quantity>.Value))  
  
        For Each n As NameQty In nqList  
            Console.WriteLine(n.name & ":" & n.qty)  
        Next  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="722d6-110">這個範例會使用`M:System.Xml.Linq.XElement.Element`引進 > 主題中的方法[How to︰ 擷取單一子項目 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="722d6-110">This example uses the `M:System.Xml.Linq.XElement.Element` method that was introduced in the topic [How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="722d6-111">它也會使用轉換以擷取 `M:System.Xml.Linq.XElement.Element` 方法所傳回的元素值。</span><span class="sxs-lookup"><span data-stu-id="722d6-111">It also uses casts to retrieve the values of the elements that are returned by the `M:System.Xml.Linq.XElement.Element` method.</span></span>  
  
 <span data-ttu-id="722d6-112">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="722d6-112">This example produces the following output:</span></span>  
  
```  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a><span data-ttu-id="722d6-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="722d6-113">See Also</span></span>  
 [<span data-ttu-id="722d6-114">投影和轉換 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="722d6-114">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
