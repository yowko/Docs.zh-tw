---
title: "數量詞作業 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9bc48c69179b1f8876efaa465295e94a9a0e0fb6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="quantifier-operations-visual-basic"></a>數量詞作業 (Visual Basic)
數量詞作業會傳回 <xref:System.Boolean> 值，指出序列中的部分或所有項目是否符合條件。  
  
 下圖說明兩個不同來源序列上的兩個不同數量詞作業。 第一個作業會詢問一個或多個項目是否為字元 'A'，而結果為 `true`。 第二個作業會詢問所有項目是否都為字元 'A'，而結果為 `true`。  
  
 ![LINQ 數量詞作業](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")  
  
 下節列出執行數量詞作業的標準查詢運算子方法。  
  
## <a name="methods"></a>方法  
  
|方法名稱|說明|Visual Basic 查詢運算式語法|更多資訊|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|全部|判斷序列中的所有項目是否都符合條件。|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|任何|判斷序列中的任何項目是否符合條件。|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|包含|判斷序列是否包含指定的項目。|不適用。|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>查詢運算式語法範例  
 這些範例使用`Aggregate`子句在 Visual Basic 中的 LINQ 查詢的篩選條件的一部分。  
  
 下列範例會使用`Aggregate`子句和<xref:System.Linq.Enumerable.All%2A>擴充方法，從集合傳回其寵物是所有早於指定存在時間這些人。  
  
 [!code-vb[CsLINQAnyAll#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_1.vb)]  
  
 下一個範例會使用`Aggregate`子句和<xref:System.Linq.Enumerable.Any%2A>擴充方法來傳回集合中至少有一個那些人 pet，小於指定存在時間。  
  
 [!code-vb[CsLINQAnyAll#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Linq>  
 [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Aggregate 子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [如何： 查詢包含一組指定的文字 (LINQ) (Visual Basic) 的句子](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
