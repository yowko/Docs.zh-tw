---
title: 常值
description: '瞭解 F # 程式設計語言中的常數值型別。'
ms.date: 08/15/2020
ms.openlocfilehash: 15f73db3c36f7c60ab1eeba96c63a28ebc6d7f01
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559150"
---
# <a name="literals"></a>常值

本文提供的表格顯示如何以 F # 指定常值的類型。

## <a name="literal-types"></a>常值類型

下表顯示 F # 中的常數值型別。 以十六進位標記法表示數位的字元不區分大小寫;識別類型的字元會區分大小寫。

|類型|描述|尾碼或前置詞|範例|
|----|-----------|----------------|--------|
|sbyte|帶正負號的8位整數|y|`86y`<br /><br />`0b00000101y`|
|byte|不帶正負號的8位自然數位|uy|`86uy`<br /><br />`0b00000101uy`|
|int16|帶正負號的16位整數|s|`86s`|
|uint16|不帶正負號的16位自然數位|us|`86us`|
|int<br /><br />int32|帶正負號的32位整數|l 或 none|`86`<br /><br />`86l`|
|uint<br /><br />uint32|不帶正負號的32位自然數位|u 或 ul|`86u`<br /><br />`86ul`|
|nativeint|帶正負號之自然數的原生指標|n|`123n`|
|unativeint|原生指標做為不帶正負號的自然數位|聯合國|`0x00002D3Fun`|
|int64|帶正負號的64位整數|L|`86L`|
|uint64|不帶正負號的64位自然數位|UL|`86UL`|
|single、float32|32位浮點數|F 或 f|`4.14F` 或 `4.14f`|
|||如果|`0x00000000lf`|
|浮點雙|64位浮點數|無|`4.14`、`2.3E+32` 或 `2.3e+32`|
|||如果|`0x0000000000000000LF`|
|BIGINT|整數，不限於64位標記法|I|`9999999999999999999999999999I`|
|decimal|以固定點或有理數表示的小數位數|M 或 m|`0.7833M` 或 `0.7833m`|
|Char|Unicode 字元|無|`'a'` 或 `'\u0061'`|
|String|Unicode 字串|無|`"text\n"`<br /><br />或<br /><br />`@"c:\filename"`<br /><br />或<br /><br />`"""<book title="Paradise Lost">"""`<br /><br />或<br /><br />`"string1" + "string2"`<br /><br />另請參閱 [字串](Strings.md)。|
|byte|ASCII 字元|B|`'a'B`|
|byte[]|ASCII 字串|B|`"text"B`|
|String 或 byte []|逐字字串|@ 前置詞|`@"\\server\share"` (Unicode) <br /><br />`@"\\server\share"B` (ASCII) |

## <a name="named-literals"></a>命名常值

要做為常數的值可以用 [Literal](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-literalattribute.html) 屬性標記。 這個屬性的效果會導致將值編譯為常數。

在模式比對運算式中，以小寫字元開頭的識別碼一律會被視為要系結的變數（而不是常值），因此當您定義常值時，通常應該使用初始大寫字母。

```fsharp
[<Literal>]
let SomeJson = """{"numbers":[1,2,3,4,5]}"""

[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

## <a name="remarks"></a>備註

Unicode 字串可以包含您可以使用來指定的明確編碼方式， `\u` 後面接著16位的十六進位程式碼 (0000-FFFF) 或您可以使用指定的32編碼， `\U` 並在後面接著32位的十六進位程式碼，表示任何 Unicode 程式碼點 (00000000 0010FFFF) 。

不允許使用以外的其他位運算子 `|||` 。

## <a name="integers-in-other-bases"></a>其他基底中的整數

您也可以 `0x` `0o` 分別使用或前置詞，以十六進位、八進位或二進位檔來指定已簽署的32位整數 `0b` 。

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a>數值常值中的底線

您可以使用底線字元 () 來分隔數位 `_` 。

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```
