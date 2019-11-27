---
title: 如何：使用定義運算子的類別
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
ms.openlocfilehash: 9ec4b4c07910100dd02cc86e882b44aa7dbd2ced
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346043"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>如何：使用定義運算子的類別 (Visual Basic)
如果您使用的類別或結構定義自己的運算子，您可以從 Visual Basic 存取這些運算子。  
  
 在類別或結構上定義運算子*也稱為多*載運算子。  
  
## <a name="example"></a>範例  
 下列範例會存取 SQL 結構 <xref:System.Data.SqlTypes.SqlString>，這會在 SQL 字串和 Visual Basic 字串之間的兩個方向定義轉換運算子（[CType 函數](../../../../visual-basic/language-reference/functions/ctype-function.md)）。 使用 `CType(`*sql 字串運算式*，`String)` 將 SQL 字串轉換為 Visual Basic 字串，並 `CType(`*Visual Basic 字串運算式*，<xref:System.Data.SqlTypes.SqlString>`)` 以另一個方向轉換。  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <xref:System.Data.SqlTypes.SqlString> 結構定義從 `String` 到 <xref:System.Data.SqlTypes.SqlString> 的轉換運算子（[CType 函數](../../../../visual-basic/language-reference/functions/ctype-function.md)），另一個則是從 <xref:System.Data.SqlTypes.SqlString> 到 `String`。 將 `title` 指派給 `jobTitle` 的語句會使用第一個運算子，而 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 函式呼叫會使用第二個運算子。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 請確定您所使用的類別或結構會定義您想要使用的運算子。 請勿假設類別或結構已定義每個可用於多載的運算子。 如需可用的運算子清單，請參閱[Operator 語句](../../../../visual-basic/language-reference/statements/operator-statement.md)。  
  
 在原始程式檔的開頭包含 SQL 字串的適當 `Imports` 語句（在此案例中為 <xref:System.Data.SqlTypes>）。  
  
 您的專案必須參考 System.web 和 system.string。  
  
## <a name="see-also"></a>請參閱

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
