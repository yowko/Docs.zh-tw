---
title: "Type Characters (Visual Basic) | Microsoft Docs"
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
  - "&H prefix for hexadecimal values"
  - "hexadecimal literals"
  - "F literal type character"
  - "& identifier type character"
  - "type characters"
  - "octal literals"
  - "literals, hexadecimal"
  - "&O prefix for octal values"
  - "literals, default types"
  - "defaults, literal types"
  - "C literal type character"
  - "type characters, literal"
  - "$ identifier type character"
  - "L literal type character"
  - "UI literal type characters"
  - "default literal types"
  - "D literal type character"
  - "literals, octal"
  - "S literal type character"
  - "! identifier type character"
  - "US literal type characters"
  - "% identifier type character"
  - "data types [Visual Basic], type characters"
  - "characters, identifier type"
  - "type characters, identifier"
  - "# identifier type character"
  - "identifier type characters"
  - "literal type characters"
  - "I literal type character"
  - "R literal type character"
  - "@ identifier type character"
  - "UL literal type characters"
  - "literal types, default"
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# Type Characters (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

除了在宣告陳述式 \(Declaration Statement\) 中指定資料型別之外，您還可以利用「*型別字元*」\(Type Character\) 來強制一些程式設計項目的資料型別。  型別字元必須緊接在項目之後，中間不可有任何介入字元。  
  
 型別字元不屬於項目名稱的一部分。  利用型別字元定義的項目，不需要型別字元就可用來做為參考。  
  
## 識別項型別字元  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 所提供的一組「*識別項型別字元*」\(Identifier Type Character\)，可讓您用來在宣告中指定變數或常數的資料型別。  下列資料表將說明可用的識別項型別字元並附用法範例。  
  
|識別項型別字元|資料型別|範例|  
|-------------|----------|--------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 `Boolean`、`Byte`、`Char`、`Date`、`Object`、`SByte`、`Short`、`UInteger`、`ULong` 或 `UShort` 資料型別或任何複合資料型別 \(例如陣列或結構\)，不會有識別項型別字元。  
  
 某些情況下，您可以將 `$` 字元附加到 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 函式，例如使用 `Left$` 代替 `Left`，以取得型別 `String` 的傳回值。  
  
 無論在任何情況下，識別項型別字元都必須緊接在識別項名稱之後。  
  
## 常值型別字元  
 所謂「*常值*」\(Literal\) 指的是特定資料型別值的文字表示。  
  
### 預設常值型別  
 通常在您的程式碼中所顯示的常值格式就能夠決定其資料型別。  下表顯示這些預設型別。  
  
|常值的文字格式|預設資料型別|範例|  
|-------------|------------|--------|  
|數字，沒有小數部分|`Integer`|`2147483647`|  
|數字，沒有小數部分，過大而不適合 `Integer`|`Long`|`2147483648`|  
|數字，有小數部分|`Double`|`1.2`|  
|放在雙引號中|`String`|`"A"`|  
|以數字符號括住|`Date`|`#5/17/1993 9:32 AM#`|  
  
### 強制常值型別  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 所提供的一組「*常值型別字元*」\(Literal Type Character\) 可讓您用來強制設定常值的資料型別，而不使用格式所指示的資料型別。  方式是將字元附加到常值之後。  下列資料表將說明可用的常值型別字元與用法的範例。  
  
|常值型別字元|資料型別|範例|  
|------------|----------|--------|  
|`S`|`Short`|`I = 347S`|  
|`I`|`Integer`|`J = 347I`|  
|`L`|`Long`|`K = 347L`|  
|`D`|`Decimal`|`X = 347D`|  
|`F`|`Single`|`Y = 347F`|  
|`R`|`Double`|`Z = 347R`|  
|`US`|`UShort`|`L = 347US`|  
|`UI`|`UInteger`|`M = 347UI`|  
|`UL`|`ULong`|`N = 347UL`|  
|`C`|`Char`|`Q = "."C`|  
  
 `Boolean`、`Byte`、`Date`、`Object`、`SByte` 或 `String` 資料型別或任何複合資料型別 \(例如陣列或結構\)，不會有常值型別字元。  
  
 就如同變數、常數和運算式一般，常值也可以使用識別項型別字元 \(`%`、`&`、`@`、`!`、`#`、`$`\)。  然而，常值型別字元 \(`S`、`I`、`L`、`D`、`F`、`R`、`C`\) 卻只能用於常值。  
  
 無論在任何情況下，常值型別字元都必須緊接在常值之後。  
  
## 十六進位和八進位常值  
 編譯器 \(Compiler\) 通常會將整數常值推斷為十進位 \(基底 10\) 數字系統。  您可以使用 `&H` 前置字元將整數常值強制為十六進位 \(基底 16\)，也可以使用 `&O` 前置字元將整數常值強制為八進位 \(基底 8\)。  前置字元後跟隨的數字必須符合數字系統。  下表將可說明這點。  
  
|數字基底|前置詞|有效數字值|範例|  
|----------|---------|-----------|--------|  
|十六進位 \(基底 16\)|`&H`|0\-9 和 A\-F|`&HFFFF`|  
|八進位 \(基底 8\)|`&O`|0\-7|`&O77`|  
  
 您可以在前置的常值後加上常值型別字元。  以下範例說明這點。  
  
```  
Dim counter As Short = &H8000S  
Dim flags As UShort = &H8000US  
```  
  
 在前一個範例中，`counter` 的十進位值為 \-32768，`flags` 的十進位值則為 \+32768。  
  
## 請參閱  
 [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)