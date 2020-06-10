---
title: '如何搜尋字串（c # 指南）'
ms.date: 02/21/2018
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with String methods
- strings [C#], searching with regular expressions
ms.assetid: fb1d9a6d-598d-4a35-bd5f-b86012edcb2b
ms.openlocfilehash: f5fd61452d6f83bd035b5c6930bd09673c0ded23
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662949"
---
# <a name="how-to-search-strings"></a><span data-ttu-id="6eb7f-102">如何搜尋字串</span><span class="sxs-lookup"><span data-stu-id="6eb7f-102">How to search strings</span></span>

<span data-ttu-id="6eb7f-103">您可以使用兩種主要策略來搜尋字串中的文字。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-103">You can use two main strategies to search for text in strings.</span></span> <span data-ttu-id="6eb7f-104"><xref:System.String> 類別的方法會搜尋特定文字。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-104">Methods of the <xref:System.String> class search for specific text.</span></span> <span data-ttu-id="6eb7f-105">規則運算式會搜尋文字中的模式。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-105">Regular expressions search for patterns in text.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="6eb7f-106">[字串](../language-reference/builtin-types/reference-types.md#the-string-type)類型，這是 <xref:System.String?displayProperty=nameWithType> 類別的別名，提供一些有用的方法來搜尋字串的內容。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-106">The [string](../language-reference/builtin-types/reference-types.md#the-string-type) type, which is an alias for the <xref:System.String?displayProperty=nameWithType> class, provides a number of useful methods for searching the contents of a string.</span></span> <span data-ttu-id="6eb7f-107">它們是 <xref:System.String.Contains%2A>、<xref:System.String.StartsWith%2A><xref:System.String.EndsWith%2A>、<xref:System.String.IndexOf%2A>、<xref:System.String.LastIndexOf%2A>。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-107">Among them are <xref:System.String.Contains%2A>, <xref:System.String.StartsWith%2A>, <xref:System.String.EndsWith%2A>, <xref:System.String.IndexOf%2A>, <xref:System.String.LastIndexOf%2A>.</span></span> <span data-ttu-id="6eb7f-108"><xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> 類別提供豐富的詞彙來搜尋文字中的模式。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-108">The <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> class provides a rich vocabulary to search for patterns in text.</span></span> <span data-ttu-id="6eb7f-109">在本文中，您了解這些技術，以及如何選擇您需求的最佳方法。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-109">In this article, you learn these techniques and how to choose the best method for your needs.</span></span>

## <a name="does-a-string-contain-text"></a><span data-ttu-id="6eb7f-110">字串是否包含文字？</span><span class="sxs-lookup"><span data-stu-id="6eb7f-110">Does a string contain text?</span></span>

<span data-ttu-id="6eb7f-111"><xref:System.String.Contains%2A?displayProperty=nameWithType>、<xref:System.String.StartsWith%2A?displayProperty=nameWithType> 和 <xref:System.String.EndsWith%2A?displayProperty=nameWithType> 方法會搜尋字串中的特定文字。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-111">The <xref:System.String.Contains%2A?displayProperty=nameWithType>, <xref:System.String.StartsWith%2A?displayProperty=nameWithType> and <xref:System.String.EndsWith%2A?displayProperty=nameWithType> methods search a string for specific text.</span></span> <span data-ttu-id="6eb7f-112">下列範例示範所有這些方法，以及使用不區分大小寫搜尋的變化：</span><span class="sxs-lookup"><span data-stu-id="6eb7f-112">The following example shows each of these methods and a variation that uses a case insensitive search:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs" id="Snippet1":::

<span data-ttu-id="6eb7f-113">上述範例示範這些方法的使用重點。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-113">The preceding example demonstrates an important point for using these methods.</span></span> <span data-ttu-id="6eb7f-114">搜尋預設會**區分大小寫**。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-114">Searches are **case-sensitive** by default.</span></span> <span data-ttu-id="6eb7f-115">您可以使用 <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> 列舉值，來指定不區分大小寫的搜尋。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-115">You use the <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> enum value to specify a case insensitive search.</span></span>

## <a name="where-does-the-sought-text-occur-in-a-string"></a><span data-ttu-id="6eb7f-116">所搜尋文字在字串中的位置？</span><span class="sxs-lookup"><span data-stu-id="6eb7f-116">Where does the sought text occur in a string?</span></span>

<span data-ttu-id="6eb7f-117"><xref:System.String.IndexOf%2A> 和 <xref:System.String.LastIndexOf%2A> 方法也會搜尋字串中的文字。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-117">The <xref:System.String.IndexOf%2A> and <xref:System.String.LastIndexOf%2A> methods also search for text in strings.</span></span> <span data-ttu-id="6eb7f-118">這些方法會傳回所搜尋文字的位置。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-118">These methods return the location of the text being sought.</span></span> <span data-ttu-id="6eb7f-119">如果找不到文字，則會傳回 `-1`。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-119">If the text isn't found, they return `-1`.</span></span> <span data-ttu-id="6eb7f-120">下列範例示範如何搜尋 "methods" 這個單字的第一個和最後一個相符項目，並在其間顯示文字。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-120">The following example shows a search for the first and last occurrence of the word "methods" and displays the text in between.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs" id="Snippet2":::

## <a name="finding-specific-text-using-regular-expressions"></a><span data-ttu-id="6eb7f-121">使用規則運算式來尋找特定文字</span><span class="sxs-lookup"><span data-stu-id="6eb7f-121">Finding specific text using regular expressions</span></span>

<span data-ttu-id="6eb7f-122"><xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> 類別可以用來搜尋字串。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-122">The <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> class can be used to search strings.</span></span> <span data-ttu-id="6eb7f-123">這些搜尋的複雜性範圍可以從簡單到複雜文字模式。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-123">These searches can range in complexity from simple to complicated text patterns.</span></span>

<span data-ttu-id="6eb7f-124">下列程式碼範例會搜尋句子中的 "the" 或 "their" 單字，但忽略大小寫。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-124">The following code example searches for the word "the" or "their" in a sentence, ignoring case.</span></span> <span data-ttu-id="6eb7f-125">靜態方法 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> 會執行搜尋。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-125">The static method <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> performs the search.</span></span> <span data-ttu-id="6eb7f-126">您為其指定要搜尋的字串和搜尋模式。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-126">You give it the string to search and a search pattern.</span></span> <span data-ttu-id="6eb7f-127">在此情況下，第三個引數指定不區分大小寫的搜尋。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-127">In this case, a third argument specifies case-insensitive search.</span></span> <span data-ttu-id="6eb7f-128">如需詳細資訊，請參閱 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-128">For more information, see <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="6eb7f-129">搜尋模式描述您搜尋的文字。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-129">The search pattern describes the text you search for.</span></span> <span data-ttu-id="6eb7f-130">下表描述搜尋模式的每個項目 </span><span class="sxs-lookup"><span data-stu-id="6eb7f-130">The following table describes each element of the search pattern.</span></span> <span data-ttu-id="6eb7f-131">(下表使用單一 `\`，其在 C# 字串中必須逸出為 `\\`)。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-131">(The table below uses the single `\` which must be escaped as `\\` in a C# string).</span></span>

| <span data-ttu-id="6eb7f-132">模式</span><span class="sxs-lookup"><span data-stu-id="6eb7f-132">Pattern</span></span>  | <span data-ttu-id="6eb7f-133">意義</span><span class="sxs-lookup"><span data-stu-id="6eb7f-133">Meaning</span></span>                          |
|----------|----------------------------------|
| `the`    | <span data-ttu-id="6eb7f-134">比對文字 "the"</span><span class="sxs-lookup"><span data-stu-id="6eb7f-134">match the text "the"</span></span>             |
| `(eir)?` | <span data-ttu-id="6eb7f-135">比對 "eir" 的 0 或 1 個出現次數</span><span class="sxs-lookup"><span data-stu-id="6eb7f-135">match 0 or 1 occurrence of "eir"</span></span> |
| `\s`     | <span data-ttu-id="6eb7f-136">比對空白字元</span><span class="sxs-lookup"><span data-stu-id="6eb7f-136">match a white-space character</span></span>    |

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs" id="Snippet3":::

> [!TIP]
> <span data-ttu-id="6eb7f-137">當您搜尋完全相符的字串時，`string` 方法通常是較好的選擇。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-137">The `string` methods are usually better choices when you are searching for an exact string.</span></span> <span data-ttu-id="6eb7f-138">當您在來源字串中搜尋某個模式時，正則運算式會更好。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-138">Regular expressions are better when you are searching for some pattern in a source string.</span></span>

## <a name="does-a-string-follow-a-pattern"></a><span data-ttu-id="6eb7f-139">字串遵循模式嗎？</span><span class="sxs-lookup"><span data-stu-id="6eb7f-139">Does a string follow a pattern?</span></span>

<span data-ttu-id="6eb7f-140">下列程式碼使用規則運算式來驗證陣列中每個字串的格式。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-140">The following code uses regular expressions to validate the format of each string in an array.</span></span> <span data-ttu-id="6eb7f-141">驗證需要每個字串具有電話號碼的形式，其中數字的三個群組以連字號分隔、前兩個群組包含三位數，而第三個群組包含四位數。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-141">The validation requires that each string have the form of a telephone number in which three groups of digits are separated by dashes, the first two groups contain three digits, and the third group contains four digits.</span></span> <span data-ttu-id="6eb7f-142">搜尋模式使用規則運算式 `^\\d{3}-\\d{3}-\\d{4}$`。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-142">The search pattern uses the regular expression `^\\d{3}-\\d{3}-\\d{4}$`.</span></span> <span data-ttu-id="6eb7f-143">如需詳細資訊，請參閱[規則運算式語言 - 快速參考](../../standard/base-types/regular-expression-language-quick-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-143">For more information, see [Regular Expression Language - Quick Reference](../../standard/base-types/regular-expression-language-quick-reference.md).</span></span>

| <span data-ttu-id="6eb7f-144">模式</span><span class="sxs-lookup"><span data-stu-id="6eb7f-144">Pattern</span></span> | <span data-ttu-id="6eb7f-145">意義</span><span class="sxs-lookup"><span data-stu-id="6eb7f-145">Meaning</span></span>                             |
|---------|-------------------------------------|
| `^`     | <span data-ttu-id="6eb7f-146">比對字串的開頭</span><span class="sxs-lookup"><span data-stu-id="6eb7f-146">matches the beginning of the string</span></span> |
| `\d{3}` | <span data-ttu-id="6eb7f-147">僅比對 3 位數的字元</span><span class="sxs-lookup"><span data-stu-id="6eb7f-147">matches exactly 3 digit characters</span></span>  |
| `-`     | <span data-ttu-id="6eb7f-148">比對 '-' 字元</span><span class="sxs-lookup"><span data-stu-id="6eb7f-148">matches the '-' character</span></span>           |
| `\d{3}` | <span data-ttu-id="6eb7f-149">僅比對 3 位數的字元</span><span class="sxs-lookup"><span data-stu-id="6eb7f-149">matches exactly 3 digit characters</span></span>  |
| `-`     | <span data-ttu-id="6eb7f-150">比對 '-' 字元</span><span class="sxs-lookup"><span data-stu-id="6eb7f-150">matches the '-' character</span></span>           |
| `\d{4}` | <span data-ttu-id="6eb7f-151">僅比對 4 位數的字元</span><span class="sxs-lookup"><span data-stu-id="6eb7f-151">matches exactly 4 digit characters</span></span>  |
| `$`     | <span data-ttu-id="6eb7f-152">比對字串的結尾</span><span class="sxs-lookup"><span data-stu-id="6eb7f-152">matches the end of the string</span></span>       |

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs" id="Snippet4":::

<span data-ttu-id="6eb7f-153">此單一搜尋模式會比對許多有效字串。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-153">This single search pattern matches many valid strings.</span></span> <span data-ttu-id="6eb7f-154">規則運算式較適合用來搜尋或驗證模式，而不是單一文字字串。</span><span class="sxs-lookup"><span data-stu-id="6eb7f-154">Regular expressions are better to search for or validate against a pattern, rather than a single text string.</span></span>

## <a name="see-also"></a><span data-ttu-id="6eb7f-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6eb7f-155">See also</span></span>

- [<span data-ttu-id="6eb7f-156">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="6eb7f-156">C# programming guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="6eb7f-157">字串</span><span class="sxs-lookup"><span data-stu-id="6eb7f-157">Strings</span></span>](../programming-guide/strings/index.md)
- [<span data-ttu-id="6eb7f-158">LINQ 和字串</span><span class="sxs-lookup"><span data-stu-id="6eb7f-158">LINQ and strings</span></span>](../programming-guide/concepts/linq/linq-and-strings.md)
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- [<span data-ttu-id="6eb7f-159">.NET Framework 正則運算式</span><span class="sxs-lookup"><span data-stu-id="6eb7f-159">.NET Framework regular expressions</span></span>](../../standard/base-types/regular-expressions.md)
- [<span data-ttu-id="6eb7f-160">正則運算式語言-快速參考</span><span class="sxs-lookup"><span data-stu-id="6eb7f-160">Regular expression language - quick reference</span></span>](../../standard/base-types/regular-expression-language-quick-reference.md)
- [<span data-ttu-id="6eb7f-161">在 .NET 中使用字串的最佳作法</span><span class="sxs-lookup"><span data-stu-id="6eb7f-161">Best practices for using strings in .NET</span></span>](../../standard/base-types/best-practices-strings.md)
