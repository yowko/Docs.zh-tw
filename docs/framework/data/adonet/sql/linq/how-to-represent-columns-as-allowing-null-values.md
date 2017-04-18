---
title: "HOW TO：將資料行表示為允許 Null 值 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# HOW TO：將資料行表示為允許 Null 值
在 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 \(Attribute\) 上使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> 屬性 \(Property\)，指定相關聯的資料庫資料行可以保存 null 值。  
  
 如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>。  
  
### 若要指定資料行允許 null 值  
  
1.  將 <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> 屬性 \(Property\) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 \(Attribute\)。  
  
2.  將 <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> 屬性 \(Property\) 值設定為 `true`。  
  
## 請參閱  
 [LINQ to SQL 物件模型](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)   
 [HOW TO：使用程式碼編輯器自訂實體類別](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)