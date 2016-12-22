---
title: "How to: Use a Class that Defines Operators (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "operator procedures, calling"
  - "procedures, operator"
  - "procedures, calling"
  - "examples [Visual Basic], CType"
  - "syntax, Operator procedures"
  - "operators [Visual Basic], overloading"
  - "return values, Operator procedures"
  - "operator overloading"
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Use a Class that Defines Operators (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

如果使用的是定義它自己運算子的類別或結構，則可從 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 中存取那些運算子。  
  
 在類別或結構上定義運算子，也稱為「*多載*」\(Overload\) 運算子。  
  
## 範例  
 下列範例會存取 SQL 結構 <xref:System.Data.SqlTypes.SqlString>，會於 SQL 字串與 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 字串的兩個方向間定義轉換運算子 \([CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)\)。  使用 `CType(`*SQL string expression*, `String)` 將 SQL 字串轉換成 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 字串，而 `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` 則可朝另一個方向轉換。  
  
 [!CODE [VbVbcnProcedures#30](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#30)]  
  
 [!CODE [VbVbcnProcedures#31](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#31)]  
  
 <xref:System.Data.SqlTypes.SqlString> 結構會將轉換運算子 \([CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)\) 定義成從 `String` 轉換成 <xref:System.Data.SqlTypes.SqlString>，另一個則是從 <xref:System.Data.SqlTypes.SqlString> 轉換成 `String`。  將 `title` 指派給 `jobTitle` 的陳述式會使用第一個運算子，而 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 函式呼叫則會使用第二個。  
  
## 編譯程式碼  
 請確定所使用的類別或結構會定義您想使用的運算子。  不要假設類別或結構已定義可用於多載化的每個運算子。  如需可用運算子的清單，請參閱 [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)。  
  
 在原始程式檔開頭處包含 SQL 字串的適當 `Imports` 陳述式 \(此例中為 <xref:System.Data.SqlTypes>\)。  
  
 專案必須具有 System.Data 和 System.XML 的參考。  
  
## 請參閱  
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [How to: Define an Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [How to: Call an Operator Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)   
 [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)   
 [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)