---
title: "HOW TO：指定資料庫的資料型別 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# HOW TO：指定資料庫的資料型別
在 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 \(Attribute\) 上使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> 屬性 \(Property\)，可以指定 T\-SQL 資料表宣告中用來定義資料行的確切文字。  
  
 只有在計劃使用 <xref:System.Data.Linq.DataContext.CreateDatabase%2A> 建立資料庫執行個體時，才必須指定 <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> 屬性 \(Property\)。  
  
 如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>。  
  
### 若要指定文字以定義 T\-SQL 資料表中的資料型別  
  
1.  將 <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> 屬性 \(Property\) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 \(Attribute\)。  
  
2.  將 <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> 屬性的值設定為 T\-SQL 使用的確切文字。  
  
## 請參閱  
 [LINQ to SQL 物件模型](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)   
 [HOW TO：使用程式碼編輯器自訂實體類別](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)