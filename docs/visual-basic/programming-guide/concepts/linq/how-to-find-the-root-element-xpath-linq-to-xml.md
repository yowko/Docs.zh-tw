---
title: HOW TO：尋找根項目 (XPATH-LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 72c3aed5-9522-4454-a876-2070aad13f2e
ms.openlocfilehash: 6a08817c16bafb2ba1f91931f9718d6ef5053fb9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687332"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-visual-basic"></a>HOW TO：尋找根項目 (XPATH-LINQ to XML) (Visual Basic)
本主題顯示如何利用 XPath 和 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 取得根項目。  
  
 XPath 運算式為：  
  
 `/PurchaseOrders`  
  
## <a name="example"></a>範例  
 這個範例會尋找根項目。  
  
 此範例使用下列 XML 文件：[範例 XML 檔：多份採購訂單 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。  
  
```vb  
Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")  
  
' LINQ to XML query  
Dim el1 As XElement = po.Root  
  
' XPath expression  
Dim el2 As XElement = po.XPathSelectElement("/PurchaseOrders")  
  
If el1 Is el2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(el1.Name)  
```  
  
 這個範例會產生下列輸出：  
  
```  
Results are identical  
PurchaseOrders  
```  
  
## <a name="see-also"></a>另請參閱
- [LINQ to XML (Visual Basic) 的 XPath 使用者適用的](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
