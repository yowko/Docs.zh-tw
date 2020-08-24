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
# <a name="character-encoding-in-net"></a><span data-ttu-id="5b1b1-103">.NET 中的字元編碼</span><span class="sxs-lookup"><span data-stu-id="5b1b1-103">Character encoding in .NET</span></span>

<span data-ttu-id="5b1b1-104">本文提供 char .net 所使用之 acter 編碼系統的簡介。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-104">This article provides an introduction to character encoding systems that are used by .NET.</span></span> <span data-ttu-id="5b1b1-105">本文說明 <xref:System.String> 、 <xref:System.Char> 、 <xref:System.Text.Rune> 和 <xref:System.Globalization.StringInfo> 類型如何使用 Unicode、utf-16 和 utf-8。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-105">The article explains how the <xref:System.String>, <xref:System.Char>, <xref:System.Text.Rune>, and <xref:System.Globalization.StringInfo> types work with Unicode, UTF-16, and UTF-8.</span></span>

<span data-ttu-id="5b1b1-106">「詞彙」（ \* char acter\* ）一詞的用途是在*讀者視為單一顯示元素*的一般意義上使用。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-106">The term *character* is used here in the general sense of *what a reader perceives as a single display element*.</span></span> <span data-ttu-id="5b1b1-107">常見範例為字母 "a"、符號 "@" 和表情 " 🐂 "。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-107">Common examples are the letter "a", the symbol "@", and the emoji "🐂".</span></span> <span data-ttu-id="5b1b1-108">有時看起來像 char 是一個 acter 實際上是由多個獨立的顯示元素組成，如 [語素簇](#grapheme-clusters) 叢集上的章節所述。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-108">Sometimes what looks like one character is actually composed of multiple independent display elements, as the section on [grapheme clusters](#grapheme-clusters) explains.</span></span>

## <a name="the-no-locstring-and-no-locchar-types"></a><span data-ttu-id="5b1b1-109">string和 char 類型</span><span class="sxs-lookup"><span data-stu-id="5b1b1-109">The string and char types</span></span>

<span data-ttu-id="5b1b1-110">類別的實例 [string](xref:System.String) 代表一些文字。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-110">An instance of the [string](xref:System.String) class represents some text.</span></span> <span data-ttu-id="5b1b1-111">`string`是邏輯上的16位值序列，每個值都是結構的實例 [char](xref:System.Char) 。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-111">A `string` is logically a sequence of 16-bit values, each of which is an instance of the [char](xref:System.Char) struct.</span></span> <span data-ttu-id="5b1b1-112">[ string 。Length](xref:System.String.Length)屬性會傳回 `char` 實例中的實例數目 `string` 。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-112">The [string.Length](xref:System.String.Length) property returns the number of `char` instances in the `string` instance.</span></span>

<span data-ttu-id="5b1b1-113">下列範例函式會以十六進位標記法來印出中所有 `char` 實例的值 `string` ：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-113">The following sample function prints out the values in hexadecimal notation of all the `char` instances in a `string`:</span></span>

<span data-ttu-id="5b1b1-114">：：： code language = "csharp" source = "程式碼片段/ char acter-編碼-簡介/csharp/PrintStringChars .cs" id = "SnippetPrintChars"：：：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-114">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::</span></span>

<span data-ttu-id="5b1b1-115">將 string "Hello" 傳遞至此函式，您會取得下列輸出：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-115">Pass the string "Hello" to this function, and you get the following output:</span></span>

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

<span data-ttu-id="5b1b1-116">每個 char acter 都是以單一 `char` 值表示。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-116">Each character is represented by a single `char` value.</span></span> <span data-ttu-id="5b1b1-117">這種模式適用于大部分世界的語言。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-117">That pattern holds true for most of the world's languages.</span></span> <span data-ttu-id="5b1b1-118">例如，以下是兩個中文 acters 的輸出 char ，這聽起來像是 *nǐ hǎo* ，意思是 *Hello*：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-118">For example, here's the output for two Chinese characters that sound like *nǐ hǎo* and mean *Hello*:</span></span>

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

<span data-ttu-id="5b1b1-119">不過，對於某些語言以及某些符號和表情符號，會採用兩個 `char` 實例來代表單一 char acter。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-119">However, for some languages and for some symbols and emoji, it takes two `char` instances to represent a single character.</span></span> <span data-ttu-id="5b1b1-120">例如，比較單字中的 char acters 和 `char` 實例，這表示 Osage 語言中的 *Osage* ：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-120">For example, compare the characters and `char` instances in the word that means *Osage* in the Osage language:</span></span>

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

<span data-ttu-id="5b1b1-121">在上述範例中， char 除了空格以外的每個 acter 都是以兩個實例來表示 `char` 。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-121">In the preceding example, each character except the space is represented by two `char` instances.</span></span>

<span data-ttu-id="5b1b1-122">單一 Unicode 表情也會以兩種 `char` 方式表示，如下列範例所示，顯示 ox 的表情：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-122">A single Unicode emoji is also represented by two `char`s, as seen in the following example showing an ox emoji:</span></span>

```
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

<span data-ttu-id="5b1b1-123">這些範例顯示的值 `string.Length` （指出 `char` 實例數目）不一定表示顯示的 char acters 數目。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-123">These examples show that the value of `string.Length`, which indicates the number of `char` instances, doesn't necessarily indicate the number of displayed characters.</span></span> <span data-ttu-id="5b1b1-124">單一 `char` 實例本身不一定代表 char acter。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-124">A single `char` instance by itself doesn't necessarily represent a character.</span></span>

<span data-ttu-id="5b1b1-125">`char`對應至單一 acter 的配對 char 稱為*代理配對*。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-125">The `char` pairs that map to a single character are called *surrogate pairs*.</span></span> <span data-ttu-id="5b1b1-126">若要瞭解其運作方式，您必須瞭解 Unicode 和 UTF-16 編碼。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-126">To understand how they work, you need to understand Unicode and UTF-16 encoding.</span></span>

## <a name="unicode-code-points"></a><span data-ttu-id="5b1b1-127">Unicode 字碼指標</span><span class="sxs-lookup"><span data-stu-id="5b1b1-127">Unicode code points</span></span>

<span data-ttu-id="5b1b1-128">Unicode 是國際編碼標準，可用於各種不同的平臺，以及各種語言和腳本。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-128">Unicode is an international encoding standard for use on various platforms and with various languages and scripts.</span></span>

<span data-ttu-id="5b1b1-129">Unicode 標準定義1100000以上的程式 [代碼點](https://www.unicode.org/glossary/#code_point)。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-129">The Unicode Standard defines over 1.1 million [code points](https://www.unicode.org/glossary/#code_point).</span></span> <span data-ttu-id="5b1b1-130">程式碼點是一個整數值，範圍從0到 `U+10FFFF` (decimal 1114111) 。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-130">A code point is an integer value that can range from 0 to `U+10FFFF` (decimal 1,114,111).</span></span> <span data-ttu-id="5b1b1-131">某些程式碼點會指派給字母、符號或表情。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-131">Some code points are assigned to letters, symbols, or emoji.</span></span> <span data-ttu-id="5b1b1-132">其他會指派給控制文字或 acters 顯示方式的動作 char ，例如前進至新行。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-132">Others are assigned to actions that control how text or characters are displayed, such as advance to a new line.</span></span> <span data-ttu-id="5b1b1-133">許多程式碼點尚未指派。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-133">Many code points are not yet assigned.</span></span>

<span data-ttu-id="5b1b1-134">以下是程式碼點指派的一些範例，其中包含出現在其中的 Unicode char ts 連結：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-134">Here are some examples of code point assignments, with links to Unicode charts in which they appear:</span></span>

|<span data-ttu-id="5b1b1-135">小數位數</span><span class="sxs-lookup"><span data-stu-id="5b1b1-135">Decimal</span></span>|<span data-ttu-id="5b1b1-136">Hex</span><span class="sxs-lookup"><span data-stu-id="5b1b1-136">Hex</span></span>       |<span data-ttu-id="5b1b1-137">範例</span><span class="sxs-lookup"><span data-stu-id="5b1b1-137">Example</span></span>|<span data-ttu-id="5b1b1-138">描述</span><span class="sxs-lookup"><span data-stu-id="5b1b1-138">Description</span></span>|
|------:|----------|-------|-----------|
|<span data-ttu-id="5b1b1-139">10</span><span class="sxs-lookup"><span data-stu-id="5b1b1-139">10</span></span>     | `U+000A` |<span data-ttu-id="5b1b1-140">N/A</span><span class="sxs-lookup"><span data-stu-id="5b1b1-140">N/A</span></span>| <span data-ttu-id="5b1b1-141">[換行字元](https://www.unicode.org/charts/PDF/U0000.pdf)</span><span class="sxs-lookup"><span data-stu-id="5b1b1-141">[LINE FEED](https://www.unicode.org/charts/PDF/U0000.pdf)</span></span> |
|<span data-ttu-id="5b1b1-142">65</span><span class="sxs-lookup"><span data-stu-id="5b1b1-142">65</span></span>     | `U+0061` | <span data-ttu-id="5b1b1-143">a</span><span class="sxs-lookup"><span data-stu-id="5b1b1-143">a</span></span> | <span data-ttu-id="5b1b1-144">[拉丁小寫字母 A](https://www.unicode.org/charts/PDF/U0000.pdf)</span><span class="sxs-lookup"><span data-stu-id="5b1b1-144">[LATIN SMALL LETTER A](https://www.unicode.org/charts/PDF/U0000.pdf)</span></span> |
|<span data-ttu-id="5b1b1-145">562</span><span class="sxs-lookup"><span data-stu-id="5b1b1-145">562</span></span>    | `U+0232` | <span data-ttu-id="5b1b1-146">Ȳ</span><span class="sxs-lookup"><span data-stu-id="5b1b1-146">Ȳ</span></span> | <span data-ttu-id="5b1b1-147">[拉丁文大寫字母 Y 加上音符號](https://www.unicode.org/charts/PDF/U0180.pdf)</span><span class="sxs-lookup"><span data-stu-id="5b1b1-147">[LATIN CAPITAL LETTER Y WITH MACRON](https://www.unicode.org/charts/PDF/U0180.pdf)</span></span> |
|<span data-ttu-id="5b1b1-148">68675</span><span class="sxs-lookup"><span data-stu-id="5b1b1-148">68,675</span></span> | `U+10C43`| <span data-ttu-id="5b1b1-149">𐱃</span><span class="sxs-lookup"><span data-stu-id="5b1b1-149">𐱃</span></span> | <span data-ttu-id="5b1b1-150">[舊的土耳其文字母鄂爾](https://www.unicode.org/charts/PDF/U10C00.pdf)</span><span class="sxs-lookup"><span data-stu-id="5b1b1-150">[OLD TURKIC LETTER ORKHON AT](https://www.unicode.org/charts/PDF/U10C00.pdf)</span></span> |
|<span data-ttu-id="5b1b1-151">127801</span><span class="sxs-lookup"><span data-stu-id="5b1b1-151">127,801</span></span>| `U+1F339`| <span data-ttu-id="5b1b1-152">🌹</span><span class="sxs-lookup"><span data-stu-id="5b1b1-152">🌹</span></span> | <span data-ttu-id="5b1b1-153">[玫瑰的表情](https://www.unicode.org/charts/PDF/U1F300.pdf)</span><span class="sxs-lookup"><span data-stu-id="5b1b1-153">[ROSE emoji](https://www.unicode.org/charts/PDF/U1F300.pdf)</span></span> |

<span data-ttu-id="5b1b1-154">程式碼點通常是使用語法來參考 `U+xxxx` ，其中 `xxxx` 是十六進位編碼的整數值。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-154">Code points are customarily referred to by using the syntax `U+xxxx`, where `xxxx` is the hex-encoded integer value.</span></span>

<span data-ttu-id="5b1b1-155">在完整範圍的程式碼點中，有兩個子範圍：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-155">Within the full range of code points there are two subranges:</span></span>

* <span data-ttu-id="5b1b1-156">範圍中的 \*\*基本多語系平面 (BMP) \*\* `U+0000..U+FFFF` 。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-156">The **Basic Multilingual Plane (BMP)** in the range `U+0000..U+FFFF`.</span></span> <span data-ttu-id="5b1b1-157">這個16位範圍提供65536的程式碼點，足以涵蓋世界上大部分的書寫系統。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-157">This 16-bit range provides 65,536 code points, enough to cover the majority of the world's writing systems.</span></span>
* <span data-ttu-id="5b1b1-158">範圍內的**補充程式碼點** `U+10000..U+10FFFF` 。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-158">**Supplementary code points** in the range `U+10000..U+10FFFF`.</span></span> <span data-ttu-id="5b1b1-159">這個21位範圍提供超過一百萬個額外的程式碼點，可用於較不知名的語言和其他用途，例如 emoji。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-159">This 21-bit range provides more than a million additional code points that can be used for less well-known languages and other purposes such as emojis.</span></span>

<span data-ttu-id="5b1b1-160">下圖說明 BMP 與補充程式碼點之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-160">The following diagram illustrates the relationship between the BMP and the supplementary code points.</span></span>

:::image type="content" source="media/:::非 loc (char) ：：： acter-encoding-introduction/bmp-and-supplementary.svg" alt-text =" BMP 和補充程式碼點"：：：

## <a name="utf-16-code-units"></a><span data-ttu-id="5b1b1-162">UTF-16 程式碼單位</span><span class="sxs-lookup"><span data-stu-id="5b1b1-162">UTF-16 code units</span></span>

<span data-ttu-id="5b1b1-163">16位 Unicode 轉換格式 ([utf-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) 是 char acter 編碼系統，使用16位程式 *代碼單位* 來代表 Unicode 程式碼點。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-163">16-bit Unicode Transformation Format ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) is a character encoding system that uses 16-bit *code units* to represent Unicode code points.</span></span> <span data-ttu-id="5b1b1-164">.NET 使用 UTF-16 將中的文字編碼 `string` 。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-164">.NET uses UTF-16 to encode the text in a `string`.</span></span> <span data-ttu-id="5b1b1-165">`char`實例代表16位程式碼單位。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-165">A `char` instance represents a 16-bit code unit.</span></span>

<span data-ttu-id="5b1b1-166">單一16位程式碼單位可以代表基本多語系平面之16位範圍內的任何程式碼點。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-166">A single 16-bit code unit can represent any code point in the 16-bit range of the Basic Multilingual Plane.</span></span> <span data-ttu-id="5b1b1-167">但是針對補充範圍中的程式碼點，需要兩個 `char` 實例。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-167">But for a code point in the supplementary range, two `char` instances are needed.</span></span>

## <a name="surrogate-pairs"></a><span data-ttu-id="5b1b1-168">代理配對</span><span class="sxs-lookup"><span data-stu-id="5b1b1-168">Surrogate pairs</span></span>

<span data-ttu-id="5b1b1-169">將 2 16 位值轉譯成單一21位值是由稱為 *代理程式碼點*的特殊範圍所組成，從 `U+D800` 到 `U+DFFF` (decimal 55296 到 57343) （含）。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-169">The translation of two 16-bit values to a single 21-bit value is facilitated by a special range called the *surrogate code points*, from `U+D800` to `U+DFFF` (decimal 55,296 to 57,343), inclusive.</span></span>

<span data-ttu-id="5b1b1-170">下圖說明 BMP 與代理程式碼點之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-170">The following diagram illustrates the relationship between the BMP and the surrogate code points.</span></span>

:::image type="content" source="media/:::非 loc (char) ：：： acter-encoding-introduction/bmp-and-surrogate.svg" alt-text =" BMP 和代理程式碼點"：：：

<span data-ttu-id="5b1b1-172">當 *高代理* 程式碼點 (`U+D800..U+DBFF`) 後面緊接著 *低代理* 程式碼點 () 時 `U+DC00..U+DFFF` ，會使用下列公式將配對解釋為補充程式碼點：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-172">When a *high surrogate* code point (`U+D800..U+DBFF`) is immediately followed by a *low surrogate* code point (`U+DC00..U+DFFF`), the pair is interpreted as a supplementary code point by using the following formula:</span></span>

```
code point = 0x10000 +
  ((high surrogate code point - 0xD800) * 0x0400) +
  (low surrogate code point - 0xDC00)
```

<span data-ttu-id="5b1b1-173">以下是使用小數點標記法的相同公式：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-173">Here's the same formula using decimal notation:</span></span>

```
code point = 65,536 +
  ((high surrogate code point - 55,296) * 1,024) +
  (low surrogate code point - 56,320)
```

<span data-ttu-id="5b1b1-174">*高*代理程式碼點沒有比*低*代理程式碼點更高的數值。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-174">A *high* surrogate code point doesn't have a higher number value than a *low* surrogate code point.</span></span> <span data-ttu-id="5b1b1-175">高代理程式碼點稱為「高」，因為它是用來計算完整21位程式碼點範圍的高序位11位。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-175">The high surrogate code point is called "high" because it's used to calculate the higher-order 11 bits of the full 21-bit code point range.</span></span> <span data-ttu-id="5b1b1-176">低代理程式碼點可用來計算較低順序的10位。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-176">The low surrogate code point is used to calculate the lower-order 10 bits.</span></span>

<span data-ttu-id="5b1b1-177">例如，對應至代理配對的實際程式碼點，其 `0xD83C` `0xDF39`  計算方式如下：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-177">For example, the actual code point that corresponds to the surrogate pair `0xD83C` and `0xDF39`  is computed as follows:</span></span>

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

<span data-ttu-id="5b1b1-178">以下是使用小數點標記法的相同計算：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-178">Here's the same calculation using decimal notation:</span></span>

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

<span data-ttu-id="5b1b1-179">上述範例示範的 `"\ud83c\udf39"` 是稍早所述的程式 `U+1F339 ROSE ('🌹')` 代碼點 utf-16 編碼。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-179">The preceding example demonstrates that `"\ud83c\udf39"` is the UTF-16 encoding of the `U+1F339 ROSE ('🌹')` code point mentioned earlier.</span></span>

## <a name="unicode-scalar-values"></a><span data-ttu-id="5b1b1-180">Unicode 純量值</span><span class="sxs-lookup"><span data-stu-id="5b1b1-180">Unicode scalar values</span></span>

<span data-ttu-id="5b1b1-181">Unicode 純量 [值](https://www.unicode.org/glossary/#unicode_scalar_value) 一詞是指代理程式碼點以外的所有程式碼點。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-181">The term [Unicode scalar value](https://www.unicode.org/glossary/#unicode_scalar_value) refers to all code points other than the surrogate code points.</span></span> <span data-ttu-id="5b1b1-182">換句話說，純量值是指派 char acter 或可在未來指派 acter 的任何程式碼點 char 。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-182">In other words, a scalar value is any code point that is assigned a character or can be assigned a character in the future.</span></span> <span data-ttu-id="5b1b1-183">此處的「字元」指的是可指派給程式碼點的任何專案，其中包含控制文字或 acters 顯示方式的動作 char 。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-183">"Character" here refers to anything that can be assigned to a code point, which includes such things as actions that control how text or characters are displayed.</span></span>

<span data-ttu-id="5b1b1-184">下圖說明純量值的程式碼點。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-184">The following diagram illustrates the scalar value code points.</span></span>

:::image type="content" source="media/:::無 loc (char) ：：： acter-encoding-introduction/scalar-values.svg" alt-text =" 純量值"：：：

### <a name="the-no-locrune-type-as-a-scalar-value"></a><span data-ttu-id="5b1b1-186">以純量 Rune 值的類型</span><span class="sxs-lookup"><span data-stu-id="5b1b1-186">The Rune type as a scalar value</span></span>

<span data-ttu-id="5b1b1-187">從 .NET Core 3.0 開始，此 <xref:System.Text.Rune?displayProperty=fullName> 型別代表 Unicode 純量值。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-187">Beginning with .NET Core 3.0, the <xref:System.Text.Rune?displayProperty=fullName> type represents a Unicode scalar value.</span></span> <span data-ttu-id="5b1b1-188">**`Rune` 不適用於 .NET Core 2.x 或 .NET Framework 4.x。**</span><span class="sxs-lookup"><span data-stu-id="5b1b1-188">**`Rune` is not available in .NET Core 2.x or .NET Framework 4.x.**</span></span>

<span data-ttu-id="5b1b1-189">這些 `Rune` 函數會驗證產生的實例是否為有效的 Unicode 純量值，否則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-189">The `Rune` constructors validate that the resulting instance is a valid Unicode scalar value, otherwise they throw an exception.</span></span> <span data-ttu-id="5b1b1-190">下列範例會顯示成功具現化實例的程式碼， `Rune` 因為輸入代表有效的純量值：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-190">The following example shows code that successfully instantiates `Rune` instances because the input represents valid scalar values:</span></span>

<span data-ttu-id="5b1b1-191">：：： code language = "csharp" source = "程式碼片段/ char acter-編碼-簡介/csharp/具現化 Rune s.cs" id = "SnippetValid"：：：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-191">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetValid":::</span></span>

<span data-ttu-id="5b1b1-192">下列範例會擲回例外狀況，因為程式碼點是在代理範圍內，而不是代理組的一部分：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-192">The following example throws an exception because the code point is in the surrogate range and isn't part of a surrogate pair:</span></span>

<span data-ttu-id="5b1b1-193">：：： code language = "csharp" source = "程式碼片段/ char acter-編碼-簡介/csharp/具現化 Rune s.cs" id = "SnippetInvalidSurrogate"：：：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-193">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidSurrogate":::</span></span>

<span data-ttu-id="5b1b1-194">下列範例會擲回例外狀況，因為程式碼點超出補充範圍：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-194">The following example throws an exception because the code point is beyond the supplementary range:</span></span>

<span data-ttu-id="5b1b1-195">：：： code language = "csharp" source = "程式碼片段/ char acter-編碼-簡介/csharp/具現化 Rune s.cs" id = "SnippetInvalidHigh"：：：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-195">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidHigh":::</span></span>

### <a name="no-locrune-usage-example-changing-letter-case"></a><span data-ttu-id="5b1b1-196">Rune 使用範例：變更字母大小寫</span><span class="sxs-lookup"><span data-stu-id="5b1b1-196">Rune usage example: changing letter case</span></span>

<span data-ttu-id="5b1b1-197">使用的 API 會 `char` 假設它使用的程式碼點是純量值，如果 `char` 是來自代理組，則無法正確運作。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-197">An API that takes a `char` and assumes it is working with a code point that is a scalar value doesn't work correctly if the `char` is from a surrogate pair.</span></span> <span data-ttu-id="5b1b1-198">例如，請考慮下列在 <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> 中對每個進行呼叫的方法 char string ：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-198">For example, consider the following method that calls <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> on each char in a string:</span></span>

<span data-ttu-id="5b1b1-199">：：： code language = "csharp" source = "程式碼片段/ char acter-編碼-簡介/csharp/ConvertToUpper .cs" id = "SnippetBadExample"：：：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-199">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::</span></span>

<span data-ttu-id="5b1b1-200">如果 `input` string () 包含小寫的 `er` 編碼方式 `𐑉` ，則此程式碼不會將它轉換成大寫 (`𐐡`) 。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-200">If the `input` string contains the lowercase Deseret letter `er` (`𐑉`), this code won't convert it to uppercase (`𐐡`).</span></span> <span data-ttu-id="5b1b1-201">程式碼會 `char.ToUpperInvariant` 在每個代理程式碼點上個別呼叫， `U+D801` 以及 `U+DC49` 。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-201">The code calls `char.ToUpperInvariant` separately on each surrogate code point, `U+D801` and `U+DC49`.</span></span> <span data-ttu-id="5b1b1-202">但是 `U+D801` 本身並沒有足夠的資訊來將它識別為小寫字母，因此請 `char.ToUpperInvariant` 單獨保留。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-202">But `U+D801` doesn't have enough information by itself to identify it as a lowercase letter, so `char.ToUpperInvariant` leaves it alone.</span></span> <span data-ttu-id="5b1b1-203">而且會以 `U+DC49` 相同的方式處理。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-203">And it handles `U+DC49` the same way.</span></span> <span data-ttu-id="5b1b1-204">結果是中的小寫 ' 𐑉 ' `input` string 不會轉換成大寫的 ' 𐑉 '。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-204">The result is that lowercase '𐑉' in the `input` string doesn't get converted to uppercase '𐐡'.</span></span>

<span data-ttu-id="5b1b1-205">以下是將 a 正確轉換成大寫的兩個選項 string ：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-205">Here are two options for correctly converting a string to uppercase:</span></span>

* <span data-ttu-id="5b1b1-206"><xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType>在輸入上呼叫， string 而不是 `char` 逐一查看 `char` 。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-206">Call <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> on the input string rather than iterating `char`-by-`char`.</span></span> <span data-ttu-id="5b1b1-207">`string.ToUpperInvariant`方法可以存取每個代理組的兩個部分，讓它能夠正確處理所有的 Unicode 程式碼點。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-207">The `string.ToUpperInvariant` method has access to both parts of each surrogate pair, so it can handle all Unicode code points correctly.</span></span>
* <span data-ttu-id="5b1b1-208">將 Unicode 純量值逐一查看為 `Rune` 實例，而不是 `char` 實例，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-208">Iterate through the Unicode scalar values as `Rune` instances instead of `char` instances, as shown in the following example.</span></span> <span data-ttu-id="5b1b1-209">因為 `Rune` 實例是有效的 Unicode 純量值，所以可以傳遞給預期會在純量值上運作的 api。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-209">Since a `Rune` instance is a valid Unicode scalar value, it can be passed to APIs that expect to operate on a scalar value.</span></span> <span data-ttu-id="5b1b1-210">例如， <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> 如下列範例所示呼叫會提供正確的結果：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-210">For example, calling <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> as shown in the following example gives correct results:</span></span>

  <span data-ttu-id="5b1b1-211">：：： code language = "csharp" source = "程式碼片段/ char acter-編碼-簡介/csharp/ConvertToUpper .cs" id = "SnippetGoodExample"：：：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-211">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::</span></span>

### <a name="other-no-locrune-apis"></a><span data-ttu-id="5b1b1-212">其他 Rune api</span><span class="sxs-lookup"><span data-stu-id="5b1b1-212">Other Rune APIs</span></span>

<span data-ttu-id="5b1b1-213">此 `Rune` 類型會公開許多 api 的類比 `char` 。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-213">The `Rune` type exposes analogs of many of the `char` APIs.</span></span> <span data-ttu-id="5b1b1-214">例如，下列方法會在類型上鏡像靜態 Api `char` ：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-214">For example, the following methods mirror static APIs on the `char` type:</span></span>

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

<span data-ttu-id="5b1b1-215">若要從實例取得原始純量值 `Rune` ，請使用 <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-215">To get the raw scalar value from a `Rune` instance, use the <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="5b1b1-216">若要將 `Rune` 實例轉換回的序列 `char` ，請使用 <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> 或 <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-216">To convert a `Rune` instance back to a sequence of `char`s, use <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> or the <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="5b1b1-217">因為任何 Unicode 純量值都是由單一 `char` 或代理配對來表示，所以任何 `Rune` 實例最多可以用2個 `char` 實例來表示。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-217">Since any Unicode scalar value is representable by a single `char` or by a surrogate pair, any `Rune` instance can be represented by at most 2 `char` instances.</span></span> <span data-ttu-id="5b1b1-218">使用 <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> 以查看需要多少 `char` 實例來表示 `Rune` 實例。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-218">Use <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> to see how many `char` instances are required to represent a `Rune` instance.</span></span>

<span data-ttu-id="5b1b1-219">如需 .NET 類型的詳細資訊 `Rune` ，請參閱[ `Rune` API 參考](xref:System.Text.Rune)。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-219">For more information about the .NET `Rune` type, see the [`Rune` API reference](xref:System.Text.Rune).</span></span>

## <a name="grapheme-clusters"></a><span data-ttu-id="5b1b1-220">語素簇叢集</span><span class="sxs-lookup"><span data-stu-id="5b1b1-220">Grapheme clusters</span></span>

<span data-ttu-id="5b1b1-221">charActer 可能會因為多個程式碼點組合而產生的結果，因此更具描述性的詞彙通常會用來取代 " char acter"[語素簇](https://www.unicode.org/glossary/#grapheme_cluster)叢集。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-221">What looks like one character might result from a combination of multiple code points, so a more descriptive term that is often used in place of "character" is [grapheme cluster](https://www.unicode.org/glossary/#grapheme_cluster).</span></span> <span data-ttu-id="5b1b1-222">.NET 中的對等詞彙是 [text 元素](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A)。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-222">The equivalent term in .NET is [text element](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span></span>

<span data-ttu-id="5b1b1-223">請考慮「a」、「×」、「×」和「」 `string` 實例 `👩🏽‍🚒` 。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-223">Consider the `string` instances "a", "á", "á", and "`👩🏽‍🚒`".</span></span> <span data-ttu-id="5b1b1-224">如果您的作業系統依 Unicode 標準所指定來處理它們，則每個 `string` 實例都會顯示為單一文字元素或語素簇叢集。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-224">If your operating system handles them as specified by the Unicode standard, each of these `string` instances appears as a single text element or grapheme cluster.</span></span> <span data-ttu-id="5b1b1-225">但最後兩個會以一個以上的純量值程式碼點來表示。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-225">But the last two are represented by more than one scalar value code point.</span></span>

* <span data-ttu-id="5b1b1-226">string"A" 是以一個純量值表示，並包含一個 `char` 實例。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-226">The string "a" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+0061 LATIN SMALL LETTER A`

* <span data-ttu-id="5b1b1-227">string"×" 是以一個純量值表示，並包含一個 `char` 實例。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-227">The string "á" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+00E1 LATIN SMALL LETTER A WITH ACUTE`

* <span data-ttu-id="5b1b1-228">「 string ×」看起來與「×」相同，但以兩個純量值表示，並包含兩個 `char` 實例。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-228">The string "á" looks the same as "á" but is represented by two scalar values and contains two `char` instances.</span></span>

  * `U+0061 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* <span data-ttu-id="5b1b1-229">最後， string " `👩🏽‍🚒` " 是由四個純量值所表示，並包含七個 `char` 實例。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-229">Finally, the string "`👩🏽‍🚒`" is represented by four scalar values and contains seven `char` instances.</span></span>

  * <span data-ttu-id="5b1b1-230">`U+1F469 WOMAN` (補充範圍，需要代理配對) </span><span class="sxs-lookup"><span data-stu-id="5b1b1-230">`U+1F469 WOMAN` (supplementary range, requires a surrogate pair)</span></span>
  * <span data-ttu-id="5b1b1-231">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (補充範圍，需要代理配對) </span><span class="sxs-lookup"><span data-stu-id="5b1b1-231">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (supplementary range, requires a surrogate pair)</span></span>
  * `U+200D ZERO WIDTH JOINER`
  * <span data-ttu-id="5b1b1-232">`U+1F692 FIRE ENGINE` (補充範圍，需要代理配對) </span><span class="sxs-lookup"><span data-stu-id="5b1b1-232">`U+1F692 FIRE ENGINE` (supplementary range, requires a surrogate pair)</span></span>

<span data-ttu-id="5b1b1-233">在上述一些範例中（例如合併式輔色修飾詞或面板音調修飾詞），程式碼點不會顯示為螢幕上的獨立元素。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-233">In some of the preceding examples - such as the combining accent modifier or the skin tone modifier - the code point does not display as a standalone element on the screen.</span></span> <span data-ttu-id="5b1b1-234">相反地，它會用來修改它之前的文字元素的外觀。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-234">Rather, it serves to modify the appearance of a text element that came before it.</span></span> <span data-ttu-id="5b1b1-235">這些範例顯示，它可能會採用多個純量值，讓我們將其視為單一「 char acter」或「語素簇叢集」。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-235">These examples show that it might take multiple scalar values to make up what we think of as a single "character," or "grapheme cluster."</span></span>

<span data-ttu-id="5b1b1-236">若要列舉的語素簇叢集 `string` ，請使用 <xref:System.Globalization.StringInfo> 類別，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-236">To enumerate the grapheme clusters of a `string`, use the <xref:System.Globalization.StringInfo> class as shown in the following example.</span></span> <span data-ttu-id="5b1b1-237">如果您熟悉 Swift，.NET 型別在 `StringInfo` 概念上類似于 [swift 的 `character` 型](https://developer.apple.com/documentation/swift/character)別。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-237">If you're familiar with Swift, the .NET `StringInfo` type is conceptually similar to [Swift's `character` type](https://developer.apple.com/documentation/swift/character).</span></span>

### <a name="example-count-no-locchar-no-locrune-and-text-element-instances"></a><span data-ttu-id="5b1b1-238">範例： count char 、 Rune 和 text 元素實例</span><span class="sxs-lookup"><span data-stu-id="5b1b1-238">Example: count char, Rune, and text element instances</span></span>

<span data-ttu-id="5b1b1-239">在 .NET Api 中，語素簇叢集稱為「 *文字」元素*。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-239">In .NET APIs, a grapheme cluster is called a *text element*.</span></span> <span data-ttu-id="5b1b1-240">下列方法示範 `char` 、 `Rune` 和中的 text 元素實例之間的差異 `string` ：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-240">The following method demonstrates the differences between `char`, `Rune`, and text element instances in a `string`:</span></span>

<span data-ttu-id="5b1b1-241">：：： code language = "csharp" source = "程式碼片段/ char acter-編碼-簡介/csharp/CountTextElements .cs" id = "SnippetCountMethod"：：：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-241">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::</span></span>

<span data-ttu-id="5b1b1-242">：：： code language = "csharp" source = "程式碼片段/ char acter-編碼-簡介/csharp/CountTextElements .cs" id = "SnippetCallCountMethod"：：：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-242">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::</span></span>

<span data-ttu-id="5b1b1-243">如果您在 .NET Framework 或 .NET Core 3.1 或更早版本中執行此程式碼，則會顯示表情的文字元素計數 `4` 。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-243">If you run this code in .NET Framework or .NET Core 3.1 or earlier, the text element count for the emoji shows `4`.</span></span> <span data-ttu-id="5b1b1-244">這是因為 `StringInfo` .net 5 中已修正的類別中有錯誤。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-244">That is due to a bug in the `StringInfo` class that is fixed in .NET 5.</span></span>

### <a name="example-splitting-no-locstring-instances"></a><span data-ttu-id="5b1b1-245">範例：分割 string 實例</span><span class="sxs-lookup"><span data-stu-id="5b1b1-245">Example: splitting string instances</span></span>

<span data-ttu-id="5b1b1-246">分割 `string` 實例時，請避免分割代理組和語素簇叢集。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-246">When splitting `string` instances, avoid splitting surrogate pairs and grapheme clusters.</span></span> <span data-ttu-id="5b1b1-247">請考慮下列不正確的程式碼範例，這會在中插入每10個 acters 的分行符號 char string ：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-247">Consider the following example of incorrect code, which intends to insert line breaks every 10 characters in a string:</span></span>

<span data-ttu-id="5b1b1-248">：：： code language = "csharp" source = "程式碼片段/ char acter-編碼-簡介/csharp/InsertNewlines .cs" id = "SnippetBadExample"：：：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-248">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::</span></span>

<span data-ttu-id="5b1b1-249">因為此程式碼會列舉 `char` 實例，所以跨10界限的代理組 `char` 將會被分割，並在其間插入一個新行。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-249">Because this code enumerates `char` instances, a surrogate pair that happens to straddle a 10-`char` boundary will be split and a newline injected between them.</span></span> <span data-ttu-id="5b1b1-250">這項插入會造成資料損毀，因為代理程式碼點只對成對有意義。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-250">This insertion introduces data corruption, because surrogate code points are meaningful only as pairs.</span></span>

<span data-ttu-id="5b1b1-251">如果您將 `Rune` 實例列舉 (純量值) 而不是實例，則不會刪除資料損毀的可能性 `char` 。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-251">The potential for data corruption isn't eliminated if you enumerate `Rune` instances (scalar values) instead of `char` instances.</span></span> <span data-ttu-id="5b1b1-252">一組 `Rune` 實例可能構成跨越10界限的語素簇叢集 `char` 。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-252">A set of `Rune` instances might make up a grapheme cluster that straddles a 10-`char` boundary.</span></span> <span data-ttu-id="5b1b1-253">如果語素簇叢集集已分割，則無法正確解讀。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-253">If the grapheme cluster set is split up, it can't be interpreted correctly.</span></span>

<span data-ttu-id="5b1b1-254">更好的方法是藉 string 由計算語素簇叢集或文字元素來中斷，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-254">A better approach is to break the string by counting grapheme clusters, or text elements, as in the following example:</span></span>

<span data-ttu-id="5b1b1-255">：：： code language = "csharp" source = "程式碼片段/ char acter-編碼-簡介/csharp/InsertNewlines .cs" id = "SnippetGoodExample"：：：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-255">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::</span></span>

<span data-ttu-id="5b1b1-256">不過如先前所述，在 .net 5 以外的 .NET 的實， `StringInfo` 類別可能會不正確地處理某些語素簇叢集。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-256">As noted earlier, however, in implementations of .NET other than .NET 5, the `StringInfo` class might handle some grapheme clusters incorrectly.</span></span>

## <a name="utf-8-and-utf-32"></a><span data-ttu-id="5b1b1-257">UTF-8 和 UTF-32</span><span class="sxs-lookup"><span data-stu-id="5b1b1-257">UTF-8 and UTF-32</span></span>

<span data-ttu-id="5b1b1-258">上述幾節著重于 UTF-16，因為 .NET 會使用它來編碼 `string` 實例。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-258">The preceding sections focused on UTF-16 because that's what .NET uses to encode `string` instances.</span></span> <span data-ttu-id="5b1b1-259">另外還有 Unicode [utf-8](https://www.unicode.org/faq/utf_bom.html#UTF8) 和 [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32)的編碼系統。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-259">There are other encoding systems for Unicode - [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) and [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32).</span></span> <span data-ttu-id="5b1b1-260">這些編碼方式分別使用8位程式碼單位和32位程式碼單位。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-260">These encodings use 8-bit code units and 32-bit code units, respectively.</span></span>

<span data-ttu-id="5b1b1-261">如同 UTF-16，UTF-8 需要多個程式碼單位來代表一些 Unicode 純量值。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-261">Like UTF-16, UTF-8 requires multiple code units to represent some Unicode scalar values.</span></span> <span data-ttu-id="5b1b1-262">32 UTF-7 可代表單一32位程式碼單位中的任何純量值。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-262">UTF-32 can represent any scalar value in a single 32-bit code unit.</span></span>

<span data-ttu-id="5b1b1-263">以下是一些範例，顯示相同的 Unicode 程式碼點在這三個 Unicode 編碼系統中的呈現方式：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-263">Here are some examples showing how the same Unicode code point is represented in each of these three Unicode encoding systems:</span></span>

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

<span data-ttu-id="5b1b1-264">如先前所述，來自 [代理](#surrogate-pairs) 組的單一 utf-16 程式碼單位本身並無意義。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-264">As noted earlier, a single UTF-16 code unit from a [surrogate pair](#surrogate-pairs) is meaningless by itself.</span></span> <span data-ttu-id="5b1b1-265">同樣地，如果單一 UTF-8 程式碼單位是以兩個、三個或四個用來計算純量值的順序，它本身就沒有意義。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-265">In the same way, a single UTF-8 code unit is meaningless by itself if it's in a sequence of two, three, or four used to calculate a scalar value.</span></span>

### <a name="endianness"></a><span data-ttu-id="5b1b1-266">位元組序</span><span class="sxs-lookup"><span data-stu-id="5b1b1-266">Endianness</span></span>

<span data-ttu-id="5b1b1-267">在 .NET 中，的 UTF-16 程式碼單位會以 string 一系列的16位整數 (實例) 的形式儲存在連續的記憶體中 `char` 。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-267">In .NET, the UTF-16 code units of a string are stored in contiguous memory as a sequence of 16-bit integers (`char` instances).</span></span> <span data-ttu-id="5b1b1-268">個別程式碼單位的位會根據目前架構的 [位元組](https://en.wikipedia.org/wiki/Endianness) 順序配置。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-268">The bits of individual code units are laid out according to the [endianness](https://en.wikipedia.org/wiki/Endianness) of the current architecture.</span></span>

<span data-ttu-id="5b1b1-269">在位元組由小到大的架構上，由 string utf-16 程式碼點組成的會 `[ D801 DCCC ]` 在記憶體中配置為位元組 `[ 0x01, 0xD8, 0xCC, 0xDC ]` 。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-269">On a little-endian architecture, the string consisting of the UTF-16 code points `[ D801 DCCC ]` would be laid out in memory as the bytes `[ 0x01, 0xD8, 0xCC, 0xDC ]`.</span></span> <span data-ttu-id="5b1b1-270">在以大到小的架構上，相同的會 string 在記憶體中配置為位元組 `[ 0xD8, 0x01, 0xDC, 0xCC ]` 。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-270">On a big-endian architecture that same string would be laid out in memory as the bytes `[ 0xD8, 0x01, 0xDC, 0xCC ]`.</span></span>

<span data-ttu-id="5b1b1-271">彼此通訊的電腦系統必須同意網路上的資料標記法。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-271">Computer systems that communicate with each other must agree on the representation of data crossing the wire.</span></span> <span data-ttu-id="5b1b1-272">大部分的網路通訊協定都是在傳輸文字時使用 UTF-8 作為標準，以避免因為以位元組由小到大的電腦與以位元組由小到大的電腦通訊所產生的問題。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-272">Most network protocols use UTF-8 as a standard when transmitting text, partly to avoid issues that might result from a big-endian machine communicating with a little-endian machine.</span></span> <span data-ttu-id="5b1b1-273">無論是否為位元組順序，由 string utf-8 程式碼點組成的 `[ F0 90 93 8C ]` 會一律以位元組表示 `[ 0xF0, 0x90, 0x93, 0x8C ]` 。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-273">The string consisting of the UTF-8 code points `[ F0 90 93 8C ]` will always be represented as the bytes `[ 0xF0, 0x90, 0x93, 0x8C ]` regardless of endianness.</span></span>

<span data-ttu-id="5b1b1-274">若要使用 UTF-8 來傳送文字，.NET 應用程式通常會使用類似下列範例的程式碼：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-274">To use UTF-8 for transmitting text, .NET applications often use code like the following example:</span></span>

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

<span data-ttu-id="5b1b1-275">在上述範例中， [GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) 方法會將 utf-16 解碼 `string` 回一連串的 Unicode 純量值，然後將這些純量值重新編碼為 utf-8，然後將產生的序列放入 `byte` 陣列中。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-275">In the preceding example, the method [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) decodes the UTF-16 `string` back into a series of Unicode scalar values, then it re-encodes those scalar values into UTF-8 and places the resulting sequence into a `byte` array.</span></span> <span data-ttu-id="5b1b1-276">方法 [編碼 GetString](xref:System.Text.UTF8Encoding.GetString%2A) 會執行相反的轉換，將 utf-8 `byte` 陣列轉換為 utf-16 `string` 。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-276">The method [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) performs the opposite transformation, converting a UTF-8 `byte` array to a UTF-16 `string`.</span></span>

> [!WARNING]
> <span data-ttu-id="5b1b1-277">由於 UTF-8 在網際網路上很普遍，從網路讀取未經處理的位元組，並將資料視為 UTF-8，可能會很吸引人。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-277">Since UTF-8 is commonplace on the internet, it may be tempting to read raw bytes from the wire and to treat the data as if it were UTF-8.</span></span> <span data-ttu-id="5b1b1-278">不過，您應該驗證它的格式是否正確。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-278">However, you should validate that it is indeed well-formed.</span></span> <span data-ttu-id="5b1b1-279">惡意用戶端可能會將格式不正確的 UTF-8 提交至您的服務。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-279">A malicious client might submit ill-formed UTF-8 to your service.</span></span> <span data-ttu-id="5b1b1-280">如果您以格式正確的方式操作該資料，則可能會導致您的應用程式發生錯誤或安全性漏洞。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-280">If you operate on that data as if it were well-formed, it could cause errors or security holes in your application.</span></span> <span data-ttu-id="5b1b1-281">若要驗證 UTF-8 資料，您可以使用類似的方法 `Encoding.UTF8.GetString` ，這會在將傳入資料轉換為時執行驗證 `string` 。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-281">To validate UTF-8 data, you can use a method like `Encoding.UTF8.GetString`, which will perform validation while converting the incoming data to a `string`.</span></span>

### <a name="well-formed-encoding"></a><span data-ttu-id="5b1b1-282">格式正確的編碼</span><span class="sxs-lookup"><span data-stu-id="5b1b1-282">Well-formed encoding</span></span>

<span data-ttu-id="5b1b1-283">格式正確的 Unicode 編碼是 string 可明確解碼，且不會發生錯誤的一連串 unicode 純量值的程式碼單位。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-283">A well-formed Unicode encoding is a string of code units that can be decoded unambiguously and without error into a sequence of Unicode scalar values.</span></span> <span data-ttu-id="5b1b1-284">格式正確的資料可以在 UTF-8、UTF-16 和 UTF-32 之間自由地來回轉碼。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-284">Well-formed data can be transcoded freely back and forth between UTF-8, UTF-16, and UTF-32.</span></span>

<span data-ttu-id="5b1b1-285">編碼順序是否格式正確或不與電腦架構的位元組格式相關的問題。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-285">The question of whether an encoding sequence is well-formed or not is unrelated to the endianness of a machine's architecture.</span></span> <span data-ttu-id="5b1b1-286">格式不正確的 UTF-8 順序在位元組由大到小的電腦上的格式不正確。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-286">An ill-formed UTF-8 sequence is ill-formed in the same way on both big-endian and little-endian machines.</span></span>

<span data-ttu-id="5b1b1-287">以下是格式錯誤的編碼範例：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-287">Here are some examples of ill-formed encodings:</span></span>

* <span data-ttu-id="5b1b1-288">在 UTF-8 中，順序的 `[ 6C C2 61 ]` 格式不正確，因為 `C2` 後面不能有 `61` 。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-288">In UTF-8, the sequence `[ 6C C2 61 ]` is ill-formed because `C2` cannot be followed by `61`.</span></span>

* <span data-ttu-id="5b1b1-289">在 UTF-16 中，順序 (， `[ DC00 DD00 ]` 或在 c # 中， string `"\udc00\udd00"`) 格式不正確，因為低代理 `DC00` 不能後面接著另一個低代理 `DD00` 。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-289">In UTF-16, the sequence `[ DC00 DD00 ]` (or, in C#, the string `"\udc00\udd00"`) is ill-formed because the low surrogate `DC00` cannot be followed by another low surrogate `DD00`.</span></span>

* <span data-ttu-id="5b1b1-290">在 32 UTF-8 中，順序的 `[ 0011ABCD ]` 格式不正確，因為超出 `0011ABCD` Unicode 純量值的範圍。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-290">In UTF-32, the sequence `[ 0011ABCD ]` is ill-formed because `0011ABCD` is outside the range of Unicode scalar values.</span></span>

<span data-ttu-id="5b1b1-291">在 .NET 中， `string` 實例幾乎一律會包含格式正確的 utf-16 資料，但不保證如此。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-291">In .NET, `string` instances almost always contain well-formed UTF-16 data, but that isn't guaranteed.</span></span> <span data-ttu-id="5b1b1-292">下列範例顯示在實例中建立格式不正確之 UTF-16 資料的有效 c # 程式碼 `string` 。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-292">The following examples show valid C# code that creates ill-formed UTF-16 data in `string` instances.</span></span>

* <span data-ttu-id="5b1b1-293">格式不正確的常值：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-293">An ill-formed literal:</span></span>

  ```csharp
  const string s = "\ud800";
  ```

* <span data-ttu-id="5b1b1-294">string分割代理配對的 sub：</span><span class="sxs-lookup"><span data-stu-id="5b1b1-294">A substring that splits up a surrogate pair:</span></span>

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

<span data-ttu-id="5b1b1-295">這類 Api [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) 不會傳回格式不正確的 `string` 實例。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-295">APIs like [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) never return ill-formed `string` instances.</span></span> <span data-ttu-id="5b1b1-296">`Encoding.GetString` 和 `Encoding.GetBytes` 方法會偵測輸入中格式不正確的序列，並在 char 產生輸出時執行 acter 替代。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-296">`Encoding.GetString` and `Encoding.GetBytes` methods detect ill-formed sequences in the input and perform character substitution when generating the output.</span></span> <span data-ttu-id="5b1b1-297">例如，如果在 [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) (輸入中看到非 ASCII 位元組的範圍 U + 0000. u + 007F) ，則會在傳回的實例中插入 '？ ' `string` 。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-297">For example, if [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) sees a non-ASCII byte in the input (outside the range U+0000..U+007F), it inserts a '?' into the returned `string` instance.</span></span> <span data-ttu-id="5b1b1-298">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A)`U+FFFD REPLACEMENT CHARACTER ('�')`在傳回的實例中，取代格式不正確的 utf-8 序列 `string` 。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-298">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A) replaces ill-formed UTF-8 sequences with `U+FFFD REPLACEMENT CHARACTER ('�')` in the returned `string` instance.</span></span> <span data-ttu-id="5b1b1-299">如需詳細資訊，請參閱 [Unicode 標準](https://www.unicode.org/versions/latest/)，章節5.22 和3.9。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-299">For more information, see [the Unicode Standard](https://www.unicode.org/versions/latest/), Sections 5.22 and 3.9.</span></span>

<span data-ttu-id="5b1b1-300">您 `Encoding` 也可以將內建類別設定為擲回例外狀況，而不是 char 在發現不正確的序列時執行 acter 替代。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-300">The built-in `Encoding` classes can also be configured to throw an exception rather than perform character substitution when ill-formed sequences are seen.</span></span> <span data-ttu-id="5b1b1-301">這種方法通常用於 char 可能無法接受 acter 替代的安全性敏感應用程式。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-301">This approach is often used in security-sensitive applications where character substitution might not be acceptable.</span></span>

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

<span data-ttu-id="5b1b1-302">如需如何使用內建類別的詳細資訊 `Encoding` ，請參閱 [如何 char 在 .net 中使用 acter 編碼類別](character-encoding.md)。</span><span class="sxs-lookup"><span data-stu-id="5b1b1-302">For information about how to use the built-in `Encoding` classes, see [How to use character encoding classes in .NET](character-encoding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5b1b1-303">請參閱</span><span class="sxs-lookup"><span data-stu-id="5b1b1-303">See also</span></span>

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [<span data-ttu-id="5b1b1-304">全球化和當地語系化</span><span class="sxs-lookup"><span data-stu-id="5b1b1-304">Globalization and Localization</span></span>](../globalization-localization/index.md)
