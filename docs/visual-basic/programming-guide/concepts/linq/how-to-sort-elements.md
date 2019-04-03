---
title: HOW TO：排序項目 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c2c09279-6c8a-482e-8e71-b1453a815052
ms.openlocfilehash: b6f2e0056582e60066b2c0715a663022b72a6c9c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841210"
---
# <a name="how-to-sort-elements-visual-basic"></a>HOW TO：排序項目 (Visual Basic)
此範例顯示如何撰寫排序其結果的查詢。  
  
## <a name="example"></a>範例  
 此範例使用下列 XML 文件：[XML 範例檔：數值資料 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md)。  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
Dim prices As IEnumerable(Of Decimal) = _  
    From el In root.<Data> _  
    Let price = Convert.ToDecimal(el.<Price>.Value) _  
    Order By (price) _  
    Select price  
For Each el As Decimal In prices  
    Console.WriteLine(el)  
Next  
```  
  
 此程式碼會產生下列輸出：  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a>範例  
 下列範例顯示命名空間中之 XML 的相同查詢。 如需詳細資訊，請參閱 <<c0> [ 處理 XML 命名空間 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)。  
  
 此範例使用下列 XML 文件：[XML 範例檔：命名空間中的數值資料](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md)。  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("DataInNamespace.xml")  
        Dim prices As IEnumerable(Of Decimal) = _  
            From el In root.<Data> _  
            Let price = Convert.ToDecimal(el.<Price>.Value) _  
            Order By (price) _  
            Select price  
        For Each el As Decimal In prices  
            Console.WriteLine(el)  
        Next  
    End Sub  
End Module  
```  
  
 此程式碼會產生下列輸出：  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a>另請參閱

- [排序資料](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)
- [基本查詢 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
