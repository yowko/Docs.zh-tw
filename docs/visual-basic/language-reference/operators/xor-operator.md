---
title: "Xor Operator (Visual Basic) | Microsoft Docs"
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
  - "vb.Xor"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "exclusive OR operator"
  - "logical exclusion"
  - "operators [Visual Basic], exclusive or"
  - "exclusion operator"
  - "operators [Visual Basic], bitwise"
  - "bitwise operators, XOR operator"
  - "Xor operator [Visual Basic]"
  - "Xor keyword"
  - "bitwise comparison"
ms.assetid: 036000a9-3934-4e7f-a9d0-a816de3d84a6
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Xor Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

對兩個 `Boolean` 運算式執行邏輯互斥 \(Logical Exclusion\)，或對兩個數值運算式執行位元互斥 \(Bitwise Exclusion\)。  
  
## 語法  
  
```  
  
result = expression1 Xor expression2  
```  
  
## 組件  
 `result`  
 必要項。  任何 `Boolean` 或數值變數。  若為布林比較，`result` 是兩個 `Boolean` 值的邏輯互斥 \(獨佔邏輯分離\)。  若為位元作業，`result` 為數值，代表兩個數值位元模式的位元排除 \(獨佔位元分離\)。  
  
 `expression1`  
 必要項。  任何 `Boolean` 或數值運算式。  
  
 `expression2`  
 必要項。  任何 `Boolean` 或數值運算式。  
  
## 備註  
 對於 Boolean 比較而言，只有在 `expression1` 和 `expression2` 中只有一個評估為 `True` 時，`result` 才會是 `True`。  也就是說，只有 `expression1` 和 `expression2` 評估為相反的 `Boolean` 值時才會如此。  下表說明如何決定 `result`。  
  
|如果 `expression1` 為|且 `expression2` 是|`result` 的值為|  
|------------------------|-----------------------|------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  在布林比較中，`Xor` 運算子一律會評估兩個運算式，其中可以包括進行程序呼叫。  沒有 `Xor` 的最少運算對應函式，因為結果一律取決於這兩個運算元。  如需「*最少運算*」邏輯運算子的相關資訊，請參閱 [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md)和 [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md)。  
  
 就位元運算而論，`Xor` 運算子會對兩個數值運算式中同位置的位元執行位元比較，並依據下表來設定 `result` 中的對應位元。  
  
|如果 `expression1` 中的位元是|並且 `expression2` 中的位元是|`result` 中的位元是|  
|----------------------------|----------------------------|--------------------|  
|1|1|0|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
>  由於邏輯和位元運算子的優先順序低於其他算術和關係運算子，所以任何位元運算都必須加上括號，以確保執行結果的正確性。  
  
 例如，5 `Xor` 3 等於 6。  要知道為什麼，請將 5 和 3 轉換成二進位表示法 101 和 011，  然後使用前面的表格得出 101 Xor 011 等於 110，正是十進位數字 6 的二進位表示法。  
  
## 資料型別  
 如果運算元是以一個 `Boolean` 運算式和一個數字運算式組成，則 Visual Basic 會將 `Boolean` 運算式轉換成數值 \(\-1 代表 `True` 而 0 代表 `False`\)，並執行位元運算。  
  
 若為 `Boolean` 比較，則結果的資料型別為 `Boolean`。  進行位元 \(Bitwise\) 比較時，結果資料型別會是數字型别，適用於 `expression1` 和 `expression2` 的資料型別。  請參閱[Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)中的「關係和位元比較」表。  
  
## 多載化  
 `Xor` 運算子可以「*多載*」，也就是，當運算元具備類別或結構的類型時，該類別或結構就可以重新定義其行為。  如果您的程式碼在這種類別或結構上使用此運算子，請確定了解其重新定義的行為。  如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## 範例  
 下列範例會使用 `Xor` 運算子，對兩個運算式執行邏輯互斥 \(獨佔邏輯分離\)。  結果是代表兩個運算式中是否只有一個為 `True` 的 `Boolean` 值。  
  
 [!code-vb[VbVbalrOperators#40](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_1.vb)]  
  
 前一個範例分別產生 `False`、`True` 和 `False` 的結果。  
  
## 範例  
 下列範例會使用 `Xor` 運算子，對兩個數值運算式的個別位元執行邏輯互斥 \(獨佔邏輯分離\)。  如果運算元中的對應位元只有其中一個是設為 1，則會將結果模式中的對應位元設為 1。  
  
 [!code-vb[VbVbalrOperators#41](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_2.vb)]  
  
 前一個範例分別產生 2、12 和 14 的結果。  
  
## 請參閱  
 [Logical\/Bitwise Operators](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)