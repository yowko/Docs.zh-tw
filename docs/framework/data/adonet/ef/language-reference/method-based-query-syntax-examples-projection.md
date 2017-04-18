---
title: "以方法為基礎的查詢語法範例：投影 | Microsoft Docs"
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
ms.assetid: 505491fa-5920-43ce-8a96-c25389e125d8
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 以方法為基礎的查詢語法範例：投影
本主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Select%2A> 和 <xref:System.Linq.Enumerable.SelectMany%2A> 方法，透過以方法為基礎的查詢語法來查詢 [AdventureWorks Sales Model](http://msdn.microsoft.com/zh-tw/f16cd988-673f-4376-b034-129ca93c7832)。  這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。  
  
 此主題中的範例將使用下列 `using`\/`Imports` 陳述式：  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## 選取  
  
### 範例  
 下列範例會使用 <xref:System.Linq.Queryable.Select%2A> 方法，將 `Product.Name` 和 `Product.ProductID` 屬性投影到匿名型別的序列中。  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
### 範例  
 下列範例會使用 <xref:System.Linq.Enumerable.Select%2A> 方法來單獨傳回產品名稱的序列。  
  
 [!code-csharp[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2_mq)]
 [!code-vb[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2_mq)]  
  
## SelectMany  
  
### 範例  
 下列範例會使用 <xref:System.Linq.Enumerable.SelectMany%2A> 方法來選取 `TotalDue` 少於 500.00 的所有訂單。  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom_mq)]  
  
### 範例  
 下列範例會使用 <xref:System.Linq.Enumerable.SelectMany%2A> 方法來選取在 2002 年 10 月 1 日或之後下單的所有訂單。  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2_mq)]  
  
## 請參閱  
 [LINQ to Entities 中的查詢](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)