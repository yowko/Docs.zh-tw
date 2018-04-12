---
title: /= 運算子 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 94448856072a949582e64577287134c4b975bfec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a>/= 運算子 (Visual Basic)
將運算式的值的變數或屬性的值除以和浮點結果指派給變數或屬性。  
  
## <a name="syntax"></a>語法  
  
```  
variableorproperty /= expression  
```  
  
## <a name="parts"></a>組件  
 `variableorproperty`  
 必要項。 任何數值變數或屬性。  
  
 `expression`  
 必要項。 任何數值運算式。  
  
## <a name="remarks"></a>備註  
 在左邊的項目`/=`運算子可以是簡單的純量變數、 屬性或陣列的項目。 變數或屬性不可[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。  
  
 `/=`運算子先除以變數或屬性 （在運算子的左側） 的值 （在運算子右手邊） 運算式的值。 然後，運算子會將浮點運算的結果指派給變數或屬性。  
  
 此陳述式會指派`Double`變數或屬性左邊的值。 如果`Option Strict`是`On`，`variableorproperty`必須`Double`。 如果`Option Strict`是`Off`，Visual Basic 執行的隱含轉換，並將結果指派至`variableorproperty`，可能在執行階段錯誤。 如需詳細資訊，請參閱[擴大和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)和[Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)。  
  
## <a name="overloading"></a>多載化  
 [/ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)可以*多載*，這表示，類別或結構可以重新定義它的行為時的運算元有該類別或結構的類型。 多載`/`運算子會影響行為`/=`運算子。 如果您的程式碼使用`/=`上類別或結構的多載`/`，確定您了解其重新定義的行為。 如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`/=`將其中一個運算子`Integer`變數的第二個和指派給第一個變數的商數。  
  
 [!code-vb[VbVbalrOperators#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [/ 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)  
 [\\= 運算子](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)
