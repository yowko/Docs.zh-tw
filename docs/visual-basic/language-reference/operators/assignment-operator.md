---
title: = 運算子 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 230005640b2b494e5413b14ba13a7cb82ee9f22b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a>= 運算子 (Visual Basic)
將值指派給變數或屬性。  
  
## <a name="syntax"></a>語法  
  
```  
variableorproperty = value  
```  
  
## <a name="parts"></a>組件  
 `variableorproperty`  
 任何可寫入的變數或任何屬性。  
  
 `value`  
 任何常值、 常數或運算式。  
  
## <a name="remarks"></a>備註  
 等號左邊的項目 (`=`) 可以是簡單的純量變數、 屬性或陣列的項目。 變數或屬性不可[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。 `=`運算子會將指派其權限給變數的值或與其左邊的屬性。  
  
> [!NOTE]
>  `=`運算子也可以用做為比較運算子。 如需詳細資訊，請參閱[比較運算子](../../../visual-basic/language-reference/operators/comparison-operators.md)。  
  
## <a name="overloading"></a>多載化  
 `=`運算子可以多載，只為關係比較運算子，而不指派運算子。 如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何指派運算子。 在右邊的值指派給左邊的變數。  
  
 [!code-vb[VbVbalrOperators#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/assignment-operator_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [&= 運算子](../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [*= 運算子](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)  
 [+= 運算子](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
 [-= 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)  
 [/ = 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [\\= 運算子](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [^= 運算子](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)  
 [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)  
 [比較運算子](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)  
 [區域類型推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
