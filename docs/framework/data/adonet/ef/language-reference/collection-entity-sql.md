---
title: "COLLECTION (Entity SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# COLLECTION (Entity SQL)
COLLECTION 關鍵字只用於內嵌函式的定義。 集合函式是處理值的集合並產生純量輸出的函式。  
  
## 語法  
  
```  
  
COLLECTION(type_definition)   
```  
  
## 引數  
 `type_definition`  
 傳回支援的型別、資料列或參考等集合的運算式。  
  
## 備註  
 如需 COLLECTION 關鍵字的詳細資訊，請參閱 [類型定義](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)。  
  
## 範例  
 下列範例示範如何使用 COLLECTION 關鍵字將十進位的集合宣告為內嵌查詢函式的引數。  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## 請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)