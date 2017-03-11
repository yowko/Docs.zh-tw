---
title: "Decimal Data Type (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Decimal"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "literal type characters, D"
  - "trailing zeros"
  - "real numbers"
  - "trailing 0 characters"
  - "Decimal data type"
  - "D literal type character"
  - "decimals, Decimal data type"
  - "0 characters, trailing"
  - "data types [Visual Basic], assigning"
  - "decimal keyword"
  - "numbers, real"
  - "variable-precision numbers"
  - "zeros, trailing"
  - "@ identifier type character"
  - "identifier type characters, @"
ms.assetid: 1d855b45-afe2-45b0-a623-96b6f63a43d5
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# Decimal Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

保存帶正負號的 128 位元 \(16 個位元組\) 值，表示 96 位元 \(12 個位元組\) 的整數，由 10 的可變乘幂所延展。  縮放比例指定小數點右邊的位數數目，範圍從 0 到 28。  比例為 0 \(沒有小數位數\) 時，最大可能值為 \+ \/\-79,228,162,514,264,337,593,543,950,335 \(\+ \/\-7.9228162514264337593543950335E \+ 28\)。  若有 28 個小數位數，最大值是 \+\/\-7.9228162514264337593543950335，而最小且不為零的值則是 \+\/\-0.0000000000000000000000000001 \(\+\/\-1E\-28\)。  
  
## 備註  
 `Decimal` 資料型別提供了數字的最大有效位數。  它支援最多 29 個有效位數，且可表示超出 7.9228 x 10^28 的值。  它特別適合於需要大量位數，但無法容忍捨入錯誤的計算作業，例如財務。  
  
 `Decimal` 的預設值為 0。  
  
## 程式設計提示  
  
-   **精確度**，`Decimal` 不是浮點數資料型別。  `Decimal` 結構會保存二進位整數值，加上正負號位元和整數縮放比例，指定值的哪一部分是小數部分。  因為這個原因，比起浮點數型別 \(`Single` 和 `Double`\)，`Decimal` 數字在記憶體裡具有更精確的表示。  
  
-   **效能**，`Decimal` 資料型別是所有數字型別 \(Numeric Type\) 中效能最慢的資料型別。  選擇資料型別之前，應先衡量精確度和效能的重要性。  
  
-   **擴展：**，`Decimal` 資料型別會擴展至 `Single` 或 `Double`。  這表示您可以將 `Decimal` 轉換成這些型別的其中一個，而不會發生 <xref:System.OverflowException?displayProperty=fullName> 錯誤。  
  
-   **結尾的零：**，Visual Basic 不會將結尾的零儲存在 `Decimal` 常值 \(Literal\) 中。  不過，`Decimal` 變數會保留計算所得的任何結尾零。  下列範例將說明這點。  
  
    ```  
    Dim d1, d2, d3, d4 As Decimal  
    d1 = 2.375D  
    d2 = 1.625D  
    d3 = d1 + d2  
    d4 = 4.000D  
    MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &  
          ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))  
    ```  
  
     前一個範例中的 `MsgBox` 輸出如下：  
  
     d1 \= 2.375, d2 \= 1.625, d3 \= 4.000, d4 \= 4  
  
-   **型別字元。**將常值型別字元 `D` 附加到常值會強制其成為 `Decimal` 資料型別。  將識別項型別字元 `@` 附加到任何識別項，會強制其成為 `Decimal`。  
  
-   **架構型別。**在 .NET Framework 中對應的型別為 <xref:System.Decimal?displayProperty=fullName> 結構。  
  
## Range  
 您可能需要使用 `D` 型別字元，指派大的值給 `Decimal` 變數或常數。  這項需求是，因為編譯器會將常值解譯為 `Long` ，除非常值型別字元後面接著常值，，如下列範例所示。  
  
```  
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.  
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.  
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.  
```  
  
 `bigDec1` 的宣告不會造成溢位，因為指派給它的值屬於 `Long`的範圍。  `Long` 值可以指派給 `Decimal` 變數。  
  
 `bigDec2` 的宣告會產生一個溢位錯誤，因為指派給它的值為 `Long`太大。  由於這個數字常值不能先解譯為 `Long`，它不能指派給 `Decimal` 變數。  
  
 對於 `bigDec3`，常值型別字元 `D` 會強制編譯器將常值解譯為解決問題做為 `Decimal` 而不是 `Long`。  
  
## 請參閱  
 <xref:System.Decimal?displayProperty=fullName>   
 <xref:System.Decimal.%23ctor%2A?displayProperty=fullName>   
 <xref:System.Math.Round%2A?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Single Data Type](../../../visual-basic/language-reference/data-types/single-data-type.md)   
 [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)