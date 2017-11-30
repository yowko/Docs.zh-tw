---
title: "彙總作業 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9d4b07eeb1d09d7db0f75d96629c816f66dbb128
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="aggregation-operations-visual-basic"></a>彙總作業 (Visual Basic)
彙總運算會計算值集合中的單一值。 彙總運算的一個範例是，當您使用一個月中每天的溫度值來計算每天平均溫度時。  
  
 下圖顯示一系列數字之三個不同彙總作業的結果。 第一項作業會加總這些數字。 第二個作業會傳回序列中的最大值。  
  
 ![LINQ 彙總作業](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")  
  
 下節列出執行彙總作業的標準查詢運算子方法。  
  
## <a name="methods"></a>方法  
  
|方法名稱|說明|Visual Basic 查詢運算式語法|更多資訊|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|彙總|對集合的值執行自訂彙總運算。|不適用。|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|平均|計算值集合的平均值。|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|計數|計算集合中的項目，選擇性僅計算滿足述詞函式的項目。|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|LongCount|計算大型集合中的項目，選擇性僅計算滿足述詞函式的項目。|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|最大|決定集合中的最大值。|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|最小|決定集合中的最小值。|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|Sum|計算集合中值的總和。|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>查詢運算式語法範例  
  
### <a name="average"></a>Average  
 下列程式碼範例使用`Aggregate Into Average`中的子句[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]來計算陣列中的數字，代表溫度平均溫度。  
  
 [!code-vb[CsLINQAggregating#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_1.vb)]  
  
### <a name="count"></a>計數  
 下列程式碼範例使用`Aggregate Into Count`中的子句[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]來計算陣列中的值大於或等於 80 的數目。  
  
 [!code-vb[CsLINQAggregating#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_2.vb)]  
  
### <a name="longcount"></a>LongCount  
 下列程式碼範例使用`Aggregate Into LongCount`子句來計算陣列中的值數目。  
  
 [!code-vb[CsLINQAggregating#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_3.vb)]  
  
### <a name="max"></a>最大  
 下列程式碼範例使用`Aggregate Into Max`子句來計算陣列中的數字，代表溫度最大的溫度。  
  
 [!code-vb[CsLINQAggregating#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_4.vb)]  
  
### <a name="min"></a>最小  
 下列程式碼範例使用`Aggregate Into Min`子句來計算陣列中的數字，代表溫度最小的溫度。  
  
 [!code-vb[CsLINQAggregating#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_5.vb)]  
  
### <a name="sum"></a>Sum  
 下列程式碼範例使用`Aggregate Into Sum`子句來計算總計的支出金額從陣列的值，表示費用。  
  
 [!code-vb[CsLINQAggregating#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_6.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Linq>  
 [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Aggregate 子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [如何： 計算 CSV 文字檔案 (LINQ) (Visual Basic) 中的資料行值](../../../../visual-basic/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 [如何：統計、加總或平均資料](../../../../visual-basic/programming-guide/language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)  
 [如何：尋找查詢結果中的最小或最大值](../../../../visual-basic/programming-guide/language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
 [如何： 查詢的最大檔案或目錄樹狀 (LINQ) (Visual Basic) 中的檔案](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 [如何： 查詢一組資料夾 (LINQ) (Visual Basic) 中的位元組總數](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)
