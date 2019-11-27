---
title: 如何：呼叫運算子程序
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedure calls [Visual Basic], operator overloading
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- overloaded operators [Visual Basic], calling
- operator overloading
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
ms.openlocfilehash: a685be7cc3b346b271413e2c29faae5a839313f4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340237"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>如何：呼叫運算子程序 (Visual Basic)
您可以在運算式中使用運算子符號來呼叫運算子程式。 在轉換運算子的情況下，您可以呼叫[CType](../../../../visual-basic/language-reference/functions/ctype-function.md)函式，將值從一種資料類型轉換成另一種。  
  
 您不會明確地呼叫運算子程式。 您只要在指派語句或運算式中使用運算子或 `CType` 函數，就像平常使用運算子一樣。 Visual Basic 會呼叫運算子程式。  
  
 在類別或結構上定義運算子*也稱為多*載運算子。  
  
### <a name="to-call-an-operator-procedure"></a>呼叫運算子程式  
  
1. 以一般方式在運算式中使用運算子符號。  
  
2. 請確定運算元的資料類型適用于運算子，並以正確的順序排列。  
  
3. 運算子會如預期般貢獻運算式的值。  
  
### <a name="to-call-a-conversion-operator-procedure"></a>呼叫轉換運算子程式  
  
1. 在運算式內使用 `CType`。  
  
2. 請確定運算元的資料類型適用于轉換，並以正確的順序排列。  
  
3. `CType` 會呼叫轉換運算子程式，並傳回轉換後的值。  
  
## <a name="example"></a>範例  
 下列範例會建立兩個 <xref:System.TimeSpan> 結構，將它們相加，然後將結果儲存在第三個 <xref:System.TimeSpan> 結構中。 <xref:System.TimeSpan> 結構會定義運算子程式來多載數個標準運算子。  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 因為 <xref:System.TimeSpan> 會多載標準 `+` 運算子，所以先前的範例會在計算 `combinedSpan`的值時呼叫 operator 程式。  
  
 如需呼叫交談運算子程式的範例，請參閱[如何：使用定義運算子的類別](./how-to-use-a-class-that-defines-operators.md)。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 請確定您所使用的類別或結構會定義您想要使用的運算子。  
  
## <a name="see-also"></a>請參閱

- [運算子程序](./operator-procedures.md)
- [如何：定義運算子](./how-to-define-an-operator.md)
- [如何：定義轉換運算子](./how-to-define-a-conversion-operator.md)
- [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Structure 陳述式](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [如何：宣告結構](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [隱含和明確轉換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [擴展和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
