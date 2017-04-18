---
title: "EXISTS (Entity SQL) | Microsoft Docs"
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
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# EXISTS (Entity SQL)
判斷集合是否為空。  
  
## 語法  
  
```  
  
[NOT] EXISTS (expression)  
```  
  
## 引數  
 `expression`  
 可傳回集合的任何有效運算式。  
  
 NOT  
 指定 EXISTS 的結果為否定運算。  
  
## 傳回值  
 如果集合不是空的則為 `true`，否則為 `false`。  
  
## 備註  
 EXISTS 是其中一個 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子。 所有 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子都會從左到右評估。 如需 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子的優先順序資訊，請參閱 [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md)。  
  
## 範例  
 下列 Entity SQL 查詢會使用 EXISTS 運算子判斷集合是否為空的。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1.  遵循 [HOW TO：執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md) 中的程序進行。  
  
2.  將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#EXISTS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#exists)]  
  
## 請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)