---
title: "Operator Precedence in Visual Basic | Microsoft Docs"
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
  - "arithmetic operators, precedence"
  - "operator precedence"
  - "logical operators, precedence"
  - "operators [Visual Basic], associativity"
  - "operators [Visual Basic], resolution"
  - "associativity of operators"
  - "operators [Visual Basic], precedence"
  - "precedence, of operators"
  - "comparison operators, precedence"
  - "math operators"
  - "order of precedence"
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Operator Precedence in Visual Basic
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

當運算式中出現數個運算時，會以稱為「*運算子優先順序*」\(Operator Precedence\) 的預先決定順序來評估及解析每個運算部分。  
  
## 優先順序規則  
 當運算式含有來自於一個以上分類的運算子時，則會按照下列規則進行評估。  
  
-   算術和串連運算子優先順序如下節所述，其優先順序都高於比較運算子、邏輯運算子和位元運算子。  
  
-   所有比較運算子的優先順序都相同，且都高於邏輯和位元運算子，但低於算術和串連運算子。  
  
-   邏輯和位元運算子優先順序如下節所述，其優先順序都低於算術運算子、串連運算子和比較運算子。  
  
-   優先順序相同的運算子，是按照其在運算式中的位置由左至右評估。  
  
## 優先順序  
 運算子會按照下列優先順序進行評估：  
  
### 等候運算子  
 等候  
  
### 算術和串連運算子  
 乘冪 \(`^`\)  
  
 一元識別和反轉正負號 \(`+`、`–`\)  
  
 乘法和浮點數除法 \(`*`、`/`\)  
  
 整數相除 \(`\`\)  
  
 模數算術 \(`Mod`\)  
  
 加法和減法 \(`+`， `–`\)  
  
 字串串連 \(`&`\)  
  
 算術位元移位 \(`<<`、`>>`\)  
  
### 比較運算子  
 所有比較運算子 \(`=`、`<>`、`<`、`<=`、`>`、`>=`、`Is`、`IsNot`、`Like`、`TypeOf`...`Is`\)  
  
### 邏輯和位元運算子  
 否定 \(`Not`\)  
  
 結合 \(`And`、`AndAlso`\)  
  
 內含分離 \(`Or`、`OrElse`\)  
  
 獨佔分離 \(`Xor`\)  
  
### 註解  
 `=` 運算子只是相等比較運算子，而非指派運算子。  
  
 字串串連運算子 \(`&`\) 不是算術運算子，但其優先順序與算術運算子相同。  
  
 `Is` 和 `IsNot` 運算子是物件參考比較運算子。  它們不會比較兩個物件的值，檢查的目的只是判斷兩個物件變數是否參考同一個物件執行個體。  
  
## 順序關聯性  
 當運算式中出現優先順序相同的運算子時 \(例如乘法和除法\)，編譯器會依運算出現順序由左至右評估。  下列範例將說明這點。  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 第一個運算式會求得 96 \/ 8 的值 \(得到 12\)，然後再求得 12 \/ 4 的值 \(得到 3\)。  因為編譯器會從左至右進行 `n1` 的運算作業，所以當您明確地為 `n2` 指定該順序時，運算的結果會完全相同。  `n1` 和 `n2` 兩者的結果都是 3。  相比之下，`n3` 的結果是 48，因為括號會強制編譯器優先求得 8 \/ 4 的值。  
  
 基於這種行為，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中的運算子就稱為「*左關聯*」\(Left Associative\)。  
  
## 覆寫優先順序和關聯性  
 您可以使用括號，強制優先評估運算式的某部分。  這樣可以同時覆寫優先順序和左順序關聯性。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 必定會優先執行括號內再執行外部運算。不過，，除非您在括號中，大括號在括號內，它可以維持一般優先順序和順序關聯性。  下列範例將說明這點。  
  
```  
Dim a, b, c, d, e, f, g As Double  
a = 8.0  
b = 3.0  
c = 4.0  
d = 2.0  
e = 1.0  
f = a - b + c / d * e  
' The preceding line sets f to 7.0. Because of natural operator   
' precedence and associativity, it is exactly equivalent to the   
' following line.  
f = (a - b) + ((c / d) * e)  
' The following line overrides the natural operator precedence   
' and left associativity.  
g = (a - (b + c)) / (d * e)  
' The preceding line sets g to 0.5.  
```  
  
## 請參閱  
 [\= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md)   
 [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md)   
 [IsNot Operator](../../../visual-basic/language-reference/operators/isnot-operator.md)   
 [Like Operator](../../../visual-basic/language-reference/operators/like-operator.md)   
 [TypeOf Operator](../../../visual-basic/language-reference/operators/typeof-operator.md)   
 [Await Operator](../../../visual-basic/language-reference/operators/await-operator.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)