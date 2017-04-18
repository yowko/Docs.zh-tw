---
title: "基本資料型別 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eca2c472-9548-4800-bd31-5d8d9f11752b
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 基本資料型別
由於 LINQ to SQL 查詢會先轉譯成 Transact\-SQL，然後才能在 Microsoft SQL Server 上執行。  因此，在基本資料型別方面，LINQ to SQL 所支援的許多內建功能都與 SQL Server 相同。  
  
## 轉型  
 如果 SQL Server 內具有與來源 CLR 型別到目標 CLR 型別之隱含或明確轉換 \(Cast\) 類似的有效轉換，就會啟用這類隱含或明確轉換。  如需 CLR 轉型的詳細資訊，請參閱 [CType 函式](../Topic/CType%20Function%20\(Visual%20Basic\).md) \([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]\) 和 [as](../Topic/as%20\(C%23%20Reference\).md)。  轉換 \(Conversion\) 之後，轉換 \(Cast\) 會變更在 CLR 運算式上執行的作業行為，使其符合其他會自然對應至目的型別之 CLR 運算式的行為。在繼承對應的內容中，轉換 \(Cast\) 也是可以轉譯的。  物件可以轉換 \(Cast\) 為更特定的實體子型別，因此可以存取物件的子型別特定資料。  
  
## 等號比較運算子  
 LINQ to SQL 支援針對 LINQ to SQL 查詢內部的基本資料型別使用下列等號比較運算子：  
  
-   等號和不等比較運算子：數值 <xref:System.Boolean>、<xref:System.DateTime> 和 <xref:System.TimeSpan> 型別都支援等號和不等比較運算子。  如需 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 運算子 `=` 和 `<>` 的詳細資訊，請參閱[Comparison Operators](../Topic/Comparison%20Operators%20\(Visual%20Basic\).md)。如需 C\# 比較運算子 `==` 和 `!=` 的詳細資訊，請分別參閱 [\=\= 運算子](../Topic/==%20Operator%20\(C%23%20Reference\).md) 和 [\!\= 運算子](../Topic/!=%20Operator%20\(C%23%20Reference\).md)  
  
-   Is 運算子：使用繼承對應時，`IS` 運算子具有支援的轉譯。  它可以用來判斷物件是否為特定實體型別，而且可以轉譯為鑑別子資料行上的檢查，而不需要直接測試鑑別子資料行。  如需 Visual Basic 和 C\# Is 運算子的詳細資訊，請參閱 [Is Operator](../Topic/Is%20Operator%20\(Visual%20Basic\).md) 和 [is](../Topic/is%20\(C%23%20Reference\).md)。  
  
## 請參閱  
 [SQL\-CLR 型別對應](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)   
 [資料型別和函式](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)