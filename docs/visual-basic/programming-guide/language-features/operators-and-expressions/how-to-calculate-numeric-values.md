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
ms.openlocfilehash: 452a8392b46f0c25b6ad2a8a30c51071f2ae1d93
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071712"
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a>如何：計算數值 (Visual Basic)

您可以透過使用數值運算式來計算數值。 *數值運算式*是包含常值、常數和變數的運算式，這些變數表示數值，以及處理這些值的運算子。  
  
## <a name="calculating-numeric-values"></a>計算數值  
  
#### <a name="to-calculate-a-numeric-value"></a>計算數值  
  
- 將一或多個數值常值、常數和變數合併為數值運算式。 下列範例顯示一些有效的數值運算式。  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     前三行會顯示常值、常數和變數。 每一個都形成一個有效的數值運算式。 最後一行顯示具有兩個常值之變數的組合。  
  
     請注意，數值運算式本身不會形成完整的 Visual Basic 語句。 您必須使用運算式做為完整語句的一部分。  
  
#### <a name="to-store-a-numeric-value"></a>若要儲存數值  
  
- 您可以使用指派語句，將數值運算式所表示的值指派給變數，如下列範例所示。  
  
     [!code-vb[VbVbalrOperators#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#82)]  
  
     在上述範例中，等號運算子右邊的運算式值 (`=`) 會指派給 `j` 運算子左邊的變數，所以會 `j` 評估為276。  
  
     如需詳細資訊，請參閱[陳述式](../../../language-reference/statements/index.md)。  
  
## <a name="multiple-operators"></a>多個運算子  

 如果數值運算式包含一個以上的運算子，則評估它們的順序是由運算子優先順序的規則來決定。 若要覆寫運算子優先順序的規則，您可以用括弧括住運算式，如上述範例所示：會先評估包含的運算式。  
  
#### <a name="to-override-normal-operator-precedence"></a>覆寫一般運算子優先順序  
  
- 使用括弧來括住您想要先執行的作業。 下列範例顯示兩個具有相同運算元和運算子的不同結果。  
  
     [!code-vb[VbVbalrOperators#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#83)]  
  
     在上述範例中， `j` 會先執行加法運算子 (`+`) ，因為覆 `(67 + i)` 寫一般優先順序的括弧和指派給的值 `j` 為 276 (4 倍 69) 。 在 `k`) 之前，的計算會在其一般優先順序 `*` (`+` ，而指派給的值 `k` 為 270 (268 加 2) 。  
  
     如需詳細資訊，請參閱 [Visual Basic 中的運算子優先順序](../../../language-reference/operators/operator-precedence.md)。  
  
## <a name="see-also"></a>另請參閱

- [運算子和運算式](index.md)
- [數值比較](value-comparisons.md)
- [陳述式](../../../language-reference/statements/index.md)
- [Visual Basic 中的運算子優先順序](../../../language-reference/operators/operator-precedence.md)
- [算術運算子](../../../language-reference/operators/arithmetic-operators.md)
- [有效的運算子組合](efficient-combination-of-operators.md)
