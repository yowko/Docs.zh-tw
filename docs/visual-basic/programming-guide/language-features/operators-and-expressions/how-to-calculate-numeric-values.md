---
title: 如何：計算數值
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
ms.openlocfilehash: d213f6b5a4abf8c52d8872ae36e89796183ff27c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348960"
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a>如何：計算數值 (Visual Basic)
您可以透過使用數值運算式來計算數值。 *數值運算式*是一個運算式，其中包含代表數值的常值、常數和變數，以及作用於那些值的運算子。  
  
## <a name="calculating-numeric-values"></a>計算數值  
  
#### <a name="to-calculate-a-numeric-value"></a>計算數值  
  
- 將一個或多個數值常值、常數和變數結合成數值運算式。 下列範例顯示一些有效的數值運算式。  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     前三行顯示常值、常數和變數。 每一個都會單獨形成有效的數值運算式。 最後一行顯示具有兩個常值之變數的組合。  
  
     請注意，數值運算式本身並不會形成完整的 Visual Basic 語句。 您必須使用運算式做為完整語句的一部分。  
  
#### <a name="to-store-a-numeric-value"></a>若要儲存數值  
  
- 您可以使用指派語句，將數值運算式所表示的值指派給變數，如下列範例所示。  
  
     [!code-vb[VbVbalrOperators#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#82)]  
  
     在上述範例中，等號運算子（`=`）右側的運算式值會指派給運算子左邊的變數 `j`，因此 `j` 會評估為276。  
  
     如需詳細資訊，請參閱[陳述式](../../../../visual-basic/language-reference/statements/index.md)。  
  
## <a name="multiple-operators"></a>多個運算子  
 如果數值運算式包含多個運算子，則評估它們的順序是由運算子優先順序的規則所決定。 若要覆寫運算子優先順序的規則，請將運算式括在括弧中，如上述範例所示：會先評估括住的運算式。  
  
#### <a name="to-override-normal-operator-precedence"></a>若要覆寫一般運算子優先順序  
  
- 使用括弧括住您想要先執行的作業。 下列範例顯示兩個具有相同運算元和運算子的不同結果。  
  
     [!code-vb[VbVbalrOperators#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#83)]  
  
     在上述範例中，`j` 的計算會先執行加法運算子（`+`），因為 `(67 + i)` 覆寫一般優先順序，而指派給 `j` 的值是276（4倍69）。 `k` 的計算會以其一般優先順序（`*` 前 `+`）執行運算子，而指派給 `k` 的值為270（268加2）。  
  
     如需詳細資訊，請參閱[Visual Basic 中的運算子優先順序](../../../../visual-basic/language-reference/operators/operator-precedence.md)。  
  
## <a name="see-also"></a>請參閱

- [運算子和運算式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [數值比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [陳述式](../../../../visual-basic/language-reference/statements/index.md)
- [Visual Basic 中的運算子優先順序](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [算術運算子](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [有效的運算子組合](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
