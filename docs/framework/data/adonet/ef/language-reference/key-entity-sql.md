---
title: "KEY (Entity SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# KEY (Entity SQL)
擷取參考的索引鍵，或實體運算式的索引鍵。  
  
## 語法  
  
```  
  
KEY(createref_expression)  
```  
  
## 備註  
 實體索引鍵會以指定之實體或實體參考的正確順序來包含索引鍵值。 因為多個實體集可視相同類型而定，相同索引鍵可能出現於每個實體集。 若要取得唯一的參考，請使用 `REF`。 KEY 運算子的傳回類型是資料列類型，會以相同順序來為實體的每個索引鍵包含一個欄位。  
  
 在下列範例中，Key 運算子會傳遞 BadOrder 實體的參考，並傳回那個參考的索引鍵部分。 在上述情形中，單一個欄位的資料錄類型對應至 `Id` 屬性。  
  
```  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## 範例  
 下列 Entity SQL 查詢會使用 KEY 運算子，擷取具有類型參考之運算式的索引鍵部分。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1.  遵循 [HOW TO：執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md) 中的程序進行。  
  
2.  將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#KEY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#key)]  
  
## 請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)   
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)   
 [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)   
 [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)