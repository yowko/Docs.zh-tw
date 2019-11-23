---
title: '>>= 運算子'
ms.date: 07/20/2015
f1_keywords:
- vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
ms.openlocfilehash: cad021c7730782d6233c60841483df7173308dc1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352000"
---
# <a name="-operator-visual-basic"></a>>>= Operator (Visual Basic)
Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.  
  
## <a name="syntax"></a>語法  
  
```vb  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a>組件  
 `variableorproperty`  
 必要項。 Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).  
  
 `amount`  
 必要項。 Numeric expression of a data type that widens to `Integer`.  
  
## <a name="remarks"></a>備註  
 The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array. The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 The `>>=` operator first performs an arithmetic right shift on the value of the variable or property. The operator then assigns the result of that operation back to the variable or property.  
  
 Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end. In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left. This means that if `variableorproperty` has a negative value, the vacated positions are set to one. If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.  
  
## <a name="overloading"></a>多載化  
 The [>> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure. Overloading the `>>` operator affects the behavior of the `>>=` operator. If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior. 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>請參閱

- [>> 運算子](../../../visual-basic/language-reference/operators/right-shift-operator.md)
- [指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [位元移位運算子](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)
