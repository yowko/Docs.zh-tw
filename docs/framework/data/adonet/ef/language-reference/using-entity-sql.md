---
title: "USING (Entity SQL) | Microsoft Docs"
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
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# USING (Entity SQL)
指定查詢運算式中使用的命名空間 \(Namespace\)。  
  
## 語法  
  
```  
USING [ alias = ] namespace  
```  
  
## 引數  
 `alias`  
 指定較短的別名 \(Alias\)，以便限定命名空間。  
  
 `namespace`  
 任何有效的命名空間。  
  
## 範例  
 下列 Entity SQL 查詢會使用 USING 運算子來指定查詢運算式中使用的命名空間。  若要編譯及執行此查詢，請遵循以下步驟：  
  
1.  按照[HOW TO：執行可傳回 PrimitiveType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)中的程序進行。  
  
2.  將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：  
  
```  
using SqlServer; RAND()  
```  
  
## 請參閱  
 [命名空間](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)   
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)