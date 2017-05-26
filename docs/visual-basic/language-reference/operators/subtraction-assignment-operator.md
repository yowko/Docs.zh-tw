---
title: "-= 運算子 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.-=
dev_langs:
- VB
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements, compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f640bd288c677954bae189c2e86ef096e7a73a2b
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="--operator-visual-basic"></a>-= 運算子 (Visual Basic)
減去運算式的值的變數或屬性的值，並將結果指派給變數或屬性。  
  
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
 在左邊的項目`-=`運算子可以是簡單的純量變數、 屬性或陣列的項目。 變數或屬性不能[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。  
  
 `-=`第一次從變數或屬性 （在運算子的左側） 的值減去 （在運算子的右側） 運算式的值的運算子。 然後，運算子會將該作業的結果指派給變數或屬性。  
  
## <a name="overloading"></a>多載化  
 [-運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md)可以是*多載*，也就是說，類別或結構可以重新定義它的行為時運算元具有該類別或結構的型別。 多載`-`運算子會影響的行為`-=`運算子。 如果您的程式碼使用`-=`類別或結構的多載上`-`，確定您了解其重新定義的行為。 如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`-=`減一的運算子`Integer`從另一個變數並指派給第一個變數的結果。  
  
 [!code-vb[VbVbalrOperators #&11;](codesnippet/VisualBasic/subtraction-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [-運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md)   
 [指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [在 Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [依功能排列的運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)

