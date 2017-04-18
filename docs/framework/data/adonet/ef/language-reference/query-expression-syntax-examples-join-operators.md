---
title: "查詢運算式語法範例：聯結運算子 | Microsoft Docs"
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
ms.assetid: 343e8dda-70b2-409d-9334-ce9a880c3cea
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 查詢運算式語法範例：聯結運算子
在以彼此沒有可瀏覽關聯性之資料來源 \(例如關聯式資料庫資料表\) 為目標的查詢中，聯結 \(Join\) 是一項重要的作業。  兩個資料來源的聯結是指某個資料來源中的物件與另一個資料來源中共用相同屬性之物件的關聯。  如需詳細資訊，請參閱[Standard Query Operators Overview](../../../../../../ocs/visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)。  
  
 本主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.GroupJoin%2A> 和 <xref:System.Linq.Enumerable.Join%2A> 方法，透過查詢運算式語法來查詢 [AdventureWorks Sales Model](http://msdn.microsoft.com/zh-tw/f16cd988-673f-4376-b034-129ca93c7832)。  這些範例中使用的 AdventureWorks Sales Model 是從 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表所建立。  
  
 此主題中的範例將使用下列 `using`\/`Imports` 陳述式：  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## GroupJoin  
  
### 範例  
 下列範例會在 SalesOrderHeader 和 SalesOrderDetail 資料表上執行 <xref:System.Linq.Enumerable.GroupJoin%2A> 來尋找每一客戶的定單數目。  群組聯結是左外部聯結的對等項目，它會傳回第一個 \(左\) 資料來源的每個項目，即使其他資料來源中沒有相互關聯的項目也一樣。  
  
 [!code-csharp[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2)]  
  
### 範例  
 下列範例會在 Contact 和 SalesOrderHeader 資料表上執行 <xref:System.Linq.Enumerable.GroupJoin%2A> 來尋找每一連絡人的定單數目。  然後顯示每一連絡人的訂單數目和 ID。  
  
 [!code-csharp[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin)]  
  
### 範例  
 下列範例會針對 Contact 和 SalesOrderHeader 資料表執行 <xref:System.Linq.Enumerable.GroupJoin%2A>。  群組聯結是左外部聯結的對等項目，它會傳回第一個 \(左\) 資料來源的每個項目，即使其他資料來源中沒有相互關聯的項目也一樣。  
  
 [!code-csharp[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin)]  
  
## Join  
  
### 範例  
 下列範例會針對 SalesOrderHeader 和 SalesOrderDetail 資料表執行聯結，以便取得八月的線上訂單資訊。  
  
 [!code-csharp[DP L2E Examples#Join](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#join)]
 [!code-vb[DP L2E Examples#Join](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#join)]  
  
## 請參閱  
 [LINQ to Entities 中的查詢](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)