---
title: Where 子句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: b80bb047551dee8ab23cfac06b961996992d69b5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359537"
---
# <a name="where-clause-visual-basic"></a>Where 子句 (Visual Basic)
指定查詢的篩選準則。  
  
## <a name="syntax"></a>語法  
  
```vb  
Where condition  
```  
  
## <a name="parts"></a>組件  
 `condition`  
 必要。 運算式，判斷集合中目前專案的值是否包含在輸出集合中。 運算式必須評估為 `Boolean` 值或對等的 `Boolean` 值。 如果條件評估為 `True` ，則專案會包含在查詢結果中，否則會從查詢結果中排除元素。  
  
## <a name="remarks"></a>備註  
 `Where`子句可讓您只選取符合特定準則的元素來篩選查詢資料。 其值會讓 `Where` 子句評估為的元素 `True` 會包含在查詢結果中，而其他元素則會排除。 子句中使用的運算式 `Where` 必須評估為或的對 `Boolean` 等 `Boolean` ，例如在 `False` 其值為零時評估為的整數。 您可以 `Where` 使用邏輯運算子（例如 `And` 、 `Or` 、 `AndAlso` 、 `OrElse` 、 `Is` 和 `IsNot` ）結合子句中的多個運算式。  
  
 根據預設，查詢運算式在存取之前不會進行評估，例如，當資料系結或在迴圈中反復執行時 `For` 。 因此，在 `Where` 存取查詢之前，不會評估子句。 如果您在子句中使用的查詢外部有值 `Where` ，請確定在執行查詢時，子句中使用了適當的值 `Where` 。 如需查詢執行的詳細資訊，請參閱[撰寫您的第一個 LINQ 查詢](../../programming-guide/concepts/linq/writing-your-first-linq-query.md)。  
  
 您可以在子句內呼叫函式 `Where` ，以從集合中目前專案的值執行計算或運算。 呼叫子句中的函式 `Where` 可能會導致查詢在定義時立即執行，而不是存取時。 如需查詢執行的詳細資訊，請參閱[撰寫您的第一個 LINQ 查詢](../../programming-guide/concepts/linq/writing-your-first-linq-query.md)。  
  
## <a name="example"></a>範例  
 下列查詢運算式會使用 `From` 子句， `cust` 針對集合中的每個物件宣告範圍變數 `Customer` `customers` 。 `Where`子句會使用範圍變數，將輸出限制為來自指定區域的客戶。 `For Each`迴圈會在查詢結果中顯示每個客戶的公司名稱。  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a>範例  
 下列範例會 `And` `Or` 在子句中使用和邏輯運算子 `Where` 。  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [查詢](index.md)
- [From 子句](from-clause.md)
- [Select 子句](select-clause.md)
- [For Each...Next 陳述式](../statements/for-each-next-statement.md)
