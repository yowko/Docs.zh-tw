---
title: HOW TO：尋找兩個位置路徑 (XPATH-LINQ to XML) 的聯集 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c82c09b4-cb0a-47ec-8cc3-a124144c2788
ms.openlocfilehash: 662cad329f4837d26b25d56f15d323fe623b05c2
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843678"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-visual-basic"></a>HOW TO：尋找兩個位置路徑 (XPATH-LINQ to XML) 的聯集 (Visual Basic)
XPath 可讓您尋找兩個 XPath 位置路徑結果的等位。  
  
 XPath 運算式為：  
  
 `//Category|//Price`  
  
 您可以使用 <xref:System.Linq.Enumerable.Concat%2A> 標準查詢運算子，達到相同的結果。  
  
## <a name="example"></a>範例  
 此範例會尋找所有 `Category` 項目與所有 `Price` 項目，然後將它們串連為單一集合。 請注意，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢會呼叫 <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> 來排列結果。 XPath 運算式評估的結果也是以文件的順序排列。  
  
 此範例使用下列 XML 文件：[XML 範例檔：數值資料 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md)。  
  
```vb  
Dim data As XDocument = XDocument.Load("Data.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    data...<Category>.Concat(data...<Price>).InDocumentOrder()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = _  
    data.XPathSelectElements("//Category|//Price")  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 這個範例會產生下列輸出：  
  
```  
Results are identical  
<Category>A</Category>  
<Price>24.50</Price>  
<Category>B</Category>  
<Price>89.99</Price>  
<Category>A</Category>  
<Price>4.95</Price>  
<Category>A</Category>  
<Price>66.00</Price>  
<Category>B</Category>  
<Price>.99</Price>  
<Category>A</Category>  
<Price>29.00</Price>  
<Category>B</Category>  
<Price>6.99</Price>  
```  
  
## <a name="see-also"></a>另請參閱

- [LINQ to XML (Visual Basic) 的 XPath 使用者適用的](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
