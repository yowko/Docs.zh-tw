---
title: .NET 規則運算式中的替代建構
description: 了解如何在規則運算式中使用條件式比對的替代建構。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- either/or matching
- alternative matching patterns
- regular expressions, alternation constructs
- alternation constructs
- optional matching patterns
- constructs, alternation
- .NET Framework regular expressions, alternation constructs
ms.assetid: 071e22e9-fbb0-4ecf-add1-8d2424f9f2d1
ms.openlocfilehash: 02664bd2812f89649ec933483161263bae530a75
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159685"
---
# <a name="alternation-constructs-in-regular-expressions"></a><span data-ttu-id="73eaa-103">規則運算式中的替代建構</span><span class="sxs-lookup"><span data-stu-id="73eaa-103">Alternation Constructs in Regular Expressions</span></span>

<span data-ttu-id="73eaa-104">替代建構會修改規則運算式來啟用二選一或條件式比對。</span><span class="sxs-lookup"><span data-stu-id="73eaa-104">Alternation constructs modify a regular expression to enable either/or or conditional matching.</span></span> <span data-ttu-id="73eaa-105">.NET 支援下列三種替代建構：</span><span class="sxs-lookup"><span data-stu-id="73eaa-105">.NET supports three alternation constructs:</span></span>

- [<span data-ttu-id="73eaa-106">以 &#124; 進行的模式比對</span><span class="sxs-lookup"><span data-stu-id="73eaa-106">Pattern matching with &#124;</span></span>](#Either_Or)
- [<span data-ttu-id="73eaa-107">以 (?(expression)yes&#124;no) 進行的條件式比對</span><span class="sxs-lookup"><span data-stu-id="73eaa-107">Conditional matching with (?(expression)yes&#124;no)</span></span>](#Conditional_Expr)
- [<span data-ttu-id="73eaa-108">基於有效捕獲的組的條件匹配</span><span class="sxs-lookup"><span data-stu-id="73eaa-108">Conditional matching based on a valid captured group</span></span>](#Conditional_Group)

<a name="Either_Or"></a>
## <a name="pattern-matching-with-124"></a><span data-ttu-id="73eaa-109">以 &#124; 進行的模式比對</span><span class="sxs-lookup"><span data-stu-id="73eaa-109">Pattern Matching with &#124;</span></span>

<span data-ttu-id="73eaa-110">您可以使用分隔號 (`|`) 字元來比對其中任一系列的模式，且 `|` 字元會分隔每一個模式。</span><span class="sxs-lookup"><span data-stu-id="73eaa-110">You can use the vertical bar (`|`) character to match any one of a series of patterns, where the `|` character separates each pattern.</span></span>

<span data-ttu-id="73eaa-111">`|` 字元和正字元類別一樣，可以用來比對一些單一字元當中的任一字元。</span><span class="sxs-lookup"><span data-stu-id="73eaa-111">Like the positive character class, the `|` character can be used to match any one of a number of single characters.</span></span> <span data-ttu-id="73eaa-112">下列範例同時使用正字元類別和透過 `|` 字元的二選一模式比對，在字串中尋找與單字 "gray" 或 "grey" 相符的項目。</span><span class="sxs-lookup"><span data-stu-id="73eaa-112">The following example uses both a positive character class and either/or pattern matching with the `|` character to locate occurrences of the words "gray" or "grey" in a string.</span></span> <span data-ttu-id="73eaa-113">在此案例中，`|` 字元會產生更詳細的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="73eaa-113">In this case, the `|` character produces a regular expression that is more verbose.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#1](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
[!code-vb[RegularExpressions.Language.Alternation#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]

<span data-ttu-id="73eaa-114">使用`|`字元`\bgr(a|e)y\b`的正則運算式被解釋為下表所示：</span><span class="sxs-lookup"><span data-stu-id="73eaa-114">The regular expression that uses the `|` character, `\bgr(a|e)y\b`, is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="73eaa-115">模式</span><span class="sxs-lookup"><span data-stu-id="73eaa-115">Pattern</span></span>|<span data-ttu-id="73eaa-116">描述</span><span class="sxs-lookup"><span data-stu-id="73eaa-116">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="73eaa-117">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="73eaa-117">Start at a word boundary.</span></span>|  
|`gr`|<span data-ttu-id="73eaa-118">比對字元 "gr"。</span><span class="sxs-lookup"><span data-stu-id="73eaa-118">Match the characters "gr".</span></span>|  
|<code>(a&#124;e)</code>|<span data-ttu-id="73eaa-119">比對 "a" 或 "e"。</span><span class="sxs-lookup"><span data-stu-id="73eaa-119">Match either an "a" or an "e".</span></span>|  
|`y\b`|<span data-ttu-id="73eaa-120">比對字邊界上的 "y"。</span><span class="sxs-lookup"><span data-stu-id="73eaa-120">Match a "y" on a word boundary.</span></span>|  

<span data-ttu-id="73eaa-121">`|` 字元也可以用來與多個字元或子運算式執行兩選一的比對，這些字元或運算式可以包含字元常值和規則運算式語言項目的任何組合。</span><span class="sxs-lookup"><span data-stu-id="73eaa-121">The `|` character can also be used to perform an either/or match with multiple characters or subexpressions, which can include any combination of character literals and regular expression language elements.</span></span> <span data-ttu-id="73eaa-122">（字元類不提供此功能。下面的示例使用`|`該字元提取美國社會保險號 （SSN），該號碼是格式為*ddd*-*dd*-ddd 的 9 位*數位，或者*使用美國雇主標識號 （EIN），該號碼是格式*為*-*ddddd*的 9 位數位。</span><span class="sxs-lookup"><span data-stu-id="73eaa-122">(The character class does not provide this functionality.) The following example uses the `|` character to extract either a U.S. Social Security Number (SSN), which is a 9-digit number with the format *ddd*-*dd*-*dddd*, or a U.S. Employer Identification Number (EIN), which is a 9-digit number with the format *dd*-*ddddddd*.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#2](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
[!code-vb[RegularExpressions.Language.Alternation#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  

<span data-ttu-id="73eaa-123">正則運算式`\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b`的解釋如下表所示：</span><span class="sxs-lookup"><span data-stu-id="73eaa-123">The regular expression `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>
  
|<span data-ttu-id="73eaa-124">模式</span><span class="sxs-lookup"><span data-stu-id="73eaa-124">Pattern</span></span>|<span data-ttu-id="73eaa-125">描述</span><span class="sxs-lookup"><span data-stu-id="73eaa-125">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="73eaa-126">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="73eaa-126">Start at a word boundary.</span></span>|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|<span data-ttu-id="73eaa-127">比對下列其中一項：兩個十進位數字後接連字號再後接七個十進位數字，或是三個十進位數字、連字號、兩個十進位數字、另一個連字號及四個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="73eaa-127">Match either of the following: two decimal digits followed by a hyphen followed by seven decimal digits; or three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\d`|<span data-ttu-id="73eaa-128">結束字緣比對。</span><span class="sxs-lookup"><span data-stu-id="73eaa-128">End the match at a word boundary.</span></span>|  
  
<a name="Conditional_Expr"></a>
## <a name="conditional-matching-with-an-expression"></a><span data-ttu-id="73eaa-129">使用運算式進行的條件式比對</span><span class="sxs-lookup"><span data-stu-id="73eaa-129">Conditional matching with an expression</span></span>

<span data-ttu-id="73eaa-130">這個語言項目會嘗試比對兩個模式的其中一個是否符合初始模式。</span><span class="sxs-lookup"><span data-stu-id="73eaa-130">This language element attempts to match one of two patterns depending on whether it can match an initial pattern.</span></span> <span data-ttu-id="73eaa-131">其語法如下：</span><span class="sxs-lookup"><span data-stu-id="73eaa-131">Its syntax is:</span></span>  

<span data-ttu-id="73eaa-132">`(?(` *expression* `)` *yes* `|` *no* `)`</span><span class="sxs-lookup"><span data-stu-id="73eaa-132">`(?(` *expression* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="73eaa-133">*其中運算式*是要匹配的初始模式，如果*匹配運算式*，*則是*要匹配的模式，如果*運算式*不匹配，*則不*匹配可選模式。</span><span class="sxs-lookup"><span data-stu-id="73eaa-133">where *expression* is the initial pattern to match, *yes* is the pattern to match if *expression* is matched, and *no* is the optional pattern to match if *expression* is not matched.</span></span> <span data-ttu-id="73eaa-134">規則運算式引擎會將 *expression* 視為零寬度的判斷提示，也就是說，規則運算式引擎不會在評估 *expression* 之後於輸入資料流中前進。</span><span class="sxs-lookup"><span data-stu-id="73eaa-134">The regular expression engine treats *expression* as a zero-width assertion; that is, the regular expression engine does not advance in the input stream after it evaluates *expression*.</span></span> <span data-ttu-id="73eaa-135">因此，此建構等同於下列：</span><span class="sxs-lookup"><span data-stu-id="73eaa-135">Therefore, this construct is equivalent to the following:</span></span>

<span data-ttu-id="73eaa-136">`(?(?=` *expression* `)` *yes* `|` *no* `)`</span><span class="sxs-lookup"><span data-stu-id="73eaa-136">`(?(?=` *expression* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="73eaa-137">`(?=`*其中運算式*`)`是零寬度斷言構造。</span><span class="sxs-lookup"><span data-stu-id="73eaa-137">where `(?=`*expression*`)` is a zero-width assertion construct.</span></span> <span data-ttu-id="73eaa-138">（有關詳細資訊，請參閱[分組構造](grouping-constructs-in-regular-expressions.md)。由於正則運算式引擎將*運算式*解釋為錨點（零寬度斷言），*因此運算式*必須是零寬度斷言（有關詳細資訊，請參閱[錨點](anchors-in-regular-expressions.md)）或包含在*yes*中的子運算式。</span><span class="sxs-lookup"><span data-stu-id="73eaa-138">(For more information, see [Grouping Constructs](grouping-constructs-in-regular-expressions.md).) Because the regular expression engine interprets *expression* as an anchor (a zero-width assertion), *expression* must either be a zero-width assertion (for more information, see [Anchors](anchors-in-regular-expressions.md)) or a subexpression that is also contained in *yes*.</span></span> <span data-ttu-id="73eaa-139">否則就無法比對 *yes* 模式。</span><span class="sxs-lookup"><span data-stu-id="73eaa-139">Otherwise, the *yes* pattern cannot be matched.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73eaa-140">如果*運算式*是命名或編號捕獲組，則交替構造將解釋為捕獲測試;如果運算式是命名或編號捕獲組，則表示交替構造將被解釋為捕獲測試。有關詳細資訊，請參閱下一節"[基於有效捕獲組的條件匹配](#Conditional_Group)"。</span><span class="sxs-lookup"><span data-stu-id="73eaa-140">If *expression* is a named or numbered capturing group, the alternation construct is interpreted as a capture test; for more information, see the next section, [Conditional Matching Based on a Valid Capture Group](#Conditional_Group).</span></span> <span data-ttu-id="73eaa-141">換句話說，規則運算式引擎不會嘗試比對擷取的子字串，而會測試群組是否存在。</span><span class="sxs-lookup"><span data-stu-id="73eaa-141">In other words, the regular expression engine does not attempt to match the captured substring, but instead tests for the presence or absence of the group.</span></span>  
  
<span data-ttu-id="73eaa-142">下列範例是[以 &#124; 進行的二選一模式比對](#Either_Or)一節中使用的範例變化。</span><span class="sxs-lookup"><span data-stu-id="73eaa-142">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="73eaa-143">它使用條件式比對，來判斷字邊界後的前三個字元是否為兩個位數後接連字號。</span><span class="sxs-lookup"><span data-stu-id="73eaa-143">It uses conditional matching to determine whether the first three characters after a word boundary are two digits followed by a hyphen.</span></span> <span data-ttu-id="73eaa-144">如果是，它會嘗試比對美國美國雇主識別碼 (EIN)。</span><span class="sxs-lookup"><span data-stu-id="73eaa-144">If they are, it attempts to match a U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="73eaa-145">如果不是，它會嘗試比對美國社會安全碼 (SSN)。</span><span class="sxs-lookup"><span data-stu-id="73eaa-145">If not, it attempts to match a U.S. Social Security Number (SSN).</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#3](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
[!code-vb[RegularExpressions.Language.Alternation#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]

<span data-ttu-id="73eaa-146">正則運算式模式`\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b`被解釋為下表所示：</span><span class="sxs-lookup"><span data-stu-id="73eaa-146">The regular expression pattern `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="73eaa-147">模式</span><span class="sxs-lookup"><span data-stu-id="73eaa-147">Pattern</span></span>|<span data-ttu-id="73eaa-148">描述</span><span class="sxs-lookup"><span data-stu-id="73eaa-148">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="73eaa-149">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="73eaa-149">Start at a word boundary.</span></span>|  
|`(?(\d{2}-)`|<span data-ttu-id="73eaa-150">判斷接下來三個字元是否為兩個數字後接連字號。</span><span class="sxs-lookup"><span data-stu-id="73eaa-150">Determine whether the next three characters consist of two digits followed by a hyphen.</span></span>|  
|`\d{2}-\d{7}`|<span data-ttu-id="73eaa-151">如果上一個模式符合，便會比對兩個數字，後接連字號，再後接七個數字。</span><span class="sxs-lookup"><span data-stu-id="73eaa-151">If the previous pattern matches, match two digits followed by a hyphen followed by seven digits.</span></span>|  
|`\d{3}-\d{2}-\d{4}`|<span data-ttu-id="73eaa-152">如果上一個模式不符合，便會比對三個十進位數字、連字號、兩個十進位數字、另一個連字號，以及四個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="73eaa-152">If the previous pattern does not match, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="73eaa-153">比對字邊界。</span><span class="sxs-lookup"><span data-stu-id="73eaa-153">Match a word boundary.</span></span>|  

<a name="Conditional_Group"></a>
## <a name="conditional-matching-based-on-a-valid-captured-group"></a><span data-ttu-id="73eaa-154">依據有效擷取群組進行的條件式比對</span><span class="sxs-lookup"><span data-stu-id="73eaa-154">Conditional matching based on a valid captured group</span></span>

<span data-ttu-id="73eaa-155">這個語言項目會嘗試根據它是否已經比對指定的擷取群組，比對兩種模式的其中一種。</span><span class="sxs-lookup"><span data-stu-id="73eaa-155">This language element attempts to match one of two patterns depending on whether it has matched a specified capturing group.</span></span> <span data-ttu-id="73eaa-156">其語法如下：</span><span class="sxs-lookup"><span data-stu-id="73eaa-156">Its syntax is:</span></span>

<span data-ttu-id="73eaa-157">`(?(` *name* `)` *yes* `|` *no* `)`</span><span class="sxs-lookup"><span data-stu-id="73eaa-157">`(?(` *name* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="73eaa-158">或</span><span class="sxs-lookup"><span data-stu-id="73eaa-158">or</span></span>

<span data-ttu-id="73eaa-159">`(?(` *數字* `)` *是* `|` *no* `)`</span><span class="sxs-lookup"><span data-stu-id="73eaa-159">`(?(` *number* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="73eaa-160">*其中名稱*是名稱，*數位*是捕獲組的數位，*是，如果\*\*名稱*或數位具有匹配項，則為匹配的運算式，如果名稱或*數位*不匹配，*則不*匹配可選運算式。</span><span class="sxs-lookup"><span data-stu-id="73eaa-160">where *name* is the name and *number* is the number of a capturing group, *yes* is the expression to match if *name* or *number* has a match, and *no* is the optional expression to match if it does not.</span></span>

<span data-ttu-id="73eaa-161">如果 *name* 並未對應到規則運算式模式中所使用的擷取群組名稱，則替代建構會解譯為運算式測試，如上一節中所說明。</span><span class="sxs-lookup"><span data-stu-id="73eaa-161">If *name* does not correspond to the name of a capturing group that is used in the regular expression pattern, the alternation construct is interpreted as an expression test, as explained in the previous section.</span></span> <span data-ttu-id="73eaa-162">通常，這意味著*運算式*計算到`false`。</span><span class="sxs-lookup"><span data-stu-id="73eaa-162">Typically, this means that *expression* evaluates to `false`.</span></span> <span data-ttu-id="73eaa-163">如果 *number* 沒有對應到規則運算式模式中所使用的編號擷取群組，則規則運算式引擎會擲回 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="73eaa-163">If *number* does not correspond to a numbered capturing group that is used in the regular expression pattern, the regular expression engine throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="73eaa-164">下列範例是[以 &#124; 進行的二選一模式比對](#Either_Or)一節中使用的範例變化。</span><span class="sxs-lookup"><span data-stu-id="73eaa-164">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="73eaa-165">它會使用名為 `n2` 的擷取群組，其由兩個數字後接連字號所組成。</span><span class="sxs-lookup"><span data-stu-id="73eaa-165">It uses a capturing group named `n2` that consists of two digits followed by a hyphen.</span></span> <span data-ttu-id="73eaa-166">替代建構會測試是否已在輸入字串中比對這個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="73eaa-166">The alternation construct tests whether this capturing group has been matched in the input string.</span></span> <span data-ttu-id="73eaa-167">如果是，交替建構會嘗試比對九位數雇主識別碼 (EIN) 的末七碼。美國雇主識別碼 (EIN)。</span><span class="sxs-lookup"><span data-stu-id="73eaa-167">If it has, the alternation construct attempts to match the last seven digits of a nine-digit U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="73eaa-168">如果不是，則會嘗試比對九位數美國社會安全碼 (SSN)。社會安全碼 (SSN)。</span><span class="sxs-lookup"><span data-stu-id="73eaa-168">If it has not, it attempts to match a nine-digit U.S. Social Security Number (SSN).</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#4](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
[!code-vb[RegularExpressions.Language.Alternation#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]

<span data-ttu-id="73eaa-169">正則運算式模式`\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b`被解釋為下表所示：</span><span class="sxs-lookup"><span data-stu-id="73eaa-169">The regular expression pattern `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="73eaa-170">模式</span><span class="sxs-lookup"><span data-stu-id="73eaa-170">Pattern</span></span>|<span data-ttu-id="73eaa-171">描述</span><span class="sxs-lookup"><span data-stu-id="73eaa-171">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="73eaa-172">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="73eaa-172">Start at a word boundary.</span></span>|  
|`(?<n2>\d{2}-)?`|<span data-ttu-id="73eaa-173">比對出現零次或一次且後接連字號的兩個數字。</span><span class="sxs-lookup"><span data-stu-id="73eaa-173">Match zero or one occurrence of two digits followed by a hyphen.</span></span> <span data-ttu-id="73eaa-174">將此擷取群組命名為 `n2`。</span><span class="sxs-lookup"><span data-stu-id="73eaa-174">Name this capturing group `n2`.</span></span>|  
|`(?(n2)`|<span data-ttu-id="73eaa-175">測試 `n2` 在輸入字串中是否相符。</span><span class="sxs-lookup"><span data-stu-id="73eaa-175">Test whether `n2` was matched in the input string.</span></span>|  
|`\d{7}`|<span data-ttu-id="73eaa-176">如果 `n2` 相符，則會比對七個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="73eaa-176">If `n2` was matched, match seven decimal digits.</span></span>|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|<span data-ttu-id="73eaa-177">如果 `n2` 不相符，則會比對三個十進位數字、一個連字號、兩個十進位數字、另一個連字號，以及四個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="73eaa-177">If `n2` was not matched, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="73eaa-178">比對字邊界。</span><span class="sxs-lookup"><span data-stu-id="73eaa-178">Match a word boundary.</span></span>|  

<span data-ttu-id="73eaa-179">此範例是使用編號的群組而不是具名群組的一種變化，如下所示。</span><span class="sxs-lookup"><span data-stu-id="73eaa-179">A variation of this example that uses a numbered group instead of a named group is shown in the following example.</span></span> <span data-ttu-id="73eaa-180">它的規則運算式模式是 `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`。</span><span class="sxs-lookup"><span data-stu-id="73eaa-180">Its regular expression pattern is `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#5](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
[!code-vb[RegularExpressions.Language.Alternation#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]

## <a name="see-also"></a><span data-ttu-id="73eaa-181">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73eaa-181">See also</span></span>

- [<span data-ttu-id="73eaa-182">正則運算式語言 - 快速參考</span><span class="sxs-lookup"><span data-stu-id="73eaa-182">Regular Expression Language - Quick Reference</span></span>](regular-expression-language-quick-reference.md)
