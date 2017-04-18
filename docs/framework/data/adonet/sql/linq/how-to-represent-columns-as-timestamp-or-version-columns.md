---
title: "HOW TO：將資料行表示為時間戳記或版本資料行 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# HOW TO：將資料行表示為時間戳記或版本資料行
使用 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 \(Attribute\) 的 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> 屬性 \(Property\)，指定欄位或屬性 \(Property\) 以表示可保存資料庫時間戳記或版本號碼的資料庫資料行。  
  
 如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>。  
  
### 若要指定欄位或屬性以表示時間戳記或版本資料行  
  
1.  將 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> 屬性 \(Property\) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 \(Attribute\)。  
  
2.  將 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> 屬性 \(Property\) 值設定為 `true`。  
  
## 請參閱  
 [LINQ to SQL 物件模型](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)   
 [HOW TO：指定要測試哪些成員是否發生並行衝突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)   
 [HOW TO：使用程式碼編輯器自訂實體類別](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)