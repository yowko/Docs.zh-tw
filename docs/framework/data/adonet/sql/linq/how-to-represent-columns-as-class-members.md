---
title: "HOW TO：將資料行表示為類別成員 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7ab28021-4d15-4d9c-bf2e-6ccc0daa7d1a
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# HOW TO：將資料行表示為類別成員
使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 \(Attribute\)，可將欄位或屬性 \(Property\) 與資料庫資料行產生關聯。  
  
### 若要將欄位或屬性 \(Property\) 對應至資料庫資料行  
  
-   將 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 \(Attribute\) 加入至屬性 \(Property\) 或欄位宣告。  
  
## 範例  
 下列程式碼會將 `Customer` 類別中的 `CustomerID` 欄位對應至 `Customers` 資料庫資料表中的 `CustomerID` 資料行。  
  
 [!code-csharp[DLinqCustomize#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#2)]
 [!code-vb[DLinqCustomize#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#2)]  
  
 如果可以推斷名稱，您就不必指定 <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> 屬性。  如果您未指定名稱，則會假設名稱就是與屬性或欄位名稱相同的名稱。  
  
## 請參閱  
 [LINQ to SQL 物件模型](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)   
 [HOW TO：使用程式碼編輯器自訂實體類別](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)