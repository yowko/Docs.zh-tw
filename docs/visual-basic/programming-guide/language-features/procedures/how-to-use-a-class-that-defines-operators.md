---
title: HOW TO：使用一個類別來定義運算子 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedures [Visual Basic], calling
- examples [Visual Basic], CType
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
ms.openlocfilehash: bd512adf2f06ed0fbd3d36ed3175a0928bf1c57c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829404"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>HOW TO：使用一個類別來定義運算子 (Visual Basic)
如果您使用的類別或結構，定義自己的運算子，您可以從 Visual Basic 中存取這些運算子。  
  
 類別或結構上定義的運算子，也稱為*多載*運算子。  
  
## <a name="example"></a>範例  
 下列範例會存取 SQL 結構<xref:System.Data.SqlTypes.SqlString>，其定義轉換運算子 ([CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)) 中的 SQL 字串和 Visual Basic 字串之間的兩個方向。 使用`CType(` *SQL 字串運算式*，`String)`將 SQL 字串轉換成 Visual Basic 字串，並`CType(` *Visual Basic 字串運算式*， <xref:System.Data.SqlTypes.SqlString> `)`另一個方向的轉換。  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <xref:System.Data.SqlTypes.SqlString>結構會定義轉換運算子 ([CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)) 從`String`來<xref:System.Data.SqlTypes.SqlString>，從另一種<xref:System.Data.SqlTypes.SqlString>至`String`。 指派的陳述式`title`要`jobTitle`會使用第一個運算子，而<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>函式呼叫會使用第二個。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 請務必在類別或您使用的結構會定義您想要使用的運算子。 請勿假設類別或結構定義每個適用於多載的運算子。 如需可用的運算子，請參閱[Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)。  
  
 包含適當`Imports`原始程式檔的 SQL 字串開頭的陳述式 (在此情況下<xref:System.Data.SqlTypes>)。  
  
 您的專案必須參考 System.Data 和 System.XML。  
  
## <a name="see-also"></a>另請參閱

- [運算子程序](./operator-procedures.md)
- [如何：定義運算子](./how-to-define-an-operator.md)
- [如何：定義轉換運算子](./how-to-define-a-conversion-operator.md)
- [如何：呼叫運算子程序](./how-to-call-an-operator-procedure.md)
- [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Structure 陳述式](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [如何：宣告結構](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [隱含和明確轉換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [擴展和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
