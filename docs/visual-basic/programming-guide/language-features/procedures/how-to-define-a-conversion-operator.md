---
title: HOW TO：定義轉換運算子 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: cf7bfdd09c7f3429f9c730a7aec34b24af3f2e9f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829222"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a>HOW TO：定義轉換運算子 (Visual Basic)
如果您已定義類別或結構，您可以定義您自己的類別或結構的類型與另一個資料類型之間的型別轉換運算子 (例如`Integer`， `Double`，或`String`)。  
  
 定義類型轉換成[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)類別或結構內的程序。 所有的轉換程序必須是`Public Shared`，以及每一個都必須指定[Widening](../../../../visual-basic/language-reference/modifiers/widening.md)或是[Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)。  
  
 類別或結構上定義的運算子，也稱為*多載*運算子。  
  
## <a name="example"></a>範例  
 下列範例會定義結構，稱為之間的轉換運算子`digit`和`Byte`。  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 您可以測試結構`digit`為下列程式碼。  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>另請參閱

- [運算子程序](./operator-procedures.md)
- [如何：定義運算子](./how-to-define-an-operator.md)
- [如何：呼叫運算子程序](./how-to-call-an-operator-procedure.md)
- [如何：使用定義運算子的類別](./how-to-use-a-class-that-defines-operators.md)
- [Operator 陳述式](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Structure 陳述式](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [如何：宣告結構](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [隱含和明確轉換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [擴展和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
