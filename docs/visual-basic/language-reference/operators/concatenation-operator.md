---
title: "&amp; Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.&"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "And (&) operator"
  - "ampersand operator (&)"
  - "& operator"
  - "concatenation operators, syntax"
  - "strings [Visual Basic], concatenating"
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# &amp; Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

產生兩個運算式的字串串連。  
  
## 語法  
  
```  
  
result = expression1 & expression2  
```  
  
## 組件  
 `result`  
 必要項。  任何 `String` 或 `Object` 變數。  
  
 `expression1`  
 必要項。  任何有擴展至 `String` 資料型別的運算式。  
  
 `expression2`  
 必要項。  任何有擴展至 `String` 資料型別的運算式。  
  
## 備註  
 如果 `expression1` 或 `expression2` 的資料型別不是 `String`，但可擴展至 `String`，則會將其轉換成 `String`。  若沒有資料型別可擴展至 `String`，則編譯器會產生錯誤。  
  
 `result` 的資料型別是 `String`。  如果一或兩個運算式評估為 [Nothing](../../../visual-basic/language-reference/nothing.md)，或有 <xref:System.DBNull.Value?displayProperty=fullName> 值，則會將這些運算式視為 "" 值的字串處理。  
  
> [!NOTE]
>  `&` 運算子可以「*多載*」，也就是，當運算元具備類別或結構的類型時，該類別或結構就可以重新定義其行為。  如果您的程式碼在這種類別或結構上使用此運算子，就一定要先瞭解其重新定義的行為。  如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
> [!NOTE]
>  連字號 \(&\) 字元也可以用於將變數識別為 `Long` 型別。  如需詳細資訊，請參閱 [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)。  
  
## 範例  
 這個範例會使用 `&` 運算子以強制字串串連。  結果是代表兩個字串運算元串連的字串值。  
  
 [!code-vb[VbVbalrOperators#2](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/concatenation-operator_1.vb)]  
  
## 請參閱  
 [&\= Operator](../../../visual-basic/language-reference/operators/and-assignment-operator.md)   
 [Concatenation Operators](../../../visual-basic/language-reference/operators/concatenation-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Concatenation Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)