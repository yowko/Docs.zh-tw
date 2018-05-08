---
title: 常值 (F#)
description: '深入了解 F # 程式語言中的常值類型。'
ms.date: 05/16/2016
ms.openlocfilehash: f28ca0ae7a0b092bbc039d23625b883faffd241c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="literals"></a>常值

> [!NOTE]
本文章中的應用程式開發介面參考連結將您移至 MSDN （適用於立即）。

本主題提供的資料表將顯示如何在 F # 中指定的常值類型。

## <a name="literal-types"></a>常值類型
下表顯示 F # 中的常值類型。 表示數字的十六進位表示法的字元不區分大小寫。識別類型的字元會區分大小寫。

|類型|描述|後置字元或前置詞|範例|
|----|-----------|----------------|--------|
|sbyte|8 位元帶正負號的整數|y|`86y`<br /><br />`0b00000101y`|
|byte|不帶正負號的 8 位元自然數字|uy|`86uy`<br /><br />`0b00000101uy`|
|int16|16 位元帶正負號的整數|秒|`86s`|
|uint16|不帶正負號的 16 位元自然數字|us|`86us`|
|int<br /><br />int32|32 位元帶正負號的整數|l 或 none|`86`<br /><br />`86l`|
|uint<br /><br />uint32|不帶正負號的 32 位元自然數字|u 或 u l|`86u`<br /><br />`86ul`|
|unativeint|原生指標做為不帶正負號的自然號碼|取消|`0x00002D3Fun`|
|int64|64 位元帶正負號的整數|L|`86L`|
|uint64|不帶正負號的 64 位元自然數字|UL|`86UL`|
|single、 float32|32 位元浮點數|F 或 f|`4.14F` 或 `4.14f`|
|||lf|`0x00000000lf`|
|浮點數。double|64 位元浮點數|無|`4.14`、`2.3E+32` 或 `2.3e+32`|
|||LF|`0x0000000000000000LF`|
|bigint|不會限制為 64 位元表示的整數|I|`9999999999999999999999999999I`|
|decimal|表示為固定的點或合理數的小數數字|M 或 m|`0.7833M` 或 `0.7833m`|
|Char|Unicode 字元|無|`'a'`|
|String|Unicode 字串|無|`"text\n"`<br /><br />或<br /><br />`@"c:\filename"`<br /><br />或<br /><br />`"""<book title="Paradise Lost">"""`<br /><br />或<br /><br />`"string1" + "string2"`<br /><br />另請參閱[字串](Strings.md)。|
|byte|ASCII 字元|B|`'a'B`|
|byte[]|ASCII 字串|B|`"text"B`|
|字串或 byte [|逐字字串|@ 前置詞|`@"\\server\share"` (Unicode)<br /><br />`@"\\server\share"B` (ASCII)|

## <a name="remarks"></a>備註
Unicode 字串可以包含明確的編碼方式，您可以指定使用`\u`後面跟著 16 位元的十六進位碼或您可以使用指定的 utf-32 編碼`\U`後面接著 32 位元的十六進位代碼，表示為 Unicodesurrogate 字組。

為準，F # 3.1，您可以使用`+`登結合字串常值。 您也可以使用位元或 (`|||`) 運算子來組合列舉旗標。 例如，下列程式碼是在 F # 3.1 中合法的：

```fsharp
[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

不允許其他位元運算子的用法。


## <a name="named-literals"></a>具名常值
要作為 常數的值都可以使用標記[常值](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285)屬性。 這個屬性具有造成編譯為常數的值。

在模式比對運算式中，以小寫字母字元開頭的識別項一律視為變數繫結，而不做為常值，所以通常應該使用第一個字母大寫時定義常值。

## <a name="integers-in-other-bases"></a>其他的基底的整數

帶正負號的 32 位元整數，也可以指定在使用十六進位、 八進位或二進位`0x`，`0o`或`0b`分別前置詞。

```fsharp
let Numbers = (0x9F, 0o77, 0b1010)
// Result: Numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a>數值常值中的底線

從 F # 4.1 開始，您可以分隔數字與底線字元 (`_`)。

```fsharp
let DeadBeef = 0xDEAD_BEEF

let DeadBeefAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let ExampleSSN = 123_456_7890
```

## <a name="see-also"></a>另請參閱

[Core.LiteralAttribute 類別](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
