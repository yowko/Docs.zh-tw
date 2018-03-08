---
title: "如何：搜尋字串(C# 指南)"
ms.date: 02/21/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with String methods
- strings [C#], searching with regular expressions
ms.assetid: fb1d9a6d-598d-4a35-bd5f-b86012edcb2b
ms.author: wiwagn
ms.openlocfilehash: cb672ef74d9eb83df7d1c8985e518136dad54c34
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="how-to-search-strings"></a><span data-ttu-id="8fff0-102">如何：搜尋字串</span><span class="sxs-lookup"><span data-stu-id="8fff0-102">How to: search strings</span></span>

<span data-ttu-id="8fff0-103">您可以使用兩種主要策略來搜尋字串中的文字。</span><span class="sxs-lookup"><span data-stu-id="8fff0-103">You can use two main strategies to search for text in strings.</span></span> <span data-ttu-id="8fff0-104"><xref:System.String> 類別的方法會搜尋特定文字。</span><span class="sxs-lookup"><span data-stu-id="8fff0-104">Methods of the <xref:System.String> class search for specific text.</span></span> <span data-ttu-id="8fff0-105">規則運算式會搜尋文字中的模式。</span><span class="sxs-lookup"><span data-stu-id="8fff0-105">Regular expressions search for patterns in text.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="8fff0-106">[字串](../language-reference/keywords/string.md)類型，這是 <xref:System.String?displayProperty=nameWithType> 類別的別名，提供一些有用的方法來搜尋字串的內容。</span><span class="sxs-lookup"><span data-stu-id="8fff0-106">The [string](../language-reference/keywords/string.md) type, which is an alias for the <xref:System.String?displayProperty=nameWithType> class, provides a number of useful methods for searching the contents of a string.</span></span> <span data-ttu-id="8fff0-107">它們是 <xref:System.String.Contains%2A>、<xref:System.String.StartsWith%2A><xref:System.String.EndsWith%2A>、<xref:System.String.IndexOf%2A>、<xref:System.String.LastIndexOf%2A>。</span><span class="sxs-lookup"><span data-stu-id="8fff0-107">Among them are <xref:System.String.Contains%2A>, <xref:System.String.StartsWith%2A>, <xref:System.String.EndsWith%2A>, <xref:System.String.IndexOf%2A>, <xref:System.String.LastIndexOf%2A>.</span></span> <span data-ttu-id="8fff0-108"><xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> 類別提供豐富的詞彙來搜尋文字中的模式。</span><span class="sxs-lookup"><span data-stu-id="8fff0-108">The <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> class provides a rich vocabulary to search for patterns in text.</span></span> <span data-ttu-id="8fff0-109">在本文中，您了解這些技術，以及如何選擇您需求的最佳方法。</span><span class="sxs-lookup"><span data-stu-id="8fff0-109">In this article, you learn these techniques and how to choose the best method for your needs.</span></span>

## <a name="does-a-string-contain-text"></a><span data-ttu-id="8fff0-110">字串是否包含文字？</span><span class="sxs-lookup"><span data-stu-id="8fff0-110">Does a string contain text?</span></span>

<span data-ttu-id="8fff0-111"><xref:System.String.Contains%2A?displayProperty=nameWithType>、<xref:System.String.StartsWith%2A?displayProperty=nameWithType> 和 <xref:System.String.EndsWith%2A?displayProperty=nameWithType> 方法會搜尋字串中的特定文字。</span><span class="sxs-lookup"><span data-stu-id="8fff0-111">The <xref:System.String.Contains%2A?displayProperty=nameWithType>, <xref:System.String.StartsWith%2A?displayProperty=nameWithType> and <xref:System.String.EndsWith%2A?displayProperty=nameWithType> methods search a string for specific text.</span></span> <span data-ttu-id="8fff0-112">下列範例示範所有這些方法，以及使用不區分大小寫搜尋的變化：</span><span class="sxs-lookup"><span data-stu-id="8fff0-112">The following example shows each of these methods and a variation that uses a case insensitive search:</span></span>

[!code-csharp-interactive[search strings using methods](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#1)]

<span data-ttu-id="8fff0-113">上述範例示範這些方法的使用重點。</span><span class="sxs-lookup"><span data-stu-id="8fff0-113">The preceding example demonstrates an important point for using these methods.</span></span> <span data-ttu-id="8fff0-114">搜尋預設會**區分大小寫**。</span><span class="sxs-lookup"><span data-stu-id="8fff0-114">Searches are **case-sensitive** by default.</span></span> <span data-ttu-id="8fff0-115">您可以使用 <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> 列舉值，來指定不區分大小寫的搜尋。</span><span class="sxs-lookup"><span data-stu-id="8fff0-115">You use the <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> enum value to specify a case insensitive search.</span></span>

## <a name="where-does-the-sought-text-occur-in-a-string"></a><span data-ttu-id="8fff0-116">所搜尋文字在字串中的位置？</span><span class="sxs-lookup"><span data-stu-id="8fff0-116">Where does the sought text occur in a string?</span></span>

<span data-ttu-id="8fff0-117"><xref:System.String.IndexOf%2A> 和 <xref:System.String.LastIndexOf%2A> 方法也會搜尋字串中的文字。</span><span class="sxs-lookup"><span data-stu-id="8fff0-117">The <xref:System.String.IndexOf%2A> and <xref:System.String.LastIndexOf%2A> methods also search for text in strings.</span></span> <span data-ttu-id="8fff0-118">這些方法會傳回所搜尋文字的位置。</span><span class="sxs-lookup"><span data-stu-id="8fff0-118">These methods return the location of the text being sought.</span></span> <span data-ttu-id="8fff0-119">如果找不到文字，則會傳回 `-1`。</span><span class="sxs-lookup"><span data-stu-id="8fff0-119">If the text isn't found, they return `-1`.</span></span> <span data-ttu-id="8fff0-120">下列範例示範如何搜尋 "methods" 這個單字的第一個和最後一個相符項目，並在其間顯示文字。</span><span class="sxs-lookup"><span data-stu-id="8fff0-120">The following example shows a search for the first and last occurrence of the word "methods" and displays the text in between.</span></span>
  
[!code-csharp-interactive[search strings for indices](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#2)]

## <a name="finding-specific-text-using-regular-expressions"></a><span data-ttu-id="8fff0-121">使用規則運算式來尋找特定文字</span><span class="sxs-lookup"><span data-stu-id="8fff0-121">Finding specific text using regular expressions</span></span>

<span data-ttu-id="8fff0-122"><xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> 類別可以用來搜尋字串。</span><span class="sxs-lookup"><span data-stu-id="8fff0-122">The <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> class can be used to search strings.</span></span> <span data-ttu-id="8fff0-123">這些搜尋的複雜性範圍可以從簡單到複雜文字模式。</span><span class="sxs-lookup"><span data-stu-id="8fff0-123">These searches can range in complexity from simple to complicated text patterns.</span></span>

<span data-ttu-id="8fff0-124">下列程式碼範例會搜尋句子中的 "the" 或 "their" 單字，但忽略大小寫。</span><span class="sxs-lookup"><span data-stu-id="8fff0-124">The following code example searches for the word "the" or "their" in a sentence, ignoring case.</span></span> <span data-ttu-id="8fff0-125">靜態方法 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> 會執行搜尋。</span><span class="sxs-lookup"><span data-stu-id="8fff0-125">The static method <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> performs the search.</span></span> <span data-ttu-id="8fff0-126">您為其指定要搜尋的字串和搜尋模式。</span><span class="sxs-lookup"><span data-stu-id="8fff0-126">You give it the string to search and a search pattern.</span></span> <span data-ttu-id="8fff0-127">在此情況下，第三個引數指定不區分大小寫的搜尋。</span><span class="sxs-lookup"><span data-stu-id="8fff0-127">In this case, a third argument specifies case-insensitive search.</span></span> <span data-ttu-id="8fff0-128">如需詳細資訊，請參閱<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="8fff0-128">For more information, see <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.</span></span>  

<span data-ttu-id="8fff0-129">搜尋模式描述您搜尋的文字。</span><span class="sxs-lookup"><span data-stu-id="8fff0-129">The search pattern describes the text you search for.</span></span> <span data-ttu-id="8fff0-130">下表描述搜尋模式的每個項目 </span><span class="sxs-lookup"><span data-stu-id="8fff0-130">The following table describes each element of the search pattern.</span></span> <span data-ttu-id="8fff0-131">(下表使用單一 `\`，其在 C# 字串中必須逸出為 `\\`)。</span><span class="sxs-lookup"><span data-stu-id="8fff0-131">(The table below uses the single `\` which must be escaped as `\\` in a C# string).</span></span>

| <span data-ttu-id="8fff0-132">pattern</span><span class="sxs-lookup"><span data-stu-id="8fff0-132">pattern</span></span>  | <span data-ttu-id="8fff0-133">意義</span><span class="sxs-lookup"><span data-stu-id="8fff0-133">Meaning</span></span>     |
| -------- |-------------|
| <span data-ttu-id="8fff0-134">the</span><span class="sxs-lookup"><span data-stu-id="8fff0-134">the</span></span>      | <span data-ttu-id="8fff0-135">比對文字 "the"</span><span class="sxs-lookup"><span data-stu-id="8fff0-135">match the text "the"</span></span> |
| <span data-ttu-id="8fff0-136">(eir)?</span><span class="sxs-lookup"><span data-stu-id="8fff0-136">(eir)?</span></span>   | <span data-ttu-id="8fff0-137">比對 "eir" 的 0 或 1 個出現項目</span><span class="sxs-lookup"><span data-stu-id="8fff0-137">match 0 or 1 occurence of "eir"</span></span> |
| <span data-ttu-id="8fff0-138">\s</span><span class="sxs-lookup"><span data-stu-id="8fff0-138">\s</span></span>       | <span data-ttu-id="8fff0-139">比對空白字元</span><span class="sxs-lookup"><span data-stu-id="8fff0-139">match a whitespace character</span></span>    |
  
[!code-csharp-interactive[Search using regular expressions](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#3)]
  
> [!TIP]
> <span data-ttu-id="8fff0-140">當您搜尋完全相符的字串時，`string` 方法通常是較好的選擇。</span><span class="sxs-lookup"><span data-stu-id="8fff0-140">The `string` methods are usually better choices when you are searching for an exact string.</span></span> <span data-ttu-id="8fff0-141">當您搜尋某個模式或來源字串時，規則運算式是較好的選擇。</span><span class="sxs-lookup"><span data-stu-id="8fff0-141">Regular expressions are better when you are searching for some pattern is a source string.</span></span>

## <a name="does-a-string-follow-a-pattern"></a><span data-ttu-id="8fff0-142">字串遵循模式嗎？</span><span class="sxs-lookup"><span data-stu-id="8fff0-142">Does a string follow a pattern?</span></span>

<span data-ttu-id="8fff0-143">下列程式碼使用規則運算式來驗證陣列中每個字串的格式。</span><span class="sxs-lookup"><span data-stu-id="8fff0-143">The following code uses regular expressions to validate the format of each string in an array.</span></span> <span data-ttu-id="8fff0-144">驗證需要每個字串具有電話號碼的形式，其中數字的三個群組以連字號分隔、前兩個群組包含三位數，而第三個群組包含四位數。</span><span class="sxs-lookup"><span data-stu-id="8fff0-144">The validation requires that each string have the form of a telephone number in which three groups of digits are separated by dashes, the first two groups contain three digits, and the third group contains four digits.</span></span> <span data-ttu-id="8fff0-145">搜尋模式使用規則運算式 `^\\d{3}-\\d{3}-\\d{4}$`。</span><span class="sxs-lookup"><span data-stu-id="8fff0-145">The search pattern uses the regular expression `^\\d{3}-\\d{3}-\\d{4}$`.</span></span> <span data-ttu-id="8fff0-146">如需詳細資訊，請參閱[規則運算式語言 - 快速參考](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c)。</span><span class="sxs-lookup"><span data-stu-id="8fff0-146">For more information, see [Regular Expression Language - Quick Reference](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c).</span></span>

| <span data-ttu-id="8fff0-147">pattern</span><span class="sxs-lookup"><span data-stu-id="8fff0-147">pattern</span></span>  | <span data-ttu-id="8fff0-148">意義</span><span class="sxs-lookup"><span data-stu-id="8fff0-148">Meaning</span></span>                             |
| -------- |-------------------------------------|
| ^        | <span data-ttu-id="8fff0-149">比對字串的開頭</span><span class="sxs-lookup"><span data-stu-id="8fff0-149">matches the beginning of the string</span></span> |
| <span data-ttu-id="8fff0-150">\d{3}</span><span class="sxs-lookup"><span data-stu-id="8fff0-150">\d{3}</span></span>    | <span data-ttu-id="8fff0-151">僅比對 3 位數的字元</span><span class="sxs-lookup"><span data-stu-id="8fff0-151">matches exactly 3 digit characters</span></span>  |
| -        | <span data-ttu-id="8fff0-152">比對 '-' 字元</span><span class="sxs-lookup"><span data-stu-id="8fff0-152">matches the '-' character</span></span>           |
| <span data-ttu-id="8fff0-153">\d{3}</span><span class="sxs-lookup"><span data-stu-id="8fff0-153">\d{3}</span></span>    | <span data-ttu-id="8fff0-154">僅比對 3 位數的字元</span><span class="sxs-lookup"><span data-stu-id="8fff0-154">matches exactly 3 digit characters</span></span>  |
| -        | <span data-ttu-id="8fff0-155">比對 '-' 字元</span><span class="sxs-lookup"><span data-stu-id="8fff0-155">matches the '-' character</span></span>           |
| <span data-ttu-id="8fff0-156">\d{4}</span><span class="sxs-lookup"><span data-stu-id="8fff0-156">\d{4}</span></span>    | <span data-ttu-id="8fff0-157">僅比對 4 位數的字元</span><span class="sxs-lookup"><span data-stu-id="8fff0-157">matches exactly 4 digit characters</span></span>  |
| $        | <span data-ttu-id="8fff0-158">比對字串的結尾</span><span class="sxs-lookup"><span data-stu-id="8fff0-158">matches the end of the string</span></span>       |


[!code-csharp-interactive[csProgGuideStrings#4](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#4)]

<span data-ttu-id="8fff0-159">此單一搜尋模式會比對許多有效字串。</span><span class="sxs-lookup"><span data-stu-id="8fff0-159">This single search pattern matches many valid strings.</span></span> <span data-ttu-id="8fff0-160">規則運算式較適合用來搜尋或驗證模式，而不是單一文字字串。</span><span class="sxs-lookup"><span data-stu-id="8fff0-160">Regular expressions are better to search for or validate against a pattern, rather than a single text string.</span></span>

<span data-ttu-id="8fff0-161">您可以查看 [GitHub 存放庫](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings)中的程式碼，來嘗試這些範例。</span><span class="sxs-lookup"><span data-stu-id="8fff0-161">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="8fff0-162">或者，您可以將範例下載[為 ZIP 檔案](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings.zip)。</span><span class="sxs-lookup"><span data-stu-id="8fff0-162">Or you can download the samples [as a zip file](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="8fff0-163">請參閱</span><span class="sxs-lookup"><span data-stu-id="8fff0-163">See Also</span></span>  

 [<span data-ttu-id="8fff0-164">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="8fff0-164">C# Programming Guide</span></span>](../programming-guide/index.md)  
 [<span data-ttu-id="8fff0-165">字串</span><span class="sxs-lookup"><span data-stu-id="8fff0-165">Strings</span></span>](../programming-guide/strings/index.md)  
 <span data-ttu-id="8fff0-166">[LINQ 和字串](../programming-guide/concepts/linq/linq-and-strings.md) </span><span class="sxs-lookup"><span data-stu-id="8fff0-166">[LINQ and Strings](../programming-guide/concepts/linq/linq-and-strings.md) </span></span>  
 <span data-ttu-id="8fff0-167"><xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8fff0-167"><xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType></span></span>     
 <span data-ttu-id="8fff0-168">[.NET Framework 規則運算式](../../standard/base-types/regular-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="8fff0-168">[.NET Framework Regular Expressions](../../standard/base-types/regular-expressions.md) </span></span>  
 <span data-ttu-id="8fff0-169">[規則運算式語言 - 快速參考](../../standard/base-types/regular-expression-language-quick-reference.md) </span><span class="sxs-lookup"><span data-stu-id="8fff0-169">[Regular Expression Language - Quick Reference](../../standard/base-types/regular-expression-language-quick-reference.md) </span></span>  
 [<span data-ttu-id="8fff0-170">在 .NET 中使用字串的最佳做法</span><span class="sxs-lookup"><span data-stu-id="8fff0-170">Best practices for using strings in .NET</span></span>](../../standard/base-types/best-practices-strings.md)  
