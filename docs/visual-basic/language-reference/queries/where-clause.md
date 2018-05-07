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
ms.openlocfilehash: 0b61a52a366fb37a0834c9223bc8b7f099354d16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="where-clause-visual-basic"></a>Where 子句 (Visual Basic)
指定查詢的篩選條件。  
  
## <a name="syntax"></a>語法  
  
```  
Where condition  
```  
  
## <a name="parts"></a>組件  
 `condition`  
 必要。 決定輸出集合中是否包含在集合中目前的項目值的運算式。 運算式必須評估為`Boolean`值或相當的`Boolean`值。 如果條件評估為`True`、 項目包含查詢結果中; 否則項目從查詢結果中排除。  
  
## <a name="remarks"></a>備註  
 `Where`子句可讓您選取符合特定準則的項目來篩選查詢資料。 項目，其值會導致`Where`子句評估為`True`隨附在查詢結果; 會排除其他項目。 使用中的運算式`Where`子句必須評估為`Boolean`或相當的`Boolean`，例如評估為整數`False`當其值是零。 您可以結合多個運算式中的`Where`子句使用邏輯運算子，像是`And`， `Or`， `AndAlso`， `OrElse`， `Is`，和`IsNot`。  
  
 根據預設，查詢運算式才會評估存取 — 比方說，當它們是資料繫結或中逐一`For`迴圈。 如此一來，`Where`存取查詢之前，將不評估子句。 如果您有外部查詢中所使用的值`Where`子句，確定適當的值用於`Where`子句在執行查詢的時間。 如需有關查詢執行的詳細資訊，請參閱[撰寫您的第一個 LINQ 查詢](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)。  
  
 您可以呼叫函式內`Where`子句來執行計算或作業的值從集合中目前的項目。 呼叫函式`Where`子句可能會造成當它定義而不是存取時，立即執行查詢。 如需有關查詢執行的詳細資訊，請參閱[撰寫您的第一個 LINQ 查詢](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)。  
  
## <a name="example"></a>範例  
 下列查詢運算式使用`From`子句來宣告範圍變數`cust`每個`Customer`物件存放至`customers`集合。 `Where`子句來限制輸出給客戶，從指定的地區中使用的範圍變數。 `For Each`迴圈會顯示查詢結果中的每個客戶的公司名稱。  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_1.vb)]  
  
## <a name="example"></a>範例  
 下列範例會使用`And`和`Or`的邏輯運算子`Where`子句。  
  
 [!code-vb[VbSimpleQuerySamples#31](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [查詢](../../../visual-basic/language-reference/queries/queries.md)  
 [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)  
 [For Each...Next 陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
