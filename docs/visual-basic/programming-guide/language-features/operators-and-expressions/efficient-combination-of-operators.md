---
title: 有效的運算子組合
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
ms.openlocfilehash: 83ad53e4c75490a75eba0f80a6bf0f078aa4d426
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348975"
---
# <a name="efficient-combination-of-operators-visual-basic"></a>有效的運算子組合 (Visual Basic)
複雜運算式可以包含許多不同的運算子。 說明如下例。  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 在上述範例中建立複雜運算式，需要徹底瞭解運算子優先順序的規則。 如需詳細資訊，請參閱[Visual Basic 中的運算子優先順序](../../../../visual-basic/language-reference/operators/operator-precedence.md)。  
  
## <a name="parenthetical-expressions"></a>括號運算式  
 您通常會想要以不同于運算子優先順序的順序來繼續作業。 請參考下列範例。  
  
 `x = z * y + 4`  
  
 上述範例會 `y`將 `z` 相乘，然後將結果新增至 `4`。 但是，如果您想要加入 `y` 並 `4`，然後再將結果乘以 `z`，您可以使用括弧來覆寫正常的運算子優先順序。 藉由將運算式括在括弧中，您會強制先評估該運算式，而不論運算子優先順序為何。 若要強制前面的範例先執行加法，您可以重寫它，如下列範例所示。  
  
 `x = z * (y + 4)`  
  
 上述範例會新增 `y` 和 `4`，然後將該總和乘以 `z`。  
  
### <a name="nested-parenthetical-expressions"></a>嵌套的括號運算式  
 您可以在多個括弧層級中嵌套運算式，以便更進一步覆寫優先順序。 最深嵌套在括弧中的運算式會先進行評估，然後再進行下一個最深的嵌套，依此類推，最後再加上最小的嵌套，最後再加上括弧以外的運算式。 說明如下例。  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 在上述範例中，會先評估 `z + 2`，然後再評估其他的括號運算式。 乘冪（通常具有高於加法或乘法的優先順序）會在此範例中最後評估，因為其他運算式會括在括弧中。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的算術運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Visual Basic 中的比較運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic 中的邏輯和位運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [邏輯/位運算子（Visual Basic）](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [布林運算式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [數值比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [如何：計算數值](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [Visual Basic 中的運算子優先順序](../../../../visual-basic/language-reference/operators/operator-precedence.md)
