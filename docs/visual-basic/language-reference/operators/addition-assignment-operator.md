---
title: "+= Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.+="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "+= operator [Visual Basic]"
  - "assignment statements, compound"
  - "statements [Visual Basic], compound assignment"
  - "+= operator [Visual Basic], appending strings"
  - "compound assignment statements"
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# += Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

將數值運算式的值加入至數值變數或屬性的值，然後將結果指派給變數或屬性。  也可以將 `String` 運算式串連至 `String` 變數或屬性，然後將結果指派給變數或屬性。  
  
## 語法  
  
```  
  
variableorproperty += expression  
```  
  
## 組件  
 `variableorproperty`  
 必要項。  任何數字或 `String` 變數或屬性。  
  
 `expression`  
 必要項。  任意數值或 `String` 運算式。  
  
## 備註  
 位於 `+=` 運算子左邊的項目可以是簡單的純量 \(Scalar\) 變數、屬性或陣列元素。  變數或屬性不能為 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。  
  
 `+=`運算子將值加入至變數或屬性，它的左邊，現在，並將結果指派給變數或它左邊的屬性。  `+=`運算子也可以用來串連`String`右邊的運算式`String`變數或屬性，其左邊，及指派給變數的結果或它左邊的屬性。  
  
> [!NOTE]
>  當使用 `+=` 運算子時，可能無法判斷是否會發生加法或字串串連。  使用 `&=` 運算子執行串連，以排除模稜兩可的情況並提供自我文件化的程式碼。  
  
 如果編譯 \(Compilation\) 環境強制嚴格語意 \(Semantics\)，則這個指派運算子會隱含執行擴展轉換，但不執行縮小轉換。  如需這些轉換的詳細資訊，請參閱[Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。  如需嚴格和寬鬆語意的詳細資訊，請參閱 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)。  
  
 若允許寬鬆語意，`+=` 運算子就會隱含地執行各種字串和數值轉換，這些轉換與 `+` 運算子所執行的轉換是相同的。  如需詳細資訊，請參閱 [\+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md)。  
  
## 多載化  
 `+` 運算子可以「*多載*」，也就是，當運算元具備類別或結構的類型時，該類別或結構就可以重新定義其行為。  多載 `+` 運算子會影響 `+=` 運算子的行為。  如果您的程式碼在多載 `+` 之類別或結構上使用 `+=`，就一定要先了解其重新定義的行為。  如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## 範例  
 下列範例使用 `+=` 運算子，將一個變數的值與另一個變數值結合。  第一個部分搭配使用 `+=` 與數值變數，將一個值加入至其他值。  第二個部分搭配使用 `+=` 與 `String` 變數來串連某個值與其他值。  在這兩個範例中，所得結果都會指派給第一個變數。  
  
 [!code-vb[VbVbalrOperators#7](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/addition-assignment-oper_1_1.vb)]  
  
 [!code-vb[VbVbalrOperators#8](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/addition-assignment-oper_1_2.vb)]  
  
 `num1` 值目前為 13，`str1` 值目前則是 103。  
  
## 請參閱  
 [\+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md)   
 [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Concatenation Operators](../../../visual-basic/language-reference/operators/concatenation-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)