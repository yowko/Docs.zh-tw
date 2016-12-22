---
title: "Concatenation Operators in Visual Basic | Microsoft Docs"
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
  - "& operator [Visual Basic], concatenation"
  - "concatenation operators"
  - "operators [Visual Basic], concatenation"
  - "Visual Basic code, operators"
  - "+ operator [Visual Basic], concatenation"
  - "concatenation operators, Visual Basic strings"
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
caps.latest.revision: 18
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Concatenation Operators in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

串連運算子會將多個字串連成單一字串。  串連運算子有兩種：`+` 和 `&`。  兩者都會進行基本的串連作業，如下例所示。  
  
 [!CODE [Dim x As String = "Mic" & "ro" & "soft" Dim y As String = "Mic" + "ro" + "soft" ' The preceding statements set both x and y to "Microsoft".](Dim x As String = "Mic" & "ro" & "soft" Dim y As String = "Mic" + "ro" + "soft" ' The preceding statements set both x and y to "Microsoft".)]  
  
 這些運算子也可以串連 `String` 變數，如下列所示。  
  
 [!code-vb[VbVbalrOperators#76](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operators_1.vb)]  
  
## 兩種串連運算子之間的差異  
 [\+ Operator](../../../../visual-basic/language-reference/operators/addition-operator.md) 的主要目的是將兩個數字相加。  不過，它也可以串連數值運算元與字串運算元。  `+` 運算子有一組複雜的規則，可判斷是要相加、串連、通知編譯器錯誤，還是擲回執行階段 <xref:System.InvalidCastException> 例外狀況。  
  
 [& Operator](../../../../visual-basic/language-reference/operators/concatenation-operator.md) 只針對 `String` 運算元進行定義，且它一律會將運算元擴展成 `String`，不論 `Option Strict` 的設定為何。  建議使用 `&` 運算元進行字串串連，因為它的定義為專門針對字串，且能減少您產生意外轉換的機會。  
  
## 效能：String 和 StringBuilder  
 如果您對字串進行大量的操作，例如串連、刪除和取代，可能可以藉由 <xref:System.Text> 命名空間中的 <xref:System.Text.StringBuilder> 類別而使效能獲得助益。  建立和初始化 <xref:System.Text.StringBuilder> 物件需要額外的指令，將其最終值轉換成 `String` 又再需要一個指令，但您可以彌補這個時間，因為 <xref:System.Text.StringBuilder> 執行地更快速。  
  
## 請參閱  
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Types of String Manipulation Methods in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)   
 [Arithmetic Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)