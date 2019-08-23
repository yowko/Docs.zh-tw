---
title: = 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: d260dffb7175e9dddcbf9acb75415f5f973727e2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962008"
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
 任何常值、常數或運算式。  
  
## <a name="remarks"></a>備註  
 等號 (`=`) 左邊的元素可以是簡單的純量變數、屬性或陣列的元素。 變數或屬性不可為[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。 `=`運算子會將其右邊的值指派給其左邊的變數或屬性。  
  
> [!NOTE]
> `=`運算子也會用來做為比較運算子。 如需詳細資訊, 請參閱[比較運算子](../../../visual-basic/language-reference/operators/comparison-operators.md)。  
  
## <a name="overloading"></a>多載化  
 `=`運算子只能多載為關聯式比較運算子, 而不是指派運算子。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例示範指派運算子。 右邊的值會指派給左邊的變數。  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>另請參閱

- [&= 運算子](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [*= 運算子](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [+= 運算子](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [-= 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [/= 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [\\= 運算子](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [^= 運算子](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)
- [比較運算子](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [區域類型推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
