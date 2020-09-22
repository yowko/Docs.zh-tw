---
title: -= 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.-=
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements [Visual Basic]
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
ms.openlocfilehash: 9149d9b350fc05c5e576f9f7800725aeb330e79d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873307"
---
# <a name="--operator-visual-basic"></a>-= 運算子 (Visual Basic)

從變數或屬性的值減去運算式的值，並將結果指派給變數或屬性。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
variableorproperty -= expression  
```  
  
## <a name="parts"></a>組件  

 `variableorproperty`  
 必要。 任何數值變數或屬性。  
  
 `expression`  
 必要。 任何數值運算式。  
  
## <a name="remarks"></a>備註  

 運算子左邊的元素 `-=` 可以是簡單的純量變數、屬性或陣列的元素。 變數或屬性不可以是 [ReadOnly](../modifiers/readonly.md)。  
  
 `-=`運算子會先將運算子右邊的運算式 (的值，從運算子左邊的變數或 (屬性的值) ) 的左邊，減去運算式的值。 然後，運算子會將該操作的結果指派給變數或屬性。  
  
## <a name="overloading"></a>多載化  

 [-運算子 (Visual Basic) ](subtraction-operator.md)可以多載 *，這*表示當運算元的類型為該類別或結構時，類別或結構可以重新定義其行為。 多載 `-` 運算子會影響運算子的行為 `-=` 。 如果您的程式碼在多載的 `-=` 類別或結構上使用 `-` ，請務必瞭解其重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  

 下列範例會使用 `-=` 運算子來減去另一個 `Integer` 變數，並將結果指派給第二個變數。  
  
 [!code-vb[VbVbalrOperators#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>另請參閱

- [- 運算子 (Visual Basic)](subtraction-operator.md)
- [指派運算子](assignment-operators.md)
- [算術運算子](arithmetic-operators.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [陳述式](../../programming-guide/language-features/statements.md)
