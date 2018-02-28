---
title: "類型字元 (Visual Basic)"
ms.custom: 
ms.date: 01/31/2018
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- '&H prefix for hexadecimal values'
- hexadecimal literals [Visual Basic]
- F literal type character [Visual Basic]
- '& identifier type character'
- type characters [Visual Basic]
- octal literals [Visual Basic]
- literals [Visual Basic], hexadecimal
- '&O prefix for octal values'
- literals [Visual Basic], default types
- defaults, literal types
- C literal type character [Visual Basic]
- type characters [Visual Basic], literal
- $ identifier type character
- L literal type character [Visual Basic]
- UI literal type characters [Visual Basic]
- default literal types [Visual Basic]
- D literal type character [Visual Basic]
- literals [Visual Basic], octal
- S literal type character [Visual Basic]
- '! identifier type character'
- US literal type characters [Visual Basic]
- '% identifier type character'
- data types [Visual Basic], type characters
- characters [Visual Basic], identifier type
- type characters [Visual Basic], identifier
- '# identifier type character'
- identifier type characters [Visual Basic]
- literal type characters [Visual Basic]
- I literal type character [Visual Basic]
- R literal type character [Visual Basic]
- '@ identifier type character'
- UL literal type characters [Visual Basic]
- literal types [Visual Basic], default
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
author: rpetrusha
ms.author: ronpet
ms.manager: wpickett
ms.openlocfilehash: 20a9a30689fb62a6956987b06470e76eeb42ebab
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2018
---
# <a name="type-characters-visual-basic"></a>輸入的字元 (Visual Basic)

除了宣告陳述式中指定的資料類型，您可以強制使用一些程式設計項目的資料型別*類型字元*。 型別字元必須緊接的項目，其中沒有任何種類的中介字元。

類型字元不是項目的名稱的一部分。 型別字元定義的項目可以參考不含類型字元。

## <a name="identifier-type-characters"></a>識別項類型字元

Visual Basic 提供的一組*識別項類型字元*您可以使用在宣告中指定的變數或常數的資料類型。 下表顯示可用的識別項類型字元，與使用方式的範例。
  
|識別項類型字元|資料類型|範例|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 存在任何識別項類型字元`Boolean`， `Byte`， `Char`， `Date`， `Object`， `SByte`， `Short`， `UInteger`， `ULong`，或`UShort`資料型別，或任何複合資料類型，例如陣列或結構。

在某些情況下，您可以將附加`$`字元為 Visual Basic 函式，例如`Left$`而不是`Left`，以取得傳回的值類型為`String`。

在所有情況下，識別項類型字元必須緊接的識別項名稱。

## <a name="literal-type-characters"></a>常值類型字元

A*常值*是特定值的資料類型的文字表示法。  

### <a name="default-literal-types"></a>預設常值類型

常值的形式通常出現在您的程式碼會判斷其資料類型。 下表顯示這些預設型別。  
  
|文字格式的常值|預設資料類型|範例|  
|-----------------------------|-----------------------|-------------|  
|數字，沒有小數部分|`Integer`|`2147483647`|  
|數字，沒有小數部分，針對太大 `Integer`|`Long`|`2147483648`|  
|數字，小數部分|`Double`|`1.2`|  
|以雙引號括住|`String`|`"A"`|  
|數字符號括住|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a>強制的常值類型

Visual Basic 提供的一組*常值類型字元*，您可以使用強制常之外的資料類型的形式表示。 您可以將字元附加到常值的結尾。 下表顯示可用的常值類型字元，與使用方式的範例。
  
|常值類型字元|資料類型|範例|  
|----------------------------|---------------|-------------|  
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

沒有常值類型字元存在`Boolean`， `Byte`， `Date`， `Object`， `SByte`，或`String`資料型別，或任何複合資料類型，例如陣列或結構。

常值也可以使用識別項類型字元 (`%`， `&`， `@`， `!`， `#`， `$`)，可能是變數、 常數和運算式。 不過，常值類型字元 (`S`， `I`， `L`， `D`， `F`， `R`， `C`) 可以僅能搭配常值。

在所有情況下，常值類型字元必須緊接的常值。

## <a name="hexadecimal-binary-and-octal-literals"></a>十六進位、 二進位以及八進位常值

編譯器通常會解譯為十進位 (基底 10) 數字系統中的常值的整數。 您也可以定義一個整數常值的十六進位 (基底 16) 數字`&H`前置詞的二進位 (基底 2) 數字`&B`前置詞，以及八進位 (基底 8) 編號，以`&O`前置詞。 請依照下列前置詞的數字必須適用於數字系統。 下表將說明這點。  
  
|數字基底|前置詞|有效的數字值|範例|
|-----------------|------------|------------------------|-------------|
|十六進位 (基底 16)|`&H`|0-9 和 A-F|`&HFFFF`|
|二進位 (基底 2)|`&B`|0-1|`&B01111100`|
|八進位 (基底 8)|`&O`|0-7|`&O77`|

從 Visual Basic 2017 開始，您可以使用底線字元 (`_`) 做為群組分隔符號，來增強整數常值的可讀性。 下列範例會使用`_`成 8 位元群組分組的二進位常值的字元：

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

您可以遵循前置的常值與常值類型字元。 下列範例顯示這點。

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

在上述範例中，`counter`的十進位值為-32768，和`flags`具有 32768 的十進位值。

從 Visual Basic 15.5 開始，您也可以使用底線字元 (`_`) 做為前置詞和十六進位、 二進位或八進位的數字之間的前置分隔符號。 例如: 

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a>請參閱

 [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [基礎資料類型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [在 Visual Basic 中的型別轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [資料類型的疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [資料類型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)
