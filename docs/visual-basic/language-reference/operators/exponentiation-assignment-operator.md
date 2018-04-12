---
title: ^= 運算子 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fa9d87d2f090a8c18aaab742e73878c7b80f55c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a>^= 運算子 (Visual Basic)
引發的變數或運算式的乘冪的屬性值，並將結果指派給變數或屬性。  
  
## <a name="syntax"></a>語法  
  
```  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a>組件  
 `variableorproperty`  
 必要項。 任何數值變數或屬性。  
  
 `expression`  
 必要項。 任何數值運算式。  
  
## <a name="remarks"></a>備註  
 在左邊的項目`^=`運算子可以是簡單的純量變數、 屬性或陣列的項目。 變數或屬性不可[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。  
  
 `^=`運算子第一次引發變數或屬性 （在運算子的左側） 的值 （在運算子右手邊） 運算式的值乘冪。 然後，運算子會將該作業的結果指派給變數或屬性。  
  
 Visual Basic 一律會執行中的乘冪[Double 資料類型](../../../visual-basic/language-reference/data-types/double-data-type.md)。 任何其他類型的運算元都轉換成`Double`，而且結果一律`Double`。  
  
 值`expression`可以是分數，負數，或兩者。  
  
## <a name="overloading"></a>多載化  
 [^ 運算子](../../../visual-basic/language-reference/operators/exponentiation-operator.md)可以*多載*，這表示，類別或結構可以重新定義它的行為時的運算元有該類別或結構的類型。 多載`^`運算子會影響行為`^=`運算子。 如果您的程式碼使用`^=`上類別或結構的多載`^`，確定您了解其重新定義的行為。 如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`^=`運算子引發其中一個值`Integer`變數的第二個變數並指派給第一個變數的結果。  
  
 [!code-vb[VbVbalrOperators#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [^ 運算子](../../../visual-basic/language-reference/operators/exponentiation-operator.md)  
 [指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)
