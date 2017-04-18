---
title: "MULTISET (Entity SQL) | Microsoft Docs"
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
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# MULTISET (Entity SQL)
從值清單建立多重集的執行個體。 MULTISET 建構函式 \(Constructor\) 中的所有值都必須是相容型別 `T`。 不允許空的多重集建構函式。  
  
## 語法  
  
```  
  
MULTISET (expression [{, expression }] )  
or  
{ expression [{, expression }] }  
```  
  
## 引數  
 `expression`  
 任何有效的值清單。  
  
## 傳回值  
 型別 MULTISET\<T\> 的集合。  
  
## 備註  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 提供三種建構函式：資料列建構函式、物件建構函式和多重集 \(或集合\) 建構函式。 如需詳細資訊，請參閱[建構類型](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)。  
  
 多重集建構函式會從值清單建立多重集的例項。 該建構函式中的所有值都必須是相容型別。  
  
 例如，下列運算式會建立整數的多重集。  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
>  只有在包裝多重集有單一多重集項目時，才支援巢狀多重集常值 \(Literal\)，例如 `{{1, 2, 3}}`。 在包裝多重集有多個多重集項目 \(例如 `{{1, 2}, {3, 4}}`\) 的情況下，並不支援巢狀多重集常值。  
  
## 範例  
 下列 Entity SQL 查詢會使用 MULTISET 運算子，從值清單建立多重集的例項。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1.  遵循 [HOW TO：執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md) 中的程序進行。  
  
2.  將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTISET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiset)]  
  
## 請參閱  
 [建構類型](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)   
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)