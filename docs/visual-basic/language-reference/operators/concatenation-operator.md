---
title: '&amp; 運算子'
ms.date: 07/20/2015
f1_keywords:
- vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
ms.openlocfilehash: 4cae7e59083890e82d754bdaa58942c2224357b0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336061"
---
# <a name="amp-operator-visual-basic"></a>&amp; Operator (Visual Basic)
Generates a string concatenation of two expressions.  
  
## <a name="syntax"></a>語法  
  
```vb  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要項。 Any `String` or `Object` variable.  
  
 `expression1`  
 必要項。 Any expression with a data type that widens to `String`.  
  
 `expression2`  
 必要項。 Any expression with a data type that widens to `String`.  
  
## <a name="remarks"></a>備註  
 If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`. If either of the data types does not widen to `String`, the compiler generates an error.  
  
 The data type of `result` is `String`. If one or both expressions evaluate to [Nothing](../../../visual-basic/language-reference/nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".  
  
> [!NOTE]
> The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure. If your code uses this operator on such a class or structure, be sure you understand its redefined behavior. 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
> [!NOTE]
> The ampersand (&) character can also be used to identify variables as type `Long`. For more information, see [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="example"></a>範例  
 This example uses the `&` operator to force string concatenation. The result is a string value representing the concatenation of the two string operands.  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>請參閱

- [&= 運算子](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [串連運算子](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Concatenation Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
