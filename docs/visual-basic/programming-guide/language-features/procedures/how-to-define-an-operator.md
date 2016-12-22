---
title: "How to: Define an Operator (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "procedures, defining"
  - "Visual Basic code, procedures"
  - "operators [Visual Basic], defining"
  - "procedures, operator"
  - "Visual Basic code, operators"
  - "syntax, Operator procedures"
  - "operators [Visual Basic], overloading"
  - "operator procedures, about operator procedures"
  - "return values, Operator procedures"
  - "operator overloading"
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Define an Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

若已定義類別或結構，則當其中一或兩個運算元的型別是類別或結構的型別時，就可以定義標準運算子的行為 \(例如 `*`、`<>` 或 `And`\)。  
  
 將標準運算子定義成類別或結構內部的運算子程序。  所有運算子程序都必須是 `Public` `Shared`。  
  
 在類別或結構上定義運算子，也稱為「*多載*」\(Overload\) 運算子。  
  
## 範例  
 下列範例定義 `height` 結構的 `+` 運算子。  結構使用以英呎和英吋測量的高度。  一「*英吋*」\(Inch\) 是 2.54 公分，一「*英呎*」\(Foot\) 則是 12 英吋。  為了確保值標準化 \(英吋 \< 12.0\)，建構函式會執行 *modulo* 12 運算。  `+` 運算子可使用建構函式來產生標準化值。  
  
 [!CODE [VbVbcnProcedures#25](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#25)]  
  
 您可以使用下列程式碼測試結構 `height` 。  
  
 [!CODE [VbVbcnProcedures#26](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#26)]  
  
 如需詳細資訊和範例，請參閱 [Visual Basic 2005 中的運算子多載](http://go.microsoft.com/fwlink/?LinkId=101703) \(英文\)。  
  
## 請參閱  
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [How to: Call an Operator Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)   
 [How to: Use a Class that Defines Operators](../../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)   
 [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Mod 運算子](../../../../visual-basic/language-reference/operators/mod-operator.md)