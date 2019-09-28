---
title: /= 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
ms.openlocfilehash: b4855e8270a329f9345339060a323b5ca9cd9792
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592180"
---
# <a name="-operator-visual-basic"></a>/= 運算子 (Visual Basic)
將變數或屬性的值除以運算式的值，並將浮點結果指派給變數或屬性。  
  
## <a name="syntax"></a>語法  
  
```vb  
variableorproperty /= expression  
```  
  
## <a name="parts"></a>組件  
 `variableorproperty`  
 必要項。 任何數值變數或屬性。  
  
 `expression`  
 必要項。 任何數值運算式。  
  
## <a name="remarks"></a>備註  
 @No__t-0 運算子左邊的元素可以是簡單的純量變數、屬性或陣列的元素。 變數或屬性不可為[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。  
  
 @No__t-0 運算子會先將變數或屬性的值（位於運算子的左邊）除以運算式的值（在運算子的右邊），然後再將它隔開。 然後，運算子會將該運算的浮點結果指派給變數或屬性。  
  
 這個語句會將 `Double` 值指派給左邊的變數或屬性。 如果 `Option Strict` 是 `On`，`variableorproperty` 必須是 `Double`。 如果 `Option Strict` 是 `Off`，Visual Basic 會執行隱含轉換，並將產生的值指派給 `variableorproperty`，並在執行時間發生可能的錯誤。 如需詳細資訊，請參閱[擴展和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)和[Option Strict 語句](../../../visual-basic/language-reference/statements/option-strict-statement.md)。  
  
## <a name="overloading"></a>多載化  
 [/運算子（Visual Basic）](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)可以多載 *，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。 多載 `/` 運算子會影響 `/=` 運算子的行為。 如果您的程式碼在多載 `/` 的類別或結構上使用 `/=`，請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用 `/=` 運算子，將一個 @no__t 1 變數除以一秒，並將該商指派給第一個變數。  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>另請參閱

- [/運算子（Visual Basic）](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [\\ = 運算子](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)
