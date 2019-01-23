---
title: += 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
ms.openlocfilehash: cfe987929099fc73ba3af9fe92b5871275c5396e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617547"
---
# <a name="-operator-visual-basic"></a>+= 運算子 (Visual Basic)
將數值變數或屬性的值加上數值運算式的值，並將結果指派給變數或屬性。 也可以用來串連`String`運算式`String`變數或屬性，而指派給變數或屬性的結果。  
  
## <a name="syntax"></a>語法  
  
```  
variableorproperty += expression  
```  
  
## <a name="parts"></a>組件  
 `variableorproperty`  
 必要項。 任何數值或`String`變數或屬性。  
  
 `expression`  
 必要項。 任何數值或`String`運算式。  
  
## <a name="remarks"></a>備註  
 在左邊的項目`+=`運算子可以是簡單的純量變數、 屬性或陣列項目。 變數或屬性不可[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。  
  
 `+=`運算子會將值加入至變數或屬性與其左邊，右邊，並將結果指派給變數或與其左邊的屬性。 `+=`運算子也可用來串連`String`權限來運算式`String`變數，或在其左側，並指派結果給變數的屬性或與其左邊的屬性。  
  
> [!NOTE]
>  當您使用`+=`運算子，可能無法判斷是否會發生加法或字串的串連。 使用`&=`運算子串連消除模稜兩可，並提供自我記錄程式碼。  
  
 此指派運算子會隱含地執行擴展但未縮小轉換，如果編譯環境強制執行嚴格的語意。 如需有關這些轉換的詳細資訊，請參閱 < [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。 如需有關嚴格和寬鬆語意的詳細資訊，請參閱[Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)。  
  
 如果您允許寬鬆的語意，`+=`運算子會隱含地執行於所執行相同的字串和數值轉換各種`+`運算子。 如需這些轉換的詳細資訊，請參閱[+ 運算子](../../../visual-basic/language-reference/operators/addition-operator.md)。  
  
## <a name="overloading"></a>多載化  
 `+`運算子只能*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。 多載`+`運算子會影響的行為`+=`運算子。 如果您的程式碼會使用`+=`上類別或結構，多載`+`，務必了解其重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`+=`運算子以結合一個變數的值與另一個。 第一個部分使用`+=`與數值的變數，以加入另一個值。 第二個部分會使用`+=`與`String`串連以另一個值的變數。 在這兩種情況下，結果會指派給第一個變數。  
  
 [!code-vb[VbVbalrOperators#7](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_1.vb)]  
  
 [!code-vb[VbVbalrOperators#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_2.vb)]  
  
 值`num1`13 和的值現在是`str1`現在是"103"。  
  
## <a name="see-also"></a>另請參閱
- [+ 運算子](../../../visual-basic/language-reference/operators/addition-operator.md)
- [指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [串連運算子](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)
