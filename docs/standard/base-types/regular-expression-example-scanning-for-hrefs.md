---
title: 規則運算式範例：掃描 HREF
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: fae2c15b-7adf-4b15-b118-58eb3906994f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b270559e9e73e18bebb29e36b815268d5426a940
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728676"
---
# <a name="regular-expression-example-scanning-for-hrefs"></a><span data-ttu-id="ae94a-102">規則運算式範例：掃描 HREF</span><span class="sxs-lookup"><span data-stu-id="ae94a-102">Regular Expression Example: Scanning for HREFs</span></span>
<span data-ttu-id="ae94a-103">下列範例將搜尋輸入字串，並顯示所有 href="..." 值和它們在字串中的位置。</span><span class="sxs-lookup"><span data-stu-id="ae94a-103">The following example searches an input string and displays all the href="…" values and their locations in the string.</span></span>  
  
## <a name="the-regex-object"></a><span data-ttu-id="ae94a-104">Regex 物件</span><span class="sxs-lookup"><span data-stu-id="ae94a-104">The Regex Object</span></span>  
 <span data-ttu-id="ae94a-105">由於可從使用者程式碼多次呼叫 `DumpHRefs` 方法，因此它會使用 `static` (在 Visual Basic 中為 `Shared`) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="ae94a-105">Because the `DumpHRefs` method can be called multiple times from user code, it uses the `static` (`Shared` in Visual Basic) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ae94a-106">這可讓規則運算式引擎快取規則運算式，並避免在每次呼叫方法時因將新 <xref:System.Text.RegularExpressions.Regex> 物件具現化而導致的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="ae94a-106">This enables the regular expression engine to cache the regular expression and avoids the overhead of instantiating a new <xref:System.Text.RegularExpressions.Regex> object each time the method is called.</span></span> <span data-ttu-id="ae94a-107">接著會使用 <xref:System.Text.RegularExpressions.Match> 物件逐一查看字串中的所有相符項目。</span><span class="sxs-lookup"><span data-stu-id="ae94a-107">A <xref:System.Text.RegularExpressions.Match> object is then used to iterate through all matches in the string.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 <span data-ttu-id="ae94a-108">下列範例說明如何呼叫 `DumpHRefs` 方法。</span><span class="sxs-lookup"><span data-stu-id="ae94a-108">The following example then illustrates a call to the `DumpHRefs` method.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 <span data-ttu-id="ae94a-109">規則運算式模式 `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` 的解譯方式如下表所示。</span><span class="sxs-lookup"><span data-stu-id="ae94a-109">The regular expression pattern `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="ae94a-110">模式</span><span class="sxs-lookup"><span data-stu-id="ae94a-110">Pattern</span></span>|<span data-ttu-id="ae94a-111">描述</span><span class="sxs-lookup"><span data-stu-id="ae94a-111">Description</span></span>|  
|-------------|-----------------|  
|`href`|<span data-ttu-id="ae94a-112">比對常值字串 "href"。</span><span class="sxs-lookup"><span data-stu-id="ae94a-112">Match the literal string "href".</span></span> <span data-ttu-id="ae94a-113">該比對不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="ae94a-113">The match is case-insensitive.</span></span>|  
|`\s*`|<span data-ttu-id="ae94a-114">比對零個以上的空白字元。</span><span class="sxs-lookup"><span data-stu-id="ae94a-114">Match zero or more white-space characters.</span></span>|  
|`=`|<span data-ttu-id="ae94a-115">比對等號。</span><span class="sxs-lookup"><span data-stu-id="ae94a-115">Match the equals sign.</span></span>|  
|`\s*`|<span data-ttu-id="ae94a-116">比對零個以上的空白字元。</span><span class="sxs-lookup"><span data-stu-id="ae94a-116">Match zero or more white-space characters.</span></span>|  
|<code>(?:\["'\](?<1>\[^"'\]*)["']&#124;(?<1>\S+))</code>|<span data-ttu-id="ae94a-117">比對下列其中一項，而不將結果指派給擷取的群組：</span><span class="sxs-lookup"><span data-stu-id="ae94a-117">Match one of the following without assigning the result to a captured group:</span></span><br /> <ul><li><p><span data-ttu-id="ae94a-118">引號 (或單引號)，後面加上零個或多個引號 (或單引號) 以外的任何字元，再加上引號 (或單引號)。</span><span class="sxs-lookup"><span data-stu-id="ae94a-118">A quotation mark or apostrophe, followed by zero or more occurrences of any character other than a quotation mark or apostrophe, followed by a quotation mark or apostrophe.</span></span> <span data-ttu-id="ae94a-119">此模式中包含名為 `1` 的群組。</span><span class="sxs-lookup"><span data-stu-id="ae94a-119">The group named `1` is included in this pattern.</span></span></p></li><li><p><span data-ttu-id="ae94a-120">一個或多個非空白字元。</span><span class="sxs-lookup"><span data-stu-id="ae94a-120">One or more non-white-space characters.</span></span> <span data-ttu-id="ae94a-121">此模式中包含名為 `1` 的群組。</span><span class="sxs-lookup"><span data-stu-id="ae94a-121">The group named `1` is included in this pattern.</span></span></p></li></ul>|  
|`(?<1>[^"']*)`|<span data-ttu-id="ae94a-122">將零個或多個引號 (或單引號) 以外的任何字元指派給名為 `1` 的擷取端群組。</span><span class="sxs-lookup"><span data-stu-id="ae94a-122">Assign zero or more occurrences of any character other than a quotation mark or apostrophe to the capturing group named `1`.</span></span>|  
|`(?<1>\S+)`|<span data-ttu-id="ae94a-123">將一或多個非空白字元指派給名為 `1` 的擷取群組。</span><span class="sxs-lookup"><span data-stu-id="ae94a-123">Assign one or more non-white-space characters to the capturing group named `1`.</span></span>|  
  
## <a name="match-result-class"></a><span data-ttu-id="ae94a-124">比對結果類別</span><span class="sxs-lookup"><span data-stu-id="ae94a-124">Match Result Class</span></span>  
 <span data-ttu-id="ae94a-125">搜尋的結果會儲存在 <xref:System.Text.RegularExpressions.Match> 類別中，可讓您存取搜尋擷取的所有子字串。</span><span class="sxs-lookup"><span data-stu-id="ae94a-125">The results of a search are stored in the <xref:System.Text.RegularExpressions.Match> class, which provides access to all the substrings extracted by the search.</span></span> <span data-ttu-id="ae94a-126">它也會記住要搜尋的字串與所用的規則運算式，使其能呼叫 <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> 方法，從最後一個搜尋結束的位置開始執行其他搜尋。</span><span class="sxs-lookup"><span data-stu-id="ae94a-126">It also remembers the string being searched and the regular expression being used, so it can call the <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> method to perform another search starting where the last one ended.</span></span>  
  
## <a name="explicitly-named-captures"></a><span data-ttu-id="ae94a-127">明確命名的擷取</span><span class="sxs-lookup"><span data-stu-id="ae94a-127">Explicitly Named Captures</span></span>  
 <span data-ttu-id="ae94a-128">在傳統的規則運算式中，會自動將擷取括號依序編號。</span><span class="sxs-lookup"><span data-stu-id="ae94a-128">In traditional regular expressions, capturing parentheses are automatically numbered sequentially.</span></span> <span data-ttu-id="ae94a-129">這會導致兩個問題。</span><span class="sxs-lookup"><span data-stu-id="ae94a-129">This leads to two problems.</span></span> <span data-ttu-id="ae94a-130">第一，如果修改規則運算式時，是以插入或移除一組括號來進行，就必須重新撰寫所有參考已編號擷取的程式碼，以反映新的編號。</span><span class="sxs-lookup"><span data-stu-id="ae94a-130">First, if a regular expression is modified by inserting or removing a set of parentheses, all code that refers to the numbered captures must be rewritten to reflect the new numbering.</span></span> <span data-ttu-id="ae94a-131">第二，不同的括號通常用來提供兩個替代運算式以進行可接受的比對，因此可能難以判斷這兩個運算式是哪一個實際傳回結果。</span><span class="sxs-lookup"><span data-stu-id="ae94a-131">Second, because different sets of parentheses often are used to provide two alternative expressions for an acceptable match, it might be difficult to determine which of the two expressions actually returned a result.</span></span>  
  
 <span data-ttu-id="ae94a-132">為了解決這些問題，<xref:System.Text.RegularExpressions.Regex> 類別支援 `(?<name>…)` 的語法，可將相符項目擷取至指定的位置 (該位置可以使用字串或整數命名；重新叫用整數的速度更快)。</span><span class="sxs-lookup"><span data-stu-id="ae94a-132">To address these problems, the <xref:System.Text.RegularExpressions.Regex> class supports the syntax `(?<name>…)` for capturing a match into a specified slot (the slot can be named using a string or an integer; integers can be recalled more quickly).</span></span> <span data-ttu-id="ae94a-133">因此，相同字串的所有替代比對皆可導向相同的位置。</span><span class="sxs-lookup"><span data-stu-id="ae94a-133">Thus, alternative matches for the same string all can be directed to the same place.</span></span> <span data-ttu-id="ae94a-134">萬一發生衝突時，最後一個進入位置的比對就是成功的比對</span><span class="sxs-lookup"><span data-stu-id="ae94a-134">In case of a conflict, the last match dropped into a slot is the successful match.</span></span> <span data-ttu-id="ae94a-135">(不過，您可以使用單一位置之多個比對的完整清單。</span><span class="sxs-lookup"><span data-stu-id="ae94a-135">(However, a complete list of multiple matches for a single slot is available.</span></span> <span data-ttu-id="ae94a-136">如需詳細資訊，請參閱 <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> 集合。)</span><span class="sxs-lookup"><span data-stu-id="ae94a-136">See the <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> collection for details.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae94a-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="ae94a-137">See Also</span></span>  
 [<span data-ttu-id="ae94a-138">.NET 規則運算式</span><span class="sxs-lookup"><span data-stu-id="ae94a-138">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
