---
title: ^= 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: a956ffdaa3456ed09443f25c3383b6aab52fb5bf
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867062"
---
# <a name="-operator-visual-basic"></a>^= 運算子 (Visual Basic)

將變數或屬性的值引發至運算式的功能，並將結果指派回變數或屬性。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a>組件  

 `variableorproperty`  
 必要。 任何數值變數或屬性。  
  
 `expression`  
 必要。 任何數值運算式。  
  
## <a name="remarks"></a>備註  

 運算子左邊的元素 `^=` 可以是簡單的純量變數、屬性或陣列的元素。 變數或屬性不可以是 [ReadOnly](../modifiers/readonly.md)。  
  
 `^=`運算子會先將運算子左邊的變數或屬性值 (，) 為運算子右邊的運算式 (值的乘冪的值) 的最右邊。 然後，運算子會將該作業的結果指派回變數或屬性。  
  
 Visual Basic 一律會執行 [Double 資料類型](../data-types/double-data-type.md)的乘冪。 任何不同類型的運算元都會轉換成 `Double` ，而且結果一律為 `Double` 。  
  
 的值 `expression` 可以是小數、負數或兩者。  
  
## <a name="overloading"></a>多載化  

 您可以多載 [^ 運算子](exponentiation-operator.md) ，這表示當運算元的類型為該類別或結構 *時，類別*或結構可以重新定義其行為。 多載 `^` 運算子會影響運算子的行為 `^=` 。 如果您的程式碼在多載的 `^=` 類別或結構上使用 `^` ，請務必瞭解其重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  

 下列範例會使用 `^=` 運算子將某個變數的值提升 `Integer` 為第二個變數的乘冪，然後將結果指派給第一個變數。  
  
 [!code-vb[VbVbalrOperators#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>另請參閱

- [^ 運算子](exponentiation-operator.md)
- [指派運算子](assignment-operators.md)
- [算術運算子](arithmetic-operators.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [陳述式](../../programming-guide/language-features/statements.md)
