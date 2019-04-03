---
title: HOW TO：計算數值 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- operator precedence
- operators [Visual Basic]
- expressions [Visual Basic], numeric
- calculations [Visual Basic], numeric expressions
- precedence [Visual Basic], of operators
- Visual Basic code, operators
- Visual Basic code, expressions
- numeric expressions
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
ms.openlocfilehash: 33184d9be275f5e777ffd79c6dd4e3182d865de7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825746"
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a>HOW TO：計算數值 (Visual Basic)
您可以計算數字的值，透過使用數值運算式。 A*數值運算式*運算式包含常值、 常數和變數表示數字的值，並處理那些值的運算子。  
  
## <a name="calculating-numeric-values"></a>計算數值  
  
#### <a name="to-calculate-a-numeric-value"></a>若要計算數值的值  
  
-   結合的數值運算式的一或多個數值常值、 常數和變數。 下列範例顯示一些有效的數值運算式。  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     前三行顯示為常值、 常數和變數。 每個本身會形成有效的數值運算式。 最後一行顯示兩個常值的變數的組合。  
  
     請注意數值的運算式不會構成完整的 Visual Basic 陳述式本身。 您必須使用運算式做為完整的陳述式的一部分。  
  
#### <a name="to-store-a-numeric-value"></a>若要儲存的數值  
  
-   若要指派給變數，數值運算式所表示的值，如下列範例所示，您可以使用指派陳述式。  
  
     [!code-vb[VbVbalrOperators#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#82)]  
  
     在上述範例中，「 等於 」 運算子的運算式右邊的值 (`=`) 指派給變數`j`運算子，左邊讓`j`276 評估結果。  
  
     如需詳細資訊，請參閱[陳述式](../../../../visual-basic/language-reference/statements/index.md)。  
  
## <a name="multiple-operators"></a>多個運算子  
 如果數字的運算式包含多個運算子，會評估的順序取決於運算子優先順序的規則。 若要覆寫的運算子優先順序的規則，您的運算式括號括住，如同在上述範例中，會先評估括住的運算式。  
  
#### <a name="to-override-normal-operator-precedence"></a>若要覆寫正常的運算子優先順序  
  
-   您可以使用括號來括住您想要優先執行的作業。 下列範例顯示兩個不同的結果，以相同的運算元和運算子。  
  
     [!code-vb[VbVbalrOperators#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#83)]  
  
     在上述範例中，計算`j`會執行加法運算子 (`+`) 第一個因為前後的括號`(67 + i)`一般優先順序，以及指派給的值會覆寫`j`是 276 (4 次 69)。 計算`k`執行其一般優先順序的運算子 (`*`之前`+`)，並指派給值`k`為 270 （268 加上 2）。  
  
     如需詳細資訊，請參閱 < [Visual Basic 中的運算子優先順序](../../../../visual-basic/language-reference/operators/operator-precedence.md)。  
  
## <a name="see-also"></a>另請參閱

- [運算子和運算式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [數值比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [陳述式](../../../../visual-basic/language-reference/statements/index.md)
- [Visual Basic 中的運算子優先順序](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [算術運算子](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [有效的運算子組合](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
