---
title: "以方法為基礎的查詢語法範例：巡覽關聯性 | Microsoft Docs"
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
ms.assetid: a0bfa4b1-99e5-4dd1-9912-4b825a9dc25c
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 以方法為基礎的查詢語法範例：巡覽關聯性
[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] 中的導覽屬性是用來尋找位於關聯兩端之實體的捷徑屬性。  導覽屬性可讓使用者在不同實體之間巡覽，或是透過關聯集從某個實體巡覽至相關的實體。  本主題提供之以方法為基礎的查詢語法範例，將說明如何透過 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查詢中的導覽屬性來巡覽關聯性。  
  
 這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。  
  
 此主題中的範例將使用下列 `using`\/`Imports` 陳述式：  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## 範例  
 下列以方法為基礎的查詢語法範例會使用 <xref:System.Linq.Queryable.SelectMany%2A> 方法取得姓氏為 "Zhou" 之連絡人的所有訂單。  `Contact.SalesOrderHeader` 導覽屬性是用來取得每一個連絡人之 `SalesOrderHeader` 物件的集合。  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders_mq)]  
  
## 範例  
 下列以方法為基礎的查詢語法範例會使用 <xref:System.Linq.Queryable.Select%2A> 方法來取得所有連絡人識別碼以及姓氏為 "Zhou" 之每位連絡人的應付總額。  `Contact.SalesOrderHeader` 導覽屬性是用來取得每一個連絡人之 `SalesOrderHeader` 物件的集合。  `Sum` 方法會使用 `Contact.SalesOrderHeader` 導覽屬性來加總每位連絡人之所有訂單的應付總額。  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2_mq)]  
  
## 範例  
 下列以方法為基礎之查詢語法的範例會取得姓氏為 "Zhou" 之連絡人的所有訂單。  `Contact.SalesOrderHeader` 導覽屬性是用來取得每一個連絡人之 `SalesOrderHeader` 物件的集合。  該連絡人的名稱和訂單會以匿名型別的形式傳回。  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3_mq)]  
  
## 範例  
 下列範例會使用 `SalesOrderHeader.Address` 和 `SalesOrderHeader.Contact` 導覽屬性來取得與每筆訂單相關聯之 `Address` 和 `Contact` 物件的集合。  到西雅圖城市之每一筆訂單的連絡人姓氏、街道地址、銷售訂單編號及應付總額會以匿名型別的形式傳回。  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships_mq)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships_mq)]  
  
## 範例  
 下列範例會使用 `Where` 方法來尋找在 2003 年 12 月 1 日之後下單的訂單，然後使用 `order.SalesOrderDetail` 導覽屬性來取得每筆訂單的詳細資料。  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## 請參閱  
 [Navigation Properties](http://msdn.microsoft.com/zh-tw/41e1e6b9-8a57-467d-99d9-1857d2ca2ea5)   
 [LINQ to Entities 中的查詢](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)