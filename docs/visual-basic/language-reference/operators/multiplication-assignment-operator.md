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
將變數或屬性的值乘以運算式的值，並將結果指派給變數或屬性。  
  
## <a name="syntax"></a>語法  
  
```vb  
variableorproperty *= expression  
```  
  
## <a name="parts"></a>組件  
 `variableorproperty`  
 必要。 任何數值變數或屬性。  
  
 `expression`  
 必要。 任何數值運算式。  
  
## <a name="remarks"></a>備註  
 `*=` 運算子左邊的元素可以是簡單的純量變數、屬性或陣列的元素。 變數或屬性不可為[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。  
  
 `*=` 運算子會先將運算式的值（位於運算子的右邊）乘以變數或屬性的值（在運算子的左邊）來相乘。 然後，運算子會將該作業的結果指派給變數或屬性。  
  
## <a name="overloading"></a>多載化  
 [* 運算子](../../../visual-basic/language-reference/operators/multiplication-operator.md)可以多載 *，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。 多載 `*` 運算子會影響 `*=` 運算子的行為。 如果您的程式碼在多載 `*`的類別或結構上使用 `*=`，請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用 `*=` 運算子，將一個 `Integer` 變數乘以一秒，然後將結果指派給第一個變數。  
  
 [!code-vb[VbVbalrOperators#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>另請參閱

- [* 運算子](../../../visual-basic/language-reference/operators/multiplication-operator.md)
- [指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)
