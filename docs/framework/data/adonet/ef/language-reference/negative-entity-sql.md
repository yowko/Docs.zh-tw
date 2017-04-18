---
title: "- (負號) (Entity SQL) | Microsoft Docs"
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
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# - (負號) (Entity SQL)
傳回數值運算式的負值。  
  
## 語法  
  
```  
  
-  
expression  
  
```  
  
## 引數  
 `expression`  
 任何一個數值資料型別的任何有效運算式。  
  
## 結果型別  
 `expression` 的資料型別。  
  
## 備註  
 如果 `expression` 是不帶正負號型別，結果型別就是與 `expression` 型別最密切相關的帶正負號型別。 例如，如果 `expression` 的型別為 Byte，就會傳回 Int16 型別的值。  
  
## 範例  
 下列 Entity SQL 查詢會使用 \- 算術運算子來傳回數值運算式的負值。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1.  遵循 [HOW TO：執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md) 中的程序進行。  
  
2.  將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#NEGATIVE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#negative)]  
  
## 請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)