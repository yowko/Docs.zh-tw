---
title: "/ (除號) (Entity SQL) | Microsoft Docs"
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
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# / (除號) (Entity SQL)
將一個數字除以另一個數字。  
  
## 語法  
  
```  
  
dividend  
/  
divisor  
  
```  
  
## 引數  
 `dividend`  
 要當做被除數的數值運算式。`dividend` 是任何一個數值資料型別的任何有效運算式。  
  
 `divisor`  
 要當做除數的數值運算式。`divisor` 是任何一個數值資料型別的任何有效運算式。  
  
## 結果型別  
 從兩個引數的隱含型別提升產生的資料型別。 如需隱含類型提升的詳細資訊，請參閱 [類型系統](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)。  
  
## 範例  
 下列 Entity SQL 查詢會使用 \/ 算術運算子讓兩個數字相除。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1.  遵循 [HOW TO：執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md) 中的程序進行。  
  
2.  將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#DIVIDE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#divide)]  
  
## 請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)