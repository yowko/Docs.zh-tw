---
title: 'How to: Define a Conversion Operator'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: 2fabcf6c6ceb38fe77d4eed4f02dcb5a5e447bf1
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085668"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a>如何：定義轉換運算子 (Visual Basic)

如果您已定義類別或結構，則可以在類別或結構的型別與另一個資料類型 (（例如 `Integer` 、或) ）之間定義型別轉換運算子 `Double` `String` 。  
  
 將類型轉換定義為類別或結構中的 [CType 函數](../../../language-reference/functions/ctype-function.md) 程式。 所有的轉換程式都必須是 `Public Shared` ，而且每一個都必須指定 [擴展](../../../language-reference/modifiers/widening.md) 或 [縮小](../../../language-reference/modifiers/narrowing.md)。  
  
 在類別或結構上定義運算子 *也稱為多* 載運算子。  
  
## <a name="example"></a>範例  

 下列範例會定義名為和的結構之間的轉換運算子 `digit` `Byte` 。  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 您可以使用下列程式碼來測試結構 `digit` 。  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>另請參閱

- [運算子程序](./operator-procedures.md)
- [如何：定義運算子](./how-to-define-an-operator.md)
- [如何：呼叫運算子程序](./how-to-call-an-operator-procedure.md)
- [如何：使用定義運算子的類別](./how-to-use-a-class-that-defines-operators.md)
- [Operator Statement](../../../language-reference/statements/operator-statement.md)
- [Structure 陳述式](../../../language-reference/statements/structure-statement.md)
- [作法：宣告結構](../data-types/how-to-declare-a-structure.md)
- [隱含和明確轉換](../data-types/implicit-and-explicit-conversions.md)
- [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md)
