---
title: "數量詞作業 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7f69aed2e0e6791ca7f17c3420ff75a1ba220187
ms.lasthandoff: 03/13/2017

---
# <a name="quantifier-operations-visual-basic"></a>數量詞作業 (Visual Basic)
數量詞作業傳回<xref:System.Boolean>值，指出部分或全部順序中的項目是否全都符合條件。</xref:System.Boolean>  
  
 下圖顯示兩個不同的來源序列的兩個不同的數量詞作業。 第一項作業會要求，是否一或多個項目是字元 'A'，且結果為`true`。 第二項作業會要求，是否所有的項目為字元 'A'，且結果為`true`。  
  
 ![LINQ 數量詞作業](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")  
  
 執行數量詞作業的標準查詢運算子方法詳列於下一節。  
  
## <a name="methods"></a>方法  
  
|方法名稱|說明|Visual Basic 查詢運算式語法|更多資訊|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|全部|判斷序列中的所有項目是否全都符合條件。|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=fullName></xref:System.Linq.Enumerable.All%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=fullName></xref:System.Linq.Queryable.All%2A?displayProperty=fullName>|  
|任何|判斷序列中的任何項目是否全都符合條件。|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=fullName></xref:System.Linq.Queryable.Any%2A?displayProperty=fullName>|  
|包含|判斷序列是否包含指定的項目。|不適用。|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Contains%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=fullName></xref:System.Linq.Queryable.Contains%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-examples"></a>查詢運算式語法範例  
 這些範例使用`Aggregate`子句在 Visual Basic 中的 LINQ 查詢的篩選條件的一部分。  
  
 下列範例會使用`Aggregate`子句和<xref:System.Linq.Enumerable.All%2A>擴充方法，從集合中傳回這些人的寵物是所有超過指定的年齡。</xref:System.Linq.Enumerable.All%2A>  
  
 [!code-vb[CsLINQAnyAll #&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_1.vb)]  
  
 下一個範例使用`Aggregate`子句和<xref:System.Linq.Enumerable.Any%2A>擴充方法來傳回集合中至少有一個這些人拍拍，已超過指定的年齡。</xref:System.Linq.Enumerable.Any%2A>  
  
 [!code-vb[CsLINQAnyAll #&2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Linq></xref:System.Linq>   
 [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Aggregate 子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)   
 [如何︰ 查詢包含一組指定的文字 (LINQ) (Visual Basic) 的句子](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
