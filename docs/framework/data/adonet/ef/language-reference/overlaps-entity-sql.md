---
title: "OVERLAPS (Entity SQL) | Microsoft Docs"
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
ms.assetid: 41743e89-79cb-4d7b-8a27-355b45024b61
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# OVERLAPS (Entity SQL)
判斷兩個集合是否有共同項目。  
  
## 語法  
  
```  
  
expression OVERLAPS expression  
```  
  
## 引數  
 `expression`  
 任何有效的查詢運算式，該運算式會傳回要與另一個查詢運算式傳回之集合相比較的集合。 所有運算式都必須具有與 `expression` 相同的型別或是共同基底型別或衍生型別。  
  
## 傳回值  
 如果兩個集合有共同項目則為 `true`；否則為 `false`。  
  
## 備註  
 OVERLAPS 提供的功能就相當於``下列程式碼：  
  
 `EXISTS ( expression INTERSECT expression )`  
  
 OVERLAPS 是其中一個 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子。 所有 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子都會從左到右評估。 如需 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子的優先順序資訊，請參閱 [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md)。  
  
## 範例  
 下列 Entity SQL 查詢會使用 OVERLAPS 運算子來判斷兩個集合是否具有共通的值。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1.  遵循 [HOW TO：執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md) 中的程序進行。  
  
2.  將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#OVERLAPS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#overlaps)]  
  
## 請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)