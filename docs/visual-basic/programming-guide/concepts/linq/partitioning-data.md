---
title: 分割資料
ms.date: 07/20/2015
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
ms.openlocfilehash: 2ab4e27ef6d825b9100fc3c15b7a9554ae49e516
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353145"
---
# <a name="partitioning-data-visual-basic"></a>Partitioning Data (Visual Basic)
LINQ 中的分割是指將輸入序列分成兩個區段的作業，不用重新排列項目，然後傳回其中一個區段。  
  
 下圖顯示字元序列三種不同分割作業的結果。 第一項作業會傳回序列中的前三個項目。 第二項作業會略過前三個項目，傳回其餘項目。 第三個作業會略過序列中的前兩個項目，傳回接下來的三個元項目。  
  
 ![顯示三個 LINQ 分割作業的圖例。](./media/partitioning-data/linq-partitioning-operations.png)  
  
 分割序列的標準查詢運算子方法詳列於下一節。  
  
## <a name="operators"></a>運算子  
  
|運算子名稱|描述|Visual Basic Query Expression Syntax|更多資訊|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|Skip|略過項目直至序列中指定的位置為止。|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|SkipWhile|根據述詞函式跳過項目，直到不符合條件的項目為止。|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|採用序列中最多到指定位置為止的項目。|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|TakeWhile|根據述詞函式採用項目，直到不符合條件的項目為止。|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>查詢運算式語法範例  
  
### <a name="skip"></a>Skip  
 The following code example uses the `Skip` clause in Visual Basic to skip over the first four strings in an array of strings before returning the remaining strings in the array.  
  
 [!code-vb[CsLINQPartitioning#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#1)]  
  
### <a name="skipwhile"></a>SkipWhile  
 The following code example uses the `Skip While` clause in Visual Basic to skip over the strings in an array while the first letter of the string is "a". The remaining strings in the array are returned.  
  
 [!code-vb[CsLINQPartitioning#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#2)]  
  
### <a name="take"></a>Take  
 The following code example uses the `Take` clause in Visual Basic to return the first two strings in an array of strings.  
  
 [!code-vb[CsLINQPartitioning#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#3)]  
  
### <a name="takewhile"></a>TakeWhile  
 The following code example uses the `Take While` clause in Visual Basic to return strings from an array while the length of the string is five or less.  
  
 [!code-vb[CsLINQPartitioning#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#4)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.Linq>
- [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Skip 子句](../../../../visual-basic/language-reference/queries/skip-clause.md)
- [Skip While 子句](../../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Take 子句](../../../../visual-basic/language-reference/queries/take-clause.md)
- [Take While 子句](../../../../visual-basic/language-reference/queries/take-while-clause.md)
