---
title: "How to: Call an Operator Procedure (Visual Basic) | Microsoft Docs"
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
  - "operator procedures, calling"
  - "procedures, operator"
  - "procedure calls, operator overloading"
  - "syntax, Operator procedures"
  - "operators [Visual Basic], overloading"
  - "return values, Operator procedures"
  - "overloaded operators, calling"
  - "operator overloading"
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Call an Operator Procedure (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

您可以在運算式中使用運算子符號，呼叫運算子程序。  在轉換運算子的情況中，您可以呼叫 [CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)，將值從某個資料型別轉換為另一個資料型別。  
  
 您並未明確地呼叫運算子程序。  使用指派陳述式或運算式中的運算子或 `CType` 函式時，方法只要和平常使用運算子的方法相同，  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 就會進行運算子程序的呼叫。  
  
 在類別或結構上定義運算子，也稱為「*多載*」\(Overload\) 運算子。  
  
### 若要呼叫運算子程序  
  
1.  以一般方式在運算式中使用運算子符號。  
  
2.  確定運算元的資料型別適用於運算子且有正確的順序。  
  
3.  運算子如預期般地組成運算式的值。  
  
### 若要呼叫轉換運算子程序  
  
1.  在運算式內使用 `CType`。  
  
2.  確定運算元的資料型別適用於轉換且有正確的順序。  
  
3.  `CType` 呼叫轉換運算子程序並傳回已轉換的值。  
  
## 範例  
 下列範例會建立兩個 <xref:System.TimeSpan> 結構、將它們加在一起，以及將結果儲存在第三個 <xref:System.TimeSpan> 結構中。  <xref:System.TimeSpan> 結構會定義運算子程序，以多載數個標準運算子。  
  
 [!code-vb[VbVbcnProcedures#29](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-call-an-operator-_1.vb)]  
  
 因為 <xref:System.TimeSpan> 會多載標準 `+` 運算子，所以上述範例會在計算 `combinedSpan` 的值時呼叫運算子程序。  
  
 如需呼叫溝通運算子程序的範例，請參閱 [How to: Use a Class that Defines Operators](../../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)。  
  
## 編譯程式碼  
 請確定所使用的類別或結構會定義您想使用的運算子。  
  
## 請參閱  
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [How to: Define an Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)   
 [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)