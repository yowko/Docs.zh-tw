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
# <a name="character-encoding-in-net"></a><span data-ttu-id="b6b18-103">.NET 中的字元編碼</span><span class="sxs-lookup"><span data-stu-id="b6b18-103">Character encoding in .NET</span></span>

<span data-ttu-id="b6b18-104">本文提供 .NET 所使用的字元編碼系統簡介。</span><span class="sxs-lookup"><span data-stu-id="b6b18-104">This article provides an introduction to character encoding systems that are used by .NET.</span></span> <span data-ttu-id="b6b18-105">本文說明 <xref:System.String> 、 <xref:System.Char> 、 <xref:System.Text.Rune> 和 <xref:System.Globalization.StringInfo> 類型如何與 Unicode、utf-16 和 utf-8 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="b6b18-105">The article explains how the <xref:System.String>, <xref:System.Char>, <xref:System.Text.Rune>, and <xref:System.Globalization.StringInfo> types work with Unicode, UTF-16, and UTF-8.</span></span>

<span data-ttu-id="b6b18-106">在這裡 *，「詞彙」* 一詞是用來*做為單一顯示元素*的一般意義。</span><span class="sxs-lookup"><span data-stu-id="b6b18-106">The term *character* is used here in the general sense of *what a reader perceives as a single display element*.</span></span> <span data-ttu-id="b6b18-107">常見的範例包括字母 "a"、符號 "@" 和表情 " 🐂 "。</span><span class="sxs-lookup"><span data-stu-id="b6b18-107">Common examples are the letter "a", the symbol "@", and the emoji "🐂".</span></span> <span data-ttu-id="b6b18-108">有時看起來像一個字元實際上是由多個獨立的顯示專案組成，如[語素簇](#grapheme-clusters)叢集上的一節所說明。</span><span class="sxs-lookup"><span data-stu-id="b6b18-108">Sometimes what looks like one character is actually composed of multiple independent display elements, as the section on [grapheme clusters](#grapheme-clusters) explains.</span></span>

## <a name="the-string-and-char-types"></a><span data-ttu-id="b6b18-109">string和 char 類型</span><span class="sxs-lookup"><span data-stu-id="b6b18-109">The string and char types</span></span>

<span data-ttu-id="b6b18-110">類別的實例 [string](xref:System.String) 代表一些文字。</span><span class="sxs-lookup"><span data-stu-id="b6b18-110">An instance of the [string](xref:System.String) class represents some text.</span></span> <span data-ttu-id="b6b18-111">`string`邏輯上是16位值的序列，其中每一個都是結構的實例 [char](xref:System.Char) 。</span><span class="sxs-lookup"><span data-stu-id="b6b18-111">A `string` is logically a sequence of 16-bit values, each of which is an instance of the [char](xref:System.Char) struct.</span></span> <span data-ttu-id="b6b18-112">[ string 。Length](xref:System.String.Length)屬性會傳回 `char` 實例中的實例數目 `string` 。</span><span class="sxs-lookup"><span data-stu-id="b6b18-112">The [string.Length](xref:System.String.Length) property returns the number of `char` instances in the `string` instance.</span></span>

<span data-ttu-id="b6b18-113">下列範例函式會以十六進位標記法印出中所有實例的值 `char` `string` ：</span><span class="sxs-lookup"><span data-stu-id="b6b18-113">The following sample function prints out the values in hexadecimal notation of all the `char` instances in a `string`:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::

<span data-ttu-id="b6b18-114">將 string "Hello" 傳遞至此函式，您會得到下列輸出：</span><span class="sxs-lookup"><span data-stu-id="b6b18-114">Pass the string "Hello" to this function, and you get the following output:</span></span>

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

<span data-ttu-id="b6b18-115">每個字元都是以單一 `char` 值表示。</span><span class="sxs-lookup"><span data-stu-id="b6b18-115">Each character is represented by a single `char` value.</span></span> <span data-ttu-id="b6b18-116">該模式適用于大部分世界的語言。</span><span class="sxs-lookup"><span data-stu-id="b6b18-116">That pattern holds true for most of the world's languages.</span></span> <span data-ttu-id="b6b18-117">例如，以下是兩個中文字元的輸出，聽起來像是*nǐ hǎo* ，而 Mean 為*Hello*：</span><span class="sxs-lookup"><span data-stu-id="b6b18-117">For example, here's the output for two Chinese characters that sound like *nǐ hǎo* and mean *Hello*:</span></span>

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

<span data-ttu-id="b6b18-118">不過，對於某些語言以及某些符號和表情，它會採用兩個 `char` 實例來表示單一字元。</span><span class="sxs-lookup"><span data-stu-id="b6b18-118">However, for some languages and for some symbols and emoji, it takes two `char` instances to represent a single character.</span></span> <span data-ttu-id="b6b18-119">例如，比較單字中的字元和 `char` 實例，這是指 Osage 語言中的*Osage* ：</span><span class="sxs-lookup"><span data-stu-id="b6b18-119">For example, compare the characters and `char` instances in the word that means *Osage* in the Osage language:</span></span>

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

<span data-ttu-id="b6b18-120">在上述範例中，空格以外的每個字元都是由兩個 `char` 實例表示。</span><span class="sxs-lookup"><span data-stu-id="b6b18-120">In the preceding example, each character except the space is represented by two `char` instances.</span></span>

<span data-ttu-id="b6b18-121">單一 Unicode 表情也會以兩個表示 `char` ，如下列範例所示，其中顯示 ox 的表情：</span><span class="sxs-lookup"><span data-stu-id="b6b18-121">A single Unicode emoji is also represented by two `char`s, as seen in the following example showing an ox emoji:</span></span>

```
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

<span data-ttu-id="b6b18-122">這些範例顯示 `string.Length` 表示實例數目的值， `char` 不一定表示顯示的字元數。</span><span class="sxs-lookup"><span data-stu-id="b6b18-122">These examples show that the value of `string.Length`, which indicates the number of `char` instances, doesn't necessarily indicate the number of displayed characters.</span></span> <span data-ttu-id="b6b18-123">單一 `char` 實例本身不一定代表一個字元。</span><span class="sxs-lookup"><span data-stu-id="b6b18-123">A single `char` instance by itself doesn't necessarily represent a character.</span></span>

<span data-ttu-id="b6b18-124">`char`對應至單一字元的配對稱為*代理配對*。</span><span class="sxs-lookup"><span data-stu-id="b6b18-124">The `char` pairs that map to a single character are called *surrogate pairs*.</span></span> <span data-ttu-id="b6b18-125">若要瞭解它們的使用方式，您必須瞭解 Unicode 和 UTF-16 編碼。</span><span class="sxs-lookup"><span data-stu-id="b6b18-125">To understand how they work, you need to understand Unicode and UTF-16 encoding.</span></span>

## <a name="unicode-code-points"></a><span data-ttu-id="b6b18-126">Unicode 字碼指標</span><span class="sxs-lookup"><span data-stu-id="b6b18-126">Unicode code points</span></span>

<span data-ttu-id="b6b18-127">Unicode 是在各種平臺上使用的國際編碼標準，以及各種語言和腳本。</span><span class="sxs-lookup"><span data-stu-id="b6b18-127">Unicode is an international encoding standard for use on various platforms and with various languages and scripts.</span></span>

<span data-ttu-id="b6b18-128">Unicode 標準定義了超過1100000個程式[代碼點](https://www.unicode.org/glossary/#code_point)。</span><span class="sxs-lookup"><span data-stu-id="b6b18-128">The Unicode Standard defines over 1.1 million [code points](https://www.unicode.org/glossary/#code_point).</span></span> <span data-ttu-id="b6b18-129">程式碼點是一個整數值，其範圍可以從0到 `U+10FFFF` （十進位1114111）。</span><span class="sxs-lookup"><span data-stu-id="b6b18-129">A code point is an integer value that can range from 0 to `U+10FFFF` (decimal 1,114,111).</span></span> <span data-ttu-id="b6b18-130">有些程式碼點會指派給字母、符號或表情。</span><span class="sxs-lookup"><span data-stu-id="b6b18-130">Some code points are assigned to letters, symbols, or emoji.</span></span> <span data-ttu-id="b6b18-131">其他會指派給控制文字或字元顯示方式的動作，例如前進到新行。</span><span class="sxs-lookup"><span data-stu-id="b6b18-131">Others are assigned to actions that control how text or characters are displayed, such as advance to a new line.</span></span> <span data-ttu-id="b6b18-132">尚未指派許多程式碼點。</span><span class="sxs-lookup"><span data-stu-id="b6b18-132">Many code points are not yet assigned.</span></span>

<span data-ttu-id="b6b18-133">以下是一些程式碼點指派範例，其中顯示的是 Unicode 圖表的連結：</span><span class="sxs-lookup"><span data-stu-id="b6b18-133">Here are some examples of code point assignments, with links to Unicode charts in which they appear:</span></span>

|<span data-ttu-id="b6b18-134">Decimal</span><span class="sxs-lookup"><span data-stu-id="b6b18-134">Decimal</span></span>|<span data-ttu-id="b6b18-135">Hex</span><span class="sxs-lookup"><span data-stu-id="b6b18-135">Hex</span></span>       |<span data-ttu-id="b6b18-136">範例</span><span class="sxs-lookup"><span data-stu-id="b6b18-136">Example</span></span>|<span data-ttu-id="b6b18-137">描述</span><span class="sxs-lookup"><span data-stu-id="b6b18-137">Description</span></span>|
|------:|----------|-------|-----------|
|<span data-ttu-id="b6b18-138">10</span><span class="sxs-lookup"><span data-stu-id="b6b18-138">10</span></span>     | `U+000A` |<span data-ttu-id="b6b18-139">N/A</span><span class="sxs-lookup"><span data-stu-id="b6b18-139">N/A</span></span>| [<span data-ttu-id="b6b18-140">換行字元</span><span class="sxs-lookup"><span data-stu-id="b6b18-140">LINE FEED</span></span>](https://www.unicode.org/charts/PDF/U0000.pdf) |
|<span data-ttu-id="b6b18-141">65</span><span class="sxs-lookup"><span data-stu-id="b6b18-141">65</span></span>     | `U+0061` | <span data-ttu-id="b6b18-142">a</span><span class="sxs-lookup"><span data-stu-id="b6b18-142">a</span></span> | [<span data-ttu-id="b6b18-143">拉丁小寫字母 A</span><span class="sxs-lookup"><span data-stu-id="b6b18-143">LATIN SMALL LETTER A</span></span>](https://www.unicode.org/charts/PDF/U0000.pdf) |
|<span data-ttu-id="b6b18-144">562</span><span class="sxs-lookup"><span data-stu-id="b6b18-144">562</span></span>    | `U+0232` | <span data-ttu-id="b6b18-145">Ȳ</span><span class="sxs-lookup"><span data-stu-id="b6b18-145">Ȳ</span></span> | [<span data-ttu-id="b6b18-146">拉丁文大寫字母 Y 加上長音符</span><span class="sxs-lookup"><span data-stu-id="b6b18-146">LATIN CAPITAL LETTER Y WITH MACRON</span></span>](https://www.unicode.org/charts/PDF/U0180.pdf) |
|<span data-ttu-id="b6b18-147">68675</span><span class="sxs-lookup"><span data-stu-id="b6b18-147">68,675</span></span> | `U+10C43`| <span data-ttu-id="b6b18-148">𐱃</span><span class="sxs-lookup"><span data-stu-id="b6b18-148">𐱃</span></span> | [<span data-ttu-id="b6b18-149">舊的土耳其文字母</span><span class="sxs-lookup"><span data-stu-id="b6b18-149">OLD TURKIC LETTER ORKHON AT</span></span>](https://www.unicode.org/charts/PDF/U10C00.pdf) |
|<span data-ttu-id="b6b18-150">127801</span><span class="sxs-lookup"><span data-stu-id="b6b18-150">127,801</span></span>| `U+1F339`| <span data-ttu-id="b6b18-151">🌹</span><span class="sxs-lookup"><span data-stu-id="b6b18-151">🌹</span></span> | [<span data-ttu-id="b6b18-152">玫瑰表情</span><span class="sxs-lookup"><span data-stu-id="b6b18-152">ROSE emoji</span></span>](https://www.unicode.org/charts/PDF/U1F300.pdf) |

<span data-ttu-id="b6b18-153">程式碼點通常是使用語法來參考 `U+xxxx` ，其中 `xxxx` 是十六進位編碼的整數值。</span><span class="sxs-lookup"><span data-stu-id="b6b18-153">Code points are customarily referred to by using the syntax `U+xxxx`, where `xxxx` is the hex-encoded integer value.</span></span>

<span data-ttu-id="b6b18-154">在完整範圍的程式碼點中有兩個子範圍：</span><span class="sxs-lookup"><span data-stu-id="b6b18-154">Within the full range of code points there are two subranges:</span></span>

* <span data-ttu-id="b6b18-155">範圍內的**基本多語系平面（BMP）** `U+0000..U+FFFF` 。</span><span class="sxs-lookup"><span data-stu-id="b6b18-155">The **Basic Multilingual Plane (BMP)** in the range `U+0000..U+FFFF`.</span></span> <span data-ttu-id="b6b18-156">這個16位範圍提供65536的程式碼點，足以涵蓋世界上大部分的書寫系統。</span><span class="sxs-lookup"><span data-stu-id="b6b18-156">This 16-bit range provides 65,536 code points, enough to cover the majority of the world's writing systems.</span></span>
* <span data-ttu-id="b6b18-157">範圍中的**補充程式碼點** `U+10000..U+10FFFF` 。</span><span class="sxs-lookup"><span data-stu-id="b6b18-157">**Supplementary code points** in the range `U+10000..U+10FFFF`.</span></span> <span data-ttu-id="b6b18-158">這個21位範圍提供超過一百萬個額外的程式碼點，可用於較不知名的語言和其他用途，例如 emoji。</span><span class="sxs-lookup"><span data-stu-id="b6b18-158">This 21-bit range provides more than a million additional code points that can be used for less well-known languages and other purposes such as emojis.</span></span>

<span data-ttu-id="b6b18-159">下圖說明 BMP 和補充程式碼點之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="b6b18-159">The following diagram illustrates the relationship between the BMP and the supplementary code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/bmp-and-supplementary.svg" alt-text="BMP 和補充程式碼點":::

## <a name="utf-16-code-units"></a><span data-ttu-id="b6b18-161">UTF-16 程式碼單位</span><span class="sxs-lookup"><span data-stu-id="b6b18-161">UTF-16 code units</span></span>

<span data-ttu-id="b6b18-162">16位 Unicode 轉換格式（[utf-16](https://www.unicode.org/faq/utf_bom.html#UTF16)）是使用16位程式*代碼單位*來代表 Unicode 程式碼點的字元編碼系統。</span><span class="sxs-lookup"><span data-stu-id="b6b18-162">16-bit Unicode Transformation Format ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) is a character encoding system that uses 16-bit *code units* to represent Unicode code points.</span></span> <span data-ttu-id="b6b18-163">.NET 會使用 UTF-16 來編碼中的文字 `string` 。</span><span class="sxs-lookup"><span data-stu-id="b6b18-163">.NET uses UTF-16 to encode the text in a `string`.</span></span> <span data-ttu-id="b6b18-164">`char`實例代表16位的程式碼單位。</span><span class="sxs-lookup"><span data-stu-id="b6b18-164">A `char` instance represents a 16-bit code unit.</span></span>

<span data-ttu-id="b6b18-165">單一16位程式碼單位可以代表基本多語系平面之16位範圍內的任何程式碼點。</span><span class="sxs-lookup"><span data-stu-id="b6b18-165">A single 16-bit code unit can represent any code point in the 16-bit range of the Basic Multilingual Plane.</span></span> <span data-ttu-id="b6b18-166">但對於補充範圍中的程式碼點， `char` 則需要兩個實例。</span><span class="sxs-lookup"><span data-stu-id="b6b18-166">But for a code point in the supplementary range, two `char` instances are needed.</span></span>

## <a name="surrogate-pairs"></a><span data-ttu-id="b6b18-167">代理配對</span><span class="sxs-lookup"><span data-stu-id="b6b18-167">Surrogate pairs</span></span>

<span data-ttu-id="b6b18-168">將 2 16 位值轉譯為單一21位值，是由稱為*代理程式碼點*的特殊範圍 `U+D800` （從到 `U+DFFF` （十進位55296到57343）（含）所組成。</span><span class="sxs-lookup"><span data-stu-id="b6b18-168">The translation of two 16-bit values to a single 21-bit value is facilitated by a special range called the *surrogate code points*, from `U+D800` to `U+DFFF` (decimal 55,296 to 57,343), inclusive.</span></span>

<span data-ttu-id="b6b18-169">下圖說明 BMP 和代理程式碼點之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="b6b18-169">The following diagram illustrates the relationship between the BMP and the surrogate code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/bmp-and-surrogate.svg" alt-text="BMP 和代理程式碼點":::

<span data-ttu-id="b6b18-171">當*高代理*程式碼點（ `U+D800..U+DBFF` ）緊接在*低代理*程式碼點（）後面時 `U+DC00..U+DFFF` ，會使用下列公式，將配對解讀為補充程式碼點：</span><span class="sxs-lookup"><span data-stu-id="b6b18-171">When a *high surrogate* code point (`U+D800..U+DBFF`) is immediately followed by a *low surrogate* code point (`U+DC00..U+DFFF`), the pair is interpreted as a supplementary code point by using the following formula:</span></span>

```
code point = 0x10000 +
  ((high surrogate code point - 0xD800) * 0x0400) +
  (low surrogate code point - 0xDC00)
```

<span data-ttu-id="b6b18-172">以下是使用小數點標記法的相同公式：</span><span class="sxs-lookup"><span data-stu-id="b6b18-172">Here's the same formula using decimal notation:</span></span>

```
code point = 65,536 +
  ((high surrogate code point - 55,296) * 1,024) +
  (low surrogate code point - 56,320)
```

<span data-ttu-id="b6b18-173">*高*代理程式碼點的數位值不會高於*低*代理程式碼點。</span><span class="sxs-lookup"><span data-stu-id="b6b18-173">A *high* surrogate code point doesn't have a higher number value than a *low* surrogate code point.</span></span> <span data-ttu-id="b6b18-174">高代理程式碼點稱為「高」，因為它是用來計算完整21位程式碼點範圍的高序位11位。</span><span class="sxs-lookup"><span data-stu-id="b6b18-174">The high surrogate code point is called "high" because it's used to calculate the higher-order 11 bits of the full 21-bit code point range.</span></span> <span data-ttu-id="b6b18-175">低代理程式碼點用來計算較低順序的10位。</span><span class="sxs-lookup"><span data-stu-id="b6b18-175">The low surrogate code point is used to calculate the lower-order 10 bits.</span></span>

<span data-ttu-id="b6b18-176">例如，對應至代理配對的實際程式碼點，其 `0xD83C` `0xDF39` 計算方式如下：</span><span class="sxs-lookup"><span data-stu-id="b6b18-176">For example, the actual code point that corresponds to the surrogate pair `0xD83C` and `0xDF39`  is computed as follows:</span></span>

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

<span data-ttu-id="b6b18-177">以下是使用小數點標記法的相同計算：</span><span class="sxs-lookup"><span data-stu-id="b6b18-177">Here's the same calculation using decimal notation:</span></span>

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

<span data-ttu-id="b6b18-178">先前的範例示範， `"\ud83c\udf39"` 是先前所述之程式碼點的 utf-16 編碼方式 `U+1F339 ROSE ('🌹')` 。</span><span class="sxs-lookup"><span data-stu-id="b6b18-178">The preceding example demonstrates that `"\ud83c\udf39"` is the UTF-16 encoding of the `U+1F339 ROSE ('🌹')` code point mentioned earlier.</span></span>

## <a name="unicode-scalar-values"></a><span data-ttu-id="b6b18-179">Unicode 純量值</span><span class="sxs-lookup"><span data-stu-id="b6b18-179">Unicode scalar values</span></span>

<span data-ttu-id="b6b18-180">「Unicode 純量[值](https://www.unicode.org/glossary/#unicode_scalar_value)」一詞指的是代理程式碼點以外的所有程式碼點。</span><span class="sxs-lookup"><span data-stu-id="b6b18-180">The term [Unicode scalar value](https://www.unicode.org/glossary/#unicode_scalar_value) refers to all code points other than the surrogate code points.</span></span> <span data-ttu-id="b6b18-181">換句話說，純量值就是指派了一個字元的任何程式碼點，或未來可以指派一個字元。</span><span class="sxs-lookup"><span data-stu-id="b6b18-181">In other words, a scalar value is any code point that is assigned a character or can be assigned a character in the future.</span></span> <span data-ttu-id="b6b18-182">此處的「字元」指的是可指派給程式碼點的任何專案，包括控制文字或字元顯示方式的動作。</span><span class="sxs-lookup"><span data-stu-id="b6b18-182">"Character" here refers to anything that can be assigned to a code point, which includes such things as actions that control how text or characters are displayed.</span></span>

<span data-ttu-id="b6b18-183">下圖說明純量值的程式碼點。</span><span class="sxs-lookup"><span data-stu-id="b6b18-183">The following diagram illustrates the scalar value code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/scalar-values.svg" alt-text="純量值":::

### <a name="the-rune-type-as-a-scalar-value"></a><span data-ttu-id="b6b18-185">Rune類型，做為純量值</span><span class="sxs-lookup"><span data-stu-id="b6b18-185">The Rune type as a scalar value</span></span>

<span data-ttu-id="b6b18-186">從 .NET Core 3.0 開始， <xref:System.Text.Rune?displayProperty=fullName> 類型代表 Unicode 純量值。</span><span class="sxs-lookup"><span data-stu-id="b6b18-186">Beginning with .NET Core 3.0, the <xref:System.Text.Rune?displayProperty=fullName> type represents a Unicode scalar value.</span></span> <span data-ttu-id="b6b18-187">**`Rune`在 .NET Core 2.x 或 .NET Framework 4.x 中無法使用。**</span><span class="sxs-lookup"><span data-stu-id="b6b18-187">**`Rune` is not available in .NET Core 2.x or .NET Framework 4.x.**</span></span>

<span data-ttu-id="b6b18-188">這些函式 `Rune` 會驗證產生的實例是否為有效的 Unicode 純量值，否則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b6b18-188">The `Rune` constructors validate that the resulting instance is a valid Unicode scalar value, otherwise they throw an exception.</span></span> <span data-ttu-id="b6b18-189">下列範例會顯示成功具現化實例的程式碼， `Rune` 因為輸入代表有效的純量值：</span><span class="sxs-lookup"><span data-stu-id="b6b18-189">The following example shows code that successfully instantiates `Rune` instances because the input represents valid scalar values:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetValid":::

<span data-ttu-id="b6b18-190">下列範例會擲回例外狀況，因為程式碼點位於代理範圍內，而且不屬於代理配對：</span><span class="sxs-lookup"><span data-stu-id="b6b18-190">The following example throws an exception because the code point is in the surrogate range and isn't part of a surrogate pair:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidSurrogate":::

<span data-ttu-id="b6b18-191">下列範例會擲回例外狀況，因為程式碼點超出補充範圍：</span><span class="sxs-lookup"><span data-stu-id="b6b18-191">The following example throws an exception because the code point is beyond the supplementary range:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidHigh":::

### <a name="rune-usage-example-changing-letter-case"></a>Rune<span data-ttu-id="b6b18-192">使用範例：變更字母大小寫</span><span class="sxs-lookup"><span data-stu-id="b6b18-192"> usage example: changing letter case</span></span>

<span data-ttu-id="b6b18-193">如果是來自代理程式配對，則會採用 `char` 並假設其使用的程式碼點為純量值，因此無法正確運作 `char` 。</span><span class="sxs-lookup"><span data-stu-id="b6b18-193">An API that takes a `char` and assumes it is working with a code point that is a scalar value doesn't work correctly if the `char` is from a surrogate pair.</span></span> <span data-ttu-id="b6b18-194">例如，請考慮下列在 <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> 中的每個上呼叫的方法 char string ：</span><span class="sxs-lookup"><span data-stu-id="b6b18-194">For example, consider the following method that calls <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> on each char in a string:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::

<span data-ttu-id="b6b18-195">如果 `input` string 包含小寫的德字塞號 `er` （ `𐑉` ），則此程式碼不會將它轉換成大寫（ `𐐡` ）。</span><span class="sxs-lookup"><span data-stu-id="b6b18-195">If the `input` string contains the lowercase Deseret letter `er` (`𐑉`), this code won't convert it to uppercase (`𐐡`).</span></span> <span data-ttu-id="b6b18-196">程式碼會 `char.ToUpperInvariant` 分別在每個代理程式碼點和上呼叫 `U+D801` `U+DC49` 。</span><span class="sxs-lookup"><span data-stu-id="b6b18-196">The code calls `char.ToUpperInvariant` separately on each surrogate code point, `U+D801` and `U+DC49`.</span></span> <span data-ttu-id="b6b18-197">但是 `U+D801` ，本身並沒有足夠的資訊來將它識別為小寫字母，所以將 `char.ToUpperInvariant` 它單獨保留。</span><span class="sxs-lookup"><span data-stu-id="b6b18-197">But `U+D801` doesn't have enough information by itself to identify it as a lowercase letter, so `char.ToUpperInvariant` leaves it alone.</span></span> <span data-ttu-id="b6b18-198">而且它會以 `U+DC49` 相同的方式處理。</span><span class="sxs-lookup"><span data-stu-id="b6b18-198">And it handles `U+DC49` the same way.</span></span> <span data-ttu-id="b6b18-199">結果是中的小寫 ' 𐑉 ' `input` string 不會轉換成大寫的 ' 𐑉 '。</span><span class="sxs-lookup"><span data-stu-id="b6b18-199">The result is that lowercase '𐑉' in the `input` string doesn't get converted to uppercase '𐐡'.</span></span>

<span data-ttu-id="b6b18-200">以下兩個選項可將正確轉換 string 成大寫：</span><span class="sxs-lookup"><span data-stu-id="b6b18-200">Here are two options for correctly converting a string to uppercase:</span></span>

* <span data-ttu-id="b6b18-201"><xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType>在輸入上呼叫， string 而不是 `char` 逐一查看 `char` 。</span><span class="sxs-lookup"><span data-stu-id="b6b18-201">Call <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> on the input string rather than iterating `char`-by-`char`.</span></span> <span data-ttu-id="b6b18-202">`string.ToUpperInvariant`方法可以存取每個代理配對中的兩個部分，以便能夠正確處理所有的 Unicode 程式碼點。</span><span class="sxs-lookup"><span data-stu-id="b6b18-202">The `string.ToUpperInvariant` method has access to both parts of each surrogate pair, so it can handle all Unicode code points correctly.</span></span>
* <span data-ttu-id="b6b18-203">逐一查看 Unicode 純量值做為 `Rune` 實例，而不是 `char` 實例，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b6b18-203">Iterate through the Unicode scalar values as `Rune` instances instead of `char` instances, as shown in the following example.</span></span> <span data-ttu-id="b6b18-204">因為 `Rune` 實例是有效的 Unicode 純量值，所以可以傳遞給預期會在純量值上運作的 api。</span><span class="sxs-lookup"><span data-stu-id="b6b18-204">Since a `Rune` instance is a valid Unicode scalar value, it can be passed to APIs that expect to operate on a scalar value.</span></span> <span data-ttu-id="b6b18-205">例如， <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> 如下列範例所示呼叫會提供正確的結果：</span><span class="sxs-lookup"><span data-stu-id="b6b18-205">For example, calling <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> as shown in the following example gives correct results:</span></span>

  :::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::

### <a name="other-rune-apis"></a><span data-ttu-id="b6b18-206">其他 Rune api</span><span class="sxs-lookup"><span data-stu-id="b6b18-206">Other Rune APIs</span></span>

<span data-ttu-id="b6b18-207">型別會 `Rune` 公開許多 api 的類比 `char` 。</span><span class="sxs-lookup"><span data-stu-id="b6b18-207">The `Rune` type exposes analogs of many of the `char` APIs.</span></span> <span data-ttu-id="b6b18-208">例如，下列方法會鏡像類型上的靜態 Api `char` ：</span><span class="sxs-lookup"><span data-stu-id="b6b18-208">For example, the following methods mirror static APIs on the `char` type:</span></span>

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

<span data-ttu-id="b6b18-209">若要從實例取得原始純量值 `Rune` ，請使用 <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="b6b18-209">To get the raw scalar value from a `Rune` instance, use the <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="b6b18-210">若要將 `Rune` 實例轉換回的序列 `char` ，請使用 <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> 或 <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="b6b18-210">To convert a `Rune` instance back to a sequence of `char`s, use <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> or the <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="b6b18-211">由於任何 Unicode 純量值都是由單一 `char` 或代理程式配對來表示，因此任何 `Rune` 實例最多可代表2個 `char` 實例。</span><span class="sxs-lookup"><span data-stu-id="b6b18-211">Since any Unicode scalar value is representable by a single `char` or by a surrogate pair, any `Rune` instance can be represented by at most 2 `char` instances.</span></span> <span data-ttu-id="b6b18-212">使用 <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> 來查看需要多少 `char` 實例來表示 `Rune` 實例。</span><span class="sxs-lookup"><span data-stu-id="b6b18-212">Use <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> to see how many `char` instances are required to represent a `Rune` instance.</span></span>

<span data-ttu-id="b6b18-213">如需 .NET 類型的詳細資訊 `Rune` ，請參閱[ `Rune` API 參考](xref:System.Text.Rune)。</span><span class="sxs-lookup"><span data-stu-id="b6b18-213">For more information about the .NET `Rune` type, see the [`Rune` API reference](xref:System.Text.Rune).</span></span>

## <a name="grapheme-clusters"></a><span data-ttu-id="b6b18-214">語素簇叢集</span><span class="sxs-lookup"><span data-stu-id="b6b18-214">Grapheme clusters</span></span>

<span data-ttu-id="b6b18-215">可能會因為多個程式碼點的組合而產生一個字元，因此，經常用來取代 "character" 的更具描述性詞彙就是[語素簇 cluster](https://www.unicode.org/glossary/#grapheme_cluster)。</span><span class="sxs-lookup"><span data-stu-id="b6b18-215">What looks like one character might result from a combination of multiple code points, so a more descriptive term that is often used in place of "character" is [grapheme cluster](https://www.unicode.org/glossary/#grapheme_cluster).</span></span> <span data-ttu-id="b6b18-216">.NET 中的對等詞彙是[text 元素](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A)。</span><span class="sxs-lookup"><span data-stu-id="b6b18-216">The equivalent term in .NET is [text element](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span></span>

<span data-ttu-id="b6b18-217">請考慮「 `string` a」、「×」實例。</span><span class="sxs-lookup"><span data-stu-id="b6b18-217">Consider the `string` instances "a", "á".</span></span> <span data-ttu-id="b6b18-218">「×」和「」 `👩🏽‍🚒` 。</span><span class="sxs-lookup"><span data-stu-id="b6b18-218">"á", and "`👩🏽‍🚒`".</span></span> <span data-ttu-id="b6b18-219">如果您的作業系統會依照 Unicode 標準的指定來處理它們，則這些實例中的每一個 `string` 都會顯示為單一文字元素或語素簇叢集。</span><span class="sxs-lookup"><span data-stu-id="b6b18-219">If your operating system handles them as specified by the Unicode standard, each of these `string` instances appears as a single text element or grapheme cluster.</span></span> <span data-ttu-id="b6b18-220">但最後兩個則是由一個以上的純量值程式碼點表示。</span><span class="sxs-lookup"><span data-stu-id="b6b18-220">But the last two are represented by more than one scalar value code point.</span></span>

* <span data-ttu-id="b6b18-221">string"A" 是以一個純量值表示，且包含一個 `char` 實例。</span><span class="sxs-lookup"><span data-stu-id="b6b18-221">The string "a" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+0061 LATIN SMALL LETTER A`

* <span data-ttu-id="b6b18-222">「 string ×」是以一個純量值表示，並包含一個 `char` 實例。</span><span class="sxs-lookup"><span data-stu-id="b6b18-222">The string "á" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+00E1 LATIN SMALL LETTER A WITH ACUTE`

* <span data-ttu-id="b6b18-223">「 string ×」看起來與「×」相同，但以兩個純量值表示，並包含兩個 `char` 實例。</span><span class="sxs-lookup"><span data-stu-id="b6b18-223">The string "á" looks the same as "á" but is represented by two scalar values and contains two `char` instances.</span></span>

  * `U+0061 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* <span data-ttu-id="b6b18-224">最後， string " `👩🏽‍🚒` " 會以四個純量值表示，並包含七個 `char` 實例。</span><span class="sxs-lookup"><span data-stu-id="b6b18-224">Finally, the string "`👩🏽‍🚒`" is represented by four scalar values and contains seven `char` instances.</span></span>

  * <span data-ttu-id="b6b18-225">`U+1F469 WOMAN`（補充範圍，需要代理配對）</span><span class="sxs-lookup"><span data-stu-id="b6b18-225">`U+1F469 WOMAN` (supplementary range, requires a surrogate pair)</span></span>
  * <span data-ttu-id="b6b18-226">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4`（補充範圍，需要代理配對）</span><span class="sxs-lookup"><span data-stu-id="b6b18-226">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (supplementary range, requires a surrogate pair)</span></span>
  * `U+200D ZERO WIDTH JOINER`
  * <span data-ttu-id="b6b18-227">`U+1F692 FIRE ENGINE`（補充範圍，需要代理配對）</span><span class="sxs-lookup"><span data-stu-id="b6b18-227">`U+1F692 FIRE ENGINE` (supplementary range, requires a surrogate pair)</span></span>

<span data-ttu-id="b6b18-228">在上述一些範例中（例如結合輔色修飾詞或外觀色調修飾詞），程式碼點不會在螢幕上顯示為獨立元素。</span><span class="sxs-lookup"><span data-stu-id="b6b18-228">In some of the preceding examples - such as the combining accent modifier or the skin tone modifier - the code point does not display as a standalone element on the screen.</span></span> <span data-ttu-id="b6b18-229">相反地，它是用來修改之前出現的文字元素外觀。</span><span class="sxs-lookup"><span data-stu-id="b6b18-229">Rather, it serves to modify the appearance of a text element that came before it.</span></span> <span data-ttu-id="b6b18-230">這些範例顯示，它可能會採用多個純量值來組成我們將其視為單一「字元」或「語素簇叢集」的意義。</span><span class="sxs-lookup"><span data-stu-id="b6b18-230">These examples show that it might take multiple scalar values to make up what we think of as a single "character," or "grapheme cluster."</span></span>

<span data-ttu-id="b6b18-231">若要列舉的語素簇叢集 `string` ，請使用 <xref:System.Globalization.StringInfo> 類別，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b6b18-231">To enumerate the grapheme clusters of a `string`, use the <xref:System.Globalization.StringInfo> class as shown in the following example.</span></span> <span data-ttu-id="b6b18-232">如果您熟悉 Swift，則 .NET 類型在 `StringInfo` 概念上類似于[swift 的 `character` 類型](https://developer.apple.com/documentation/swift/character)。</span><span class="sxs-lookup"><span data-stu-id="b6b18-232">If you're familiar with Swift, the .NET `StringInfo` type is conceptually similar to [Swift's `character` type](https://developer.apple.com/documentation/swift/character).</span></span>

### <a name="example-count-char-rune-and-text-element-instances"></a><span data-ttu-id="b6b18-233">範例： count char 、 Rune 和 text 元素實例</span><span class="sxs-lookup"><span data-stu-id="b6b18-233">Example: count char, Rune, and text element instances</span></span>

<span data-ttu-id="b6b18-234">在 .NET Api 中，語素簇叢集稱為「*文字」元素*。</span><span class="sxs-lookup"><span data-stu-id="b6b18-234">In .NET APIs, a grapheme cluster is called a *text element*.</span></span> <span data-ttu-id="b6b18-235">下列方法示範 `char` `Rune` 中、和文字元素實例之間的差異 `string` ：</span><span class="sxs-lookup"><span data-stu-id="b6b18-235">The following method demonstrates the differences between `char`, `Rune`, and text element instances in a `string`:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::

<span data-ttu-id="b6b18-236">如果您在 .NET Framework 或 .NET Core 3.1 或更早版本中執行此程式碼，則會顯示表情的文字元素計數 `4` 。</span><span class="sxs-lookup"><span data-stu-id="b6b18-236">If you run this code in .NET Framework or .NET Core 3.1 or earlier, the text element count for the emoji shows `4`.</span></span> <span data-ttu-id="b6b18-237">這是因為在 .NET 5 中修正的類別中有 bug `StringInfo` 。</span><span class="sxs-lookup"><span data-stu-id="b6b18-237">That is due to a bug in the `StringInfo` class that is fixed in .NET 5.</span></span>

### <a name="example-splitting-string-instances"></a><span data-ttu-id="b6b18-238">範例：分割 string 實例</span><span class="sxs-lookup"><span data-stu-id="b6b18-238">Example: splitting string instances</span></span>

<span data-ttu-id="b6b18-239">分割 `string` 實例時，請避免分割代理項配對和語素簇叢集。</span><span class="sxs-lookup"><span data-stu-id="b6b18-239">When splitting `string` instances, avoid splitting surrogate pairs and grapheme clusters.</span></span> <span data-ttu-id="b6b18-240">請考慮下列不正確程式碼的範例，其打算在中插入分行符號，每10個字元 string ：</span><span class="sxs-lookup"><span data-stu-id="b6b18-240">Consider the following example of incorrect code, which intends to insert line breaks every 10 characters in a string:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::

<span data-ttu-id="b6b18-241">因為此程式碼會列舉 `char` 實例，所以會分割一個跨10界限的代理配對， `char` 並在其間插入一個分行符號。</span><span class="sxs-lookup"><span data-stu-id="b6b18-241">Because this code enumerates `char` instances, a surrogate pair that happens to straddle a 10-`char` boundary will be split and a newline injected between them.</span></span> <span data-ttu-id="b6b18-242">這項插入會導入資料損毀，因為代理程式碼點僅有意義的配對。</span><span class="sxs-lookup"><span data-stu-id="b6b18-242">This insertion introduces data corruption, because surrogate code points are meaningful only as pairs.</span></span>

<span data-ttu-id="b6b18-243">如果您列舉 `Rune` 實例（純量值）而不是實例，則不會去除資料損毀的可能性 `char` 。</span><span class="sxs-lookup"><span data-stu-id="b6b18-243">The potential for data corruption isn't eliminated if you enumerate `Rune` instances (scalar values) instead of `char` instances.</span></span> <span data-ttu-id="b6b18-244">一組 `Rune` 實例可能會構成跨越10界限的語素簇叢集 `char` 。</span><span class="sxs-lookup"><span data-stu-id="b6b18-244">A set of `Rune` instances might make up a grapheme cluster that straddles a 10-`char` boundary.</span></span> <span data-ttu-id="b6b18-245">如果語素簇叢集集已分割，則無法正確地加以解讀。</span><span class="sxs-lookup"><span data-stu-id="b6b18-245">If the grapheme cluster set is split up, it can't be interpreted correctly.</span></span>

<span data-ttu-id="b6b18-246">較好的方法是藉 string 由計算語素簇叢集或文字元素來中斷，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="b6b18-246">A better approach is to break the string by counting grapheme clusters, or text elements, as in the following example:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::

<span data-ttu-id="b6b18-247">如先前所述，在 .net 5 以外的 .NET 中， `StringInfo` 類別可能會不正確地處理某些語素簇叢集。</span><span class="sxs-lookup"><span data-stu-id="b6b18-247">As noted earlier, however, in implementations of .NET other than .NET 5, the `StringInfo` class might handle some grapheme clusters incorrectly.</span></span>

## <a name="utf-8-and-utf-32"></a><span data-ttu-id="b6b18-248">UTF-8 和 UTF-32</span><span class="sxs-lookup"><span data-stu-id="b6b18-248">UTF-8 and UTF-32</span></span>

<span data-ttu-id="b6b18-249">上述章節著重于 UTF-16，因為這是 .NET 用來對實例進行編碼的原因 `string` 。</span><span class="sxs-lookup"><span data-stu-id="b6b18-249">The preceding sections focused on UTF-16 because that's what .NET uses to encode `string` instances.</span></span> <span data-ttu-id="b6b18-250">Unicode [utf-8](https://www.unicode.org/faq/utf_bom.html#UTF8)和[UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32)還有其他編碼系統。</span><span class="sxs-lookup"><span data-stu-id="b6b18-250">There are other encoding systems for Unicode - [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) and [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32).</span></span> <span data-ttu-id="b6b18-251">這些編碼分別使用8位程式碼單位和32位程式碼單位。</span><span class="sxs-lookup"><span data-stu-id="b6b18-251">These encodings use 8-bit code units and 32-bit code units, respectively.</span></span>

<span data-ttu-id="b6b18-252">就像 UTF-16，UTF-8 需要多個程式碼單位來代表一些 Unicode 純量值。</span><span class="sxs-lookup"><span data-stu-id="b6b18-252">Like UTF-16, UTF-8 requires multiple code units to represent some Unicode scalar values.</span></span> <span data-ttu-id="b6b18-253">UTF-32 可以代表單一32位程式碼單位中的任何純量值。</span><span class="sxs-lookup"><span data-stu-id="b6b18-253">UTF-32 can represent any scalar value in a single 32-bit code unit.</span></span>

<span data-ttu-id="b6b18-254">以下範例顯示在這三個 Unicode 編碼系統中，如何表示相同的 Unicode 程式碼點：</span><span class="sxs-lookup"><span data-stu-id="b6b18-254">Here are some examples showing how the same Unicode code point is represented in each of these three Unicode encoding systems:</span></span>

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

<span data-ttu-id="b6b18-255">如先前所述，來自[代理配對](#surrogate-pairs)的單一 utf-16 程式碼單位本身毫無意義。</span><span class="sxs-lookup"><span data-stu-id="b6b18-255">As noted earlier, a single UTF-16 code unit from a [surrogate pair](#surrogate-pairs) is meaningless by itself.</span></span> <span data-ttu-id="b6b18-256">同樣地，如果單一 UTF-8 程式碼單位是以兩個、三個或四個用來計算純量值的序列，則不會有任何意義。</span><span class="sxs-lookup"><span data-stu-id="b6b18-256">In the same way, a single UTF-8 code unit is meaningless by itself if it's in a sequence of two, three, or four used to calculate a scalar value.</span></span>

### <a name="endianness"></a><span data-ttu-id="b6b18-257">位元組序</span><span class="sxs-lookup"><span data-stu-id="b6b18-257">Endianness</span></span>

<span data-ttu-id="b6b18-258">在 .NET 中，的 UTF-16 程式碼單位會以 string 16 位整數（實例）的序列儲存在連續記憶體中 `char` 。</span><span class="sxs-lookup"><span data-stu-id="b6b18-258">In .NET, the UTF-16 code units of a string are stored in contiguous memory as a sequence of 16-bit integers (`char` instances).</span></span> <span data-ttu-id="b6b18-259">個別程式碼單位的位會根據目前架構的[位元組](https://en.wikipedia.org/wiki/Endianness)程式來配置。</span><span class="sxs-lookup"><span data-stu-id="b6b18-259">The bits of individual code units are laid out according to the [endianness](https://en.wikipedia.org/wiki/Endianness) of the current architecture.</span></span>

<span data-ttu-id="b6b18-260">在以位元組為基礎的架構上，由 string utf-16 程式碼點組成的會 `[ D801 DCCC ]` 在記憶體中配置為位元組 `[ 0x01, 0xD8, 0xCC, 0xDC ]` 。</span><span class="sxs-lookup"><span data-stu-id="b6b18-260">On a little-endian architecture, the string consisting of the UTF-16 code points `[ D801 DCCC ]` would be laid out in memory as the bytes `[ 0x01, 0xD8, 0xCC, 0xDC ]`.</span></span> <span data-ttu-id="b6b18-261">在以大到小的結構上，相同的 string 會在記憶體中配置為位元組 `[ 0xD8, 0x01, 0xDC, 0xCC ]` 。</span><span class="sxs-lookup"><span data-stu-id="b6b18-261">On a big-endian architecture that same string would be laid out in memory as the bytes `[ 0xD8, 0x01, 0xDC, 0xCC ]`.</span></span>

<span data-ttu-id="b6b18-262">彼此通訊的電腦系統必須同意透過網路的資料標記法。</span><span class="sxs-lookup"><span data-stu-id="b6b18-262">Computer systems that communicate with each other must agree on the representation of data crossing the wire.</span></span> <span data-ttu-id="b6b18-263">大部分的網路通訊協定都會在傳輸文字時使用 UTF-8 做為標準，部分是為了避免因大型電腦與小序電腦通訊而產生的問題。</span><span class="sxs-lookup"><span data-stu-id="b6b18-263">Most network protocols use UTF-8 as a standard when transmitting text, partly to avoid issues that might result from a big-endian machine communicating with a little-endian machine.</span></span> <span data-ttu-id="b6b18-264">由 string utf-8 程式碼點組成的，一律會以 `[ F0 90 93 8C ]` 位元組表示， `[ 0xF0, 0x90, 0x93, 0x8C ]` 而不論是否為 endian。</span><span class="sxs-lookup"><span data-stu-id="b6b18-264">The string consisting of the UTF-8 code points `[ F0 90 93 8C ]` will always be represented as the bytes `[ 0xF0, 0x90, 0x93, 0x8C ]` regardless of endianness.</span></span>

<span data-ttu-id="b6b18-265">若要使用 UTF-8 來傳輸文字，.NET 應用程式通常會使用類似下列範例的程式碼：</span><span class="sxs-lookup"><span data-stu-id="b6b18-265">To use UTF-8 for transmitting text, .NET applications often use code like the following example:</span></span>

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

<span data-ttu-id="b6b18-266">在上述範例中，方法[GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A)會將 utf-16 解碼 `string` 回一系列 Unicode 純量值，然後將這些純量值重新編碼為 utf-8，並將產生的序列放入 `byte` 陣列中。</span><span class="sxs-lookup"><span data-stu-id="b6b18-266">In the preceding example, the method [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) decodes the UTF-16 `string` back into a series of Unicode scalar values, then it re-encodes those scalar values into UTF-8 and places the resulting sequence into a `byte` array.</span></span> <span data-ttu-id="b6b18-267">方法[編碼 GetString](xref:System.Text.UTF8Encoding.GetString%2A)會執行相反的轉換，將 utf-8 `byte` 陣列轉換成 utf-16 `string` 。</span><span class="sxs-lookup"><span data-stu-id="b6b18-267">The method [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) performs the opposite transformation, converting a UTF-8 `byte` array to a UTF-16 `string`.</span></span>

> [!WARNING]
> <span data-ttu-id="b6b18-268">由於 UTF-8 在網際網路上很常見，因此從網路讀取未經處理的位元組，並將資料視為 UTF-8，可能會很有吸引力。</span><span class="sxs-lookup"><span data-stu-id="b6b18-268">Since UTF-8 is commonplace on the internet, it may be tempting to read raw bytes from the wire and to treat the data as if it were UTF-8.</span></span> <span data-ttu-id="b6b18-269">不過，您應該驗證它的格式是否正確。</span><span class="sxs-lookup"><span data-stu-id="b6b18-269">However, you should validate that it is indeed well-formed.</span></span> <span data-ttu-id="b6b18-270">惡意用戶端可能會將格式不正確的 UTF-8 提交給您的服務。</span><span class="sxs-lookup"><span data-stu-id="b6b18-270">A malicious client might submit ill-formed UTF-8 to your service.</span></span> <span data-ttu-id="b6b18-271">如果您以正確格式的方式操作該資料，可能會在您的應用程式中造成錯誤或安全性漏洞。</span><span class="sxs-lookup"><span data-stu-id="b6b18-271">If you operate on that data as if it were well-formed, it could cause errors or security holes in your application.</span></span> <span data-ttu-id="b6b18-272">若要驗證 UTF-8 資料，您可以使用類似的方法 `Encoding.UTF8.GetString` ，將傳入的資料轉換成時，會執行驗證 `string` 。</span><span class="sxs-lookup"><span data-stu-id="b6b18-272">To validate UTF-8 data, you can use a method like `Encoding.UTF8.GetString`, which will perform validation while converting the incoming data to a `string`.</span></span>

### <a name="well-formed-encoding"></a><span data-ttu-id="b6b18-273">格式正確的編碼</span><span class="sxs-lookup"><span data-stu-id="b6b18-273">Well-formed encoding</span></span>

<span data-ttu-id="b6b18-274">格式正確的 Unicode 編碼是 string 可以明確解碼，而且不會發生錯誤的程式碼單位序列。</span><span class="sxs-lookup"><span data-stu-id="b6b18-274">A well-formed Unicode encoding is a string of code units that can be decoded unambiguously and without error into a sequence of Unicode scalar values.</span></span> <span data-ttu-id="b6b18-275">格式正確的資料可以在 UTF-8、UTF-16 和 UTF-32 之間自由地來回轉碼。</span><span class="sxs-lookup"><span data-stu-id="b6b18-275">Well-formed data can be transcoded freely back and forth between UTF-8, UTF-16, and UTF-32.</span></span>

<span data-ttu-id="b6b18-276">編碼順序是否語式正確的問題，或不與機器架構的 endian 格式無關。</span><span class="sxs-lookup"><span data-stu-id="b6b18-276">The question of whether an encoding sequence is well-formed or not is unrelated to the endianness of a machine's architecture.</span></span> <span data-ttu-id="b6b18-277">格式不正確的 UTF-8 順序格式不正確，其方式與以大到小的電腦相同。</span><span class="sxs-lookup"><span data-stu-id="b6b18-277">An ill-formed UTF-8 sequence is ill-formed in the same way on both big-endian and little-endian machines.</span></span>

<span data-ttu-id="b6b18-278">以下是一些格式錯誤編碼的範例：</span><span class="sxs-lookup"><span data-stu-id="b6b18-278">Here are some examples of ill-formed encodings:</span></span>

* <span data-ttu-id="b6b18-279">在 UTF-8 中，順序格式不 `[ 6C C2 61 ]` 正確，因為 `C2` 後面不能有 `61` 。</span><span class="sxs-lookup"><span data-stu-id="b6b18-279">In UTF-8, the sequence `[ 6C C2 61 ]` is ill-formed because `C2` cannot be followed by `61`.</span></span>

* <span data-ttu-id="b6b18-280">在 UTF-16 中，順序 `[ DC00 DD00 ]` （或 c # 中的 string `"\udc00\udd00"` ）格式不正確，因為低的代理 `DC00` 不能後面接著另一個低代理 `DD00` 。</span><span class="sxs-lookup"><span data-stu-id="b6b18-280">In UTF-16, the sequence `[ DC00 DD00 ]` (or, in C#, the string `"\udc00\udd00"`) is ill-formed because the low surrogate `DC00` cannot be followed by another low surrogate `DD00`.</span></span>

* <span data-ttu-id="b6b18-281">在 UTF-32 中，順序的 `[ 0011ABCD ]` 格式不正確，因為超出 `0011ABCD` Unicode 純量值的範圍。</span><span class="sxs-lookup"><span data-stu-id="b6b18-281">In UTF-32, the sequence `[ 0011ABCD ]` is ill-formed because `0011ABCD` is outside the range of Unicode scalar values.</span></span>

<span data-ttu-id="b6b18-282">在 .NET 中， `string` 實例幾乎一律包含格式正確的 utf-16 資料，但不保證。</span><span class="sxs-lookup"><span data-stu-id="b6b18-282">In .NET, `string` instances almost always contain well-formed UTF-16 data, but that isn't guaranteed.</span></span> <span data-ttu-id="b6b18-283">下列範例顯示在實例中建立格式不正確之 UTF-16 資料的有效 c # 程式碼 `string` 。</span><span class="sxs-lookup"><span data-stu-id="b6b18-283">The following examples show valid C# code that creates ill-formed UTF-16 data in `string` instances.</span></span>

* <span data-ttu-id="b6b18-284">格式不正確的常值：</span><span class="sxs-lookup"><span data-stu-id="b6b18-284">An ill-formed literal:</span></span>

  ```csharp
  const string s = "\ud800";
  ```

* <span data-ttu-id="b6b18-285">用來分割代理配對的子字串：</span><span class="sxs-lookup"><span data-stu-id="b6b18-285">A substring that splits up a surrogate pair:</span></span>

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

<span data-ttu-id="b6b18-286">之類 [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) 的 api 不會傳回格式不正確的 `string` 實例。</span><span class="sxs-lookup"><span data-stu-id="b6b18-286">APIs like [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) never return ill-formed `string` instances.</span></span> <span data-ttu-id="b6b18-287">`Encoding.GetString`和 `Encoding.GetBytes` 方法會偵測輸入中格式不正確的序列，並在產生輸出時執行字元替代。</span><span class="sxs-lookup"><span data-stu-id="b6b18-287">`Encoding.GetString` and `Encoding.GetBytes` methods detect ill-formed sequences in the input and perform character substitution when generating the output.</span></span> <span data-ttu-id="b6b18-288">例如，如果 [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) 在輸入中看到非 ASCII 位元組（在 u + 0000 的範圍外），它會將 '？ ' 插入傳回的 `string` 實例中。</span><span class="sxs-lookup"><span data-stu-id="b6b18-288">For example, if [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) sees a non-ASCII byte in the input (outside the range U+0000..U+007F), it inserts a '?' into the returned `string` instance.</span></span> <span data-ttu-id="b6b18-289">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A)`U+FFFD REPLACEMENT CHARACTER ('�')`在傳回的實例中，取代格式不正確的 utf-8 序列 `string` 。</span><span class="sxs-lookup"><span data-stu-id="b6b18-289">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A) replaces ill-formed UTF-8 sequences with `U+FFFD REPLACEMENT CHARACTER ('�')` in the returned `string` instance.</span></span> <span data-ttu-id="b6b18-290">如需詳細資訊，請參閱[Unicode 標準](https://www.unicode.org/versions/latest/)，第5.22 和3.9 節。</span><span class="sxs-lookup"><span data-stu-id="b6b18-290">For more information, see [the Unicode Standard](https://www.unicode.org/versions/latest/), Sections 5.22 and 3.9.</span></span>

<span data-ttu-id="b6b18-291">`Encoding`當出現格式不正確的序列時，內建類別也可以設定為擲回例外狀況，而不是執行字元替代。</span><span class="sxs-lookup"><span data-stu-id="b6b18-291">The built-in `Encoding` classes can also be configured to throw an exception rather than perform character substitution when ill-formed sequences are seen.</span></span> <span data-ttu-id="b6b18-292">這種方法通常用於可能無法接受字元替代的安全性敏感應用程式中。</span><span class="sxs-lookup"><span data-stu-id="b6b18-292">This approach is often used in security-sensitive applications where character substitution might not be acceptable.</span></span>

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

<span data-ttu-id="b6b18-293">如需如何使用內建類別的詳細資訊 `Encoding` ，請參閱[如何在 .net 中使用字元編碼類別](character-encoding.md)。</span><span class="sxs-lookup"><span data-stu-id="b6b18-293">For information about how to use the built-in `Encoding` classes, see [How to use character encoding classes in .NET](character-encoding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b6b18-294">請參閱</span><span class="sxs-lookup"><span data-stu-id="b6b18-294">See also</span></span>

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [<span data-ttu-id="b6b18-295">全球化和當地語系化</span><span class="sxs-lookup"><span data-stu-id="b6b18-295">Globalization and Localization</span></span>](../globalization-localization/index.md)
