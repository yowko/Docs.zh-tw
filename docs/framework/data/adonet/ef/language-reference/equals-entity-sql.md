---
title: "= (等號) (Entity SQL) | Microsoft Docs"
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
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# = (等號) (Entity SQL)
比較兩個運算式是否相等。  
  
## 語法  
  
```  
  
          expression  
          =  
          expression  
or   
expression==expression  
```  
  
## 引數  
 `expression`  
 任何有效的運算式。 兩個運算式都必須有可隱含轉換的資料型別。  
  
## 結果型別  
 如果左運算式等於右運算式則為 `true`；否則為 `false`。  
  
## 備註  
 \=\= 運算子就相當於 \=。  
  
## 範例  
 以下 Entity SQL 查詢使用 \= 比較運算子來比較兩個運算式是否相等。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1.  遵循 [HOW TO：執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md) 中的程序進行。  
  
2.  將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#equals)]  
  
## 請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)