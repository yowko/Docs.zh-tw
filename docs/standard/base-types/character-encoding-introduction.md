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
# <a name="character-encoding-in-net"></a><span data-ttu-id="99b74-103">.NET 中的字元編碼</span><span class="sxs-lookup"><span data-stu-id="99b74-103">Character encoding in .NET</span></span>

<span data-ttu-id="99b74-104">本文介紹了 .NET 使用的字元編碼系統。</span><span class="sxs-lookup"><span data-stu-id="99b74-104">This article provides an introduction to character encoding systems that are used by .NET.</span></span> <span data-ttu-id="99b74-105">本文介紹了<xref:System.String>、<xref:System.Char><xref:System.Text.Rune>和<xref:System.Globalization.StringInfo>類型如何與 Unicode、UTF-16 和 UTF-8 一起工作。</span><span class="sxs-lookup"><span data-stu-id="99b74-105">The article explains how the <xref:System.String>, <xref:System.Char>, <xref:System.Text.Rune>, and <xref:System.Globalization.StringInfo> types work with Unicode, UTF-16, and UTF-8.</span></span>

<span data-ttu-id="99b74-106">術語*字元*在這裡使用，在*讀者認為單個顯示元素*的一般意義上。</span><span class="sxs-lookup"><span data-stu-id="99b74-106">The term *character* is used here in the general sense of *what a reader perceives as a single display element*.</span></span> <span data-ttu-id="99b74-107">常見示例是字母"a"、符號"\*"和表情符號""。🐂</span><span class="sxs-lookup"><span data-stu-id="99b74-107">Common examples are the letter "a", the symbol "@", and the emoji "🐂".</span></span> <span data-ttu-id="99b74-108">有時，一個字元實際上由多個獨立的顯示元素組成，如[石墨星系團](#grapheme-clusters)上的部分所解釋的那樣。</span><span class="sxs-lookup"><span data-stu-id="99b74-108">Sometimes what looks like one character is actually composed of multiple independent display elements, as the section on [grapheme clusters](#grapheme-clusters) explains.</span></span>

## <a name="the-string-and-char-types"></a><span data-ttu-id="99b74-109">字串和字元類型</span><span class="sxs-lookup"><span data-stu-id="99b74-109">The string and char types</span></span>

<span data-ttu-id="99b74-110">[字串](xref:System.String)類的實例表示某些文本。</span><span class="sxs-lookup"><span data-stu-id="99b74-110">An instance of the [string](xref:System.String) class represents some text.</span></span> <span data-ttu-id="99b74-111">邏輯`string`上，A 是 16 位值的序列，每個值都是[字元](xref:System.Char)結構的實例。</span><span class="sxs-lookup"><span data-stu-id="99b74-111">A `string` is logically a sequence of 16-bit values, each of which is an instance of the [char](xref:System.Char) struct.</span></span> <span data-ttu-id="99b74-112">[字串。Length](xref:System.String.Length)屬性返回`string`實例中的`char`實例數。</span><span class="sxs-lookup"><span data-stu-id="99b74-112">The [string.Length](xref:System.String.Length) property returns the number of `char` instances in the `string` instance.</span></span>

<span data-ttu-id="99b74-113">以下示例函數列印出`char``string`十六進位標記法中的值：</span><span class="sxs-lookup"><span data-stu-id="99b74-113">The following sample function prints out the values in hexadecimal notation of all the `char` instances in a `string`:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::

<span data-ttu-id="99b74-114">將字串"Hello"傳遞給此函數，您將獲得以下輸出：</span><span class="sxs-lookup"><span data-stu-id="99b74-114">Pass the string "Hello" to this function, and you get the following output:</span></span>

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

<span data-ttu-id="99b74-115">每個字元由單個`char`值表示。</span><span class="sxs-lookup"><span data-stu-id="99b74-115">Each character is represented by a single `char` value.</span></span> <span data-ttu-id="99b74-116">這種模式在世界上大多數語言中都適用。</span><span class="sxs-lookup"><span data-stu-id="99b74-116">That pattern holds true for most of the world's languages.</span></span> <span data-ttu-id="99b74-117">例如，下面是兩個漢字的輸出，聽起來像*n= ho*和"表示*你好*"</span><span class="sxs-lookup"><span data-stu-id="99b74-117">For example, here's the output for two Chinese characters that sound like *nǐ hǎo* and mean *Hello*:</span></span>

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

<span data-ttu-id="99b74-118">但是，對於某些語言和某些符號和表情符號，需要兩`char`個實例來表示一個字元。</span><span class="sxs-lookup"><span data-stu-id="99b74-118">However, for some languages and for some symbols and emoji, it takes two `char` instances to represent a single character.</span></span> <span data-ttu-id="99b74-119">例如，比較單詞中的字元和`char`實例，在奧薩奇語中表示*Osage：*</span><span class="sxs-lookup"><span data-stu-id="99b74-119">For example, compare the characters and `char` instances in the word that means *Osage* in the Osage language:</span></span>

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

<span data-ttu-id="99b74-120">在前面的示例中，空格以外的每個字元都由兩個`char`實例表示。</span><span class="sxs-lookup"><span data-stu-id="99b74-120">In the preceding example, each character except the space is represented by two `char` instances.</span></span>

<span data-ttu-id="99b74-121">單個 Unicode 表情符號也由兩`char`個 s 表示，如下例所示，顯示牛表情符號：</span><span class="sxs-lookup"><span data-stu-id="99b74-121">A single Unicode emoji is also represented by two `char`s, as seen in the following example showing an ox emoji:</span></span>

```
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

<span data-ttu-id="99b74-122">這些示例顯示 ， 指示`string.Length`實例數`char`的值不一定指示顯示的字元數。</span><span class="sxs-lookup"><span data-stu-id="99b74-122">These examples show that the value of `string.Length`, which indicates the number of `char` instances, doesn't necessarily indicate the number of displayed characters.</span></span> <span data-ttu-id="99b74-123">單個`char`實例本身不一定表示字元。</span><span class="sxs-lookup"><span data-stu-id="99b74-123">A single `char` instance by itself doesn't necessarily represent a character.</span></span>

<span data-ttu-id="99b74-124">映射到`char`單個字元的對稱為*代理項對*。</span><span class="sxs-lookup"><span data-stu-id="99b74-124">The `char` pairs that map to a single character are called *surrogate pairs*.</span></span> <span data-ttu-id="99b74-125">要瞭解它們的工作原理，您需要瞭解 Unicode 和 UTF-16 編碼。</span><span class="sxs-lookup"><span data-stu-id="99b74-125">To understand how they work, you need to understand Unicode and UTF-16 encoding.</span></span>

## <a name="unicode-code-points"></a><span data-ttu-id="99b74-126">Unicode 字碼指標</span><span class="sxs-lookup"><span data-stu-id="99b74-126">Unicode code points</span></span>

<span data-ttu-id="99b74-127">Unicode 是一種國際編碼標準，用於各種平臺以及各種語言和腳本。</span><span class="sxs-lookup"><span data-stu-id="99b74-127">Unicode is an international encoding standard for use on various platforms and with various languages and scripts.</span></span>

<span data-ttu-id="99b74-128">Unicode 標準定義了超過 110 萬[個代碼點](https://www.unicode.org/glossary/#code_point)。</span><span class="sxs-lookup"><span data-stu-id="99b74-128">The Unicode Standard defines over 1.1 million [code points](https://www.unicode.org/glossary/#code_point).</span></span> <span data-ttu-id="99b74-129">代碼點是一個整數值，範圍從 0 到`U+10FFFF`（十進位 1，114，111）。</span><span class="sxs-lookup"><span data-stu-id="99b74-129">A code point is an integer value that can range from 0 to `U+10FFFF` (decimal 1,114,111).</span></span> <span data-ttu-id="99b74-130">某些代碼點分配給字母、符號或表情符號。</span><span class="sxs-lookup"><span data-stu-id="99b74-130">Some code points are assigned to letters, symbols, or emoji.</span></span> <span data-ttu-id="99b74-131">其他操作被分配給控制文本或字元的顯示方式的操作，例如前進到新行。</span><span class="sxs-lookup"><span data-stu-id="99b74-131">Others are assigned to actions that control how text or characters are displayed, such as advance to a new line.</span></span> <span data-ttu-id="99b74-132">許多代碼點尚未分配。</span><span class="sxs-lookup"><span data-stu-id="99b74-132">Many code points are not yet assigned.</span></span>

<span data-ttu-id="99b74-133">下面是代碼點分配的一些示例，其中連結指向 Unicode 圖表，其中顯示代碼圖表：</span><span class="sxs-lookup"><span data-stu-id="99b74-133">Here are some examples of code point assignments, with links to Unicode charts in which they appear:</span></span>

|<span data-ttu-id="99b74-134">Decimal</span><span class="sxs-lookup"><span data-stu-id="99b74-134">Decimal</span></span>|<span data-ttu-id="99b74-135">Hex</span><span class="sxs-lookup"><span data-stu-id="99b74-135">Hex</span></span>       |<span data-ttu-id="99b74-136">範例</span><span class="sxs-lookup"><span data-stu-id="99b74-136">Example</span></span>|<span data-ttu-id="99b74-137">描述</span><span class="sxs-lookup"><span data-stu-id="99b74-137">Description</span></span>|
|------:|----------|-------|-----------|
|<span data-ttu-id="99b74-138">10</span><span class="sxs-lookup"><span data-stu-id="99b74-138">10</span></span>     | `U+000A` |<span data-ttu-id="99b74-139">N/A</span><span class="sxs-lookup"><span data-stu-id="99b74-139">N/A</span></span>| [<span data-ttu-id="99b74-140">換行</span><span class="sxs-lookup"><span data-stu-id="99b74-140">LINE FEED</span></span>](https://www.unicode.org/charts/PDF/U0000.pdf) |
|<span data-ttu-id="99b74-141">65</span><span class="sxs-lookup"><span data-stu-id="99b74-141">65</span></span>     | `U+0061` | <span data-ttu-id="99b74-142">a</span><span class="sxs-lookup"><span data-stu-id="99b74-142">a</span></span> | [<span data-ttu-id="99b74-143">拉丁小字母 A</span><span class="sxs-lookup"><span data-stu-id="99b74-143">LATIN SMALL LETTER A</span></span>](https://www.unicode.org/charts/PDF/U0000.pdf) |
|<span data-ttu-id="99b74-144">562</span><span class="sxs-lookup"><span data-stu-id="99b74-144">562</span></span>    | `U+0232` | <span data-ttu-id="99b74-145">·</span><span class="sxs-lookup"><span data-stu-id="99b74-145">Ȳ</span></span> | [<span data-ttu-id="99b74-146">拉丁資本字母 Y 與 MACRON</span><span class="sxs-lookup"><span data-stu-id="99b74-146">LATIN CAPITAL LETTER Y WITH MACRON</span></span>](https://www.unicode.org/charts/PDF/U0180.pdf) |
|<span data-ttu-id="99b74-147">68,675</span><span class="sxs-lookup"><span data-stu-id="99b74-147">68,675</span></span> | `U+10C43`| <span data-ttu-id="99b74-148">𐱃</span><span class="sxs-lookup"><span data-stu-id="99b74-148">𐱃</span></span> | [<span data-ttu-id="99b74-149">舊突厥字母ORKHON在</span><span class="sxs-lookup"><span data-stu-id="99b74-149">OLD TURKIC LETTER ORKHON AT</span></span>](https://www.unicode.org/charts/PDF/U10C00.pdf) |
|<span data-ttu-id="99b74-150">127,801</span><span class="sxs-lookup"><span data-stu-id="99b74-150">127,801</span></span>| `U+1F339`| <span data-ttu-id="99b74-151">🌹</span><span class="sxs-lookup"><span data-stu-id="99b74-151">🌹</span></span> | [<span data-ttu-id="99b74-152">ROSE 表情符號</span><span class="sxs-lookup"><span data-stu-id="99b74-152">ROSE emoji</span></span>](https://www.unicode.org/charts/PDF/U1F300.pdf) |

<span data-ttu-id="99b74-153">代碼點通常使用語法`U+xxxx`引用 ，其中`xxxx`六進制編碼的整數值。</span><span class="sxs-lookup"><span data-stu-id="99b74-153">Code points are customarily referred to by using the syntax `U+xxxx`, where `xxxx` is the hex-encoded integer value.</span></span>

<span data-ttu-id="99b74-154">在代碼點的完整範圍內有兩個子範圍：</span><span class="sxs-lookup"><span data-stu-id="99b74-154">Within the full range of code points there are two subranges:</span></span>

* <span data-ttu-id="99b74-155">範圍內**的基本多語言平面 （BMP）。** `U+0000..U+FFFF`</span><span class="sxs-lookup"><span data-stu-id="99b74-155">The **Basic Multilingual Plane (BMP)** in the range `U+0000..U+FFFF`.</span></span> <span data-ttu-id="99b74-156">此 16 位範圍提供 65，536 個代碼點，足以覆蓋世界上大多數書寫系統。</span><span class="sxs-lookup"><span data-stu-id="99b74-156">This 16-bit range provides 65,536 code points, enough to cover the majority of the world's writing systems.</span></span>
* <span data-ttu-id="99b74-157">`U+10000..U+10FFFF`**範圍內的補充代碼點**。</span><span class="sxs-lookup"><span data-stu-id="99b74-157">**Supplementary code points** in the range `U+10000..U+10FFFF`.</span></span> <span data-ttu-id="99b74-158">此 21 位範圍提供了超過一百萬個額外的代碼點，可用於不太知名的語言和其他目的，如表情符號。</span><span class="sxs-lookup"><span data-stu-id="99b74-158">This 21-bit range provides more than a million additional code points that can be used for less well-known languages and other purposes such as emojis.</span></span>

<span data-ttu-id="99b74-159">下圖說明瞭 BMP 和補充代碼點之間的關係。</span><span class="sxs-lookup"><span data-stu-id="99b74-159">The following diagram illustrates the relationship between the BMP and the supplementary code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/bmp-and-supplementary.svg" alt-text="BMP 和補充代碼點":::

## <a name="utf-16-code-units"></a><span data-ttu-id="99b74-161">UTF-16 代碼單元</span><span class="sxs-lookup"><span data-stu-id="99b74-161">UTF-16 code units</span></span>

<span data-ttu-id="99b74-162">16 位 Unicode 轉換格式 （[UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)） 是一個字元編碼系統，使用 16 位*代碼單元*來表示 Unicode 代碼點。</span><span class="sxs-lookup"><span data-stu-id="99b74-162">16-bit Unicode Transformation Format ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) is a character encoding system that uses 16-bit *code units* to represent Unicode code points.</span></span> <span data-ttu-id="99b74-163">.NET 使用 UTF-16 對 文本`string`進行編碼。</span><span class="sxs-lookup"><span data-stu-id="99b74-163">.NET uses UTF-16 to encode the text in a `string`.</span></span> <span data-ttu-id="99b74-164">實例`char`表示 16 位代碼單元。</span><span class="sxs-lookup"><span data-stu-id="99b74-164">A `char` instance represents a 16-bit code unit.</span></span>

<span data-ttu-id="99b74-165">單個 16 位代碼單元可以表示基本多語言平面 16 位範圍內的任何代碼點。</span><span class="sxs-lookup"><span data-stu-id="99b74-165">A single 16-bit code unit can represent any code point in the 16-bit range of the Basic Multilingual Plane.</span></span> <span data-ttu-id="99b74-166">但對於補充範圍內的代碼點，需要兩`char`個實例。</span><span class="sxs-lookup"><span data-stu-id="99b74-166">But for a code point in the supplementary range, two `char` instances are needed.</span></span>

## <a name="surrogate-pairs"></a><span data-ttu-id="99b74-167">代理對</span><span class="sxs-lookup"><span data-stu-id="99b74-167">Surrogate pairs</span></span>

<span data-ttu-id="99b74-168">兩個 16 位值到單個 21 位值的轉換由一個稱為*代理代碼點*的特殊範圍（包括小`U+D800`數`U+DFFF`55，296 到 57，343）促進。</span><span class="sxs-lookup"><span data-stu-id="99b74-168">The translation of two 16-bit values to a single 21-bit value is facilitated by a special range called the *surrogate code points*, from `U+D800` to `U+DFFF` (decimal 55,296 to 57,343), inclusive.</span></span>

<span data-ttu-id="99b74-169">下圖說明瞭 BMP 和代理代碼點之間的關係。</span><span class="sxs-lookup"><span data-stu-id="99b74-169">The following diagram illustrates the relationship between the BMP and the surrogate code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/bmp-and-surrogate.svg" alt-text="BMP 和代理代碼點":::

<span data-ttu-id="99b74-171">當*高代理項*代碼點`U+D800..U+DBFF`（ ） 緊跟*低代理項*代碼點`U+DC00..U+DFFF`（ ）， 使用以下公式將配對解釋為輔助代碼點：</span><span class="sxs-lookup"><span data-stu-id="99b74-171">When a *high surrogate* code point (`U+D800..U+DBFF`) is immediately followed by a *low surrogate* code point (`U+DC00..U+DFFF`), the pair is interpreted as a supplementary code point by using the following formula:</span></span>

```
code point = 0x10000 +
  ((high surrogate code point - 0xD800) * 0x0400) +
  (low surrogate code point - 0xDC00)
```

<span data-ttu-id="99b74-172">下面是使用十進位標記法的相同公式：</span><span class="sxs-lookup"><span data-stu-id="99b74-172">Here's the same formula using decimal notation:</span></span>

```
code point = 65,536 +
  ((high surrogate code point - 55,296) * 1,024) +
  (low surrogate code point - 56,320)
```

<span data-ttu-id="99b74-173">*高*代理項代碼點的數位值不高於*低*代理項代碼點。</span><span class="sxs-lookup"><span data-stu-id="99b74-173">A *high* surrogate code point doesn't have a higher number value than a *low* surrogate code point.</span></span> <span data-ttu-id="99b74-174">高代理項代碼點稱為"高"，因為它用於計算完整 21 位代碼點範圍的高階 11 位。</span><span class="sxs-lookup"><span data-stu-id="99b74-174">The high surrogate code point is called "high" because it's used to calculate the higher-order 11 bits of the full 21-bit code point range.</span></span> <span data-ttu-id="99b74-175">低代理項代碼點用於計算低階 10 位。</span><span class="sxs-lookup"><span data-stu-id="99b74-175">The low surrogate code point is used to calculate the lower-order 10 bits.</span></span>

<span data-ttu-id="99b74-176">例如，對應于代理項對`0xD83C`並`0xDF39`計算的實際代碼點如下所示：</span><span class="sxs-lookup"><span data-stu-id="99b74-176">For example, the actual code point that corresponds to the surrogate pair `0xD83C` and `0xDF39`  is computed as follows:</span></span>

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

<span data-ttu-id="99b74-177">下面是使用十進位標記法的相同計算：</span><span class="sxs-lookup"><span data-stu-id="99b74-177">Here's the same calculation using decimal notation:</span></span>

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

<span data-ttu-id="99b74-178">前面的示例演示了`"\ud83c\udf39"`前面提到的`U+1F339 ROSE ('🌹')`代碼點的 UTF-16 編碼。</span><span class="sxs-lookup"><span data-stu-id="99b74-178">The preceding example demonstrates that `"\ud83c\udf39"` is the UTF-16 encoding of the `U+1F339 ROSE ('🌹')` code point mentioned earlier.</span></span>

## <a name="unicode-scalar-values"></a><span data-ttu-id="99b74-179">Unicode 標量值</span><span class="sxs-lookup"><span data-stu-id="99b74-179">Unicode scalar values</span></span>

<span data-ttu-id="99b74-180">術語[Unicode 標量值](https://www.unicode.org/glossary/#unicode_scalar_value)引用代理代碼點以外的所有代碼點。</span><span class="sxs-lookup"><span data-stu-id="99b74-180">The term [Unicode scalar value](https://www.unicode.org/glossary/#unicode_scalar_value) refers to all code points other than the surrogate code points.</span></span> <span data-ttu-id="99b74-181">換句話說，標量值是分配給字元或將來可以分配字元的任何代碼點。</span><span class="sxs-lookup"><span data-stu-id="99b74-181">In other words, a scalar value is any code point that is assigned a character or can be assigned a character in the future.</span></span> <span data-ttu-id="99b74-182">此處的"字元"是指可以分配給代碼點的任何內容，其中包括控制文本或字元顯示方式的操作等操作。</span><span class="sxs-lookup"><span data-stu-id="99b74-182">"Character" here refers to anything that can be assigned to a code point, which includes such things as actions that control how text or characters are displayed.</span></span>

<span data-ttu-id="99b74-183">下圖說明瞭標量值代碼點。</span><span class="sxs-lookup"><span data-stu-id="99b74-183">The following diagram illustrates the scalar value code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/scalar-values.svg" alt-text="純量值":::

### <a name="the-opno-locrune-type-as-a-scalar-value"></a><span data-ttu-id="99b74-185">Rune類型為標量值</span><span class="sxs-lookup"><span data-stu-id="99b74-185">The Rune type as a scalar value</span></span>

<span data-ttu-id="99b74-186">從 .NET Core 3.0<xref:System.Text.Rune?displayProperty=fullName>開始，該類型表示 Unicode 標量值。</span><span class="sxs-lookup"><span data-stu-id="99b74-186">Beginning with .NET Core 3.0, the <xref:System.Text.Rune?displayProperty=fullName> type represents a Unicode scalar value.</span></span> <span data-ttu-id="99b74-187">**`Rune`不在 .NET 核心 2.x 或 .NET 框架 4.x 中可用。**</span><span class="sxs-lookup"><span data-stu-id="99b74-187">**`Rune` is not available in .NET Core 2.x or .NET Framework 4.x.**</span></span>

<span data-ttu-id="99b74-188">構造`Rune`函數驗證生成的實例是否是有效的 Unicode 標量值，否則它們會引發異常。</span><span class="sxs-lookup"><span data-stu-id="99b74-188">The `Rune` constructors validate that the resulting instance is a valid Unicode scalar value, otherwise they throw an exception.</span></span> <span data-ttu-id="99b74-189">下面的示例顯示成功具現化`Rune`的代碼，因為輸入表示有效的標量值：</span><span class="sxs-lookup"><span data-stu-id="99b74-189">The following example shows code that successfully instantiates `Rune` instances because the input represents valid scalar values:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetValid":::

<span data-ttu-id="99b74-190">下面的示例引發異常，因為代碼點位於代理項範圍內，並且不是代理項對的一部分：</span><span class="sxs-lookup"><span data-stu-id="99b74-190">The following example throws an exception because the code point is in the surrogate range and isn't part of a surrogate pair:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidSurrogate":::

<span data-ttu-id="99b74-191">以下示例引發異常，因為代碼點超出補充範圍：</span><span class="sxs-lookup"><span data-stu-id="99b74-191">The following example throws an exception because the code point is beyond the supplementary range:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidHigh":::

### <a name="opno-locrune-usage-example-changing-letter-case"></a>Rune<span data-ttu-id="99b74-192">使用示例：更改字母大小寫</span><span class="sxs-lookup"><span data-stu-id="99b74-192"> usage example: changing letter case</span></span>

<span data-ttu-id="99b74-193">如果`char`從 代理`char`項對中獲取 並假定它正在使用標量值的代碼點的 API 不能正常工作。</span><span class="sxs-lookup"><span data-stu-id="99b74-193">An API that takes a `char` and assumes it is working with a code point that is a scalar value doesn't work correctly if the `char` is from a surrogate pair.</span></span> <span data-ttu-id="99b74-194">例如，請考慮以下方法，該方法調用<xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType>中的每個char方法： string</span><span class="sxs-lookup"><span data-stu-id="99b74-194">For example, consider the following method that calls <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> on each char in a string:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::

<span data-ttu-id="99b74-195">`input` string如果 包含小寫 Deseret 字母`er``𐑉`（），則此代碼不會將其轉換為大寫 （）。`𐐡`</span><span class="sxs-lookup"><span data-stu-id="99b74-195">If the `input` string contains the lowercase Deseret letter `er` (`𐑉`), this code won't convert it to uppercase (`𐐡`).</span></span> <span data-ttu-id="99b74-196">代碼在每個代理`char.ToUpperInvariant`代碼點上分別調用 ，`U+D801`和`U+DC49`.</span><span class="sxs-lookup"><span data-stu-id="99b74-196">The code calls `char.ToUpperInvariant` separately on each surrogate code point, `U+D801` and `U+DC49`.</span></span> <span data-ttu-id="99b74-197">但是`U+D801`，沒有足夠的資訊本身來識別它作為小寫字母，所以`char.ToUpperInvariant`別管它。</span><span class="sxs-lookup"><span data-stu-id="99b74-197">But `U+D801` doesn't have enough information by itself to identify it as a lowercase letter, so `char.ToUpperInvariant` leaves it alone.</span></span> <span data-ttu-id="99b74-198">它處理`U+DC49`的方式相同。</span><span class="sxs-lookup"><span data-stu-id="99b74-198">And it handles `U+DC49` the same way.</span></span> <span data-ttu-id="99b74-199">結果是，中的`input`string小寫""不會轉換為大寫""。"。</span><span class="sxs-lookup"><span data-stu-id="99b74-199">The result is that lowercase '𐑉' in the `input` string doesn't get converted to uppercase '𐐡'.</span></span>

<span data-ttu-id="99b74-200">以下是正確轉換為大寫字母的string兩個選項：</span><span class="sxs-lookup"><span data-stu-id="99b74-200">Here are two options for correctly converting a string to uppercase:</span></span>

* <span data-ttu-id="99b74-201">調用<xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType>輸入string，而不是`char`逐反覆運算 。`char`</span><span class="sxs-lookup"><span data-stu-id="99b74-201">Call <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> on the input string rather than iterating `char`-by-`char`.</span></span> <span data-ttu-id="99b74-202">該方法`string.ToUpperInvariant`有權訪問每個代理項對的兩個部分，因此它可以正確處理所有 Unicode 代碼點。</span><span class="sxs-lookup"><span data-stu-id="99b74-202">The `string.ToUpperInvariant` method has access to both parts of each surrogate pair, so it can handle all Unicode code points correctly.</span></span>
* <span data-ttu-id="99b74-203">反覆運算 Unicode 標量值作為`Rune`實例而不是`char`實例，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="99b74-203">Iterate through the Unicode scalar values as `Rune` instances instead of `char` instances, as shown in the following example.</span></span> <span data-ttu-id="99b74-204">由於`Rune`實例是有效的 Unicode 標量值，因此可以將它傳遞給預期對標量值操作的 API。</span><span class="sxs-lookup"><span data-stu-id="99b74-204">Since a `Rune` instance is a valid Unicode scalar value, it can be passed to APIs that expect to operate on a scalar value.</span></span> <span data-ttu-id="99b74-205">例如，如下例<xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType>所示的調用可提供正確的結果：</span><span class="sxs-lookup"><span data-stu-id="99b74-205">For example, calling <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> as shown in the following example gives correct results:</span></span>

  :::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::

### <a name="other-opno-locrune-apis"></a><span data-ttu-id="99b74-206">其他RuneAPI</span><span class="sxs-lookup"><span data-stu-id="99b74-206">Other Rune APIs</span></span>

<span data-ttu-id="99b74-207">該`Rune`類型公開了許多 API 的`char`類比。</span><span class="sxs-lookup"><span data-stu-id="99b74-207">The `Rune` type exposes analogs of many of the `char` APIs.</span></span> <span data-ttu-id="99b74-208">例如，以下方法在`char`類型上鏡像靜態 API：</span><span class="sxs-lookup"><span data-stu-id="99b74-208">For example, the following methods mirror static APIs on the `char` type:</span></span>

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

<span data-ttu-id="99b74-209">要從`Rune`實例獲取原始標量值，請使用 屬性<xref:System.Text.Rune.Value%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="99b74-209">To get the raw scalar value from a `Rune` instance, use the <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="99b74-210">要將`Rune`實例轉換回 s 序列`char`，請使用<xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType>或<xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="99b74-210">To convert a `Rune` instance back to a sequence of `char`s, use <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> or the <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="99b74-211">由於任何 Unicode 標量值都可以由單個`char`或代理項對表示，因此最多`Rune`只能由 2`char`個實例表示任何實例。</span><span class="sxs-lookup"><span data-stu-id="99b74-211">Since any Unicode scalar value is representable by a single `char` or by a surrogate pair, any `Rune` instance can be represented by at most 2 `char` instances.</span></span> <span data-ttu-id="99b74-212">用於<xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType>查看表示`Rune`實例所需的`char`實例數。</span><span class="sxs-lookup"><span data-stu-id="99b74-212">Use <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> to see how many `char` instances are required to represent a `Rune` instance.</span></span>

<span data-ttu-id="99b74-213">有關 .NET`Rune`類型的詳細資訊，請參閱[`Rune`API 引用](xref:System.Text.Rune)。</span><span class="sxs-lookup"><span data-stu-id="99b74-213">For more information about the .NET `Rune` type, see the [`Rune` API reference](xref:System.Text.Rune).</span></span>

## <a name="grapheme-clusters"></a><span data-ttu-id="99b74-214">石墨聚類</span><span class="sxs-lookup"><span data-stu-id="99b74-214">Grapheme clusters</span></span>

<span data-ttu-id="99b74-215">看起來像一個字元的原因可能是由多個代碼點的組合產生的，因此通常用來代替"字元"的更具描述性的術語是[石墨聚類](https://www.unicode.org/glossary/#grapheme_cluster)。</span><span class="sxs-lookup"><span data-stu-id="99b74-215">What looks like one character might result from a combination of multiple code points, so a more descriptive term that is often used in place of "character" is [grapheme cluster](https://www.unicode.org/glossary/#grapheme_cluster).</span></span> <span data-ttu-id="99b74-216">.NET 中的等效術語是[文本元素](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A)。</span><span class="sxs-lookup"><span data-stu-id="99b74-216">The equivalent term in .NET is [text element](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span></span>

<span data-ttu-id="99b74-217">考慮`string`實例"a"，"\""。</span><span class="sxs-lookup"><span data-stu-id="99b74-217">Consider the `string` instances "a", "á".</span></span> <span data-ttu-id="99b74-218">""和""。`👩🏽‍🚒`</span><span class="sxs-lookup"><span data-stu-id="99b74-218">"á", and "`👩🏽‍🚒`".</span></span> <span data-ttu-id="99b74-219">如果作業系統按 Unicode 標準指定處理它們，則每個`string`實例都顯示為單個文本元素或圖形學群集。</span><span class="sxs-lookup"><span data-stu-id="99b74-219">If your operating system handles them as specified by the Unicode standard, each of these `string` instances appears as a single text element or grapheme cluster.</span></span> <span data-ttu-id="99b74-220">但後兩個由多個標量值代碼點表示。</span><span class="sxs-lookup"><span data-stu-id="99b74-220">But the last two are represented by more than one scalar value code point.</span></span>

* <span data-ttu-id="99b74-221">"a"string由一個標量值表示，並包含一個`char`實例。</span><span class="sxs-lookup"><span data-stu-id="99b74-221">The string "a" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+0061 LATIN SMALL LETTER A`

* <span data-ttu-id="99b74-222">"="string由一個標量值表示，並包含一個`char`實例。</span><span class="sxs-lookup"><span data-stu-id="99b74-222">The string "á" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+00E1 LATIN SMALL LETTER E WITH ACUTE`

* <span data-ttu-id="99b74-223">"="string看起來與"="相同，但由兩個標量值表示，並包含兩`char`個實例。</span><span class="sxs-lookup"><span data-stu-id="99b74-223">The string "á" looks the same as "á" but is represented by two scalar values and contains two `char` instances.</span></span>

  * `U+0065 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* <span data-ttu-id="99b74-224">最後，""string`👩🏽‍🚒`由四個標量值表示，並包含七`char`個實例。</span><span class="sxs-lookup"><span data-stu-id="99b74-224">Finally, the string "`👩🏽‍🚒`" is represented by four scalar values and contains seven `char` instances.</span></span>

  * <span data-ttu-id="99b74-225">`U+1F469 WOMAN`（補充範圍，需要代理對）</span><span class="sxs-lookup"><span data-stu-id="99b74-225">`U+1F469 WOMAN` (supplementary range, requires a surrogate pair)</span></span>
  * <span data-ttu-id="99b74-226">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4`（補充範圍，需要代理對）</span><span class="sxs-lookup"><span data-stu-id="99b74-226">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (supplementary range, requires a surrogate pair)</span></span>
  * `U+200D ZERO WIDTH JOINER`
  * <span data-ttu-id="99b74-227">`U+1F692 FIRE ENGINE`（補充範圍，需要代理對）</span><span class="sxs-lookup"><span data-stu-id="99b74-227">`U+1F692 FIRE ENGINE` (supplementary range, requires a surrogate pair)</span></span>

<span data-ttu-id="99b74-228">在前面的一些示例中（如組合重音修改器或膚色修飾符）中，代碼點不會在螢幕上顯示為獨立元素。</span><span class="sxs-lookup"><span data-stu-id="99b74-228">In some of the preceding examples - such as the combining accent modifier or the skin tone modifier - the code point does not display as a standalone element on the screen.</span></span> <span data-ttu-id="99b74-229">相反，它用於修改它之前的文本元素的外觀。</span><span class="sxs-lookup"><span data-stu-id="99b74-229">Rather, it serves to modify the appearance of a text element that came before it.</span></span> <span data-ttu-id="99b74-230">這些示例表明，可能需要多個標量值來構成我們認為為單個"字元"或"圖形群集"。"</span><span class="sxs-lookup"><span data-stu-id="99b74-230">These examples show that it might take multiple scalar values to make up what we think of as a single "character," or "grapheme cluster."</span></span>

<span data-ttu-id="99b74-231">要枚舉 的`string`圖目組，請使用類，<xref:System.Globalization.StringInfo>如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="99b74-231">To enumerate the grapheme clusters of a `string`, use the <xref:System.Globalization.StringInfo> class as shown in the following example.</span></span> <span data-ttu-id="99b74-232">如果您熟悉 Swift，則 .NET`StringInfo`類型在概念上與[Swift`character`的類型](https://developer.apple.com/documentation/swift/character)類似。</span><span class="sxs-lookup"><span data-stu-id="99b74-232">If you're familiar with Swift, the .NET `StringInfo` type is conceptually similar to [Swift's `character` type](https://developer.apple.com/documentation/swift/character).</span></span>

### <a name="example-count-opno-locchar-opno-locrune-and-text-element-instances"></a><span data-ttu-id="99b74-233">示例：計數charRune和 文本元素實例</span><span class="sxs-lookup"><span data-stu-id="99b74-233">Example: count char, Rune, and text element instances</span></span>

<span data-ttu-id="99b74-234">在 .NET API 中，圖形學群集稱為*文本元素*。</span><span class="sxs-lookup"><span data-stu-id="99b74-234">In .NET APIs, a grapheme cluster is called a *text element*.</span></span> <span data-ttu-id="99b74-235">以下方法演示 了 中`char``Rune`的文本元素實例之間的差異`string`：</span><span class="sxs-lookup"><span data-stu-id="99b74-235">The following method demonstrates the differences between `char`, `Rune`, and text element instances in a `string`:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::

<span data-ttu-id="99b74-236">如果在 .NET 框架或 .NET Core 3.1 或更早版本中運行此代碼，則表情符號`4`的文本元素計數將顯示 。</span><span class="sxs-lookup"><span data-stu-id="99b74-236">If you run this code in .NET Framework or .NET Core 3.1 or earlier, the text element count for the emoji shows `4`.</span></span> <span data-ttu-id="99b74-237">這是因為在 .NET 5`StringInfo`中修復的類中存在 Bug。</span><span class="sxs-lookup"><span data-stu-id="99b74-237">That is due to a bug in the `StringInfo` class that is fixed in .NET 5.</span></span>

### <a name="example-splitting-opno-locstring-instances"></a><span data-ttu-id="99b74-238">示例：拆分string實例</span><span class="sxs-lookup"><span data-stu-id="99b74-238">Example: splitting string instances</span></span>

<span data-ttu-id="99b74-239">拆分`string`實例時，請避免拆分代理項對和石墨組。</span><span class="sxs-lookup"><span data-stu-id="99b74-239">When splitting `string` instances, avoid splitting surrogate pairs and grapheme clusters.</span></span> <span data-ttu-id="99b74-240">請考慮以下錯誤代碼示例，該示例打算在 中每 10 個字元插入換string行符：</span><span class="sxs-lookup"><span data-stu-id="99b74-240">Consider the following example of incorrect code, which intends to insert line breaks every 10 characters in a string:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::

<span data-ttu-id="99b74-241">由於此代碼枚`char`舉實例，因此將拆分恰巧跨越 10 邊界的`char`代理項對，並在它們之間注入一條新線。</span><span class="sxs-lookup"><span data-stu-id="99b74-241">Because this code enumerates `char` instances, a surrogate pair that happens to straddle a 10-`char` boundary will be split and a newline injected between them.</span></span> <span data-ttu-id="99b74-242">此插入會引入資料損壞，因為代理代碼點僅作為對有意義。</span><span class="sxs-lookup"><span data-stu-id="99b74-242">This insertion introduces data corruption, because surrogate code points are meaningful only as pairs.</span></span>

<span data-ttu-id="99b74-243">如果枚舉`Rune`實例（標點值）而不是`char`實例，則不會消除資料損壞的可能性。</span><span class="sxs-lookup"><span data-stu-id="99b74-243">The potential for data corruption isn't eliminated if you enumerate `Rune` instances (scalar values) instead of `char` instances.</span></span> <span data-ttu-id="99b74-244">一組`Rune`實例可能構成跨越 10 邊界的`char`石墨星系團。</span><span class="sxs-lookup"><span data-stu-id="99b74-244">A set of `Rune` instances might make up a grapheme cluster that straddles a 10-`char` boundary.</span></span> <span data-ttu-id="99b74-245">如果圖形圖姆群集集被拆分，則無法正確解釋它。</span><span class="sxs-lookup"><span data-stu-id="99b74-245">If the grapheme cluster set is split up, it can't be interpreted correctly.</span></span>

<span data-ttu-id="99b74-246">更好的方法是string通過計算石墨烯聚類或文本元素來打破，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="99b74-246">A better approach is to break the string by counting grapheme clusters, or text elements, as in the following example:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::

<span data-ttu-id="99b74-247">但是，如前所述，在 .NET 的實現中，除了 .NET `StringInfo` 5 之外，類可能會錯誤地處理某些圖目群。</span><span class="sxs-lookup"><span data-stu-id="99b74-247">As noted earlier, however, in implementations of .NET other than .NET 5, the `StringInfo` class might handle some grapheme clusters incorrectly.</span></span>

## <a name="utf-8-and-utf-32"></a><span data-ttu-id="99b74-248">UTF-8 和 UTF-32</span><span class="sxs-lookup"><span data-stu-id="99b74-248">UTF-8 and UTF-32</span></span>

<span data-ttu-id="99b74-249">前面各節重點介紹 UTF-16，因為這是 .NET 用於對實例`string`進行編碼的內容。</span><span class="sxs-lookup"><span data-stu-id="99b74-249">The preceding sections focused on UTF-16 because that's what .NET uses to encode `string` instances.</span></span> <span data-ttu-id="99b74-250">Unicode - [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8)和[UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32)還有其他編碼系統。</span><span class="sxs-lookup"><span data-stu-id="99b74-250">There are other encoding systems for Unicode - [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) and [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32).</span></span> <span data-ttu-id="99b74-251">這些編碼分別使用 8 位代碼單元和 32 位代碼單元。</span><span class="sxs-lookup"><span data-stu-id="99b74-251">These encodings use 8-bit code units and 32-bit code units, respectively.</span></span>

<span data-ttu-id="99b74-252">與 UTF-16 一樣，UTF-8 需要多個代碼單元來表示某些 Unicode 標量值。</span><span class="sxs-lookup"><span data-stu-id="99b74-252">Like UTF-16, UTF-8 requires multiple code units to represent some Unicode scalar values.</span></span> <span data-ttu-id="99b74-253">UTF-32 可以表示單個 32 位代碼單元中的任何標量值。</span><span class="sxs-lookup"><span data-stu-id="99b74-253">UTF-32 can represent any scalar value in a single 32-bit code unit.</span></span>

<span data-ttu-id="99b74-254">下面是一些示例，顯示了如何在以下三個 Unicode 編碼系統中表示同一 Unicode 代碼點：</span><span class="sxs-lookup"><span data-stu-id="99b74-254">Here are some examples showing how the same Unicode code point is represented in each of these three Unicode encoding systems:</span></span>

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

<span data-ttu-id="99b74-255">如前所述，[代理對](#surrogate-pairs)中單個 UTF-16 代碼單元本身就毫無意義。</span><span class="sxs-lookup"><span data-stu-id="99b74-255">As noted earlier, a single UTF-16 code unit from a [surrogate pair](#surrogate-pairs) is meaningless by itself.</span></span> <span data-ttu-id="99b74-256">同樣，如果單個 UTF-8 代碼單元的序列為 2、3 或 4，則它本身就毫無意義。</span><span class="sxs-lookup"><span data-stu-id="99b74-256">In the same way, a single UTF-8 code unit is meaningless by itself if it's in a sequence of two, three, or four used to calculate a scalar value.</span></span>

### <a name="endianness"></a><span data-ttu-id="99b74-257">位元組序</span><span class="sxs-lookup"><span data-stu-id="99b74-257">Endianness</span></span>

<span data-ttu-id="99b74-258">在 .NET 中，astring的 UTF-16 代碼單元作為 16 位整數（`char`實例）的順序存儲在連續記憶體中。</span><span class="sxs-lookup"><span data-stu-id="99b74-258">In .NET, the UTF-16 code units of a string are stored in contiguous memory as a sequence of 16-bit integers (`char` instances).</span></span> <span data-ttu-id="99b74-259">各個代碼單元的位根據當前體系結構的[內端性](https://en.wikipedia.org/wiki/Endianness)進行佈局。</span><span class="sxs-lookup"><span data-stu-id="99b74-259">The bits of individual code units are laid out according to the [endianness](https://en.wikipedia.org/wiki/Endianness) of the current architecture.</span></span>

<span data-ttu-id="99b74-260">在一個小端架構上，string由UTF-16代碼點組成的代碼點`[ D801 DCCC ]`將作為位元組`[ 0x01, 0xD8, 0xCC, 0xDC ]`在記憶體中佈局。</span><span class="sxs-lookup"><span data-stu-id="99b74-260">On a little-endian architecture, the string consisting of the UTF-16 code points `[ D801 DCCC ]` would be laid out in memory as the bytes `[ 0x01, 0xD8, 0xCC, 0xDC ]`.</span></span> <span data-ttu-id="99b74-261">在大型的體系結構上，在string記憶體中也會像位元組`[ 0xD8, 0x01, 0xDC, 0xCC ]`一樣佈局。</span><span class="sxs-lookup"><span data-stu-id="99b74-261">On a big-endian architecture that same string would be laid out in memory as the bytes `[ 0xD8, 0x01, 0xDC, 0xCC ]`.</span></span>

<span data-ttu-id="99b74-262">相互通信的電腦系統必須就跨線資料的表示方式達成一致。</span><span class="sxs-lookup"><span data-stu-id="99b74-262">Computer systems that communicate with each other must agree on the representation of data crossing the wire.</span></span> <span data-ttu-id="99b74-263">大多數網路通訊協定在傳輸文本時使用 UTF-8 作為標準，部分是為了避免與小終端機器通信時可能出現的問題。</span><span class="sxs-lookup"><span data-stu-id="99b74-263">Most network protocols use UTF-8 as a standard when transmitting text, partly to avoid issues that might result from a big-endian machine communicating with a little-endian machine.</span></span> <span data-ttu-id="99b74-264">UTF-8 代碼點string`[ F0 90 93 8C ]`組成將始終表示為位元組`[ 0xF0, 0x90, 0x93, 0x8C ]`，而不考慮端點性。</span><span class="sxs-lookup"><span data-stu-id="99b74-264">The string consisting of the UTF-8 code points `[ F0 90 93 8C ]` will always be represented as the bytes `[ 0xF0, 0x90, 0x93, 0x8C ]` regardless of endianness.</span></span>

<span data-ttu-id="99b74-265">要使用 UTF-8 傳輸文本，.NET 應用程式通常使用如下示例這樣的代碼：</span><span class="sxs-lookup"><span data-stu-id="99b74-265">To use UTF-8 for transmitting text, .NET applications often use code like the following example:</span></span>

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

<span data-ttu-id="99b74-266">在前面的示例中，方法[Code.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A)將 UTF-16`string`解碼回一系列 Unicode 標量值，然後將這些標量值重新編碼到 UTF-8 中，並將生成的序列放入`byte`陣列中。</span><span class="sxs-lookup"><span data-stu-id="99b74-266">In the preceding example, the method [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) decodes the UTF-16 `string` back into a series of Unicode scalar values, then it re-encodes those scalar values into UTF-8 and places the resulting sequence into a `byte` array.</span></span> <span data-ttu-id="99b74-267">方法[Encode.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A)執行相反的轉換，將 UTF-8`byte`陣列轉換為 UTF-16 `string`。</span><span class="sxs-lookup"><span data-stu-id="99b74-267">The method [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) performs the opposite transformation, converting a UTF-8 `byte` array to a UTF-16 `string`.</span></span>

> [!WARNING]
> <span data-ttu-id="99b74-268">由於 UTF-8 在互聯網上很常見，因此從導線中讀取原始位元組並像將資料視為 UTF-8 時，可能會很誘人。</span><span class="sxs-lookup"><span data-stu-id="99b74-268">Since UTF-8 is commonplace on the internet, it may be tempting to read raw bytes from the wire and to treat the data as if it were UTF-8.</span></span> <span data-ttu-id="99b74-269">但是，您應該驗證它確實格式良好。</span><span class="sxs-lookup"><span data-stu-id="99b74-269">However, you should validate that it is indeed well-formed.</span></span> <span data-ttu-id="99b74-270">惡意用戶端可能會向服務提交格式錯誤的 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="99b74-270">A malicious client might submit ill-formed UTF-8 to your service.</span></span> <span data-ttu-id="99b74-271">如果對該資料進行操作，就好像它格式良好一樣，則可能會導致應用程式中的錯誤或安全性漏洞。</span><span class="sxs-lookup"><span data-stu-id="99b74-271">If you operate on that data as if it were well-formed, it could cause errors or security holes in your application.</span></span> <span data-ttu-id="99b74-272">要驗證 UTF-8 資料，可以使用 類似`Encoding.UTF8.GetString`的方法，該方法將在將傳入資料轉換為 時執行驗證`string`。</span><span class="sxs-lookup"><span data-stu-id="99b74-272">To validate UTF-8 data, you can use a method like `Encoding.UTF8.GetString`, which will perform validation while converting the incoming data to a `string`.</span></span>

### <a name="well-formed-encoding"></a><span data-ttu-id="99b74-273">格式良好的編碼</span><span class="sxs-lookup"><span data-stu-id="99b74-273">Well-formed encoding</span></span>

<span data-ttu-id="99b74-274">格式良好的 Unicode 編碼是一string種代碼單元，可以明確解碼，而不會出錯地解碼到 Unicode 標量值序列中。</span><span class="sxs-lookup"><span data-stu-id="99b74-274">A well-formed Unicode encoding is a string of code units that can be decoded unambiguously and without error into a sequence of Unicode scalar values.</span></span> <span data-ttu-id="99b74-275">格式良好的資料可以在 UTF-8、UTF-16 和 UTF-32 之間自由來回轉換。</span><span class="sxs-lookup"><span data-stu-id="99b74-275">Well-formed data can be transcoded freely back and forth between UTF-8, UTF-16, and UTF-32.</span></span>

<span data-ttu-id="99b74-276">編碼序列是否格式良好的問題與電腦體系結構的內向性無關。</span><span class="sxs-lookup"><span data-stu-id="99b74-276">The question of whether an encoding sequence is well-formed or not is unrelated to the endianness of a machine's architecture.</span></span> <span data-ttu-id="99b74-277">在大型機器和小端型機器上，格式錯誤的 UTF-8 序列格式不正確。</span><span class="sxs-lookup"><span data-stu-id="99b74-277">An ill-formed UTF-8 sequence is ill-formed in the same way on both big-endian and little-endian machines.</span></span>

<span data-ttu-id="99b74-278">下面是一些格式錯誤的編碼示例：</span><span class="sxs-lookup"><span data-stu-id="99b74-278">Here are some examples of ill-formed encodings:</span></span>

* <span data-ttu-id="99b74-279">在 UTF-8 中`[ 6C C2 61 ]`，序列格式不正確，`C2`因為不能跟後`61`。</span><span class="sxs-lookup"><span data-stu-id="99b74-279">In UTF-8, the sequence `[ 6C C2 61 ]` is ill-formed because `C2` cannot be followed by `61`.</span></span>

* <span data-ttu-id="99b74-280">在 UTF-16 中`[ DC00 DD00 ]`，序列（或，在 C#string`"\udc00\udd00"`中， ） 格式不正確`DC00`，因為低代理項不能跟`DD00`後另一個低代理項 。</span><span class="sxs-lookup"><span data-stu-id="99b74-280">In UTF-16, the sequence `[ DC00 DD00 ]` (or, in C#, the string `"\udc00\udd00"`) is ill-formed because the low surrogate `DC00` cannot be followed by another low surrogate `DD00`.</span></span>

* <span data-ttu-id="99b74-281">在 UTF-32 中`[ 0011ABCD ]`，序列格式不正確，`0011ABCD`因為超出 Unicode 標量值的範圍。</span><span class="sxs-lookup"><span data-stu-id="99b74-281">In UTF-32, the sequence `[ 0011ABCD ]` is ill-formed because `0011ABCD` is outside the range of Unicode scalar values.</span></span>

<span data-ttu-id="99b74-282">在 .NET`string`中，實例幾乎總是包含格式良好的 UTF-16 資料，但這不能保證。</span><span class="sxs-lookup"><span data-stu-id="99b74-282">In .NET, `string` instances almost always contain well-formed UTF-16 data, but that isn't guaranteed.</span></span> <span data-ttu-id="99b74-283">以下示例顯示在實例中`string`創建格式錯誤的 UTF-16 資料的有效 C# 代碼。</span><span class="sxs-lookup"><span data-stu-id="99b74-283">The following examples show valid C# code that creates ill-formed UTF-16 data in `string` instances.</span></span>

* <span data-ttu-id="99b74-284">格式不佳的字面：</span><span class="sxs-lookup"><span data-stu-id="99b74-284">An ill-formed literal:</span></span>

  ```csharp
  const string s = "\ud800";
  ```

* <span data-ttu-id="99b74-285">拆分代理項對的子字串：</span><span class="sxs-lookup"><span data-stu-id="99b74-285">A substring that splits up a surrogate pair:</span></span>

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

<span data-ttu-id="99b74-286">API 就像[`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A)從不返回格式`string`錯誤的實例一樣。</span><span class="sxs-lookup"><span data-stu-id="99b74-286">APIs like [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) never return ill-formed `string` instances.</span></span> <span data-ttu-id="99b74-287">`Encoding.GetString`和方法`Encoding.GetBytes`檢測輸入中的格式錯誤的序列，並在生成輸出時執行字元替換。</span><span class="sxs-lookup"><span data-stu-id="99b74-287">`Encoding.GetString` and `Encoding.GetBytes` methods detect ill-formed sequences in the input and perform character substitution when generating the output.</span></span> <span data-ttu-id="99b74-288">例如，如果在[`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A)輸入中看到非 ASCII 位元組（超出 U+0000..U+007F 範圍），它將在返回`string`的實例中插入"？</span><span class="sxs-lookup"><span data-stu-id="99b74-288">For example, if [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) sees a non-ASCII byte in the input (outside the range U+0000..U+007F), it inserts a '?' into the returned `string` instance.</span></span> <span data-ttu-id="99b74-289">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A)在返回`U+FFFD REPLACEMENT CHARACTER ('�')``string`的實例中用格式錯誤的 UTF-8 序列替換格式不正確的 UTF-8 序列。</span><span class="sxs-lookup"><span data-stu-id="99b74-289">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A) replaces ill-formed UTF-8 sequences with `U+FFFD REPLACEMENT CHARACTER ('�')` in the returned `string` instance.</span></span> <span data-ttu-id="99b74-290">有關詳細資訊，請參閱[Unicode 標準](https://www.unicode.org/versions/latest/)，第 5.22 節和第 3.9 節。</span><span class="sxs-lookup"><span data-stu-id="99b74-290">For more information, see [the Unicode Standard](https://www.unicode.org/versions/latest/), Sections 5.22 and 3.9.</span></span>

<span data-ttu-id="99b74-291">也可以將內置`Encoding`類配置為引發異常，而不是在看到格式錯誤的序列時執行字元替換。</span><span class="sxs-lookup"><span data-stu-id="99b74-291">The built-in `Encoding` classes can also be configured to throw an exception rather than perform character substitution when ill-formed sequences are seen.</span></span> <span data-ttu-id="99b74-292">此方法通常用於對安全敏感的應用程式，其中字元替換可能不可接受。</span><span class="sxs-lookup"><span data-stu-id="99b74-292">This approach is often used in security-sensitive applications where character substitution might not be acceptable.</span></span>

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

<span data-ttu-id="99b74-293">有關如何使用內置`Encoding`類的資訊，請參閱[如何在 .NET 中使用字元編碼類](character-encoding.md)。</span><span class="sxs-lookup"><span data-stu-id="99b74-293">For information about how to use the built-in `Encoding` classes, see [How to use character encoding classes in .NET](character-encoding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="99b74-294">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99b74-294">See also</span></span>

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [<span data-ttu-id="99b74-295">全球化與當地語系化</span><span class="sxs-lookup"><span data-stu-id="99b74-295">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)
