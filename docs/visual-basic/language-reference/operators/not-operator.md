---
title: Not 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: 332cee57c8d25d7f51737e01e70ba515d50bd6e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="not-operator-visual-basic"></a>Not 運算子 (Visual Basic)
上執行邏輯否定`Boolean`運算式或數值運算式上的位元否定運算。  
  
## <a name="syntax"></a>語法  
  
```  
result = Not expression  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要。 任何`Boolean`或數值運算式。  
  
 `expression`  
 必要。 任何`Boolean`或數值運算式。  
  
## <a name="remarks"></a>備註  
 如`Boolean`運算式下, 表將說明如何`result`決定。  
  
|如果`expression`是|值`result`是|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 針對數值運算式，`Not`運算子反轉任何數值運算式的位元值和對應的中位元設`result`根據下表。  
  
|如果位元`expression`是|中的位元`result`是|  
|-------------------------------|----------------------------|  
|1|0|  
|0|1|  
  
> [!NOTE]
>  因為邏輯和位元運算子會有較低的優先順序高於其他算術和關係運算子，所以任何位元運算應該括在括號可確保能夠正確執行。  
  
## <a name="data-types"></a>資料類型  
 布林值的否定運算結果的資料型別是`Boolean`。 位元否定運算，將結果資料類型是屬於相同`expression`。 不過，如果運算式是`Decimal`，結果是`Long`。  
  
## <a name="overloading"></a>多載化  
 `Not`運算子可以是*多載*，這表示，類別或結構可以重新定義它的行為時其運算元的該類別或結構的類型。 如果您的程式碼會使用此運算子，這類類別或結構上，請確定您了解其重新定義的行為。 如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`Not`上執行邏輯否定運算子`Boolean`運算式。 結果是`Boolean`值，表示運算式值的反向。  
  
 [!code-vb[VbVbalrOperators#33](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_1.vb)]  
  
 上述範例產生的結果`False`和`True`分別。  
  
## <a name="example"></a>範例  
 下列範例會使用`Not`運算子執行邏輯否定的數值運算式的個別位元。 結果模式中的位元會設定為在運算元模式中，包括正負號位元的對應位元的反向。  
  
 [!code-vb[VbVbalrOperators#34](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_2.vb)]  
  
 上述範例中會分別產生-11-9 及-7 的結果。  
  
## <a name="see-also"></a>另請參閱  
 [邏輯/位元運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [在 Visual Basic 中的邏輯和位元運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
