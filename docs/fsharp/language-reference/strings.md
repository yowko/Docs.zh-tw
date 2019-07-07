---
title: 字串
description: 了解如何F#'string' 類型以一連串的 Unicode 字元表示不可變的文字。
ms.date: 07/05/2019
ms.openlocfilehash: b252aef7d7e6e299df8282407198714971e80cd5
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610168"
---
# <a name="strings"></a>字串

> [!NOTE]
> 本文中的 API 參考連結將帶您前往 MSDN。  docs.microsoft.com API 參考不完整。

`string`類型以一連串的 Unicode 字元表示不可變的文字。 `string` 是 `System.String` 在 .NET Framework 中的別名。

## <a name="remarks"></a>備註

字串常值是以引號 （"） 字元分隔。 反斜線字元 ( \\ ) 來編碼某些特殊字元。 反斜線和放在一起的下一個字元稱為*逸出序列*。 逸出序列中支援F#字串常值會顯示下表中。

|字元|逸出序列|
|---------|---------------|
|警示|`\a`|
|退格鍵|`\b`|
|換頁字元|`\f`|
|新行字元|`\n`|
|歸位字元|`\r`|
|索引標籤|`\t`|
|垂直 Tab|`\v`|
|反斜線|`\\`|
|引號|`\"`|
|所有格符號|`\'`|
|Unicode 字元|`\DDD` (其中`D`表示十進位數字，範圍的 000-255，例如`\231`="ç")|
|Unicode 字元|`\xHH` (其中`H`表示的十六進位數字，範圍為 00-FF; 例如`\xE7`="ç")|
|Unicode 字元|`\uHHHH` (UTF-16)(其中`H`表示的十六進位數字; 0000-FFFF; 的範圍 例如`\u00E7`="ç")|
|Unicode 字元|`\U00HHHHHH` (UTF-32)(其中`H`表示的十六進位數字，範圍是 000000-10ffff 且; 例如`\U0001F47D`="👽")|

> [!IMPORTANT]
> `\DDD`逸出序列是十進位表示法，而不是八進位的標記法類似大多數其他語言中。 因此，數字`8`並`9`有效，以及一系列`\032`代表空格 (u+0020)，而該相同的字碼指標，八進位標記法會`\040`。

> [!NOTE]
> 正在受限於範圍介於 0-255 (0xFF)，`\DDD`並`\x`逸出序列都是有效[ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout)字元集，則為，由於符合的前 256 個 Unicode 字碼指標。

如果前面加上 @ 符號，此常值是逐字字串。 這表示，則會忽略任何逸出序列，不同之處在於兩個引號字元視為一個引號字元。

此外，可能以三引號括住字串。 在此情況下，會忽略所有逸出序列，包括雙引號字元。 若要指定包含內嵌字串加上引號的字串，您可以使用逐字字串或三重物件加上引號的字串。 如果您使用逐字字串時，您必須指定兩個引號字元來表示一個單引號字元。 如果您使用三重物件加上引號的字串，您可以使用單引號字元沒有它們正在剖析為字串的結尾。 當您使用 XML 或其他結構包含內嵌的引號，則這個方法就很有用。

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

程式碼中，接受已換行的字串，並換行符號會解譯為常值為換行符號，除非反斜線字元換行之前的最後一個字元。 使用反斜線字元時，會忽略在下一行的前置空白字元。 下列程式碼產生的字串`str1`具有值`"abc\ndef"`和字串`str2`具有值`"abcdef"`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

您可以存取個別字元在字串中的使用類似陣列的語法，如下所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

輸出為 `b`。

或者，您可以使用陣列配量語法，來擷取子字串，如下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

輸出如下。

```
abc
def
```

您可以不帶正負號位元組，型別陣列表示 ASCII 字串`byte[]`。 新增後置詞`B`為字串常值以指出它是 ASCII 字串。 ASCII 字串常值的位元組陣列搭配使用支援相同逸出序列為 Unicode 字串，除了 Unicode 逸出序列。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a>字串運算子

有兩種方式來串連字串： 使用`+`運算子或使用`^`運算子。 `+`運算子會維護與.NET Framework 的字串處理功能的相容性。

下列範例說明字串串連。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a>字串類別

因為字串類型在F#是實際的.NET Framework`System.String`類型，所有`System.String`成員都可以使用。 這包括`+`運算子，用來串連字串，就`Length`屬性，而`Chars`屬性，會傳回字串的 Unicode 字元陣列。 如需字串的詳細資訊，請參閱`System.String`。

藉由使用`Chars`屬性`System.String`，您可以存取個別字元在字串中的指定的索引，如下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a>字串模組

字串處理的其他功能包含在`String`中的模組`FSharp.Core`命名空間。 如需詳細資訊，請參閱 < [Core.String 模組](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d)。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
