---
title: "查詢運算式 (Entity SQL) | Microsoft Docs"
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
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 查詢運算式 (Entity SQL)
查詢運算式將許多不同的查詢運算子結合成單一語法。  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 提供許多不同種類的運算式，包括：[常值](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md)、[參數](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)、[變數](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md)、運算子、[函式](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)、設定運算子等。  如需詳細資訊，請參閱[Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)。  
  
## 子句  
 查詢運算式是由一系列將後續運算套用到物件集合的子句組成。  它們都是依據標準 SQL SELECT 陳述式中相同的子句：[SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)、[FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md)、[WHERE](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md)、[GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md)、[HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md) 和 [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)。  
  
## 範圍  
 FROM 子句中定義的名稱會依出現的順序 \(從左到右\) 導入 FROM 範圍內。  在 JOIN 清單中，運算式可以參考之前定義在清單中的名稱。  FROM 子句中所識別項目的公用屬性不會加入到 FROM 範圍：它們一定要透過別名限定的名稱來參考。  一般而言，SELECT 運算式的所有部分都視為在 FROM 範圍中。  
  
## 請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)