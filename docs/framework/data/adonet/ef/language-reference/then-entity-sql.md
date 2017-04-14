---
title: "THEN (Entity SQL) | Microsoft Docs"
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
  - "ESQL"
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# THEN (Entity SQL)
當 WHEN 子句評估為 `true` 時，該子句的結果。  
  
## 語法  
  
```  
  
WHEN when_expression THEN then_expression  
```  
  
## 引數  
 `when_expression`  
 任何有效的 Boolean 運算式。  
  
 `then_expression`  
 傳回集合的任何有效查詢運算式。  
  
## 備註  
 如果 `when_expression` 評估為 `true` 值，結果就是對應的 `then-expression`。 如果沒有滿足任何 WHEN 條件，就會評估 `else-expression`。 不過，如果沒有任何 `else-expression`，結果就是 null。  
  
 如需範例，請參閱 [CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)。  
  
## 範例  
 下列 Entity SQL 查詢會使用 CASE 運算式來評估一組 `Boolean` 運算式。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1.  遵循 [HOW TO：執行可傳回 PrimitiveType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md) 中的程序進行。  
  
2.  將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## 請參閱  
 [CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)   
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)