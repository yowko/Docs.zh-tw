---
title: 字串
description: 瞭解 F# "字串"類型如何表示不可變文本作為 Unicode 字元序列。
ms.date: 07/05/2019
ms.openlocfilehash: 242a2cefa1cce8995090dddd1d1fd7181e0f5e0c
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739565"
---
# <a name="strings"></a>字串

> [!NOTE]
> 本文中的 API 參考連結將帶您前往 MSDN。  docs.microsoft.com API 參考不完整。

該`string`類型表示不可變文本為 Unicode 字元序列。 `string` 是 `System.String` 在 .NET Framework 中的別名。

## <a name="remarks"></a>備註

字串文字由引號 (") 字元分隔。 反斜杠字元\\( ) 用於編碼某些特殊字元。 反斜杠與下一個字元一起被稱為*逸出序列*。 F# 字串文字中支援的轉義序列顯示在下表中。

|字元|逸出序列|
|---------|---------------|
|警示|`\a`|
|退格鍵|`\b`|
|換頁字元|`\f`|
|新行字元|`\n`|
|歸位字元|`\r`|
|索引標籤|`\t`|
|垂直 Tab 鍵|`\v`|
|反斜線|`\\`|
|引號|`\"`|
|單引號|`\'`|
|Unicode 字元|`\DDD`(其中`D`表示小數數位;範圍為 000 -`\231`255; 例如,= "*")|
|Unicode 字元|`\xHH`(其中`H`指示十六進位元;範圍為 00 - FF;例如,= `\xE7` "*")|
|Unicode 字元|`\uHHHH`(UTF-16)(其中`H`表示十六進位元;範圍為 0000 - FFFF; 例如,= `\u00E7` "*")|
|Unicode 字元|`\U00HHHHHH`(UTF-32)(其中`H`表示十六進位元;範圍為 000000 - 10FFFF; 例如,= `\U0001F47D` """)👽|

> [!IMPORTANT]
> `\DDD`轉義序列是十進制表示法,不像大多數其他語言那樣的八進位表示法。 因此,數位`8`和`9`有效,並且序列`\032`表示空格 (U+0020),而八進位表示法中的同一代碼`\040`點將是 。

> [!NOTE]
> 被限制到 0 - 255 (0xFF)`\DDD``\x`的範圍, 和轉義序列實際上是[ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout)字元集, 因為它匹配前 256 個 Unicode 點。

## <a name="verbatim-strings"></a>逐字串

如果前面有 + 符號,則文本是逐字字串。 這意味著忽略任何轉義序列,只不過兩個引號字元被解釋為一個引號字元。

## <a name="triple-quoted-strings"></a>三重報價字串

此外,字串可以用三重引弧括起來。 在這種情況下,將忽略所有轉義序列,包括雙引號字元。 要指定包含嵌入引言字串的字串,可以使用逐字字串或三重引號字串。 如果使用逐字字串,則必須指定兩個引號字元以指示單個引號字元。 如果使用三重引號字串,則可以使用單個引號字元,而無需將它們解析為字串的末尾。 當您使用 XML 或其他包含嵌入引號的結構時,此方法非常有用。

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

在代碼中,接受具有換行符的字串,並且換行元從字面上解釋為換行符,除非反斜杠字元是換行符之前的最後一個字元。 使用反斜杠字元時,將忽略下一行的前導空格。 `str1`以下代碼產生具有值`"abc\ndef"`的字串和具有值`str2``"abcdef"`的字串。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a>字串索引和切片

可以使用類似於陣列的語法訪問字串中的單個字元,如下所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

輸出為 `b`。

或者,您可以使用陣列切片語法提取子字串,如以下代碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

輸出如下。

```console
abc
def
```

您可以按未簽署的陣列表示 ASCII 字串,類型`byte[]`為 。 將後綴`B`添加到字串文字,以指示它是 ASCII 字串。 與位元陣列一起使用的 ASCII 字串文字支援與 Unicode 字串相同的轉義序列,Unicode 轉義序列除外。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a>字串運算子

該`+`運算元可用於串聯字串,保持與 .NET 框架字串處理功能的相容性。 下面的示例演示了字串串聯。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a>字串類別

由於 F# 中的字串類型實際上是`System.String`.NET`System.String`框架類型, 因此所有成員都可用。 這包括`+`運算子,該運算元用於串聯字串、`Length`屬性和`Chars`屬性,後者將字串作為 Unicode 字元的陣列返回。 有關字串的詳細資訊,請參閱`System.String`。

通過使用`Chars``System.String`屬性 ,可以通過指定索引來訪問字串中的單個字元,如下代碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a>字串模組

`FSharp.Core`命名空間中的`String`模組中包括字串處理的其他功能。 有關詳細資訊,請參閱[Core.String 模組](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d)。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
