---
title: "How to: Define a Conversion Operator (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "procedures, defining"
  - "operators [Visual Basic], defining"
  - "procedures, operator"
  - "operators [Visual Basic], overloading"
  - "return values, Operator procedures"
  - "operator overloading"
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# How to: Define a Conversion Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

如果已定義類別或結構，則可定義類別或結構型別與其他資料型別 \(例如 `Integer`、`Double` 或 `String`\) 之間的型別轉換運算子。  
  
 將型別轉換定義成類別或結構內的 [CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)程序。  所有轉換程序都必須是 `Public Shared`，且每個程序都必須指定 [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) 或 [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)。  
  
 在類別或結構上定義運算子，也稱為「*多載*」\(Overload\) 運算子。  
  
## 範例  
 下列範例會定義名為  `digit`  之結構與 `Byte` 間的轉換運算子。  
  
 [!code-vb[VbVbcnProcedures#27](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-define-a-conversi_1.vb)]  
  
 您可以使用下列程式碼來測試結構 `digit`。  
  
 [!code-vb[VbVbcnProcedures#28](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-define-a-conversi_2.vb)]  
  
## 請參閱  
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [How to: Define an Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [How to: Call an Operator Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)   
 [How to: Use a Class that Defines Operators](../../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)   
 [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)