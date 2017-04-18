---
title: "HOW TO：執行可傳回 PrimitiveType 結果的查詢 | Microsoft Docs"
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
  - "jsharp"
ms.assetid: 7139d585-4034-4dfa-916f-2120a8b72792
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# HOW TO：執行可傳回 PrimitiveType 結果的查詢
本主題顯示如何使用 <xref:System.Data.EntityClient.EntityCommand>，針對概念模型執行命令，以及如何使用 <xref:System.Data.EntityClient.EntityDataReader> 擷取 <xref:System.Data.Metadata.Edm.PrimitiveType> 結果。  
  
### 執行此範例中的程式碼  
  
1.  將 [AdventureWorks Sales Model](http://msdn.microsoft.com/zh-tw/f16cd988-673f-4376-b034-129ca93c7832) 加入至專案中，並將專案設定為使用 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。  如需詳細資訊，請參閱[How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/zh-tw/dadb058a-c5d9-4c5c-8b01-28044112231d)。  
  
2.  在應用程式的字碼頁中加入下列 `using` 陳述式 \(在 Visual Basic 中為 `Imports`\)：  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## 範例  
 此範例會執行傳回 <xref:System.Data.Metadata.Edm.PrimitiveType> 結果的查詢。  如果您將下列查詢當做引數傳遞至 `ExecutePrimitiveTypeQuery` 函式，則函式會顯示所有 `Products` 的平均清單價格：  
  
 [!code-csharp[DP EntityServices Concepts#EDM_AVG](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)]
 [!code-sql[DP EntityServices Concepts#EDM_AVG](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)]  
  
 如果您傳遞了參數型查詢 \(類似下列查詢\)，請將 <xref:System.Data.EntityClient.EntityParameter> 物件加入至 <xref:System.Data.EntityClient.EntityCommand> 物件的 <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> 屬性。  
  
 [!code-csharp[DP EntityServices Concepts#CASE_WHEN_THEN_ELSE](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#case_when_then_else)]
 [!code-sql[DP EntityServices Concepts#CASE_WHEN_THEN_ELSE](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#case_when_then_else)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLPrimitiveTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlprimitivetypes)]
 [!code-vb[DP EntityServices Concepts#eSQLPrimitiveTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlprimitivetypes)]  
  
## 請參閱  
 [Entity SQL 參考](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)   
 [Entity Framework 的 EntityClient 提供者](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)