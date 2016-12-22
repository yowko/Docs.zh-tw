---
title: "&gt;&gt;= Operator (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.>>="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "assignment statements, compound"
  - "statements [Visual Basic], compound assignment"
  - "operator >>= [Visual Basic]"
  - "compound assignment statements"
  - ">>= operator [Visual Basic]"
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &gt;&gt;= Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

執行變數或屬性值上的算術右移位，並將結果指派回該變數或屬性。  
  
## 語法  
  
```  
  
variableorproperty >>= amount  
```  
  
## 組件  
 `variableorproperty`  
 必要項。  整數類資料型別 \(Integral Type\) \(`SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long` 或 `ULong`\) 的變數或屬性。  
  
 `amount`  
 必要項。  擴展為 `Integer` 資料型別的數值運算式。  
  
## 備註  
 位於 `>>=` 運算子左邊的項目可以是簡單的純量 \(Scalar\) 變數、屬性或陣列元素。  變數或屬性不能為 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。  
  
 `>>=`運算子會先在變數或屬性的值上執行算術右移位。   然後，運算子會將該運算的結果指派給變數或屬性。  
  
 算術移位不是循環型，這表示位元從結果某端移出後，就不會再從另一端進入。  在算術右移位中，位元移動的範圍若超過最右邊的位元位置會予以捨棄，而且最左邊的位元會傳播到左方空出的位元位置中。  這表示若 `variableorproperty` 有負值，空出的位置就會設成 1。  若 `variableorproperty` 是正值，或其資料型別是不帶正負號的型別，則空出的位置就會設成零。  
  
## 多載化  
 [\>\> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) 可以「*多載*」，也就是，當運算元具備類別或結構的類型時，該類別或結構就可以重新定義其行為。  多載 `>>` 運算子會影響 `>>=` 運算子的行為。  如果您的程式碼在多載 `>>` 之類別或結構上使用 `>>=`，就一定要先了解其重新定義的行為。  如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## 範例  
 下列範例會使用 `>>=` 運算子，依指定數量將 `Integer` 變數的位元模式向右移動，並將結果指派回該變數。  
  
 [!code-vb[VbVbalrOperators#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-assignment-operator_1.vb)]  
  
## 請參閱  
 [\>\> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md)   
 [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Bit Shift Operators](../../../visual-basic/language-reference/operators/bit-shift-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)