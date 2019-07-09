---
title: 字串
description: 了解如何F#'string' 類型以一連串的 Unicode 字元表示不可變的文字。
ms.date: 07/05/2019
ms.openlocfilehash: ec895723cc6d21a701a27b5d70d053bb681ce2b3
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67660602"
---
# <a name="strings"></a><span data-ttu-id="ef8f1-103">字串</span><span class="sxs-lookup"><span data-stu-id="ef8f1-103">Strings</span></span>

> [!NOTE]
> <span data-ttu-id="ef8f1-104">本文中的 API 參考連結將帶您前往 MSDN。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="ef8f1-105">docs.microsoft.com API 參考不完整。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="ef8f1-106">`string`類型以一連串的 Unicode 字元表示不可變的文字。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="ef8f1-107">`string` 是 `System.String` 在 .NET Framework 中的別名。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="ef8f1-108">備註</span><span class="sxs-lookup"><span data-stu-id="ef8f1-108">Remarks</span></span>

<span data-ttu-id="ef8f1-109">字串常值是以引號 （"） 字元分隔。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="ef8f1-110">反斜線字元 ( \\ ) 來編碼某些特殊字元。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="ef8f1-111">反斜線和放在一起的下一個字元稱為*逸出序列*。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="ef8f1-112">逸出序列中支援F#字串常值會顯示下表中。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="ef8f1-113">字元</span><span class="sxs-lookup"><span data-stu-id="ef8f1-113">Character</span></span>|<span data-ttu-id="ef8f1-114">逸出序列</span><span class="sxs-lookup"><span data-stu-id="ef8f1-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="ef8f1-115">警示</span><span class="sxs-lookup"><span data-stu-id="ef8f1-115">Alert</span></span>|`\a`|
|<span data-ttu-id="ef8f1-116">退格鍵</span><span class="sxs-lookup"><span data-stu-id="ef8f1-116">Backspace</span></span>|`\b`|
|<span data-ttu-id="ef8f1-117">換頁字元</span><span class="sxs-lookup"><span data-stu-id="ef8f1-117">Form feed</span></span>|`\f`|
|<span data-ttu-id="ef8f1-118">新行字元</span><span class="sxs-lookup"><span data-stu-id="ef8f1-118">Newline</span></span>|`\n`|
|<span data-ttu-id="ef8f1-119">歸位字元</span><span class="sxs-lookup"><span data-stu-id="ef8f1-119">Carriage return</span></span>|`\r`|
|<span data-ttu-id="ef8f1-120">索引標籤</span><span class="sxs-lookup"><span data-stu-id="ef8f1-120">Tab</span></span>|`\t`|
|<span data-ttu-id="ef8f1-121">垂直 Tab</span><span class="sxs-lookup"><span data-stu-id="ef8f1-121">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="ef8f1-122">反斜線</span><span class="sxs-lookup"><span data-stu-id="ef8f1-122">Backslash</span></span>|`\\`|
|<span data-ttu-id="ef8f1-123">引號</span><span class="sxs-lookup"><span data-stu-id="ef8f1-123">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="ef8f1-124">所有格符號</span><span class="sxs-lookup"><span data-stu-id="ef8f1-124">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="ef8f1-125">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="ef8f1-125">Unicode character</span></span>|<span data-ttu-id="ef8f1-126">`\DDD` (其中`D`表示十進位數字，範圍的 000-255，例如`\231`="ç")</span><span class="sxs-lookup"><span data-stu-id="ef8f1-126">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; for example, `\231` = "ç")</span></span>|
|<span data-ttu-id="ef8f1-127">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="ef8f1-127">Unicode character</span></span>|<span data-ttu-id="ef8f1-128">`\xHH` (其中`H`表示的十六進位數字，範圍為 00-FF; 比方說， `\xE7` ="ç")</span><span class="sxs-lookup"><span data-stu-id="ef8f1-128">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; for example, `\xE7` = "ç")</span></span>|
|<span data-ttu-id="ef8f1-129">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="ef8f1-129">Unicode character</span></span>|<span data-ttu-id="ef8f1-130">`\uHHHH` (UTF-16)(其中`H`表示的十六進位數字; 0000-FFFF; 的範圍 比方說， `\u00E7` ="ç")</span><span class="sxs-lookup"><span data-stu-id="ef8f1-130">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  for example, `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="ef8f1-131">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="ef8f1-131">Unicode character</span></span>|<span data-ttu-id="ef8f1-132">`\U00HHHHHH` (UTF-32)(其中`H`表示的十六進位數字，範圍是 000000-10ffff 且; 例如， `\U0001F47D` ="👽")</span><span class="sxs-lookup"><span data-stu-id="ef8f1-132">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  for example, `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="ef8f1-133">`\DDD`逸出序列是十進位表示法，而不是八進位的標記法類似大多數其他語言中。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-133">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="ef8f1-134">因此，數字`8`並`9`有效，以及一系列`\032`代表空格 (u+0020)，而該相同的字碼指標，八進位標記法會`\040`。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-134">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="ef8f1-135">正在受限於範圍介於 0-255 (0xFF)，`\DDD`並`\x`逸出序列都是有效[ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout)字元集，則為，由於符合的前 256 個 Unicode 字碼指標。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-135">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

<span data-ttu-id="ef8f1-136">如果前面加上 @ 符號，此常值是逐字字串。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-136">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="ef8f1-137">這表示，則會忽略任何逸出序列，不同之處在於兩個引號字元視為一個引號字元。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-137">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

<span data-ttu-id="ef8f1-138">此外，可能以三引號括住字串。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-138">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="ef8f1-139">在此情況下，會忽略所有逸出序列，包括雙引號字元。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-139">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="ef8f1-140">若要指定包含內嵌字串加上引號的字串，您可以使用逐字字串或三重物件加上引號的字串。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-140">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="ef8f1-141">如果您使用逐字字串時，您必須指定兩個引號字元來表示一個單引號字元。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-141">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="ef8f1-142">如果您使用三重物件加上引號的字串，您可以使用單引號字元沒有它們正在剖析為字串的結尾。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-142">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="ef8f1-143">當您使用 XML 或其他結構包含內嵌的引號，則這個方法就很有用。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-143">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="ef8f1-144">程式碼中，接受已換行的字串，並換行符號會解譯為常值為換行符號，除非反斜線字元換行之前的最後一個字元。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-144">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="ef8f1-145">使用反斜線字元時，會忽略在下一行的前置空白字元。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-145">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="ef8f1-146">下列程式碼產生的字串`str1`具有值`"abc\ndef"`和字串`str2`具有值`"abcdef"`。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-146">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

<span data-ttu-id="ef8f1-147">您可以存取個別字元在字串中的使用類似陣列的語法，如下所示。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-147">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="ef8f1-148">輸出為 `b`。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-148">The output is `b`.</span></span>

<span data-ttu-id="ef8f1-149">或者，您可以使用陣列配量語法，來擷取子字串，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-149">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="ef8f1-150">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-150">The output is as follows.</span></span>

```
abc
def
```

<span data-ttu-id="ef8f1-151">您可以不帶正負號位元組，型別陣列表示 ASCII 字串`byte[]`。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-151">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="ef8f1-152">新增後置詞`B`為字串常值以指出它是 ASCII 字串。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-152">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="ef8f1-153">ASCII 字串常值的位元組陣列搭配使用支援相同逸出序列為 Unicode 字串，除了 Unicode 逸出序列。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-153">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="ef8f1-154">字串運算子</span><span class="sxs-lookup"><span data-stu-id="ef8f1-154">String Operators</span></span>

<span data-ttu-id="ef8f1-155">有兩種方式來串連字串： 使用`+`運算子或使用`^`運算子。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-155">There are two ways to concatenate strings: by using the `+` operator or by using the `^` operator.</span></span> <span data-ttu-id="ef8f1-156">`+`運算子會維護與.NET Framework 的字串處理功能的相容性。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-156">The `+` operator maintains compatibility with the .NET Framework string handling features.</span></span>

<span data-ttu-id="ef8f1-157">下列範例說明字串串連。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-157">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="ef8f1-158">字串類別</span><span class="sxs-lookup"><span data-stu-id="ef8f1-158">String Class</span></span>

<span data-ttu-id="ef8f1-159">因為字串類型在F#是實際的.NET Framework`System.String`類型，所有`System.String`成員都可以使用。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-159">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="ef8f1-160">這包括`+`運算子，用來串連字串，就`Length`屬性，而`Chars`屬性，會傳回字串的 Unicode 字元陣列。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-160">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="ef8f1-161">如需字串的詳細資訊，請參閱`System.String`。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-161">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="ef8f1-162">藉由使用`Chars`屬性`System.String`，您可以存取個別字元在字串中的指定的索引，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-162">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="ef8f1-163">字串模組</span><span class="sxs-lookup"><span data-stu-id="ef8f1-163">String Module</span></span>

<span data-ttu-id="ef8f1-164">字串處理的其他功能包含在`String`中的模組`FSharp.Core`命名空間。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-164">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="ef8f1-165">如需詳細資訊，請參閱 < [Core.String 模組](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d)。</span><span class="sxs-lookup"><span data-stu-id="ef8f1-165">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="ef8f1-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef8f1-166">See also</span></span>

- [<span data-ttu-id="ef8f1-167">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="ef8f1-167">F# Language Reference</span></span>](index.md)
