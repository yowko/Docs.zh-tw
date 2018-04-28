---
title: 字串 (F#)
description: "了解 F # 'string' 類型為 Unicode 字元序列所代表的不可變的文字。"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: bf3c15db43c6419222dc3e5b32ac8947a53982f0
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="strings"></a>字串

> [!NOTE]
本文中的 API 參考連結將帶您前往 MSDN。  docs.microsoft.com API 參考不完整。

`string`類型不可變的文字表示為 Unicode 字元序列。 `string` 是 `System.String` 在 .NET Framework 中的別名。

## <a name="remarks"></a>備註
字串常值是以引號 （"） 字元分隔。 反斜線字元 (\)用來編碼某些特殊字元。 反斜線和在一起的下一個字元稱為*逸出序列*。 逸出序列支援 F # 字串常值會顯示下表中。

|字元|逸出序列|
|---------|---------------|
|退格鍵|\b|
|新行字元|\n|
|歸位字元|\r|
|索引標籤|\t|
|反斜線|\\|
|引號|\"|
|所有格符號|\'|
|Unicode 字元|\u*XXXX*或 \U*XXXXXXXX* (其中*X*表示十六進位數字)|

如果前面加上 @ 符號，常值是逐字字串。 這表示，則會忽略任何逸出序列，不同之處在於兩個引號字元視為一個引號字元。

此外，可能會以三引號括住字串。 在此情況下，會忽略所有逸出序列，包括雙引號字元。 若要指定字串，其中包含內嵌加引號的字串，您可以使用逐字字串或三重加上引號的字串。 如果您使用逐字字串時，您必須指定兩個引號字元來表示單一引號字元。 如果您使用 triple 加上引號的字串，您可以使用單引號字元沒有它們正在剖析為字串的結尾。 當您使用 XML 或其他結構包含內嵌的引號時，這個技巧就很有用。

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

在程式碼中，接受字串有分行符號，分行符號會逐字解譯為換行，除非反斜線字元就分行前的最後一個字元。 使用反斜線字元時，會忽略在下一行的開頭空白。 下列程式碼會產生字串`str1`，並且其值`"abc\n     def"`和字串`str2`，並且其值`"abcdef"`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

您可以存取個別字元在字串中的使用類似陣列的語法，如下所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

輸出為 `b`。

或者，您可以使用陣列的配量語法，來擷取子字串，如下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

輸出如下。

```
abc
def
```

您可以表示不帶正負號位元組，型別陣列的 ASCII 字串`byte[]`。 新增後置詞`B`為字串常值以指出它是 ASCII 字串。 ASCII 字串常值的位元組陣列搭配使用支援相同的逸出序列，做為 Unicode 字串，除了 Unicode 逸出序列。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]
    
## <a name="string-operators"></a>字串運算子
有兩種方式將字串串連： 使用`+`運算子或使用`^`運算子。 `+`運算子會維護與.NET Framework 字串處理功能的相容性。

下列範例說明字串串連。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]
    
## <a name="string-class"></a>字串類別
因為在 F # 字串型別實際上是以.NET Framework`System.String`輸入所有`System.String`成員都可以使用。 這包括`+`運算子，就會用來串連字串，`Length`屬性，而`Chars`屬性，傳回的字串為 Unicode 字元陣列。 如需字串的詳細資訊，請參閱`System.String`。

使用`Chars`屬性`System.String`，您可以存取個別字元在字串中的指定的索引，如下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]
    
## <a name="string-module"></a>字串模組
字串處理的額外功能隨附於`String`中的模組`FSharp.Core`命名空間。 如需詳細資訊，請參閱[Core.String 模組](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d)。

## <a name="see-also"></a>另請參閱
[F# 語言參考](index.md)
