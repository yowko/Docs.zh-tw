---
title: "Mod 運算子 (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Mod"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "餘數 (Mod 運算子)"
  - "除法運算子，Mod 運算子"
  - "模數運算子，Visual Basic"
  - "Mod 運算子 [Visual Basic]"
  - "運算子 [Visual Basic]，除法"
  - "算術運算子，MOD"
  - "數學運算子"
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# Mod 運算子 (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

將兩個數字相除，只傳回餘數。  
  
## 語法  
  
```  
  
number1 Mod number2  
```  
  
## 組件  
 `number1`  
 必要項。  任何數值運算式。  
  
 `number2`  
 必要項。  任何數值運算式。  
  
## 支援類型  
 所有數字型別 \(Numeric Type\)。  這包括不帶正負號和浮點型別，以及 `Decimal`。  
  
## 結果  
 結果是 `number1` 除以 `number2` 後所留的餘數。  例如，運算式 `14 Mod 4` 會評估為 2。  
  
## 備註  
 如果 `number1` 或 `number2` 是浮點數值，就會傳回除法運算的浮點數餘數。  結果的資料型別是可保留所有可能值的最小資料型別，這些可能值是由 `number1` 和 `number2` 之資料型別的除法運算所產生。  
  
 如果 `number1` 或 `number2` 評估為 [Nothing](../../../visual-basic/language-reference/nothing.md)，即視為零。  
  
 相關運算子包括下列幾項：  
  
-   [\\ Operator](../../../visual-basic/language-reference/operators/integer-division-operator.md) 會傳回除法運算的整數商數。  例如，運算式 `14 \ 4` 會評估為 3。  
  
-   [\/ Operator](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) 會以浮點數值傳回完整商數，包括餘數。  例如，運算式 `14 / 4` 會評估為 3.5。  
  
## 嘗試以零為除數  
 如果 `number2` 評估為零，則 `Mod` 運算子的行為會視運算元的資料型別而定。  整數類除法會擲回 <xref:System.DivideByZeroException> 例外狀況。  浮點數除法會傳回 <xref:System.Double.NaN>。  
  
## 對等公式  
 運算式 `a Mod b` 等於下列公式：  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## 浮點數非精度表示  
 使用浮點數值 \(Floating\-Point Number\) 時，請記住它們在記憶體中不一定都會有精確的表示。  這樣可能會因為某些作業，例如值比較和 `Mod` 運算子，而導致無法預期的結果。  如需詳細資訊，請參閱[Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。  
  
## 多載化  
 `Mod` 運算子可以「*多載*」，這表示類別或結構可以重新定義其行為。  如果您的程式碼套用 `Mod` 到包含多載之類別或結構的執行個體，請確定您了解它重新定義的行為。  如需詳細資訊，請參閱[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## 範例  
 下列範例會使用 `Mod` 運算子，將兩數相除並只傳回餘數。  如果任一數值是浮點數值，則結果是代表餘數的浮點數值。  
  
 [!code-vb[VbVbalrOperators#31](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_1.vb)]  
  
## 範例  
 下列範例示範浮點數運算元的潛在不精確情況。  在第一個陳述式中，運算元是 `Double`，而 0.2 是預存值為 0.20000000000000001 的無限重複二進位小數。  在第二個陳述式中，常值型別字元 `D` 會將兩個運算元強制為 `Decimal`，而 0.2 具有精確表示。  
  
 [!code-vb[VbVbalrOperators#32](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_2.vb)]  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [\\ Operator](../../../visual-basic/language-reference/operators/integer-division-operator.md)