---
title: 字串
description: 瞭解「字串F# 」類型如何以 Unicode 字元序清單示不可變的文字。
ms.date: 07/05/2019
ms.openlocfilehash: 002de464d09a49b6161608db6e46c619369f5ceb
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452814"
---
# <a name="strings"></a><span data-ttu-id="6eabf-103">字串</span><span class="sxs-lookup"><span data-stu-id="6eabf-103">Strings</span></span>

> [!NOTE]
> <span data-ttu-id="6eabf-104">本文中的 API 參考連結將帶您前往 MSDN。</span><span class="sxs-lookup"><span data-stu-id="6eabf-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="6eabf-105">docs.microsoft.com API 參考不完整。</span><span class="sxs-lookup"><span data-stu-id="6eabf-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="6eabf-106">`string` 類型會以 Unicode 字元序列的形式來表示不可變的文字。</span><span class="sxs-lookup"><span data-stu-id="6eabf-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="6eabf-107">`string` 是 `System.String` 在 .NET Framework 中的別名。</span><span class="sxs-lookup"><span data-stu-id="6eabf-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="6eabf-108">備註</span><span class="sxs-lookup"><span data-stu-id="6eabf-108">Remarks</span></span>

<span data-ttu-id="6eabf-109">字串常值是以引號（"）字元分隔。</span><span class="sxs-lookup"><span data-stu-id="6eabf-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="6eabf-110">反斜線字元（\\）是用來編碼某些特殊字元。</span><span class="sxs-lookup"><span data-stu-id="6eabf-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="6eabf-111">反斜線和下一個字元一起稱為「*逸出序列*」。</span><span class="sxs-lookup"><span data-stu-id="6eabf-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="6eabf-112">下表顯示F#字串常值中支援的 Escape 序列。</span><span class="sxs-lookup"><span data-stu-id="6eabf-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="6eabf-113">字元</span><span class="sxs-lookup"><span data-stu-id="6eabf-113">Character</span></span>|<span data-ttu-id="6eabf-114">逸出序列</span><span class="sxs-lookup"><span data-stu-id="6eabf-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="6eabf-115">警示</span><span class="sxs-lookup"><span data-stu-id="6eabf-115">Alert</span></span>|`\a`|
|<span data-ttu-id="6eabf-116">退格鍵</span><span class="sxs-lookup"><span data-stu-id="6eabf-116">Backspace</span></span>|`\b`|
|<span data-ttu-id="6eabf-117">換頁字元</span><span class="sxs-lookup"><span data-stu-id="6eabf-117">Form feed</span></span>|`\f`|
|<span data-ttu-id="6eabf-118">新行字元</span><span class="sxs-lookup"><span data-stu-id="6eabf-118">Newline</span></span>|`\n`|
|<span data-ttu-id="6eabf-119">歸位字元</span><span class="sxs-lookup"><span data-stu-id="6eabf-119">Carriage return</span></span>|`\r`|
|<span data-ttu-id="6eabf-120">索引標籤</span><span class="sxs-lookup"><span data-stu-id="6eabf-120">Tab</span></span>|`\t`|
|<span data-ttu-id="6eabf-121">垂直 Tab 鍵</span><span class="sxs-lookup"><span data-stu-id="6eabf-121">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="6eabf-122">反斜線</span><span class="sxs-lookup"><span data-stu-id="6eabf-122">Backslash</span></span>|`\\`|
|<span data-ttu-id="6eabf-123">引號</span><span class="sxs-lookup"><span data-stu-id="6eabf-123">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="6eabf-124">省略號</span><span class="sxs-lookup"><span data-stu-id="6eabf-124">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="6eabf-125">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="6eabf-125">Unicode character</span></span>|<span data-ttu-id="6eabf-126">`\DDD` （其中 `D` 表示十進位數; 範圍為 000-255; 例如，`\231` = "ç"）</span><span class="sxs-lookup"><span data-stu-id="6eabf-126">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; for example, `\231` = "ç")</span></span>|
|<span data-ttu-id="6eabf-127">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="6eabf-127">Unicode character</span></span>|<span data-ttu-id="6eabf-128">`\xHH` （其中 `H` 表示十六進位數位; 00-FF 的範圍，例如，`\xE7` = "ç"）</span><span class="sxs-lookup"><span data-stu-id="6eabf-128">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; for example, `\xE7` = "ç")</span></span>|
|<span data-ttu-id="6eabf-129">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="6eabf-129">Unicode character</span></span>|<span data-ttu-id="6eabf-130">`\uHHHH` （UTF-16）（其中 `H` 表示十六進位數位; 0000-FFFF 的範圍; 例如，`\u00E7` = "ç"）</span><span class="sxs-lookup"><span data-stu-id="6eabf-130">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  for example, `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="6eabf-131">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="6eabf-131">Unicode character</span></span>|<span data-ttu-id="6eabf-132">`\U00HHHHHH` （UTF-32）（其中 `H` 表示十六進位數位; 000000-10FFFF 且的範圍; 例如，`\U0001F47D` = "👽"）</span><span class="sxs-lookup"><span data-stu-id="6eabf-132">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  for example, `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="6eabf-133">`\DDD` 的逸出序列是十進位標記法，而不是像大部分其他語言中的八進位標記法。</span><span class="sxs-lookup"><span data-stu-id="6eabf-133">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="6eabf-134">因此，`8` 和 `9` 的數位是有效的，而 `\032` 的序列則代表空格（U + 0020），而八進位標記法中的相同程式碼點也會 `\040`。</span><span class="sxs-lookup"><span data-stu-id="6eabf-134">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="6eabf-135">受限於 0-255 （0xFF）的範圍，`\DDD` 和 `\x` 的逸出序列實際上是[ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout)字元集，因為這符合第一個 256 Unicode 程式碼點。</span><span class="sxs-lookup"><span data-stu-id="6eabf-135">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

## <a name="verbatim-strings"></a><span data-ttu-id="6eabf-136">逐字字串</span><span class="sxs-lookup"><span data-stu-id="6eabf-136">Verbatim Strings</span></span>

<span data-ttu-id="6eabf-137">如果前面加上 @ 符號，常值就是逐字字串。</span><span class="sxs-lookup"><span data-stu-id="6eabf-137">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="6eabf-138">這表示會忽略任何逸出序列，不過，兩個引號字元會被視為一個引號字元。</span><span class="sxs-lookup"><span data-stu-id="6eabf-138">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

## <a name="triple-quoted-strings"></a><span data-ttu-id="6eabf-139">三加引號的字串</span><span class="sxs-lookup"><span data-stu-id="6eabf-139">Triple Quoted Strings</span></span>

<span data-ttu-id="6eabf-140">此外，字串可以用三個引號括住。</span><span class="sxs-lookup"><span data-stu-id="6eabf-140">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="6eabf-141">在此情況下，會忽略所有的逸出序列，包括雙引號字元。</span><span class="sxs-lookup"><span data-stu-id="6eabf-141">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="6eabf-142">若要指定包含內嵌加上引號之字串的字串，您可以使用逐字字串或以三個引號括住的字串。</span><span class="sxs-lookup"><span data-stu-id="6eabf-142">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="6eabf-143">如果您使用逐字字串，您必須指定兩個引號字元來表示單一引號字元。</span><span class="sxs-lookup"><span data-stu-id="6eabf-143">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="6eabf-144">如果您使用三加引號的字串，您可以使用單引號字元，而不將它們剖析為字串的結尾。</span><span class="sxs-lookup"><span data-stu-id="6eabf-144">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="6eabf-145">當您使用包含內嵌引號的 XML 或其他結構時，這項技術會很有用。</span><span class="sxs-lookup"><span data-stu-id="6eabf-145">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="6eabf-146">在程式碼中，會接受具有分行符號的字串，而且分行符號會以逐字的方式轉譯為分行符號，除非反斜線字元是分行符號前的最後一個字元。</span><span class="sxs-lookup"><span data-stu-id="6eabf-146">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="6eabf-147">使用反斜線字元時，會忽略下一行的前置空白字元。</span><span class="sxs-lookup"><span data-stu-id="6eabf-147">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="6eabf-148">下列程式碼會產生具有值 `"abc\ndef"` 的字串 `str1`，以及具有值 `"abcdef"`的字串 `str2`。</span><span class="sxs-lookup"><span data-stu-id="6eabf-148">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a><span data-ttu-id="6eabf-149">字串索引和切割</span><span class="sxs-lookup"><span data-stu-id="6eabf-149">String Indexing and Slicing</span></span>

<span data-ttu-id="6eabf-150">您可以使用類似陣列的語法來存取字串中的個別字元，如下所示。</span><span class="sxs-lookup"><span data-stu-id="6eabf-150">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="6eabf-151">輸出為 `b`。</span><span class="sxs-lookup"><span data-stu-id="6eabf-151">The output is `b`.</span></span>

<span data-ttu-id="6eabf-152">或者，您可以使用陣列配量語法來解壓縮子字串，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="6eabf-152">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="6eabf-153">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="6eabf-153">The output is as follows.</span></span>

```console
abc
def
```

<span data-ttu-id="6eabf-154">您可以依不帶正負號的位元組陣列來表示 ASCII 字串，請輸入 `byte[]`。</span><span class="sxs-lookup"><span data-stu-id="6eabf-154">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="6eabf-155">您可以將尾碼 `B` 新增至字串常值，以表示它是 ASCII 字串。</span><span class="sxs-lookup"><span data-stu-id="6eabf-155">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="6eabf-156">搭配位元組陣列使用的 ASCII 字串常值支援與 Unicode 字串相同的轉義順序，但 Unicode 逸出序列除外。</span><span class="sxs-lookup"><span data-stu-id="6eabf-156">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="6eabf-157">字串運算子</span><span class="sxs-lookup"><span data-stu-id="6eabf-157">String Operators</span></span>

<span data-ttu-id="6eabf-158">串連字號串的方法有兩種：使用 `+` 運算子，或使用 `^` 運算子。</span><span class="sxs-lookup"><span data-stu-id="6eabf-158">There are two ways to concatenate strings: by using the `+` operator or by using the `^` operator.</span></span> <span data-ttu-id="6eabf-159">`+` 運算子會維持與 .NET Framework 字串處理功能的相容性。</span><span class="sxs-lookup"><span data-stu-id="6eabf-159">The `+` operator maintains compatibility with the .NET Framework string handling features.</span></span>

<span data-ttu-id="6eabf-160">下列範例說明字串串連。</span><span class="sxs-lookup"><span data-stu-id="6eabf-160">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="6eabf-161">String 類別</span><span class="sxs-lookup"><span data-stu-id="6eabf-161">String Class</span></span>

<span data-ttu-id="6eabf-162">因為中F#的字串類型實際上是 .NET Framework `System.String` 類型，所以所有 `System.String` 成員都可以使用。</span><span class="sxs-lookup"><span data-stu-id="6eabf-162">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="6eabf-163">這包括 `+` 運算子，用來串連字號串、`Length` 屬性和 `Chars` 屬性，這會傳回字串做為 Unicode 字元陣列。</span><span class="sxs-lookup"><span data-stu-id="6eabf-163">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="6eabf-164">如需有關字串的詳細資訊，請參閱 `System.String`。</span><span class="sxs-lookup"><span data-stu-id="6eabf-164">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="6eabf-165">藉由使用 `System.String`的 `Chars` 屬性，您可以藉由指定索引來存取字串中的個別字元，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="6eabf-165">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="6eabf-166">字串模組</span><span class="sxs-lookup"><span data-stu-id="6eabf-166">String Module</span></span>

<span data-ttu-id="6eabf-167">字串處理的其他功能會包含在 `FSharp.Core` 命名空間的 `String` 模組中。</span><span class="sxs-lookup"><span data-stu-id="6eabf-167">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="6eabf-168">如需詳細資訊，請參閱[Core. 字串模組](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d)。</span><span class="sxs-lookup"><span data-stu-id="6eabf-168">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="6eabf-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6eabf-169">See also</span></span>

- [<span data-ttu-id="6eabf-170">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="6eabf-170">F# Language Reference</span></span>](index.md)
