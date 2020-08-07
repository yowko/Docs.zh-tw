---
title: 字串
description: "瞭解 F # ' string ' 類型如何以 Unicode 字元序列來表示不可變的文字。"
ms.date: 07/05/2019
ms.openlocfilehash: 67a6506b4b8c479da1022c069a7f53402f904b4d
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855409"
---
# <a name="strings"></a><span data-ttu-id="f9ffa-103">字串</span><span class="sxs-lookup"><span data-stu-id="f9ffa-103">Strings</span></span>

<span data-ttu-id="f9ffa-104">`string`類型以 Unicode 字元序清單示不可變的文字。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-104">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="f9ffa-105">`string` 是 `System.String` 在 .NET 中的別名。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-105">`string` is an alias for `System.String` in .NET.</span></span>

> [!NOTE]
> <span data-ttu-id="f9ffa-106">F # 的 docs.microsoft.com API 參考不完整。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-106">The docs.microsoft.com API reference for F# is not complete.</span></span> <span data-ttu-id="f9ffa-107">如果您遇到任何中斷的連結，請改為參考[F # 核心程式庫檔](https://fsharp.github.io/fsharp-core-docs/)。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-107">If you encounter any broken links, reference [F# Core Library Documentation](https://fsharp.github.io/fsharp-core-docs/) instead.</span></span>

## <a name="remarks"></a><span data-ttu-id="f9ffa-108">備註</span><span class="sxs-lookup"><span data-stu-id="f9ffa-108">Remarks</span></span>

<span data-ttu-id="f9ffa-109">字串常值是以引號分隔 ( ") 字元。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="f9ffa-110">反斜線字元 ( \\ ) 用來編碼某些特殊字元。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="f9ffa-111">反斜線和下一個字元一起稱為「*逸出序列*」。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="f9ffa-112">下表顯示 F # 字串常值中支援的 Escape 序列。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="f9ffa-113">字元</span><span class="sxs-lookup"><span data-stu-id="f9ffa-113">Character</span></span>|<span data-ttu-id="f9ffa-114">逸出序列</span><span class="sxs-lookup"><span data-stu-id="f9ffa-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="f9ffa-115">警示</span><span class="sxs-lookup"><span data-stu-id="f9ffa-115">Alert</span></span>|`\a`|
|<span data-ttu-id="f9ffa-116">退格鍵</span><span class="sxs-lookup"><span data-stu-id="f9ffa-116">Backspace</span></span>|`\b`|
|<span data-ttu-id="f9ffa-117">換頁字元</span><span class="sxs-lookup"><span data-stu-id="f9ffa-117">Form feed</span></span>|`\f`|
|<span data-ttu-id="f9ffa-118">新行字元</span><span class="sxs-lookup"><span data-stu-id="f9ffa-118">Newline</span></span>|`\n`|
|<span data-ttu-id="f9ffa-119">歸位字元</span><span class="sxs-lookup"><span data-stu-id="f9ffa-119">Carriage return</span></span>|`\r`|
|<span data-ttu-id="f9ffa-120">索引標籤</span><span class="sxs-lookup"><span data-stu-id="f9ffa-120">Tab</span></span>|`\t`|
|<span data-ttu-id="f9ffa-121">垂直 Tab 鍵</span><span class="sxs-lookup"><span data-stu-id="f9ffa-121">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="f9ffa-122">反斜線</span><span class="sxs-lookup"><span data-stu-id="f9ffa-122">Backslash</span></span>|`\\`|
|<span data-ttu-id="f9ffa-123">引號</span><span class="sxs-lookup"><span data-stu-id="f9ffa-123">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="f9ffa-124">單引號</span><span class="sxs-lookup"><span data-stu-id="f9ffa-124">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="f9ffa-125">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="f9ffa-125">Unicode character</span></span>|<span data-ttu-id="f9ffa-126">`\DDD` (，其中 `D` 表示十進位數; 範圍為 000-255，例如 `\231` = "ç" ) </span><span class="sxs-lookup"><span data-stu-id="f9ffa-126">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; for example, `\231` = "ç")</span></span>|
|<span data-ttu-id="f9ffa-127">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="f9ffa-127">Unicode character</span></span>|<span data-ttu-id="f9ffa-128">`\xHH` (，其中 `H` 表示十六進位數位; 00-FF 的範圍，例如 `\xE7` = "ç" ) </span><span class="sxs-lookup"><span data-stu-id="f9ffa-128">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; for example, `\xE7` = "ç")</span></span>|
|<span data-ttu-id="f9ffa-129">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="f9ffa-129">Unicode character</span></span>|<span data-ttu-id="f9ffa-130">`\uHHHH` (UTF-16)  (，其中 `H` 表示十六進位數位; 0000-FFFF 的範圍; 例如， `\u00E7` = "ç" ) </span><span class="sxs-lookup"><span data-stu-id="f9ffa-130">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  for example, `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="f9ffa-131">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="f9ffa-131">Unicode character</span></span>|<span data-ttu-id="f9ffa-132">`\U00HHHHHH` (UTF-32)  (，其中 `H` 表示十六進位數位; 000000-10ffff 且的範圍; 例如， `\U0001F47D` = " 👽 " ) </span><span class="sxs-lookup"><span data-stu-id="f9ffa-132">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  for example, `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="f9ffa-133">`\DDD`Escape 序列是十進位標記法，而非八進位標記法，就像大多數其他語言一樣。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-133">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="f9ffa-134">因此，數位 `8` 和 `9` 有效，而的序列 `\032` 表示 (U + 0020) 的空格，而八進位標記法中的相同程式碼點則為 `\040` 。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-134">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="f9ffa-135">受限於 0-255 (0xFF) 的範圍， `\DDD` 和 `\x` escape 序列實際上是[ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout)字元集，因為這符合第一個 256 Unicode 程式碼點。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-135">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

## <a name="verbatim-strings"></a><span data-ttu-id="f9ffa-136">逐字字串</span><span class="sxs-lookup"><span data-stu-id="f9ffa-136">Verbatim Strings</span></span>

<span data-ttu-id="f9ffa-137">如果前面加上 @ 符號，常值就是逐字字串。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-137">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="f9ffa-138">這表示會忽略任何逸出序列，不過，兩個引號字元會被視為一個引號字元。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-138">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

## <a name="triple-quoted-strings"></a><span data-ttu-id="f9ffa-139">三加引號的字串</span><span class="sxs-lookup"><span data-stu-id="f9ffa-139">Triple Quoted Strings</span></span>

<span data-ttu-id="f9ffa-140">此外，字串可以用三個引號括住。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-140">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="f9ffa-141">在此情況下，會忽略所有的逸出序列，包括雙引號字元。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-141">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="f9ffa-142">若要指定包含內嵌加上引號之字串的字串，您可以使用逐字字串或以三個引號括住的字串。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-142">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="f9ffa-143">如果您使用逐字字串，您必須指定兩個引號字元來表示單一引號字元。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-143">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="f9ffa-144">如果您使用三加引號的字串，您可以使用單引號字元，而不將它們剖析為字串的結尾。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-144">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="f9ffa-145">當您使用包含內嵌引號的 XML 或其他結構時，這項技術會很有用。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-145">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="f9ffa-146">在程式碼中，會接受具有分行符號的字串，而且分行符號會以逐字的方式轉譯為分行符號，除非反斜線字元是分行符號前的最後一個字元。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-146">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="f9ffa-147">使用反斜線字元時，會忽略下一行的前置空白字元。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-147">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="f9ffa-148">下列程式碼會產生具有值的字串， `str1` `"abc\ndef"` 以及 `str2` 具有值的字串 `"abcdef"` 。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-148">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a><span data-ttu-id="f9ffa-149">字串索引和切割</span><span class="sxs-lookup"><span data-stu-id="f9ffa-149">String Indexing and Slicing</span></span>

<span data-ttu-id="f9ffa-150">您可以使用類似陣列的語法來存取字串中的個別字元，如下所示。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-150">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="f9ffa-151">輸出為 `b`。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-151">The output is `b`.</span></span>

<span data-ttu-id="f9ffa-152">或者，您可以使用陣列配量語法來解壓縮子字串，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-152">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="f9ffa-153">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-153">The output is as follows.</span></span>

```console
abc
def
```

<span data-ttu-id="f9ffa-154">您可以依不帶正負號的位元組陣列來表示 ASCII 字串，類型為 `byte[]` 。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-154">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="f9ffa-155">您可以將尾碼新增 `B` 至字串常值，以表示它是 ASCII 字串。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-155">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="f9ffa-156">搭配位元組陣列使用的 ASCII 字串常值支援與 Unicode 字串相同的轉義順序，但 Unicode 逸出序列除外。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-156">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="f9ffa-157">字串運算子</span><span class="sxs-lookup"><span data-stu-id="f9ffa-157">String Operators</span></span>

<span data-ttu-id="f9ffa-158">`+`運算子可以用來串連字號串，並維持與 .NET Framework 字串處理功能的相容性。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-158">The `+` operator can be used to concatenate strings, maintaining compatibility with the .NET Framework string handling features.</span></span> <span data-ttu-id="f9ffa-159">下列範例說明字串串連。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-159">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="f9ffa-160">String 類別</span><span class="sxs-lookup"><span data-stu-id="f9ffa-160">String Class</span></span>

<span data-ttu-id="f9ffa-161">因為 F # 中的字串類型實際上是 .NET Framework `System.String` 類型，所以所有 `System.String` 成員都可以使用。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-161">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="f9ffa-162">這包括 `+` 運算子，用來串連字號串、 `Length` 屬性和 `Chars` 屬性（property），這會以 Unicode 字元陣列的形式傳回字串。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-162">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="f9ffa-163">如需字串的詳細資訊，請參閱 `System.String` 。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-163">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="f9ffa-164">藉由使用的 `Chars` 屬性 `System.String` ，您可以藉由指定索引來存取字串中的個別字元，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-164">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="f9ffa-165">字串模組</span><span class="sxs-lookup"><span data-stu-id="f9ffa-165">String Module</span></span>

<span data-ttu-id="f9ffa-166">字串處理的其他功能會包含在 `String` 命名空間的模組中 `FSharp.Core` 。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-166">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="f9ffa-167">如需詳細資訊，請參閱[Core. 字串模組](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d)。</span><span class="sxs-lookup"><span data-stu-id="f9ffa-167">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="f9ffa-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9ffa-168">See also</span></span>

- [<span data-ttu-id="f9ffa-169">F # 語言參考</span><span class="sxs-lookup"><span data-stu-id="f9ffa-169">F# Language Reference</span></span>](index.md)
