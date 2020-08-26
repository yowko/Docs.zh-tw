---
title: 字串
description: "瞭解 F # ' string ' 類型如何將不可變的文字表示為 Unicode 字元序列。"
ms.date: 08/15/2020
ms.openlocfilehash: f6ec36feeb197bf785c702e7b626cf5cf80696ab
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812207"
---
# <a name="strings"></a>字串

型別會將 `string` 不可變的文字表示為 Unicode 字元序列。 `string` 是 `System.String` 在 .NET 中的別名。

## <a name="remarks"></a>備註

字串常值是以引號 ( ") 字元分隔。  ( ) 的反斜線字元 \\ 用來編碼某些特殊字元。 反斜線和下一個字元統稱為「escape」 *序列*。 下表顯示 F # 字串常值中支援的 Escape 序列。

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
|Unicode 字元|`\DDD` (，其中 `D` 指出十進位數; 範圍為 000-255; 例如 `\231` = "ç" ) |
|Unicode 字元|`\xHH` (，其中 `H` 指出十六進位數位; 範圍為 00-FF，例如 `\xE7` = "ç" ) |
|Unicode 字元|`\uHHHH` (UTF-16)  (其中 `H` 指出十六進位數位; 範圍為 0000-FFFF; 例如， `\u00E7` = "ç" ) |
|Unicode 字元|`\U00HHHHHH` (32 UTF-8)  (，其中 `H` 指出十六進位數位; 範圍為 000000-10FFFF; 例如， `\U0001F47D` = " 👽 " ) |

> [!IMPORTANT]
> `\DDD`Escape 序列是十進位標記法，而非八進位標記法，就像大多數其他語言一樣。 因此，數位 `8` 和 `9` 是有效的，而序列 `\032` 表示 (U + 0020) 的空格，而八進位標記法中的相同程式碼點則為 `\040` 。

> [!NOTE]
> 受限於 0-255 (0xFF) 的範圍， `\DDD` 和 `\x` escape 序列實際上是 [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) 字元集，因為該字元集符合前 256 Unicode 程式碼點。

## <a name="verbatim-strings"></a>逐字字串

如果前面加上 @ 符號，常值為逐字字串。 這表示會忽略任何 escape 序列，但會將兩個引號字元視為一個引號字元。

## <a name="triple-quoted-strings"></a>三個引號的字串

此外，字串可以用三個引號括住。 在此情況下，會忽略所有的 escape 序列，包括雙引號字元。 若要指定包含內嵌引號字串的字串，您可以使用逐字字串或以三括弧括住的字串。 如果您使用逐字字串，您必須指定兩個引號字元，以表示單引號字元。 如果您使用以三個引號括住的字串，則可以使用單引號字元，而不將它們剖析為字串的結尾。 當您使用 XML 或其他包含內嵌引號的結構時，這項技術會很有用。

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

在程式碼中，接受分行符號的字串會被接受，而且分行符號會以逐字的形式解釋為分行符號，除非反斜線字元是分行符號之前的最後一個字元。 使用反斜線字元時，會忽略下一行的開頭空白字元。 下列程式碼會產生具有值的字串， `str1` `"abc\ndef"` 以及 `str2` 具有值的字串 `"abcdef"` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a>字串編制索引和切割

您可以使用類似陣列的語法來存取字串中的個別字元，如下所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

輸出為 `b`。

或者，您可以使用陣列配量語法來解壓縮子字串，如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

輸出如下。

```console
abc
def
```

您可以使用不帶正負號的位元組陣列來代表 ASCII 字串，請輸入 `byte[]` 。 您將尾碼新增 `B` 至字串常值，以表示它是 ASCII 字串。 搭配位元組陣列使用的 ASCII 字串常值支援與 Unicode 字串相同的 escape 序列，但 Unicode escape 序列除外。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a>字串運算子

`+`操作員可以用來串連字號串，維持與 .NET Framework 字串處理功能的相容性。 下列範例說明字串串連。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a>String 類別

因為 F # 中的字串類型實際上是 .NET Framework `System.String` 類型，所以所有 `System.String` 成員都可以使用。 這包括 `+` 用來串連字號串的運算子、 `Length` 屬性和 `Chars` 屬性（property），這會以 Unicode 字元陣列的形式傳回字串。 如需字串的詳細資訊，請參閱 `System.String` 。

藉由使用的 `Chars` 屬性 `System.String` ，您可以藉由指定索引來存取字串中的個別字元，如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a>字串模組

字串處理的其他功能會包含在 `String` 命名空間的模組中 `FSharp.Core` 。 如需詳細資訊，請參閱 [字串模組](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-stringmodule.html)。

## <a name="see-also"></a>另請參閱

- [F # 語言參考](index.md)
