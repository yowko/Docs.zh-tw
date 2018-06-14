---
title: '&amp;= 運算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
ms.openlocfilehash: c3db2d4095600f32af92d1a4ce1f806a3f032af0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33601877"
---
# <a name="amp-operator-visual-basic"></a>&amp;= 運算子 (Visual Basic)
串連`String`運算式`String`變數或屬性，並將結果指派給變數或屬性。  
  
## <a name="syntax"></a>語法  
  
```  
variableorproperty &= expression  
```  
  
## <a name="parts"></a>組件  
 `variableorproperty`  
 必要。 任何`String`變數或屬性。  
  
 `expression`  
 必要。 任何 `String` 運算式。  
  
## <a name="remarks"></a>備註  
 在左邊的項目`&=`運算子可以是簡單的純量變數、 屬性或陣列的項目。 變數或屬性不可[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。 `&=`運算子串連`String`運算式右邊`String`變數或屬性與其左邊，並將結果指派給變數或屬性與其左邊。  
  
## <a name="overloading"></a>多載化  
 [& 運算子](../../../visual-basic/language-reference/operators/concatenation-operator.md)可以*多載*，這表示，類別或結構可以重新定義它的行為時的運算元有該類別或結構的類型。 多載`&`運算子會影響行為`&=`運算子。 如果您的程式碼使用`&=`上類別或結構的多載`&`，確定您了解其重新定義的行為。 如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`&=`運算子來串連兩個`String`變數並指派給第一個變數的結果。  
  
 [!code-vb[VbVbalrOperators#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [& 運算子](../../../visual-basic/language-reference/operators/concatenation-operator.md)  
 [+= 運算子](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
 [指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [串連運算子](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)
