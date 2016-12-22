---
title: "Comparison Operators in Visual Basic | Microsoft Docs"
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
  - "comparison operators, comparing strings"
  - "comparison operators, comparing objects"
  - "strings [Visual Basic], comparing"
  - "comparison operators"
  - "string comparison [Visual Basic], operators"
  - "objects [Visual Basic], comparing"
  - "numbers, comparing"
  - "Visual Basic code, operators"
  - "string comparison [Visual Basic]"
  - "numeric values, comparing"
  - "comparison operators, comparing numeric values"
  - "operators [Visual Basic], comparison"
ms.assetid: 0b570339-5407-474f-8421-e183a8b303ee
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Comparison Operators in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

比較運算子會比較兩個運算式，然後傳回 `Boolean` 值，該值代表它們之值的關係。  包括用於比較數值的運算子、用於比較字串的運算子及用於比較物件的運算子。  此處將討論這三種運算子。  
  
## 比較數值  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 會使用六個數值比較運算子，進行數值比較。  每一個運算子都會利用兩個可求出數值的運算式當做運算元。  下表會列出這六個運算子，並顯示每個運算子的範例。  
  
|運算子|測試的條件|範例|  
|---------|-----------|--------|  
|`=` \(相等\)|第一個運算式的值是否等於第二個運算式的值？|`23`   `=`   `33    ' False`<br /><br /> `23`   `=`   `23    ' True`<br /><br /> `23`   `=`   `12    ' False`|  
|`<>` \(不等\)|第一個運算式的值是否不等於第二個運算式的值？|`23`   `<>`   `33    ' True`<br /><br /> `23`   `<>`   `23    ' False`<br /><br /> `23`   `<>`   `12    ' True`|  
|`<` \(小於\)|第一個運算式的值是否小於第二個運算式的值？|`23`   `<`   `33    ' True`<br /><br /> `23`   `<`   `23    ' False`<br /><br /> `23`   `<`   `12    ' False`|  
|`>` \(大於\)|第一個運算式的值是否大於第二個運算式的值？|`23`   `>`   `33    ' False`<br /><br /> `23`   `>`   `23    ' False`<br /><br /> `23`   `>`   `12    ' True`|  
|`<=` \(小於或等於\)|第一個運算式的值是否小於或等於第二個運算式的值？|`23`   `<=`   `33    ' True`<br /><br /> `23`   `<=`   `23    ' True`<br /><br /> `23`   `<=`   `12    ' False`|  
|`>=` \(大於或等於\)|第一個運算式的值是否大於或等於第二個運算式的值？|`23`   `>=`   `33    ' False`<br /><br /> `23`   `>=`   `23    ' True`<br /><br /> `23`   `>=`   `12    ' True`|  
  
## 比較字串  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 會使用 [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md) 以及數值比較運算，進行字串的比較。  `Like` 運算子可讓您指定樣式。  然後，根據此樣式比較字串，如果此字串符合，則結果為 `True`。  否則，產生結果是 `False`。  數值運算子可讓您依據 `String` 值的排序次序進行比較，如下列範例所示。  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 因為第一個字串中的第一個字元 \(數字 7\) 會排在第二個字串中的第一個字元 \(數字 9\) 之前，所以上面的範例結果為 `True`。  如果第一個字元相等，則比較會繼續比較兩個字串中的下一個字元，以此類推。  您也可以使用相等運算子來測試字串是否相等，如下列範例所示。  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 如果某字串是另一個字串的前置字元，例如 "aa" 及 "aaa"，則會將較長的字串視為大於較短的字串。  下列範例將說明這點。  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 排序次序會根據 `Option Compare` 的設定，以二進位比較或文字比較的方式進行。  如需詳細資訊，請參閱 [Option Compare Statement](../../../../visual-basic/language-reference/statements/option-compare-statement.md)。  
  
## 比較物件  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 會以 [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) 和 [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md)比較兩個物件參考變數。  您可以使用這兩個運算子的其中一個，判斷這兩個參考變數是否會參考相同的物件執行個體。  下列範例將說明這點。  
  
 [!code-vb[VbVbalrOperators#65](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 在先前範例中，因為 `x Is y` 中的這兩個變數都會參考相同的執行個體，所以會評估為 `True`。  請將此結果與下列範例進行比較。  
  
 [!code-vb[VbVbalrOperators#66](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_2.vb)]  
  
 在先前範例中，雖然 `x Is y` 會因變數都參考相同類型的物件而評估為 `False`，但它們所參考的是該類型的不同執行個體。  
  
 當您想測試兩個不是指向相同執行個體的物件時，`IsNot` 運算子可讓您免除同時使用 `Not` 和 `Is` 語法上的不便之處。  下列範例將說明這點。  
  
 [!code-vb[VbVbalrOperators#67](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_3.vb)]  
  
 在先前範例中，`If a IsNot b` 會等於 `If Not a Is b`。  
  
### 比較物件型別  
 您可以使用 `TypeOf`...`Is` 運算式，測試物件是否屬於特定型別。  語法如下：  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 當 `typename` 指定介面型別時，如果物件實作介面型別，則 `TypeOf`...`Is` 運算式便會傳回 `True`。  當 `typename` 是類別型別時，如果物件是指定類別的執行個體或是自指定類別衍生之類別的執行個體，運算式便會傳回 `True`。  下列範例將說明這點。  
  
 [!code-vb[VbVbalrOperators#68](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_4.vb)]  
  
 在先前範例中，`TypeOf x Is Control` 運算式會評估為 `True`，是因為 `x` 的型別為 `Button`，而此型別是繼承自 `Control`。  
  
 如需詳細資訊，請參閱 [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md)。  
  
## 請參閱  
 [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [Comparison Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Operators](../../../../visual-basic/language-reference/operators/index.md)   
 [Arithmetic Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Concatenation Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)