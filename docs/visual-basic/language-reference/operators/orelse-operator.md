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
ms.openlocfilehash: d5a0a3420d86df67e38df390ce98fbbe43c69459
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981346"
---
# <a name="orelse-operator-visual-basic"></a>OrElse 運算子 (Visual Basic)
執行最少運算的兩個運算式上的內含邏輯分離。  
  
## <a name="syntax"></a>語法  
  
```  
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
 邏輯作業即所謂*最少運算*如果編譯的程式碼就可以略過運算式的評估，根據另一個運算式的結果。 如果評估的第一個運算式的結果判斷作業的最終結果，則不需要評估第二個運算式，因為它不能變更的最終結果。 如果已略過的運算式很複雜，或如果它包含程序呼叫，則最少運算可提升效能。  
  
 如果任一個或兩個運算式都評估為`True`，`result`是`True`。 下表將說明如何`result`決定。  
  
|如果`expression1`是|和`expression2`是|值`result`是|  
|-------------------------|--------------------------|------------------------------|  
|`True`|（不會評估）|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a>資料類型  
 `OrElse`僅適用於定義運算子[布林資料型別](../../../visual-basic/language-reference/data-types/boolean-data-type.md)。 Visual Basic 會將轉換為所需的每個運算元`Boolean`，並執行作業完全`Boolean`。 如果您將結果指派給數值類型時，Visual Basic 會將它從`Boolean`為該型別。 這可能會產生非預期的行為。 例如，`5 OrElse 12`會導致`–1`當轉換成`Integer`。  
  
## <a name="overloading"></a>多載化  
 [或運算子](../../../visual-basic/language-reference/operators/or-operator.md)並[IsTrue 運算子](../../../visual-basic/language-reference/operators/istrue-operator.md)可以是*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別的型別或結構。 多載`Or`並`IsTrue`運算子會影響的行為`OrElse`運算子。 如果您的程式碼會使用`OrElse`上類別或結構，多載`Or`和`IsTrue`，務必了解其重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`OrElse`上兩個運算式執行邏輯分離的運算子。 結果是`Boolean`值，表示其中兩個運算式是否為 true。 如果第一個運算式為`True`，則不會評估第二個。  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 上述範例產生的結果`True`， `True`，和`False`分別。 計算`firstCheck`，因為已經是第一，不會評估第二個運算式`True`。 不過，第二個運算式評估的計算`secondCheck`。  
  
## <a name="example"></a>範例  
 下列範例所示`If`...`Then`包含兩個程序呼叫陳述式。 如果第一次呼叫傳回`True`，不會呼叫第二個程序。 如果第二個程序執行的重要工作，應該一律在這段程式碼執行時才執行，這可能產生非預期的結果。  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a>另請參閱
- [邏輯/位元運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Or 運算子](../../../visual-basic/language-reference/operators/or-operator.md)
- [IsTrue 運算子](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [在 Visual Basic 中的邏輯和位元運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
