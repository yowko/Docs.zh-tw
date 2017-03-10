---
title: "How to: Match a String against a Pattern (Visual Basic) | Microsoft Docs"
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
  - "comparison operators, comparing strings"
  - "pattern matching"
  - "strings [Visual Basic], comparing"
  - "string comparison [Visual Basic], operators"
  - "Visual Basic code, operators"
  - "pattern matching, string comparison"
  - "string comparison [Visual Basic]"
  - "Like operator [Visual Basic], pattern matching"
  - "pattern matching, empty strings"
  - "operators [Visual Basic], comparison"
ms.assetid: 19a83804-b5af-4739-928b-ac93e64e457f
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# How to: Match a String against a Pattern (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

如果您想找出[String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) 的運算式是否符合樣式，可以使用 [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md)。  
  
 `Like` 會採用兩個運算元。  左運算元為字串運算式，右運算元則為包含用於比對之樣式的字串。  `Like` 會傳回 `Boolean` 値，表示字串運算式是否符合模式。  
  
 您可以針對特定字元、萬用字元、字元清單或字元範圍，比對字串運算式中的每個字元。  樣式比對字串中的規格位置，會對應到要在字串運算式中比對的字元位置。  
  
### 根據特定字元比對字串運算式中的字元  
  
-   將該特定字元直接放在樣式比對字串中。  某些特殊字元必須放在方括弧 \(`[ ]`\) 中。  如需詳細資訊，請參閱 [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md)。  
  
     下列範例會測試 `myString` 是否恰好由單一字元 `H` 所組成。  
  
     [!code-vb[VbVbalrOperators#70](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/how-to-match-a-string-ag_1.vb)]  
  
### 根據萬用字元比對字串運算式中的字元  
  
-   將問號 \(`?`\) 放在樣式比對字串中。  在這個位置的任何有效字元都能使比對成功。  
  
     下列範例會測試 `myString` 是否包含單一字元 `W`，且此字元後面恰好緊接著兩個字元 \(這兩個字元可以是任何值\)。  
  
     [!code-vb[VbVbalrOperators#71](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/how-to-match-a-string-ag_2.vb)]  
  
### 根據字元清單比對字串運算式中的字元  
  
-   將方括弧 \(`[ ]`\) 放在樣式比對字串中，並將字元清單放在方括弧內。  請勿以逗號或任何其他分隔符號隔開字元。  清單中的任何單一字元，都能使比對成功。  
  
     下列範例會測試 `myString` 是否包含任何有效字元，且此字元後面恰好緊接著 `A`、`C` 或 `E` 其中一個字元。  
  
     [!code-vb[VbVbalrOperators#72](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/how-to-match-a-string-ag_3.vb)]  
  
     請注意，這項比對必須區分大小寫。  
  
### 根據字元範圍比對字串運算式中的字元  
  
-   將方括弧 \(`[ ]`\) 放在樣式比對字串中，並將範圍內的最低和最高字元放在方括弧內，以短破折號 \(`–`\) 分隔。  範圍內的任何單一字元都能使比對成功。  
  
     下列範例會測試 `myString` 是否包含字元 `num`，此字元後面恰好緊接著 `i`、`j`、`k`、`l`、`m` 或 `n` 其中一個字元。  
  
     [!code-vb[VbVbalrOperators#73](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/how-to-match-a-string-ag_4.vb)]  
  
     請注意，這項比對必須區分大小寫。  
  
## 比對空字串  
 `Like` 會將序列 \(Sequence\) `[]` 視為長度為零的字串 \(`""`\)。  您可以使用 `[]` 測試整個字串運算式是否為空的，但無法用於測試字串運算式中的特定位置是否為空的。  如果空位置是您需測試的其中一個選項，則可以多次使用 `Like`。  
  
#### 若要根據字元清單或無字元比對字串運算式中的字元  
  
1.  在相同的字串運算式上呼叫 `Like` 運算子兩次，並以 [Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md) 或 [OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md)連接這兩次呼叫。  
  
2.  在第一個 `Like` 子句的樣式比對字串中，納入字元清單並放在方括弧 \(`[ ]`\) 中。  
  
3.  在第二個 `Like` 子句的樣式比對字串中，請勿在要比對的位置放入任何字元。  
  
     下列範例會測試七位數的電話號碼 `phoneNum`，是否剛好為三位數字，之後緊接著空格、短破折號 \(`–`\)、句號 \(`.`\) 或全然沒有字元，再緊接著的剛好是四位數字。  
  
     [!code-vb[VbVbalrOperators#74](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/how-to-match-a-string-ag_5.vb)]  
  
## 請參閱  
 [Comparison Operators](../../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Operators and Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md)   
 [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md)