---
title: "Operator Procedures (Visual Basic) | Microsoft Docs"
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
  - "Visual Basic code, procedures"
  - "procedures, operator"
  - "Visual Basic code, operators"
  - "syntax, Operator procedures"
  - "operators [Visual Basic], overloading"
  - "overloaded operators"
  - "operator overloading"
  - "operator procedures"
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operator Procedures (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

運算子程序是一連串的 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 陳述式，用來在已定義之類別或結構上定義標準運算子 \(例如，`*`、`<>` 或 `And`\) 的行為。  這也稱為「*運算子多載*」\(Operator Overloading\)。  
  
## 定義運算子程序的時機  
 已定義類別或結構時，可將變數宣告成該類別或結構的型別。  有時，這類變數需要參與運算式的運算。  若要這樣做，則它必須是運算子的運算元。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 只可將運算子定義成它的主要資料型別。  當其中一個或兩個運算元的型別是類別或結構的型別時，即可定義運算子的行為。  
  
 如需詳細資訊，請參閱 [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)。  
  
## 運算子程序的型別  
 運算子程序可以是下列其中一個型別：  
  
-   一元 \(Unary\) 運算子的定義，其中引數的型別就是類別或結構的型別。  
  
-   二元 \(Binary\) 運算子的定義，其中至少要有一個引數的型別是類別或結構的型別。  
  
-   轉換運算子的定義，其中引數的型別就是類別或結構的型別。  
  
-   轉換運算子的定義，傳回類別或結構的型別。  
  
 轉換運算子一律為一元，且一律使用 `CType` 當成所定義的運算子。  
  
## 宣告語法  
 宣告運算子程序的語法如下：  
  
 `Public Shared`   `[Widening | Narrowing]`   `Operator`   ``  *operatorsymbol*  `(` *operand1*  `[,`  *operand2* `]) As`  *datatype*  
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 `Widening` 或 `Narrowing` 關鍵字只可用於型別轉換運算子上。  運算子符號一律是型別轉換運算子的 [CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)。  
  
 宣告兩個運算元以定義二元運算子，且宣告一個運算元以定義一元運算子 \(包含型別轉換運算子\)。  必須宣告所有運算元 `ByVal`。  
  
 每個運算元的宣告方式都與宣告 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)之參數的方式相同。  
  
### 資料型別  
 因為是在已定義的類別或結構上定義運算子，所以至少必須有一個運算元的型別是該類別或結構的型別。  若為型別轉換運算子，則運算元或傳回型別的型別必須是類別或結構的資料型別。  
  
 如需詳細資訊，請參閱 [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)。  
  
## 呼叫語法  
 在運算式中使用運算子符號，即可隱含叫用 \(Invoke\) 運算子程序。  提供運算元的方式與提供預先定義之運算子的方式相同。  
  
 運算子程序的隱含呼叫語法如下：  
  
 `Dim testStruct As`  *structurename*  
  
 `Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`  
  
### 宣告和呼叫的說明  
 下列結構會將帶有正負號的 128 位元整數值儲存成構成高序位 \(High Order\) 和低序位 \(Low Order\) 部分。  它會定義 `+` 運算子以相加兩個 `veryLong` 值，並產生結果 `veryLong` 值。  
  
 [!CODE [VbVbcnProcedures#23](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#23)]  
  
 下列範例會顯示在 `veryLong` 上所定義之 `+` 運算子的典型呼叫：  
  
 [!CODE [VbVbcnProcedures#24](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#24)]  
  
 如需詳細資訊和範例，請參閱 [Visual Basic 2005 中的運算子多載](http://go.microsoft.com/fwlink/?LinkId=101703) \(英文\)。  
  
## 請參閱  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [函式程序](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [屬性程序](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)   
 [How to: Define an Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [How to: Call an Operator Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)   
 [How to: Use a Class that Defines Operators](../../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)