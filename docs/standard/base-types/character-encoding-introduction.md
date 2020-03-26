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
ms.openlocfilehash: 34b1577f8bcea80c1f41b6f9605bf47d132fdb4f
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134419"
---
# <a name="character-encoding-in-net"></a>.NET 中的字元編碼

本文介紹了 .NET 使用的字元編碼系統。 本文介紹了<xref:System.String>、<xref:System.Char><xref:System.Text.Rune>和<xref:System.Globalization.StringInfo>類型如何與 Unicode、UTF-16 和 UTF-8 一起工作。

術語*字元*在這裡使用，在*讀者認為單個顯示元素*的一般意義上。 常見示例是字母"a"、符號"*"和表情符號""。🐂 有時，一個字元實際上由多個獨立的顯示元素組成，如[石墨星系團](#grapheme-clusters)上的部分所解釋的那樣。

## <a name="the-string-and-char-types"></a>字串和字元類型

[字串](xref:System.String)類的實例表示某些文本。 邏輯`string`上，A 是 16 位值的序列，每個值都是[字元](xref:System.Char)結構的實例。 [字串。Length](xref:System.String.Length)屬性返回`string`實例中的`char`實例數。

以下示例函數列印出`char``string`十六進位標記法中的值：

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::

將字串"Hello"傳遞給此函數，您將獲得以下輸出：

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

每個字元由單個`char`值表示。 這種模式在世界上大多數語言中都適用。 例如，下面是兩個漢字的輸出，聽起來像*n= ho*和"表示*你好*"

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

但是，對於某些語言和某些符號和表情符號，需要兩`char`個實例來表示一個字元。 例如，比較單詞中的字元和`char`實例，在奧薩奇語中表示*Osage：*

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

在前面的示例中，空格以外的每個字元都由兩個`char`實例表示。

單個 Unicode 表情符號也由兩`char`個 s 表示，如下例所示，顯示牛表情符號：

```
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

這些示例顯示 ， 指示`string.Length`實例數`char`的值不一定指示顯示的字元數。 單個`char`實例本身不一定表示字元。

映射到`char`單個字元的對稱為*代理項對*。 要瞭解它們的工作原理，您需要瞭解 Unicode 和 UTF-16 編碼。

## <a name="unicode-code-points"></a>Unicode 字碼指標

Unicode 是一種國際編碼標準，用於各種平臺以及各種語言和腳本。

Unicode 標準定義了超過 110 萬[個代碼點](https://www.unicode.org/glossary/#code_point)。 代碼點是一個整數值，範圍從 0 到`U+10FFFF`（十進位 1，114，111）。 某些代碼點分配給字母、符號或表情符號。 其他操作被分配給控制文本或字元的顯示方式的操作，例如前進到新行。 許多代碼點尚未分配。

下面是代碼點分配的一些示例，其中連結指向 Unicode 圖表，其中顯示代碼圖表：

|Decimal|Hex       |範例|描述|
|------:|----------|-------|-----------|
|10     | `U+000A` |N/A| [換行](https://www.unicode.org/charts/PDF/U0000.pdf) |
|65     | `U+0061` | a | [拉丁小字母 A](https://www.unicode.org/charts/PDF/U0000.pdf) |
|562    | `U+0232` | · | [拉丁資本字母 Y 與 MACRON](https://www.unicode.org/charts/PDF/U0180.pdf) |
|68,675 | `U+10C43`| 𐱃 | [舊突厥字母ORKHON在](https://www.unicode.org/charts/PDF/U10C00.pdf) |
|127,801| `U+1F339`| 🌹 | [ROSE 表情符號](https://www.unicode.org/charts/PDF/U1F300.pdf) |

代碼點通常使用語法`U+xxxx`引用 ，其中`xxxx`六進制編碼的整數值。

在代碼點的完整範圍內有兩個子範圍：

* 範圍內**的基本多語言平面 （BMP）。** `U+0000..U+FFFF` 此 16 位範圍提供 65，536 個代碼點，足以覆蓋世界上大多數書寫系統。
* `U+10000..U+10FFFF`**範圍內的補充代碼點**。 此 21 位範圍提供了超過一百萬個額外的代碼點，可用於不太知名的語言和其他目的，如表情符號。

下圖說明瞭 BMP 和補充代碼點之間的關係。

:::image type="content" source="media/character-encoding-introduction/bmp-and-supplementary.svg" alt-text="BMP 和補充代碼點":::

## <a name="utf-16-code-units"></a>UTF-16 代碼單元

16 位 Unicode 轉換格式 （[UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)） 是一個字元編碼系統，使用 16 位*代碼單元*來表示 Unicode 代碼點。 .NET 使用 UTF-16 對 文本`string`進行編碼。 實例`char`表示 16 位代碼單元。

單個 16 位代碼單元可以表示基本多語言平面 16 位範圍內的任何代碼點。 但對於補充範圍內的代碼點，需要兩`char`個實例。

## <a name="surrogate-pairs"></a>代理對

兩個 16 位值到單個 21 位值的轉換由一個稱為*代理代碼點*的特殊範圍（包括小`U+D800`數`U+DFFF`55，296 到 57，343）促進。

下圖說明瞭 BMP 和代理代碼點之間的關係。

:::image type="content" source="media/character-encoding-introduction/bmp-and-surrogate.svg" alt-text="BMP 和代理代碼點":::

當*高代理項*代碼點`U+D800..U+DBFF`（ ） 緊跟*低代理項*代碼點`U+DC00..U+DFFF`（ ）， 使用以下公式將配對解釋為輔助代碼點：

```
code point = 0x10000 +
  ((high surrogate code point - 0xD800) * 0x0400) +
  (low surrogate code point - 0xDC00)
```

下面是使用十進位標記法的相同公式：

```
code point = 65,536 +
  ((high surrogate code point - 55,296) * 1,024) +
  (low surrogate code point - 56,320)
```

*高*代理項代碼點的數位值不高於*低*代理項代碼點。 高代理項代碼點稱為"高"，因為它用於計算完整 21 位代碼點範圍的高階 11 位。 低代理項代碼點用於計算低階 10 位。

例如，對應于代理項對`0xD83C`並`0xDF39`計算的實際代碼點如下所示：

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

下面是使用十進位標記法的相同計算：

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

前面的示例演示了`"\ud83c\udf39"`前面提到的`U+1F339 ROSE ('🌹')`代碼點的 UTF-16 編碼。

## <a name="unicode-scalar-values"></a>Unicode 標量值

術語[Unicode 標量值](https://www.unicode.org/glossary/#unicode_scalar_value)引用代理代碼點以外的所有代碼點。 換句話說，標量值是分配給字元或將來可以分配字元的任何代碼點。 此處的"字元"是指可以分配給代碼點的任何內容，其中包括控制文本或字元顯示方式的操作等操作。

下圖說明瞭標量值代碼點。

:::image type="content" source="media/character-encoding-introduction/scalar-values.svg" alt-text="純量值":::

### <a name="the-opno-locrune-type-as-a-scalar-value"></a>Rune類型為標量值

從 .NET Core 3.0<xref:System.Text.Rune?displayProperty=fullName>開始，該類型表示 Unicode 標量值。 **`Rune`不在 .NET 核心 2.x 或 .NET 框架 4.x 中可用。**

構造`Rune`函數驗證生成的實例是否是有效的 Unicode 標量值，否則它們會引發異常。 下面的示例顯示成功具現化`Rune`的代碼，因為輸入表示有效的標量值：

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetValid":::

下面的示例引發異常，因為代碼點位於代理項範圍內，並且不是代理項對的一部分：

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidSurrogate":::

以下示例引發異常，因為代碼點超出補充範圍：

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidHigh":::

### <a name="opno-locrune-usage-example-changing-letter-case"></a>Rune使用示例：更改字母大小寫

如果`char`從 代理`char`項對中獲取 並假定它正在使用標量值的代碼點的 API 不能正常工作。 例如，請考慮以下方法，該方法調用<xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType>中的每個char方法： string

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::

`input` string如果 包含小寫 Deseret 字母`er``𐑉`（），則此代碼不會將其轉換為大寫 （）。`𐐡` 代碼在每個代理`char.ToUpperInvariant`代碼點上分別調用 ，`U+D801`和`U+DC49`. 但是`U+D801`，沒有足夠的資訊本身來識別它作為小寫字母，所以`char.ToUpperInvariant`別管它。 它處理`U+DC49`的方式相同。 結果是，中的`input`string小寫""不會轉換為大寫""。"。

以下是正確轉換為大寫字母的string兩個選項：

* 調用<xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType>輸入string，而不是`char`逐反覆運算 。`char` 該方法`string.ToUpperInvariant`有權訪問每個代理項對的兩個部分，因此它可以正確處理所有 Unicode 代碼點。
* 反覆運算 Unicode 標量值作為`Rune`實例而不是`char`實例，如以下示例所示。 由於`Rune`實例是有效的 Unicode 標量值，因此可以將它傳遞給預期對標量值操作的 API。 例如，如下例<xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType>所示的調用可提供正確的結果：

  :::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::

### <a name="other-opno-locrune-apis"></a>其他RuneAPI

該`Rune`類型公開了許多 API 的`char`類比。 例如，以下方法在`char`類型上鏡像靜態 API：

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

要從`Rune`實例獲取原始標量值，請使用 屬性<xref:System.Text.Rune.Value%2A?displayProperty=nameWithType>。

要將`Rune`實例轉換回 s 序列`char`，請使用<xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType>或<xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType>方法。

由於任何 Unicode 標量值都可以由單個`char`或代理項對表示，因此最多`Rune`只能由 2`char`個實例表示任何實例。 用於<xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType>查看表示`Rune`實例所需的`char`實例數。

有關 .NET`Rune`類型的詳細資訊，請參閱[`Rune`API 引用](xref:System.Text.Rune)。

## <a name="grapheme-clusters"></a>石墨聚類

看起來像一個字元的原因可能是由多個代碼點的組合產生的，因此通常用來代替"字元"的更具描述性的術語是[石墨聚類](https://www.unicode.org/glossary/#grapheme_cluster)。 .NET 中的等效術語是[文本元素](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A)。

考慮`string`實例"a"，"\""。 ""和""。`👩🏽‍🚒` 如果作業系統按 Unicode 標準指定處理它們，則每個`string`實例都顯示為單個文本元素或圖形學群集。 但後兩個由多個標量值代碼點表示。

* "a"string由一個標量值表示，並包含一個`char`實例。

  * `U+0061 LATIN SMALL LETTER A`

* "="string由一個標量值表示，並包含一個`char`實例。

  * `U+00E1 LATIN SMALL LETTER E WITH ACUTE`

* "="string看起來與"="相同，但由兩個標量值表示，並包含兩`char`個實例。

  * `U+0065 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* 最後，""string`👩🏽‍🚒`由四個標量值表示，並包含七`char`個實例。

  * `U+1F469 WOMAN`（補充範圍，需要代理對）
  * `U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4`（補充範圍，需要代理對）
  * `U+200D ZERO WIDTH JOINER`
  * `U+1F692 FIRE ENGINE`（補充範圍，需要代理對）

在前面的一些示例中（如組合重音修改器或膚色修飾符）中，代碼點不會在螢幕上顯示為獨立元素。 相反，它用於修改它之前的文本元素的外觀。 這些示例表明，可能需要多個標量值來構成我們認為為單個"字元"或"圖形群集"。"

要枚舉 的`string`圖目組，請使用類，<xref:System.Globalization.StringInfo>如以下示例所示。 如果您熟悉 Swift，則 .NET`StringInfo`類型在概念上與[Swift`character`的類型](https://developer.apple.com/documentation/swift/character)類似。

### <a name="example-count-opno-locchar-opno-locrune-and-text-element-instances"></a>示例：計數charRune和 文本元素實例

在 .NET API 中，圖形學群集稱為*文本元素*。 以下方法演示 了 中`char``Rune`的文本元素實例之間的差異`string`：

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::

如果在 .NET 框架或 .NET Core 3.1 或更早版本中運行此代碼，則表情符號`4`的文本元素計數將顯示 。 這是因為在 .NET 5`StringInfo`中修復的類中存在 Bug。

### <a name="example-splitting-opno-locstring-instances"></a>示例：拆分string實例

拆分`string`實例時，請避免拆分代理項對和石墨組。 請考慮以下錯誤代碼示例，該示例打算在 中每 10 個字元插入換string行符：

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::

由於此代碼枚`char`舉實例，因此將拆分恰巧跨越 10 邊界的`char`代理項對，並在它們之間注入一條新線。 此插入會引入資料損壞，因為代理代碼點僅作為對有意義。

如果枚舉`Rune`實例（標點值）而不是`char`實例，則不會消除資料損壞的可能性。 一組`Rune`實例可能構成跨越 10 邊界的`char`石墨星系團。 如果圖形圖姆群集集被拆分，則無法正確解釋它。

更好的方法是string通過計算石墨烯聚類或文本元素來打破，如以下示例所示：

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::

但是，如前所述，在 .NET 的實現中，除了 .NET `StringInfo` 5 之外，類可能會錯誤地處理某些圖目群。

## <a name="utf-8-and-utf-32"></a>UTF-8 和 UTF-32

前面各節重點介紹 UTF-16，因為這是 .NET 用於對實例`string`進行編碼的內容。 Unicode - [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8)和[UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32)還有其他編碼系統。 這些編碼分別使用 8 位代碼單元和 32 位代碼單元。

與 UTF-16 一樣，UTF-8 需要多個代碼單元來表示某些 Unicode 標量值。 UTF-32 可以表示單個 32 位代碼單元中的任何標量值。

下面是一些示例，顯示了如何在以下三個 Unicode 編碼系統中表示同一 Unicode 代碼點：

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

如前所述，[代理對](#surrogate-pairs)中單個 UTF-16 代碼單元本身就毫無意義。 同樣，如果單個 UTF-8 代碼單元的序列為 2、3 或 4，則它本身就毫無意義。

### <a name="endianness"></a>位元組序

在 .NET 中，astring的 UTF-16 代碼單元作為 16 位整數（`char`實例）的順序存儲在連續記憶體中。 各個代碼單元的位根據當前體系結構的[內端性](https://en.wikipedia.org/wiki/Endianness)進行佈局。

在一個小端架構上，string由UTF-16代碼點組成的代碼點`[ D801 DCCC ]`將作為位元組`[ 0x01, 0xD8, 0xCC, 0xDC ]`在記憶體中佈局。 在大型的體系結構上，在string記憶體中也會像位元組`[ 0xD8, 0x01, 0xDC, 0xCC ]`一樣佈局。

相互通信的電腦系統必須就跨線資料的表示方式達成一致。 大多數網路通訊協定在傳輸文本時使用 UTF-8 作為標準，部分是為了避免與小終端機器通信時可能出現的問題。 UTF-8 代碼點string`[ F0 90 93 8C ]`組成將始終表示為位元組`[ 0xF0, 0x90, 0x93, 0x8C ]`，而不考慮端點性。

要使用 UTF-8 傳輸文本，.NET 應用程式通常使用如下示例這樣的代碼：

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

在前面的示例中，方法[Code.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A)將 UTF-16`string`解碼回一系列 Unicode 標量值，然後將這些標量值重新編碼到 UTF-8 中，並將生成的序列放入`byte`陣列中。 方法[Encode.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A)執行相反的轉換，將 UTF-8`byte`陣列轉換為 UTF-16 `string`。

> [!WARNING]
> 由於 UTF-8 在互聯網上很常見，因此從導線中讀取原始位元組並像將資料視為 UTF-8 時，可能會很誘人。 但是，您應該驗證它確實格式良好。 惡意用戶端可能會向服務提交格式錯誤的 UTF-8。 如果對該資料進行操作，就好像它格式良好一樣，則可能會導致應用程式中的錯誤或安全性漏洞。 要驗證 UTF-8 資料，可以使用 類似`Encoding.UTF8.GetString`的方法，該方法將在將傳入資料轉換為 時執行驗證`string`。

### <a name="well-formed-encoding"></a>格式良好的編碼

格式良好的 Unicode 編碼是一string種代碼單元，可以明確解碼，而不會出錯地解碼到 Unicode 標量值序列中。 格式良好的資料可以在 UTF-8、UTF-16 和 UTF-32 之間自由來回轉換。

編碼序列是否格式良好的問題與電腦體系結構的內向性無關。 在大型機器和小端型機器上，格式錯誤的 UTF-8 序列格式不正確。

下面是一些格式錯誤的編碼示例：

* 在 UTF-8 中`[ 6C C2 61 ]`，序列格式不正確，`C2`因為不能跟後`61`。

* 在 UTF-16 中`[ DC00 DD00 ]`，序列（或，在 C#string`"\udc00\udd00"`中， ） 格式不正確`DC00`，因為低代理項不能跟`DD00`後另一個低代理項 。

* 在 UTF-32 中`[ 0011ABCD ]`，序列格式不正確，`0011ABCD`因為超出 Unicode 標量值的範圍。

在 .NET`string`中，實例幾乎總是包含格式良好的 UTF-16 資料，但這不能保證。 以下示例顯示在實例中`string`創建格式錯誤的 UTF-16 資料的有效 C# 代碼。

* 格式不佳的字面：

  ```csharp
  const string s = "\ud800";
  ```

* 拆分代理項對的子字串：

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

API 就像[`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A)從不返回格式`string`錯誤的實例一樣。 `Encoding.GetString`和方法`Encoding.GetBytes`檢測輸入中的格式錯誤的序列，並在生成輸出時執行字元替換。 例如，如果在[`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A)輸入中看到非 ASCII 位元組（超出 U+0000..U+007F 範圍），它將在返回`string`的實例中插入"？ [`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A)在返回`U+FFFD REPLACEMENT CHARACTER ('�')``string`的實例中用格式錯誤的 UTF-8 序列替換格式不正確的 UTF-8 序列。 有關詳細資訊，請參閱[Unicode 標準](https://www.unicode.org/versions/latest/)，第 5.22 節和第 3.9 節。

也可以將內置`Encoding`類配置為引發異常，而不是在看到格式錯誤的序列時執行字元替換。 此方法通常用於對安全敏感的應用程式，其中字元替換可能不可接受。

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

有關如何使用內置`Encoding`類的資訊，請參閱[如何在 .NET 中使用字元編碼類](character-encoding.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [全球化與當地語系化](../../../docs/standard/globalization-localization/index.md)
