---
title: 類型字元
ms.date: 01/31/2018
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
ms.openlocfilehash: a48260694c1dfcbbb8f804f220fe89b1663c7319
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393074"
---
# <a name="type-characters-visual-basic"></a>類型字元（Visual Basic）

除了在宣告語句中指定資料類型之外，您還可以使用*類型字元*來強制某些程式設計項目的資料類型。 類型字元必須緊接在元素後面，不含任何類型的中間字元。

類型字元不是元素名稱的一部分。 以類型字元定義的專案，可以不使用類型字元來參考。

## <a name="identifier-type-characters"></a>識別項型別字元

Visual Basic 提供一組*識別項型別字元*，您可以在宣告中用來指定變數或常數的資料類型。 下表顯示可用的識別項型別字元，以及使用方式的範例。
  
|識別項型別字元|資料類型|範例|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 對於 `Boolean` 、、、、、、、 `Byte` 、 `Char` `Date` `Object` `SByte` `Short` `UInteger` `ULong` 或 `UShort` 資料類型，或任何複合資料型別（例如陣列或結構），都不會有任何識別項型別字元。

在某些情況下，您可以將 `$` 字元附加至 Visual Basic 函式（例如 `Left$` ，而不是 `Left` ），以取得類型的傳回值 `String` 。

在所有情況下，識別項型別字元必須緊接在識別碼名稱之後。

## <a name="literal-type-characters"></a>常數值型別字元

*常*值是資料類型之特定值的文字標記法。  

### <a name="default-literal-types"></a>預設常數值型別

常值出現在程式碼中的形式，通常會決定其資料類型。 下表顯示這些預設類型。  
  
|文字形式的常值|預設資料類型|範例|  
|-----------------------------|-----------------------|-------------|  
|數值，無小數部分|`Integer`|`2147483647`|  
|數值，沒有小數部分，太大，無法用於`Integer`|`Long`|`2147483648`|  
|數值、小數部分|`Double`|`1.2`|  
|括在雙引號中|`String`|`"A"`|  
|包含在數位記號內|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a>強制常數值型別

Visual Basic 會提供一組*常數值型別字元*，您可以用它來強制常值採用其表單所表示的資料類型。 若要這麼做，請將字元附加到常值的結尾。 下表顯示可用的常數值型別字元，以及使用方式的範例。
  
|常數值型別字元|資料類型|範例|  
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

對於 `Boolean` 、 `Byte` 、 `Date` 、 `Object` 、 `SByte` 或 `String` 資料類型，或任何複合資料型別（例如陣列或結構），都不會有常數值型別字元。

常值也可以使用識別項型別字元（ `%` 、 `&` 、 `@` 、 `!` 、 `#` 、 `$` ），就像變數、常數和運算式一樣。 不過，常數值型別字元（ `S` 、 `I` 、 `L` 、 `D` 、 `F` 、 `R` 、 `C` ）只能搭配常值使用。

在所有情況下，常數值型別字元必須緊接在常值後面。

## <a name="hexadecimal-binary-and-octal-literals"></a>十六進位、二進位和八進位常值

編譯器通常會將整數常值轉譯為十進位（基底10）數值系統中的。 您也可以將整數常值定義為具有前置詞的十六進位（基底16）數位 `&H` ，做為具有前置詞的二進位（基底2）數位， `&B` 以及前置詞為八進位（基底8）的數位 `&O` 。 前置詞後面的數位必須適用于數字系統。 下表將說明這一點。  
  
|數位基底|前置詞|有效的數位值|範例|
|-----------------|------------|------------------------|-------------|
|十六進位 (基底 16)|`&H`|0-9 和 A-f|`&HFFFF`|
|二進位（基底2）|`&B`|0-1|`&B01111100`|
|八進位 (基底 8)|`&O`|0-7|`&O77`|

從 Visual Basic 2017 開始，您可以使用底線字元（ `_` ）做為群組分隔符號，以增強整數常值的可讀性。 下列範例會使用 `_` 字元，將二進位常值分組為8位群組：

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

您可以遵循具有常數值型別字元的首碼常值。 以下範例說明這點。

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

在上述範例中，的 `counter` 十進位值為-32768，而 `flags` 的十進位值為 + 32768。

從 Visual Basic 15.5 開始，您也可以使用底線字元（ `_` ）做為前置詞和十六進位、二進位或八進位數位之間的前置分隔符號。 例如：

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a>另請參閱

- [資料類型](index.md)
- [基礎資料類型](elementary-data-types.md)
- [Value Types and Reference Types](value-types-and-reference-types.md)
- [Visual Basic 中的類型轉換](type-conversions.md)
- [疑難排解資料類型的問題](troubleshooting-data-types.md)
- [變數宣告](../variables/variable-declaration.md)
- [資料類型](../../../language-reference/data-types/index.md)
