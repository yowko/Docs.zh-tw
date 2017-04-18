---
title: "ANYELEMENT (Entity SQL) | Microsoft Docs"
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
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# ANYELEMENT (Entity SQL)
從多重值集合中擷取元素。  
  
## 語法  
  
```  
  
ANYELEMENT (expression)  
```  
  
## 引數  
 `expression`  
 傳回可從中擷取元素之集合的任何有效查詢運算式。  
  
## 傳回值  
 如果集合具有多個元素，就是集合中的單一元素或任意元素。如果集合是空的，則傳回 `null`。 如果 ```collection``` 是類型 `Collection<T>` 的集合，則  `ANYELEMENT(collection)`  就是產生類型 `T` 執行個體的有效運算式。  
  
## 備註  
 ANYELEMENT 會從多重值集合中擷取任意元素。 例如，下列範例會嘗試從 `Customers` 集合中擷取單一元素。  
  
```  
ANYELEMENT(Customers)  
```  
  
## 範例  
 下列 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢會使用 ANYELEMENT 運算子，從多重值集合中擷取元素。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1.  遵循 [HOW TO：執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md) 中的程序進行。  
  
2.  將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## 請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)   
 [可為 Null 的結構類型](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)