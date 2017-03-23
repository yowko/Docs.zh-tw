---
title: "如何︰ 使用類別定義運算子 (Visual Basic) |Microsoft 文件"
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
- procedures, calling
- examples [Visual Basic], CType
- syntax, Operator procedures
- operators [Visual Basic], overloading
- return values, Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
caps.latest.revision: 21
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
ms.openlocfilehash: b1db7c0b2a6fd8160baa48892b5f2214df24674e
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>如何：使用定義運算子的類別 (Visual Basic)
如果您使用的類別或結構定義自己的運算子，您可以存取這些運算子，從[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。  
  
 在類別或結構上定義運算子，也稱為*多載*運算子。  
  
## <a name="example"></a>範例  
 下列範例會存取 SQL 結構<xref:System.Data.SqlTypes.SqlString>，以定義轉換運算子 ([CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)) 中的 SQL 字串之間進行雙向和[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]字串。</xref:System.Data.SqlTypes.SqlString> 使用`CType(` *SQL 字串運算式*，`String)`要轉換的 SQL 字串[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]字串，和`CType(` *Visual Basic 字串運算式*，<xref:System.Data.SqlTypes.SqlString>`)`將另一個方向。</xref:System.Data.SqlTypes.SqlString>  
  
 [!code-vb[VbVbcnProcedures #&30;](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]  
  
 [!code-vb[VbVbcnProcedures #&31;](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]  
  
 <xref:System.Data.SqlTypes.SqlString>結構定義的轉換運算子 ([CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)) 從`String`至<xref:System.Data.SqlTypes.SqlString>，從另一個<xref:System.Data.SqlTypes.SqlString>到`String`。</xref:System.Data.SqlTypes.SqlString> </xref:System.Data.SqlTypes.SqlString> </xref:System.Data.SqlTypes.SqlString> 指派的陳述式`title`至`jobTitle`會使用第一個運算子，而<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>函式呼叫會使用第二個。</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 請確定您使用的結構或類別定義您想要使用的運算子。 請勿假設類別或結構定義每個可用的多載的運算子。 如需可用的運算子，請參閱[Operator 陳述式](../../../../visual-basic/language-reference/statements/operator-statement.md)。  
  
 包含適當`Imports`SQL 字串開頭的陳述式的原始程式檔 (在此情況下<xref:System.Data.SqlTypes>)。</xref:System.Data.SqlTypes>  
  
 您的專案必須參考 System.Data 和 System.XML 等。  
  
## <a name="see-also"></a>另請參閱  
 [運算子程序](./operator-procedures.md)   
 [如何︰ 定義運算子](./how-to-define-an-operator.md)   
 [如何︰ 定義轉換運算子](./how-to-define-a-conversion-operator.md)   
 [如何︰ 呼叫運算子程序](./how-to-call-an-operator-procedure.md)   
 [擴展](../../../../visual-basic/language-reference/modifiers/widening.md)   
 [縮小](../../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Structure 陳述式](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [如何︰ 宣告結構](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [隱含和明確轉換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [擴展和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
