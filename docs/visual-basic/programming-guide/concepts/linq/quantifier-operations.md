---
title: 數量詞作業
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: 0c1c69cb36ac16126454dc0c24cd84fc85b0b218
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075300"
---
# <a name="quantifier-operations-visual-basic"></a>數量詞作業 (Visual Basic) 

數量詞作業會傳回 <xref:System.Boolean> 值，指出序列中的部分或所有項目是否符合條件。  
  
 下圖說明兩個不同來源序列上的兩個不同數量詞作業。 第一個作業會詢問一個或多個項目是否為字元 'A'，而結果為 `true`。 第二個作業會詢問所有項目是否都為字元 'A'，而結果為 `true`。  
  
 ![LINQ 數量詞作業](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 下節列出執行數量詞作業的標準查詢運算子方法。  
  
## <a name="methods"></a>方法  
  
|方法名稱|描述|Visual Basic 查詢運算式語法|相關資訊|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|全部|判斷序列中的所有項目是否都符合條件。|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|任意|判斷序列中的任何項目是否符合條件。|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|包含|判斷序列是否包含指定的項目。|不適用。|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>查詢運算式語法範例  

 這些範例使用 `Aggregate` Visual Basic 中的子句作為 LINQ 查詢中篩選準則的一部分。  
  
 下列範例 `Aggregate` 會使用子句和 <xref:System.Linq.Enumerable.All%2A> 延伸方法，從集合中傳回其寵物全都早于指定年齡的人員。  
  
 [!code-vb[CsLINQAnyAll#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#1)]  
  
 下一個範例會使用 `Aggregate` 子句和 <xref:System.Linq.Enumerable.Any%2A> 延伸方法，從集合中傳回至少有一個寵物早于指定年齡的人。  
  
 [!code-vb[CsLINQAnyAll#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Linq>
- [標準查詢運算子概觀 (Visual Basic)](standard-query-operators-overview.md)
- [Aggregate Clause](../../../language-reference/queries/aggregate-clause.md)
- [如何：查詢包含指定字組的句子 (LINQ) (Visual Basic)](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
