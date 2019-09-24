---
title: 字串
description: 瞭解「字串F# 」類型如何以 Unicode 字元序清單示不可變的文字。
ms.date: 07/05/2019
ms.openlocfilehash: 25f5d7ce5059ba5ddb4e938313c511734c2d7320
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216742"
---
# <a name="strings"></a><span data-ttu-id="82c8c-103">字串</span><span class="sxs-lookup"><span data-stu-id="82c8c-103">Strings</span></span>

> [!NOTE]
> <span data-ttu-id="82c8c-104">本文中的 API 參考連結將帶您前往 MSDN。</span><span class="sxs-lookup"><span data-stu-id="82c8c-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="82c8c-105">docs.microsoft.com API 參考不完整。</span><span class="sxs-lookup"><span data-stu-id="82c8c-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="82c8c-106">`string`類型以 Unicode 字元序清單示不可變的文字。</span><span class="sxs-lookup"><span data-stu-id="82c8c-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="82c8c-107">`string` 是 `System.String` 在 .NET Framework 中的別名。</span><span class="sxs-lookup"><span data-stu-id="82c8c-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="82c8c-108">備註</span><span class="sxs-lookup"><span data-stu-id="82c8c-108">Remarks</span></span>

<span data-ttu-id="82c8c-109">字串常值是以引號（"）字元分隔。</span><span class="sxs-lookup"><span data-stu-id="82c8c-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="82c8c-110">反斜線字元（ \\ ）是用來編碼某些特殊字元。</span><span class="sxs-lookup"><span data-stu-id="82c8c-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="82c8c-111">反斜線和下一個字元一起稱為「*逸出序列*」。</span><span class="sxs-lookup"><span data-stu-id="82c8c-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="82c8c-112">下表顯示F#字串常值中支援的 Escape 序列。</span><span class="sxs-lookup"><span data-stu-id="82c8c-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="82c8c-113">字元</span><span class="sxs-lookup"><span data-stu-id="82c8c-113">Character</span></span>|<span data-ttu-id="82c8c-114">逸出序列</span><span class="sxs-lookup"><span data-stu-id="82c8c-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="82c8c-115">警示</span><span class="sxs-lookup"><span data-stu-id="82c8c-115">Alert</span></span>|`\a`|
|<span data-ttu-id="82c8c-116">退格鍵</span><span class="sxs-lookup"><span data-stu-id="82c8c-116">Backspace</span></span>|`\b`|
|<span data-ttu-id="82c8c-117">換頁字元</span><span class="sxs-lookup"><span data-stu-id="82c8c-117">Form feed</span></span>|`\f`|
|<span data-ttu-id="82c8c-118">新行字元</span><span class="sxs-lookup"><span data-stu-id="82c8c-118">Newline</span></span>|`\n`|
|<span data-ttu-id="82c8c-119">歸位字元</span><span class="sxs-lookup"><span data-stu-id="82c8c-119">Carriage return</span></span>|`\r`|
|<span data-ttu-id="82c8c-120">索引標籤</span><span class="sxs-lookup"><span data-stu-id="82c8c-120">Tab</span></span>|`\t`|
|<span data-ttu-id="82c8c-121">垂直 Tab</span><span class="sxs-lookup"><span data-stu-id="82c8c-121">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="82c8c-122">反斜線</span><span class="sxs-lookup"><span data-stu-id="82c8c-122">Backslash</span></span>|`\\`|
|<span data-ttu-id="82c8c-123">引號</span><span class="sxs-lookup"><span data-stu-id="82c8c-123">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="82c8c-124">省略號</span><span class="sxs-lookup"><span data-stu-id="82c8c-124">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="82c8c-125">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="82c8c-125">Unicode character</span></span>|<span data-ttu-id="82c8c-126">`\DDD`（其中`D`表示十進位數; 範圍為 000-255， `\231`例如 = "ç"）</span><span class="sxs-lookup"><span data-stu-id="82c8c-126">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; for example, `\231` = "ç")</span></span>|
|<span data-ttu-id="82c8c-127">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="82c8c-127">Unicode character</span></span>|<span data-ttu-id="82c8c-128">`\xHH`（其中`H`表示十六進位數位; 00-FF 的範圍， `\xE7`例如 = "ç"）</span><span class="sxs-lookup"><span data-stu-id="82c8c-128">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; for example, `\xE7` = "ç")</span></span>|
|<span data-ttu-id="82c8c-129">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="82c8c-129">Unicode character</span></span>|<span data-ttu-id="82c8c-130">`\uHHHH`（UTF-16）（其中`H`表示十六進位數位; 0000-FFFF 的範圍; 例如， `\u00E7` = "ç"）</span><span class="sxs-lookup"><span data-stu-id="82c8c-130">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  for example, `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="82c8c-131">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="82c8c-131">Unicode character</span></span>|<span data-ttu-id="82c8c-132">`\U00HHHHHH`（UTF-32）（其中`H`表示十六進位數位; 000000-10ffff 且的範圍; 例如， `\U0001F47D` = "👽"）</span><span class="sxs-lookup"><span data-stu-id="82c8c-132">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  for example, `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="82c8c-133">`\DDD` Escape 序列是十進位標記法，而非八進位標記法，就像大多數其他語言一樣。</span><span class="sxs-lookup"><span data-stu-id="82c8c-133">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="82c8c-134">因此，數位`8`和`9`有效`\032` ，而的序列則代表空格（U + 0020），而八進位標記法中的相同程式碼點則為`\040`。</span><span class="sxs-lookup"><span data-stu-id="82c8c-134">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="82c8c-135">受限於 0-255 （0xff）的範圍， `\DDD`和`\x` escape 序列實際上是[ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout)字元集，因為這符合第一個 256 Unicode 程式碼點。</span><span class="sxs-lookup"><span data-stu-id="82c8c-135">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

<span data-ttu-id="82c8c-136">如果前面加上 @ 符號，常值就是逐字字串。</span><span class="sxs-lookup"><span data-stu-id="82c8c-136">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="82c8c-137">這表示會忽略任何逸出序列，不過，兩個引號字元會被視為一個引號字元。</span><span class="sxs-lookup"><span data-stu-id="82c8c-137">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

<span data-ttu-id="82c8c-138">此外，字串可以用三個引號括住。</span><span class="sxs-lookup"><span data-stu-id="82c8c-138">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="82c8c-139">在此情況下，會忽略所有的逸出序列，包括雙引號字元。</span><span class="sxs-lookup"><span data-stu-id="82c8c-139">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="82c8c-140">若要指定包含內嵌加上引號之字串的字串，您可以使用逐字字串或以三個引號括住的字串。</span><span class="sxs-lookup"><span data-stu-id="82c8c-140">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="82c8c-141">如果您使用逐字字串，您必須指定兩個引號字元來表示單一引號字元。</span><span class="sxs-lookup"><span data-stu-id="82c8c-141">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="82c8c-142">如果您使用三加引號的字串，您可以使用單引號字元，而不將它們剖析為字串的結尾。</span><span class="sxs-lookup"><span data-stu-id="82c8c-142">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="82c8c-143">當您使用包含內嵌引號的 XML 或其他結構時，這項技術會很有用。</span><span class="sxs-lookup"><span data-stu-id="82c8c-143">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="82c8c-144">在程式碼中，會接受具有分行符號的字串，而且分行符號會以逐字的方式轉譯為分行符號，除非反斜線字元是分行符號前的最後一個字元。</span><span class="sxs-lookup"><span data-stu-id="82c8c-144">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="82c8c-145">使用反斜線字元時，會忽略下一行的前置空白字元。</span><span class="sxs-lookup"><span data-stu-id="82c8c-145">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="82c8c-146">下列程式碼會產生具有`str1`值`"abc\ndef"`的字串，以及具有`str2`值`"abcdef"`的字串。</span><span class="sxs-lookup"><span data-stu-id="82c8c-146">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

<span data-ttu-id="82c8c-147">您可以使用類似陣列的語法來存取字串中的個別字元，如下所示。</span><span class="sxs-lookup"><span data-stu-id="82c8c-147">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="82c8c-148">輸出為 `b`。</span><span class="sxs-lookup"><span data-stu-id="82c8c-148">The output is `b`.</span></span>

<span data-ttu-id="82c8c-149">或者，您可以使用陣列配量語法來解壓縮子字串，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="82c8c-149">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="82c8c-150">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="82c8c-150">The output is as follows.</span></span>

```console
abc
def
```

<span data-ttu-id="82c8c-151">您可以依不帶正負號的位元組陣列來表示`byte[]`ASCII 字串，類型為。</span><span class="sxs-lookup"><span data-stu-id="82c8c-151">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="82c8c-152">您可以將尾碼`B`新增至字串常值，以表示它是 ASCII 字串。</span><span class="sxs-lookup"><span data-stu-id="82c8c-152">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="82c8c-153">搭配位元組陣列使用的 ASCII 字串常值支援與 Unicode 字串相同的轉義順序，但 Unicode 逸出序列除外。</span><span class="sxs-lookup"><span data-stu-id="82c8c-153">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="82c8c-154">字串運算子</span><span class="sxs-lookup"><span data-stu-id="82c8c-154">String Operators</span></span>

<span data-ttu-id="82c8c-155">有兩種方式可以串連字號串：使用`+`運算子或`^`使用運算子。</span><span class="sxs-lookup"><span data-stu-id="82c8c-155">There are two ways to concatenate strings: by using the `+` operator or by using the `^` operator.</span></span> <span data-ttu-id="82c8c-156">`+`運算子會維持與 .NET Framework 字串處理功能的相容性。</span><span class="sxs-lookup"><span data-stu-id="82c8c-156">The `+` operator maintains compatibility with the .NET Framework string handling features.</span></span>

<span data-ttu-id="82c8c-157">下列範例說明字串串連。</span><span class="sxs-lookup"><span data-stu-id="82c8c-157">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="82c8c-158">String 類別</span><span class="sxs-lookup"><span data-stu-id="82c8c-158">String Class</span></span>

<span data-ttu-id="82c8c-159">因為中F#的字串類型實際上是 .NET Framework `System.String` `System.String`類型，所以所有成員都可以使用。</span><span class="sxs-lookup"><span data-stu-id="82c8c-159">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="82c8c-160">這包括`+`運算子，用來串連字號串`Length` 、屬性和`Chars`屬性（property），這會以 Unicode 字元陣列的形式傳回字串。</span><span class="sxs-lookup"><span data-stu-id="82c8c-160">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="82c8c-161">如需字串的詳細資訊， `System.String`請參閱。</span><span class="sxs-lookup"><span data-stu-id="82c8c-161">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="82c8c-162">藉由使用`Chars`的`System.String`屬性，您可以藉由指定索引來存取字串中的個別字元，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="82c8c-162">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="82c8c-163">字串模組</span><span class="sxs-lookup"><span data-stu-id="82c8c-163">String Module</span></span>

<span data-ttu-id="82c8c-164">字串處理的其他功能會包含在`String` `FSharp.Core`命名空間的模組中。</span><span class="sxs-lookup"><span data-stu-id="82c8c-164">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="82c8c-165">如需詳細資訊，請參閱[Core. 字串模組](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d)。</span><span class="sxs-lookup"><span data-stu-id="82c8c-165">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="82c8c-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82c8c-166">See also</span></span>

- [<span data-ttu-id="82c8c-167">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="82c8c-167">F# Language Reference</span></span>](index.md)
