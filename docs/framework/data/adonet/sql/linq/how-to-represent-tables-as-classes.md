---
title: "HOW TO：將資料表表示為類別 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# HOW TO：將資料表表示為類別
使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> 屬性 \(Attribute\) 來指定類別 \(Class\)，做為與資料庫資料表相關聯的實體 \(Entity\) 類別。  
  
### 若要將類別對應至資料庫資料表  
  
-   將 <xref:System.Data.Linq.Mapping.TableAttribute> 屬性加入至類別宣告。  
  
## 範例  
 下列程式碼所建立的 `Customer` 類別，可做為與 `Customers` 資料庫資料表相關聯的實體類別。  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 如果可以推斷名稱，您就不必指定 <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> 屬性。  如果您未指定名稱，則會假設名稱就是與屬性或欄位名稱相同的名稱。  
  
## 請參閱  
 [LINQ to SQL 物件模型](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)   
 [HOW TO：使用程式碼編輯器自訂實體類別](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)