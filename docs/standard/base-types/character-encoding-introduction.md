---
title: .NET 中的字元編碼簡介
description: 了解 .NET 中的編碼及解碼字元。
ms.date: 03/09/2020
no-loc:
- Rune
- char
- string
dev_langs:
- csharp
helpviewer_keywords:
- encoding, understanding
ms.openlocfilehash: 85349e1e1c4eca4dd3ef7980f48350a4145fca24
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599863"
---
# <a name="character-encoding-in-net"></a>.NET 中的字元編碼

本文提供 .NET 所使用的字元編碼系統簡介。 本文說明 <xref:System.String> 、 <xref:System.Char> 、 <xref:System.Text.Rune> 和 <xref:System.Globalization.StringInfo> 類型如何與 Unicode、utf-16 和 utf-8 搭配使用。

在這裡 *，「詞彙」* 一詞是用來*做為單一顯示元素*的一般意義。 常見的範例包括字母 "a"、符號 "@" 和表情 " 🐂 "。 有時看起來像一個字元實際上是由多個獨立的顯示專案組成，如[語素簇](#grapheme-clusters)叢集上的一節所說明。

## <a name="the-string-and-char-types"></a>string和 char 類型

類別的實例 [string](xref:System.String) 代表一些文字。 `string`邏輯上是16位值的序列，其中每一個都是結構的實例 [char](xref:System.Char) 。 [ string 。Length](xref:System.String.Length)屬性會傳回 `char` 實例中的實例數目 `string` 。

下列範例函式會以十六進位標記法印出中所有實例的值 `char` `string` ：

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::

將 string "Hello" 傳遞至此函式，您會得到下列輸出：

```csharp
PrintChars("Hello");
```

```output
"Hello".Length = 5
s[0] = 'H' ('\u0048')
s[1] = 'e' ('\u0065')
s[2] = 'l' ('\u006c')
s[3] = 'l' ('\u006c')
s[4] = 'o' ('\u006f')
```

每個字元都是以單一 `char` 值表示。 該模式適用于大部分世界的語言。 例如，以下是兩個中文字元的輸出，聽起來像是*nǐ hǎo* ，而 Mean 為*Hello*：

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

不過，對於某些語言以及某些符號和表情，它會採用兩個 `char` 實例來表示單一字元。 例如，比較單字中的字元和 `char` 實例，這是指 Osage 語言中的*Osage* ：

```csharp
PrintChars("𐓏𐓘𐓻𐓘𐓻𐓟 𐒻𐓟");
```

```output
"𐓏𐓘𐓻𐓘𐓻𐓟 𐒻𐓟".Length = 17
s[0] = '�' ('\ud801')
s[1] = '�' ('\udccf')
s[2] = '�' ('\ud801')
s[3] = '�' ('\udcd8')
s[4] = '�' ('\ud801')
s[5] = '�' ('\udcfb')
s[6] = '�' ('\ud801')
s[7] = '�' ('\udcd8')
s[8] = '�' ('\ud801')
s[9] = '�' ('\udcfb')
s[10] = '�' ('\ud801')
s[11] = '�' ('\udcdf')
s[12] = ' ' ('\u0020')
s[13] = '�' ('\ud801')
s[14] = '�' ('\udcbb')
s[15] = '�' ('\ud801')
s[16] = '�' ('\udcdf')
```

在上述範例中，空格以外的每個字元都是由兩個 `char` 實例表示。

單一 Unicode 表情也會以兩個表示 `char` ，如下列範例所示，其中顯示 ox 的表情：

```
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

這些範例顯示 `string.Length` 表示實例數目的值， `char` 不一定表示顯示的字元數。 單一 `char` 實例本身不一定代表一個字元。

`char`對應至單一字元的配對稱為*代理配對*。 若要瞭解它們的使用方式，您必須瞭解 Unicode 和 UTF-16 編碼。

## <a name="unicode-code-points"></a>Unicode 字碼指標

Unicode 是在各種平臺上使用的國際編碼標準，以及各種語言和腳本。

Unicode 標準定義了超過1100000個程式[代碼點](https://www.unicode.org/glossary/#code_point)。 程式碼點是一個整數值，其範圍可以從0到 `U+10FFFF` （十進位1114111）。 有些程式碼點會指派給字母、符號或表情。 其他會指派給控制文字或字元顯示方式的動作，例如前進到新行。 尚未指派許多程式碼點。

以下是一些程式碼點指派範例，其中顯示的是 Unicode 圖表的連結：

|Decimal|Hex       |範例|描述|
|------:|----------|-------|-----------|
|10     | `U+000A` |N/A| [換行字元](https://www.unicode.org/charts/PDF/U0000.pdf) |
|65     | `U+0061` | a | [拉丁小寫字母 A](https://www.unicode.org/charts/PDF/U0000.pdf) |
|562    | `U+0232` | Ȳ | [拉丁文大寫字母 Y 加上長音符](https://www.unicode.org/charts/PDF/U0180.pdf) |
|68675 | `U+10C43`| 𐱃 | [舊的土耳其文字母](https://www.unicode.org/charts/PDF/U10C00.pdf) |
|127801| `U+1F339`| 🌹 | [玫瑰表情](https://www.unicode.org/charts/PDF/U1F300.pdf) |

程式碼點通常是使用語法來參考 `U+xxxx` ，其中 `xxxx` 是十六進位編碼的整數值。

在完整範圍的程式碼點中有兩個子範圍：

* 範圍內的**基本多語系平面（BMP）** `U+0000..U+FFFF` 。 這個16位範圍提供65536的程式碼點，足以涵蓋世界上大部分的書寫系統。
* 範圍中的**補充程式碼點** `U+10000..U+10FFFF` 。 這個21位範圍提供超過一百萬個額外的程式碼點，可用於較不知名的語言和其他用途，例如 emoji。

下圖說明 BMP 和補充程式碼點之間的關聯性。

:::image type="content" source="media/character-encoding-introduction/bmp-and-supplementary.svg" alt-text="BMP 和補充程式碼點":::

## <a name="utf-16-code-units"></a>UTF-16 程式碼單位

16位 Unicode 轉換格式（[utf-16](https://www.unicode.org/faq/utf_bom.html#UTF16)）是使用16位程式*代碼單位*來代表 Unicode 程式碼點的字元編碼系統。 .NET 會使用 UTF-16 來編碼中的文字 `string` 。 `char`實例代表16位的程式碼單位。

單一16位程式碼單位可以代表基本多語系平面之16位範圍內的任何程式碼點。 但對於補充範圍中的程式碼點， `char` 則需要兩個實例。

## <a name="surrogate-pairs"></a>代理配對

將 2 16 位值轉譯為單一21位值，是由稱為*代理程式碼點*的特殊範圍 `U+D800` （從到 `U+DFFF` （十進位55296到57343）（含）所組成。

下圖說明 BMP 和代理程式碼點之間的關聯性。

:::image type="content" source="media/character-encoding-introduction/bmp-and-surrogate.svg" alt-text="BMP 和代理程式碼點":::

當*高代理*程式碼點（ `U+D800..U+DBFF` ）緊接在*低代理*程式碼點（）後面時 `U+DC00..U+DFFF` ，會使用下列公式，將配對解讀為補充程式碼點：

```
code point = 0x10000 +
  ((high surrogate code point - 0xD800) * 0x0400) +
  (low surrogate code point - 0xDC00)
```

以下是使用小數點標記法的相同公式：

```
code point = 65,536 +
  ((high surrogate code point - 55,296) * 1,024) +
  (low surrogate code point - 56,320)
```

*高*代理程式碼點的數位值不會高於*低*代理程式碼點。 高代理程式碼點稱為「高」，因為它是用來計算完整21位程式碼點範圍的高序位11位。 低代理程式碼點用來計算較低順序的10位。

例如，對應至代理配對的實際程式碼點，其 `0xD83C` `0xDF39` 計算方式如下：

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

以下是使用小數點標記法的相同計算：

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

先前的範例示範， `"\ud83c\udf39"` 是先前所述之程式碼點的 utf-16 編碼方式 `U+1F339 ROSE ('🌹')` 。

## <a name="unicode-scalar-values"></a>Unicode 純量值

「Unicode 純量[值](https://www.unicode.org/glossary/#unicode_scalar_value)」一詞指的是代理程式碼點以外的所有程式碼點。 換句話說，純量值就是指派了一個字元的任何程式碼點，或未來可以指派一個字元。 此處的「字元」指的是可指派給程式碼點的任何專案，包括控制文字或字元顯示方式的動作。

下圖說明純量值的程式碼點。

:::image type="content" source="media/character-encoding-introduction/scalar-values.svg" alt-text="純量值":::

### <a name="the-rune-type-as-a-scalar-value"></a>Rune類型，做為純量值

從 .NET Core 3.0 開始， <xref:System.Text.Rune?displayProperty=fullName> 類型代表 Unicode 純量值。 **`Rune`在 .NET Core 2.x 或 .NET Framework 4.x 中無法使用。**

這些函式 `Rune` 會驗證產生的實例是否為有效的 Unicode 純量值，否則會擲回例外狀況。 下列範例會顯示成功具現化實例的程式碼， `Rune` 因為輸入代表有效的純量值：

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetValid":::

下列範例會擲回例外狀況，因為程式碼點位於代理範圍內，而且不屬於代理配對：

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidSurrogate":::

下列範例會擲回例外狀況，因為程式碼點超出補充範圍：

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidHigh":::

### <a name="rune-usage-example-changing-letter-case"></a>Rune使用範例：變更字母大小寫

如果是來自代理程式配對，則會採用 `char` 並假設其使用的程式碼點為純量值，因此無法正確運作 `char` 。 例如，請考慮下列在 <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> 中的每個上呼叫的方法 char string ：

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::

如果 `input` string 包含小寫的德字塞號 `er` （ `𐑉` ），則此程式碼不會將它轉換成大寫（ `𐐡` ）。 程式碼會 `char.ToUpperInvariant` 分別在每個代理程式碼點和上呼叫 `U+D801` `U+DC49` 。 但是 `U+D801` ，本身並沒有足夠的資訊來將它識別為小寫字母，所以將 `char.ToUpperInvariant` 它單獨保留。 而且它會以 `U+DC49` 相同的方式處理。 結果是中的小寫 ' 𐑉 ' `input` string 不會轉換成大寫的 ' 𐑉 '。

以下兩個選項可將正確轉換 string 成大寫：

* <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType>在輸入上呼叫， string 而不是 `char` 逐一查看 `char` 。 `string.ToUpperInvariant`方法可以存取每個代理配對中的兩個部分，以便能夠正確處理所有的 Unicode 程式碼點。
* 逐一查看 Unicode 純量值做為 `Rune` 實例，而不是 `char` 實例，如下列範例所示。 因為 `Rune` 實例是有效的 Unicode 純量值，所以可以傳遞給預期會在純量值上運作的 api。 例如， <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> 如下列範例所示呼叫會提供正確的結果：

  :::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::

### <a name="other-rune-apis"></a>其他 Rune api

型別會 `Rune` 公開許多 api 的類比 `char` 。 例如，下列方法會鏡像類型上的靜態 Api `char` ：

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

若要從實例取得原始純量值 `Rune` ，請使用 <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> 屬性。

若要將 `Rune` 實例轉換回的序列 `char` ，請使用 <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> 或 <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> 方法。

由於任何 Unicode 純量值都是由單一 `char` 或代理程式配對來表示，因此任何 `Rune` 實例最多可代表2個 `char` 實例。 使用 <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> 來查看需要多少 `char` 實例來表示 `Rune` 實例。

如需 .NET 類型的詳細資訊 `Rune` ，請參閱[ `Rune` API 參考](xref:System.Text.Rune)。

## <a name="grapheme-clusters"></a>語素簇叢集

可能會因為多個程式碼點的組合而產生一個字元，因此，經常用來取代 "character" 的更具描述性詞彙就是[語素簇 cluster](https://www.unicode.org/glossary/#grapheme_cluster)。 .NET 中的對等詞彙是[text 元素](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A)。

請考慮「 `string` a」、「×」實例。 「×」和「」 `👩🏽‍🚒` 。 如果您的作業系統會依照 Unicode 標準的指定來處理它們，則這些實例中的每一個 `string` 都會顯示為單一文字元素或語素簇叢集。 但最後兩個則是由一個以上的純量值程式碼點表示。

* string"A" 是以一個純量值表示，且包含一個 `char` 實例。

  * `U+0061 LATIN SMALL LETTER A`

* 「 string ×」是以一個純量值表示，並包含一個 `char` 實例。

  * `U+00E1 LATIN SMALL LETTER A WITH ACUTE`

* 「 string ×」看起來與「×」相同，但以兩個純量值表示，並包含兩個 `char` 實例。

  * `U+0061 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* 最後， string " `👩🏽‍🚒` " 會以四個純量值表示，並包含七個 `char` 實例。

  * `U+1F469 WOMAN`（補充範圍，需要代理配對）
  * `U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4`（補充範圍，需要代理配對）
  * `U+200D ZERO WIDTH JOINER`
  * `U+1F692 FIRE ENGINE`（補充範圍，需要代理配對）

在上述一些範例中（例如結合輔色修飾詞或外觀色調修飾詞），程式碼點不會在螢幕上顯示為獨立元素。 相反地，它是用來修改之前出現的文字元素外觀。 這些範例顯示，它可能會採用多個純量值來組成我們將其視為單一「字元」或「語素簇叢集」的意義。

若要列舉的語素簇叢集 `string` ，請使用 <xref:System.Globalization.StringInfo> 類別，如下列範例所示。 如果您熟悉 Swift，則 .NET 類型在 `StringInfo` 概念上類似于[swift 的 `character` 類型](https://developer.apple.com/documentation/swift/character)。

### <a name="example-count-char-rune-and-text-element-instances"></a>範例： count char 、 Rune 和 text 元素實例

在 .NET Api 中，語素簇叢集稱為「*文字」元素*。 下列方法示範 `char` `Rune` 中、和文字元素實例之間的差異 `string` ：

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::

如果您在 .NET Framework 或 .NET Core 3.1 或更早版本中執行此程式碼，則會顯示表情的文字元素計數 `4` 。 這是因為在 .NET 5 中修正的類別中有 bug `StringInfo` 。

### <a name="example-splitting-string-instances"></a>範例：分割 string 實例

分割 `string` 實例時，請避免分割代理項配對和語素簇叢集。 請考慮下列不正確程式碼的範例，其打算在中插入分行符號，每10個字元 string ：

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::

因為此程式碼會列舉 `char` 實例，所以會分割一個跨10界限的代理配對， `char` 並在其間插入一個分行符號。 這項插入會導入資料損毀，因為代理程式碼點僅有意義的配對。

如果您列舉 `Rune` 實例（純量值）而不是實例，則不會去除資料損毀的可能性 `char` 。 一組 `Rune` 實例可能會構成跨越10界限的語素簇叢集 `char` 。 如果語素簇叢集集已分割，則無法正確地加以解讀。

較好的方法是藉 string 由計算語素簇叢集或文字元素來中斷，如下列範例所示：

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::

如先前所述，在 .net 5 以外的 .NET 中， `StringInfo` 類別可能會不正確地處理某些語素簇叢集。

## <a name="utf-8-and-utf-32"></a>UTF-8 和 UTF-32

上述章節著重于 UTF-16，因為這是 .NET 用來對實例進行編碼的原因 `string` 。 Unicode [utf-8](https://www.unicode.org/faq/utf_bom.html#UTF8)和[UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32)還有其他編碼系統。 這些編碼分別使用8位程式碼單位和32位程式碼單位。

就像 UTF-16，UTF-8 需要多個程式碼單位來代表一些 Unicode 純量值。 UTF-32 可以代表單一32位程式碼單位中的任何純量值。

以下範例顯示在這三個 Unicode 編碼系統中，如何表示相同的 Unicode 程式碼點：

```
Scalar: U+0061 LATIN SMALL LETTER A ('a')
UTF-8 : [ 61 ]           (1x  8-bit code unit  = 8 bits total)
UTF-16: [ 0061 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 00000061 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+0429 CYRILLIC CAPITAL LETTER SHCHA ('Щ')
UTF-8 : [ D0 A9 ]        (2x  8-bit code units = 16 bits total)
UTF-16: [ 0429 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 00000429 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+A992 JAVANESE LETTER GA ('ꦒ')
UTF-8 : [ EA A6 92 ]     (3x  8-bit code units = 24 bits total)
UTF-16: [ A992 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 0000A992 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+104CC OSAGE CAPITAL LETTER TSHA ('𐓌')
UTF-8 : [ F0 90 93 8C ]  (4x  8-bit code units = 32 bits total)
UTF-16: [ D801 DCCC ]    (2x 16-bit code units = 32 bits total)
UTF-32: [ 000104CC ]     (1x 32-bit code unit  = 32 bits total)
```

如先前所述，來自[代理配對](#surrogate-pairs)的單一 utf-16 程式碼單位本身毫無意義。 同樣地，如果單一 UTF-8 程式碼單位是以兩個、三個或四個用來計算純量值的序列，則不會有任何意義。

### <a name="endianness"></a>位元組序

在 .NET 中，的 UTF-16 程式碼單位會以 string 16 位整數（實例）的序列儲存在連續記憶體中 `char` 。 個別程式碼單位的位會根據目前架構的[位元組](https://en.wikipedia.org/wiki/Endianness)程式來配置。

在以位元組為基礎的架構上，由 string utf-16 程式碼點組成的會 `[ D801 DCCC ]` 在記憶體中配置為位元組 `[ 0x01, 0xD8, 0xCC, 0xDC ]` 。 在以大到小的結構上，相同的 string 會在記憶體中配置為位元組 `[ 0xD8, 0x01, 0xDC, 0xCC ]` 。

彼此通訊的電腦系統必須同意透過網路的資料標記法。 大部分的網路通訊協定都會在傳輸文字時使用 UTF-8 做為標準，部分是為了避免因大型電腦與小序電腦通訊而產生的問題。 由 string utf-8 程式碼點組成的，一律會以 `[ F0 90 93 8C ]` 位元組表示， `[ 0xF0, 0x90, 0x93, 0x8C ]` 而不論是否為 endian。

若要使用 UTF-8 來傳輸文字，.NET 應用程式通常會使用類似下列範例的程式碼：

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

在上述範例中，方法[GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A)會將 utf-16 解碼 `string` 回一系列 Unicode 純量值，然後將這些純量值重新編碼為 utf-8，並將產生的序列放入 `byte` 陣列中。 方法[編碼 GetString](xref:System.Text.UTF8Encoding.GetString%2A)會執行相反的轉換，將 utf-8 `byte` 陣列轉換成 utf-16 `string` 。

> [!WARNING]
> 由於 UTF-8 在網際網路上很常見，因此從網路讀取未經處理的位元組，並將資料視為 UTF-8，可能會很有吸引力。 不過，您應該驗證它的格式是否正確。 惡意用戶端可能會將格式不正確的 UTF-8 提交給您的服務。 如果您以正確格式的方式操作該資料，可能會在您的應用程式中造成錯誤或安全性漏洞。 若要驗證 UTF-8 資料，您可以使用類似的方法 `Encoding.UTF8.GetString` ，將傳入的資料轉換成時，會執行驗證 `string` 。

### <a name="well-formed-encoding"></a>格式正確的編碼

格式正確的 Unicode 編碼是 string 可以明確解碼，而且不會發生錯誤的程式碼單位序列。 格式正確的資料可以在 UTF-8、UTF-16 和 UTF-32 之間自由地來回轉碼。

編碼順序是否語式正確的問題，或不與機器架構的 endian 格式無關。 格式不正確的 UTF-8 順序格式不正確，其方式與以大到小的電腦相同。

以下是一些格式錯誤編碼的範例：

* 在 UTF-8 中，順序格式不 `[ 6C C2 61 ]` 正確，因為 `C2` 後面不能有 `61` 。

* 在 UTF-16 中，順序 `[ DC00 DD00 ]` （或 c # 中的 string `"\udc00\udd00"` ）格式不正確，因為低的代理 `DC00` 不能後面接著另一個低代理 `DD00` 。

* 在 UTF-32 中，順序的 `[ 0011ABCD ]` 格式不正確，因為超出 `0011ABCD` Unicode 純量值的範圍。

在 .NET 中， `string` 實例幾乎一律包含格式正確的 utf-16 資料，但不保證。 下列範例顯示在實例中建立格式不正確之 UTF-16 資料的有效 c # 程式碼 `string` 。

* 格式不正確的常值：

  ```csharp
  const string s = "\ud800";
  ```

* 用來分割代理配對的子字串：

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

之類 [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) 的 api 不會傳回格式不正確的 `string` 實例。 `Encoding.GetString`和 `Encoding.GetBytes` 方法會偵測輸入中格式不正確的序列，並在產生輸出時執行字元替代。 例如，如果 [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) 在輸入中看到非 ASCII 位元組（在 u + 0000 的範圍外），它會將 '？ ' 插入傳回的 `string` 實例中。 [`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A)`U+FFFD REPLACEMENT CHARACTER ('�')`在傳回的實例中，取代格式不正確的 utf-8 序列 `string` 。 如需詳細資訊，請參閱[Unicode 標準](https://www.unicode.org/versions/latest/)，第5.22 和3.9 節。

`Encoding`當出現格式不正確的序列時，內建類別也可以設定為擲回例外狀況，而不是執行字元替代。 這種方法通常用於可能無法接受字元替代的安全性敏感應用程式中。

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

如需如何使用內建類別的詳細資訊 `Encoding` ，請參閱[如何在 .net 中使用字元編碼類別](character-encoding.md)。

## <a name="see-also"></a>請參閱

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [全球化和當地語系化](../globalization-localization/index.md)
