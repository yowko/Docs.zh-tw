---
title: "HOW TO：使用 EntityCommand 執行參數化預存程序 | Microsoft Docs"
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
ms.assetid: 4f5639bf-bb7f-4982-bb1d-c7caa4348888
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# HOW TO：使用 EntityCommand 執行參數化預存程序
本主題顯示如何使用 <xref:System.Data.EntityClient.EntityCommand> 類別，執行參數化預存程序。  
  
### 執行此範例中的程式碼  
  
1.  將 [School Model](http://msdn.microsoft.com/zh-tw/859a9587-81ea-4a45-9bc0-f8d330e1adac) 加入至專案中，並將專案設定為使用 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。  如需詳細資訊，請參閱[How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/zh-tw/dadb058a-c5d9-4c5c-8b01-28044112231d)。  
  
2.  在應用程式的字碼頁中加入下列 `using` 陳述式 \(在 Visual Basic 中為 `Imports`\)：  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  匯入 `GetStudentGrades` 預存程序，並指定 `CourseGrade` 實體做為傳回型別。  如需如何匯入預存程序的詳細資訊，請參閱 [How to: Import a Stored Procedure](http://msdn.microsoft.com/zh-tw/24e68bf4-bd6d-428d-bc35-92d7b8e3736d)。  
  
## 範例  
 下列程式碼會執行 `GetStudentGrades` 預存程序，其中 `StudentId` 是必要參數。  然後 <xref:System.Data.EntityClient.EntityDataReader> 會讀取結果。  
  
 [!code-csharp[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#storedprocwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#storedprocwithentitycommand)]  
  
## 請參閱  
 [Entity Framework 的 EntityClient 提供者](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)