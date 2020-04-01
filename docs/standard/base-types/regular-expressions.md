---
title: .NET Framework 規則運算式
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
- regular expressions [.NET Framework], about regular expressions
- regular expressions [.NET Framework]
- .NET Framework regular expressions, about
- characters [.NET Framework], regular expressions
- parsing text with regular expressions, overview
- .NET Framework regular expressions
- strings [.NET Framework], regular expressions
ms.assetid: 521b3f6d-f869-42e1-93e5-158c54a6895d
ms.openlocfilehash: 99a70fa1b56a45087ee380d063c66326976f5b41
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523789"
---
# <a name="net-regular-expressions"></a><span data-ttu-id="b871d-102">.NET 規則運算式</span><span class="sxs-lookup"><span data-stu-id="b871d-102">.NET regular expressions</span></span>

<span data-ttu-id="b871d-103">規則運算式提供功能強大、彈性且有效率的方法來處理文字。</span><span class="sxs-lookup"><span data-stu-id="b871d-103">Regular expressions provide a powerful, flexible, and efficient method for processing text.</span></span> <span data-ttu-id="b871d-104">一般表示式的粗模式匹配表示法使您能夠快速分析大量文本,以便:</span><span class="sxs-lookup"><span data-stu-id="b871d-104">The extensive pattern-matching notation of regular expressions enables you to quickly parse large amounts of text to:</span></span>

- <span data-ttu-id="b871d-105">尋找特定的字元模式。</span><span class="sxs-lookup"><span data-stu-id="b871d-105">Find specific character patterns.</span></span>
- <span data-ttu-id="b871d-106">驗證文本以確保與預定義的模式(如電子郵寄地址)匹配。</span><span class="sxs-lookup"><span data-stu-id="b871d-106">Validate text to ensure that it matches a predefined pattern (such as an email address).</span></span>
- <span data-ttu-id="b871d-107">提取、編輯、替換或刪除文字子字串。</span><span class="sxs-lookup"><span data-stu-id="b871d-107">Extract, edit, replace, or delete text substrings.</span></span>
- <span data-ttu-id="b871d-108">將提取的字串添加到集合以生成報表。</span><span class="sxs-lookup"><span data-stu-id="b871d-108">Add extracted strings to a collection in order to generate a report.</span></span>

<span data-ttu-id="b871d-109">對許多處理字串或剖析大型文字區塊的應用程式而言，規則運算式是不可或缺的工具。</span><span class="sxs-lookup"><span data-stu-id="b871d-109">For many applications that deal with strings or that parse large blocks of text, regular expressions are an indispensable tool.</span></span>  
  
## <a name="how-regular-expressions-work"></a><span data-ttu-id="b871d-110">正規表示式的工作原理</span><span class="sxs-lookup"><span data-stu-id="b871d-110">How regular expressions work</span></span>

 <span data-ttu-id="b871d-111">使用規則運算式來處理文字的核心是規則運算式引擎，以 .NET 中的 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> 物件來表示。</span><span class="sxs-lookup"><span data-stu-id="b871d-111">The centerpiece of text processing with regular expressions is the regular expression engine, which is represented by the <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> object in .NET.</span></span> <span data-ttu-id="b871d-112">使用規則運算式來處理文字時，至少需要提供規則運算式引擎以及下列兩個資訊項目：</span><span class="sxs-lookup"><span data-stu-id="b871d-112">At a minimum, processing text using regular expressions requires that the regular expression engine be provided with the following two items of information:</span></span>  
  
- <span data-ttu-id="b871d-113">要在文字中識別的規則運算式模式。</span><span class="sxs-lookup"><span data-stu-id="b871d-113">The regular expression pattern to identify in the text.</span></span>  
  
     <span data-ttu-id="b871d-114">在 .NET 中，規則運算式模式是以特殊的語法或語言來定義，其相容於 Perl 5 規則運算式，並新增一些其他功能，例如由右至左比對。</span><span class="sxs-lookup"><span data-stu-id="b871d-114">In .NET, regular expression patterns are defined by a special syntax or language, which is compatible with Perl 5 regular expressions and adds some additional features such as right-to-left matching.</span></span> <span data-ttu-id="b871d-115">如需詳細資訊，請參閱[規則運算式語言 - 快速參考](regular-expression-language-quick-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="b871d-115">For more information, see [Regular Expression Language - Quick Reference](regular-expression-language-quick-reference.md).</span></span>  
  
- <span data-ttu-id="b871d-116">要為規則運算式模式剖析的文字。</span><span class="sxs-lookup"><span data-stu-id="b871d-116">The text to parse for the regular expression pattern.</span></span>  
  
<span data-ttu-id="b871d-117"><xref:System.Text.RegularExpressions.Regex> 類別的方法可讓您執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="b871d-117">The methods of the <xref:System.Text.RegularExpressions.Regex> class let you perform the following operations:</span></span>  
  
- <span data-ttu-id="b871d-118">呼叫 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> 方法，以判定規則運算式模式是否出現在輸入文字中。</span><span class="sxs-lookup"><span data-stu-id="b871d-118">Determine whether the regular expression pattern occurs in the input text by calling the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b871d-119">如需使用 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> 方法來驗證文字的範例，請參閱[如何：確認字串是否為有效的電子郵件格式](how-to-verify-that-strings-are-in-valid-email-format.md)。</span><span class="sxs-lookup"><span data-stu-id="b871d-119">For an example that uses the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method for validating text, see [How to: Verify that Strings Are in Valid Email Format](how-to-verify-that-strings-are-in-valid-email-format.md).</span></span>  
  
- <span data-ttu-id="b871d-120">呼叫 <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> 或 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> 方法，以擷取符合規則運算式模式的所有文字。</span><span class="sxs-lookup"><span data-stu-id="b871d-120">Retrieve one or all occurrences of text that matches the regular expression pattern by calling the <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> or <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b871d-121">前一個方法會傳回 <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> 物件，提供相符文字的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b871d-121">The former method returns a <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> object that provides information about the matching text.</span></span> <span data-ttu-id="b871d-122">後一個方法會傳回 <xref:System.Text.RegularExpressions.MatchCollection> 物件，其中針對在所剖析文字中找到的每個相符項目，各包含一個 <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> 物件。</span><span class="sxs-lookup"><span data-stu-id="b871d-122">The latter returns a <xref:System.Text.RegularExpressions.MatchCollection> object that contains one <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> object for each match found in the parsed text.</span></span>  
  
- <span data-ttu-id="b871d-123">呼叫 <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> 方法，以取代符合規則運算式模式的文字。</span><span class="sxs-lookup"><span data-stu-id="b871d-123">Replace text that matches the regular expression pattern by calling the <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b871d-124">如需使用 <xref:System.Text.RegularExpressions.Regex.Replace%2A> 方法來變更日期格式，以及移除字串中無效字元的範例，請參閱[如何：從字串中刪除無效的字元](how-to-strip-invalid-characters-from-a-string.md)和[如何：變更日期格式](regular-expression-example-changing-date-formats.md)。</span><span class="sxs-lookup"><span data-stu-id="b871d-124">For examples that use the <xref:System.Text.RegularExpressions.Regex.Replace%2A> method to change date formats and remove invalid characters from a string, see [How to: Strip Invalid Characters from a String](how-to-strip-invalid-characters-from-a-string.md) and [Example: Changing Date Formats](regular-expression-example-changing-date-formats.md).</span></span>  
  
<span data-ttu-id="b871d-125">如需規則運算式物件模型概觀，請參閱[規則運算式物件模型](the-regular-expression-object-model.md)。</span><span class="sxs-lookup"><span data-stu-id="b871d-125">For an overview of the regular expression object model, see [The Regular Expression Object Model](the-regular-expression-object-model.md).</span></span>  
  
<span data-ttu-id="b871d-126">如需規則運算式語言的詳細資訊，請參閱[規則運算式語言 - 快速參考](regular-expression-language-quick-reference.md)，或下載並列印下列其中一本小手冊：</span><span class="sxs-lookup"><span data-stu-id="b871d-126">For more information about the regular expression language, see [Regular Expression Language - Quick Reference](regular-expression-language-quick-reference.md) or download and print one of these brochures:</span></span>  
  
- [<span data-ttu-id="b871d-127">Word (.docx) 格式的快速參考</span><span class="sxs-lookup"><span data-stu-id="b871d-127">Quick Reference in Word (.docx) format</span></span>](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
- [<span data-ttu-id="b871d-128">PDF (.pdf) 格式的快速參考</span><span class="sxs-lookup"><span data-stu-id="b871d-128">Quick Reference in PDF (.pdf) format</span></span>](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)  
  
## <a name="regular-expression-examples"></a><span data-ttu-id="b871d-129">規則運算式範例</span><span class="sxs-lookup"><span data-stu-id="b871d-129">Regular expression examples</span></span>

<span data-ttu-id="b871d-130"><xref:System.String> 類別包含數種字串搜尋和取代方法，可供您在大型字串中尋找常值字串時使用。</span><span class="sxs-lookup"><span data-stu-id="b871d-130">The <xref:System.String> class includes a number of string search and replacement methods that you can use when you want to locate literal strings in a larger string.</span></span> <span data-ttu-id="b871d-131">當您想要在大型字串中尋找數個子字串時，或是當您想要識別字串中的模式時，規則運算式最為好用，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b871d-131">Regular expressions are most useful either when you want to locate one of several substrings in a larger string, or when you want to identify patterns in a string, as the following examples illustrate.</span></span>

> [!TIP]
> <span data-ttu-id="b871d-132"><xref:System.Web.RegularExpressions> 命名空間包含一些規則運算式物件，這些物件會實作預先定義的規則運算式模式，以用於剖析來自 HTML、XML 和 ASP.NET 文件的字串。</span><span class="sxs-lookup"><span data-stu-id="b871d-132">The <xref:System.Web.RegularExpressions> namespace contains a number of regular expression objects that implement predefined regular expression patterns for parsing strings from HTML, XML, and ASP.NET documents.</span></span> <span data-ttu-id="b871d-133">例如，<xref:System.Web.RegularExpressions.TagRegex> 類別會識別字串中的開始標記，而 <xref:System.Web.RegularExpressions.CommentRegex> 類別會識別字串中的 ASP.NET 註解。</span><span class="sxs-lookup"><span data-stu-id="b871d-133">For example, the <xref:System.Web.RegularExpressions.TagRegex> class identifies start tags in a string and the <xref:System.Web.RegularExpressions.CommentRegex> class identifies ASP.NET comments in a string.</span></span>

### <a name="example-1-replace-substrings"></a><span data-ttu-id="b871d-134">範例 1:取代子字串</span><span class="sxs-lookup"><span data-stu-id="b871d-134">Example 1: Replace substrings</span></span>  

 <span data-ttu-id="b871d-135">假設郵寄清單包含的名稱有時候會包括稱謂 (Mr.、Mrs.、Miss 或 Ms.) 以及姓名。</span><span class="sxs-lookup"><span data-stu-id="b871d-135">Assume that a mailing list contains names that sometimes include a title (Mr., Mrs., Miss, or Ms.) along with a first and last name.</span></span> <span data-ttu-id="b871d-136">當您從清單產生信封標籤時，如果不想包括稱謂，就可以使用規則運算式來移除稱謂，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b871d-136">If you do not want to include the titles when you generate envelope labels from the list, you can use a regular expression to remove the titles, as the following example illustrates.</span></span>  
  
 [!code-csharp[Conceptual.Regex#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example1.cs#2)]
 [!code-vb[Conceptual.Regex#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example1.vb#2)]  
  
 <span data-ttu-id="b871d-137">規則運算式模式 `(Mr\.? |Mrs\.? |Miss |Ms\.? )` 會比對所出現的任何 "Mr "、"Mr. "、"Mrs "、"Mrs. "、"Miss "、"Ms 或 "Ms. "。</span><span class="sxs-lookup"><span data-stu-id="b871d-137">The regular expression pattern `(Mr\.? |Mrs\.? |Miss |Ms\.? )` matches any occurrence of "Mr ", "Mr. ", "Mrs ", "Mrs. ", "Miss ", "Ms or "Ms. ".</span></span> <span data-ttu-id="b871d-138">呼叫 <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> 方法會將相符的字串取代為 <xref:System.String.Empty?displayProperty=nameWithType>；換句話說，就是將其從原始字串中移除。</span><span class="sxs-lookup"><span data-stu-id="b871d-138">The call to the <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method replaces the matched string with <xref:System.String.Empty?displayProperty=nameWithType>; in other words, it removes it from the original string.</span></span>  
  
### <a name="example-2-identify-duplicated-words"></a><span data-ttu-id="b871d-139">範例 2:識別重複的單字</span><span class="sxs-lookup"><span data-stu-id="b871d-139">Example 2: Identify duplicated words</span></span>  

 <span data-ttu-id="b871d-140">不小心重複文字是作者常犯的錯誤。</span><span class="sxs-lookup"><span data-stu-id="b871d-140">Accidentally duplicating words is a common error that writers make.</span></span> <span data-ttu-id="b871d-141">規則運算式可用來識別重複的文字，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b871d-141">A regular expression can be used to identify duplicated words, as the following example shows.</span></span>  
  
 [!code-csharp[Conceptual.Regex#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example2.cs#3)]
 [!code-vb[Conceptual.Regex#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example2.vb#3)]  
  
 <span data-ttu-id="b871d-142">規則運算式模式 `\b(\w+?)\s\1\b` 可解譯如下：</span><span class="sxs-lookup"><span data-stu-id="b871d-142">The regular expression pattern `\b(\w+?)\s\1\b` can be interpreted as follows:</span></span>  
  
> [!div class="mx-tdCol2BreakAll"]
> |<span data-ttu-id="b871d-143">模式</span><span class="sxs-lookup"><span data-stu-id="b871d-143">Pattern</span></span>|<span data-ttu-id="b871d-144">解譯</span><span class="sxs-lookup"><span data-stu-id="b871d-144">Interpretation</span></span>|  
> |-|-|
> |`\b`|<span data-ttu-id="b871d-145">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="b871d-145">Start at a word boundary.</span></span>|  
> |`(\w+?)`|<span data-ttu-id="b871d-146">比對一或多個字元，但字元數愈少愈好。</span><span class="sxs-lookup"><span data-stu-id="b871d-146">Match one or more word characters, but as few characters as possible.</span></span> <span data-ttu-id="b871d-147">這些一起構成可稱之為 `\1` 的群組。</span><span class="sxs-lookup"><span data-stu-id="b871d-147">Together, they form a group that can be referred to as `\1`.</span></span>|  
> |`\s`|<span data-ttu-id="b871d-148">比對空白字元。</span><span class="sxs-lookup"><span data-stu-id="b871d-148">Match a white-space character.</span></span>|  
> |`\1`|<span data-ttu-id="b871d-149">比對等同於名為 `\1` 之群組的子字串。</span><span class="sxs-lookup"><span data-stu-id="b871d-149">Match the substring that is equal to the group named `\1`.</span></span>|  
> |`\b`|<span data-ttu-id="b871d-150">比對字邊界。</span><span class="sxs-lookup"><span data-stu-id="b871d-150">Match a word boundary.</span></span>|  
  
 <span data-ttu-id="b871d-151">呼叫 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> 方法時，規則運算式選項設為 <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="b871d-151">The <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> method is called with regular expression options set to <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b871d-152">因此，比對作業不區分大小寫，而且此範例會將子字串 "This this" 視為重複。</span><span class="sxs-lookup"><span data-stu-id="b871d-152">Therefore, the match operation is case-insensitive, and the example identifies the substring "This this" as a duplication.</span></span>  
  
 <span data-ttu-id="b871d-153">請注意，輸入字串包括子字串 "this?</span><span class="sxs-lookup"><span data-stu-id="b871d-153">Note that the input string includes the substring "this?</span></span> <span data-ttu-id="b871d-154">This"。</span><span class="sxs-lookup"><span data-stu-id="b871d-154">This".</span></span> <span data-ttu-id="b871d-155">不過，因為中間有標點符號，所以不會將其視為重複。</span><span class="sxs-lookup"><span data-stu-id="b871d-155">However, because of the intervening punctuation mark, it is not identified as a duplication.</span></span>  
  
### <a name="example-3-dynamically-build-a-culture-sensitive-regular-expression"></a><span data-ttu-id="b871d-156">範例 3:動態建構區分區域性的正規表示式</span><span class="sxs-lookup"><span data-stu-id="b871d-156">Example 3: Dynamically build a culture-sensitive regular expression</span></span>  

 <span data-ttu-id="b871d-157">下列範例說明規則運算式結合 .NET 全球化功能所提供的彈性，功能有多麼強大。</span><span class="sxs-lookup"><span data-stu-id="b871d-157">The following example illustrates the power of regular expressions combined with the flexibility offered by .NET's globalization features.</span></span> <span data-ttu-id="b871d-158">它會使用 <xref:System.Globalization.NumberFormatInfo> 物件來判定系統目前文化特性中的幣值格式，</span><span class="sxs-lookup"><span data-stu-id="b871d-158">It uses the <xref:System.Globalization.NumberFormatInfo> object to determine the format of currency values in the system's current culture.</span></span> <span data-ttu-id="b871d-159">然後利用該資訊動態建構可從文字擷取幣值的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="b871d-159">It then uses that information to dynamically construct a regular expression that extracts currency values from the text.</span></span> <span data-ttu-id="b871d-160">針對每個比對，它會擷取僅包含數值字串的子群組，將其轉換成 <xref:System.Decimal> 值，並計算執行總計。</span><span class="sxs-lookup"><span data-stu-id="b871d-160">For each match, it extracts the subgroup that contains the numeric string only, converts it to a <xref:System.Decimal> value, and calculates a running total.</span></span>  
  
 [!code-csharp[Conceptual.Regex#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example.cs#1)]
 [!code-vb[Conceptual.Regex#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example.vb#1)]  
  
 <span data-ttu-id="b871d-161">在目前文化特性為 English - United States (en-US) 的電腦上，此範例會動態建立規則運算式 `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`。</span><span class="sxs-lookup"><span data-stu-id="b871d-161">On a computer whose current culture is English - United States (en-US), the example dynamically builds the regular expression `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`.</span></span> <span data-ttu-id="b871d-162">此規則運算式模式可解譯如下：</span><span class="sxs-lookup"><span data-stu-id="b871d-162">This regular expression pattern can be interpreted as follows:</span></span>  

> [!div class="mx-tdCol2BreakAll"]
> |<span data-ttu-id="b871d-163">模式</span><span class="sxs-lookup"><span data-stu-id="b871d-163">Pattern</span></span>|<span data-ttu-id="b871d-164">解譯</span><span class="sxs-lookup"><span data-stu-id="b871d-164">Interpretation</span></span>|  
> |-|-|  
> |`\$`|<span data-ttu-id="b871d-165">在輸入字串中尋找單獨出現的貨幣符號 (`$`)。</span><span class="sxs-lookup"><span data-stu-id="b871d-165">Look for a single occurrence of the dollar symbol (`$`) in the input string.</span></span> <span data-ttu-id="b871d-166">規則運算式模式字串包含反斜線，表示貨幣符號要解譯為字面意義，而不是規則運算式錨點。</span><span class="sxs-lookup"><span data-stu-id="b871d-166">The regular expression pattern string includes a backslash to indicate that the dollar symbol is to be interpreted literally rather than as a regular expression anchor.</span></span> <span data-ttu-id="b871d-167">(僅`$`符號就表示正則表達式引擎應嘗試在字串末尾開始其匹配。為了確保當前區域性的貨幣符號不會被誤解為正則表達式符號,該示例調用<xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=nameWithType>方法以轉義字元。</span><span class="sxs-lookup"><span data-stu-id="b871d-167">(The `$` symbol alone would indicate that the regular expression engine should try to begin its match at the end of a string.) To ensure that the current culture's currency symbol is not misinterpreted as a regular expression symbol, the example calls the <xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=nameWithType> method to escape the character.</span></span>|  
> |`\s*`|<span data-ttu-id="b871d-168">尋找出現零或多次的空格字元。</span><span class="sxs-lookup"><span data-stu-id="b871d-168">Look for zero or more occurrences of a white-space character.</span></span>|  
> |`[-+]?`|<span data-ttu-id="b871d-169">尋找出現一或多次的正號或負號。</span><span class="sxs-lookup"><span data-stu-id="b871d-169">Look for zero or one occurrence of either a positive sign or a negative sign.</span></span>|  
> |`([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`|<span data-ttu-id="b871d-170">此運算式外面括號將其定義成擷取群組或子運算式。</span><span class="sxs-lookup"><span data-stu-id="b871d-170">The outer parentheses around this expression define it as a capturing group or a subexpression.</span></span> <span data-ttu-id="b871d-171">如果找到相符項目，從 <xref:System.Text.RegularExpressions.Group> 屬性傳回之 <xref:System.Text.RegularExpressions.GroupCollection> 物件中的第二個 <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> 物件，擷取此部分比對字串的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b871d-171">If a match is found, information about this part of the matching string can be retrieved from the second <xref:System.Text.RegularExpressions.Group> object in the <xref:System.Text.RegularExpressions.GroupCollection> object returned by the <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="b871d-172">(集合中的第一個項目代表整個比對。)</span><span class="sxs-lookup"><span data-stu-id="b871d-172">(The first element in the collection represents the entire match.)</span></span>|  
> |`[0-9]{0,3}`|<span data-ttu-id="b871d-173">尋找出現零到三次的十進位數字 0 到 9。</span><span class="sxs-lookup"><span data-stu-id="b871d-173">Look for zero to three occurrences of the decimal digits 0 through 9.</span></span>|  
> |`(,[0-9]{3})*`|<span data-ttu-id="b871d-174">尋找出現零或多次、後面接三個十進位數字的群組分隔符號。</span><span class="sxs-lookup"><span data-stu-id="b871d-174">Look for zero or more occurrences of a group separator followed by three decimal digits.</span></span>|  
> |`\.`|<span data-ttu-id="b871d-175">尋找單次出現的十進位分隔符號。</span><span class="sxs-lookup"><span data-stu-id="b871d-175">Look for a single occurrence of the decimal separator.</span></span>|  
> |`[0-9]+`|<span data-ttu-id="b871d-176">尋找一或多個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="b871d-176">Look for one or more decimal digits.</span></span>|  
> |`(\.[0-9]+)?`|<span data-ttu-id="b871d-177">尋找出現零或一次、後接至少一個十進位數字的十進位分隔符號。</span><span class="sxs-lookup"><span data-stu-id="b871d-177">Look for zero or one occurrence of the decimal separator followed by at least one decimal digit.</span></span>|  
  
 <span data-ttu-id="b871d-178">如果在輸入字串中找到上述每個子模式，則比對成功，並且會將包含此比對相關資訊的 <xref:System.Text.RegularExpressions.Match> 物件加入至 <xref:System.Text.RegularExpressions.MatchCollection> 物件。</span><span class="sxs-lookup"><span data-stu-id="b871d-178">If each of these subpatterns is found in the input string, the match succeeds, and a <xref:System.Text.RegularExpressions.Match> object that contains information about the match is added to the <xref:System.Text.RegularExpressions.MatchCollection> object.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="b871d-179">相關主題</span><span class="sxs-lookup"><span data-stu-id="b871d-179">Related topics</span></span>  
  
|<span data-ttu-id="b871d-180">Title</span><span class="sxs-lookup"><span data-stu-id="b871d-180">Title</span></span>|<span data-ttu-id="b871d-181">描述</span><span class="sxs-lookup"><span data-stu-id="b871d-181">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="b871d-182">規則運算式語言 - 快速參考</span><span class="sxs-lookup"><span data-stu-id="b871d-182">Regular Expression Language - Quick Reference</span></span>](regular-expression-language-quick-reference.md)|<span data-ttu-id="b871d-183">提供您可以用來定義規則運算式之字元、運算子和建構組合的資訊。</span><span class="sxs-lookup"><span data-stu-id="b871d-183">Provides information on the set of characters, operators, and constructs that you can use to define regular expressions.</span></span>|  
|[<span data-ttu-id="b871d-184">規則運算式物件模型</span><span class="sxs-lookup"><span data-stu-id="b871d-184">The Regular Expression Object Model</span></span>](the-regular-expression-object-model.md)|<span data-ttu-id="b871d-185">提供資訊和程式碼範例，說明如何使用規則運算式類別。</span><span class="sxs-lookup"><span data-stu-id="b871d-185">Provides information and code examples that illustrate how to use the regular expression classes.</span></span>|  
|[<span data-ttu-id="b871d-186">規則運算式行為的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="b871d-186">Details of Regular Expression Behavior</span></span>](details-of-regular-expression-behavior.md)|<span data-ttu-id="b871d-187">提供 .NET 規則運算式之功能和行為的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b871d-187">Provides information about the capabilities and behavior of .NET regular expressions.</span></span>|
|[<span data-ttu-id="b871d-188">在可視化工作室中使用正則運算式</span><span class="sxs-lookup"><span data-stu-id="b871d-188">Use regular expressions in Visual Studio</span></span>](/visualstudio/ide/using-regular-expressions-in-visual-studio)||
  
## <a name="reference"></a><span data-ttu-id="b871d-189">參考</span><span class="sxs-lookup"><span data-stu-id="b871d-189">Reference</span></span>  

- <xref:System.Text.RegularExpressions?displayProperty=nameWithType>  
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>  
- [<span data-ttu-id="b871d-190">規則運算式 - 快速參考 (以 Word 格式下載)</span><span class="sxs-lookup"><span data-stu-id="b871d-190">Regular Expressions - Quick Reference (download in Word format)</span></span>](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
- [<span data-ttu-id="b871d-191">規則運算式 - 快速參考 (以 PDF 格式下載)</span><span class="sxs-lookup"><span data-stu-id="b871d-191">Regular Expressions - Quick Reference (download in PDF format)</span></span>](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
