---
title: "HOW TO：指定私用儲存欄位 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a40e816-cc6e-43a0-b32a-9caaa0ab6912
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# HOW TO：指定私用儲存欄位
使用 <xref:System.Data.Linq.Mapping.DataAttribute> 屬性 \(Attribute\) 的 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> 屬性 \(Property\)，指定基礎儲存欄位的名稱。  
  
 如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>。  
  
### 若要指定基礎儲存欄位的名稱  
  
1.  將 <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> 屬性 \(Property\) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 \(Attribute\)。  
  
2.  指定欄位名稱做為 <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> 屬性 \(Property\) 的值。  
  
## 請參閱  
 [LINQ to SQL 物件模型](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)   
 [HOW TO：使用程式碼編輯器自訂實體類別](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)