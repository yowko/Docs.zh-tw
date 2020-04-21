---
title: 字串
description: 瞭解 F# "字串"類型如何表示不可變文本作為 Unicode 字元序列。
ms.date: 07/05/2019
ms.openlocfilehash: 242a2cefa1cce8995090dddd1d1fd7181e0f5e0c
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739565"
---
# <a name="strings"></a><span data-ttu-id="a6026-103">字串</span><span class="sxs-lookup"><span data-stu-id="a6026-103">Strings</span></span>

> [!NOTE]
> <span data-ttu-id="a6026-104">本文中的 API 參考連結將帶您前往 MSDN。</span><span class="sxs-lookup"><span data-stu-id="a6026-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="a6026-105">docs.microsoft.com API 參考不完整。</span><span class="sxs-lookup"><span data-stu-id="a6026-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="a6026-106">該`string`類型表示不可變文本為 Unicode 字元序列。</span><span class="sxs-lookup"><span data-stu-id="a6026-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="a6026-107">`string` 是 `System.String` 在 .NET Framework 中的別名。</span><span class="sxs-lookup"><span data-stu-id="a6026-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="a6026-108">備註</span><span class="sxs-lookup"><span data-stu-id="a6026-108">Remarks</span></span>

<span data-ttu-id="a6026-109">字串文字由引號 (") 字元分隔。</span><span class="sxs-lookup"><span data-stu-id="a6026-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="a6026-110">反斜杠字元\\( ) 用於編碼某些特殊字元。</span><span class="sxs-lookup"><span data-stu-id="a6026-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="a6026-111">反斜杠與下一個字元一起被稱為*逸出序列*。</span><span class="sxs-lookup"><span data-stu-id="a6026-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="a6026-112">F# 字串文字中支援的轉義序列顯示在下表中。</span><span class="sxs-lookup"><span data-stu-id="a6026-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="a6026-113">字元</span><span class="sxs-lookup"><span data-stu-id="a6026-113">Character</span></span>|<span data-ttu-id="a6026-114">逸出序列</span><span class="sxs-lookup"><span data-stu-id="a6026-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="a6026-115">警示</span><span class="sxs-lookup"><span data-stu-id="a6026-115">Alert</span></span>|`\a`|
|<span data-ttu-id="a6026-116">退格鍵</span><span class="sxs-lookup"><span data-stu-id="a6026-116">Backspace</span></span>|`\b`|
|<span data-ttu-id="a6026-117">換頁字元</span><span class="sxs-lookup"><span data-stu-id="a6026-117">Form feed</span></span>|`\f`|
|<span data-ttu-id="a6026-118">新行字元</span><span class="sxs-lookup"><span data-stu-id="a6026-118">Newline</span></span>|`\n`|
|<span data-ttu-id="a6026-119">歸位字元</span><span class="sxs-lookup"><span data-stu-id="a6026-119">Carriage return</span></span>|`\r`|
|<span data-ttu-id="a6026-120">索引標籤</span><span class="sxs-lookup"><span data-stu-id="a6026-120">Tab</span></span>|`\t`|
|<span data-ttu-id="a6026-121">垂直 Tab 鍵</span><span class="sxs-lookup"><span data-stu-id="a6026-121">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="a6026-122">反斜線</span><span class="sxs-lookup"><span data-stu-id="a6026-122">Backslash</span></span>|`\\`|
|<span data-ttu-id="a6026-123">引號</span><span class="sxs-lookup"><span data-stu-id="a6026-123">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="a6026-124">單引號</span><span class="sxs-lookup"><span data-stu-id="a6026-124">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="a6026-125">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="a6026-125">Unicode character</span></span>|<span data-ttu-id="a6026-126">`\DDD`(其中`D`表示小數數位;範圍為 000 -`\231`255; 例如,= "\*")</span><span class="sxs-lookup"><span data-stu-id="a6026-126">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; for example, `\231` = "ç")</span></span>|
|<span data-ttu-id="a6026-127">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="a6026-127">Unicode character</span></span>|<span data-ttu-id="a6026-128">`\xHH`(其中`H`指示十六進位元;範圍為 00 - FF;例如,= `\xE7` "\*")</span><span class="sxs-lookup"><span data-stu-id="a6026-128">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; for example, `\xE7` = "ç")</span></span>|
|<span data-ttu-id="a6026-129">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="a6026-129">Unicode character</span></span>|<span data-ttu-id="a6026-130">`\uHHHH`(UTF-16)(其中`H`表示十六進位元;範圍為 0000 - FFFF; 例如,= `\u00E7` "\*")</span><span class="sxs-lookup"><span data-stu-id="a6026-130">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  for example, `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="a6026-131">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="a6026-131">Unicode character</span></span>|<span data-ttu-id="a6026-132">`\U00HHHHHH`(UTF-32)(其中`H`表示十六進位元;範圍為 000000 - 10FFFF; 例如,= `\U0001F47D` """)👽</span><span class="sxs-lookup"><span data-stu-id="a6026-132">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  for example, `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="a6026-133">`\DDD`轉義序列是十進制表示法,不像大多數其他語言那樣的八進位表示法。</span><span class="sxs-lookup"><span data-stu-id="a6026-133">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="a6026-134">因此,數位`8`和`9`有效,並且序列`\032`表示空格 (U+0020),而八進位表示法中的同一代碼`\040`點將是 。</span><span class="sxs-lookup"><span data-stu-id="a6026-134">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="a6026-135">被限制到 0 - 255 (0xFF)`\DDD``\x`的範圍, 和轉義序列實際上是[ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout)字元集, 因為它匹配前 256 個 Unicode 點。</span><span class="sxs-lookup"><span data-stu-id="a6026-135">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

## <a name="verbatim-strings"></a><span data-ttu-id="a6026-136">逐字串</span><span class="sxs-lookup"><span data-stu-id="a6026-136">Verbatim Strings</span></span>

<span data-ttu-id="a6026-137">如果前面有 + 符號,則文本是逐字字串。</span><span class="sxs-lookup"><span data-stu-id="a6026-137">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="a6026-138">這意味著忽略任何轉義序列,只不過兩個引號字元被解釋為一個引號字元。</span><span class="sxs-lookup"><span data-stu-id="a6026-138">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

## <a name="triple-quoted-strings"></a><span data-ttu-id="a6026-139">三重報價字串</span><span class="sxs-lookup"><span data-stu-id="a6026-139">Triple Quoted Strings</span></span>

<span data-ttu-id="a6026-140">此外,字串可以用三重引弧括起來。</span><span class="sxs-lookup"><span data-stu-id="a6026-140">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="a6026-141">在這種情況下,將忽略所有轉義序列,包括雙引號字元。</span><span class="sxs-lookup"><span data-stu-id="a6026-141">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="a6026-142">要指定包含嵌入引言字串的字串,可以使用逐字字串或三重引號字串。</span><span class="sxs-lookup"><span data-stu-id="a6026-142">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="a6026-143">如果使用逐字字串,則必須指定兩個引號字元以指示單個引號字元。</span><span class="sxs-lookup"><span data-stu-id="a6026-143">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="a6026-144">如果使用三重引號字串,則可以使用單個引號字元,而無需將它們解析為字串的末尾。</span><span class="sxs-lookup"><span data-stu-id="a6026-144">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="a6026-145">當您使用 XML 或其他包含嵌入引號的結構時,此方法非常有用。</span><span class="sxs-lookup"><span data-stu-id="a6026-145">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="a6026-146">在代碼中,接受具有換行符的字串,並且換行元從字面上解釋為換行符,除非反斜杠字元是換行符之前的最後一個字元。</span><span class="sxs-lookup"><span data-stu-id="a6026-146">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="a6026-147">使用反斜杠字元時,將忽略下一行的前導空格。</span><span class="sxs-lookup"><span data-stu-id="a6026-147">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="a6026-148">`str1`以下代碼產生具有值`"abc\ndef"`的字串和具有值`str2``"abcdef"`的字串。</span><span class="sxs-lookup"><span data-stu-id="a6026-148">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a><span data-ttu-id="a6026-149">字串索引和切片</span><span class="sxs-lookup"><span data-stu-id="a6026-149">String Indexing and Slicing</span></span>

<span data-ttu-id="a6026-150">可以使用類似於陣列的語法訪問字串中的單個字元,如下所示。</span><span class="sxs-lookup"><span data-stu-id="a6026-150">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="a6026-151">輸出為 `b`。</span><span class="sxs-lookup"><span data-stu-id="a6026-151">The output is `b`.</span></span>

<span data-ttu-id="a6026-152">或者,您可以使用陣列切片語法提取子字串,如以下代碼所示。</span><span class="sxs-lookup"><span data-stu-id="a6026-152">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="a6026-153">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="a6026-153">The output is as follows.</span></span>

```console
abc
def
```

<span data-ttu-id="a6026-154">您可以按未簽署的陣列表示 ASCII 字串,類型`byte[]`為 。</span><span class="sxs-lookup"><span data-stu-id="a6026-154">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="a6026-155">將後綴`B`添加到字串文字,以指示它是 ASCII 字串。</span><span class="sxs-lookup"><span data-stu-id="a6026-155">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="a6026-156">與位元陣列一起使用的 ASCII 字串文字支援與 Unicode 字串相同的轉義序列,Unicode 轉義序列除外。</span><span class="sxs-lookup"><span data-stu-id="a6026-156">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="a6026-157">字串運算子</span><span class="sxs-lookup"><span data-stu-id="a6026-157">String Operators</span></span>

<span data-ttu-id="a6026-158">該`+`運算元可用於串聯字串,保持與 .NET 框架字串處理功能的相容性。</span><span class="sxs-lookup"><span data-stu-id="a6026-158">The `+` operator can be used to concatenate strings, maintaining compatibility with the .NET Framework string handling features.</span></span> <span data-ttu-id="a6026-159">下面的示例演示了字串串聯。</span><span class="sxs-lookup"><span data-stu-id="a6026-159">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="a6026-160">字串類別</span><span class="sxs-lookup"><span data-stu-id="a6026-160">String Class</span></span>

<span data-ttu-id="a6026-161">由於 F# 中的字串類型實際上是`System.String`.NET`System.String`框架類型, 因此所有成員都可用。</span><span class="sxs-lookup"><span data-stu-id="a6026-161">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="a6026-162">這包括`+`運算子,該運算元用於串聯字串、`Length`屬性和`Chars`屬性,後者將字串作為 Unicode 字元的陣列返回。</span><span class="sxs-lookup"><span data-stu-id="a6026-162">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="a6026-163">有關字串的詳細資訊,請參閱`System.String`。</span><span class="sxs-lookup"><span data-stu-id="a6026-163">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="a6026-164">通過使用`Chars``System.String`屬性 ,可以通過指定索引來訪問字串中的單個字元,如下代碼所示。</span><span class="sxs-lookup"><span data-stu-id="a6026-164">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="a6026-165">字串模組</span><span class="sxs-lookup"><span data-stu-id="a6026-165">String Module</span></span>

<span data-ttu-id="a6026-166">`FSharp.Core`命名空間中的`String`模組中包括字串處理的其他功能。</span><span class="sxs-lookup"><span data-stu-id="a6026-166">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="a6026-167">有關詳細資訊,請參閱[Core.String 模組](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d)。</span><span class="sxs-lookup"><span data-stu-id="a6026-167">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="a6026-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6026-168">See also</span></span>

- [<span data-ttu-id="a6026-169">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="a6026-169">F# Language Reference</span></span>](index.md)
