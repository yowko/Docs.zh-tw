---
title: 作法：尋找子代元素（XPath-LINQ to XML）（Visual Basic）
ms.date: 07/20/2015
ms.assetid: e7e2dc9e-bda9-420d-a5b1-4fabf1cca46b
ms.openlocfilehash: 3ee496c1a3e797a8edaf5878d9832583396a851f
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250127"
---
# <a name="how-to-find-descendant-elements-xpath-linq-to-xml-visual-basic"></a>作法：尋找子代元素（XPath-LINQ to XML）（Visual Basic）
本主題顯示如何利用特定名稱取得子代項目。  
  
 XPath 運算式為 `//Name`。  
  
## <a name="example"></a>範例  
 此範例會尋找名稱為 `Name` 的所有子代。  
  
 此範例使用下列 XML 文件：[XML 範例檔：多個訂購單 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。  
  
```vb  
      Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = po...<Name>  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = po.XPathSelectElements("//Name")  
  
If (list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count()) Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 這個範例會產生下列輸出：  
  
```console
Results are identical  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
## <a name="see-also"></a>另請參閱

- [XPath 使用者的 LINQ to XML （Visual Basic）](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
