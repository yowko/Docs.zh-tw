---
title: 常值
description: 瞭解程式F#設計語言中的常數值型別。
ms.date: 06/28/2019
ms.openlocfilehash: 9792a24ac28eb402e35e78574cd6a2bf9526734d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041036"
---
# <a name="literals"></a>常值

> [!NOTE]
> 本文中的 API 參考連結將帶您前往 MSDN （目前為）。

本主題提供的表格說明如何在中F#指定常值的型別。

## <a name="literal-types"></a>常數值型別

下表顯示中F#的常數值型別。 代表十六進位標記法中數位的字元不區分大小寫;識別類型的字元會區分大小寫。

|輸入|描述|尾碼或前置詞|範例|
|----|-----------|----------------|--------|
|sbyte|帶正負號的8位整數|Y|`86y`<br /><br />`0b00000101y`|
|byte|不帶正負號的8位自然數位|uy|`86uy`<br /><br />`0b00000101uy`|
|int16|帶正負號的16位整數|秒|`86s`|
|uint16|不帶正負號的16位自然數位|us|`86us`|
|int<br /><br />int32|帶正負號的32位整數|l 或 none|`86`<br /><br />`86l`|
|uint<br /><br />uint32|不帶正負號的32位自然數位|u 或 ul|`86u`<br /><br />`86ul`|
|nativeint|帶正負號之自然數位的原生指標|n|`123n`|
|unativeint|原生指標做為不帶正負號的自然數|取消|`0x00002D3Fun`|
|int64|帶正負號的64位整數|L|`86L`|
|uint64|不帶正負號的64位自然數位|UL|`86UL`|
|single、float32|32位浮點數字|F 或 f|`4.14F` 或 `4.14f`|
|||分行符號|`0x00000000lf`|
|float兩|64位浮點數字|none|`4.14`、`2.3E+32` 或 `2.3e+32`|
|||分行符號|`0x0000000000000000LF`|
|bigint|整數不限於64位標記法|I|`9999999999999999999999999999I`|
|decimal|以固定點或有理數表示的小數位數|M 或 m|`0.7833M` 或 `0.7833m`|
|Char|Unicode 字元|none|`'a'` 或 `'\u0061'`|
|String|Unicode 字串|none|`"text\n"`<br /><br />或<br /><br />`@"c:\filename"`<br /><br />或<br /><br />`"""<book title="Paradise Lost">"""`<br /><br />或<br /><br />`"string1" + "string2"`<br /><br />另請參閱[字串](Strings.md)。|
|byte|ASCII 字元|B|`'a'B`|
|byte[]|ASCII 字串|B|`"text"B`|
|String 或 byte []|逐字字串|@ 前置詞|`@"\\server\share"` （Unicode）<br /><br />`@"\\server\share"B` （ASCII）|

## <a name="named-literals"></a>命名的常值

要做為常數的值可以使用[Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285)屬性來標記。 這個屬性具有導致值編譯為常數的效果。

在模式比對運算式中，以小寫字元開頭的識別碼一律會被視為要系結的變數，而不是常值，因此當您定義常值時，通常應該使用首字母大寫。

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

Unicode 字串可以包含明確的編碼方式，您可以使用 `\u` 後面接著16位的十六進位碼（0000-FFFF），或您可以使用 `\U` 指定的 UTF-32 編碼，再加上代表任何 Unicode 的32位十六進位程式碼程式碼點（00000000-0010FFFF 之間）。

不允許使用 `|||` 以外的其他位運算子。

## <a name="integers-in-other-bases"></a>其他基底中的整數

您也可以使用 `0x`、`0o` 或 `0b` 前置詞，分別指定十六進位、八進位或二進位格式的已簽署32位整數。

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a>數值常值中的底線

您可以使用底線字元（`_`）來分隔數位。

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a>請參閱

- [LiteralAttribute 類別](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
