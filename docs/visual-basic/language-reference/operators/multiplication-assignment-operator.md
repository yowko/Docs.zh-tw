---
title: '*= 運算子 (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.*=
helpviewer_keywords:
- operator *=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '*= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 96c86509-6eb8-4682-8226-3852e049376f
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d0a2c638f3faaf20fadb745ef437941ee29d4f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a>*= 運算子 (Visual Basic)
將變數或屬性的值，乘以運算式的值，並將結果指派給變數或屬性。  
  
## <a name="syntax"></a>語法  
  
```  
variableorproperty *= expression  
```  
  
## <a name="parts"></a>組件  
 `variableorproperty`  
 必要項。 任何數值變數或屬性。  
  
 `expression`  
 必要項。 任何數值運算式。  
  
## <a name="remarks"></a>備註  
 在左邊的項目`*=`運算子可以是簡單的純量變數、 屬性或陣列的項目。 變數或屬性不可[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。  
  
 `*=`運算子先乘以 （在運算子右手邊） 運算式的值的變數或屬性 （在運算子的左側） 的值。 然後，運算子會將該作業的結果指派給變數或屬性。  
  
## <a name="overloading"></a>多載化  
 [* 運算子](../../../visual-basic/language-reference/operators/multiplication-operator.md)可以*多載*，這表示，類別或結構可以重新定義它的行為時的運算元有該類別或結構的類型。 多載`*`運算子會影響行為`*=`運算子。 如果您的程式碼使用`*=`上類別或結構的多載`*`，確定您了解其重新定義的行為。 如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`*=`要相乘的其中一個運算子`Integer`變數的第二個和指派給第一個變數的結果。  
  
 [!code-vb[VbVbalrOperators#5](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/multiplication-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [* 運算子](../../../visual-basic/language-reference/operators/multiplication-operator.md)  
 [指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)
