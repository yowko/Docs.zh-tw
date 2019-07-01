---
title: 字串
description: 了解如何F#'string' 類型以一連串的 Unicode 字元表示不可變的文字。
ms.date: 06/28/2019
ms.openlocfilehash: 8bd7a65a8d8e9e6a2d3930cd1fc9e800342d9a18
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487762"
---
# <a name="strings"></a><span data-ttu-id="3078a-103">字串</span><span class="sxs-lookup"><span data-stu-id="3078a-103">Strings</span></span>

> [!NOTE]
> <span data-ttu-id="3078a-104">本文中的 API 參考連結將帶您前往 MSDN。</span><span class="sxs-lookup"><span data-stu-id="3078a-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="3078a-105">docs.microsoft.com API 參考不完整。</span><span class="sxs-lookup"><span data-stu-id="3078a-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="3078a-106">`string`類型以一連串的 Unicode 字元表示不可變的文字。</span><span class="sxs-lookup"><span data-stu-id="3078a-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="3078a-107">`string` 是 `System.String` 在 .NET Framework 中的別名。</span><span class="sxs-lookup"><span data-stu-id="3078a-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="3078a-108">備註</span><span class="sxs-lookup"><span data-stu-id="3078a-108">Remarks</span></span>

<span data-ttu-id="3078a-109">字串常值是以引號 （"） 字元分隔。</span><span class="sxs-lookup"><span data-stu-id="3078a-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="3078a-110">反斜線字元 ( \\ ) 來編碼某些特殊字元。</span><span class="sxs-lookup"><span data-stu-id="3078a-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="3078a-111">反斜線和放在一起的下一個字元稱為*逸出序列*。</span><span class="sxs-lookup"><span data-stu-id="3078a-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="3078a-112">逸出序列中支援F#字串常值會顯示下表中。</span><span class="sxs-lookup"><span data-stu-id="3078a-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="3078a-113">字元</span><span class="sxs-lookup"><span data-stu-id="3078a-113">Character</span></span>|<span data-ttu-id="3078a-114">逸出序列</span><span class="sxs-lookup"><span data-stu-id="3078a-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="3078a-115">退格鍵</span><span class="sxs-lookup"><span data-stu-id="3078a-115">Backspace</span></span>|`\b`|
|<span data-ttu-id="3078a-116">新行字元</span><span class="sxs-lookup"><span data-stu-id="3078a-116">Newline</span></span>|`\n`|
|<span data-ttu-id="3078a-117">歸位字元</span><span class="sxs-lookup"><span data-stu-id="3078a-117">Carriage return</span></span>|`\r`|
|<span data-ttu-id="3078a-118">索引標籤</span><span class="sxs-lookup"><span data-stu-id="3078a-118">Tab</span></span>|`\t`|
|<span data-ttu-id="3078a-119">反斜線</span><span class="sxs-lookup"><span data-stu-id="3078a-119">Backslash</span></span>|`\\`|
|<span data-ttu-id="3078a-120">引號</span><span class="sxs-lookup"><span data-stu-id="3078a-120">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="3078a-121">所有格符號</span><span class="sxs-lookup"><span data-stu-id="3078a-121">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="3078a-122">Unicode 字元</span><span class="sxs-lookup"><span data-stu-id="3078a-122">Unicode character</span></span>|<span data-ttu-id="3078a-123">`\uXXXX` (Utf-16) 或`\U00XXXXXX`(UTF-32) (其中`X`表示十六進位數字)</span><span class="sxs-lookup"><span data-stu-id="3078a-123">`\uXXXX` (UTF-16) or `\U00XXXXXX` (UTF-32) (where `X` indicates a hexadecimal digit)</span></span>|

<span data-ttu-id="3078a-124">如果前面加上 @ 符號，此常值是逐字字串。</span><span class="sxs-lookup"><span data-stu-id="3078a-124">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="3078a-125">這表示，則會忽略任何逸出序列，不同之處在於兩個引號字元視為一個引號字元。</span><span class="sxs-lookup"><span data-stu-id="3078a-125">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

<span data-ttu-id="3078a-126">此外，可能以三引號括住字串。</span><span class="sxs-lookup"><span data-stu-id="3078a-126">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="3078a-127">在此情況下，會忽略所有逸出序列，包括雙引號字元。</span><span class="sxs-lookup"><span data-stu-id="3078a-127">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="3078a-128">若要指定包含內嵌字串加上引號的字串，您可以使用逐字字串或三重物件加上引號的字串。</span><span class="sxs-lookup"><span data-stu-id="3078a-128">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="3078a-129">如果您使用逐字字串時，您必須指定兩個引號字元來表示一個單引號字元。</span><span class="sxs-lookup"><span data-stu-id="3078a-129">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="3078a-130">如果您使用三重物件加上引號的字串，您可以使用單引號字元沒有它們正在剖析為字串的結尾。</span><span class="sxs-lookup"><span data-stu-id="3078a-130">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="3078a-131">當您使用 XML 或其他結構包含內嵌的引號，則這個方法就很有用。</span><span class="sxs-lookup"><span data-stu-id="3078a-131">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="3078a-132">程式碼中，接受已換行的字串，並換行符號會解譯為常值為換行符號，除非反斜線字元換行之前的最後一個字元。</span><span class="sxs-lookup"><span data-stu-id="3078a-132">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="3078a-133">使用反斜線字元時，會忽略在下一行的前置空白字元。</span><span class="sxs-lookup"><span data-stu-id="3078a-133">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="3078a-134">下列程式碼產生的字串`str1`具有值`"abc\ndef"`和字串`str2`具有值`"abcdef"`。</span><span class="sxs-lookup"><span data-stu-id="3078a-134">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

<span data-ttu-id="3078a-135">您可以存取個別字元在字串中的使用類似陣列的語法，如下所示。</span><span class="sxs-lookup"><span data-stu-id="3078a-135">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="3078a-136">輸出為 `b`。</span><span class="sxs-lookup"><span data-stu-id="3078a-136">The output is `b`.</span></span>

<span data-ttu-id="3078a-137">或者，您可以使用陣列配量語法，來擷取子字串，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="3078a-137">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="3078a-138">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="3078a-138">The output is as follows.</span></span>

```
abc
def
```

<span data-ttu-id="3078a-139">您可以不帶正負號位元組，型別陣列表示 ASCII 字串`byte[]`。</span><span class="sxs-lookup"><span data-stu-id="3078a-139">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="3078a-140">新增後置詞`B`為字串常值以指出它是 ASCII 字串。</span><span class="sxs-lookup"><span data-stu-id="3078a-140">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="3078a-141">ASCII 字串常值的位元組陣列搭配使用支援相同逸出序列為 Unicode 字串，除了 Unicode 逸出序列。</span><span class="sxs-lookup"><span data-stu-id="3078a-141">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="3078a-142">字串運算子</span><span class="sxs-lookup"><span data-stu-id="3078a-142">String Operators</span></span>

<span data-ttu-id="3078a-143">有兩種方式來串連字串： 使用`+`運算子或使用`^`運算子。</span><span class="sxs-lookup"><span data-stu-id="3078a-143">There are two ways to concatenate strings: by using the `+` operator or by using the `^` operator.</span></span> <span data-ttu-id="3078a-144">`+`運算子會維護與.NET Framework 的字串處理功能的相容性。</span><span class="sxs-lookup"><span data-stu-id="3078a-144">The `+` operator maintains compatibility with the .NET Framework string handling features.</span></span>

<span data-ttu-id="3078a-145">下列範例說明字串串連。</span><span class="sxs-lookup"><span data-stu-id="3078a-145">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="3078a-146">字串類別</span><span class="sxs-lookup"><span data-stu-id="3078a-146">String Class</span></span>

<span data-ttu-id="3078a-147">因為字串類型在F#是實際的.NET Framework`System.String`類型，所有`System.String`成員都可以使用。</span><span class="sxs-lookup"><span data-stu-id="3078a-147">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="3078a-148">這包括`+`運算子，用來串連字串，就`Length`屬性，而`Chars`屬性，會傳回字串的 Unicode 字元陣列。</span><span class="sxs-lookup"><span data-stu-id="3078a-148">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="3078a-149">如需字串的詳細資訊，請參閱`System.String`。</span><span class="sxs-lookup"><span data-stu-id="3078a-149">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="3078a-150">藉由使用`Chars`屬性`System.String`，您可以存取個別字元在字串中的指定的索引，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="3078a-150">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="3078a-151">字串模組</span><span class="sxs-lookup"><span data-stu-id="3078a-151">String Module</span></span>

<span data-ttu-id="3078a-152">字串處理的其他功能包含在`String`中的模組`FSharp.Core`命名空間。</span><span class="sxs-lookup"><span data-stu-id="3078a-152">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="3078a-153">如需詳細資訊，請參閱 < [Core.String 模組](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d)。</span><span class="sxs-lookup"><span data-stu-id="3078a-153">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="3078a-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3078a-154">See also</span></span>

- [<span data-ttu-id="3078a-155">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="3078a-155">F# Language Reference</span></span>](index.md)
