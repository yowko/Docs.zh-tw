---
title: ^= 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: 382e0b27c2dbf27e5acccf29f1b8d2b002cb6664
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592228"
---
# <a name="-operator-visual-basic"></a>^= 運算子 (Visual Basic)
將變數或屬性的值引發至運算式的乘冪，並將結果指派回變數或屬性。  
  
## <a name="syntax"></a>語法  
  
```vb  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a>組件  
 `variableorproperty`  
 必要項。 任何數值變數或屬性。  
  
 `expression`  
 必要項。 任何數值運算式。  
  
## <a name="remarks"></a>備註  
 @No__t-0 運算子左邊的元素可以是簡單的純量變數、屬性或陣列的元素。 變數或屬性不可為[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。  
  
 @No__t-0 運算子會先將變數或屬性的值（位於運算子的左邊），提升為運算式值的乘冪（位於運算子的右邊）。 然後，運算子會將該作業的結果指派回變數或屬性。  
  
 Visual Basic 一律會執行[Double 資料類型](../../../visual-basic/language-reference/data-types/double-data-type.md)的乘冪。 任何不同類型的運算元都會轉換成 `Double`，而結果一律 `Double`。  
  
 @No__t-0 的值可以是小數、負數或兩者。  
  
## <a name="overloading"></a>多載化  
 [^ 運算子](../../../visual-basic/language-reference/operators/exponentiation-operator.md)可以多載 *，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。 多載 `^` 運算子會影響 `^=` 運算子的行為。 如果您的程式碼在多載 `^` 的類別或結構上使用 `^=`，請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用 `^=` 運算子，將一個 @no__t 1 變數的值提升為第二個變數的乘冪，並將結果指派給第一個變數。  
  
 [!code-vb[VbVbalrOperators#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>另請參閱

- [^ 運算子](../../../visual-basic/language-reference/operators/exponentiation-operator.md)
- [指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)
