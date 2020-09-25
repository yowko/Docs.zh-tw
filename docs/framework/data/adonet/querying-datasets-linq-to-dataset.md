---
title: 查詢資料集 (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: f42cd792772a4e2b9f24ea8f76ea588da10d9c51
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184972"
---
# <a name="querying-datasets-linq-to-dataset"></a>查詢資料集 (LINQ to DataSet)

當 <xref:System.Data.DataSet> 物件已經填入 (Populate) 資料之後，您就可以開始查詢它。 使用 LINQ to DataSet 來設計查詢類似于使用語言整合式查詢 (LINQ) 與其他已啟用 LINQ 的資料來源。 不過請記住，當您在物件上使用 LINQ 查詢時， <xref:System.Data.DataSet> 您要查詢物件的列舉 <xref:System.Data.DataRow> ，而不是自訂型別的列舉。 這表示您可以 <xref:System.Data.DataRow> 在 LINQ 查詢中使用類別的任何成員。 這可讓您建立豐富且複雜的查詢。  
  
 如同 LINQ 的其他執行，您可以使用兩種不同的形式來建立 LINQ to DataSet 查詢：查詢運算式語法和以方法為基礎的查詢語法。 您可以使用查詢運算式語法或以方法為基礎的查詢語法，針對 <xref:System.Data.DataSet> 中的單一資料表、針對 <xref:System.Data.DataSet> 中的多個資料表，或針對具型別 <xref:System.Data.DataSet> 中的資料表執行查詢。  
  
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
