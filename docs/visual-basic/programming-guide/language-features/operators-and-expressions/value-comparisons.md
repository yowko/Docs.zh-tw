---
title: 數值比較 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], comparing values
- Visual Basic code, operators
- Visual Basic code, expressions
- comparison operators [Visual Basic], comparing expressions
- numeric expressions
- operators [Visual Basic], comparison
- expressions [Visual Basic], comparing
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
ms.openlocfilehash: 6e1eda09784814d139ef94b6720b538aef30e5e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="value-comparisons-visual-basic"></a>數值比較 (Visual Basic)
比較運算子可用來建構比較數值變數的值的運算式。 這些運算式會傳回`Boolean`值根據是否比較為 true 或 false。 這類運算式的範例如下所示。  
  
 `45 > 26`  
  
 `26 > 45`  
  
 第一個運算式會評估為`True`，因為 45 大於 26。 第二個範例評估結果為`False`，因為 26 不大於 45。  
  
 您也可以比較這種方式中的數值運算式。 比較運算式本身可能是複雜的運算式，如下列範例所示。  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 先前的複雜運算式包含常值、 變數和函式呼叫。 比較運算子的兩邊運算式會評估，並產生的值會再使用比較`>=`比較運算子。 如果左側運算式的值是否大於或等於右運算式的值，整個運算式評估為`True`; 否則其評估結果為`False`。  
  
 比較值的運算式最常用於`If...Then`語法結構，如下列範例所示。  
  
 [!code-vb[VbVbalrOperators#84](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_1.vb)]  
  
 `=`號是比較運算子，以及指派運算子。 當做比較運算子使用時，它會評估在左邊的值是否等於右邊的值，如下列範例所示。  
  
 [!code-vb[VbVbalrOperators#85](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_2.vb)]  
  
 您也可以隨處使用比較運算式`Boolean`值是所需，例如`If`， `While`， `Loop`，或`ElseIf`陳述式，或是當您指派給或傳遞值至`Boolean`變數。 下列範例中，在比較運算式所傳回的值指派給`Boolean`變數。  
  
 [!code-vb[VbVbalrOperators#86](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_3.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [布林運算式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [運算子和運算式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [在 Visual Basic 中的比較運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [如何：計算數值](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)  
 [Visual Basic 中的運算子優先順序](../../../../visual-basic/language-reference/operators/operator-precedence.md)
