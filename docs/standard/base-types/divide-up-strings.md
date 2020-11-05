---
title: 將字串分隔成子字串
description: 瞭解用來解壓縮字串元件的不同技術，包括字串、分割、正則運算式和字串。
ms.date: 10/30/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET], breaking up
ms.openlocfilehash: 88947c4576b0496e4b4e45042d665e3ca5857c53
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "93403607"
---
# <a name="extract-substrings-from-a-string"></a><span data-ttu-id="9a315-103">從字串中解壓縮子字串</span><span class="sxs-lookup"><span data-stu-id="9a315-103">Extract substrings from a string</span></span>

<span data-ttu-id="9a315-104">本文涵蓋一些用於解壓縮部分字串的不同技術。</span><span class="sxs-lookup"><span data-stu-id="9a315-104">This article covers some different techniques for extracting parts of a string.</span></span>

- <span data-ttu-id="9a315-105">當您想要的子字串以已知的分隔字元分隔 (或字元) 時，請使用 [Split 方法](#stringsplit-method) 。</span><span class="sxs-lookup"><span data-stu-id="9a315-105">Use the [Split method](#stringsplit-method) when the substrings you want are separated by a known delimiting character (or characters).</span></span>
- <span data-ttu-id="9a315-106">當字串符合固定模式時，[正則運算式](#regular-expressions)會很有用。</span><span class="sxs-lookup"><span data-stu-id="9a315-106">[Regular expressions](#regular-expressions) are useful when the string conforms to a fixed pattern.</span></span>
- <span data-ttu-id="9a315-107">當您不想要將字串中的 *所有* 子字串解壓縮時，請搭配使用 [IndexOf 和 Substring 方法](#stringindexof-and-stringsubstring-methods)。</span><span class="sxs-lookup"><span data-stu-id="9a315-107">Use the [IndexOf and Substring methods](#stringindexof-and-stringsubstring-methods) in conjunction when you don't want to extract *all* of the substrings in a string.</span></span>

## <a name="stringsplit-method"></a><span data-ttu-id="9a315-108">字串. Split 方法</span><span class="sxs-lookup"><span data-stu-id="9a315-108">String.Split method</span></span>

<span data-ttu-id="9a315-109"><xref:System.String.Split%2A?displayProperty=nameWithType> 提供數個多載，可協助您根據指定的一或多個分隔字元，將字串分割成子字串群組。</span><span class="sxs-lookup"><span data-stu-id="9a315-109"><xref:System.String.Split%2A?displayProperty=nameWithType> provides a handful of overloads to help you break up a string into a group of substrings based on one or more delimiting characters that you specify.</span></span> <span data-ttu-id="9a315-110">您可以選擇限制最終結果中的子字串總數、修剪子字串的空白字元，或排除空白的子字串。</span><span class="sxs-lookup"><span data-stu-id="9a315-110">You can choose to limit the total number of substrings in the final result, trim white-space characters from substrings, or exclude empty substrings.</span></span>

<span data-ttu-id="9a315-111">下列範例顯示三個不同的多載 `String.Split()` 。</span><span class="sxs-lookup"><span data-stu-id="9a315-111">The following examples show three different overloads of `String.Split()`.</span></span> <span data-ttu-id="9a315-112">第一個範例會呼叫多載， <xref:System.String.Split(System.Char[])> 而不會傳遞任何分隔字元。</span><span class="sxs-lookup"><span data-stu-id="9a315-112">The first example calls the <xref:System.String.Split(System.Char[])> overload without passing any separator characters.</span></span> <span data-ttu-id="9a315-113">當您未指定任何分隔字元時， `String.Split()` 會使用預設分隔符號（也就是空白字元）來分割字串。</span><span class="sxs-lookup"><span data-stu-id="9a315-113">When you don't specify any delimiting characters, `String.Split()` uses default delimiters, which are white-space characters, to split up the string.</span></span>

[!code-csharp-interactive[Intro#1](snippets/parse-strings/csharp/intro.cs#1)]
:::code language="vb" source="snippets/parse-strings/vb/intro.vb" id="1":::

<span data-ttu-id="9a315-114">如您所見， () 的句點字元 `.` 都包含在兩個子字串中。</span><span class="sxs-lookup"><span data-stu-id="9a315-114">As you can see, the period characters (`.`) are included in two of the substrings.</span></span> <span data-ttu-id="9a315-115">如果您想要排除句號字元，您可以新增句點字元做為額外的分隔字元。</span><span class="sxs-lookup"><span data-stu-id="9a315-115">If you want to exclude the period characters, you can add the period character as an additional delimiting character.</span></span> <span data-ttu-id="9a315-116">下一個範例會示範如何進行。</span><span class="sxs-lookup"><span data-stu-id="9a315-116">The next example shows how to do this.</span></span>

[!code-csharp-interactive[Intro#1](snippets/parse-strings/csharp/intro.cs#2)]
:::code language="vb" source="snippets/parse-strings/vb/intro.vb" id="2":::

<span data-ttu-id="9a315-117">這段期間已從子字串中消失，但現在已包含兩個額外的空白子字串。</span><span class="sxs-lookup"><span data-stu-id="9a315-117">The periods are gone from the substrings, but now two extra empty substrings have been included.</span></span> <span data-ttu-id="9a315-118">這些空白子字串代表單字和其後接句點之間的子字串。</span><span class="sxs-lookup"><span data-stu-id="9a315-118">These empty substring represent the substring between the word and the period that follows it.</span></span> <span data-ttu-id="9a315-119">若要省略所產生陣列中的空白子字串，您可以呼叫多載 <xref:System.String.Split(System.Char[],System.StringSplitOptions)> ，並 <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> 為 `options` 參數指定。</span><span class="sxs-lookup"><span data-stu-id="9a315-119">To omit empty substrings from the resulting array, you can call the <xref:System.String.Split(System.Char[],System.StringSplitOptions)> overload and specify <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> for the `options` parameter.</span></span>

[!code-csharp-interactive[Intro#1](snippets/parse-strings/csharp/intro.cs#3)]
:::code language="vb" source="snippets/parse-strings/vb/intro.vb" id="3":::

## <a name="regular-expressions"></a><span data-ttu-id="9a315-120">規則運算式</span><span class="sxs-lookup"><span data-stu-id="9a315-120">Regular expressions</span></span>

<span data-ttu-id="9a315-121">如果您的字串符合固定模式，您可以使用正則運算式來解壓縮和處理其元素。</span><span class="sxs-lookup"><span data-stu-id="9a315-121">If your string conforms to a fixed pattern, you can use a regular expression to extract and handle its elements.</span></span> <span data-ttu-id="9a315-122">例如，如果字串的格式為「 *數位\*\*運算元* \*\* 」，則您可以使用 [正則運算式](regular-expressions.md)來將字串的元素解壓縮並加以處理。</span><span class="sxs-lookup"><span data-stu-id="9a315-122">For example, if strings take the form " *number* *operand* *number* ", you can use a [regular expression](regular-expressions.md) to extract and handle the string's elements.</span></span> <span data-ttu-id="9a315-123">以下是範例：</span><span class="sxs-lookup"><span data-stu-id="9a315-123">Here's an example:</span></span>

:::code language="csharp" source="snippets/parse-strings/csharp/regex.cs" id="1" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/regex.vb" id="1":::

<span data-ttu-id="9a315-124">正則運算式模式的 `(\d+)\s+([-+*/])\s+(\d+)` 定義如下：</span><span class="sxs-lookup"><span data-stu-id="9a315-124">The regular expression pattern `(\d+)\s+([-+*/])\s+(\d+)` is defined like this:</span></span>

|<span data-ttu-id="9a315-125">模式</span><span class="sxs-lookup"><span data-stu-id="9a315-125">Pattern</span></span>|<span data-ttu-id="9a315-126">描述</span><span class="sxs-lookup"><span data-stu-id="9a315-126">Description</span></span>|
|-------------|-----------------|
|`(\d+)`|<span data-ttu-id="9a315-127">比對一個或多個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="9a315-127">Match one or more decimal digits.</span></span> <span data-ttu-id="9a315-128">這是第一個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="9a315-128">This is the first capturing group.</span></span>|
|`\s+`|<span data-ttu-id="9a315-129">符合一或多個空白字元。</span><span class="sxs-lookup"><span data-stu-id="9a315-129">Match one or more white-space characters.</span></span>|
|`([-+*/])`|<span data-ttu-id="9a315-130">符合算術運算子正負號 (+、-、\* 或/) 。</span><span class="sxs-lookup"><span data-stu-id="9a315-130">Match an arithmetic operator sign (+, -, \*, or /).</span></span> <span data-ttu-id="9a315-131">這是第二個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="9a315-131">This is the second capturing group.</span></span>|
|`\s+`|<span data-ttu-id="9a315-132">符合一或多個空白字元。</span><span class="sxs-lookup"><span data-stu-id="9a315-132">Match one or more white-space characters.</span></span>|
|`(\d+)`|<span data-ttu-id="9a315-133">比對一個或多個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="9a315-133">Match one or more decimal digits.</span></span> <span data-ttu-id="9a315-134">這是第三個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="9a315-134">This is the third capturing group.</span></span>|

<span data-ttu-id="9a315-135">您也可以使用正則運算式，根據模式（而不是一組固定的字元）從字串中解壓縮子字串。</span><span class="sxs-lookup"><span data-stu-id="9a315-135">You can also use a regular expression to extract substrings from a string based on a pattern rather than a fixed set of characters.</span></span> <span data-ttu-id="9a315-136">當發生下列其中一種情況時，這是常見的情況：</span><span class="sxs-lookup"><span data-stu-id="9a315-136">This is a common scenario when either of these conditions occurs:</span></span>

- <span data-ttu-id="9a315-137">一個或多個分隔符號在實例中不 *一定* 會當做分隔符號 <xref:System.String> 。</span><span class="sxs-lookup"><span data-stu-id="9a315-137">One or more of the delimiter characters does not *always* serve as a delimiter in the <xref:System.String> instance.</span></span>

- <span data-ttu-id="9a315-138">分隔符號的序列和數目是變數或未知的。</span><span class="sxs-lookup"><span data-stu-id="9a315-138">The sequence and number of delimiter characters is variable or unknown.</span></span>

<span data-ttu-id="9a315-139">例如， <xref:System.String.Split%2A> 方法不能用來分割下列字串，因為 `\n` (行) 字元的數目是變數，而且不一定會當做分隔符號。</span><span class="sxs-lookup"><span data-stu-id="9a315-139">For example, the <xref:System.String.Split%2A> method cannot be used to split the following string, because the number of `\n` (newline) characters is variable, and they don't always serve as delimiters.</span></span>

```text
[This is captured\ntext.]\n\n[\n[This is more captured text.]\n]
\n[Some more captured text:\n   Option1\n   Option2][Terse text.]
```

<span data-ttu-id="9a315-140">正則運算式可以輕鬆地分割此字串，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="9a315-140">A regular expression can split this string easily, as the following example shows.</span></span>

:::code language="csharp" source="snippets/parse-strings/csharp/regex.cs" id="2" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/regex.vb" id="2":::

<span data-ttu-id="9a315-141">正則運算式模式的 `\[([^\[\]]+)\]` 定義如下：</span><span class="sxs-lookup"><span data-stu-id="9a315-141">The regular expression pattern `\[([^\[\]]+)\]` is defined like this:</span></span>

|<span data-ttu-id="9a315-142">模式</span><span class="sxs-lookup"><span data-stu-id="9a315-142">Pattern</span></span>|<span data-ttu-id="9a315-143">描述</span><span class="sxs-lookup"><span data-stu-id="9a315-143">Description</span></span>|
|-------------|-----------------|
|`\[`|<span data-ttu-id="9a315-144">符合左括弧。</span><span class="sxs-lookup"><span data-stu-id="9a315-144">Match an opening bracket.</span></span>|
|`([^\[\]]+)`|<span data-ttu-id="9a315-145">比對不是開頭或右括弧的任何字元一或多次。</span><span class="sxs-lookup"><span data-stu-id="9a315-145">Match any character that is not an opening or a closing bracket one or more times.</span></span> <span data-ttu-id="9a315-146">這是第一個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="9a315-146">This is the first capturing group.</span></span>|
|`\]`|<span data-ttu-id="9a315-147">符合右括弧。</span><span class="sxs-lookup"><span data-stu-id="9a315-147">Match a closing bracket.</span></span>|

<span data-ttu-id="9a315-148"><xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType>方法幾乎與相同 <xref:System.String.Split%2A?displayProperty=nameWithType> ，不同之處在于它會根據正則運算式模式（而非固定字元集）來分割字串。</span><span class="sxs-lookup"><span data-stu-id="9a315-148">The <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method is almost identical to <xref:System.String.Split%2A?displayProperty=nameWithType>, except that it splits a string based on a regular expression pattern instead of a fixed character set.</span></span> <span data-ttu-id="9a315-149">例如，下列範例會使用 <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> 方法來分割字串，其中包含以多個連字號和其他字元組合分隔的子字串。</span><span class="sxs-lookup"><span data-stu-id="9a315-149">For example, the following example uses the <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method to split a string that contains substrings delimited by various combinations of hyphens and other characters.</span></span>

:::code language="csharp" source="snippets/parse-strings/csharp/regex.cs" id="3" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/regex.vb" id="3":::

<span data-ttu-id="9a315-150">正則運算式模式的 `\s-\s?[+*]?\s?-\s` 定義如下：</span><span class="sxs-lookup"><span data-stu-id="9a315-150">The regular expression pattern `\s-\s?[+*]?\s?-\s` is defined like this:</span></span>

|<span data-ttu-id="9a315-151">模式</span><span class="sxs-lookup"><span data-stu-id="9a315-151">Pattern</span></span>|<span data-ttu-id="9a315-152">描述</span><span class="sxs-lookup"><span data-stu-id="9a315-152">Description</span></span>|
|-------------|-----------------|
|`\s-`|<span data-ttu-id="9a315-153">比對空白字元後面接著連字號的空白字元。</span><span class="sxs-lookup"><span data-stu-id="9a315-153">Match a white-space character followed by a hyphen.</span></span>|
|`\s?`|<span data-ttu-id="9a315-154">比對零個或一個空白字元。</span><span class="sxs-lookup"><span data-stu-id="9a315-154">Match zero or one white-space character.</span></span>|
|`[+*]?`|<span data-ttu-id="9a315-155">比對出現零次或一次以上的 + 或 \* 字元。</span><span class="sxs-lookup"><span data-stu-id="9a315-155">Match zero or one occurrence of either the + or \* character.</span></span>|
|`\s?`|<span data-ttu-id="9a315-156">比對零個或一個空白字元。</span><span class="sxs-lookup"><span data-stu-id="9a315-156">Match zero or one white-space character.</span></span>|
|`-\s`|<span data-ttu-id="9a315-157">比對後接空白字元的連字號。</span><span class="sxs-lookup"><span data-stu-id="9a315-157">Match a hyphen followed by a white-space character.</span></span>|

## <a name="stringindexof-and-stringsubstring-methods"></a><span data-ttu-id="9a315-158">IndexOf 和 String Substring 方法</span><span class="sxs-lookup"><span data-stu-id="9a315-158">String.IndexOf and String.Substring methods</span></span>

<span data-ttu-id="9a315-159">如果您對字串中的所有子字串都不感興趣，您可能會想要使用其中一個字串比較方法，以傳回相符項開始的索引。</span><span class="sxs-lookup"><span data-stu-id="9a315-159">If you aren't interested in all of the substrings in a string, you might prefer to work with one of the string comparison methods that returns the index at which the match begins.</span></span> <span data-ttu-id="9a315-160">然後您可以呼叫 <xref:System.String.Substring%2A> 方法，將您想要的子字串解壓縮。</span><span class="sxs-lookup"><span data-stu-id="9a315-160">You can then call the <xref:System.String.Substring%2A> method to extract the substring that you want.</span></span> <span data-ttu-id="9a315-161">字串比較方法包括：</span><span class="sxs-lookup"><span data-stu-id="9a315-161">The string comparison methods include:</span></span>

- <span data-ttu-id="9a315-162"><xref:System.String.IndexOf%2A>，傳回字串實例中第一次出現字元或字串的以零為基底的索引。</span><span class="sxs-lookup"><span data-stu-id="9a315-162"><xref:System.String.IndexOf%2A>, which returns the zero-based index of the first occurrence of a character or string in a string instance.</span></span>

- <span data-ttu-id="9a315-163"><xref:System.String.IndexOfAny%2A>，會在字元陣列中第一次出現任何字元的目前字串實例中傳回以零為基底的索引。</span><span class="sxs-lookup"><span data-stu-id="9a315-163"><xref:System.String.IndexOfAny%2A>, which returns the zero-based index in the current string instance of the first occurrence of any character in a character array.</span></span>

- <span data-ttu-id="9a315-164"><xref:System.String.LastIndexOf%2A>，傳回字串實例中最後一次出現字元或字串的以零為基底的索引。</span><span class="sxs-lookup"><span data-stu-id="9a315-164"><xref:System.String.LastIndexOf%2A>, which returns the zero-based index of the last occurrence of a character or string in a string instance.</span></span>

- <span data-ttu-id="9a315-165"><xref:System.String.LastIndexOfAny%2A>，會在字元陣列中任何字元最後一次出現的目前字串實例中傳回以零為基底的索引。</span><span class="sxs-lookup"><span data-stu-id="9a315-165"><xref:System.String.LastIndexOfAny%2A>, which returns a zero-based index in the current string instance of the last occurrence of any character in a character array.</span></span>

<span data-ttu-id="9a315-166">下列範例會使用 <xref:System.String.IndexOf%2A> 方法來尋找字串中的句號。</span><span class="sxs-lookup"><span data-stu-id="9a315-166">The following example uses the <xref:System.String.IndexOf%2A> method to find the periods in a string.</span></span> <span data-ttu-id="9a315-167">然後，它會使用 <xref:System.String.Substring%2A> 方法來傳回完整的句子。</span><span class="sxs-lookup"><span data-stu-id="9a315-167">It then uses the <xref:System.String.Substring%2A> method to return full sentences.</span></span>

:::code language="csharp" source="snippets/parse-strings/csharp/indexof.cs" id="1" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/indexof.vb" id="1":::

## <a name="see-also"></a><span data-ttu-id="9a315-168">請參閱</span><span class="sxs-lookup"><span data-stu-id="9a315-168">See also</span></span>

- [<span data-ttu-id="9a315-169">.NET 中的基底字元串作業</span><span class="sxs-lookup"><span data-stu-id="9a315-169">Basic string operations in .NET</span></span>](basic-string-operations.md)
- [<span data-ttu-id="9a315-170">.NET 正則運算式</span><span class="sxs-lookup"><span data-stu-id="9a315-170">.NET regular expressions</span></span>](regular-expressions.md)
- [<span data-ttu-id="9a315-171">如何使用字串剖析字串。以 C 分隔#</span><span class="sxs-lookup"><span data-stu-id="9a315-171">How to parse strings using String.Split in C#</span></span>](../../csharp/how-to/parse-strings-using-split.md)
