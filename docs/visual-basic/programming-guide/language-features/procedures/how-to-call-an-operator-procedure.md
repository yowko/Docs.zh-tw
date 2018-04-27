---
title: 如何：呼叫運算子程序 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 21545f2488bfabd0abc9c6e316d21bbc4d5aeb91
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>如何：呼叫運算子程序 (Visual Basic)
您可以在運算式中使用運算子符號，以呼叫運算子程序。 如果是轉換運算子，您呼叫[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)將值從一種資料類型轉換到另一個。  
  
 您無法明確呼叫運算子程序。 您只使用運算子，或`CType`函式，在指派陳述式或運算式，您通常使用運算子的相同方式。 Visual Basic 呼叫運算子程序。  
  
 在類別或結構上定義運算子，也稱為*多載*運算子。  
  
### <a name="to-call-an-operator-procedure"></a>若要呼叫運算子程序  
  
1.  在運算式中使用運算子符號，以一般方式。  
  
2.  請確定資料類型的運算元是適用於運算子，且有正確的順序。  
  
3.  如預期般，運算子就是計算運算式的值。  
  
### <a name="to-call-a-conversion-operator-procedure"></a>若要呼叫轉換運算子程序  
  
1.  使用`CType`在運算式中。  
  
2.  請確定資料類型的運算元不適當的轉換，並且以正確的順序。  
  
3.  `CType` 呼叫轉換運算子程序，並傳回已轉換的值。  
  
## <a name="example"></a>範例  
 下列範例會建立兩個<xref:System.TimeSpan>、 將它們相加，並將結果儲存在第三個<xref:System.TimeSpan>結構。 <xref:System.TimeSpan>結構會定義數個標準的運算子多載的運算子程序。  
  
 [!code-vb[VbVbcnProcedures#29](./codesnippet/VisualBasic/how-to-call-an-operator-procedure_1.vb)]  
  
 因為<xref:System.TimeSpan>多載標準`+`運算子，前一個範例會呼叫運算子程序計算的值時`combinedSpan`。  
  
 如需呼叫交談運算子程序的範例，請參閱[How to： 使用類別，該定義的運算子](./how-to-use-a-class-that-defines-operators.md)。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 請確定該類別或結構會使用定義您想要使用的運算子。  
  
## <a name="see-also"></a>另請參閱  
 [運算子程序](./operator-procedures.md)  
 [如何：定義運算子](./how-to-define-an-operator.md)  
 [如何：定義轉換運算子](./how-to-define-a-conversion-operator.md)  
 [Operator 陳述式](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Structure 陳述式](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [如何：宣告結構](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [隱含和明確轉換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [擴展和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
