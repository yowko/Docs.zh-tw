---
title: "變數 (Entity SQL) | Microsoft Docs"
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
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 變數 (Entity SQL)
## 變數  
 變數運算式是目前範圍中所定義之具名運算式的參考。  變數參考必須是有效的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 識別碼，如[識別項](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md) 中所定義。  
  
 下列範例示範如何在運算式中使用變數。  FROM 子句中的 `c` 是變數的定義。  SELECT 子句中的 `c` 使用代表變數參考。  
  
```  
select c   
from LOB.customers as c  
```  
  
## 請參閱  
 [識別項](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)   
 [參數](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)   
 [Entity SQL 概觀](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)