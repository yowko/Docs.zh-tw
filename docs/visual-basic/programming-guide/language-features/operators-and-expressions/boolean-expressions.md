---
title: 布林運算式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- expressions [Visual Basic], Boolean
- expression evaluation [Visual Basic], Boolean expressions
- operators [Visual Basic], short-circuiting
- Visual Basic code, operators
- short-circuit evaluation
- logical operators [Visual Basic], short-circuiting
- operators [Visual Basic], Boolean
- Visual Basic code, expressions
ms.assetid: d3d90406-55c8-4404-8143-50fd7f0d0d1a
ms.openlocfilehash: ff5843c815658468ac69fe5d62a9ea4cac2be830
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="boolean-expressions-visual-basic"></a>布林運算式 (Visual Basic)
A*布林運算式*是評估為值的運算式[布林資料型別](../../../../visual-basic/language-reference/data-types/boolean-data-type.md):`True`或`False`。 `Boolean` 運算式可以採用數種格式。 最簡單的是直接比較值的`Boolean`變數設為`Boolean`常值，如下列範例所示。  
  
 [!code-vb[VbVbalrOperators#87](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_1.vb)]  
  
## <a name="two-meanings-of-the--operator"></a>兩個意義的 = 運算子  
 請注意，指派陳述式`newCustomer = True`與相同的運算式，在上述範例中，但是它會執行不同的函式，並使用方式。 在上述範例中，運算式`newCustomer = True`代表布林值，而`=`號會解譯為比較運算子。 在獨立的陳述式，`=`符號會解譯為指派運算子和指派左邊變數 右邊的值。 下列範例將說明這點。  
  
 [!code-vb[VbVbalrOperators#88](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_2.vb)]  
  
 如需詳細資訊，請參閱[值比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)和[陳述式](../../../../visual-basic/language-reference/statements/index.md)。  
  
## <a name="comparison-operators"></a>比較運算子  
 比較運算子，例如`=`， `<`， `>`， `<>`， `<=`，和`>=`比較運算子右邊的運算式的左邊的運算式所產生的布林運算式運算子和評估結果為`True`或`False`。 下列範例將說明這點。  
  
 `42 < 81`  
  
 由於 42 小於 81，上述範例中的布林運算式會評估為`True`。 如需這類運算式的詳細資訊，請參閱[值比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)。  
  
### <a name="comparison-operators-combined-with-logical-operators"></a>結合邏輯運算子的比較運算子  
 比較運算式可產生更複雜的布林運算式中使用邏輯運算子結合。 下列範例示範如何搭配使用邏輯運算子的比較運算子的使用。  
  
 `x > y And x < 1000`  
  
 在上述範例中，整個運算式的值取決於每一邊的運算式值`And`運算子。 如果這兩個運算式都是`True`，則整體的運算式會評估為`True`。 如果任一個運算式是`False`，則整個運算式會評估為`False`。  
  
## <a name="short-circuiting-operators"></a>最少運算運算子  
 邏輯運算子`AndAlso`和`OrElse`表現所謂*最少運算*。 最少運算運算子會先評估的左的運算元。 如果左的運算元判斷整個運算式的值，程式執行程序而不需要評估右運算式。 下列範例將說明這點。  
  
 [!code-vb[VbVbalrOperators#89](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_3.vb)]  
  
 在上述範例中，運算子會評估左邊的運算式， `45 < 12`。 因為左邊的運算式會評估為`False`，整個邏輯運算式必須評估為`False`。 程式執行，因此略過內的程式碼執行`If`區塊，而不需要評估右運算式， `testFunction(3)`。 此範例不會呼叫`testFunction()`因為左邊的運算式證明整個運算式。  
  
 同樣地，如果左邊的運算式中使用邏輯運算式`OrElse`評估為`True`，繼續執行至下一行程式碼而不需要評估右運算式，因為左邊的運算式已經驗證整個運算式。  
  
### <a name="comparison-with-non-short-circuiting-operators"></a>具有非最少運算運算子的比較  
 相反地，會評估邏輯運算子的兩側時邏輯運算子`And`和`Or`可用。 下列範例將說明這點。  
  
 [!code-vb[VbVbalrOperators#90](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_4.vb)]  
  
 上述範例會呼叫`testFunction()`即使左邊的運算式評估為`False`。  
  
## <a name="parenthetical-expressions"></a>括號運算式  
 您可以使用括號控制的布林運算式的評估順序。 先評估括號括住的運算式。 多個巢狀層級，優先順序會授與給巢狀最深處的運算式。 括號內評估會繼續根據運算子優先順序的規則。 如需詳細資訊，請參閱[Visual Basic 中的運算子優先順序](../../../../visual-basic/language-reference/operators/operator-precedence.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Basic 中的邏輯和位元運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [數值比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [陳述式](../../../../visual-basic/programming-guide/language-features/statements.md)  
 [比較運算子](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [有效的運算子組合](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)  
 [Visual Basic 中的運算子優先順序](../../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Boolean 資料類型](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)
