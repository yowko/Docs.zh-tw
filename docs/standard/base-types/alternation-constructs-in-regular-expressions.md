---
title: "規則運算式中的替代建構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6ad632130b6f111ff863648b8b1a3b2835c27660
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="alternation-constructs-in-regular-expressions"></a><span data-ttu-id="b6887-102">規則運算式中的替代建構</span><span class="sxs-lookup"><span data-stu-id="b6887-102">Alternation Constructs in Regular Expressions</span></span>
<span data-ttu-id="b6887-103"><a name="top"></a> 交替建構會修改規則運算式來啟用二選一或條件式比對。</span><span class="sxs-lookup"><span data-stu-id="b6887-103"><a name="top"></a> Alternation constructs modify a regular expression to enable either/or or conditional matching.</span></span> <span data-ttu-id="b6887-104">.NET 支援下列三種替代建構：</span><span class="sxs-lookup"><span data-stu-id="b6887-104">.NET supports three alternation constructs:</span></span>  
  
-   [<span data-ttu-id="b6887-105">以 &#124; 進行的模式比對</span><span class="sxs-lookup"><span data-stu-id="b6887-105">Pattern matching with &#124;</span></span>](#Either_Or)  
  
-   [<span data-ttu-id="b6887-106">以 (?(expression)yes&#124;no) 進行的條件式比對</span><span class="sxs-lookup"><span data-stu-id="b6887-106">Conditional matching with (?(expression)yes&#124;no)</span></span>](#Conditional_Expr)  
  
-   [<span data-ttu-id="b6887-107">依據有效擷取群組進行的條件式比對</span><span class="sxs-lookup"><span data-stu-id="b6887-107">Conditional matching based on a valid captured group</span></span>](#Conditional_Group)  
  
<a name="Either_Or"></a>   
## <a name="pattern-matching-with-124"></a><span data-ttu-id="b6887-108">以 &#124; 進行的模式比對</span><span class="sxs-lookup"><span data-stu-id="b6887-108">Pattern Matching with &#124;</span></span>  
 <span data-ttu-id="b6887-109">您可以使用分隔號 (`|`) 字元來比對其中任一系列的模式，且 `|` 字元會分隔每一個模式。</span><span class="sxs-lookup"><span data-stu-id="b6887-109">You can use the vertical bar (`|`) character to match any one of a series of patterns, where the `|` character separates each pattern.</span></span>  
  
 <span data-ttu-id="b6887-110">`|` 字元和正字元類別一樣，可以用來比對一些單一字元當中的任一字元。</span><span class="sxs-lookup"><span data-stu-id="b6887-110">Like the positive character class, the `|` character can be used to match any one of a number of single characters.</span></span> <span data-ttu-id="b6887-111">下列範例同時使用正字元類別和透過 `|` 字元的二選一模式比對，在字串中尋找與單字 "gray" 或 "grey" 相符的項目。</span><span class="sxs-lookup"><span data-stu-id="b6887-111">The following example uses both a positive character class and either/or pattern matching with the `|` character to locate occurrences of the words "gray" or "grey" in a string.</span></span> <span data-ttu-id="b6887-112">在此案例中， `|` 字元會產生更詳細的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="b6887-112">In this case, the `|` character produces a regular expression that is more verbose.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
 [!code-vb[RegularExpressions.Language.Alternation#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]  
  
 <span data-ttu-id="b6887-113">使用 `|` 字元的規則運算式 `\bgr(a|e)y\b`的解譯方式如下表所示。</span><span class="sxs-lookup"><span data-stu-id="b6887-113">The regular expression that uses the `|` character, `\bgr(a|e)y\b`, is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="b6887-114">模式</span><span class="sxs-lookup"><span data-stu-id="b6887-114">Pattern</span></span>|<span data-ttu-id="b6887-115">描述</span><span class="sxs-lookup"><span data-stu-id="b6887-115">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="b6887-116">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="b6887-116">Start at a word boundary.</span></span>|  
|`gr`|<span data-ttu-id="b6887-117">比對字元 "gr"。</span><span class="sxs-lookup"><span data-stu-id="b6887-117">Match the characters "gr".</span></span>|  
|<code>(a&#124;e)</code>|<span data-ttu-id="b6887-118">比對 "a" 或 "e"。</span><span class="sxs-lookup"><span data-stu-id="b6887-118">Match either an "a" or an "e".</span></span>|  
|`y\b`|<span data-ttu-id="b6887-119">比對字邊界上的 "y"。</span><span class="sxs-lookup"><span data-stu-id="b6887-119">Match a "y" on a word boundary.</span></span>|  
  
 <span data-ttu-id="b6887-120">`|` 字元也可以用來與多個字元或子運算式執行兩選一的比對，這些字元或運算式可以包含字元常值和規則運算式語言項目的任何組合。</span><span class="sxs-lookup"><span data-stu-id="b6887-120">The `|` character can also be used to perform an either/or match with multiple characters or subexpressions, which can include any combination of character literals and regular expression language elements.</span></span> <span data-ttu-id="b6887-121">然而，字元類別並不提供這項功能。下列範例使用 `|` 字元擷取其中任一組美國社會安全號碼 (SSN)，*ddd*-*dd*-*dddd* 格式的 9 位數數字，或擷取美國雇主識別碼 (EIN)，其為 *dd*-*ddddddd* 格式的 9 位數數字。</span><span class="sxs-lookup"><span data-stu-id="b6887-121">(The character class does not provide this functionality.) The following example uses the `|` character to extract either a U.S. Social Security Number (SSN), which is a 9-digit number with the format *ddd*-*dd*-*dddd*, or a U.S. Employer Identification Number (EIN), which is a 9-digit number with the format *dd*-*ddddddd*.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
 [!code-vb[RegularExpressions.Language.Alternation#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  
  
 <span data-ttu-id="b6887-122">規則運算式 `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` 的解譯方式如下表所示。</span><span class="sxs-lookup"><span data-stu-id="b6887-122">The regular expression `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="b6887-123">模式</span><span class="sxs-lookup"><span data-stu-id="b6887-123">Pattern</span></span>|<span data-ttu-id="b6887-124">描述</span><span class="sxs-lookup"><span data-stu-id="b6887-124">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="b6887-125">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="b6887-125">Start at a word boundary.</span></span>|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|<span data-ttu-id="b6887-126">比對下列其中一項：兩個十進位數字後接連字號再後接七個十進位數字，或是三個十進位數字、連字號、兩個十進位數字、另一個連字號及四個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="b6887-126">Match either of the following: two decimal digits followed by a hyphen followed by seven decimal digits; or three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\d`|<span data-ttu-id="b6887-127">結束字緣比對。</span><span class="sxs-lookup"><span data-stu-id="b6887-127">End the match at a word boundary.</span></span>|  
  
 [<span data-ttu-id="b6887-128">回到頁首</span><span class="sxs-lookup"><span data-stu-id="b6887-128">Back to top</span></span>](#top)  
  
<a name="Conditional_Expr"></a>   
## <a name="conditional-matching-with-an-expression"></a><span data-ttu-id="b6887-129">以運算式進行的條件式比對</span><span class="sxs-lookup"><span data-stu-id="b6887-129">Conditional Matching with an Expression</span></span>  
 <span data-ttu-id="b6887-130">這個語言項目會嘗試比對兩個模式的其中一個是否符合初始模式。</span><span class="sxs-lookup"><span data-stu-id="b6887-130">This language element attempts to match one of two patterns depending on whether it can match an initial pattern.</span></span> <span data-ttu-id="b6887-131">它的語法為：</span><span class="sxs-lookup"><span data-stu-id="b6887-131">Its syntax is:</span></span>  
  
 <span data-ttu-id="b6887-132">`(?(` *運算式* `)` *是* `|` *no* `)`</span><span class="sxs-lookup"><span data-stu-id="b6887-132">`(?(` *expression* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="b6887-133">其中 *expression* 是要比對的初始模式， *yes* 是符合 *expression* 時要比對的模式，而 *no* 是不符合 *expression* 時要比對的選擇性模式。</span><span class="sxs-lookup"><span data-stu-id="b6887-133">where *expression* is the initial pattern to match, *yes* is the pattern to match if *expression* is matched, and *no* is the optional pattern to match if *expression* is not matched.</span></span> <span data-ttu-id="b6887-134">規則運算式引擎會將 *expression* 視為零寬度的判斷提示，也就是說，規則運算式引擎不會在評估 *expression*之後於輸入資料流中前進。</span><span class="sxs-lookup"><span data-stu-id="b6887-134">The regular expression engine treats *expression* as a zero-width assertion; that is, the regular expression engine does not advance in the input stream after it evaluates *expression*.</span></span> <span data-ttu-id="b6887-135">因此，此建構等同於下列：</span><span class="sxs-lookup"><span data-stu-id="b6887-135">Therefore, this construct is equivalent to the following:</span></span>  
  
 <span data-ttu-id="b6887-136">`(?(?=` *運算式* `)` *是* `|` *no* `)`</span><span class="sxs-lookup"><span data-stu-id="b6887-136">`(?(?=` *expression* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="b6887-137">其中 `(?=`*expression*`)`) 是零寬度的判斷提示建構</span><span class="sxs-lookup"><span data-stu-id="b6887-137">where `(?=`*expression*`)` is a zero-width assertion construct.</span></span> <span data-ttu-id="b6887-138">(如需詳細資訊，請參閱[群組建構](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)。)由於規則運算式引擎會將 *expression* 解譯為錨點 (零寬度的判斷提示)，因此 *expression* 必須是零寬度的判斷提示 (如需詳細資訊，請參閱[錨點](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) 或是同樣包含在 *yes* 中的子運算式。</span><span class="sxs-lookup"><span data-stu-id="b6887-138">(For more information, see [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Because the regular expression engine interprets *expression* as an anchor (a zero-width assertion), *expression* must either be a zero-width assertion (for more information, see [Anchors](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) or a subexpression that is also contained in *yes*.</span></span> <span data-ttu-id="b6887-139">否則就無法比對 *yes* 模式。</span><span class="sxs-lookup"><span data-stu-id="b6887-139">Otherwise, the *yes* pattern cannot be matched.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6887-140">如果 *expression*是具名或編號的擷取群組，則交替建構會解譯為擷取測試。如需詳細資訊，請參閱下一節 [依據有效擷取群組進行的條件式比對](#Conditional_Group)。</span><span class="sxs-lookup"><span data-stu-id="b6887-140">If *expression*is a named or numbered capturing group, the alternation construct is interpreted as a capture test; for more information, see the next section, [Conditional Matching Based on a Valid Capture Group](#Conditional_Group).</span></span> <span data-ttu-id="b6887-141">換句話說，規則運算式引擎不會嘗試比對擷取的子字串，而會測試群組是否存在。</span><span class="sxs-lookup"><span data-stu-id="b6887-141">In other words, the regular expression engine does not attempt to match the captured substring, but instead tests for the presence or absence of the group.</span></span>  
  
 <span data-ttu-id="b6887-142">下列範例是[以 &#124; 進行的二選一模式比對](#Either_Or)一節中使用的範例變化。</span><span class="sxs-lookup"><span data-stu-id="b6887-142">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="b6887-143">它使用條件式比對，來判斷字邊界後的前三個字元是否為兩個位數後接連字號。</span><span class="sxs-lookup"><span data-stu-id="b6887-143">It uses conditional matching to determine whether the first three characters after a word boundary are two digits followed by a hyphen.</span></span> <span data-ttu-id="b6887-144">如果是，它會嘗試比對美國美國雇主識別碼 (EIN)。</span><span class="sxs-lookup"><span data-stu-id="b6887-144">If they are, it attempts to match a U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="b6887-145">如果不是，它會嘗試比對美國社會安全碼 (SSN)。</span><span class="sxs-lookup"><span data-stu-id="b6887-145">If not, it attempts to match a U.S. Social Security Number (SSN).</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
 [!code-vb[RegularExpressions.Language.Alternation#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]  
  
 <span data-ttu-id="b6887-146">規則運算式模式 `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` 的解譯方式如下表所示。</span><span class="sxs-lookup"><span data-stu-id="b6887-146">The regular expression pattern `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="b6887-147">模式</span><span class="sxs-lookup"><span data-stu-id="b6887-147">Pattern</span></span>|<span data-ttu-id="b6887-148">描述</span><span class="sxs-lookup"><span data-stu-id="b6887-148">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="b6887-149">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="b6887-149">Start at a word boundary.</span></span>|  
|`(?(\d{2}-)`|<span data-ttu-id="b6887-150">判斷接下來三個字元是否為兩個數字後接連字號。</span><span class="sxs-lookup"><span data-stu-id="b6887-150">Determine whether the next three characters consist of two digits followed by a hyphen.</span></span>|  
|`\d{2}-\d{7}`|<span data-ttu-id="b6887-151">如果上一個模式符合，便會比對兩個數字，後接連字號，再後接七個數字。</span><span class="sxs-lookup"><span data-stu-id="b6887-151">If the previous pattern matches, match two digits followed by a hyphen followed by seven digits.</span></span>|  
|`\d{3}-\d{2}-\d{4}`|<span data-ttu-id="b6887-152">如果上一個模式不符合，便會比對三個十進位數字、連字號、兩個十進位數字、另一個連字號，以及四個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="b6887-152">If the previous pattern does not match, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="b6887-153">比對字邊界。</span><span class="sxs-lookup"><span data-stu-id="b6887-153">Match a word boundary.</span></span>|  
  
 [<span data-ttu-id="b6887-154">回到頁首</span><span class="sxs-lookup"><span data-stu-id="b6887-154">Back to top</span></span>](#top)  
  
<a name="Conditional_Group"></a>   
## <a name="conditional-matching-based-on-a-valid-captured-group"></a><span data-ttu-id="b6887-155">依據有效擷取群組進行的條件式比對</span><span class="sxs-lookup"><span data-stu-id="b6887-155">Conditional Matching Based on a Valid Captured Group</span></span>  
 <span data-ttu-id="b6887-156">這個語言項目會嘗試根據它是否已經比對指定的擷取群組，比對兩種模式的其中一種。</span><span class="sxs-lookup"><span data-stu-id="b6887-156">This language element attempts to match one of two patterns depending on whether it has matched a specified capturing group.</span></span> <span data-ttu-id="b6887-157">它的語法為：</span><span class="sxs-lookup"><span data-stu-id="b6887-157">Its syntax is:</span></span>  
  
 <span data-ttu-id="b6887-158">`(?(` *name* `)` *是* `|` *no* `)`</span><span class="sxs-lookup"><span data-stu-id="b6887-158">`(?(` *name* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="b6887-159">或</span><span class="sxs-lookup"><span data-stu-id="b6887-159">or</span></span>  
  
 <span data-ttu-id="b6887-160">`(?(` *數字* `)` *是* `|` *no* `)`</span><span class="sxs-lookup"><span data-stu-id="b6887-160">`(?(` *number* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="b6887-161">其中 *name* 是名稱，而 *number* 是擷取群組的數目， *yes* 是 *name* 或 *number* 其中之一相符時要比對的運算式，而 *no* 則是不符合時要比對的選擇性運算式。</span><span class="sxs-lookup"><span data-stu-id="b6887-161">where *name* is the name and *number* is the number of a capturing group, *yes* is the expression to match if *name* or *number* has a match, and *no* is the optional expression to match if it does not.</span></span>  
  
 <span data-ttu-id="b6887-162">如果 *name* 並未對應到規則運算式模式中所使用的擷取群組名稱，則交替建構會解譯為運算式測試，如上一節中所說明。</span><span class="sxs-lookup"><span data-stu-id="b6887-162">If *name* does not correspond to the name of a capturing group that is used in the regular expression pattern, the alternation construct is interpreted as an expression test, as explained in the previous section.</span></span> <span data-ttu-id="b6887-163">通常，這表示 *expression* 判斷值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="b6887-163">Typically, this means that *expression* evaluates to `false`.</span></span> <span data-ttu-id="b6887-164">如果 *number* 沒有對應到規則運算式模式中所使用的編號擷取群組，則規則運算式引擎會擲回 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="b6887-164">If *number* does not correspond to a numbered capturing group that is used in the regular expression pattern, the regular expression engine throws an <xref:System.ArgumentException>.</span></span>  
  
 <span data-ttu-id="b6887-165">下列範例是[以 &#124; 進行的二選一模式比對](#Either_Or)一節中使用的範例變化。</span><span class="sxs-lookup"><span data-stu-id="b6887-165">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="b6887-166">它會使用名為 `n2` 的擷取群組，其由兩個數字後接連字號所組成。</span><span class="sxs-lookup"><span data-stu-id="b6887-166">It uses a capturing group named `n2` that consists of two digits followed by a hyphen.</span></span> <span data-ttu-id="b6887-167">替代建構會測試是否已在輸入字串中比對這個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="b6887-167">The alternation construct tests whether this capturing group has been matched in the input string.</span></span> <span data-ttu-id="b6887-168">如果是，替代建構會嘗試比對九位數雇主識別碼 (EIN) 的末七碼。美國雇主識別碼 (EIN)。</span><span class="sxs-lookup"><span data-stu-id="b6887-168">If it has, the alternation construct attempts to match the last seven digits of a nine-digit U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="b6887-169">如果不是，則會嘗試比對九位數美國社會安全碼 (SSN)。社會安全碼 (SSN)。</span><span class="sxs-lookup"><span data-stu-id="b6887-169">If it has not, it attempts to match a nine-digit U.S. Social Security Number (SSN).</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
 [!code-vb[RegularExpressions.Language.Alternation#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]  
  
 <span data-ttu-id="b6887-170">規則運算式模式 `\b(?<n2>\d{2}-)*(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` 的解譯方式如下表所示。</span><span class="sxs-lookup"><span data-stu-id="b6887-170">The regular expression pattern `\b(?<n2>\d{2}-)*(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="b6887-171">模式</span><span class="sxs-lookup"><span data-stu-id="b6887-171">Pattern</span></span>|<span data-ttu-id="b6887-172">描述</span><span class="sxs-lookup"><span data-stu-id="b6887-172">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="b6887-173">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="b6887-173">Start at a word boundary.</span></span>|  
|`(?<n2>\d{2}-)*`|<span data-ttu-id="b6887-174">比對出現零次或一次且後接連字號的兩個數字。</span><span class="sxs-lookup"><span data-stu-id="b6887-174">Match zero or one occurrence of two digits followed by a hyphen.</span></span> <span data-ttu-id="b6887-175">將此擷取群組命名為 `n2`。</span><span class="sxs-lookup"><span data-stu-id="b6887-175">Name this capturing group `n2`.</span></span>|  
|`(?(n2)`|<span data-ttu-id="b6887-176">測試 `n2` 在輸入字串中是否相符。</span><span class="sxs-lookup"><span data-stu-id="b6887-176">Test whether `n2` was matched in the input string.</span></span>|  
|`)\d{7}`|<span data-ttu-id="b6887-177">如果 `n2` 相符，則會比對七個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="b6887-177">If `n2` was matched, match seven decimal digits.</span></span>|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|<span data-ttu-id="b6887-178">如果 `n2` 不相符，則會比對三個十進位數字、一個連字號、兩個十進位數字、另一個連字號，以及四個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="b6887-178">If `n2` was not matched, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="b6887-179">比對字邊界。</span><span class="sxs-lookup"><span data-stu-id="b6887-179">Match a word boundary.</span></span>|  
  
 <span data-ttu-id="b6887-180">此範例是使用編號的群組而不是具名群組的一種變化，如下所示。</span><span class="sxs-lookup"><span data-stu-id="b6887-180">A variation of this example that uses a numbered group instead of a named group is shown in the following example.</span></span> <span data-ttu-id="b6887-181">它的規則運算式模式是 `\b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`。</span><span class="sxs-lookup"><span data-stu-id="b6887-181">Its regular expression pattern is `\b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
 [!code-vb[RegularExpressions.Language.Alternation#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="b6887-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6887-182">See Also</span></span>  
 [<span data-ttu-id="b6887-183">規則運算式語言 - 快速參考</span><span class="sxs-lookup"><span data-stu-id="b6887-183">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
