---
title: "DEREF (Entity SQL) | Microsoft Docs"
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
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# DEREF (Entity SQL)
對參考值取值並且產生該取值的結果。  
  
## 語法  
  
```  
  
SELECT DEREF ( o.expression) from Table as o;  
```  
  
## 引數  
 `expression`  
 傳回集合的任何有效查詢運算式。  
  
## 傳回值  
 所參考之實體的值。  
  
## 備註  
 DEREF 運算子會對參考值取值並且產生該取值的結果。 舉例來講，假設  `r`  是 ref\<T\> 類型的參考， `Deref``(r)`  是產生  `r` 所參考之實體的  `T`  類型的運算式。 如果此參數值為 null，或為懸空 \(也就是參考的目標不存在\)，DEREF 運算子的結果就會是 null。  
  
## 範例  
 以下 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢使用 DEREF 運算子對參考值取值並且產生該取值的結果。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1.  遵循 [HOW TO：執行可傳回 PrimitiveType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md) 中的程序進行。  
  
2.  將下列查詢當成引數傳遞至 ExecutePrimitiveTypeQuery 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#DEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#deref)]  
  
## 請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)   
 [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)   
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)   
 [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)   
 [可為 Null 的結構類型](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)