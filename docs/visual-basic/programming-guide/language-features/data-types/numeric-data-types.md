---
title: "Numeric Data Types (Visual Basic) | Microsoft Docs"
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
  - "integral types, Visual Basic"
  - "Short data type, numeric data types"
  - "Double data type, numeric data types"
  - "Long data type, Visual Basic numeric data types"
  - "numbers, whole"
  - "fractions"
  - "numbers"
  - "whole numbers"
  - "integer numbers"
  - "numbers, integer"
  - "fractional data types"
  - "mantissas, of fractional numbers"
  - "mantissas"
  - "data types [Visual Basic], numeric"
  - "Integer data type, numeric data types"
  - "exponent, of fractional numbers"
  - "integers"
  - "numeric data types, Visual Basic"
  - "Single data type, numeric types"
  - "Decimal data type, numeric data types"
ms.assetid: a27bd4d0-7e14-43eb-9cc4-b42eaab323c9
caps.latest.revision: 25
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 25
---
# Numeric Data Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會提供多種「*數字資料型別*」\(Numeric Data Type\) 來處理不同表示法的數字。  「*整數類*」\(Integral\) 資料型別僅用來表示整數 \(正數、負數和零\)，而「*非整數類*」\(Nonintegral\) 資料型別則可用來表示同時含有整數和分數部分的數字。  
  
 如需 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 資料型別的並存比較表，請參閱[Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)。  
  
## 整數類數字型別  
 「*整數類資料型別*」\(Integral Data Type\) 是僅表示整數，不含分數部分的型別。  
  
 「*帶正負號的*」\(Signed\) 整數類資料型別為 [SByte Data Type](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md) \(8 位元\)、[Short Data Type](../../../../visual-basic/language-reference/data-types/short-data-type.md) \(16 位元\)、[Integer Data Type](../../../../visual-basic/language-reference/data-types/integer-data-type.md) \(32 位元\) 和 [Long Data Type](../../../../visual-basic/language-reference/data-types/long-data-type.md) \(64 位元\)。  如果變數只儲存整數，而不儲存分數，則將其宣告為以上任一種型別。  
  
 「*不帶正負號的*」\(Unsigned\) 整數類資料型別為 [Byte Data Type](../../../../visual-basic/language-reference/data-types/byte-data-type.md) \(8 位元\)、[UShort Data Type](../../../../visual-basic/language-reference/data-types/ushort-data-type.md) \(16 位元\)、[UInteger Data Type](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md) \(32 位元\) 和 [ULong Data Type](../../../../visual-basic/language-reference/data-types/ulong-data-type.md) \(64 位元\)。  若變數含有二進位資料，或性質不明的資料，則將其宣告為以上任一種型別。  
  
### 效能  
 整數型別的算術運算比其他資料型別的運算來得快。  在 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中，`Integer` 和 `UInteger` 型別是處理速度最快的型別。  
  
### 最大整數  
 如果您要保留的整數比 `Integer` 資料型別所能保留的數字還大，您可以使用 `Long` 資料型別代替。  `Long` 變數可以保留 \-9,223,372,036,854,775,808 到 9,223,372,036,854,775,807 的數字。  `Long` 的運算速度較 `Integer` 稍慢一些。  
  
 如果您還需要更大的數字，則可以使用 [Decimal Data Type](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)。  如果您不會使用任何小數位數，在 `Decimal` 變數中，可以保留從 \-79,228,162,514,264,337,593,543,950,335 到 79,228,162,514,264,337,593,543,950,335 的數字。  然而，`Decimal` 數字的運算速度，較任何其他數字資料型別慢很多。  
  
### 最小整數  
 如果您不需要完整的 `Integer` 資料型別範圍，可以使用 `Short` 資料型別，以保留從 \-32,768 到 32,767 的整數。  針對最小整數範圍，`SByte` 資料型別可保留從 \-128 到 127 的整數。  如果您有非常大量只保留最小整數的變數，Common Language Runtime 有時能更有效地儲存您的 `Short` 和 `SByte` 變數，並減少記憶體的消耗量。  然而，`Short` 和 `SByte` 的運算速度會較 `Integer` 稍慢一些。  
  
### 不帶正負號的整數  
 如果您知道變數絕對不需要保留負數，可以使用「*不帶正負號型別*」\(Unsigned Type\) `Byte`、`UShort`、`UInteger` 和 `ULong`。  這些資料型別各別可保留的正整數，大小是其對應的帶正負號型別 \(`SByte`、`Short`、`Integer` 和 `Long`\) 的兩倍。  就效能而言，每個不帶正負號型別與其對應的帶正負號型別，兩者的處理效率都一樣。  特別是 `UInteger` 和 `Integer`，兩者都享有所有基礎數字資料型別中最有效率的特徵。  
  
## 非整數類數字型別  
 「*非整數類資料型別*」\(Nonintegral Data Type\) 用來表示同時包含整數和分數部分的數字。  
  
 非整數類數字資料型別包括 `Decimal` \(128 位元定點\)、[Single Data Type](../../../../visual-basic/language-reference/data-types/single-data-type.md) \(32 位元浮點\) 和 [Double Data Type](../../../../visual-basic/language-reference/data-types/double-data-type.md) \(64 位元浮點\)。  這些都是帶正負號的型別。  如果變數會包含分數，則將其宣告為以上任一種型別。  
  
 `Decimal` 不是浮點數資料型別。  `Decimal` 數字包括二進位整數值，以及會指定數值的哪個部分為十進位分數的整數縮放比例。  
  
 您可以使用`Decimal`為 money 值的變數。  好處是值的精確度。  `Double` 資料型別雖然速度比較快，而且需要的記憶體也比較少，但它比較容易產生四捨五入誤差。  `Decimal`資料型別會保留到 28 的小數位數的正確性。  
  
 浮點 \(`Single` 和 `Double`\) 數字的範圍比 `Decimal` 數字的範圍大，但會有捨入的誤差。  浮點型別支援的有效位數比 `Decimal` 少，但可以表示較大範圍的值。  
  
 非整數類數值可表示成 mmmEeee，其中 mmm 是「*尾數*」\(Mantissa\) \(有效位數\)，而 eee 是「*指數*」\(Exponent\) \(10 的乘冪\)。  非整數類資料型別 `Decimal` 的最大正數值是 7.9228162514264337593543950335E\+28，`Single` 的最大正數值是 3.4028235E\+38，而 `Double` 的最大正數值則是 1.79769313486231570E\+308。  
  
### 效能  
 `Double` 是最有效率的分數資料型別，因為目前平台的處理器是以雙精度浮點數 \(Double\) 來執行浮點作業。  然而，`Double` 作業不會像 `Integer` 的整數類資料型別一樣快。  
  
### 最小範圍  
 針對最小可能範圍 \(最接近 0\) 的數值，`Double` 變數可以保留小至 \-4.94065645841246544E\-324 的負數值，以及小至 4.94065645841246544E\-324 的正數值。  
  
### 最小分數  
 如果您不需要完整的 `Double` 資料型別範圍，可以使用 `Single` 資料型別，以保留從 \-3.4028235E\+38 到 3.4028235E\+38 的浮點數。  `Single` 變數的最小範圍為 \-1.401298E\-45 的負數值和 1.401298E\-45 的正數值。  如果有非常大量只保留最小浮點數的變數，Common Language Runtime 有時能更有效地儲存您的 `Single` 變數，並減少記憶體的消耗量。  
  
## 請參閱  
 [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Character Data Types](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)   
 [Miscellaneous Data Types](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [How to: Call a Windows Function that Takes Unsigned Types](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)