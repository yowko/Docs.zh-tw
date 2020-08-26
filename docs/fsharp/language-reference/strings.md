---
title: 字串
description: "瞭解 F # ' string ' 類型如何將不可變的文字表示為 Unicode 字元序列。"
ms.date: 08/15/2020
ms.openlocfilehash: f6ec36feeb197bf785c702e7b626cf5cf80696ab
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812207"
---
# <a name="strings"></a><span data-ttu-id="53c7f-103">字串</span><span class="sxs-lookup"><span data-stu-id="53c7f-103">Strings</span></span>

<span data-ttu-id="53c7f-104">型別會將 `string` 不可變的文字表示為 Unicode 字元序列。</span><span class="sxs-lookup"><span data-stu-id="53c7f-104">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="53c7f-105">`string` 是 `System.String` 在 .NET 中的別名。</span><span class="sxs-lookup"><span data-stu-id="53c7f-105">`string` is an alias for `System.String` in .NET.</span></span>

## <a name="remarks"></a><span data-ttu-id="53c7f-106">備註</span><span class="sxs-lookup"><span data-stu-id="53c7f-106">Remarks</span></span>

<span data-ttu-id="53c7f-107">字串常值是以引號 ( ") 字元分隔。</span><span class="sxs-lookup"><span data-stu-id="53c7f-107">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="53c7f-108"> ( ) 的反斜線字元 \\ 用來編碼某些特殊字元。</span><span class="sxs-lookup"><span data-stu-id="53c7f-108">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="53c7f-109">反斜線和下一個字元統稱為「escape」 *序列*。</span><span class="sxs-lookup"><span data-stu-id="53c7f-109">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="53c7f-110">下表顯示 F # 字串常值中支援的 Escape 序列。</span><span class="sxs-lookup"><span data-stu-id="53c7f-110">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="53c7f-111">字元</span><span class="sxs-lookup"><span data-stu-id="53c7f-111">Character</span></span>|<span data-ttu-id="53c7f-112">逸出序列</span><span class="sxs-lookup"><span data-stu-id="53c7f-112">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="53c7f-113">警示</span><span class="sxs-lookup"><span data-stu-id="53c7f-113">Alert</span></span>|`\a`|
|<span data-ttu-id="53c7f-114">退格鍵</span><span class="sxs-lookup"><span data-stu-id="53c7f-114">Backspace</span></span>|`\b`|
|<span data-ttu-id="53c7f-115">換頁字元</span><span class="sxs-lookup"><span data-stu-id="53c7f-115">Form feed</span></span>|`\f`|
|<span data-ttu-id="53c7f-116">新行字元</span><span class="sxs-lookup"><span data-stu-id="53c7f-116">Newline</span></span>|`\n`|
|<span data-ttu-id="53c7f-117">歸位字元</span><span class="sxs-lookup"><span data-stu-id="53c7f-117">Carriage return</span></span>|`\r`|
|<span data-ttu-id="53c7f-118">索引標籤</span><span class="sxs-lookup"><span data-stu-id="53c7f-118">Tab</span></span>|`\t`|
|<span data-ttu-id="53c7f-119">垂直 Tab 鍵</span><span class="sxs-lookup"><span data-stu-id="53c7f-119">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="53c7f-120">反斜線</span><span class="sxs-lookup"><span data-stu-id="53c7f-120">Backslash</span></span>|`\\`|
|<span data-ttu-id="53c7f-121">引號</span><span class="sxs-lookup"><span data-stu-id="53c7f-121">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="53c7f-122">單引號</span><span class="sxs-lookup"><span data-stu-id="53c7f-122">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="53c7f-123">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="53c7f-123">Unicode character</span></span>|<span data-ttu-id="53c7f-124">`\DDD` (，其中 `D` 指出十進位數; 範圍為 000-255; 例如 `\231` = "ç" ) </span><span class="sxs-lookup"><span data-stu-id="53c7f-124">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; for example, `\231` = "ç")</span></span>|
|<span data-ttu-id="53c7f-125">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="53c7f-125">Unicode character</span></span>|<span data-ttu-id="53c7f-126">`\xHH` (，其中 `H` 指出十六進位數位; 範圍為 00-FF，例如 `\xE7` = "ç" ) </span><span class="sxs-lookup"><span data-stu-id="53c7f-126">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; for example, `\xE7` = "ç")</span></span>|
|<span data-ttu-id="53c7f-127">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="53c7f-127">Unicode character</span></span>|<span data-ttu-id="53c7f-128">`\uHHHH` (UTF-16)  (其中 `H` 指出十六進位數位; 範圍為 0000-FFFF; 例如， `\u00E7` = "ç" ) </span><span class="sxs-lookup"><span data-stu-id="53c7f-128">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  for example, `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="53c7f-129">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="53c7f-129">Unicode character</span></span>|<span data-ttu-id="53c7f-130">`\U00HHHHHH` (32 UTF-8)  (，其中 `H` 指出十六進位數位; 範圍為 000000-10FFFF; 例如， `\U0001F47D` = " 👽 " ) </span><span class="sxs-lookup"><span data-stu-id="53c7f-130">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  for example, `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="53c7f-131">`\DDD`Escape 序列是十進位標記法，而非八進位標記法，就像大多數其他語言一樣。</span><span class="sxs-lookup"><span data-stu-id="53c7f-131">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="53c7f-132">因此，數位 `8` 和 `9` 是有效的，而序列 `\032` 表示 (U + 0020) 的空格，而八進位標記法中的相同程式碼點則為 `\040` 。</span><span class="sxs-lookup"><span data-stu-id="53c7f-132">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="53c7f-133">受限於 0-255 (0xFF) 的範圍， `\DDD` 和 `\x` escape 序列實際上是 [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) 字元集，因為該字元集符合前 256 Unicode 程式碼點。</span><span class="sxs-lookup"><span data-stu-id="53c7f-133">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

## <a name="verbatim-strings"></a><span data-ttu-id="53c7f-134">逐字字串</span><span class="sxs-lookup"><span data-stu-id="53c7f-134">Verbatim Strings</span></span>

<span data-ttu-id="53c7f-135">如果前面加上 @ 符號，常值為逐字字串。</span><span class="sxs-lookup"><span data-stu-id="53c7f-135">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="53c7f-136">這表示會忽略任何 escape 序列，但會將兩個引號字元視為一個引號字元。</span><span class="sxs-lookup"><span data-stu-id="53c7f-136">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

## <a name="triple-quoted-strings"></a><span data-ttu-id="53c7f-137">三個引號的字串</span><span class="sxs-lookup"><span data-stu-id="53c7f-137">Triple Quoted Strings</span></span>

<span data-ttu-id="53c7f-138">此外，字串可以用三個引號括住。</span><span class="sxs-lookup"><span data-stu-id="53c7f-138">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="53c7f-139">在此情況下，會忽略所有的 escape 序列，包括雙引號字元。</span><span class="sxs-lookup"><span data-stu-id="53c7f-139">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="53c7f-140">若要指定包含內嵌引號字串的字串，您可以使用逐字字串或以三括弧括住的字串。</span><span class="sxs-lookup"><span data-stu-id="53c7f-140">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="53c7f-141">如果您使用逐字字串，您必須指定兩個引號字元，以表示單引號字元。</span><span class="sxs-lookup"><span data-stu-id="53c7f-141">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="53c7f-142">如果您使用以三個引號括住的字串，則可以使用單引號字元，而不將它們剖析為字串的結尾。</span><span class="sxs-lookup"><span data-stu-id="53c7f-142">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="53c7f-143">當您使用 XML 或其他包含內嵌引號的結構時，這項技術會很有用。</span><span class="sxs-lookup"><span data-stu-id="53c7f-143">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="53c7f-144">在程式碼中，接受分行符號的字串會被接受，而且分行符號會以逐字的形式解釋為分行符號，除非反斜線字元是分行符號之前的最後一個字元。</span><span class="sxs-lookup"><span data-stu-id="53c7f-144">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="53c7f-145">使用反斜線字元時，會忽略下一行的開頭空白字元。</span><span class="sxs-lookup"><span data-stu-id="53c7f-145">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="53c7f-146">下列程式碼會產生具有值的字串， `str1` `"abc\ndef"` 以及 `str2` 具有值的字串 `"abcdef"` 。</span><span class="sxs-lookup"><span data-stu-id="53c7f-146">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a><span data-ttu-id="53c7f-147">字串編制索引和切割</span><span class="sxs-lookup"><span data-stu-id="53c7f-147">String Indexing and Slicing</span></span>

<span data-ttu-id="53c7f-148">您可以使用類似陣列的語法來存取字串中的個別字元，如下所示。</span><span class="sxs-lookup"><span data-stu-id="53c7f-148">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="53c7f-149">輸出為 `b`。</span><span class="sxs-lookup"><span data-stu-id="53c7f-149">The output is `b`.</span></span>

<span data-ttu-id="53c7f-150">或者，您可以使用陣列配量語法來解壓縮子字串，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="53c7f-150">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="53c7f-151">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="53c7f-151">The output is as follows.</span></span>

```console
abc
def
```

<span data-ttu-id="53c7f-152">您可以使用不帶正負號的位元組陣列來代表 ASCII 字串，請輸入 `byte[]` 。</span><span class="sxs-lookup"><span data-stu-id="53c7f-152">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="53c7f-153">您將尾碼新增 `B` 至字串常值，以表示它是 ASCII 字串。</span><span class="sxs-lookup"><span data-stu-id="53c7f-153">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="53c7f-154">搭配位元組陣列使用的 ASCII 字串常值支援與 Unicode 字串相同的 escape 序列，但 Unicode escape 序列除外。</span><span class="sxs-lookup"><span data-stu-id="53c7f-154">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="53c7f-155">字串運算子</span><span class="sxs-lookup"><span data-stu-id="53c7f-155">String Operators</span></span>

<span data-ttu-id="53c7f-156">`+`操作員可以用來串連字號串，維持與 .NET Framework 字串處理功能的相容性。</span><span class="sxs-lookup"><span data-stu-id="53c7f-156">The `+` operator can be used to concatenate strings, maintaining compatibility with the .NET Framework string handling features.</span></span> <span data-ttu-id="53c7f-157">下列範例說明字串串連。</span><span class="sxs-lookup"><span data-stu-id="53c7f-157">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="53c7f-158">String 類別</span><span class="sxs-lookup"><span data-stu-id="53c7f-158">String Class</span></span>

<span data-ttu-id="53c7f-159">因為 F # 中的字串類型實際上是 .NET Framework `System.String` 類型，所以所有 `System.String` 成員都可以使用。</span><span class="sxs-lookup"><span data-stu-id="53c7f-159">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="53c7f-160">這包括 `+` 用來串連字號串的運算子、 `Length` 屬性和 `Chars` 屬性（property），這會以 Unicode 字元陣列的形式傳回字串。</span><span class="sxs-lookup"><span data-stu-id="53c7f-160">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="53c7f-161">如需字串的詳細資訊，請參閱 `System.String` 。</span><span class="sxs-lookup"><span data-stu-id="53c7f-161">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="53c7f-162">藉由使用的 `Chars` 屬性 `System.String` ，您可以藉由指定索引來存取字串中的個別字元，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="53c7f-162">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="53c7f-163">字串模組</span><span class="sxs-lookup"><span data-stu-id="53c7f-163">String Module</span></span>

<span data-ttu-id="53c7f-164">字串處理的其他功能會包含在 `String` 命名空間的模組中 `FSharp.Core` 。</span><span class="sxs-lookup"><span data-stu-id="53c7f-164">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="53c7f-165">如需詳細資訊，請參閱 [字串模組](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-stringmodule.html)。</span><span class="sxs-lookup"><span data-stu-id="53c7f-165">For more information, see [String Module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-stringmodule.html).</span></span>

## <a name="see-also"></a><span data-ttu-id="53c7f-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53c7f-166">See also</span></span>

- [<span data-ttu-id="53c7f-167">F # 語言參考</span><span class="sxs-lookup"><span data-stu-id="53c7f-167">F# Language Reference</span></span>](index.md)
