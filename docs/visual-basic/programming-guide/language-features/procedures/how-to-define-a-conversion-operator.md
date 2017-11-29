---
title: "如何：定義轉換運算子 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b0f9e63ba039a48226186fa4ce118d3e47b5673e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a>如何：定義轉換運算子 (Visual Basic)
如果您已定義類別或結構，您可以定義類別或結構的類型和其他資料型別之間型別轉換運算子 (例如`Integer`， `Double`，或`String`)。  
  
 定義型別轉換為[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)類別或結構中的程序。 所有的轉換程序必須是`Public Shared`，和每個必須指定[Widening](../../../../visual-basic/language-reference/modifiers/widening.md)或[Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)。  
  
 在類別或結構上定義運算子，也稱為*多載*運算子。  
  
## <a name="example"></a>範例  
 下列範例會定義稱為結構之間的轉換運算子`digit`和`Byte`。  
  
 [!code-vb[VbVbcnProcedures#27](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_1.vb)]  
  
 您可以測試的結構`digit`為下列程式碼。  
  
 [!code-vb[VbVbcnProcedures#28](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [運算子程序](./operator-procedures.md)  
 [如何：定義運算子](./how-to-define-an-operator.md)  
 [如何：呼叫運算子程序](./how-to-call-an-operator-procedure.md)  
 [如何：使用定義運算子的類別](./how-to-use-a-class-that-defines-operators.md)  
 [Operator 陳述式](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Structure 陳述式](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [如何：宣告結構](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [隱含和明確轉換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [擴展和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
