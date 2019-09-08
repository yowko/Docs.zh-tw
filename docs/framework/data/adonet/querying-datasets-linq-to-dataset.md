---
title: 查詢資料集 (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: 79a9b320fbdbfecc3f7d531d992b1529873871a5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783044"
---
# <a name="querying-datasets-linq-to-dataset"></a>查詢資料集 (LINQ to DataSet)
當 <xref:System.Data.DataSet> 物件已經填入 (Populate) 資料之後，您就可以開始查詢它。 使用 LINQ to DataSet 來編寫查詢，類似于[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]針對其他[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]啟用的資料來源使用。 不過，請記住，當您在[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] <xref:System.Data.DataSet>物件上使用查詢時，您<xref:System.Data.DataRow>會查詢物件的列舉，而不是自訂類型的列舉。 這表示您可以<xref:System.Data.DataRow> [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]在查詢中使用類別的任何成員。 這可讓您建立內容豐富且複雜的查詢。  
  
 如同的其他執行方式[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]，您可以使用兩種不同的形式來建立 LINQ to DataSet 查詢：查詢運算式語法和以方法為基礎的查詢語法。 您可以使用查詢運算式語法或以方法為基礎的查詢語法，針對 <xref:System.Data.DataSet> 中的單一資料表、針對 <xref:System.Data.DataSet> 中的多個資料表，或針對具型別 <xref:System.Data.DataSet> 中的資料表執行查詢。  
  
## <a name="in-this-section"></a>本節內容  
 [單一資料表查詢](single-table-queries-linq-to-dataset.md)  
 說明如何執行單一資料表查詢。  
  
 [跨資料表查詢](cross-table-queries-linq-to-dataset.md)  
 說明如何執行跨資料表查詢。  
  
 [查詢具類型資料集](querying-typed-datasets.md)  
 說明如何查詢具型別 <xref:System.Data.DataSet> 物件。  
  
## <a name="see-also"></a>另請參閱

- [LINQ to DataSet 範例](linq-to-dataset-examples.md)
- [將資料載入至資料集](loading-data-into-a-dataset.md)
