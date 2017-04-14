---
title: "HOW TO：建立 EntityConnection 連接字串 | Microsoft Docs"
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
ms.assetid: 5bd1a748-3df7-4d0a-a607-14f25e3175e9
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# HOW TO：建立 EntityConnection 連接字串
本主題提供的範例將示範如何建立 <xref:System.Data.EntityClient.EntityConnection>。  
  
### 執行此範例中的程式碼  
  
1.  將 [AdventureWorks Sales Model](http://msdn.microsoft.com/zh-tw/f16cd988-673f-4376-b034-129ca93c7832) 加入至專案中，並將專案設定為使用 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。  如需詳細資訊，請參閱[How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/zh-tw/dadb058a-c5d9-4c5c-8b01-28044112231d)。  
  
2.  在應用程式的字碼頁中加入下列 `using` 陳述式 \(在 Visual Basic 中為 `Imports`\)：  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## 範例  
 下列範例會初始化基礎提供者的 <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName>，然後初始化 <xref:System.Data.EntityClient.EntityConnectionStringBuilder?displayProperty=fullName> 物件並將此物件傳遞給 <xref:System.Data.EntityClient.EntityConnection> 的建構函式 \(Constructor\)。  
  
 [!code-csharp[DP EntityServices Concepts#BuildingConnectionStringWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#buildingconnectionstringwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#BuildingConnectionStringWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#buildingconnectionstringwithentitycommand)]  
  
## 請參閱  
 [How to: Use EntityConnection with an Object Context](http://msdn.microsoft.com/zh-tw/2140fe7b-b88b-47c8-a749-d7f142eb1080)   
 [Entity Framework 的 EntityClient 提供者](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)