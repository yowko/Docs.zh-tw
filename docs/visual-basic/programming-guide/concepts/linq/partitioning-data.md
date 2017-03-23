---
title: "分割資料 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
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
ms.openlocfilehash: a746ce3e24812d1df6b6e221cca0364bf2cc7f1c
ms.lasthandoff: 03/13/2017

---
# <a name="partitioning-data-visual-basic"></a>資料分割 (Visual Basic)
LINQ 中的資料分割是指作業分成兩個區段，將輸入的序列，而不需要重新排列項目，並接著傳回其中一個區段。  
  
 下圖顯示三個不同資料分割的作業序列的字元的結果。 第一項作業會傳回序列中的前三個項目。 第二項作業會略過前三個項目，並傳回其餘項目。 第三個作業會略過序列中的前兩個項目，並傳回接下來的三項目。  
  
 ![LINQ 分割作業](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")  
  
 分割序列的標準查詢運算子方法詳列於下一節。  
  
## <a name="operators"></a>運算子  
  
|運算子名稱|描述|Visual Basic 查詢運算式語法|更多資訊|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|Skip|略過項目直到序列中指定的位置。|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Skip%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=fullName></xref:System.Linq.Queryable.Skip%2A?displayProperty=fullName>|  
|SkipWhile|根據述詞函式，直到項目不符合條件的項目會略過。|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=fullName></xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=fullName></xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=fullName>|  
|Take|會採用最序列中的指定位置的項目。|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Take%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=fullName></xref:System.Linq.Queryable.Take%2A?displayProperty=fullName>|  
|TakeWhile|會根據述詞函式，直到項目不符合條件的項目。|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=fullName></xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=fullName></xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-examples"></a>查詢運算式語法範例  
  
### <a name="skip"></a>Skip  
 下列程式碼範例使用`Skip`子句[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]略過的字串陣列中的前四個字串，再傳回陣列中的其餘字串。  
  
 [!code-vb[CsLINQPartitioning #&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_1.vb)]  
  
### <a name="skipwhile"></a>SkipWhile  
 下列程式碼範例使用`Skip While`子句[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]略過時的第一個字母字串的陣列中的字串為"a"。 傳回陣列中的其餘字串。  
  
 [!code-vb[CsLINQPartitioning #&2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_2.vb)]  
  
### <a name="take"></a>Take  
 下列程式碼範例使用`Take`子句[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]傳回字串陣列中的前兩個字串。  
  
 [!code-vb[CsLINQPartitioning #&3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_3.vb)]  
  
### <a name="takewhile"></a>TakeWhile  
 下列程式碼範例使用`Take While`子句[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]來傳回的字串陣列，而字串的長度為五個或更少。  
  
 [!code-vb[CsLINQPartitioning #&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_4.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Linq></xref:System.Linq>   
 [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Skip 子句](../../../../visual-basic/language-reference/queries/skip-clause.md)   
 [Skip While 子句](../../../../visual-basic/language-reference/queries/skip-while-clause.md)   
 [Take 子句](../../../../visual-basic/language-reference/queries/take-clause.md)   
 [Take While 子句](../../../../visual-basic/language-reference/queries/take-while-clause.md)
