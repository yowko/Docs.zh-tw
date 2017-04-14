---
title: "HAVING (Entity SQL) | Microsoft Docs"
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
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# HAVING (Entity SQL)
指定群組或彙總的搜尋條件。  
  
## 語法  
  
```  
  
[ HAVING search_condition ]  
```  
  
## 引數  
 `search_condition`  
 指定群組或彙總要符合的搜尋條件。 搭配 GROUP BY ALL 使用 HAVING 時，HAVING 子句會覆寫 ALL。  
  
## 備註  
 HAVING 子句是用來在群組的結果上指定額外篩選條件。 如果查詢運算式中未指定 GROUP BY 子句，便會假設為一組隱含的單一群組。  
  
> [!NOTE]
>  HAVING 只能搭配 [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) 陳述式使用。 未使用 [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) 時，HAVING 的行為就像是 WHERE 子句。  
  
 HAVING 子句的運作方式很類似 WHERE 字句，唯一不同的是它必須套用在 GROUP BY 運算後面。 這表示 HAVING 子句只能參考群組別名和彙總，如以下範例所述。  
  
```  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 前面的範例會將群組限制為包含一件產品以上的項目。  
  
## 範例  
 以下 Entity SQL 查詢使用 HAVING 和 GROUP BY 運算子指定群組或彙總的搜尋條件。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1.  遵循 [HOW TO：執行可傳回 PrimitiveType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md) 中的程序進行。  
  
2.  將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#HAVING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#having)]  
  
## 請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)   
 [查詢運算式](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)