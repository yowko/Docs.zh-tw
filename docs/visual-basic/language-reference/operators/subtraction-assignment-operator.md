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
ms.openlocfilehash: be1ff4f10f6b30d8448d2441ee3ad2c1e2f80e2d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58815897"
---
# <a name="--operator-visual-basic"></a>-= 運算子 (Visual Basic)
減去運算式的值的變數或屬性的值，然後將結果指派給變數或屬性。  
  
## <a name="syntax"></a>語法  
  
```  
variableorproperty -= expression  
```  
  
## <a name="parts"></a>組件  
 `variableorproperty`  
 必要項。 任何數值變數或屬性。  
  
 `expression`  
 必要項。 任何數值運算式。  
  
## <a name="remarks"></a>備註  
 在左邊的項目`-=`運算子可以是簡單的純量變數、 屬性或陣列項目。 變數或屬性不可[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。  
  
 `-=`第一次從變數或屬性 （在運算子的左側） 的值減去 （在運算子右手邊） 運算式的值的運算子。 然後，運算子會將該作業的結果指派給變數或屬性。  
  
## <a name="overloading"></a>多載化  
 [-運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md)可以是*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。 多載`-`運算子會影響的行為`-=`運算子。 如果您的程式碼會使用`-=`上類別或結構，多載`-`，務必了解其重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`-=`減一的運算子`Integer`從另一個變數並指派結果對應到第二個變數。  
  
 [!code-vb[VbVbalrOperators#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>另請參閱

- [-運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md)
- [指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)
