---
title: "區域方法呼叫 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 區域方法呼叫
區域方法呼叫就是在物件模型 \(Object Model\) 內執行的呼叫。  遠端方法呼叫則是 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 轉譯為 SQL 並傳輸給資料庫引擎進行執行的呼叫。  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 無法將呼叫轉譯為 SQL 時，就需要區域方法呼叫。  否則會擲回 <xref:System.InvalidOperationException>。  
  
## 範例 1  
 在下列範例中，`Order` 類別會對應至 Northwind 範例資料庫中的 Orders 資料表。  本機執行個體方法已加入至這個類別中。  
  
 在查詢 1 中，會在本機執行 `Order` 類別的建構函式。  在查詢 2 中，如果 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 嘗試將 `LocalInstanceMethod()` 轉譯為 SQL，則嘗試會失敗，而且會擲回 <xref:System.InvalidOperationException> 例外狀況 \(Exception\)。但是因為 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支援區域方法呼叫，所以查詢 2 不會擲回例外狀況。  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## 請參閱  
 [背景資訊](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)