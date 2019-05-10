---
title: Visual Basic 中的運算子和運算式
ms.date: 07/20/2015
helpviewer_keywords:
- operators [Visual Basic], operands
- operators [Visual Basic]
- operands [Visual Basic], definition
- Visual Basic code, operators
- Visual Basic code, expressions
- operands
- expressions [Visual Basic]
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
ms.openlocfilehash: 40d71c5231b8d278f4ca8d9352e6e3cba5104f9b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649700"
---
# <a name="operators-and-expressions-in-visual-basic"></a>Visual Basic 中的運算子和運算式
「運算子」是一種程式碼項目，可對保留值的一或多個程式碼項目執行運算。 值項目包含 `Function` 與 `Operator` 程序和運算式的變數、常數、常值、屬性、傳回值。  
  
 「運算式」是一系列與運算子合併的值項目，可產生新的值。 運算子透過執行計算、比較或其他作業來當成值項目。  
  
## <a name="types-of-operators"></a>運算子類型  
 Visual Basic 提供下列類型的運算子：  
  
- [算術運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)可對數值執行類似的計算，包括移位其位元模式。  
  
- [比較運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)可比較兩個運算式，並傳回代表比較結果的 `Boolean` 值。  
  
- [串連運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)可將多個字串連成單一字串。  
  
- [Visual Basic 中的邏輯運算子和位元運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)可合併 `Boolean` 或數值，並傳回與值相同之資料類型的結果。  
  
 與運算子合併使用的值項目稱為該運算子的「運算元」。 與值項目合併使用的運算子可形成運算式，但不含可形成「陳述式」的指派運算子。 如需詳細資訊，請參閱[陳述式](../../../../visual-basic/programming-guide/language-features/statements.md)。  
  
## <a name="evaluation-of-expressions"></a>運算式評估  
 運算式的最終結果代表值，通常是熟悉的資料類型，例如 `Boolean`、`String` 或數值類型。  
  
 下列是運算式範例。  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 數個運算子可以在單一運算式或陳述式中執行動作，如下列範例所示。  
  
 [!code-vb[VbVbalrOperators#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#56)]  
  
 在上述範例中，Visual Basic，請執行指派運算子右邊的運算式中的作業 (`=`)，然後將產生的值指派給變數`x`左側。 可合併到運算式的運算子數目沒有實際限制，但需要了解 [Visual Basic 中的運算子優先順序](../../../../visual-basic/language-reference/operators/operator-precedence.md)，才能確保您取得所要的結果。  

## <a name="see-also"></a>另請參閱

- [運算子](../../../../visual-basic/language-reference/operators/index.md)
- [有效的運算子組合](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
- [陳述式](../../../../visual-basic/language-reference/statements/index.md)
