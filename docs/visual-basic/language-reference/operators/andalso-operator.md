---
title: AndAlso 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AndAlso
- AndAlso
helpviewer_keywords:
- short-circuiting
- AndAlso operator [Visual Basic]
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], conjunction
- short-circuit evaluation
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
ms.openlocfilehash: a52f598c8a7c7a79b0f2436f1add7b3eb5d5261b
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835233"
---
# <a name="andalso-operator-visual-basic"></a>AndAlso 運算子 (Visual Basic)
在兩個運算式上執行短路邏輯結合。  
  
## <a name="syntax"></a>語法  
  
```vb
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`result`|必要項。 任何 `Boolean` 運算式。 結果會是兩個運算式的比較 @no__t 0 的結果。|  
|`expression1`|必要項。 任何 `Boolean` 運算式。|  
|`expression2`|必要項。 任何 `Boolean` 運算式。|  
  
## <a name="remarks"></a>備註  
 *如果已*編譯的程式碼可以根據另一個運算式的結果，略過一個運算式的評估，則邏輯作業稱為「最少運算」。 如果第一個運算式評估的結果決定了作業的最後結果，就不需要評估第二個運算式，因為它無法變更最終的結果。 如果略過的運算式很複雜，或如果它牽涉到程序呼叫，則最少運算可以改善效能。  
  
 如果兩個運算式都評估為 `True`，`result` 會 `True`。 下表說明如何判斷 `result`。  
  
|如果`expression1`為|和`expression2`為|@No__t-0 的值為|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|（未評估）|`False`|  
  
## <a name="data-types"></a>資料類型  
 @No__t-0 運算子只會針對[布林資料類型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)來定義。 Visual Basic 在評估運算式之前，會視需要將每個運算元轉換為 `Boolean`。 如果您將結果指派給數數值型別，Visual Basic 會將它從 `Boolean` 轉換成該類型，如此 `False` 會變成 `0`，而 `True` 會變成 `-1`。
如需詳細資訊，請參閱布林型別[轉換](../data-types/boolean-data-type.md#type-conversions)。
  
## <a name="overloading"></a>多載化  
 [And 運算子](../../../visual-basic/language-reference/operators/and-operator.md)和[IsFalse 運算子](../../../visual-basic/language-reference/operators/isfalse-operator.md)可以多載，這表示當運算元具有該類別或結構的類型*時，類別*或結構可以重新定義其行為。 多載 `And` 和 @no__t 1 運算子會影響 @no__t 2 運算子的行為。 如果您的程式碼在多載 `And` 和 `IsFalse` 的類別或結構上使用 `AndAlso`，請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用 `AndAlso` 運算子，在兩個運算式上執行邏輯結合。 結果為 @no__t 0 的值，表示整個子句運算式是否為 true。 如果第一個運算式 `False`，則不會評估第二個運算式。  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 上述範例會分別產生 `True`、`False` 和 `False` 的結果。 在 `secondCheck` 的計算中，因為第一個運算式已經 `False`，所以不會進行評估。 不過，第二個運算式會在 `thirdCheck` 的計算中進行評估。  
  
## <a name="example"></a>範例  
 下列範例顯示的 `Function` 程式會在陣列的元素之間搜尋指定的值。 如果陣列是空的，或超過陣列長度，則 `While` 語句不會針對搜尋值測試陣列元素。  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a>另請參閱

- [邏輯/位運算子（Visual Basic）](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [And 運算子](../../../visual-basic/language-reference/operators/and-operator.md)
- [IsFalse 運算子](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [Visual Basic 中的邏輯和位運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
