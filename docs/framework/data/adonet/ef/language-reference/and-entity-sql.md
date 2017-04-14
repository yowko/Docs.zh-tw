---
title: "&amp;&amp; (AND) (Entity SQL) | Microsoft Docs"
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
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# &amp;&amp; (AND) (Entity SQL)
如果兩個運算式都是 `true` 則傳回 `true`，否則為 `false` 或 `NULL`。  
  
## 語法  
  
```  
  
          boolean_expression AND boolean_expression  
or  
boolean_expression && boolean_expression  
```  
  
## 引數  
 `boolean_expression`  
 傳回布林值的任何有效運算式。  
  
## 備註  
 雙連字號 \(&&\) 的功能與 AND 運算子相同。  
  
 下表顯示可能的輸入值和傳回型別。  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|TRUE|FALSE|NULL|  
|`FALSE`|FALSE|FALSE|FALSE|  
|`NULL`|NULL|FALSE|NULL|  
  
## 範例  
 下列 Entity SQL 查詢會示範如何使用 AND 運算子。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1.  遵循 [HOW TO：執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md) 中的程序進行。  
  
2.  將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## 請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)