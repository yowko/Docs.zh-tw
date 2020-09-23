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
ms.openlocfilehash: 9ba6be8e1dd03c0589f712b0e9b39258953cd223
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077081"
---
# <a name="efficient-combination-of-operators-visual-basic"></a>有效的運算子組合 (Visual Basic)

複雜運算式可包含許多不同的運算子。 下列範例將說明這點。  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 若要建立複雜的運算式（例如上述範例中的運算式），必須徹底瞭解運算子優先順序的規則。 如需詳細資訊，請參閱 [Visual Basic 中的運算子優先順序](../../../language-reference/operators/operator-precedence.md)。  
  
## <a name="parenthetical-expressions"></a>括號運算式  

 通常您會想要以運算子優先順序所決定的不同順序來繼續執行作業。 請思考一下下列範例。  
  
 `x = z * y + 4`  
  
 上述範例會乘以 `z` `y` ，然後將結果加入至 `4` 。 但是，如果您想要在將 `y` `4` 結果相乘之前加入 `z` ，則可以使用括弧覆寫一般運算子優先順序。 藉由將運算式括在括弧中，您就可以強制先評估運算式，而不考慮運算子優先順序。 若要強制上述範例先執行加法，您可以如下列範例所示重寫它。  
  
 `x = z * (y + 4)`  
  
 上述範例會新增 `y` 和 `4` ，然後將該總和乘以 `z` 。  
  
### <a name="nested-parenthetical-expressions"></a>嵌套括號運算式  

 您可以在多個括弧層級中嵌套運算式，更進一步覆寫優先順序。 最深層嵌套在括弧中的運算式會先進行評估，然後再以最深的嵌套方式進行評估，最後再進行最深的嵌套，最後是括弧外的運算式。 下列範例將說明這點。  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 在上述範例中， `z + 2` 會先評估另一個括號運算式。 通常優先順序高於加法或乘法的乘冪會在此範例中最後評估，因為其他運算式會以括弧括住。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 的算術運算子](arithmetic-operators.md)
- [Comparison Operators in Visual Basic](comparison-operators.md)
- [Visual Basic 中的邏輯運算子和位元運算子](logical-and-bitwise-operators.md)
- [邏輯/位元運算子 (Visual Basic)](../../../language-reference/operators/logical-bitwise-operators.md)
- [布林運算式](boolean-expressions.md)
- [數值比較](value-comparisons.md)
- [如何：計算數值](how-to-calculate-numeric-values.md)
- [Visual Basic 中的運算子優先順序](../../../language-reference/operators/operator-precedence.md)
