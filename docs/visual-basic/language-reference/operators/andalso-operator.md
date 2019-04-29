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
ms.openlocfilehash: 3876fd9c32d486b8ebecc9ee2428486a687a1624
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608310"
---
# <a name="andalso-operator-visual-basic"></a>AndAlso 運算子 (Visual Basic)
執行最少運算邏輯結合兩個運算式上。  
  
## <a name="syntax"></a>語法  
  
```  
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`result`|必要項。 任何 `Boolean` 運算式。 結果是`Boolean`比較兩個運算式的結果。|  
|`expression1`|必要項。 任何 `Boolean` 運算式。|  
|`expression2`|必要項。 任何 `Boolean` 運算式。|  
  
## <a name="remarks"></a>備註  
 邏輯作業即所謂*最少運算*如果編譯的程式碼就可以略過運算式的評估，根據另一個運算式的結果。 如果評估的第一個運算式的結果判斷作業的最終結果，則不需要評估第二個運算式，因為它不能變更的最終結果。 如果已略過的運算式很複雜，或如果它包含程序呼叫，則最少運算可提升效能。  
  
 如果這兩個運算式都評估為`True`，`result`是`True`。 下表將說明如何`result`決定。  
  
|如果`expression1`是|和`expression2`是|值`result`是|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|（不會評估）|`False`|  
  
## <a name="data-types"></a>資料類型  
 `AndAlso`僅適用於定義運算子[布林資料型別](../../../visual-basic/language-reference/data-types/boolean-data-type.md)。 Visual Basic 會將轉換為所需的每個運算元`Boolean`，並執行作業完全`Boolean`。 如果您將結果指派給數值類型時，Visual Basic 會將它從`Boolean`為該型別。 這可能會產生非預期的行為。 例如，`5 AndAlso 12`會導致`–1`當轉換成`Integer`。  
  
## <a name="overloading"></a>多載化  
 [與運算子](../../../visual-basic/language-reference/operators/and-operator.md)並[IsFalse 運算子](../../../visual-basic/language-reference/operators/isfalse-operator.md)可以是*多載*，這表示，類別或結構可以重新定義其行為時運算元的類型，類別或結構。 多載`And`並`IsFalse`運算子會影響的行為`AndAlso`運算子。 如果您的程式碼會使用`AndAlso`上類別或結構，多載`And`和`IsFalse`，務必了解其重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`AndAlso`運算子執行邏輯結合兩個運算式上。 結果是`Boolean`表示整個優先運算式的值為 true。 如果第一個運算式為`False`，則不會評估第二個。  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 上述範例產生的結果`True`， `False`，和`False`分別。 計算`secondCheck`，因為已經是第一，不會評估第二個運算式`False`。 不過，第二個運算式評估的計算`thirdCheck`。  
  
## <a name="example"></a>範例  
 下列範例所示`Function`搜尋指定的值陣列的項目之間的程序。 如果陣列是空的或如果已超過陣列長度，`While`陳述式不會測試針對搜尋值的陣列項目。  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a>另請參閱

- [邏輯/位元運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [And 運算子](../../../visual-basic/language-reference/operators/and-operator.md)
- [IsFalse 運算子](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [在 Visual Basic 中的邏輯和位元運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
