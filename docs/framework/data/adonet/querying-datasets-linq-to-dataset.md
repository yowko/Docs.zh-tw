---
title: "查詢 DataSet (LINQ to DataSet) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 查詢 DataSet (LINQ to DataSet)
當 <xref:System.Data.DataSet> 物件已經填入 \(Populate\) 資料之後，您就可以開始查詢它。  使用 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 來編寫查詢與針對其他啟用 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 的資料來源使用 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] 很相似。  不過，請記住，當您針對 <xref:System.Data.DataSet> 物件使用 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 查詢時，您正在查詢的是 <xref:System.Data.DataRow> 物件的列舉型別 \(Enumeration\)，而非自訂型別的列舉型別。  這表示，您可以在 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 查詢中使用 <xref:System.Data.DataRow> 類別 \(Class\) 的任何成員。  這可讓您建立內容豐富且複雜的查詢。  
  
 如同 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 的其他實作，您可以用兩種不同的形式來建立 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 查詢：查詢運算式語法和以方法為基礎的查詢語法。  如需這兩種形式的詳細資訊，請參閱[Getting Started with LINQ](http://msdn.microsoft.com/zh-tw/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9)。您可以使用查詢運算式語法或以方法為基礎的查詢語法，針對 <xref:System.Data.DataSet> 中的單一資料表、針對 <xref:System.Data.DataSet> 中的多個資料表，或針對具型別 <xref:System.Data.DataSet> 中的資料表執行查詢。  
  
## 本章節內容  
 [單一資料表查詢](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 說明如何執行單一資料表查詢。  
  
 [跨資料表查詢](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 說明如何執行跨資料表查詢。  
  
 [查詢具型別 DataSet](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 說明如何查詢具型別 <xref:System.Data.DataSet> 物件。  
  
## 請參閱  
 [LINQ to DataSet 範例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)   
 [將資料載入 DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)