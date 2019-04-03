---
title: 有效的運算子組合 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- expressions [Visual Basic], parentheses
- operators [Visual Basic], associativity
- expressions [Visual Basic], operators
- operators [Visual Basic], precedence
- Visual Basic code, operators
- Visual Basic code, expressions
- operators [Visual Basic], complex expressions
- expressions [Visual Basic], complex
- parentheses [Visual Basic], complex expressions
- numeric expressions
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
ms.openlocfilehash: 8f5dd6c56b3e4576b9d798e0e5e10b2996f558dc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841237"
---
# <a name="efficient-combination-of-operators-visual-basic"></a>有效的運算子組合 (Visual Basic)
複雜運算式可以包含許多不同的運算子。 下列範例將說明這點。  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 建立複雜的運算式，例如上述範例中的一個需要徹底了解運算子優先順序的規則。 如需詳細資訊，請參閱 < [Visual Basic 中的運算子優先順序](../../../../visual-basic/language-reference/operators/operator-precedence.md)。  
  
## <a name="parenthetical-expressions"></a>括號運算式  
 通常您會想作業繼續進行中的運算子優先順序所決定的順序不同。 請參考下列範例。  
  
 `x = z * y + 4`  
  
 上述範例會乘以`z`所`y`，然後將結果`4`。 但是，如果您想要新增`y`並`4`相乘的結果之前`z`，您可以使用括號覆寫正常的運算子優先順序。 您可以以括弧括住的運算式，強制該運算式先受到評估，無論運算子優先順序。 若要強制執行加法上述的範例，您可以將它改寫如下列範例所示。  
  
 `x = z * (y + 4)`  
  
 上述範例中新增`y`並`4`，然後乘以藉由加總`z`。  
  
### <a name="nested-parenthetical-expressions"></a>巢狀放在括號運算式  
 您可以巢狀括號來覆寫優先順序更進一步的多個層級中的運算式。 最深的巢狀括號括住的運算式會先評估，後面接著巢狀最深處，依此類推到最深的巢狀，而最後運算式括號外的下一步。 下列範例將說明這點。  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 在上述範例中，`z + 2`會先評估，然後放在括號運算式。 在此範例中，因為其他運算式括在括號中乘冪，通常具有較高的優先順序高於加法或乘法，是上一次評估。  
  
## <a name="see-also"></a>另請參閱

- [在 Visual Basic 中的算術運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [在 Visual Basic 中的比較運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [在 Visual Basic 中的邏輯和位元運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [邏輯/位元運算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [布林運算式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [數值比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [如何：計算數值](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [Visual Basic 中的運算子優先順序](../../../../visual-basic/language-reference/operators/operator-precedence.md)
