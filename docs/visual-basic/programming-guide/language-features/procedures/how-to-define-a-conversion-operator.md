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
ms.openlocfilehash: 0ff95390206947e5a28f7a5b85547b496746a9cc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344892"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a>如何：定義轉換運算子 (Visual Basic)
如果您已定義類別或結構，您可以在類別或結構的類型與另一個資料類型（例如 `Integer`、`Double`或 `String`）之間定義類型轉換運算子。  
  
 將類型轉換定義為類別或結構內的[CType 函數](../../../../visual-basic/language-reference/functions/ctype-function.md)程式。 所有的轉換程式都必須 `Public Shared`，而且每一個都必須指定[擴展](../../../../visual-basic/language-reference/modifiers/widening.md)或[縮小](../../../../visual-basic/language-reference/modifiers/narrowing.md)。  
  
 在類別或結構上定義運算子*也稱為多*載運算子。  
  
## <a name="example"></a>範例  
 下列範例會在名為 `digit` 的結構和 `Byte`之間定義轉換運算子。  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 您可以使用下列程式碼來測試結構 `digit`。  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>請參閱

- [運算子程序](./operator-procedures.md)
- [如何：定義運算子](./how-to-define-an-operator.md)
- [如何：呼叫運算子程序](./how-to-call-an-operator-procedure.md)
- [如何：使用定義運算子的類別](./how-to-use-a-class-that-defines-operators.md)
- [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Structure 陳述式](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [如何：宣告結構](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [隱含和明確轉換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [擴展和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
