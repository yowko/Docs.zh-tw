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
If you are using a class or structure that defines its own operators, you can access those operators from Visual Basic.  
  
 Defining an operator on a class or structure is also called *overloading* the operator.  
  
## <a name="example"></a>範例  
 The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) in both directions between a SQL string and a Visual Basic string. Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a Visual Basic string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`. The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 Be sure the class or structure you are using defines the operator you want to use. Do not assume that the class or structure has defined every operator available for overloading. For a list of available operators, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
 Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).  
  
 Your project must have references to System.Data and System.XML.  
  
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
