---
title: "如何︰ 尋找前一個同層級項目 (XPATH-LINQ to XML) (Visual Basic) |Microsoft 文件"
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
ms.assetid: 59055718-d0a7-4db3-8901-18dd33587703
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 250028f73eff7aad3926ee4916aef7d118b6fbea
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-find-preceding-siblings-xpath-linq-to-xml-visual-basic"></a>如何︰ 尋找前一個同層級項目 (XPATH-LINQ to XML) (Visual Basic)
本主題會比較 XPath`preceding-sibling`座標軸[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]子<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName>軸。</xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName>  
  
 XPath 運算式為：  
  
 `preceding-sibling::*`  
  
 請注意，這兩者的結果<xref:System.Xml.XPath.Extensions.XPathSelectElements%2A>和<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName>為文件順序。</xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName> </xref:System.Xml.XPath.Extensions.XPathSelectElements%2A>  
  
## <a name="example"></a>範例  
 下列範例會尋找 `FullAddress` 項目，然後使用 `preceding-sibling` 座標軸擷取先前的項目。  
  
 這個範例會使用下列 XML 文件︰[範例 XML 檔︰ 客戶和訂單 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md)。  
  
```vb  
Dim co As XElement = XElement.Load("CustomersOrders.xml")  
Dim add As XElement = co.<Customers>.<Customer>. _  
        <FullAddress>.FirstOrDefault  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = add.ElementsBeforeSelf()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = add.XPathSelectElements("preceding-sibling::*")  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list2  
    Console.WriteLine(el)  
Next  
```  
  
 這個範例會產生下列輸出：  
  
```  
Results are identical  
<CompanyName>Great Lakes Food Market</CompanyName>  
<ContactName>Howard Snyder</ContactName>  
<ContactTitle>Marketing Manager</ContactTitle>  
<Phone>(503) 555-7555</Phone>  
```  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to XML 的 XPath 使用者 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
