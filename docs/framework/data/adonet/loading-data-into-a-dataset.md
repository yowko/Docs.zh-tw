---
title: "將資料載入 DataSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 將資料載入 DataSet
<xref:System.Data.DataSet> 物件必須先填入 \(Populate\) 資料，然後您才能使用 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 來查詢它。  目前有許多不同的方式可以填入 <xref:System.Data.DataSet>。  例如，您可以使用 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] 來查詢資料庫並將結果載入 <xref:System.Data.DataSet>。  如需詳細資訊，請參閱[LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)。  
  
 另一種將資料載入 <xref:System.Data.DataSet> 的常見方式是使用 <xref:System.Data.Common.DataAdapter> 類別 \(Class\)，從資料庫中擷取資料。  下列範例將說明這種方式。  
  
## 範例  
 這則範例會使用 <xref:System.Data.Common.DataAdapter>，在 AdventureWorks 資料庫中查詢是否有 2002 年的銷售資訊，然後將結果載入 <xref:System.Data.DataSet>。  當 <xref:System.Data.DataSet> 已經填入資料之後，您就可以使用 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 來針對它撰寫查詢。  這則範例中的 `FillDataSet` 方法用於 [LINQ to DataSet 範例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)的範例查詢中。  如需詳細資訊，請參閱[查詢 DataSet](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)。  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## 請參閱  
 [LINQ to DataSet 概觀](../../../../docs/framework/data/adonet/linq-to-dataset-overview.md)   
 [查詢 DataSet](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)   
 [LINQ to DataSet 範例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)