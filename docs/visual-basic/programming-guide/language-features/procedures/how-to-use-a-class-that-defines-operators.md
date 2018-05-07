---
title: 如何：使用定義運算子的類別 (Visual Basic)
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
ms.openlocfilehash: 7e1d5698c1e83f0adf1be67245e0726aecaabdac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>如何：使用定義運算子的類別 (Visual Basic)
如果您使用類別或結構，定義自己的運算子，您可以從 Visual Basic 中存取這些運算子。  
  
 在類別或結構上定義運算子，也稱為*多載*運算子。  
  
## <a name="example"></a>範例  
 下列範例會存取 SQL 結構<xref:System.Data.SqlTypes.SqlString>，它負責定義轉換運算子 ([CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)) 中的 SQL 字串與 Visual Basic 字串之間雙向流動。 使用`CType(` *SQL 字串運算式*，`String)`要轉換成 Visual Basic 字串，SQL 字串和`CType(` *Visual Basic 字串運算式*， <xref:System.Data.SqlTypes.SqlString> `)`轉換中另一種方向。  
  
 [!code-vb[VbVbcnProcedures#30](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#31](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]  
  
 <xref:System.Data.SqlTypes.SqlString>結構會定義轉換運算子 ([CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)) 從`String`至<xref:System.Data.SqlTypes.SqlString>，從另一個<xref:System.Data.SqlTypes.SqlString>至`String`。 指派的陳述式`title`至`jobTitle`會使用第一個運算子，而<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>函式呼叫會使用第二個。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 請確定該類別或結構會使用定義您想要使用的運算子。 請勿假設類別或結構定義每個可用的多載的運算子。 如需可用的運算子，請參閱[Operator 陳述式](../../../../visual-basic/language-reference/statements/operator-statement.md)。  
  
 包含適當`Imports`SQL 字串的開頭的陳述式的原始程式檔 (在此情況下<xref:System.Data.SqlTypes>)。  
  
 您的專案必須已 System.Data 和 System.XML 參考。  
  
## <a name="see-also"></a>另請參閱  
 [運算子程序](./operator-procedures.md)  
 [如何：定義運算子](./how-to-define-an-operator.md)  
 [如何：定義轉換運算子](./how-to-define-a-conversion-operator.md)  
 [如何：呼叫運算子程序](./how-to-call-an-operator-procedure.md)  
 [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Structure 陳述式](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [如何：宣告結構](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [隱含和明確轉換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [擴展和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
