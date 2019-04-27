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
ms.openlocfilehash: 270b226d0a1aa7d08721e6f9ed36d68492685af3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864387"
---
# <a name="value-comparisons-visual-basic"></a>數值比較 (Visual Basic)
比較運算子可用來建構比較數值變數的值的運算式。 這些運算式會傳回`Boolean`值根據比較為 true 或 false。 這類運算式的範例如下所示。  
  
 `45 > 26`  
  
 `26 > 45`  
  
 第一個運算式評估為`True`，因為 45 大於 26。 第二個範例評估結果為`False`，因為不是大於 45 26。  
  
 您也可以比較這種方式中的數值運算式。 您比較運算式本身可能是複雜的運算式，如下列範例所示。  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 先前的複雜運算式包含常值、 變數和函式呼叫。 比較運算子兩邊的運算式會評估，並產生的值然後比較使用`>=`比較運算子。 如果運算式左邊的值是否大於或等於右運算式的值，整個運算式評估為`True`; 否則它會評估為`False`。  
  
 最常用於比較值的運算式`If...Then`建構，如下列範例所示。  
  
 [!code-vb[VbVbalrOperators#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#84)]  
  
 `=`符號是比較運算子，以及指派運算子。 當做比較運算子使用時，它會評估在左邊的值是否等於右邊的值，如下列範例所示。  
  
 [!code-vb[VbVbalrOperators#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#85)]  
  
 您也可以隨處使用比較運算式`Boolean`值是所需的例如，在`If`， `While`， `Loop`，或`ElseIf`陳述式，或是當您將指派給，或將值傳遞至`Boolean`變數。 在下列範例中，比較運算式所傳回的值指派給`Boolean`變數。  
  
 [!code-vb[VbVbalrOperators#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#86)]  
  
## <a name="see-also"></a>另請參閱

- [布林運算式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [運算子和運算式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [在 Visual Basic 中的比較運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [如何：計算數值](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [Visual Basic 中的運算子優先順序](../../../../visual-basic/language-reference/operators/operator-precedence.md)
