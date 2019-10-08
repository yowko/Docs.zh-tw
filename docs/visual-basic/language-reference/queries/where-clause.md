---
title: Where 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: 404dd848058f7e5c9bc8a74b6d89df18c6c55fad
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005007"
---
# <a name="where-clause-visual-basic"></a>Where 子句 (Visual Basic)
指定查詢的篩選準則。  
  
## <a name="syntax"></a>語法  
  
```vb  
Where condition  
```  
  
## <a name="parts"></a>組件  
 `condition`  
 必要項。 運算式，判斷集合中目前專案的值是否包含在輸出集合中。 運算式必須評估為 `Boolean` 值或等於 `Boolean` 值。 如果條件評估為 `True`，則元素會包含在查詢結果中;否則，會從查詢結果中排除元素。  
  
## <a name="remarks"></a>備註  
 @No__t-0 子句可讓您只選取符合特定準則的元素來篩選查詢資料。 其值導致 `Where` 子句評估為 `True` 的元素會包含在查詢結果中;排除其他元素。 @No__t-0 子句中使用的運算式必須評估為 `Boolean` 或對等的 `Boolean`，例如當其值為零時，評估為 `False` 的整數。 您可以使用邏輯運算子（例如 `And`、`Or`、`AndAlso`、`OrElse`、`Is` 和 `IsNot`）來結合 @no__t 0 子句中的多個運算式。  
  
 根據預設，查詢運算式在存取之前不會進行評估，例如，當資料系結或在 `For` 迴圈中反復執行時。 因此，在存取查詢之前，不會評估 `Where` 子句。 如果您在 `Where` 子句中使用查詢外部的值，請確定在執行查詢時，`Where` 子句中使用適當的值。 如需查詢執行的詳細資訊，請參閱[撰寫您的第一個 LINQ 查詢](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)。  
  
 您可以呼叫 `Where` 子句內的函式，從集合中目前元素的值執行計算或運算。 呼叫 `Where` 子句中的函式可能會在定義時立即執行查詢，而不是在存取時。 如需查詢執行的詳細資訊，請參閱[撰寫您的第一個 LINQ 查詢](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)。  
  
## <a name="example"></a>範例  
 下列查詢運算式會使用 `From` 子句，針對 `customers` 集合中的每個 @no__t 2 物件，宣告範圍變數 `cust`。 @No__t-0 子句會使用範圍變數，將輸出限制為來自指定區域的客戶。 [@No__t-0] 迴圈會在查詢結果中顯示每個客戶的公司名稱。  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a>範例  
 下列範例會在 `Where` 子句中使用 `And` 和 @no__t 1 邏輯運算子。  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [查詢](../../../visual-basic/language-reference/queries/index.md)
- [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)
- [For Each...Next 陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
