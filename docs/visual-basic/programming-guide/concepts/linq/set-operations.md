---
title: "設定作業 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
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
ms.openlocfilehash: e835737b388427445a15b6658c7d148801f29b79
ms.lasthandoff: 03/13/2017

---
# <a name="set-operations-visual-basic"></a>設定作業 (Visual Basic)
產生的結果集根據相同或不同的集合 （或集合） 內的對等項目存在的查詢作業，請參閱 LINQ 中的 set 作業。  
  
 執行設定作業的標準查詢運算子方法詳列於下一節。  
  
## <a name="methods"></a>方法  
  
|方法名稱|描述|Visual Basic 查詢運算式語法|更多資訊|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Distinct|移除重複值的集合。|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=fullName></xref:System.Linq.Queryable.Distinct%2A?displayProperty=fullName>|  
|例外|傳回的集合差異，這表示不會出現在第二個集合的一個集合中項目。|不適用。|<xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=fullName></xref:System.Linq.Queryable.Except%2A?displayProperty=fullName>|  
|交集|傳回集合的交集，這表示會出現在兩個集合的項目。|不適用。|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=fullName></xref:System.Linq.Queryable.Intersect%2A?displayProperty=fullName>|  
|聯集|傳回的集合聯集，這表示會出現在兩個集合的唯一項目。|不適用。|<xref:System.Linq.Enumerable.Union%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Union%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=fullName></xref:System.Linq.Queryable.Union%2A?displayProperty=fullName>|  
  
## <a name="comparison-of-set-operations"></a>設定作業的比較  
  
### <a name="distinct"></a>Distinct  
 下圖說明的行為<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName>方法的一連串字元。</xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName> 傳回的序列包含輸入序列中的唯一項目。  
  
 ![顯示 distinct （） 的行為的圖形。](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "相異")  
  
### <a name="except"></a>例外  
 下圖說明<xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName>.</xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName>行為 傳回的序列包含只從第一個輸入序列中的項目不第二個輸入序列。  
  
 ![顯示 except （） 的動作圖形。](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")  
  
### <a name="intersect"></a>交集  
 下圖說明<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName>.</xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName>行為 傳回的序列中沒有包含通用於這兩個輸入序列的項目。  
  
 ![顯示兩個序列的交集的圖形。](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "交集")  
  
### <a name="union"></a>聯集  
 下圖說明兩個序列的字元聯集作業。 傳回的序列包含兩個輸入序列中的唯一項目。  
  
 ![顯示兩個序列的聯集圖形。](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")  
  
## <a name="query-expression-syntax-example"></a>查詢運算式語法範例  
 下列範例會使用`Distinct`子句在 LINQ 查詢中傳回唯一的數字從整數的清單。  
  
 [!code-vb[CsLINQSetOps #&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/set-operations_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Linq></xref:System.Linq>   
 [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Distinct 子句](../../../../visual-basic/language-reference/queries/distinct-clause.md)   
 [如何︰ 合併和比較字串集合 (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)   
 [如何︰ 尋找兩個清單 (LINQ) (Visual Basic) 之間的差異](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
