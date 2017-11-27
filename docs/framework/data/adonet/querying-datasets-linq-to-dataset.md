---
title: "查詢資料集 (LINQ to DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4f1b1a70025dc81bdf99c636b65c23d373e73a80
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="querying-datasets-linq-to-dataset"></a>查詢資料集 (LINQ to DataSet)
當 <xref:System.Data.DataSet> 物件已經填入 (Populate) 資料之後，您就可以開始查詢它。 使用 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 來編寫查詢與針對其他啟用 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] 的資料來源使用 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 很相似。 請記住，但是，當您使用[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]查詢經過一段<xref:System.Data.DataSet>您要查詢的列舉物件<xref:System.Data.DataRow>物件，而不是自訂類型的列舉。 這表示您可以使用任何成員的<xref:System.Data.DataRow>類別中您[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]查詢。 這可讓您建立內容豐富且複雜的查詢。  
  
 如同其他實作[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]，您可以建立[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]兩種不同形式的查詢： 查詢運算式語法和以方法為基礎的查詢語法。 如需有關這兩種格式的詳細資訊，請參閱[撰寫 LINQ 入門](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9)。 您可以使用查詢運算式語法或以方法為基礎的查詢語法，針對 <xref:System.Data.DataSet> 中的單一資料表、針對 <xref:System.Data.DataSet> 中的多個資料表，或針對具型別 <xref:System.Data.DataSet> 中的資料表執行查詢。  
  
## <a name="in-this-section"></a>本章節內容  
 [單一資料表查詢](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 說明如何執行單一資料表查詢。  
  
 [跨資料表查詢](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 說明如何執行跨資料表查詢。  
  
 [查詢具類型資料集](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 說明如何查詢具型別 <xref:System.Data.DataSet> 物件。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to DataSet 範例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [載入資料至資料集](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
