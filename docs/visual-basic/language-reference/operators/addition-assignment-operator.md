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
ms.openlocfilehash: f12a0560d984f871110c02f1df2c2ec42b68809b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-visual-basic"></a>+= 運算子 (Visual Basic)
將數值變數或屬性的值加上數值運算式的值，並將結果指派給變數或屬性。 也可用來串連`String`運算式`String`變數或屬性並指派結果給變數或屬性。  
  
## <a name="syntax"></a>語法  
  
```  
variableorproperty += expression  
```  
  
## <a name="parts"></a>組件  
 `variableorproperty`  
 必要。 任何數值或`String`變數或屬性。  
  
 `expression`  
 必要。 任何數值或`String`運算式。  
  
## <a name="remarks"></a>備註  
 在左邊的項目`+=`運算子可以是簡單的純量變數、 屬性或陣列的項目。 變數或屬性不可[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。  
  
 `+=`運算子將值加入至變數或屬性與其左邊，右邊，並將結果指派給變數或屬性與其左邊。 `+=`運算子也可用來串連`String`運算式右邊`String`變數，或在其左邊，並指派結果給變數的屬性或與其左邊的屬性。  
  
> [!NOTE]
>  當您使用`+=`運算子，可能無法判斷發生加法或字串串連。 使用`&=`運算子串連避免模稜兩可，以及提供自我記錄程式碼。  
  
 此指派運算子隱含執行擴展但未縮小轉換，如果編譯環境強制執行嚴格的語意。 如需有關這些轉換的詳細資訊，請參閱[擴大和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。 Strict 及寬鬆語意的詳細資訊，請參閱[Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)。  
  
 如果允許寬鬆的語意，`+=`運算子隱含地執行各種字串和數值轉換所執行的相同`+`運算子。 如需這些轉換的詳細資訊，請參閱[+ 運算子](../../../visual-basic/language-reference/operators/addition-operator.md)。  
  
## <a name="overloading"></a>多載化  
 `+`運算子可以是*多載*，這表示，類別或結構可以重新定義它的行為時的運算元有該類別或結構的類型。 多載`+`運算子會影響行為`+=`運算子。 如果您的程式碼使用`+=`上類別或結構的多載`+`，確定您了解其重新定義的行為。 如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`+=`運算子以結合以另一個變數的值。 第一個部分使用`+=`數值變數來加入到另一個值。 第二個部分會使用`+=`與`String`来串連的一個值與另一個變數。 在這兩種情況下，結果會指派給第一個變數。  
  
 [!code-vb[VbVbalrOperators#7](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_1.vb)]  
  
 [!code-vb[VbVbalrOperators#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_2.vb)]  
  
 值`num1`13 和的值現在是`str1`現在是"103"。  
  
## <a name="see-also"></a>另請參閱  
 [+ 運算子](../../../visual-basic/language-reference/operators/addition-operator.md)  
 [指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [串連運算子](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)
