---
title: "如何︰ 呼叫運算子程序 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- operator procedures, calling
- procedures, operator
- procedure calls, operator overloading
- syntax, Operator procedures
- operators [Visual Basic], overloading
- return values, Operator procedures
- overloaded operators, calling
- operator overloading
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
caps.latest.revision: 16
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2403e7a8270c17a8db5417cd8394fd47c373d493
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>如何：呼叫運算子程序 (Visual Basic)
您可以在運算式中使用運算子符號呼叫運算子程序。 轉換運算子，在您呼叫[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)將值從一種資料類型轉換到另一個。  
  
 您無法明確地呼叫運算子程序。 您只使用運算子，或`CType`函式，在指派陳述式或運算式相同的方式，您通常使用的運算子。 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]呼叫運算子程序。  
  
 在類別或結構上定義運算子，也稱為*多載*運算子。  
  
### <a name="to-call-an-operator-procedure"></a>若要呼叫運算子程序  
  
1.  在運算式中使用運算子符號，以一般方式。  
  
2.  請確定資料類型的運算元是適用於運算子，且正確的順序。  
  
3.  如預期般，運算子會提供給運算式的值。  
  
### <a name="to-call-a-conversion-operator-procedure"></a>若要呼叫的轉換運算子程序  
  
1.  使用`CType`運算式內。  
  
2.  請務必運算元的資料型別是正確的轉換，和正確的順序。  
  
3.  `CType`呼叫轉換運算子程序，並傳回已轉換的值。  
  
## <a name="example"></a>範例  
 下列範例會建立兩個<xref:System.TimeSpan>、 將它們相加，並將結果儲存在第三個<xref:System.TimeSpan>結構。</xref:System.TimeSpan> </xref:System.TimeSpan> <xref:System.TimeSpan>結構會定義數個標準的運算子多載的運算子程序。</xref:System.TimeSpan>  
  
 [!code-vb[VbVbcnProcedures #&29;](./codesnippet/VisualBasic/how-to-call-an-operator-procedure_1.vb)]  
  
 因為<xref:System.TimeSpan>多載標準`+`運算子前, 一個範例則會呼叫運算子程序計算的值時`combinedSpan`。</xref:System.TimeSpan>  
  
 呼叫交談運算子程序的範例，請參閱[How to︰ 使用類別的定義運算子](./how-to-use-a-class-that-defines-operators.md)。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 請確定您使用的結構或類別定義您想要使用的運算子。  
  
## <a name="see-also"></a>另請參閱  
 [運算子程序](./operator-procedures.md)   
 [如何︰ 定義運算子](./how-to-define-an-operator.md)   
 [如何︰ 定義轉換運算子](./how-to-define-a-conversion-operator.md)   
 [Operator 陳述式](../../../../visual-basic/language-reference/statements/operator-statement.md)   
 [擴展](../../../../visual-basic/language-reference/modifiers/widening.md)   
 [縮小](../../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Structure 陳述式](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [如何︰ 宣告結構](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [隱含和明確轉換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [擴展和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
