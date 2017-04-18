---
title: "FLATTEN (Entity SQL) | Microsoft Docs"
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
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# FLATTEN (Entity SQL)
將集合轉換成扁平化集合。 新集合所包含的所有元素與舊集合相同，但是不包含巢狀結構。  
  
## 語法  
  
```  
  
FLATTEN ( collection )  
```  
  
## 引數  
 `collection`  
 任何傳回值集合的集合以便扁平化成為單一集合的有效運算式。  
  
## 備註  
 `FLATTEN` 是其中一個 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子。 所有 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子都會從左到右評估。 如需 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子的優先順序資訊，請參閱 [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md)。  
  
## 範例  
 下列 Entity SQL 查詢會使用 `FLATTEN` 運算子，將集合轉換成扁平化集合。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1.  遵循 [HOW TO：執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md) 中的程序進行。  
  
2.  將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#FLATTEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#flatten)]  
  
## 請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)