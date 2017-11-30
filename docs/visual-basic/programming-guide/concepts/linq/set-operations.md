---
title: "設定作業 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2e30c521635326afeea4aad9ce932d5206d06c6d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="set-operations-visual-basic"></a>設定作業 (Visual Basic)
LINQ 中的設定作業指的是產生結果集的查詢作業，而結果集是根據相同或不同集合 (集) 內是否有對等項目而定。  
  
 下節列出執行設定作業的標準查詢運算子方法。  
  
## <a name="methods"></a>方法  
  
|方法名稱|說明|Visual Basic 查詢運算式語法|更多資訊|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Distinct|移除集合中的重複值。|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|例外|傳回集差異，表示未出現在第二個集合中的某個集合中的項目。|不適用。|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|交集|傳回集交集，表示出現在這兩個集合中的項目。|不適用。|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|聯集|傳回集聯集，表示出現在兩個集合中任一集合的唯一項目。|不適用。|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a>比較設定作業  
  
### <a name="distinct"></a>Distinct  
 下圖說明一連串字元的 <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> 方法行為。 所傳回的序列包含輸入序列中的唯一項目。  
  
 ![顯示 Distinct&#40;&#41; 行為的圖形。](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinct")  
  
### <a name="except"></a>例外  
 下圖說明 <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType> 的行為。 所傳回的序列只包含第一個輸入序列中不在第二個輸入序列中的項目。  
  
 ![顯示 Except&#40;&#41; 動作的圖形。](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")  
  
### <a name="intersect"></a>交集  
 下圖說明 <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType> 的行為。 所傳回的序列包含兩個輸入序列共有的項目。  
  
 ![顯示兩種序列交集的圖形。](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")  
  
### <a name="union"></a>聯集  
 下圖說明兩個字元序列的聯合作業。 所傳回的序列包含兩個輸入序列中的唯一項目。  
  
 ![顯示兩個序列聯集的圖形。](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")  
  
## <a name="query-expression-syntax-example"></a>查詢運算式語法範例  
 下列範例會使用`Distinct`LINQ 查詢來傳回唯一的數字從整數的清單中的子句。  
  
 [!code-vb[CsLINQSetOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/set-operations_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Linq>  
 [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Distinct 子句](../../../../visual-basic/language-reference/queries/distinct-clause.md)  
 [如何： 合併和比較字串集合 (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)  
 [如何： 尋找兩個清單 (LINQ) (Visual Basic) 之間的差異](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
