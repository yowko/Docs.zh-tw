---
title: HOW TO：呼叫運算子程序 (Visual Basic)
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
ms.openlocfilehash: ab9dd9e3f9abdd8379a59ed458c47d5ec8b4f2ad
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978965"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>HOW TO：呼叫運算子程序 (Visual Basic)
您可以在運算式中使用運算子符號，以呼叫運算子程序。 轉換運算子，在您呼叫[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)將值從一種資料類型轉換到另一個。  
  
 您未明確呼叫運算子程序。 您只使用運算子，或`CType`函式，在指派陳述式或運算式，您通常會使用運算子相同的方式。 Visual Basic 可讓運算子程序的呼叫。  
  
 類別或結構上定義的運算子，也稱為*多載*運算子。  
  
### <a name="to-call-an-operator-procedure"></a>若要呼叫運算子程序  
  
1.  在運算式中使用運算子符號，以一般方式。  
  
2.  請確定資料類型的運算元是適用於運算子，且有正確的順序。  
  
3.  如預期般，運算子會提供給運算式的值。  
  
### <a name="to-call-a-conversion-operator-procedure"></a>若要呼叫的轉換運算子程序  
  
1.  使用`CType`在運算式中。  
  
2.  請確定資料類型的運算元會適當轉換，並以正確的順序。  
  
3.  `CType` 呼叫轉換運算子程序，並傳回已轉換的值。  
  
## <a name="example"></a>範例  
 下列範例會建立兩個<xref:System.TimeSpan>、 將它們相加，並將結果儲存在第三個<xref:System.TimeSpan>結構。 <xref:System.TimeSpan>結構會定義數個標準運算子的多載的運算子程序。  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 因為<xref:System.TimeSpan>多載標準`+`運算子，前一個範例會呼叫運算子程序計算的值時`combinedSpan`。  
  
 如需呼叫交談運算子程序的範例，請參閱[How to:使用定義運算子的類別](./how-to-use-a-class-that-defines-operators.md)。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 請務必在類別或您使用的結構會定義您想要使用的運算子。  
  
## <a name="see-also"></a>另請參閱
- [運算子程序](./operator-procedures.md)
- [如何：定義運算子](./how-to-define-an-operator.md)
- [如何：定義轉換運算子](./how-to-define-a-conversion-operator.md)
- [Operator 陳述式](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Structure 陳述式](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [如何：宣告結構](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [隱含和明確轉換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [擴展和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
