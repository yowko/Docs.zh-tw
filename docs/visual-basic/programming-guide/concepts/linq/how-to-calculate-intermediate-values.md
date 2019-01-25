---
title: HOW TO：計算中繼值 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 933a97b2-dfe7-4f4d-94ad-e6e20df84abd
ms.openlocfilehash: 2908abae5f4c4738752fba62c36da340fb3b2ba3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628817"
---
# <a name="how-to-calculate-intermediate-values-visual-basic"></a><span data-ttu-id="fa9d2-102">HOW TO：計算中繼值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa9d2-102">How to: Calculate Intermediate Values (Visual Basic)</span></span>
<span data-ttu-id="fa9d2-103">這個範例顯示如何計算可用於排序、篩選與選取的中繼值。</span><span class="sxs-lookup"><span data-stu-id="fa9d2-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa9d2-104">範例</span><span class="sxs-lookup"><span data-stu-id="fa9d2-104">Example</span></span>  
 <span data-ttu-id="fa9d2-105">下列範例使用 `Let` 子句。</span><span class="sxs-lookup"><span data-stu-id="fa9d2-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="fa9d2-106">此範例使用下列 XML 文件：[範例 XML 檔：數值資料 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="fa9d2-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
Dim extensions As IEnumerable(Of Decimal) = _  
    From el In root.<Data> _  
    Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _  
    Where extension > 25 _  
    Order By extension _  
    Select extension  
For Each ex As Decimal In extensions  
    Console.WriteLine(ex)  
Next  
```  
  
 <span data-ttu-id="fa9d2-107">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="fa9d2-107">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="fa9d2-108">範例</span><span class="sxs-lookup"><span data-stu-id="fa9d2-108">Example</span></span>  
 <span data-ttu-id="fa9d2-109">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="fa9d2-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="fa9d2-110">如需詳細資訊，請參閱 <<c0> [ 處理 XML 命名空間 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="fa9d2-110">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="fa9d2-111">此範例使用下列 XML 文件：[範例 XML 檔：命名空間中的數值資料](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="fa9d2-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns="http://www.adatum.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("DataInNamespace.xml")  
        Dim extensions As IEnumerable(Of Decimal) = _  
            From el In root.<Data> _  
            Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _  
            Where extension > 25 _  
            Order By extension _  
            Select extension  
        For Each ex As Decimal In extensions  
            Console.WriteLine(ex)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="fa9d2-112">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="fa9d2-112">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="see-also"></a><span data-ttu-id="fa9d2-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa9d2-113">See also</span></span>
- [<span data-ttu-id="fa9d2-114">基本查詢 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa9d2-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
