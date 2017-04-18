---
title: "如何︰ 尋找根項目 (XPATH-LINQ to XML) (Visual Basic) |Microsoft 文件"
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
ms.assetid: 72c3aed5-9522-4454-a876-2070aad13f2e
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4763181b56037f3efe7e3a2e4e31651b515e1424
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-visual-basic"></a>如何︰ 尋找根項目 (XPATH-LINQ to XML) (Visual Basic)
本主題顯示如何利用 XPath 和 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 取得根項目。  
  
 XPath 運算式為：  
  
 `/PurchaseOrders`  
  
## <a name="example"></a>範例  
 這個範例會尋找根項目。  
  
 這個範例會使用下列 XML 文件︰[範例 XML 檔︰ 多份採購訂單 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。  
  
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
 [LINQ to XML 的 XPath 使用者 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
