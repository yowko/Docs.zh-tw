---
title: 將字串分隔成子字串
description: 瞭解用來解壓縮字串元件的不同技術，包括字串、分割、正則運算式和字串。
ms.date: 10/30/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET], breaking up
ms.openlocfilehash: 88947c4576b0496e4b4e45042d665e3ca5857c53
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "93403607"
---
# <a name="extract-substrings-from-a-string"></a>從字串中解壓縮子字串

本文涵蓋一些用於解壓縮部分字串的不同技術。

- 當您想要的子字串以已知的分隔字元分隔 (或字元) 時，請使用 [Split 方法](#stringsplit-method) 。
- 當字串符合固定模式時，[正則運算式](#regular-expressions)會很有用。
- 當您不想要將字串中的 *所有* 子字串解壓縮時，請搭配使用 [IndexOf 和 Substring 方法](#stringindexof-and-stringsubstring-methods)。

## <a name="stringsplit-method"></a>字串. Split 方法

<xref:System.String.Split%2A?displayProperty=nameWithType> 提供數個多載，可協助您根據指定的一或多個分隔字元，將字串分割成子字串群組。 您可以選擇限制最終結果中的子字串總數、修剪子字串的空白字元，或排除空白的子字串。

下列範例顯示三個不同的多載 `String.Split()` 。 第一個範例會呼叫多載， <xref:System.String.Split(System.Char[])> 而不會傳遞任何分隔字元。 當您未指定任何分隔字元時， `String.Split()` 會使用預設分隔符號（也就是空白字元）來分割字串。

[!code-csharp-interactive[Intro#1](snippets/parse-strings/csharp/intro.cs#1)]
:::code language="vb" source="snippets/parse-strings/vb/intro.vb" id="1":::

如您所見， () 的句點字元 `.` 都包含在兩個子字串中。 如果您想要排除句號字元，您可以新增句點字元做為額外的分隔字元。 下一個範例會示範如何進行。

[!code-csharp-interactive[Intro#1](snippets/parse-strings/csharp/intro.cs#2)]
:::code language="vb" source="snippets/parse-strings/vb/intro.vb" id="2":::

這段期間已從子字串中消失，但現在已包含兩個額外的空白子字串。 這些空白子字串代表單字和其後接句點之間的子字串。 若要省略所產生陣列中的空白子字串，您可以呼叫多載 <xref:System.String.Split(System.Char[],System.StringSplitOptions)> ，並 <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> 為 `options` 參數指定。

[!code-csharp-interactive[Intro#1](snippets/parse-strings/csharp/intro.cs#3)]
:::code language="vb" source="snippets/parse-strings/vb/intro.vb" id="3":::

## <a name="regular-expressions"></a>規則運算式

如果您的字串符合固定模式，您可以使用正則運算式來解壓縮和處理其元素。 例如，如果字串的格式為「 *數位**運算元* ** 」，則您可以使用 [正則運算式](regular-expressions.md)來將字串的元素解壓縮並加以處理。 以下是範例：

:::code language="csharp" source="snippets/parse-strings/csharp/regex.cs" id="1" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/regex.vb" id="1":::

正則運算式模式的 `(\d+)\s+([-+*/])\s+(\d+)` 定義如下：

|模式|描述|
|-------------|-----------------|
|`(\d+)`|比對一個或多個十進位數字。 這是第一個擷取群組。|
|`\s+`|符合一或多個空白字元。|
|`([-+*/])`|符合算術運算子正負號 (+、-、* 或/) 。 這是第二個擷取群組。|
|`\s+`|符合一或多個空白字元。|
|`(\d+)`|比對一個或多個十進位數字。 這是第三個擷取群組。|

您也可以使用正則運算式，根據模式（而不是一組固定的字元）從字串中解壓縮子字串。 當發生下列其中一種情況時，這是常見的情況：

- 一個或多個分隔符號在實例中不 *一定* 會當做分隔符號 <xref:System.String> 。

- 分隔符號的序列和數目是變數或未知的。

例如， <xref:System.String.Split%2A> 方法不能用來分割下列字串，因為 `\n` (行) 字元的數目是變數，而且不一定會當做分隔符號。

```text
[This is captured\ntext.]\n\n[\n[This is more captured text.]\n]
\n[Some more captured text:\n   Option1\n   Option2][Terse text.]
```

正則運算式可以輕鬆地分割此字串，如下列範例所示。

:::code language="csharp" source="snippets/parse-strings/csharp/regex.cs" id="2" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/regex.vb" id="2":::

正則運算式模式的 `\[([^\[\]]+)\]` 定義如下：

|模式|描述|
|-------------|-----------------|
|`\[`|符合左括弧。|
|`([^\[\]]+)`|比對不是開頭或右括弧的任何字元一或多次。 這是第一個擷取群組。|
|`\]`|符合右括弧。|

<xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType>方法幾乎與相同 <xref:System.String.Split%2A?displayProperty=nameWithType> ，不同之處在于它會根據正則運算式模式（而非固定字元集）來分割字串。 例如，下列範例會使用 <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> 方法來分割字串，其中包含以多個連字號和其他字元組合分隔的子字串。

:::code language="csharp" source="snippets/parse-strings/csharp/regex.cs" id="3" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/regex.vb" id="3":::

正則運算式模式的 `\s-\s?[+*]?\s?-\s` 定義如下：

|模式|描述|
|-------------|-----------------|
|`\s-`|比對空白字元後面接著連字號的空白字元。|
|`\s?`|比對零個或一個空白字元。|
|`[+*]?`|比對出現零次或一次以上的 + 或 * 字元。|
|`\s?`|比對零個或一個空白字元。|
|`-\s`|比對後接空白字元的連字號。|

## <a name="stringindexof-and-stringsubstring-methods"></a>IndexOf 和 String Substring 方法

如果您對字串中的所有子字串都不感興趣，您可能會想要使用其中一個字串比較方法，以傳回相符項開始的索引。 然後您可以呼叫 <xref:System.String.Substring%2A> 方法，將您想要的子字串解壓縮。 字串比較方法包括：

- <xref:System.String.IndexOf%2A>，傳回字串實例中第一次出現字元或字串的以零為基底的索引。

- <xref:System.String.IndexOfAny%2A>，會在字元陣列中第一次出現任何字元的目前字串實例中傳回以零為基底的索引。

- <xref:System.String.LastIndexOf%2A>，傳回字串實例中最後一次出現字元或字串的以零為基底的索引。

- <xref:System.String.LastIndexOfAny%2A>，會在字元陣列中任何字元最後一次出現的目前字串實例中傳回以零為基底的索引。

下列範例會使用 <xref:System.String.IndexOf%2A> 方法來尋找字串中的句號。 然後，它會使用 <xref:System.String.Substring%2A> 方法來傳回完整的句子。

:::code language="csharp" source="snippets/parse-strings/csharp/indexof.cs" id="1" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/indexof.vb" id="1":::

## <a name="see-also"></a>請參閱

- [.NET 中的基底字元串作業](basic-string-operations.md)
- [.NET 正則運算式](regular-expressions.md)
- [如何使用字串剖析字串。以 C 分隔#](../../csharp/how-to/parse-strings-using-split.md)
