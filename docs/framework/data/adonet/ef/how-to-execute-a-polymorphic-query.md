---
title: "HOW TO：執行多型查詢 | Microsoft Docs"
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
ms.assetid: 2f05da1e-845b-4f14-83e4-c6353a850553
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# HOW TO：執行多型查詢
本主題將示範如何使用 [OFTYPE](../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) 運算子執行 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 多型查詢。  
  
### 執行此範例中的程式碼  
  
1.  將 [School Model](http://msdn.microsoft.com/zh-tw/859a9587-81ea-4a45-9bc0-f8d330e1adac)加入至專案中，並將專案設定成使用 Entity Framework。  如需詳細資訊，請參閱[How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/zh-tw/dadb058a-c5d9-4c5c-8b01-28044112231d)。  
  
2.  在應用程式的字碼頁中加入下列 `using` 陳述式 \(在 Visual Basic 中為 `Imports`\)：  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  依照[Walkthrough: Mapping Inheritance \- Table\-per\-Hierarchy](http://msdn.microsoft.com/zh-tw/49b685cf-9db8-4d6d-b885-8837ed238f55)中的步驟，可修改概念模型以擁有每個階層的資料表繼承。  
  
## 範例  
 下列範例會使用 OFTYPE 運算子，從 `Courses` 的集合中取得並顯示只有 `OnsiteCourses` 的集合。  
  
 [!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
 [!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]  
  
## 請參閱  
 [Entity Framework 的 EntityClient 提供者](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)   
 [Entity SQL 語言](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)