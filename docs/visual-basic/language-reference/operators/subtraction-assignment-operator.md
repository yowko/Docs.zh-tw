---
title: -= 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.-=
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements [Visual Basic]
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
ms.openlocfilehash: 598fd9db4262d0a33bf0408ebe9455760d5e4506
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="--operator-visual-basic"></a>-= 運算子 (Visual Basic)
減去運算式的值的變數或屬性的值，並將結果指派給變數或屬性。  
  
## <a name="syntax"></a>語法  
  
```  
variableorproperty -= expression  
```  
  
## <a name="parts"></a>組件  
 `variableorproperty`  
 必要。 任何數值變數或屬性。  
  
 `expression`  
 必要。 任何數值運算式。  
  
## <a name="remarks"></a>備註  
 在左邊的項目`-=`運算子可以是簡單的純量變數、 屬性或陣列的項目。 變數或屬性不可[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。  
  
 `-=`運算子先減去 （在運算子右手邊） 運算式的值從變數或屬性 （在運算子的左側） 的值。 然後，運算子會將該作業的結果指派給變數或屬性。  
  
## <a name="overloading"></a>多載化  
 [-運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md)可以*多載*，這表示，類別或結構可以重新定義它的行為時的運算元有該類別或結構的類型。 多載`-`運算子會影響行為`-=`運算子。 如果您的程式碼使用`-=`上類別或結構的多載`-`，確定您了解其重新定義的行為。 如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`-=`減一的運算子`Integer`從另一個變數並指派給第一個變數的結果。  
  
 [!code-vb[VbVbalrOperators#11](codesnippet/VisualBasic/subtraction-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [-運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md)  
 [指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)
