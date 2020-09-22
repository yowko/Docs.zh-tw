---
title: = 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: eccea0b43564a4980778c9d1a5b8f9a8c2a9207d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874824"
---
# <a name="-operator-visual-basic"></a>= 運算子 (Visual Basic)

指派值給變數或屬性。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
variableorproperty = value  
```  
  
## <a name="parts"></a>組件  

 `variableorproperty`  
 任何可寫入的變數或任何屬性。  
  
 `value`  
 任何常值、常數或運算式。  
  
## <a name="remarks"></a>備註  

 等號 () 左邊的元素 `=` 可以是簡單的純量變數、屬性或陣列的元素。 變數或屬性不可以是 [ReadOnly](../modifiers/readonly.md)。 運算子會將 `=` 其右邊的值指派給左邊的變數或屬性。  
  
> [!NOTE]
> `=`運算子也可用來做為比較運算子。 如需詳細資訊，請參閱 [比較運算子](comparison-operators.md)。  
  
## <a name="overloading"></a>多載化  

 `=`運算子只能以關聯式比較運算子的方式多載，而不能以指派運算子的方式多載。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  

 下列範例示範指派運算子。 右邊的值會指派給左邊的變數。  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>另請參閱

- [&= 運算子](and-assignment-operator.md)
- [* = 運算子](multiplication-assignment-operator.md)
- [+ = 運算子](addition-assignment-operator.md)
- [-= 運算子 (Visual Basic) ](subtraction-assignment-operator.md)
- [/= 運算子 (Visual Basic) ](floating-point-division-assignment-operator.md)
- [\\= 運算子](integer-division-assignment-operator.md)
- [^ = 運算子](exponentiation-assignment-operator.md)
- [陳述式](../../programming-guide/language-features/statements.md)
- [比較運算子](comparison-operators.md)
- [ReadOnly](../modifiers/readonly.md)
- [區域型別推斷](../../programming-guide/language-features/variables/local-type-inference.md)
