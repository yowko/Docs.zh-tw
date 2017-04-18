---
title: "以方法為基礎的查詢語法範例：分割 | Microsoft Docs"
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
ms.assetid: b7b64874-c3c8-4bdb-862c-89a168d07827
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 以方法為基礎的查詢語法範例：分割
本主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Take%2A> 方法，透過查詢運算式語法來查詢 [AdventureWorks Sales Model](http://msdn.microsoft.com/zh-tw/f16cd988-673f-4376-b034-129ca93c7832)。  這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。  
  
 此主題中的範例將使用下列 `using`\/`Imports` 陳述式：  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## Skip  
  
### 範例  
 下列範例會使用 <xref:System.Linq.Enumerable.Skip%2A> 方法來取得 Contact 資料表的所有連絡人 \(前五位連絡人除外\)。  
  
 [!code-csharp[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipsimple)]  
  
### 範例  
 下列範例會使用 <xref:System.Linq.Enumerable.Skip%2A> 方法來取得西雅圖的所有地址 \(前兩筆地址除外\)。  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## Take  
  
### 範例  
 下列範例會使用 <xref:System.Linq.Enumerable.Take%2A> 方法，單獨從 Contact 資料表中取得前五位連絡人。  
  
 [!code-csharp[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takesimple)]  
  
### 範例  
 下列範例會使用 <xref:System.Linq.Enumerable.Take%2A> 方法來取得西雅圖的前三筆地址。  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## 請參閱  
 [LINQ to Entities 中的查詢](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)