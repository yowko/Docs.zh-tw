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
ms.openlocfilehash: 3a43554fb25592bf413525a2df109010e4868492
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869629"
---
# <a name="where-clause-visual-basic"></a>Where 子句 (Visual Basic)

指定查詢的篩選準則。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Where condition  
```  
  
## <a name="parts"></a>組件  

 `condition`  
 必要。 運算式，判斷集合中目前專案的值是否包含在輸出集合中。 運算式必須評估為值 `Boolean` 或相等的 `Boolean` 值。 如果條件評估為 `True` ，元素就會包含在查詢結果中; 否則，會將元素從查詢結果中排除。  
  
## <a name="remarks"></a>備註  

 `Where`子句可讓您只選取符合特定準則的元素，以篩選查詢資料。 值導致 `Where` 子句進行評估的元素 `True` 會包含在查詢結果中; 其他元素則會被排除。 子句中使用的運算式 `Where` 必須評估為 `Boolean` 或相等的 `Boolean` ，例如， `False` 當其值為零時評估為的整數。 您可以 `Where` 使用邏輯運算子（例如 `And` 、 `Or` 、 `AndAlso` 、 `OrElse` 、 `Is` 和），將子句 `IsNot` 中的多個運算式結合在一起。  
  
 依預設，查詢運算式在存取之前都不會進行評估，例如，當資料系結或在迴圈中逐一查看時 `For` 。 因此，在 `Where` 存取查詢之前，不會評估子句。 如果您在子句中使用的查詢外部有值 `Where` ，請確定在執行查詢時，子句中使用了適當的值 `Where` 。 如需查詢執行的詳細資訊，請參閱 [撰寫您的第一個 LINQ 查詢](../../programming-guide/concepts/linq/writing-your-first-linq-query.md)。  
  
 您可以呼叫子句內的函式 `Where` ，對集合中目前元素的值執行計算或運算。 在子句中呼叫函式 `Where` 可能會導致查詢在定義時立即執行，而不是在存取時執行。 如需查詢執行的詳細資訊，請參閱 [撰寫您的第一個 LINQ 查詢](../../programming-guide/concepts/linq/writing-your-first-linq-query.md)。  
  
## <a name="example"></a>範例  

 下列查詢運算式使用 `From` 子句來為 `cust` 集合中的每個物件宣告範圍變數 `Customer` `customers` 。 `Where`子句會使用範圍變數，將輸出限制為來自指定區域的客戶。 `For Each`迴圈會顯示查詢結果中每個客戶的公司名稱。  
  
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
