---
title: "如何︰ 投影匿名類型 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 30b42987-0e0e-4b2b-adb1-5255ddfbcd7b
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a9edd260e9bc36449445ee835648573c7bc9c229
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-project-an-anonymous-type-visual-basic"></a>如何︰ 投影匿名類型 (Visual Basic)
在某些情況下，即使您知道您只會短期使用新型別，您可能還是想要將查詢規劃為該型別。 建立新型別只用於這個規劃太費工。 在此情況下，較有效率的方法為規劃匿名型別。 匿名型別可讓您定義類別，然後宣告並初始化該類別的物件，而不用提供類別一個名稱。  
  
 匿名型別是數學概念的 C# 實作*tuple*。 數學術語「Tuple」源自於 single、double、triple、quadruple、quintuple、n-tuple 序列。 這表示有限的物件順序，每個都有特定的型別。 有時候，這稱為成對的名稱/值清單。 比方說，在地址內容[範例 XML 檔︰ 典型採購訂單 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md)無法表示 XML 文件，如下所示︰  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 當您建立匿名型別的執行個體時，將它視為建立順序 n 的 Tuple 比較方法。 如果您撰寫可在 `Select` 子句中建立 Tuple 的查詢，該查詢會傳回 Tuple 的 `IEnumerable`。  
  
## <a name="example"></a>範例  
 在這個範例中，`Select` 子句會規劃匿名型別。 然後，此範例會使用 `Dim` 來建立 `IEnumerable` 物件。 在 `For Each` 迴圈中，反覆運算變數會變成在查詢運算式中建立之匿名型別的執行個體。  
  
 這個範例會使用下列 XML 文件︰[範例 XML 檔︰ 客戶和訂單 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md)。  
  
```vb  
Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")  
Dim custList = _  
    From el In custOrd.<Customers>.<Customer> _  
    Select New With { _  
        .CustomerID = el.@<CustomerID>, _  
        .CompanyName = el.<CompanyName>.Value, _  
        .ContactName = el.<ContactName>.Value _  
    }  
For Each cust In custList  
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName)  
Next  
  
```  
  
 此程式碼會產生下列輸出：  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>另請參閱  
 [投影和轉換 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
