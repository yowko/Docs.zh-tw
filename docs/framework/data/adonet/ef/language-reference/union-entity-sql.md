---
title: "UNION (Entity SQL) | Microsoft Docs"
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
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# UNION (Entity SQL)
將二個或多個查詢的結果結合成單一集合。  
  
## 語法  
  
```  
  
          expression  
UNION [ ALL ]  
expression  
```  
  
## 引數  
 `expression`  
 任何有效的查詢運算式，該運算式會傳回與此集合結合的集合。所有運算式都必須具有與 `expression` 相同的型別或是共同基底類型或衍生型別。  
  
 UNION  
 指定要結合多個集合，並當做單一集合傳回。  
  
 ALL  
 指定要結合多個集合，並當做單一集合傳回，包括重複的項目。 若未指定，就會從結果集合中移除重複的項目。  
  
## 傳回值  
 具有與 `expression` 相同的型別或是共同基底類型或衍生型別的集合。  
  
## 備註  
 UNION 是其中一個 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子。 所有 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子都會從左到右評估。 如需 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子的優先順序資訊，請參閱 [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md)。  
  
## 範例  
 下列 Entity SQL 查詢會使用 UNION ALL 運算子，將兩個查詢的結果結合成單一集合。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1.  遵循 [HOW TO：執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md) 中的程序進行。  
  
2.  將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#UNION](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#union)]  
  
## 請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)