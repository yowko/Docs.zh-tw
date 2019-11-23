---
title: '*= 運算子'
ms.date: 07/20/2015
f1_keywords:
- vb.*=
helpviewer_keywords:
- operator *=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '*= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 96c86509-6eb8-4682-8226-3852e049376f
ms.openlocfilehash: 4b60fa44a92bff683e13f850da025d7fe753618d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349778"
---
# <a name="-operator-visual-basic"></a>*= 運算子 (Visual Basic)
Multiplies the value of a variable or property by the value of an expression and assigns the result to the variable or property.  
  
## <a name="syntax"></a>語法  
  
```vb  
variableorproperty *= expression  
```  
  
## <a name="parts"></a>組件  
 `variableorproperty`  
 必要項。 Any numeric variable or property.  
  
 `expression`  
 必要項。 任何數值運算式。  
  
## <a name="remarks"></a>備註  
 The element on the left side of the `*=` operator can be a simple scalar variable, a property, or an element of an array. The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 The `*=` operator first multiplies the value of the expression (on the right-hand side of the operator) by the value of the variable or property (on the left-hand side of the operator). The operator then assigns the result of that operation to the variable or property.  
  
## <a name="overloading"></a>多載化  
 The [* Operator](../../../visual-basic/language-reference/operators/multiplication-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure. Overloading the `*` operator affects the behavior of the `*=` operator. If your code uses `*=` on a class or structure that overloads `*`, be sure you understand its redefined behavior. 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 The following example uses the `*=` operator to multiply one `Integer` variable by a second and assign the result to the first variable.  
  
 [!code-vb[VbVbalrOperators#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>請參閱

- [* 運算子](../../../visual-basic/language-reference/operators/multiplication-operator.md)
- [指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)
