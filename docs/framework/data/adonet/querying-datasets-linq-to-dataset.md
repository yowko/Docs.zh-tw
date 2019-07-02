---
title: 查詢資料集 (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: ec4ee345835294499f7ac9f665a9b79e2efc0f64
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504660"
---
# <a name="querying-datasets-linq-to-dataset"></a>查詢資料集 (LINQ to DataSet)
當 <xref:System.Data.DataSet> 物件已經填入 (Populate) 資料之後，您就可以開始查詢它。 來編寫查詢與 LINQ to DataSet，類似於使用[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]針對其他[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-已啟用資料來源。 記住，不過，當您使用[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]透過查詢<xref:System.Data.DataSet>物件，您要查詢的列舉<xref:System.Data.DataRow>物件，而不是自訂類型的列舉型別。 這表示，您可以使用任何的成員清單<xref:System.Data.DataRow>類別中您[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]查詢。 這可讓您建立內容豐富且複雜的查詢。  
  
 如同其他的實作[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]，您可以建立 LINQ to DataSet 查詢兩種不同形式： 查詢運算式語法和以方法為基礎的查詢語法。 您可以使用查詢運算式語法或以方法為基礎的查詢語法，針對 <xref:System.Data.DataSet> 中的單一資料表、針對 <xref:System.Data.DataSet> 中的多個資料表，或針對具型別 <xref:System.Data.DataSet> 中的資料表執行查詢。  
  
## <a name="in-this-section"></a>本節內容  
 [單一資料表查詢](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 說明如何執行單一資料表查詢。  
  
 [跨資料表查詢](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 說明如何執行跨資料表查詢。  
  
 [查詢具類型資料集](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 說明如何查詢具型別 <xref:System.Data.DataSet> 物件。  
  
## <a name="see-also"></a>另請參閱

- [LINQ to DataSet 範例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [將資料載入至資料集](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
