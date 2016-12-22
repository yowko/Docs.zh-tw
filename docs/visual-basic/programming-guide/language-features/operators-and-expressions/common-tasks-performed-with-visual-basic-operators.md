---
title: "Common Tasks Performed with Visual Basic Operators | Microsoft Docs"
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
  - "operators [Visual Basic], logical"
  - "operators [Visual Basic], string concatenation"
  - "operators [Visual Basic], bitwise"
  - "operators [Visual Basic], bit-shift"
  - "operators [Visual Basic], arithmetic"
  - "operators [Visual Basic], string comparison"
  - "operators [Visual Basic], concatenation"
  - "Visual Basic code, operators"
  - "operators [Visual Basic], comparison"
  - "operators [Visual Basic], short-circuiting logical"
ms.assetid: d181afe5-fafa-460f-a13b-81203f6f4587
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Common Tasks Performed with Visual Basic Operators
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

運算子會執行許多一般工作，這些工作會涉及一或多個稱為「*運算元*」\(Operand\) 的運算式。  
  
## 算術和位元移位工作  
 下表會彙總可用的算術和位元移位作業。  
  
|||  
|-|-|  
|若要|請參閱|  
|將兩個數值相加|[\+ Operator](../../../../visual-basic/language-reference/operators/addition-operator.md)|  
|將兩個數值相減|[\- Operator](../../../../visual-basic/language-reference/operators/subtraction-operator.md)|  
|改變數值的正負號|[\- Operator](../../../../visual-basic/language-reference/operators/subtraction-operator.md)|  
|將兩個數值相乘|[\* Operator](../../../../visual-basic/language-reference/operators/multiplication-operator.md)|  
|將兩個數值相除|[\/ Operator](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md)|  
|尋找兩個數值相除後的商數 \(沒有餘數\)|[\\ Operator](../../../../visual-basic/language-reference/operators/integer-division-operator.md)|  
|尋找兩個數值相除後的餘數 \(沒有商數\)|[Mod 運算子](../../../../visual-basic/language-reference/operators/mod-operator.md)|  
|將某個數值提高為另一個數值的次方|[^ Operator](../../../../visual-basic/language-reference/operators/exponentiation-operator.md)|  
|將數值的位元模式移位至左邊|[\<\< Operator](../Topic/%3C%3C%20Operator%20\(Visual%20Basic\).md)|  
|將數值的位元模式移位至右邊|[\>\> Operator](../../../../visual-basic/language-reference/operators/right-shift-operator.md)|  
  
## 比較工作  
 下表會彙總可用的比較作業。  
  
|||  
|-|-|  
|若要|請參閱|  
|判斷兩個值是否相等|`=` 運算子 \([Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)\)|  
|判斷兩個值是否不相等|`<>` 運算子 \([Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)\)|  
|判斷某個值是否小於另一個值|`<` 運算子 \([Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)\)|  
|判斷某個值是否大於另一個值|`>` 運算子 \([Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)\)|  
|判斷某個值是否小於或等於另一個值|`<=` 運算子 \([Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)\)|  
|判斷某個值是否大於或等於另一個值|`>=` 運算子 \([Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)\)|  
|判斷兩個物件變數是否參考相同的物件執行個體 \(Instance\)|[Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md)|  
|判斷兩個物件變數是否參考不同的物件執行個體|[IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md)|  
|判斷物件是否具有特定型別|[TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md)|  
  
## 串連工作  
 下表會彙總可用的串連作業。  
  
|||  
|-|-|  
|若要|請參閱|  
|將多個字串聯結 \(Join\) 成單一字串|`&` 運算子 \([Concatenation Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)\)|  
|聯結數值與字串值|`+` 運算子 \([Concatenation Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)\)|  
  
## 邏輯和位元工作  
 下表會彙總可用的邏輯和位元運算。  
  
|||  
|-|-|  
|若要|請參閱|  
|對布林 \(Boolean\) 值執行邏輯負運算|[Not Operator](../../../../visual-basic/language-reference/operators/not-operator.md)|  
|對兩個布林值執行邏輯結合|[And Operator](../../../../visual-basic/language-reference/operators/and-operator.md)|  
|對兩個布林值執行內含的邏輯分離 \(Logical Disjunction\)|[Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md)|  
|對兩個布林值執行排除的邏輯分離|[Xor Operator](../../../../visual-basic/language-reference/operators/xor-operator.md)|  
|對兩個布林值執行最少運算 \(Short\-Circuit\) 的邏輯結合|[AndAlso Operator](../../../../visual-basic/language-reference/operators/andalso-operator.md)|  
|對兩個布林值執行最少運算內含的邏輯分離|[OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md)|  
|對兩個整數值執行逐位元的邏輯結合|[And Operator](../../../../visual-basic/language-reference/operators/and-operator.md)|  
|對兩個整數值執行逐位元的內含邏輯分離|[Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md)|  
|對兩個整數值執行逐位元的排除邏輯分離|[Xor Operator](../../../../visual-basic/language-reference/operators/xor-operator.md)|  
|對一個整數值執行逐位元的邏輯負運算|[Not Operator](../../../../visual-basic/language-reference/operators/not-operator.md)|  
  
## 請參閱  
 [Operators and Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Operators Listed by Functionality](../../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)