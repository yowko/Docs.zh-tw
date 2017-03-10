---
title: "Data Types of Operator Results (Visual Basic) | Microsoft Docs"
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
  - "data types [Visual Basic], operator result data types"
  - "result data types"
  - "operator result data types"
  - "operators [Visual Basic], data types"
  - "data types [Visual Basic], ranges"
  - "operators [Visual Basic], result data types"
ms.assetid: 9d524533-e1a1-4aa8-b1b8-622068173d06
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 27
---
# Data Types of Operator Results (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 可根據運算元的資料型別，決定運算的結果資料型別。  在某些情況下，這可能是範圍大於任一運算元範圍的資料型別。  
  
## 資料型別範圍  
 相關資料型別的範圍，順序從最小到最大，如下所示：  
  
-   [Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)：兩個可能值  
  
-   [SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md) 和 [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md)：256 個可能的整數值  
  
-   [Short](../../../visual-basic/language-reference/data-types/short-data-type.md) 和 [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)：65,536 \(6.5...E\+4\) 個可能的整數值  
  
-   [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md) 和 [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)：4,294,967,296 \(4.2...E\+9\) 個可能的整數值  
  
-   [Long](../../../visual-basic/language-reference/data-types/long-data-type.md) 和 [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)：18,446,744,073,709,551,615 \(1.8...E\+19\) 個可能的整數值  
  
-   [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)：1.5...E\+29 個可能的整數值，最大範圍 7.9...E\+28 \(絕對值\)  
  
-   [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)：最大範圍 3.4...E\+38 \(絕對值\)  
  
-   [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)：最大範圍 1.7...E\+308 \(絕對值\)  
  
 如需 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 資料型別的詳細資訊，請參閱[Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)。  
  
 若運算元評估為 [Nothing](../../../visual-basic/language-reference/nothing.md)，則 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 的算術運算子會將其視為零。  
  
## 十進位運算  
 請注意，[Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) 資料型別不是浮點數或整數。  
  
 如果 `+`、`–`、`*`、`/` 或 `Mod` 運算的任一運算元是 `Decimal`，且其他運算元不是 `Single` 或 `Double`，則 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會將其他運算元擴展為 `Decimal`。  它會執行 `Decimal` 中的運算，且結果資料型別是 `Decimal`。  
  
## 浮點數運算  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 可在 [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) 中執行大部分的浮點數運算，它對此類運算是最有效率的資料型別。  然而，若一個運算元是 [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)，且另一個運算元不是 `Double`，則 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會在 `Single` 中執行運算。  它可以在運算之前，視需要將每一個運算元擴展為適當的資料型別，且結果將會有該資料型別。  
  
### \/ 和 ^ 運算子  
 `/` 運算子的定義，只會為 [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)、[Single](../../../visual-basic/language-reference/data-types/single-data-type.md) 和 [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) 資料型別進行。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會在進行作業之前，將每個運算元視需要加寬為適當的資料型別，而且結果也會具有該資料型別。  
  
 下表顯示 `/` 運算子的結果資料型別。  請注意，這個資料表是對稱式；對於指定的運算元資料型別組合來說，不管運算元的順序為何，其結果資料型別都是相同的。  
  
||||||  
|-|-|-|-|-|  
||`Decimal`|`Single`|`Double`|任何整數型別|  
|`Decimal`|Decimal|Single|Double|Decimal|  
|`Single`|Single|Single|Double|Single|  
|`Double`|Double|Double|Double|Double|  
|任何整數型別|Decimal|Single|Double|Double|  
  
 `^` 運算子的定義只會為 `Double` 資料型別進行。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會在運算之前，將每個運算元視需要加寬為 `Double`，而且結果資料型別一定都會是 `Double`。  
  
## 整數運算  
 整數運算的結果資料型別取決於運算元的資料型別。  一般而言，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 可使用下列原則來決定結果資料型別：  
  
-   如果二元運算子的兩個運算元都有相同的資料型別，所產生的結果會有該資料型別。  一個例外狀況 \(Exception\) 是 `Boolean`，會強制轉換為 `Short`。  
  
-   若不帶正負號的運算元會與帶正負號的運算元搭配使用，則結果將有帶正負號的型別，其範圍至少與其中一個運算元一樣大。  
  
-   否則，結果通常會具有兩個運算元資料型別中的較大者。  
  
 請注意，結果資料型別可能不會與任一運算元資料型別相同。  
  
> [!NOTE]
>  結果資料型別不一定總是夠大，因此可能無法保留運算所得的所有可能值。  若值對結果資料型別而言太大，則可能發生 <xref:System.OverflowException> 例外狀況。  
  
### 一元運算子 \+ 和 –  
 下表顯示 `+` 和 `–` 這兩個一元運算子的結果資料型別。  
  
|||||||||||  
|-|-|-|-|-|-|-|-|-|-|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|一元 `+`|Short|SByte|Byte|Short|UShort|Integer|UInteger|Long|ULong|  
|一元 `–`|Short|SByte|Short|Short|Integer|Integer|Long|Long|Decimal|  
  
### \<\< 和 \>\> 運算子  
 下表顯示兩個位元移位運算子 `<<` 和 `>>` 的結果資料型別。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會在其左運算元上，將每一個位元位移運算子視為一元運算子 \(要位移的位元模式\)。  
  
|||||||||||  
|-|-|-|-|-|-|-|-|-|-|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|Short|SByte|Byte|Short|UShort|Integer|UInteger|Long|ULong|  
  
 如果左運算元是 `Decimal`、`Single`、`Double` 或 `String`，則 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會在運算之前，嘗試將其轉換為 `Long`，且結果資料型別是 `Long`。  右運算元 \(要位移的位元位置數目\) 必須為 `Integer` 或擴展為 `Integer` 的型別。  
  
### 二元運算子 \+、–、\* 和 Mod  
 下表顯示二元運算子 `+` 和 `–` 的結果資料型別，以及 `*` 和 `Mod` 運算子的結果資料型別。  請注意，這個資料表是對稱式；對於指定的運算元資料型別組合來說，不管運算元的順序為何，其結果資料型別都是相同的。  
  
|||||||||||  
|-|-|-|-|-|-|-|-|-|-|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Short|SByte|Short|Short|Integer|Integer|Long|Long|Decimal|  
|`SByte`|SByte|SByte|Short|Short|Integer|Integer|Long|Long|Decimal|  
|`Byte`|Short|Short|Byte|Short|UShort|Integer|UInteger|Long|ULong|  
|`Short`|Short|Short|Short|Short|Integer|Integer|Long|Long|Decimal|  
|`UShort`|Integer|Integer|UShort|Integer|UShort|Integer|UInteger|Long|ULong|  
|`Integer`|Integer|Integer|Integer|Integer|Integer|Integer|Long|Long|Decimal|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Decimal|  
|`ULong`|Decimal|Decimal|ULong|Decimal|ULong|Decimal|ULong|Decimal|ULong|  
  
### \\ 運算子  
 下表顯示 `\` 運算子的結果資料型別。  請注意，這個資料表是對稱式；對於指定的運算元資料型別組合來說，不管運算元的順序為何，其結果資料型別都是相同的。  
  
|||||||||||  
|-|-|-|-|-|-|-|-|-|-|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Short|SByte|Short|Short|Integer|Integer|Long|Long|Long|  
|`SByte`|SByte|SByte|Short|Short|Integer|Integer|Long|Long|Long|  
|`Byte`|Short|Short|Byte|Short|UShort|Integer|UInteger|Long|ULong|  
|`Short`|Short|Short|Short|Short|Integer|Integer|Long|Long|Long|  
|`UShort`|Integer|Integer|UShort|Integer|UShort|Integer|UInteger|Long|ULong|  
|`Integer`|Integer|Integer|Integer|Integer|Integer|Integer|Long|Long|Long|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Long|  
|`ULong`|Long|Long|ULong|Long|ULong|Long|ULong|Long|ULong|  
  
 如果 `\` 運算子的其中一個運算元是 [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)、[Single](../../../visual-basic/language-reference/data-types/single-data-type.md) 或 [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)，則 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 也會在運算之前，嘗試將其轉換成 [Long](../../../visual-basic/language-reference/data-types/long-data-type.md)，且結果資料型別是 `Long`。  
  
## 關係和位元比較  
 關係運算的結果資料型別 \(`=`、`<>`、`<`、`>`、`<=`、`>=`\) 一律是 `Boolean`[Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md)。  這種情況也適用於 `Boolean` 運算元的邏輯運算 \(`And`、`AndAlso`、`Not`、`Or`、`OrElse`、`Xor`\)。  
  
 位元邏輯運算的結果資料型別取決於運算元的資料型別。  請注意，`AndAlso` 和 `OrElse` 只會針對 `Boolean` 定義，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會在執行運算之前，視需要將每一個運算元轉換成 `Boolean`。  
  
### \=、\<\>、\<、\>、\<\= 和 \>\= 運算子  
 若兩個運算元都是 `Boolean`，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會將 `True` 視為小於 `False`。  如果數字型別是與 `String` 比較，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會在運算之前，嘗試將 `String` 轉換成 `Double`。  `Char` 或 `Date` 運算元只能與相同資料型別的另一個運算元比較。  結果資料型別一律是 `Boolean`。  
  
### 位元 NOT 運算子  
 下表顯示位元 `Not` 運算子的結果資料型別。  
  
|||||||||||  
|-|-|-|-|-|-|-|-|-|-|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|Boolean|SByte|Byte|Short|UShort|Integer|UInteger|Long|ULong|  
  
 如果運算元是 `Decimal`、`Single`、`Double` 或 `String`，則 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會在運算之前，嘗試將其轉換為 `Long`，且結果資料型別是 `Long`。  
  
### 位元 And、Or 和 Xor 運算子  
 下表顯示位元 `And`、`Or` 和 `Xor` 運算子的結果資料型別。  請注意，這個資料表是對稱式；對於指定的運算元資料型別組合來說，不管運算元的順序為何，其結果資料型別都是相同的。  
  
|||||||||||  
|-|-|-|-|-|-|-|-|-|-|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Boolean|SByte|Short|Short|Integer|Integer|Long|Long|Long|  
|`SByte`|SByte|SByte|Short|Short|Integer|Integer|Long|Long|Long|  
|`Byte`|Short|Short|Byte|Short|UShort|Integer|UInteger|Long|ULong|  
|`Short`|Short|Short|Short|Short|Integer|Integer|Long|Long|Long|  
|`UShort`|Integer|Integer|UShort|Integer|UShort|Integer|UInteger|Long|ULong|  
|`Integer`|Integer|Integer|Integer|Integer|Integer|Integer|Long|Long|Long|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Long|  
|`ULong`|Long|Long|ULong|Long|ULong|Long|ULong|Long|ULong|  
  
 如果運算元是 `Decimal`、`Single`、`Double` 或 `String`，則 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會在運算之前，嘗試將其轉換為 `Long`，且將得到相同的結果資料型別，如同該運算元已經是 `Long`。  
  
## 雜項運算子  
 `&` 運算子的定義只會為 `String` 運算元的串連進行。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會在作業之前，將每個運算元視需要轉換為 `String`，而且結果資料型別一定都會是 `String`。  基於 `&` 運算子的目的，會將轉換至 `String` 的所有動作視為擴展，即使 `Option Strict` 是 `On` 也一樣。  
  
 `Is` 和 `IsNot` 運算子需要兩個當做參考型別 \(Reference Type\) 的運算元。  `TypeOf`...`Is` 運算式會要求第一個運算元必須是參考型別，第二個則是資料型別的名稱。  在所有狀況中，結果資料型別是 `Boolean`。  
  
 `Like` 運算子的定義只會為 `String` 運算元的模式比對進行。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會嘗試在運算前，將每個運算元視需要轉換為 `String`。  結果資料型別一律是 `Boolean`。  
  
## 請參閱  
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Comparison Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Operators](../../../visual-basic/language-reference/operators/index.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)