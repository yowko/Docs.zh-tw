---
title: "制定投影 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 制定投影
下列範例顯示 C\# 中的 `select` 陳述式和 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 中的 `Select` 陳述式如何與其他功能結合，以構成查詢投影。  
  
## 範例  
 下列範例使用 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 中的 `Select` 子句 \(C\# 中的 `select` 子句\)，傳回 `Customers` 的連絡人名稱序列。  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## 範例  
 下列範例使用 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] `Select` 中的子句 \(C\# 中的 `select` 子句\) 和「*匿名型別*」\(Anonymous Type\)，傳回 `Customers` 的連絡人名稱和電話號碼序列。  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## 範例  
 下列範例使用 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 中的 `Select` 子句 \(C\# 中的 `select` 子句\) 和「*匿名型別*」，傳回員工的姓名和電話號碼序列。  `FirstName` 和 `LastName` 欄位會合併成單一欄位 \(`Name`\)，而在結果序列中 `HomePhone` 欄位會重新命名為 `Phone`。  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## 範例  
 下列範例使用 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 中的 `Select` 子句 \(C\# 中的 `select` 子句\) 和「*匿名型別*」，傳回所有 `ProductID` 的序列和名為 `HalfPrice` 的計算值。  此值設為 `UnitPrice` 除以 2。  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## 範例  
 下列範例使用 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 中的 `Select` 子句 \(C\# 中的 `select` 子句\) 和「*條件陳述式*」\(Conditional Statement\)，傳回產品名稱和產品可用性的序列。  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## 範例  
 下列範例使用 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] `Select` 子句 \(C\# 中的 `select` 子句\) 和「*已知型別*」\(Known Type\) \(Name\)，傳回員工姓名的序列。  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## 範例  
 下列範例使用 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 中的 `Select` 和 `Where` \(C\# 中的 `select` 和 `where`\)，傳回倫敦客戶之連絡人名稱的「*篩選序列*」\(Filtered Sequence\)。  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## 範例  
 下列範例使用 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 中的  `Select` 子句 \(C\# 中的 `select` 子句\) 和「*匿名型別*」，傳回客戶相關資料的「*合適子集*」\(Shaped Subset\)。  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## 範例  
 下列範例使用巢狀查詢，傳回下列結果：  
  
-   所有訂單與其對應 `OrderID` 的序列。  
  
-   訂單中有折扣之項目的序列。  
  
-   不包含運送成本時所節省的金額。  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## 請參閱  
 [查詢範例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)