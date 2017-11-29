---
title: "有效的運算子組合 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4b0f1d637bc1757515cf271a8c70d62effab0843
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="efficient-combination-of-operators-visual-basic"></a>有效的運算子組合 (Visual Basic)
複雜運算式可包含許多不同的運算子。 下列範例將說明這點。  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 建立複雜的運算式，例如上述範例中的一個需要瞭解的運算子優先順序的規則。 如需詳細資訊，請參閱[Visual Basic 中的運算子優先順序](../../../../visual-basic/language-reference/operators/operator-precedence.md)。  
  
## <a name="parenthetical-expressions"></a>括號運算式  
 通常您會想從運算子優先順序所決定以不同順序繼續進行作業。 請參考下列範例。  
  
 `x = z * y + 4`  
  
 上述範例會乘以`z`由`y`，然後將結果以`4`。 但是，如果您想要新增`y`和`4`之前相乘的結果`z`，您可以使用括號覆寫一般運算子優先順序。 您可以以括弧括住運算式，強制該運算式要評估第一次，不論運算子優先順序。 若要強制執行加法上述的範例，您無法將它改寫下列範例所示。  
  
 `x = z * (y + 4)`  
  
 前述範例新增`y`和`4`，然後乘以相加的`z`。  
  
### <a name="nested-parenthetical-expressions"></a>巢狀括號運算式  
 您可以巢狀括號來覆寫優先順序更進一步的多個層級中的運算式。 最深的巢狀括號括住的運算式會先評估，接著是巢狀最深處，依此類推，最深的巢狀，最後括號外的運算式。 下列範例將說明這點。  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 在上述範例中，`z + 2`會先評估，然後放在括號運算式。 在此範例中，因為其他運算式會以括號括住乘冪，通常具有較高的優先順序高於加法或乘法，是上一次評估。  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Basic 中的算術運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [在 Visual Basic 中的比較運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [在 Visual Basic 中的邏輯和位元運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [邏輯/位元運算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [布林運算式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [數值比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [如何：計算數值](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)  
 [Visual Basic 中的運算子優先順序](../../../../visual-basic/language-reference/operators/operator-precedence.md)
