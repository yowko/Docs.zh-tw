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
ms.openlocfilehash: fe15e976e6a5469f2a9d1b3521a70a3e1860fdd3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414346"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>如何：使用定義運算子的類別 (Visual Basic)
如果您使用的類別或結構定義自己的運算子，您可以從 Visual Basic 存取這些運算子。  
  
 在類別或結構上定義運算子*也稱為多*載運算子。  
  
## <a name="example"></a>範例  
 下列範例會存取 SQL 結構 <xref:System.Data.SqlTypes.SqlString> ，這會在 sql 字串與 Visual Basic 字串之間的兩個方向中定義轉換運算子（[CType 函數](../../../language-reference/functions/ctype-function.md)）。 使用 `CType(` *sql 字串運算式*，將 `String)` sql 字串轉換成 Visual Basic 字串，並 `CType(` *Visual Basic 字串運算式*， <xref:System.Data.SqlTypes.SqlString> `)` 以另一個方向進行轉換。  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <xref:System.Data.SqlTypes.SqlString>結構會定義從到的轉換運算子（[CType 函數](../../../language-reference/functions/ctype-function.md)） `String` <xref:System.Data.SqlTypes.SqlString> ，另一個則從 <xref:System.Data.SqlTypes.SqlString> 到 `String` 。 指派給的語句 `title` `jobTitle` 會使用第一個運算子，而 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 函式呼叫會使用第二個運算子。  
  
## <a name="compile-the-code"></a>編譯程式碼  
 請確定您所使用的類別或結構會定義您想要使用的運算子。 請勿假設類別或結構已定義每個可用於多載的運算子。 如需可用的運算子清單，請參閱[Operator 語句](../../../language-reference/statements/operator-statement.md)。  
  
 在 `Imports` 原始程式檔的開頭包含 SQL 字串的適當語句（在此案例中為 <xref:System.Data.SqlTypes> ）。  
  
 您的專案必須參考 System.web 和 system.string。  
  
## <a name="see-also"></a>另請參閱

- [運算子程序](./operator-procedures.md)
- [如何：定義運算子](./how-to-define-an-operator.md)
- [How to: Define a Conversion Operator](./how-to-define-a-conversion-operator.md)
- [如何：呼叫運算子程序](./how-to-call-an-operator-procedure.md)
- [Widening](../../../language-reference/modifiers/widening.md)
- [Narrowing](../../../language-reference/modifiers/narrowing.md)
- [Structure 陳述式](../../../language-reference/statements/structure-statement.md)
- [作法：宣告結構](../data-types/how-to-declare-a-structure.md)
- [隱含和明確轉換](../data-types/implicit-and-explicit-conversions.md)
- [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md)
