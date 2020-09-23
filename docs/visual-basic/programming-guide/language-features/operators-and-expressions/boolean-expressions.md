---
title: 布林運算式
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
ms.openlocfilehash: 51340bf95795d837c055df796424f3cad912adc7
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085746"
---
# <a name="boolean-expressions-visual-basic"></a>布林運算式 (Visual Basic)

*布林運算式*是評估為[布林資料類型](../../../language-reference/data-types/boolean-data-type.md)值的運算式： `True` 或 `False` 。 `Boolean` 運算式可以採用數種形式。 最簡單的方式就是將變數值直接與 `Boolean` 常值進行比較 `Boolean` ，如下列範例所示。  
  
 [!code-vb[VbVbalrOperators#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#87)]  
  
## <a name="two-meanings-of-the--operator"></a>= 運算子的兩個意義  

 請注意，指派語句 `newCustomer = True` 看起來與上述範例中的運算式相同，但它會執行不同的函式，並使用不同的方式。 在上述範例中，運算式 `newCustomer = True` 代表布林值，而且 `=` 會將正負號解釋為比較運算子。 在獨立的語句中，會將 `=` 正負號視為指派運算子，並將右邊的值指派給左邊的變數。 下列範例將說明這點。  
  
 [!code-vb[VbVbalrOperators#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#88)]  
  
 如需詳細資訊，請參閱 [值比較](value-comparisons.md) 和 [語句](../../../language-reference/statements/index.md)。  
  
## <a name="comparison-operators"></a>比較運算子  

 比較運算子（例如 `=` 、 `<` 、、、和）會將 `>` `<>` `<=` `>=` 運算子左邊的運算式與運算子右邊的運算式進行比較，並將結果評估為 or，以產生布林運算式 `True` `False` 。 下列範例將說明這點。  
  
 `42 < 81`  
  
 因為42小於81，所以上述範例中的布林運算式會評估為 `True` 。 如需這種運算式的詳細資訊，請參閱 [值比較](value-comparisons.md)。  
  
### <a name="comparison-operators-combined-with-logical-operators"></a>比較運算子與邏輯運算子結合  

 您可以使用邏輯運算子來結合比較運算式，以產生更複雜的布林運算式。 下列範例示範如何使用比較運算子搭配邏輯運算子。  
  
 `x > y And x < 1000`  
  
 在上述範例中，整體運算式的值取決於運算子每一端的運算式值 `And` 。 如果這兩個運算式都是 `True` ，則整體運算式會評估為 `True` 。 如果任一運算式為 `False` ，則整個運算式會評估為 `False` 。  
  
## <a name="short-circuiting-operators"></a>短路運算子  

 邏輯運算子 `AndAlso` 和 `OrElse` 表現行為，稱為「最 *小*運算」。 短路運算子會先評估左運算元。 如果左運算元決定整個運算式的值，則會繼續執行程式，而不會評估正確的運算式。 下列範例將說明這點。  
  
 [!code-vb[VbVbalrOperators#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#89)]  
  
 在上述範例中，運算子會評估左邊的運算式 `45 < 12` 。 因為左運算式會評估為 `False` ，所以整個邏輯運算式必須評估為 `False` 。 程式執行會在區塊內略過程式碼的執行 `If` ，而不需要評估正確的運算式 `testFunction(3)` 。 `testFunction()`因為左運算式 falsifies 整個運算式，所以不會呼叫這個範例。  
  
 同樣地，如果使用的邏輯運算式中的左運算式 `OrElse` 評估為 `True` ，就會繼續執行到下一行程式碼，而不會評估右邊的運算式，因為左運算式已經驗證整個運算式。  
  
### <a name="comparison-with-non-short-circuiting-operators"></a>與非短路運算運算子的比較  

 相反地，在使用邏輯運算子和時，會評估邏輯運算子的 `And` 兩邊 `Or` 。 下列範例將說明這點。  
  
 [!code-vb[VbVbalrOperators#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#90)]  
  
 `testFunction()`即使左運算式評估為，上述範例仍會呼叫 `False` 。  
  
## <a name="parenthetical-expressions"></a>括號運算式  

 您可以使用括弧來控制布林運算式的評估順序。 以括弧括住的運算式會先進行評估。 針對多個嵌套層級，會將優先順序授與最深的嵌套運算式。 在括弧內，評估會根據運算子優先順序的規則繼續進行。 如需詳細資訊，請參閱 [Visual Basic 中的運算子優先順序](../../../language-reference/operators/operator-precedence.md)。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的邏輯運算子和位元運算子](logical-and-bitwise-operators.md)
- [數值比較](value-comparisons.md)
- [陳述式](../statements.md)
- [比較運算子](../../../language-reference/operators/comparison-operators.md)
- [有效的運算子組合](efficient-combination-of-operators.md)
- [Visual Basic 中的運算子優先順序](../../../language-reference/operators/operator-precedence.md)
- [Boolean 資料類型](../../../language-reference/data-types/boolean-data-type.md)
