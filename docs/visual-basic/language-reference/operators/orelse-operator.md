---
title: OrElse 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- OrElse
- vb.OrElse
helpviewer_keywords:
- short-circuiting
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], disjunction
- short-circuit evaluation
- OrElse operator [Visual Basic]
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
ms.openlocfilehash: 8290e642db3ec76a931bdd2febe427309457bc86
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835237"
---
# <a name="orelse-operator-visual-basic"></a>OrElse 運算子 (Visual Basic)
在兩個運算式上執行最少運算（含）運算邏輯分離。  
  
## <a name="syntax"></a>語法  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要項。 任何 `Boolean` 運算式。  
  
 `expression1`  
 必要項。 任何 `Boolean` 運算式。  
  
 `expression2`  
 必要項。 任何 `Boolean` 運算式。  
  
## <a name="remarks"></a>備註  
 *如果已*編譯的程式碼可以根據另一個運算式的結果，略過一個運算式的評估，則邏輯作業稱為「最少運算」。 如果第一個運算式評估的結果決定了作業的最後結果，就不需要評估第二個運算式，因為它無法變更最終的結果。 如果略過的運算式很複雜，或如果它牽涉到程序呼叫，則最少運算可以改善效能。  
  
 如果任一個或兩個運算式評估為 `True`，`result` 會 `True`。 下表說明如何判斷 `result`。  
  
|如果`expression1`為|和`expression2`為|@No__t-0 的值為|  
|-------------------------|--------------------------|------------------------------|  
|`True`|（未評估）|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a>資料類型  
 @No__t-0 運算子只會針對[布林資料類型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)來定義。 Visual Basic 在評估運算式之前，會視需要將每個運算元轉換為 `Boolean`。 如果您將結果指派給數數值型別，Visual Basic 會將它從 `Boolean` 轉換成該類型，如此 `False` 會變成 `0`，而 `True` 會變成 `-1`。
如需詳細資訊，請參閱布林型別[轉換](../data-types/boolean-data-type.md#type-conversions)。
  
## <a name="overloading"></a>多載化  
 [Or 運算子](../../../visual-basic/language-reference/operators/or-operator.md)和[IsTrue 運算子](../../../visual-basic/language-reference/operators/istrue-operator.md)可以多載，這表示當運算元具有該類別或結構的類型*時，類別*或結構可以重新定義其行為。 多載 `Or` 和 @no__t 1 運算子會影響 @no__t 2 運算子的行為。 如果您的程式碼在多載 `Or` 和 `IsTrue` 的類別或結構上使用 `OrElse`，請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用 `OrElse` 運算子，在兩個運算式上執行邏輯分離。 結果為 @no__t 0 的值，表示兩個運算式的其中一個是否為 true。 如果第一個運算式 `True`，則不會評估第二個運算式。  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 上述範例會分別產生 `True`、`True` 和 `False` 的結果。 在 `firstCheck` 的計算中，因為第一個運算式已經 `True`，所以不會進行評估。 不過，第二個運算式會在 `secondCheck` 的計算中進行評估。  
  
## <a name="example"></a>範例  
 下列範例顯示包含兩個程序呼叫的 `If` ... @no__t 1 語句。 如果第一次呼叫傳回 `True`，則不會呼叫第二個程式。 如果第二個程式執行程式碼的這個區段時一定要執行的重要工作，這可能會產生非預期的結果。  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a>另請參閱

- [邏輯/位運算子（Visual Basic）](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Or 運算子](../../../visual-basic/language-reference/operators/or-operator.md)
- [IsTrue 運算子](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Visual Basic 中的邏輯和位運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
