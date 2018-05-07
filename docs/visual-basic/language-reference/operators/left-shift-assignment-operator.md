---
title: '&lt;&lt;= 運算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.<<=
helpviewer_keywords:
- operator <<=
- assignment statements [Visual Basic], compound
- <<= operator [Visual Basic]
- statements [Visual Basic], compound assignment
- operator<<=
- compound assignment statements [Visual Basic]
ms.assetid: 8ad26613-faff-4e2f-89ee-63feee33bfda
ms.openlocfilehash: 559624f7097f90d374ee83e3c0a9ac97d9f93444
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ltlt-operator-visual-basic"></a>&lt;&lt;= 運算子 (Visual Basic)
變數或屬性的值上執行算術左的移位並將結果指派給變數或屬性。  
  
## <a name="syntax"></a>語法  
  
```  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a>組件  
 `variableorproperty`  
 必要。 變數或屬性的整數類型 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`，或`ULong`)。  
  
 `amount`  
 必要。 數值運算式的資料類型可擴展成`Integer`。  
  
## <a name="remarks"></a>備註  
 在左邊的項目`<<=`運算子可以是簡單的純量變數、 屬性或陣列的項目。 變數或屬性不可[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。  
  
 `<<=`運算子會先執行算術左的移位的變數或屬性的值。 然後，運算子會將該作業的結果指派給該變數或屬性。  
  
 算術排班不是循環，這表示移出結果的一個 end 的位元會重新引入的另一端。 在算術左移位，移位超出結果資料類型之範圍的位元會捨棄，而且右方空出的位元位置會設定為零。  
  
## <a name="overloading"></a>多載化  
 [<< 運算子](../../../visual-basic/language-reference/operators/left-shift-operator.md)可以*多載*，這表示，類別或結構可以重新定義它的行為時的運算元有該類別或結構的類型。 多載`<<`運算子會影響行為`<<=`運算子。 如果您的程式碼使用`<<=`上類別或結構的多載`<<`，確定您了解其重新定義的行為。 如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`<<=`要移位的位元模式的運算子`Integer`變數向左程式指定的數量並指派結果給變數。  
  
 [!code-vb[VbVbalrOperators#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [<< 運算子](../../../visual-basic/language-reference/operators/left-shift-operator.md)  
 [指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [位元移位運算子](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)
