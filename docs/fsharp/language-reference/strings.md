---
title: 字串
description: 瞭解「字串F# 」類型如何以 Unicode 字元序清單示不可變的文字。
ms.date: 07/05/2019
ms.openlocfilehash: 002de464d09a49b6161608db6e46c619369f5ceb
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452814"
---
# <a name="strings"></a>字串

> [!NOTE]
> 本文中的 API 參考連結將帶您前往 MSDN。  docs.microsoft.com API 參考不完整。

`string` 類型會以 Unicode 字元序列的形式來表示不可變的文字。 `string` 是 `System.String` 在 .NET Framework 中的別名。

## <a name="remarks"></a>備註

字串常值是以引號（"）字元分隔。 反斜線字元（\\）是用來編碼某些特殊字元。 反斜線和下一個字元一起稱為「*逸出序列*」。 下表顯示F#字串常值中支援的 Escape 序列。

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
|省略號|`\'`|
|Unicode 字元|`\DDD` （其中 `D` 表示十進位數; 範圍為 000-255; 例如，`\231` = "ç"）|
|Unicode 字元|`\xHH` （其中 `H` 表示十六進位數位; 00-FF 的範圍，例如，`\xE7` = "ç"）|
|Unicode 字元|`\uHHHH` （UTF-16）（其中 `H` 表示十六進位數位; 0000-FFFF 的範圍; 例如，`\u00E7` = "ç"）|
|Unicode 字元|`\U00HHHHHH` （UTF-32）（其中 `H` 表示十六進位數位; 000000-10FFFF 且的範圍; 例如，`\U0001F47D` = "👽"）|

> [!IMPORTANT]
> `\DDD` 的逸出序列是十進位標記法，而不是像大部分其他語言中的八進位標記法。 因此，`8` 和 `9` 的數位是有效的，而 `\032` 的序列則代表空格（U + 0020），而八進位標記法中的相同程式碼點也會 `\040`。

> [!NOTE]
> 受限於 0-255 （0xFF）的範圍，`\DDD` 和 `\x` 的逸出序列實際上是[ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout)字元集，因為這符合第一個 256 Unicode 程式碼點。

## <a name="verbatim-strings"></a>逐字字串

如果前面加上 @ 符號，常值就是逐字字串。 這表示會忽略任何逸出序列，不過，兩個引號字元會被視為一個引號字元。

## <a name="triple-quoted-strings"></a>三加引號的字串

此外，字串可以用三個引號括住。 在此情況下，會忽略所有的逸出序列，包括雙引號字元。 若要指定包含內嵌加上引號之字串的字串，您可以使用逐字字串或以三個引號括住的字串。 如果您使用逐字字串，您必須指定兩個引號字元來表示單一引號字元。 如果您使用三加引號的字串，您可以使用單引號字元，而不將它們剖析為字串的結尾。 當您使用包含內嵌引號的 XML 或其他結構時，這項技術會很有用。

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

在程式碼中，會接受具有分行符號的字串，而且分行符號會以逐字的方式轉譯為分行符號，除非反斜線字元是分行符號前的最後一個字元。 使用反斜線字元時，會忽略下一行的前置空白字元。 下列程式碼會產生具有值 `"abc\ndef"` 的字串 `str1`，以及具有值 `"abcdef"`的字串 `str2`。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a>字串索引和切割

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

您可以依不帶正負號的位元組陣列來表示 ASCII 字串，請輸入 `byte[]`。 您可以將尾碼 `B` 新增至字串常值，以表示它是 ASCII 字串。 搭配位元組陣列使用的 ASCII 字串常值支援與 Unicode 字串相同的轉義順序，但 Unicode 逸出序列除外。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a>字串運算子

串連字號串的方法有兩種：使用 `+` 運算子，或使用 `^` 運算子。 `+` 運算子會維持與 .NET Framework 字串處理功能的相容性。

下列範例說明字串串連。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a>String 類別

因為中F#的字串類型實際上是 .NET Framework `System.String` 類型，所以所有 `System.String` 成員都可以使用。 這包括 `+` 運算子，用來串連字號串、`Length` 屬性和 `Chars` 屬性，這會傳回字串做為 Unicode 字元陣列。 如需有關字串的詳細資訊，請參閱 `System.String`。

藉由使用 `System.String`的 `Chars` 屬性，您可以藉由指定索引來存取字串中的個別字元，如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a>字串模組

字串處理的其他功能會包含在 `FSharp.Core` 命名空間的 `String` 模組中。 如需詳細資訊，請參閱[Core. 字串模組](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d)。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
