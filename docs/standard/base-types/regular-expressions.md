---
title: .NET 規則運算式
description: 使用正則運算式來尋找特定字元模式、驗證文字、使用文字子字串，& 在 .NET 中將解壓縮的字串新增至集合。
ms.topic: conceptual
ms.date: 06/30/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pattern-matching with regular expressions, about pattern-matching
- substrings
- searching with regular expressions, about regular expressions
- pattern-matching with regular expressions
- searching with regular expressions
- parsing text with regular expressions
- regular expressions [.NET], about regular expressions
- regular expressions [.NET]
- .NET regular expressions, about
- characters [.NET], regular expressions
- parsing text with regular expressions, overview
- .NET regular expressions
- strings [.NET], regular expressions
ms.assetid: 521b3f6d-f869-42e1-93e5-158c54a6895d
ms.openlocfilehash: ea6b16909b79236245b35238ad43d778eec3051a
ms.sourcegitcommit: 4313614f57690f9a5119a37314f0a1fd738ebda2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2021
ms.locfileid: "98692769"
---
# <a name="net-regular-expressions"></a><span data-ttu-id="bc8f6-103">.NET 規則運算式</span><span class="sxs-lookup"><span data-stu-id="bc8f6-103">.NET regular expressions</span></span>

<span data-ttu-id="bc8f6-104">規則運算式提供功能強大、彈性且有效率的方法來處理文字。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-104">Regular expressions provide a powerful, flexible, and efficient method for processing text.</span></span> <span data-ttu-id="bc8f6-105">正則運算式的廣泛模式比對標記法可讓您快速剖析大量文字，以：</span><span class="sxs-lookup"><span data-stu-id="bc8f6-105">The extensive pattern-matching notation of regular expressions enables you to quickly parse large amounts of text to:</span></span>

- <span data-ttu-id="bc8f6-106">尋找特定的字元模式。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-106">Find specific character patterns.</span></span>
- <span data-ttu-id="bc8f6-107">驗證文字，以確保它符合預先定義的模式 (例如電子郵件地址) 。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-107">Validate text to ensure that it matches a predefined pattern (such as an email address).</span></span>
- <span data-ttu-id="bc8f6-108">解壓縮、編輯、取代或刪除文字子字串。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-108">Extract, edit, replace, or delete text substrings.</span></span>
- <span data-ttu-id="bc8f6-109">將解壓縮的字串加入至集合，以便產生報表。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-109">Add extracted strings to a collection in order to generate a report.</span></span>

<span data-ttu-id="bc8f6-110">對許多處理字串或剖析大型文字區塊的應用程式而言，規則運算式是不可或缺的工具。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-110">For many applications that deal with strings or that parse large blocks of text, regular expressions are an indispensable tool.</span></span>  
  
## <a name="how-regular-expressions-work"></a><span data-ttu-id="bc8f6-111">正則運算式的運作方式</span><span class="sxs-lookup"><span data-stu-id="bc8f6-111">How regular expressions work</span></span>

 <span data-ttu-id="bc8f6-112">使用規則運算式來處理文字的核心是規則運算式引擎，以 .NET 中的 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> 物件來表示。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-112">The centerpiece of text processing with regular expressions is the regular expression engine, which is represented by the <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> object in .NET.</span></span> <span data-ttu-id="bc8f6-113">使用規則運算式來處理文字時，至少需要提供規則運算式引擎以及下列兩個資訊項目：</span><span class="sxs-lookup"><span data-stu-id="bc8f6-113">At a minimum, processing text using regular expressions requires that the regular expression engine be provided with the following two items of information:</span></span>  
  
- <span data-ttu-id="bc8f6-114">要在文字中識別的規則運算式模式。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-114">The regular expression pattern to identify in the text.</span></span>  
  
     <span data-ttu-id="bc8f6-115">在 .NET 中，規則運算式模式是以特殊的語法或語言來定義，其相容於 Perl 5 規則運算式，並新增一些其他功能，例如由右至左比對。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-115">In .NET, regular expression patterns are defined by a special syntax or language, which is compatible with Perl 5 regular expressions and adds some additional features such as right-to-left matching.</span></span> <span data-ttu-id="bc8f6-116">如需詳細資訊，請參閱[規則運算式語言 - 快速參考](regular-expression-language-quick-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-116">For more information, see [Regular Expression Language - Quick Reference](regular-expression-language-quick-reference.md).</span></span>  
  
- <span data-ttu-id="bc8f6-117">要為規則運算式模式剖析的文字。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-117">The text to parse for the regular expression pattern.</span></span>  
  
<span data-ttu-id="bc8f6-118"><xref:System.Text.RegularExpressions.Regex> 類別的方法可讓您執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="bc8f6-118">The methods of the <xref:System.Text.RegularExpressions.Regex> class let you perform the following operations:</span></span>  
  
- <span data-ttu-id="bc8f6-119">呼叫 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> 方法，以判定規則運算式模式是否出現在輸入文字中。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-119">Determine whether the regular expression pattern occurs in the input text by calling the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="bc8f6-120">如需使用 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> 方法來驗證文字的範例，請參閱[如何：確認字串是否為有效的電子郵件格式](how-to-verify-that-strings-are-in-valid-email-format.md)。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-120">For an example that uses the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method for validating text, see [How to: Verify that Strings Are in Valid Email Format](how-to-verify-that-strings-are-in-valid-email-format.md).</span></span>  
  
- <span data-ttu-id="bc8f6-121">呼叫 <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> 或 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> 方法，以擷取符合規則運算式模式的所有文字。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-121">Retrieve one or all occurrences of text that matches the regular expression pattern by calling the <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> or <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="bc8f6-122">前一個方法會傳回 <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> 物件，提供相符文字的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-122">The former method returns a <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> object that provides information about the matching text.</span></span> <span data-ttu-id="bc8f6-123">後一個方法會傳回 <xref:System.Text.RegularExpressions.MatchCollection> 物件，其中針對在所剖析文字中找到的每個相符項目，各包含一個 <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> 物件。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-123">The latter returns a <xref:System.Text.RegularExpressions.MatchCollection> object that contains one <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> object for each match found in the parsed text.</span></span>  
  
- <span data-ttu-id="bc8f6-124">呼叫 <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> 方法，以取代符合規則運算式模式的文字。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-124">Replace text that matches the regular expression pattern by calling the <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="bc8f6-125">如需使用 <xref:System.Text.RegularExpressions.Regex.Replace%2A> 方法來變更日期格式，以及移除字串中無效字元的範例，請參閱[如何：從字串中刪除無效的字元](how-to-strip-invalid-characters-from-a-string.md)和[如何：變更日期格式](regular-expression-example-changing-date-formats.md)。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-125">For examples that use the <xref:System.Text.RegularExpressions.Regex.Replace%2A> method to change date formats and remove invalid characters from a string, see [How to: Strip Invalid Characters from a String](how-to-strip-invalid-characters-from-a-string.md) and [Example: Changing Date Formats](regular-expression-example-changing-date-formats.md).</span></span>  
  
<span data-ttu-id="bc8f6-126">如需規則運算式物件模型概觀，請參閱[規則運算式物件模型](the-regular-expression-object-model.md)。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-126">For an overview of the regular expression object model, see [The Regular Expression Object Model](the-regular-expression-object-model.md).</span></span>  
  
<span data-ttu-id="bc8f6-127">如需規則運算式語言的詳細資訊，請參閱[規則運算式語言 - 快速參考](regular-expression-language-quick-reference.md)，或下載並列印下列其中一本小手冊：</span><span class="sxs-lookup"><span data-stu-id="bc8f6-127">For more information about the regular expression language, see [Regular Expression Language - Quick Reference](regular-expression-language-quick-reference.md) or download and print one of these brochures:</span></span>  
  
- [<span data-ttu-id="bc8f6-128">Word (.docx) 格式的快速參考</span><span class="sxs-lookup"><span data-stu-id="bc8f6-128">Quick Reference in Word (.docx) format</span></span>](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
- [<span data-ttu-id="bc8f6-129">PDF (.pdf) 格式的快速參考</span><span class="sxs-lookup"><span data-stu-id="bc8f6-129">Quick Reference in PDF (.pdf) format</span></span>](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)  
  
## <a name="regular-expression-examples"></a><span data-ttu-id="bc8f6-130">規則運算式範例</span><span class="sxs-lookup"><span data-stu-id="bc8f6-130">Regular expression examples</span></span>

<span data-ttu-id="bc8f6-131"><xref:System.String> 類別包含數種字串搜尋和取代方法，可供您在大型字串中尋找常值字串時使用。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-131">The <xref:System.String> class includes a number of string search and replacement methods that you can use when you want to locate literal strings in a larger string.</span></span> <span data-ttu-id="bc8f6-132">當您想要在大型字串中尋找數個子字串時，或是當您想要識別字串中的模式時，規則運算式最為好用，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-132">Regular expressions are most useful either when you want to locate one of several substrings in a larger string, or when you want to identify patterns in a string, as the following examples illustrate.</span></span>

[!INCLUDE [regex](../../../includes/regex.md)]

> [!TIP]
> <span data-ttu-id="bc8f6-133"><xref:System.Web.RegularExpressions> 命名空間包含一些規則運算式物件，這些物件會實作預先定義的規則運算式模式，以用於剖析來自 HTML、XML 和 ASP.NET 文件的字串。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-133">The <xref:System.Web.RegularExpressions> namespace contains a number of regular expression objects that implement predefined regular expression patterns for parsing strings from HTML, XML, and ASP.NET documents.</span></span> <span data-ttu-id="bc8f6-134">例如，<xref:System.Web.RegularExpressions.TagRegex> 類別會識別字串中的開始標記，而 <xref:System.Web.RegularExpressions.CommentRegex> 類別會識別字串中的 ASP.NET 註解。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-134">For example, the <xref:System.Web.RegularExpressions.TagRegex> class identifies start tags in a string and the <xref:System.Web.RegularExpressions.CommentRegex> class identifies ASP.NET comments in a string.</span></span>

### <a name="example-1-replace-substrings"></a><span data-ttu-id="bc8f6-135">範例1：取代子字串</span><span class="sxs-lookup"><span data-stu-id="bc8f6-135">Example 1: Replace substrings</span></span>  

 <span data-ttu-id="bc8f6-136">假設郵寄清單包含的名稱有時候會包括稱謂 (Mr.、Mrs.、Miss 或 Ms.) 以及姓名。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-136">Assume that a mailing list contains names that sometimes include a title (Mr., Mrs., Miss, or Ms.) along with a first and last name.</span></span> <span data-ttu-id="bc8f6-137">當您從清單產生信封標籤時，如果不想包括稱謂，就可以使用規則運算式來移除稱謂，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-137">If you do not want to include the titles when you generate envelope labels from the list, you can use a regular expression to remove the titles, as the following example illustrates.</span></span>  
  
 [!code-csharp[Conceptual.Regex#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example1.cs#2)]
 [!code-vb[Conceptual.Regex#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example1.vb#2)]  
  
 <span data-ttu-id="bc8f6-138">規則運算式模式 `(Mr\.? |Mrs\.? |Miss |Ms\.? )` 會比對所出現的任何 "Mr "、"Mr. "、"Mrs "、"Mrs. "、"Miss "、"Ms 或 "Ms. "。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-138">The regular expression pattern `(Mr\.? |Mrs\.? |Miss |Ms\.? )` matches any occurrence of "Mr ", "Mr. ", "Mrs ", "Mrs. ", "Miss ", "Ms or "Ms. ".</span></span> <span data-ttu-id="bc8f6-139">呼叫 <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> 方法會將相符的字串取代為 <xref:System.String.Empty?displayProperty=nameWithType>；換句話說，就是將其從原始字串中移除。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-139">The call to the <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method replaces the matched string with <xref:System.String.Empty?displayProperty=nameWithType>; in other words, it removes it from the original string.</span></span>  
  
### <a name="example-2-identify-duplicated-words"></a><span data-ttu-id="bc8f6-140">範例2：識別重複的字組</span><span class="sxs-lookup"><span data-stu-id="bc8f6-140">Example 2: Identify duplicated words</span></span>  

 <span data-ttu-id="bc8f6-141">不小心重複文字是作者常犯的錯誤。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-141">Accidentally duplicating words is a common error that writers make.</span></span> <span data-ttu-id="bc8f6-142">規則運算式可用來識別重複的文字，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-142">A regular expression can be used to identify duplicated words, as the following example shows.</span></span>  
  
 [!code-csharp[Conceptual.Regex#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example2.cs#3)]
 [!code-vb[Conceptual.Regex#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example2.vb#3)]  
  
 <span data-ttu-id="bc8f6-143">規則運算式模式 `\b(\w+?)\s\1\b` 可解譯如下：</span><span class="sxs-lookup"><span data-stu-id="bc8f6-143">The regular expression pattern `\b(\w+?)\s\1\b` can be interpreted as follows:</span></span>  
  
> [!div class="mx-tdCol2BreakAll"]
> |<span data-ttu-id="bc8f6-144">模式</span><span class="sxs-lookup"><span data-stu-id="bc8f6-144">Pattern</span></span>|<span data-ttu-id="bc8f6-145">解讀</span><span class="sxs-lookup"><span data-stu-id="bc8f6-145">Interpretation</span></span>|  
> |-|-|
> |`\b`|<span data-ttu-id="bc8f6-146">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-146">Start at a word boundary.</span></span>|  
> |`(\w+?)`|<span data-ttu-id="bc8f6-147">比對一或多個字元，但字元數愈少愈好。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-147">Match one or more word characters, but as few characters as possible.</span></span> <span data-ttu-id="bc8f6-148">這些一起構成可稱之為 `\1` 的群組。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-148">Together, they form a group that can be referred to as `\1`.</span></span>|  
> |`\s`|<span data-ttu-id="bc8f6-149">比對空白字元。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-149">Match a white-space character.</span></span>|  
> |`\1`|<span data-ttu-id="bc8f6-150">比對等同於名為 `\1` 之群組的子字串。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-150">Match the substring that is equal to the group named `\1`.</span></span>|  
> |`\b`|<span data-ttu-id="bc8f6-151">比對字邊界。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-151">Match a word boundary.</span></span>|  
  
 <span data-ttu-id="bc8f6-152">呼叫 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> 方法時，規則運算式選項設為 <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-152">The <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> method is called with regular expression options set to <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bc8f6-153">因此，比對作業不區分大小寫，而且此範例會將子字串 "This this" 視為重複。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-153">Therefore, the match operation is case-insensitive, and the example identifies the substring "This this" as a duplication.</span></span>  
  
 <span data-ttu-id="bc8f6-154">輸入字串包含子字串 "this？</span><span class="sxs-lookup"><span data-stu-id="bc8f6-154">The input string includes the substring "this?</span></span> <span data-ttu-id="bc8f6-155">This"。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-155">This".</span></span> <span data-ttu-id="bc8f6-156">不過，因為中間有標點符號，所以不會將其視為重複。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-156">However, because of the intervening punctuation mark, it is not identified as a duplication.</span></span>  
  
### <a name="example-3-dynamically-build-a-culture-sensitive-regular-expression"></a><span data-ttu-id="bc8f6-157">範例3：動態建立區分文化特性的正則運算式</span><span class="sxs-lookup"><span data-stu-id="bc8f6-157">Example 3: Dynamically build a culture-sensitive regular expression</span></span>  

 <span data-ttu-id="bc8f6-158">下列範例說明規則運算式結合 .NET 全球化功能所提供的彈性，功能有多麼強大。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-158">The following example illustrates the power of regular expressions combined with the flexibility offered by .NET's globalization features.</span></span> <span data-ttu-id="bc8f6-159">它會使用 <xref:System.Globalization.NumberFormatInfo> 物件來判定系統目前文化特性中的幣值格式，</span><span class="sxs-lookup"><span data-stu-id="bc8f6-159">It uses the <xref:System.Globalization.NumberFormatInfo> object to determine the format of currency values in the system's current culture.</span></span> <span data-ttu-id="bc8f6-160">然後利用該資訊動態建構可從文字擷取幣值的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-160">It then uses that information to dynamically construct a regular expression that extracts currency values from the text.</span></span> <span data-ttu-id="bc8f6-161">針對每個比對，它會擷取僅包含數值字串的子群組，將其轉換成 <xref:System.Decimal> 值，並計算執行總計。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-161">For each match, it extracts the subgroup that contains the numeric string only, converts it to a <xref:System.Decimal> value, and calculates a running total.</span></span>  
  
 [!code-csharp[Conceptual.Regex#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example.cs#1)]
 [!code-vb[Conceptual.Regex#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example.vb#1)]  
  
 <span data-ttu-id="bc8f6-162">在目前文化特性為 English - United States (en-US) 的電腦上，此範例會動態建立規則運算式 `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-162">On a computer whose current culture is English - United States (en-US), the example dynamically builds the regular expression `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`.</span></span> <span data-ttu-id="bc8f6-163">此規則運算式模式可解譯如下：</span><span class="sxs-lookup"><span data-stu-id="bc8f6-163">This regular expression pattern can be interpreted as follows:</span></span>  

> [!div class="mx-tdCol2BreakAll"]
> |<span data-ttu-id="bc8f6-164">模式</span><span class="sxs-lookup"><span data-stu-id="bc8f6-164">Pattern</span></span>|<span data-ttu-id="bc8f6-165">解讀</span><span class="sxs-lookup"><span data-stu-id="bc8f6-165">Interpretation</span></span>|  
> |-|-|  
> |`\$`|<span data-ttu-id="bc8f6-166">在輸入字串中尋找單獨出現的貨幣符號 (`$`)。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-166">Look for a single occurrence of the dollar symbol (`$`) in the input string.</span></span> <span data-ttu-id="bc8f6-167">規則運算式模式字串包含反斜線，表示貨幣符號要解譯為字面意義，而不是規則運算式錨點。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-167">The regular expression pattern string includes a backslash to indicate that the dollar symbol is to be interpreted literally rather than as a regular expression anchor.</span></span> <span data-ttu-id="bc8f6-168">單獨 (`$` 符號，表示正則運算式引擎應該嘗試在字串結尾處開始比對 ) 。若要確保目前文化特性的貨幣符號不會誤譯為正則運算式符號，此範例會呼叫 <xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=nameWithType> 方法來將該字元換用。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-168">(The `$` symbol alone would indicate that the regular expression engine should try to begin its match at the end of a string.) To ensure that the current culture's currency symbol is not misinterpreted as a regular expression symbol, the example calls the <xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=nameWithType> method to escape the character.</span></span>|  
> |`\s*`|<span data-ttu-id="bc8f6-169">尋找出現零或多次的空格字元。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-169">Look for zero or more occurrences of a white-space character.</span></span>|  
> |`[-+]?`|<span data-ttu-id="bc8f6-170">尋找出現一或多次的正號或負號。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-170">Look for zero or one occurrence of either a positive sign or a negative sign.</span></span>|  
> |`([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`|<span data-ttu-id="bc8f6-171">此運算式外面括號將其定義成擷取群組或子運算式。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-171">The outer parentheses around this expression define it as a capturing group or a subexpression.</span></span> <span data-ttu-id="bc8f6-172">如果找到相符項目，從 <xref:System.Text.RegularExpressions.Group> 屬性傳回之 <xref:System.Text.RegularExpressions.GroupCollection> 物件中的第二個 <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> 物件，擷取此部分比對字串的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-172">If a match is found, information about this part of the matching string can be retrieved from the second <xref:System.Text.RegularExpressions.Group> object in the <xref:System.Text.RegularExpressions.GroupCollection> object returned by the <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="bc8f6-173">(集合中的第一個項目代表整個比對。)</span><span class="sxs-lookup"><span data-stu-id="bc8f6-173">(The first element in the collection represents the entire match.)</span></span>|  
> |`[0-9]{0,3}`|<span data-ttu-id="bc8f6-174">尋找出現零到三次的十進位數字 0 到 9。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-174">Look for zero to three occurrences of the decimal digits 0 through 9.</span></span>|  
> |`(,[0-9]{3})*`|<span data-ttu-id="bc8f6-175">尋找出現零或多次、後面接三個十進位數字的群組分隔符號。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-175">Look for zero or more occurrences of a group separator followed by three decimal digits.</span></span>|  
> |`\.`|<span data-ttu-id="bc8f6-176">尋找單次出現的十進位分隔符號。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-176">Look for a single occurrence of the decimal separator.</span></span>|  
> |`[0-9]+`|<span data-ttu-id="bc8f6-177">尋找一或多個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-177">Look for one or more decimal digits.</span></span>|  
> |`(\.[0-9]+)?`|<span data-ttu-id="bc8f6-178">尋找出現零或一次、後接至少一個十進位數字的十進位分隔符號。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-178">Look for zero or one occurrence of the decimal separator followed by at least one decimal digit.</span></span>|  
  
 <span data-ttu-id="bc8f6-179">如果在輸入字串中找到上述每個子模式，則比對成功，並且會將包含此比對相關資訊的 <xref:System.Text.RegularExpressions.Match> 物件加入至 <xref:System.Text.RegularExpressions.MatchCollection> 物件。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-179">If each of these subpatterns is found in the input string, the match succeeds, and a <xref:System.Text.RegularExpressions.Match> object that contains information about the match is added to the <xref:System.Text.RegularExpressions.MatchCollection> object.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="bc8f6-180">相關主題</span><span class="sxs-lookup"><span data-stu-id="bc8f6-180">Related topics</span></span>  
  
|<span data-ttu-id="bc8f6-181">標題</span><span class="sxs-lookup"><span data-stu-id="bc8f6-181">Title</span></span>|<span data-ttu-id="bc8f6-182">描述</span><span class="sxs-lookup"><span data-stu-id="bc8f6-182">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="bc8f6-183">規則運算式語言 - 快速參考</span><span class="sxs-lookup"><span data-stu-id="bc8f6-183">Regular Expression Language - Quick Reference</span></span>](regular-expression-language-quick-reference.md)|<span data-ttu-id="bc8f6-184">提供您可以用來定義規則運算式之字元、運算子和建構組合的資訊。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-184">Provides information on the set of characters, operators, and constructs that you can use to define regular expressions.</span></span>|  
|[<span data-ttu-id="bc8f6-185">規則運算式物件模型</span><span class="sxs-lookup"><span data-stu-id="bc8f6-185">The Regular Expression Object Model</span></span>](the-regular-expression-object-model.md)|<span data-ttu-id="bc8f6-186">提供資訊和程式碼範例，說明如何使用規則運算式類別。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-186">Provides information and code examples that illustrate how to use the regular expression classes.</span></span>|  
|[<span data-ttu-id="bc8f6-187">規則運算式行為的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="bc8f6-187">Details of Regular Expression Behavior</span></span>](details-of-regular-expression-behavior.md)|<span data-ttu-id="bc8f6-188">提供 .NET 規則運算式之功能和行為的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="bc8f6-188">Provides information about the capabilities and behavior of .NET regular expressions.</span></span>|
|[<span data-ttu-id="bc8f6-189">在 Visual Studio 中使用正則運算式</span><span class="sxs-lookup"><span data-stu-id="bc8f6-189">Use regular expressions in Visual Studio</span></span>](/visualstudio/ide/using-regular-expressions-in-visual-studio)||
  
## <a name="reference"></a><span data-ttu-id="bc8f6-190">參考</span><span class="sxs-lookup"><span data-stu-id="bc8f6-190">Reference</span></span>  

- <xref:System.Text.RegularExpressions?displayProperty=nameWithType>  
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>  
- [<span data-ttu-id="bc8f6-191">規則運算式 - 快速參考 (以 Word 格式下載)</span><span class="sxs-lookup"><span data-stu-id="bc8f6-191">Regular Expressions - Quick Reference (download in Word format)</span></span>](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
- [<span data-ttu-id="bc8f6-192">規則運算式 - 快速參考 (以 PDF 格式下載)</span><span class="sxs-lookup"><span data-stu-id="bc8f6-192">Regular Expressions - Quick Reference (download in PDF format)</span></span>](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
