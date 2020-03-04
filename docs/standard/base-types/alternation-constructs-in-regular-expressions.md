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
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159685"
---
# <a name="alternation-constructs-in-regular-expressions"></a><span data-ttu-id="490ad-103">規則運算式中的替代建構</span><span class="sxs-lookup"><span data-stu-id="490ad-103">Alternation Constructs in Regular Expressions</span></span>

<span data-ttu-id="490ad-104">替代建構會修改規則運算式來啟用二選一或條件式比對。</span><span class="sxs-lookup"><span data-stu-id="490ad-104">Alternation constructs modify a regular expression to enable either/or or conditional matching.</span></span> <span data-ttu-id="490ad-105">.NET 支援下列三種替代建構：</span><span class="sxs-lookup"><span data-stu-id="490ad-105">.NET supports three alternation constructs:</span></span>

- [<span data-ttu-id="490ad-106">以 &#124; 進行的模式比對</span><span class="sxs-lookup"><span data-stu-id="490ad-106">Pattern matching with &#124;</span></span>](#Either_Or)
- [<span data-ttu-id="490ad-107">以 (?(expression)yes&#124;no) 進行的條件式比對</span><span class="sxs-lookup"><span data-stu-id="490ad-107">Conditional matching with (?(expression)yes&#124;no)</span></span>](#Conditional_Expr)
- [<span data-ttu-id="490ad-108">依據有效擷取群組進行的條件式比對</span><span class="sxs-lookup"><span data-stu-id="490ad-108">Conditional matching based on a valid captured group</span></span>](#Conditional_Group)

<a name="Either_Or"></a>
## <a name="pattern-matching-with-124"></a><span data-ttu-id="490ad-109">以 &#124; 進行的模式比對</span><span class="sxs-lookup"><span data-stu-id="490ad-109">Pattern Matching with &#124;</span></span>

<span data-ttu-id="490ad-110">您可以使用分隔號 (`|`) 字元來比對其中任一系列的模式，且 `|` 字元會分隔每一個模式。</span><span class="sxs-lookup"><span data-stu-id="490ad-110">You can use the vertical bar (`|`) character to match any one of a series of patterns, where the `|` character separates each pattern.</span></span>

<span data-ttu-id="490ad-111">`|` 字元和正字元類別一樣，可以用來比對一些單一字元當中的任一字元。</span><span class="sxs-lookup"><span data-stu-id="490ad-111">Like the positive character class, the `|` character can be used to match any one of a number of single characters.</span></span> <span data-ttu-id="490ad-112">下列範例同時使用正字元類別和透過 `|` 字元的二選一模式比對，在字串中尋找與單字 "gray" 或 "grey" 相符的項目。</span><span class="sxs-lookup"><span data-stu-id="490ad-112">The following example uses both a positive character class and either/or pattern matching with the `|` character to locate occurrences of the words "gray" or "grey" in a string.</span></span> <span data-ttu-id="490ad-113">在此案例中， `|` 字元會產生更詳細的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="490ad-113">In this case, the `|` character produces a regular expression that is more verbose.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#1](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
[!code-vb[RegularExpressions.Language.Alternation#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]

<span data-ttu-id="490ad-114">使用 `|` 字元 `\bgr(a|e)y\b`的正則運算式，如下表所示：</span><span class="sxs-lookup"><span data-stu-id="490ad-114">The regular expression that uses the `|` character, `\bgr(a|e)y\b`, is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="490ad-115">模式</span><span class="sxs-lookup"><span data-stu-id="490ad-115">Pattern</span></span>|<span data-ttu-id="490ad-116">描述</span><span class="sxs-lookup"><span data-stu-id="490ad-116">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="490ad-117">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="490ad-117">Start at a word boundary.</span></span>|  
|`gr`|<span data-ttu-id="490ad-118">比對字元 "gr"。</span><span class="sxs-lookup"><span data-stu-id="490ad-118">Match the characters "gr".</span></span>|  
|<code>(a&#124;e)</code>|<span data-ttu-id="490ad-119">比對 "a" 或 "e"。</span><span class="sxs-lookup"><span data-stu-id="490ad-119">Match either an "a" or an "e".</span></span>|  
|`y\b`|<span data-ttu-id="490ad-120">比對字邊界上的 "y"。</span><span class="sxs-lookup"><span data-stu-id="490ad-120">Match a "y" on a word boundary.</span></span>|  

<span data-ttu-id="490ad-121">`|` 字元也可以用來與多個字元或子運算式執行兩選一的比對，這些字元或運算式可以包含字元常值和規則運算式語言項目的任何組合。</span><span class="sxs-lookup"><span data-stu-id="490ad-121">The `|` character can also be used to perform an either/or match with multiple characters or subexpressions, which can include any combination of character literals and regular expression language elements.</span></span> <span data-ttu-id="490ad-122">（字元類別不提供這種功能）。下列範例會使用 `|` 字元來解壓縮美國社會安全號碼（SSN），這是具有*ddd*-*dd*-*dddd*格式的9位數數位，或美國雇主識別碼（EIN），其為*dd*-*ddddddd*格式的9位數數位。</span><span class="sxs-lookup"><span data-stu-id="490ad-122">(The character class does not provide this functionality.) The following example uses the `|` character to extract either a U.S. Social Security Number (SSN), which is a 9-digit number with the format *ddd*-*dd*-*dddd*, or a U.S. Employer Identification Number (EIN), which is a 9-digit number with the format *dd*-*ddddddd*.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#2](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
[!code-vb[RegularExpressions.Language.Alternation#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  

<span data-ttu-id="490ad-123">正則運算式 `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` 的解讀方式如下表所示：</span><span class="sxs-lookup"><span data-stu-id="490ad-123">The regular expression `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>
  
|<span data-ttu-id="490ad-124">模式</span><span class="sxs-lookup"><span data-stu-id="490ad-124">Pattern</span></span>|<span data-ttu-id="490ad-125">描述</span><span class="sxs-lookup"><span data-stu-id="490ad-125">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="490ad-126">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="490ad-126">Start at a word boundary.</span></span>|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|<span data-ttu-id="490ad-127">比對下列其中一項：兩個十進位數字後接連字號再後接七個十進位數字，或是三個十進位數字、連字號、兩個十進位數字、另一個連字號及四個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="490ad-127">Match either of the following: two decimal digits followed by a hyphen followed by seven decimal digits; or three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\d`|<span data-ttu-id="490ad-128">結束字緣比對。</span><span class="sxs-lookup"><span data-stu-id="490ad-128">End the match at a word boundary.</span></span>|  
  
<a name="Conditional_Expr"></a>
## <a name="conditional-matching-with-an-expression"></a><span data-ttu-id="490ad-129">使用運算式進行的條件式比對</span><span class="sxs-lookup"><span data-stu-id="490ad-129">Conditional matching with an expression</span></span>

<span data-ttu-id="490ad-130">這個語言項目會嘗試比對兩個模式的其中一個是否符合初始模式。</span><span class="sxs-lookup"><span data-stu-id="490ad-130">This language element attempts to match one of two patterns depending on whether it can match an initial pattern.</span></span> <span data-ttu-id="490ad-131">其語法如下：</span><span class="sxs-lookup"><span data-stu-id="490ad-131">Its syntax is:</span></span>  

<span data-ttu-id="490ad-132">`(?(`*運算式*`)`*是*`|`*否*`)`</span><span class="sxs-lookup"><span data-stu-id="490ad-132">`(?(` *expression* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="490ad-133">其中 *expression* 是要比對的初始模式， *yes* 是符合 *expression* 時要比對的模式，而 *no* 是不符合 *expression* 時要比對的選擇性模式。</span><span class="sxs-lookup"><span data-stu-id="490ad-133">where *expression* is the initial pattern to match, *yes* is the pattern to match if *expression* is matched, and *no* is the optional pattern to match if *expression* is not matched.</span></span> <span data-ttu-id="490ad-134">規則運算式引擎會將 *expression* 視為零寬度的判斷提示，也就是說，規則運算式引擎不會在評估 *expression* 之後於輸入資料流中前進。</span><span class="sxs-lookup"><span data-stu-id="490ad-134">The regular expression engine treats *expression* as a zero-width assertion; that is, the regular expression engine does not advance in the input stream after it evaluates *expression*.</span></span> <span data-ttu-id="490ad-135">因此，此建構等同於下列：</span><span class="sxs-lookup"><span data-stu-id="490ad-135">Therefore, this construct is equivalent to the following:</span></span>

<span data-ttu-id="490ad-136">`(?(?=`*運算式*`)`*是*`|`*否*`)`</span><span class="sxs-lookup"><span data-stu-id="490ad-136">`(?(?=` *expression* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="490ad-137">其中 `(?=`*expression*`)`) 是零寬度的判斷提示建構</span><span class="sxs-lookup"><span data-stu-id="490ad-137">where `(?=`*expression*`)` is a zero-width assertion construct.</span></span> <span data-ttu-id="490ad-138">（如需詳細資訊，請參閱[群組結構](grouping-constructs-in-regular-expressions.md)）。因為正則運算式引擎會將*expression*解讀為錨點（零寬度的判斷提示），所以*expression*必須是零寬度的判斷提示（如需詳細資訊，請參閱[錨點](anchors-in-regular-expressions.md)）或也包含在 *[是]* 中的子運算式。</span><span class="sxs-lookup"><span data-stu-id="490ad-138">(For more information, see [Grouping Constructs](grouping-constructs-in-regular-expressions.md).) Because the regular expression engine interprets *expression* as an anchor (a zero-width assertion), *expression* must either be a zero-width assertion (for more information, see [Anchors](anchors-in-regular-expressions.md)) or a subexpression that is also contained in *yes*.</span></span> <span data-ttu-id="490ad-139">否則就無法比對 *yes* 模式。</span><span class="sxs-lookup"><span data-stu-id="490ad-139">Otherwise, the *yes* pattern cannot be matched.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="490ad-140">如果*expression*是一個已命名或編號的捕捉群組，則交替結構會解讀為「捕捉測試」。如需詳細資訊，請參閱下一節[根據有效的 Capture 群組進行條件](#Conditional_Group)式比對。</span><span class="sxs-lookup"><span data-stu-id="490ad-140">If *expression* is a named or numbered capturing group, the alternation construct is interpreted as a capture test; for more information, see the next section, [Conditional Matching Based on a Valid Capture Group](#Conditional_Group).</span></span> <span data-ttu-id="490ad-141">換句話說，規則運算式引擎不會嘗試比對擷取的子字串，而會測試群組是否存在。</span><span class="sxs-lookup"><span data-stu-id="490ad-141">In other words, the regular expression engine does not attempt to match the captured substring, but instead tests for the presence or absence of the group.</span></span>  
  
<span data-ttu-id="490ad-142">下列範例是[以 &#124; 進行的二選一模式比對](#Either_Or)一節中使用的範例變化。</span><span class="sxs-lookup"><span data-stu-id="490ad-142">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="490ad-143">它使用條件式比對，來判斷字邊界後的前三個字元是否為兩個位數後接連字號。</span><span class="sxs-lookup"><span data-stu-id="490ad-143">It uses conditional matching to determine whether the first three characters after a word boundary are two digits followed by a hyphen.</span></span> <span data-ttu-id="490ad-144">如果是，它會嘗試比對美國美國雇主識別碼 (EIN)。</span><span class="sxs-lookup"><span data-stu-id="490ad-144">If they are, it attempts to match a U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="490ad-145">如果不是，它會嘗試比對美國社會安全碼 (SSN)。</span><span class="sxs-lookup"><span data-stu-id="490ad-145">If not, it attempts to match a U.S. Social Security Number (SSN).</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#3](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
[!code-vb[RegularExpressions.Language.Alternation#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]

<span data-ttu-id="490ad-146">正則運算式模式 `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` 的解讀方式如下表所示：</span><span class="sxs-lookup"><span data-stu-id="490ad-146">The regular expression pattern `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="490ad-147">模式</span><span class="sxs-lookup"><span data-stu-id="490ad-147">Pattern</span></span>|<span data-ttu-id="490ad-148">描述</span><span class="sxs-lookup"><span data-stu-id="490ad-148">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="490ad-149">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="490ad-149">Start at a word boundary.</span></span>|  
|`(?(\d{2}-)`|<span data-ttu-id="490ad-150">判斷接下來三個字元是否為兩個數字後接連字號。</span><span class="sxs-lookup"><span data-stu-id="490ad-150">Determine whether the next three characters consist of two digits followed by a hyphen.</span></span>|  
|`\d{2}-\d{7}`|<span data-ttu-id="490ad-151">如果上一個模式符合，便會比對兩個數字，後接連字號，再後接七個數字。</span><span class="sxs-lookup"><span data-stu-id="490ad-151">If the previous pattern matches, match two digits followed by a hyphen followed by seven digits.</span></span>|  
|`\d{3}-\d{2}-\d{4}`|<span data-ttu-id="490ad-152">如果上一個模式不符合，便會比對三個十進位數字、連字號、兩個十進位數字、另一個連字號，以及四個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="490ad-152">If the previous pattern does not match, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="490ad-153">比對字邊界。</span><span class="sxs-lookup"><span data-stu-id="490ad-153">Match a word boundary.</span></span>|  

<a name="Conditional_Group"></a>
## <a name="conditional-matching-based-on-a-valid-captured-group"></a><span data-ttu-id="490ad-154">依據有效擷取群組進行的條件式比對</span><span class="sxs-lookup"><span data-stu-id="490ad-154">Conditional matching based on a valid captured group</span></span>

<span data-ttu-id="490ad-155">這個語言項目會嘗試根據它是否已經比對指定的擷取群組，比對兩種模式的其中一種。</span><span class="sxs-lookup"><span data-stu-id="490ad-155">This language element attempts to match one of two patterns depending on whether it has matched a specified capturing group.</span></span> <span data-ttu-id="490ad-156">其語法如下：</span><span class="sxs-lookup"><span data-stu-id="490ad-156">Its syntax is:</span></span>

<span data-ttu-id="490ad-157">`(?(`*名稱*`)`*是*`|`*否*`)`</span><span class="sxs-lookup"><span data-stu-id="490ad-157">`(?(` *name* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="490ad-158">或</span><span class="sxs-lookup"><span data-stu-id="490ad-158">or</span></span>

<span data-ttu-id="490ad-159">`(?(`*數位*`)`*是*`|`*否*`)`</span><span class="sxs-lookup"><span data-stu-id="490ad-159">`(?(` *number* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="490ad-160">其中 *name* 是名稱，而 *number* 是擷取群組的數目， *yes* 是 *name* 或 *number* 其中之一相符時要比對的運算式，而 *no* 則是不符合時要比對的選擇性運算式。</span><span class="sxs-lookup"><span data-stu-id="490ad-160">where *name* is the name and *number* is the number of a capturing group, *yes* is the expression to match if *name* or *number* has a match, and *no* is the optional expression to match if it does not.</span></span>

<span data-ttu-id="490ad-161">如果 *name* 並未對應到規則運算式模式中所使用的擷取群組名稱，則替代建構會解譯為運算式測試，如上一節中所說明。</span><span class="sxs-lookup"><span data-stu-id="490ad-161">If *name* does not correspond to the name of a capturing group that is used in the regular expression pattern, the alternation construct is interpreted as an expression test, as explained in the previous section.</span></span> <span data-ttu-id="490ad-162">通常，這表示 *expression* 判斷值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="490ad-162">Typically, this means that *expression* evaluates to `false`.</span></span> <span data-ttu-id="490ad-163">如果 *number* 沒有對應到規則運算式模式中所使用的編號擷取群組，則規則運算式引擎會擲回 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="490ad-163">If *number* does not correspond to a numbered capturing group that is used in the regular expression pattern, the regular expression engine throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="490ad-164">下列範例是[以 &#124; 進行的二選一模式比對](#Either_Or)一節中使用的範例變化。</span><span class="sxs-lookup"><span data-stu-id="490ad-164">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="490ad-165">它會使用名為 `n2` 的擷取群組，其由兩個數字後接連字號所組成。</span><span class="sxs-lookup"><span data-stu-id="490ad-165">It uses a capturing group named `n2` that consists of two digits followed by a hyphen.</span></span> <span data-ttu-id="490ad-166">替代建構會測試是否已在輸入字串中比對這個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="490ad-166">The alternation construct tests whether this capturing group has been matched in the input string.</span></span> <span data-ttu-id="490ad-167">如果是，交替建構會嘗試比對九位數雇主識別碼 (EIN) 的末七碼。美國雇主識別碼 (EIN)。</span><span class="sxs-lookup"><span data-stu-id="490ad-167">If it has, the alternation construct attempts to match the last seven digits of a nine-digit U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="490ad-168">如果不是，則會嘗試比對九位數美國社會安全碼 (SSN)。社會安全碼 (SSN)。</span><span class="sxs-lookup"><span data-stu-id="490ad-168">If it has not, it attempts to match a nine-digit U.S. Social Security Number (SSN).</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#4](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
[!code-vb[RegularExpressions.Language.Alternation#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]

<span data-ttu-id="490ad-169">正則運算式模式 `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` 的解讀方式如下表所示：</span><span class="sxs-lookup"><span data-stu-id="490ad-169">The regular expression pattern `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="490ad-170">模式</span><span class="sxs-lookup"><span data-stu-id="490ad-170">Pattern</span></span>|<span data-ttu-id="490ad-171">描述</span><span class="sxs-lookup"><span data-stu-id="490ad-171">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="490ad-172">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="490ad-172">Start at a word boundary.</span></span>|  
|`(?<n2>\d{2}-)?`|<span data-ttu-id="490ad-173">比對出現零次或一次且後接連字號的兩個數字。</span><span class="sxs-lookup"><span data-stu-id="490ad-173">Match zero or one occurrence of two digits followed by a hyphen.</span></span> <span data-ttu-id="490ad-174">將此擷取群組命名為 `n2`。</span><span class="sxs-lookup"><span data-stu-id="490ad-174">Name this capturing group `n2`.</span></span>|  
|`(?(n2)`|<span data-ttu-id="490ad-175">測試 `n2` 在輸入字串中是否相符。</span><span class="sxs-lookup"><span data-stu-id="490ad-175">Test whether `n2` was matched in the input string.</span></span>|  
|`\d{7}`|<span data-ttu-id="490ad-176">如果 `n2` 相符，則會比對七個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="490ad-176">If `n2` was matched, match seven decimal digits.</span></span>|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|<span data-ttu-id="490ad-177">如果 `n2` 不相符，則會比對三個十進位數字、一個連字號、兩個十進位數字、另一個連字號，以及四個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="490ad-177">If `n2` was not matched, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="490ad-178">比對字邊界。</span><span class="sxs-lookup"><span data-stu-id="490ad-178">Match a word boundary.</span></span>|  

<span data-ttu-id="490ad-179">此範例是使用編號的群組而不是具名群組的一種變化，如下所示。</span><span class="sxs-lookup"><span data-stu-id="490ad-179">A variation of this example that uses a numbered group instead of a named group is shown in the following example.</span></span> <span data-ttu-id="490ad-180">它的規則運算式模式是 `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`。</span><span class="sxs-lookup"><span data-stu-id="490ad-180">Its regular expression pattern is `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#5](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
[!code-vb[RegularExpressions.Language.Alternation#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]

## <a name="see-also"></a><span data-ttu-id="490ad-181">另請參閱</span><span class="sxs-lookup"><span data-stu-id="490ad-181">See also</span></span>

- [<span data-ttu-id="490ad-182">規則運算式語言 - 快速參考</span><span class="sxs-lookup"><span data-stu-id="490ad-182">Regular Expression Language - Quick Reference</span></span>](regular-expression-language-quick-reference.md)
