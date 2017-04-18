---
title: "HOW TO：儲存和重複使用查詢 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a012bd79-1809-45e3-adea-0229532396cc
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# HOW TO：儲存和重複使用查詢
當您的應用程式會多次執行結構類似的查詢時，您藉由編譯查詢一次並使用不同的參數加以執行數次，通常可以提高效能。  例如，應用程式可能必須擷取位於特定城市的所有客戶，該城市是使用者於執行階段在表單中指定。  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支援就此目的使用「*已編譯查詢*」\(Compiled Query\)。  
  
> [!NOTE]
>  這種模式的使用方式代表已編譯查詢的最常見用途。  其他方法也有可能。  例如，在可擴充設計工具所產生之程式碼的部分類別中，已編譯查詢可以儲存為靜態成員。  
  
## 範例  
 在許多情況下，您會想要跨越執行緒界限重複使用查詢。  在此情況下，以靜態變數儲存已編譯查詢特別有效。  下列程式碼範例採用了設計用來儲存已編譯查詢的 `Queries` 類別，並採用表示強型別 <xref:System.Data.Linq.DataContext> 的 Northwind 類別。  
  
 [!code-csharp[DLinqQuerying#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#6)]
 [!code-vb[DLinqQuerying#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#6)]  
  
 [!code-csharp[DLinqQuerying#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#7)]
 [!code-vb[DLinqQuerying#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#7)]  
  
## 範例  
 您目前無法 \(以靜態變數\) 儲存會傳回「*匿名型別*」\(anonymous type\) 的查詢，因為該型別沒有名稱可提供做為泛型引數。  下列範例顯示如何藉由建立可表示結果的型別並以它做為泛型引數，來解決這個問題。  
  
 [!code-csharp[DLinqQuerying#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#8)]
 [!code-vb[DLinqQuerying#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#8)]  
  
## 請參閱  
 <xref:System.Data.Linq.CompiledQuery>   
 [查詢概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)   
 [查詢資料庫](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)