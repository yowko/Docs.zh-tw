---
title: char.Net 中的 acter 編碼簡介
description: 瞭解如何 char 在 .net 中 acter 編碼和解碼。
ms.date: 03/09/2020
no-loc:
- Rune
- char
- string
dev_langs:
- csharp
helpviewer_keywords:
- encoding, understanding
ms.openlocfilehash: a5d838176bf4437a295ebe6c2cea8b1fe0eeeb61
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656289"
---
# <a name="character-encoding-in-net"></a>.NET 中的字元編碼

本文提供 char .net 所使用之 acter 編碼系統的簡介。 本文說明 <xref:System.String> 、 <xref:System.Char> 、 <xref:System.Text.Rune> 和 <xref:System.Globalization.StringInfo> 類型如何使用 Unicode、utf-16 和 utf-8。

「詞彙」（ * char acter* ）一詞的用途是在*讀者視為單一顯示元素*的一般意義上使用。 常見範例為字母 "a"、符號 "@" 和表情 " 🐂 "。 有時看起來像 char 是一個 acter 實際上是由多個獨立的顯示元素組成，如 [語素簇](#grapheme-clusters) 叢集上的章節所述。

## <a name="the-no-locstring-and-no-locchar-types"></a>string和 char 類型

類別的實例 [string](xref:System.String) 代表一些文字。 `string`是邏輯上的16位值序列，每個值都是結構的實例 [char](xref:System.Char) 。 [ string 。Length](xref:System.String.Length)屬性會傳回 `char` 實例中的實例數目 `string` 。

下列範例函式會以十六進位標記法來印出中所有 `char` 實例的值 `string` ：

：：： code language = "csharp" source = "程式碼片段/ char acter-編碼-簡介/csharp/PrintStringChars .cs" id = "SnippetPrintChars"：：：

將 string "Hello" 傳遞至此函式，您會取得下列輸出：

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

每個 char acter 都是以單一 `char` 值表示。 這種模式適用于大部分世界的語言。 例如，以下是兩個中文 acters 的輸出 char ，這聽起來像是 *nǐ hǎo* ，意思是 *Hello*：

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

不過，對於某些語言以及某些符號和表情符號，會採用兩個 `char` 實例來代表單一 char acter。 例如，比較單字中的 char acters 和 `char` 實例，這表示 Osage 語言中的 *Osage* ：

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

在上述範例中， char 除了空格以外的每個 acter 都是以兩個實例來表示 `char` 。

單一 Unicode 表情也會以兩種 `char` 方式表示，如下列範例所示，顯示 ox 的表情：

```
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

這些範例顯示的值 `string.Length` （指出 `char` 實例數目）不一定表示顯示的 char acters 數目。 單一 `char` 實例本身不一定代表 char acter。

`char`對應至單一 acter 的配對 char 稱為*代理配對*。 若要瞭解其運作方式，您必須瞭解 Unicode 和 UTF-16 編碼。

## <a name="unicode-code-points"></a>Unicode 字碼指標

Unicode 是國際編碼標準，可用於各種不同的平臺，以及各種語言和腳本。

Unicode 標準定義1100000以上的程式 [代碼點](https://www.unicode.org/glossary/#code_point)。 程式碼點是一個整數值，範圍從0到 `U+10FFFF` (decimal 1114111) 。 某些程式碼點會指派給字母、符號或表情。 其他會指派給控制文字或 acters 顯示方式的動作 char ，例如前進至新行。 許多程式碼點尚未指派。

以下是程式碼點指派的一些範例，其中包含出現在其中的 Unicode char ts 連結：

|小數位數|Hex       |範例|描述|
|------:|----------|-------|-----------|
|10     | `U+000A` |N/A| [換行字元](https://www.unicode.org/charts/PDF/U0000.pdf) |
|65     | `U+0061` | a | [拉丁小寫字母 A](https://www.unicode.org/charts/PDF/U0000.pdf) |
|562    | `U+0232` | Ȳ | [拉丁文大寫字母 Y 加上音符號](https://www.unicode.org/charts/PDF/U0180.pdf) |
|68675 | `U+10C43`| 𐱃 | [舊的土耳其文字母鄂爾](https://www.unicode.org/charts/PDF/U10C00.pdf) |
|127801| `U+1F339`| 🌹 | [玫瑰的表情](https://www.unicode.org/charts/PDF/U1F300.pdf) |

程式碼點通常是使用語法來參考 `U+xxxx` ，其中 `xxxx` 是十六進位編碼的整數值。

在完整範圍的程式碼點中，有兩個子範圍：

* 範圍中的 **基本多語系平面 (BMP) ** `U+0000..U+FFFF` 。 這個16位範圍提供65536的程式碼點，足以涵蓋世界上大部分的書寫系統。
* 範圍內的**補充程式碼點** `U+10000..U+10FFFF` 。 這個21位範圍提供超過一百萬個額外的程式碼點，可用於較不知名的語言和其他用途，例如 emoji。

下圖說明 BMP 與補充程式碼點之間的關聯性。

:::image type="content" source="media/:::非 loc (char) ：：： acter-encoding-introduction/bmp-and-supplementary。 svg" "alt-text =" BMP 和補充程式碼點 "：：：

## <a name="utf-16-code-units"></a>UTF-16 程式碼單位

16位 Unicode 轉換格式 ([utf-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) 是 char acter 編碼系統，使用16位程式 *代碼單位* 來代表 Unicode 程式碼點。 .NET 使用 UTF-16 將中的文字編碼 `string` 。 `char`實例代表16位程式碼單位。

單一16位程式碼單位可以代表基本多語系平面之16位範圍內的任何程式碼點。 但是針對補充範圍中的程式碼點，需要兩個 `char` 實例。

## <a name="surrogate-pairs"></a>代理配對

將 2 16 位值轉譯成單一21位值是由稱為 *代理程式碼點*的特殊範圍所組成，從 `U+D800` 到 `U+DFFF` (decimal 55296 到 57343) （含）。

下圖說明 BMP 與代理程式碼點之間的關聯性。

:::image type="content" source="media/:::非 loc (char) ：：： acter-encoding-introduction/bmp-and-surrogate。 svg" "alt-text =" BMP 和代理程式碼點 "：：：

當 *高代理* 程式碼點 (`U+D800..U+DBFF`) 後面緊接著 *低代理* 程式碼點 () 時 `U+DC00..U+DFFF` ，會使用下列公式將配對解釋為補充程式碼點：

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

*高*代理程式碼點沒有比*低*代理程式碼點更高的數值。 高代理程式碼點稱為「高」，因為它是用來計算完整21位程式碼點範圍的高序位11位。 低代理程式碼點可用來計算較低順序的10位。

例如，對應至代理配對的實際程式碼點，其 `0xD83C` `0xDF39`  計算方式如下：

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

上述範例示範的 `"\ud83c\udf39"` 是稍早所述的程式 `U+1F339 ROSE ('🌹')` 代碼點 utf-16 編碼。

## <a name="unicode-scalar-values"></a>Unicode 純量值

Unicode 純量 [值](https://www.unicode.org/glossary/#unicode_scalar_value) 一詞是指代理程式碼點以外的所有程式碼點。 換句話說，純量值是指派 char acter 或可在未來指派 acter 的任何程式碼點 char 。 此處的「字元」指的是可指派給程式碼點的任何專案，其中包含控制文字或 acters 顯示方式的動作 char 。

下圖說明純量值的程式碼點。

:::image type="content" source="media/:::無 loc (char) ：：： acter-encoding-introduction/scalar-values svg" "alt-text =" 純量值 "：：：

### <a name="the-no-locrune-type-as-a-scalar-value"></a>以純量 Rune 值的類型

從 .NET Core 3.0 開始，此 <xref:System.Text.Rune?displayProperty=fullName> 型別代表 Unicode 純量值。 **`Rune` 不適用於 .NET Core 2.x 或 .NET Framework 4.x。**

這些 `Rune` 函數會驗證產生的實例是否為有效的 Unicode 純量值，否則會擲回例外狀況。 下列範例會顯示成功具現化實例的程式碼， `Rune` 因為輸入代表有效的純量值：

：：： code language = "csharp" source = "程式碼片段/ char acter-編碼-簡介/csharp/具現化 Rune s.cs" id = "SnippetValid"：：：

下列範例會擲回例外狀況，因為程式碼點是在代理範圍內，而不是代理組的一部分：

：：： code language = "csharp" source = "程式碼片段/ char acter-編碼-簡介/csharp/具現化 Rune s.cs" id = "SnippetInvalidSurrogate"：：：

下列範例會擲回例外狀況，因為程式碼點超出補充範圍：

：：： code language = "csharp" source = "程式碼片段/ char acter-編碼-簡介/csharp/具現化 Rune s.cs" id = "SnippetInvalidHigh"：：：

### <a name="no-locrune-usage-example-changing-letter-case"></a>Rune 使用範例：變更字母大小寫

使用的 API 會 `char` 假設它使用的程式碼點是純量值，如果 `char` 是來自代理組，則無法正確運作。 例如，請考慮下列在 <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> 中對每個進行呼叫的方法 char string ：

：：： code language = "csharp" source = "程式碼片段/ char acter-編碼-簡介/csharp/ConvertToUpper .cs" id = "SnippetBadExample"：：：

如果 `input` string () 包含小寫的 `er` 編碼方式 `𐑉` ，則此程式碼不會將它轉換成大寫 (`𐐡`) 。 程式碼會 `char.ToUpperInvariant` 在每個代理程式碼點上個別呼叫， `U+D801` 以及 `U+DC49` 。 但是 `U+D801` 本身並沒有足夠的資訊來將它識別為小寫字母，因此請 `char.ToUpperInvariant` 單獨保留。 而且會以 `U+DC49` 相同的方式處理。 結果是中的小寫 ' 𐑉 ' `input` string 不會轉換成大寫的 ' 𐑉 '。

以下是將 a 正確轉換成大寫的兩個選項 string ：

* <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType>在輸入上呼叫， string 而不是 `char` 逐一查看 `char` 。 `string.ToUpperInvariant`方法可以存取每個代理組的兩個部分，讓它能夠正確處理所有的 Unicode 程式碼點。
* 將 Unicode 純量值逐一查看為 `Rune` 實例，而不是 `char` 實例，如下列範例所示。 因為 `Rune` 實例是有效的 Unicode 純量值，所以可以傳遞給預期會在純量值上運作的 api。 例如， <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> 如下列範例所示呼叫會提供正確的結果：

  ：：： code language = "csharp" source = "程式碼片段/ char acter-編碼-簡介/csharp/ConvertToUpper .cs" id = "SnippetGoodExample"：：：

### <a name="other-no-locrune-apis"></a>其他 Rune api

此 `Rune` 類型會公開許多 api 的類比 `char` 。 例如，下列方法會在類型上鏡像靜態 Api `char` ：

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

若要從實例取得原始純量值 `Rune` ，請使用 <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> 屬性。

若要將 `Rune` 實例轉換回的序列 `char` ，請使用 <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> 或 <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> 方法。

因為任何 Unicode 純量值都是由單一 `char` 或代理配對來表示，所以任何 `Rune` 實例最多可以用2個 `char` 實例來表示。 使用 <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> 以查看需要多少 `char` 實例來表示 `Rune` 實例。

如需 .NET 類型的詳細資訊 `Rune` ，請參閱[ `Rune` API 參考](xref:System.Text.Rune)。

## <a name="grapheme-clusters"></a>語素簇叢集

charActer 可能會因為多個程式碼點組合而產生的結果，因此更具描述性的詞彙通常會用來取代 " char acter"[語素簇](https://www.unicode.org/glossary/#grapheme_cluster)叢集。 .NET 中的對等詞彙是 [text 元素](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A)。

請考慮「a」、「×」、「×」和「」 `string` 實例 `👩🏽‍🚒` 。 如果您的作業系統依 Unicode 標準所指定來處理它們，則每個 `string` 實例都會顯示為單一文字元素或語素簇叢集。 但最後兩個會以一個以上的純量值程式碼點來表示。

* string"A" 是以一個純量值表示，並包含一個 `char` 實例。

  * `U+0061 LATIN SMALL LETTER A`

* string"×" 是以一個純量值表示，並包含一個 `char` 實例。

  * `U+00E1 LATIN SMALL LETTER A WITH ACUTE`

* 「 string ×」看起來與「×」相同，但以兩個純量值表示，並包含兩個 `char` 實例。

  * `U+0061 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* 最後， string " `👩🏽‍🚒` " 是由四個純量值所表示，並包含七個 `char` 實例。

  * `U+1F469 WOMAN` (補充範圍，需要代理配對) 
  * `U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (補充範圍，需要代理配對) 
  * `U+200D ZERO WIDTH JOINER`
  * `U+1F692 FIRE ENGINE` (補充範圍，需要代理配對) 

在上述一些範例中（例如合併式輔色修飾詞或面板音調修飾詞），程式碼點不會顯示為螢幕上的獨立元素。 相反地，它會用來修改它之前的文字元素的外觀。 這些範例顯示，它可能會採用多個純量值，讓我們將其視為單一「 char acter」或「語素簇叢集」。

若要列舉的語素簇叢集 `string` ，請使用 <xref:System.Globalization.StringInfo> 類別，如下列範例所示。 如果您熟悉 Swift，.NET 型別在 `StringInfo` 概念上類似于 [swift 的 `character` 型](https://developer.apple.com/documentation/swift/character)別。

### <a name="example-count-no-locchar-no-locrune-and-text-element-instances"></a>範例： count char 、 Rune 和 text 元素實例

在 .NET Api 中，語素簇叢集稱為「 *文字」元素*。 下列方法示範 `char` 、 `Rune` 和中的 text 元素實例之間的差異 `string` ：

：：： code language = "csharp" source = "程式碼片段/ char acter-編碼-簡介/csharp/CountTextElements .cs" id = "SnippetCountMethod"：：：

：：： code language = "csharp" source = "程式碼片段/ char acter-編碼-簡介/csharp/CountTextElements .cs" id = "SnippetCallCountMethod"：：：

如果您在 .NET Framework 或 .NET Core 3.1 或更早版本中執行此程式碼，則會顯示表情的文字元素計數 `4` 。 這是因為 `StringInfo` .net 5 中已修正的類別中有錯誤。

### <a name="example-splitting-no-locstring-instances"></a>範例：分割 string 實例

分割 `string` 實例時，請避免分割代理組和語素簇叢集。 請考慮下列不正確的程式碼範例，這會在中插入每10個 acters 的分行符號 char string ：

：：： code language = "csharp" source = "程式碼片段/ char acter-編碼-簡介/csharp/InsertNewlines .cs" id = "SnippetBadExample"：：：

因為此程式碼會列舉 `char` 實例，所以跨10界限的代理組 `char` 將會被分割，並在其間插入一個新行。 這項插入會造成資料損毀，因為代理程式碼點只對成對有意義。

如果您將 `Rune` 實例列舉 (純量值) 而不是實例，則不會刪除資料損毀的可能性 `char` 。 一組 `Rune` 實例可能構成跨越10界限的語素簇叢集 `char` 。 如果語素簇叢集集已分割，則無法正確解讀。

更好的方法是藉 string 由計算語素簇叢集或文字元素來中斷，如下列範例所示：

：：： code language = "csharp" source = "程式碼片段/ char acter-編碼-簡介/csharp/InsertNewlines .cs" id = "SnippetGoodExample"：：：

不過如先前所述，在 .net 5 以外的 .NET 的實， `StringInfo` 類別可能會不正確地處理某些語素簇叢集。

## <a name="utf-8-and-utf-32"></a>UTF-8 和 UTF-32

上述幾節著重于 UTF-16，因為 .NET 會使用它來編碼 `string` 實例。 另外還有 Unicode [utf-8](https://www.unicode.org/faq/utf_bom.html#UTF8) 和 [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32)的編碼系統。 這些編碼方式分別使用8位程式碼單位和32位程式碼單位。

如同 UTF-16，UTF-8 需要多個程式碼單位來代表一些 Unicode 純量值。 32 UTF-7 可代表單一32位程式碼單位中的任何純量值。

以下是一些範例，顯示相同的 Unicode 程式碼點在這三個 Unicode 編碼系統中的呈現方式：

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

如先前所述，來自 [代理](#surrogate-pairs) 組的單一 utf-16 程式碼單位本身並無意義。 同樣地，如果單一 UTF-8 程式碼單位是以兩個、三個或四個用來計算純量值的順序，它本身就沒有意義。

### <a name="endianness"></a>位元組序

在 .NET 中，的 UTF-16 程式碼單位會以 string 一系列的16位整數 (實例) 的形式儲存在連續的記憶體中 `char` 。 個別程式碼單位的位會根據目前架構的 [位元組](https://en.wikipedia.org/wiki/Endianness) 順序配置。

在位元組由小到大的架構上，由 string utf-16 程式碼點組成的會 `[ D801 DCCC ]` 在記憶體中配置為位元組 `[ 0x01, 0xD8, 0xCC, 0xDC ]` 。 在以大到小的架構上，相同的會 string 在記憶體中配置為位元組 `[ 0xD8, 0x01, 0xDC, 0xCC ]` 。

彼此通訊的電腦系統必須同意網路上的資料標記法。 大部分的網路通訊協定都是在傳輸文字時使用 UTF-8 作為標準，以避免因為以位元組由小到大的電腦與以位元組由小到大的電腦通訊所產生的問題。 無論是否為位元組順序，由 string utf-8 程式碼點組成的 `[ F0 90 93 8C ]` 會一律以位元組表示 `[ 0xF0, 0x90, 0x93, 0x8C ]` 。

若要使用 UTF-8 來傳送文字，.NET 應用程式通常會使用類似下列範例的程式碼：

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

在上述範例中， [GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) 方法會將 utf-16 解碼 `string` 回一連串的 Unicode 純量值，然後將這些純量值重新編碼為 utf-8，然後將產生的序列放入 `byte` 陣列中。 方法 [編碼 GetString](xref:System.Text.UTF8Encoding.GetString%2A) 會執行相反的轉換，將 utf-8 `byte` 陣列轉換為 utf-16 `string` 。

> [!WARNING]
> 由於 UTF-8 在網際網路上很普遍，從網路讀取未經處理的位元組，並將資料視為 UTF-8，可能會很吸引人。 不過，您應該驗證它的格式是否正確。 惡意用戶端可能會將格式不正確的 UTF-8 提交至您的服務。 如果您以格式正確的方式操作該資料，則可能會導致您的應用程式發生錯誤或安全性漏洞。 若要驗證 UTF-8 資料，您可以使用類似的方法 `Encoding.UTF8.GetString` ，這會在將傳入資料轉換為時執行驗證 `string` 。

### <a name="well-formed-encoding"></a>格式正確的編碼

格式正確的 Unicode 編碼是 string 可明確解碼，且不會發生錯誤的一連串 unicode 純量值的程式碼單位。 格式正確的資料可以在 UTF-8、UTF-16 和 UTF-32 之間自由地來回轉碼。

編碼順序是否格式正確或不與電腦架構的位元組格式相關的問題。 格式不正確的 UTF-8 順序在位元組由大到小的電腦上的格式不正確。

以下是格式錯誤的編碼範例：

* 在 UTF-8 中，順序的 `[ 6C C2 61 ]` 格式不正確，因為 `C2` 後面不能有 `61` 。

* 在 UTF-16 中，順序 (， `[ DC00 DD00 ]` 或在 c # 中， string `"\udc00\udd00"`) 格式不正確，因為低代理 `DC00` 不能後面接著另一個低代理 `DD00` 。

* 在 32 UTF-8 中，順序的 `[ 0011ABCD ]` 格式不正確，因為超出 `0011ABCD` Unicode 純量值的範圍。

在 .NET 中， `string` 實例幾乎一律會包含格式正確的 utf-16 資料，但不保證如此。 下列範例顯示在實例中建立格式不正確之 UTF-16 資料的有效 c # 程式碼 `string` 。

* 格式不正確的常值：

  ```csharp
  const string s = "\ud800";
  ```

* string分割代理配對的 sub：

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

這類 Api [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) 不會傳回格式不正確的 `string` 實例。 `Encoding.GetString` 和 `Encoding.GetBytes` 方法會偵測輸入中格式不正確的序列，並在 char 產生輸出時執行 acter 替代。 例如，如果在 [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) (輸入中看到非 ASCII 位元組的範圍 U + 0000. u + 007F) ，則會在傳回的實例中插入 '？ ' `string` 。 [`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A)`U+FFFD REPLACEMENT CHARACTER ('�')`在傳回的實例中，取代格式不正確的 utf-8 序列 `string` 。 如需詳細資訊，請參閱 [Unicode 標準](https://www.unicode.org/versions/latest/)，章節5.22 和3.9。

您 `Encoding` 也可以將內建類別設定為擲回例外狀況，而不是 char 在發現不正確的序列時執行 acter 替代。 這種方法通常用於 char 可能無法接受 acter 替代的安全性敏感應用程式。

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

如需如何使用內建類別的詳細資訊 `Encoding` ，請參閱 [如何 char 在 .net 中使用 acter 編碼類別](character-encoding.md)。

## <a name="see-also"></a>請參閱

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [全球化和當地語系化](../globalization-localization/index.md)
