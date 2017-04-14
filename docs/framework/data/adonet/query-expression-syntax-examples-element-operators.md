---
title: "查詢運算式語法範例：元素運算子 (LINQ to DataSet) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ca392dda-16e3-45c7-8d87-12d8d4ee0578
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 查詢運算式語法範例：元素運算子 (LINQ to DataSet)
此主題中的範例將示範如何使用 <xref:System.Linq.Enumerable.First%2A> 和 <xref:System.Linq.Enumerable.ElementAt%2A> 方法並搭配查詢運算式語法來取得 <xref:System.Data.DataSet> 中的 <xref:System.Data.DataRow> 項目。  
  
 在這些範例中使用的 `FillDataSet` 方法指定於[將資料載入 DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)。  
  
 此主題中的範例將使用 AdventureWorks 範例資料庫中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 資料表。  
  
 此主題中的範例將使用下列 `using`\/`Imports` 陳述式：  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 如需詳細資訊，請參閱[HOW TO：在 Visual Studio 中建立 LINQ to DataSet 專案](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md)。  
  
## ElementAt  
  
### 範例  
 這則範例會使用 <xref:System.Linq.Enumerable.ElementAt%2A> 方法來擷取 `PostalCode` \=\= "M4B 1V7" 的第五筆地址。  
  
 [!code-csharp[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#elementat)]
 [!code-vb[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#elementat)]  
  
## First  
  
### 範例  
 這則範例會使用 <xref:System.Linq.Enumerable.First%2A> 方法來傳回名字為 'Brooke' 的第一位連絡人。  
  
 [!code-csharp[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#firstsimple)]  
  
## 請參閱  
 [將資料載入 DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)   
 [LINQ to DataSet 範例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)   
 [Standard Query Operators Overview](../../../../ocs/visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)