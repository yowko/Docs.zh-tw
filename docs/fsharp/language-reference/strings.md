---
title: "字串 (F#)"
description: "了解 F # 'string' 類型為 Unicode 字元序列所代表的不可變的文字。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: df7624e5-ca6c-4e77-9e2b-87ca7e5e6f52
ms.openlocfilehash: 96a398ebcd53681481b10d1a2bee5f1e5442a5cd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="strings"></a><span data-ttu-id="9f722-104">字串</span><span class="sxs-lookup"><span data-stu-id="9f722-104">Strings</span></span>

> [!NOTE]
<span data-ttu-id="9f722-105">本文中的 API 參考連結將帶您前往 MSDN。</span><span class="sxs-lookup"><span data-stu-id="9f722-105">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="9f722-106">docs.microsoft.com API 參考不完整。</span><span class="sxs-lookup"><span data-stu-id="9f722-106">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="9f722-107">`string`類型不可變的文字表示為 Unicode 字元序列。</span><span class="sxs-lookup"><span data-stu-id="9f722-107">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="9f722-108">`string` 是 `System.String` 在 .NET Framework 中的別名。</span><span class="sxs-lookup"><span data-stu-id="9f722-108">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="9f722-109">備註</span><span class="sxs-lookup"><span data-stu-id="9f722-109">Remarks</span></span>
<span data-ttu-id="9f722-110">字串常值是以引號 （"） 字元分隔。</span><span class="sxs-lookup"><span data-stu-id="9f722-110">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="9f722-111">反斜線字元 (\)用來編碼某些特殊字元。</span><span class="sxs-lookup"><span data-stu-id="9f722-111">The backslash character (\) is used to encode certain special characters.</span></span> <span data-ttu-id="9f722-112">反斜線和在一起的下一個字元稱為*逸出序列*。</span><span class="sxs-lookup"><span data-stu-id="9f722-112">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="9f722-113">逸出序列支援 F # 字串常值會顯示下表中。</span><span class="sxs-lookup"><span data-stu-id="9f722-113">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="9f722-114">字元</span><span class="sxs-lookup"><span data-stu-id="9f722-114">Character</span></span>|<span data-ttu-id="9f722-115">逸出序列</span><span class="sxs-lookup"><span data-stu-id="9f722-115">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="9f722-116">退格鍵</span><span class="sxs-lookup"><span data-stu-id="9f722-116">Backspace</span></span>|<span data-ttu-id="9f722-117">\b</span><span class="sxs-lookup"><span data-stu-id="9f722-117">\b</span></span>|
|<span data-ttu-id="9f722-118">新行字元</span><span class="sxs-lookup"><span data-stu-id="9f722-118">Newline</span></span>|\n|
|<span data-ttu-id="9f722-119">歸位字元</span><span class="sxs-lookup"><span data-stu-id="9f722-119">Carriage return</span></span>|<span data-ttu-id="9f722-120">\r</span><span class="sxs-lookup"><span data-stu-id="9f722-120">\r</span></span>|
|<span data-ttu-id="9f722-121">索引標籤</span><span class="sxs-lookup"><span data-stu-id="9f722-121">Tab</span></span>|<span data-ttu-id="9f722-122">\t</span><span class="sxs-lookup"><span data-stu-id="9f722-122">\t</span></span>|
|<span data-ttu-id="9f722-123">反斜線</span><span class="sxs-lookup"><span data-stu-id="9f722-123">Backslash</span></span>|\\|
|<span data-ttu-id="9f722-124">引號</span><span class="sxs-lookup"><span data-stu-id="9f722-124">Quotation mark</span></span>|\"|
|<span data-ttu-id="9f722-125">所有格符號</span><span class="sxs-lookup"><span data-stu-id="9f722-125">Apostrophe</span></span>|\'|
|<span data-ttu-id="9f722-126">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="9f722-126">Unicode character</span></span>|<span data-ttu-id="9f722-127">\u*XXXX*或 \U*XXXXXXXX* (其中*X*表示十六進位數字)</span><span class="sxs-lookup"><span data-stu-id="9f722-127">\u*XXXX* or \U*XXXXXXXX* (where *X* indicates a hexadecimal digit)</span></span>|

<span data-ttu-id="9f722-128">如果前面加上 @ 符號，常值是逐字字串。</span><span class="sxs-lookup"><span data-stu-id="9f722-128">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="9f722-129">這表示，則會忽略任何逸出序列，不同之處在於兩個引號字元視為一個引號字元。</span><span class="sxs-lookup"><span data-stu-id="9f722-129">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

<span data-ttu-id="9f722-130">此外，可能會以三引號括住字串。</span><span class="sxs-lookup"><span data-stu-id="9f722-130">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="9f722-131">在此情況下，會忽略所有逸出序列，包括雙引號字元。</span><span class="sxs-lookup"><span data-stu-id="9f722-131">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="9f722-132">若要指定字串，其中包含內嵌加引號的字串，您可以使用逐字字串或三重加上引號的字串。</span><span class="sxs-lookup"><span data-stu-id="9f722-132">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="9f722-133">如果您使用逐字字串時，您必須指定兩個引號字元來表示單一引號字元。</span><span class="sxs-lookup"><span data-stu-id="9f722-133">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="9f722-134">如果您使用 triple 加上引號的字串，您可以使用單引號字元沒有它們正在剖析為字串的結尾。</span><span class="sxs-lookup"><span data-stu-id="9f722-134">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="9f722-135">當您使用 XML 或其他結構包含內嵌的引號時，這個技巧就很有用。</span><span class="sxs-lookup"><span data-stu-id="9f722-135">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="9f722-136">在程式碼中，接受字串有分行符號，分行符號會逐字解譯為換行，除非反斜線字元就分行前的最後一個字元。</span><span class="sxs-lookup"><span data-stu-id="9f722-136">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="9f722-137">使用反斜線字元時，會忽略在下一行的開頭空白。</span><span class="sxs-lookup"><span data-stu-id="9f722-137">Leading whitespace on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="9f722-138">下列程式碼會產生字串`str1`，並且其值`"abc\n     def"`和字串`str2`，並且其值`"abcdef"`。</span><span class="sxs-lookup"><span data-stu-id="9f722-138">The following code produces a string `str1` that has value `"abc\n     def"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

<span data-ttu-id="9f722-139">您可以存取個別字元在字串中的使用類似陣列的語法，如下所示。</span><span class="sxs-lookup"><span data-stu-id="9f722-139">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="9f722-140">輸出為 `b`。</span><span class="sxs-lookup"><span data-stu-id="9f722-140">The output is `b`.</span></span>

<span data-ttu-id="9f722-141">或者，您可以使用陣列的配量語法，來擷取子字串，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="9f722-141">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="9f722-142">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="9f722-142">The output is as follows.</span></span>

```
abc
def
```

<span data-ttu-id="9f722-143">您可以表示不帶正負號位元組，型別陣列的 ASCII 字串`byte[]`。</span><span class="sxs-lookup"><span data-stu-id="9f722-143">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="9f722-144">新增後置詞`B`為字串常值以指出它是 ASCII 字串。</span><span class="sxs-lookup"><span data-stu-id="9f722-144">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="9f722-145">ASCII 字串常值的位元組陣列搭配使用支援相同的逸出序列，做為 Unicode 字串，除了 Unicode 逸出序列。</span><span class="sxs-lookup"><span data-stu-id="9f722-145">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]
    
## <a name="string-operators"></a><span data-ttu-id="9f722-146">字串運算子</span><span class="sxs-lookup"><span data-stu-id="9f722-146">String Operators</span></span>
<span data-ttu-id="9f722-147">有兩種方式將字串串連： 使用`+`運算子或使用`^`運算子。</span><span class="sxs-lookup"><span data-stu-id="9f722-147">There are two ways to concatenate strings: by using the `+` operator or by using the `^` operator.</span></span> <span data-ttu-id="9f722-148">`+`運算子會維護與.NET Framework 字串處理功能的相容性。</span><span class="sxs-lookup"><span data-stu-id="9f722-148">The `+` operator maintains compatibility with the .NET Framework string handling features.</span></span>

<span data-ttu-id="9f722-149">下列範例說明字串串連。</span><span class="sxs-lookup"><span data-stu-id="9f722-149">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]
    
## <a name="string-class"></a><span data-ttu-id="9f722-150">字串類別</span><span class="sxs-lookup"><span data-stu-id="9f722-150">String Class</span></span>
<span data-ttu-id="9f722-151">因為在 F # 字串型別實際上是以.NET Framework`System.String`輸入所有`System.String`成員都可以使用。</span><span class="sxs-lookup"><span data-stu-id="9f722-151">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="9f722-152">這包括`+`運算子，就會用來串連字串，`Length`屬性，而`Chars`屬性，傳回的字串為 Unicode 字元陣列。</span><span class="sxs-lookup"><span data-stu-id="9f722-152">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="9f722-153">如需字串的詳細資訊，請參閱`System.String`。</span><span class="sxs-lookup"><span data-stu-id="9f722-153">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="9f722-154">使用`Chars`屬性`System.String`，您可以存取個別字元在字串中的指定的索引，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="9f722-154">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]
    
## <a name="string-module"></a><span data-ttu-id="9f722-155">字串模組</span><span class="sxs-lookup"><span data-stu-id="9f722-155">String Module</span></span>
<span data-ttu-id="9f722-156">字串處理的額外功能隨附於`String`中的模組`FSharp.Core`命名空間。</span><span class="sxs-lookup"><span data-stu-id="9f722-156">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="9f722-157">如需詳細資訊，請參閱[Core.String 模組](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d)。</span><span class="sxs-lookup"><span data-stu-id="9f722-157">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="9f722-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f722-158">See Also</span></span>
[<span data-ttu-id="9f722-159">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="9f722-159">F# Language Reference</span></span>](index.md)
