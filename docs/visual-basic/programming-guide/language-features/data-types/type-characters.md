---
title: 類型字元 (Visual Basic)
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
ms.openlocfilehash: a469a08ebadd77d5abbfa95b270784c9ef534691
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734866"
---
# <a name="type-characters-visual-basic"></a>輸入字元 (Visual Basic)

除了宣告陳述式中指定的資料類型，您可以強制使用一些程式設計項目的資料型別*型別字元*。 類型字元必須緊接的項目，不可有任何類型的任何中介字元。

類型字元不是項目的名稱的一部分。 定義使用類型字元的項目可以參考不含類型字元。

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
  
 沒有識別項類型字元存在`Boolean`， `Byte`， `Char`， `Date`， `Object`， `SByte`， `Short`， `UInteger`， `ULong`，或`UShort`資料類型，或任何複合資料類型，例如陣列或結構。

在某些情況下，您可以將附加`$`字元，是 Visual Basic 函式，例如`Left$`而不是`Left`，以取得傳回的值類型為`String`。

在所有情況下，識別項類型字元必須緊接的識別項名稱。

## <a name="literal-type-characters"></a>常值類型字元

A*常值*是特定值的資料類型的文字表示法。  

### <a name="default-literal-types"></a>預設常值類型

常值的形式通常出現在您的程式碼會判斷其資料型別。 下表顯示這些預設型別。  
  
|文字格式的常值|預設資料類型|範例|  
|-----------------------------|-----------------------|-------------|  
|數字，沒有小數部分|`Integer`|`2147483647`|  
|數字，沒有小數部分，針對太大 `Integer`|`Long`|`2147483648`|  
|數字的小數點後的組件|`Double`|`1.2`|  
|以雙引號括住|`String`|`"A"`|  
|數字符號括住|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a>強制的常值類型

Visual Basic 提供的一組*常值類型字元*，可用來強制常之外的資料類型的形式表示。 您可以將字元附加到常值的結尾。 下表顯示可用的常值類型字元，與使用方式的範例。
  
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

任何常值類型字元存在`Boolean`， `Byte`， `Date`， `Object`， `SByte`，或`String`資料類型，或任何的複合資料類型，例如陣列或結構。

常值也可以使用識別項類型字元 (`%`， `&`， `@`， `!`， `#`， `$`)，如可以變數、 常數和運算式。 不過，常值類型字元 (`S`， `I`， `L`， `D`， `F`， `R`， `C`) 可以僅能搭配常值。

在所有情況下，常值類型字元必須緊接的常值。

## <a name="hexadecimal-binary-and-octal-literals"></a>十六進位、 二進位以及八進位的常值

通常，編譯器會解譯為十進位 (基底 10) 數字系統中的常值的整數。 您也可以定義的常值整數的十六進位 (基底 16) 數字`&H`前置詞的二進位 (基底 2) 數字`&B`前置詞，以及八進位 (基底 8) 編號，以`&O`前置詞。 請依照下列前置詞的數字必須適用於數字系統。 下表說明這點。  
  
|數字基底|前置詞|有效的數字值|範例|
|-----------------|------------|------------------------|-------------|
|十六進位 (基底 16)|`&H`|0-9 和 A-F|`&HFFFF`|
|二進位檔 (基底 2)|`&B`|0-1|`&B01111100`|
|八進位 (基底 8)|`&O`|0-7|`&O77`|

從 Visual Basic 2017 開始，您可以使用底線字元 (`_`) 做為群組分隔符號，以提升的整數常值的可讀性。 下列範例會使用`_`群 8 位元群組中的二進位常值的字元：

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

您可以依照前置的常值與常值類型字元。 下列範例會示範這。

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

在上述範例中，`counter`具有十進位值，介於-32768 和`flags`32768 的十進位值。

從 Visual Basic 15.5 開始，您也可以使用底線字元 (`_`) 作為前置分隔符號之間的前置詞和十六進位、 二進位或八進位數字。 例如: 

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a>另請參閱

- [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [基礎資料類型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [在 Visual Basic 中的類型轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [資料類型的疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [資料類型](../../../../visual-basic/language-reference/data-types/index.md)
