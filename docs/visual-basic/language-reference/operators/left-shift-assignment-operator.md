---
title: "&lt;&lt;= Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.<<="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "operator <<="
  - "assignment statements, compound"
  - "<<= operator [Visual Basic]"
  - "statements [Visual Basic], compound assignment"
  - "operator<<="
  - "compound assignment statements"
ms.assetid: 8ad26613-faff-4e2f-89ee-63feee33bfda
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# &lt;&lt;= Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

執行變數或屬性 \(Property\) 值上的算術左移位 \(Shift\)，並將結果指派回該變數或屬性。  
  
## 語法  
  
```  
  
variableorproperty <<= amount  
```  
  
## 組件  
 `variableorproperty`  
 必要項。  整數類資料型別 \(Integral Type\) \(`SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long` 或 `ULong`\) 的變數或屬性。  
  
 `amount`  
 必要項。  擴展為 `Integer` 資料型別的數值運算式。  
  
## 備註  
 位於 `<<=` 運算子左邊的項目可以是簡單的純量 \(Scalar\) 變數、屬性或陣列元素。  變數或屬性不能為 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。  
  
 `<<=`運算子會先執行的算術左移位變數或屬性的值。   然後，運算子會將該運算的結果指派給該變數或屬性。  
  
 算術移位不是循環型，這表示位元從結果某端移出後，就不會再從另一端進入。  在算術左移位中，位元移動的範圍若超過結果資料型別會予以捨棄，而且右方空出的位元位置會設定成零。  
  
## 多載化  
 [\<\< Operator](../../../visual-basic/language-reference/operators/left-shift-operator.md) 可以「*多載*」，也就是，當運算元具備類別或結構的類型時，該類別或結構就可以重新定義其行為。  多載 `<<` 運算子會影響 `<<=` 運算子的行為。  如果您的程式碼在多載 `<<` 之類別或結構上使用 `<<=`，就一定要先了解其重新定義的行為。  如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## 範例  
 下列範例會使用 `<<=` 運算子，依指定數量將 `Integer` 變數的位元模式向左移動，並將結果指派回該變數。  
  
 [!code-vb[VbVbalrOperators#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-assignment-operator_1.vb)]  
  
## 請參閱  
 [\<\< Operator](../../../visual-basic/language-reference/operators/left-shift-operator.md)   
 [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Bit Shift Operators](../../../visual-basic/language-reference/operators/bit-shift-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)