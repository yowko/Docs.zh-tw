---
title: "以方法為基礎的查詢語法範例：群組 | Microsoft Docs"
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
ms.assetid: cb23c25c-1075-4cc3-a8ff-4db72e536c0d
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 以方法為基礎的查詢語法範例：群組
本主題的範例為您示範如何使用 `GroupBy` 方法，利用以方法為基礎的查詢語法查詢 [AdventureWorks Sales Model](http://msdn.microsoft.com/zh-tw/f16cd988-673f-4376-b034-129ca93c7832)。  這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。  
  
 此主題中的範例將使用下列 `using`\/`Imports` 陳述式：  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## 範例  
 以下範例使用 `GroupBy` 方法傳回依郵遞區號群組的 `Address` 物件。  這些結果會投影至匿名型別中。  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3_mq)]  
  
## 範例  
 以下範例使用 `GroupBy` 方法傳回依連絡人姓氏的第一個字母群組的 `Contact` 物件。  結果也會依連絡人姓氏的第一個字母排序，並且會投影到匿名型別中。  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2_mq)]  
  
## 範例  
 以下範例使用 `GroupBy` 方法傳回客戶 ID 群組的 `SalesOrderHeader` 物件。  也會傳回每一客戶的銷售數量。  
  
 [!code-csharp[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount_mq)]
 [!code-vb[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount_mq)]  
  
## 請參閱  
 [LINQ to Entities 中的查詢](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)