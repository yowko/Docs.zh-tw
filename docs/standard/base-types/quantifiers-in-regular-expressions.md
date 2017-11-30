---
title: "規則運算式中的數量詞"
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
- regular expressions, quantifiers
- metacharacters, quantifiers
- minimal matching quantifiers
- quantifiers in regular expressions
- .NET Framework regular expressions, quantifiers
- quantifiers
- lazy quantifiers
ms.assetid: 36b81212-6511-49ed-a8f1-ff080415312f
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ab06aa0c331c8cbd4c8986cced29334046f30264
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="quantifiers-in-regular-expressions"></a><span data-ttu-id="7c932-102">規則運算式中的數量詞</span><span class="sxs-lookup"><span data-stu-id="7c932-102">Quantifiers in Regular Expressions</span></span>
<span data-ttu-id="7c932-103">數量詞指定輸入中要有多少字元、群組或字元類別的執行個體，才能找到相符項目。</span><span class="sxs-lookup"><span data-stu-id="7c932-103">Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found.</span></span>  <span data-ttu-id="7c932-104">下表列出 .NET 支援的數量詞。</span><span class="sxs-lookup"><span data-stu-id="7c932-104">The following table lists the quantifiers supported by .NET.</span></span>  
  
|<span data-ttu-id="7c932-105">Greedy (窮盡) 數量詞</span><span class="sxs-lookup"><span data-stu-id="7c932-105">Greedy quantifier</span></span>|<span data-ttu-id="7c932-106">Lazy (最少) 數量詞</span><span class="sxs-lookup"><span data-stu-id="7c932-106">Lazy quantifier</span></span>|<span data-ttu-id="7c932-107">說明</span><span class="sxs-lookup"><span data-stu-id="7c932-107">Description</span></span>|  
|-----------------------|---------------------|-----------------|  
|`*`|`*?`|<span data-ttu-id="7c932-108">比對零或多次。</span><span class="sxs-lookup"><span data-stu-id="7c932-108">Match zero or more times.</span></span>|  
|`+`|`+?`|<span data-ttu-id="7c932-109">比對一或多次。</span><span class="sxs-lookup"><span data-stu-id="7c932-109">Match one or more times.</span></span>|  
|`?`|`??`|<span data-ttu-id="7c932-110">比對零或一次。</span><span class="sxs-lookup"><span data-stu-id="7c932-110">Match zero or one time.</span></span>|  
|<span data-ttu-id="7c932-111">`{` *n* `}`</span><span class="sxs-lookup"><span data-stu-id="7c932-111">`{` *n* `}`</span></span>|<span data-ttu-id="7c932-112">`{` *n* `}?`</span><span class="sxs-lookup"><span data-stu-id="7c932-112">`{` *n* `}?`</span></span>|<span data-ttu-id="7c932-113">完全符合 *n* 時間。</span><span class="sxs-lookup"><span data-stu-id="7c932-113">Match exactly *n* times.</span></span>|  
|<span data-ttu-id="7c932-114">`{` *n* `,}`</span><span class="sxs-lookup"><span data-stu-id="7c932-114">`{` *n* `,}`</span></span>|<span data-ttu-id="7c932-115">`{` *n* `,}?`</span><span class="sxs-lookup"><span data-stu-id="7c932-115">`{` *n* `,}?`</span></span>|<span data-ttu-id="7c932-116">符合至少 *n* 時間。</span><span class="sxs-lookup"><span data-stu-id="7c932-116">Match at least *n* times.</span></span>|  
|<span data-ttu-id="7c932-117">`{` *n* `,` *m* `}`</span><span class="sxs-lookup"><span data-stu-id="7c932-117">`{` *n* `,` *m* `}`</span></span>|<span data-ttu-id="7c932-118">`{` *n* `,` *m* `}?`</span><span class="sxs-lookup"><span data-stu-id="7c932-118">`{` *n* `,` *m* `}?`</span></span>|<span data-ttu-id="7c932-119">從符合 *n* 至*m*時間。</span><span class="sxs-lookup"><span data-stu-id="7c932-119">Match from *n* to *m* times.</span></span>|  
  
 <span data-ttu-id="7c932-120">將數量`n`和`m`都是整數常數。</span><span class="sxs-lookup"><span data-stu-id="7c932-120">The quantities `n` and `m` are integer constants.</span></span> <span data-ttu-id="7c932-121">數量詞通常是 Greedy (窮盡)。其會讓規則運算式引擎盡可能多地從每次出現的特定模式進行比對。</span><span class="sxs-lookup"><span data-stu-id="7c932-121">Ordinarily, quantifiers are greedy; they cause the regular expression engine to match as many occurrences of particular patterns as possible.</span></span> <span data-ttu-id="7c932-122">在量詞中加上 `?` 字元會使它 lazy (忽略優先)，造成規則運算式引擎比對的項目愈少愈好。</span><span class="sxs-lookup"><span data-stu-id="7c932-122">Appending the `?` character to a quantifier makes it lazy; it causes the regular expression engine to match as few occurrences as possible.</span></span> <span data-ttu-id="7c932-123">如需 greedy (匹配優先) 與 lazy (忽略優先) 量詞間差異的完整說明，請參閱本主題稍後的 [Greedy (匹配優先) 與 Lazy (忽略優先) 量詞](#Greedy)一節。</span><span class="sxs-lookup"><span data-stu-id="7c932-123">For a complete description of the difference between greedy and lazy quantifiers, see the section [Greedy and Lazy Quantifiers](#Greedy) later in this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7c932-124">巢狀數量詞 (如規則運算式模式 `(a*)*` 所做) 會增加規則運算式引擎必須執行的比較次數，如輸入字串中的字元數指數函數一樣。</span><span class="sxs-lookup"><span data-stu-id="7c932-124">Nesting quantifiers (for example, as the regular expression pattern `(a*)*` does) can increase the number of comparisons that the regular expression engine must perform, as an exponential function of the number of characters in the input string.</span></span> <span data-ttu-id="7c932-125">如需有關此行為，以及其因應措施的詳細資訊，請參閱[回溯](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="7c932-125">For more information about this behavior and its workarounds, see [Backtracking](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).</span></span>  
  
## <a name="regular-expression-quantifiers"></a><span data-ttu-id="7c932-126">規則運算式量詞</span><span class="sxs-lookup"><span data-stu-id="7c932-126">Regular Expression Quantifiers</span></span>  
 <span data-ttu-id="7c932-127">下列章節會列出 .NET 規則運算式支援的數量詞。</span><span class="sxs-lookup"><span data-stu-id="7c932-127">The following sections list the quantifiers supported by .NET regular expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c932-128">如果 *，+，？，{，與} 字元在規則運算式模式中遇到，規則運算式引擎會將它們解譯為數量詞或組件的數量詞的建構除非它們包含在[字元類別](../../../docs/standard/base-types/character-classes-in-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="7c932-128">If the *, +, ?, {, and } characters are encountered in a regular expression pattern, the regular expression engine interprets them as quantifiers or part of quantifier constructs unless they are included in a [character class](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).</span></span> <span data-ttu-id="7c932-129">若要在字元類別外將這些字元解譯為常值字元，您必須在它們前面加上反斜線以逸出字元。</span><span class="sxs-lookup"><span data-stu-id="7c932-129">To interpret these as literal characters outside a character class, you must escape them by preceding them with a backslash.</span></span> <span data-ttu-id="7c932-130">例如，字串`\*`在規則運算式模式會解譯為常值的星號 ("\*") 字元。</span><span class="sxs-lookup"><span data-stu-id="7c932-130">For example, the string `\*` in a regular expression pattern is interpreted as a literal asterisk ("\*") character.</span></span>  
  
### <a name="match-zero-or-more-times-"></a><span data-ttu-id="7c932-131">比對零或多次：*</span><span class="sxs-lookup"><span data-stu-id="7c932-131">Match Zero or More Times: *</span></span>  
 <span data-ttu-id="7c932-132">`*` 數量詞會比對前置元素零次或多次。</span><span class="sxs-lookup"><span data-stu-id="7c932-132">The `*` quantifier matches the preceding element zero or more times.</span></span> <span data-ttu-id="7c932-133">它相當於`{0,}`數量詞。</span><span class="sxs-lookup"><span data-stu-id="7c932-133">It is equivalent to the `{0,}` quantifier.</span></span> <span data-ttu-id="7c932-134">`*`是窮盡數量詞，其延遲的對等項目是`*?`。</span><span class="sxs-lookup"><span data-stu-id="7c932-134">`*` is a greedy quantifier whose lazy equivalent is `*?`.</span></span>  
  
 <span data-ttu-id="7c932-135">下例會示範此規則運算式。</span><span class="sxs-lookup"><span data-stu-id="7c932-135">The following example illustrates this regular expression.</span></span> <span data-ttu-id="7c932-136">在輸入字串的九個數字中，有五個符合模式，四個 (`95`、`929`、`9129` 和 `9919`) 不符合。</span><span class="sxs-lookup"><span data-stu-id="7c932-136">Of the nine digits in the input string, five match the pattern and four (`95`, `929`, `9129`, and `9919`) do not.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#1)]  
  
 <span data-ttu-id="7c932-137">規則運算式模式的定義如下表所示。</span><span class="sxs-lookup"><span data-stu-id="7c932-137">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="7c932-138">模式</span><span class="sxs-lookup"><span data-stu-id="7c932-138">Pattern</span></span>|<span data-ttu-id="7c932-139">描述</span><span class="sxs-lookup"><span data-stu-id="7c932-139">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="7c932-140">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="7c932-140">Start at a word boundary.</span></span>|  
|`91*`|<span data-ttu-id="7c932-141">比對後面接著零或多個 "1" 字元的 "9"。</span><span class="sxs-lookup"><span data-stu-id="7c932-141">Match a "9" followed by zero or more "1" characters.</span></span>|  
|`9*`|<span data-ttu-id="7c932-142">比對零或多個 "9" 字元。</span><span class="sxs-lookup"><span data-stu-id="7c932-142">Match zero or more "9" characters.</span></span>|  
|`\b`|<span data-ttu-id="7c932-143">在字邊界結束。</span><span class="sxs-lookup"><span data-stu-id="7c932-143">End at a word boundary.</span></span>|  
  
### <a name="match-one-or-more-times-"></a><span data-ttu-id="7c932-144">比對一或多次：+</span><span class="sxs-lookup"><span data-stu-id="7c932-144">Match One or More Times: +</span></span>  
 <span data-ttu-id="7c932-145">`+`數量詞比對前面的項目一次以上。</span><span class="sxs-lookup"><span data-stu-id="7c932-145">The `+` quantifier matches the preceding element one or more times.</span></span> <span data-ttu-id="7c932-146">它相當於`{1,}`。</span><span class="sxs-lookup"><span data-stu-id="7c932-146">It is equivalent to `{1,}`.</span></span> <span data-ttu-id="7c932-147">`+`是窮盡數量詞，其延遲的對等項目是`+?`。</span><span class="sxs-lookup"><span data-stu-id="7c932-147">`+` is a greedy quantifier whose lazy equivalent is `+?`.</span></span>  
  
 <span data-ttu-id="7c932-148">例如，規則運算式 `\ban+\w*?\b` 會嘗試比對以字母 `a` 開頭、接著一或多個字母 `n` 的單字。</span><span class="sxs-lookup"><span data-stu-id="7c932-148">For example, the regular expression `\ban+\w*?\b` tries to match entire words that begin with the letter `a` followed by one or more instances of the letter `n`.</span></span> <span data-ttu-id="7c932-149">下例會示範此規則運算式。</span><span class="sxs-lookup"><span data-stu-id="7c932-149">The following example illustrates this regular expression.</span></span> <span data-ttu-id="7c932-150">規則運算式會比對出單字 `an`、`annual`、`announcement` 和 `antique`，而不會比對出 `autumn` 和 `all`。</span><span class="sxs-lookup"><span data-stu-id="7c932-150">The regular expression matches the words `an`, `annual`, `announcement`, and `antique`, and correctly fails to match `autumn` and `all`.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#2)]  
  
 <span data-ttu-id="7c932-151">規則運算式模式的定義如下表所示。</span><span class="sxs-lookup"><span data-stu-id="7c932-151">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="7c932-152">模式</span><span class="sxs-lookup"><span data-stu-id="7c932-152">Pattern</span></span>|<span data-ttu-id="7c932-153">描述</span><span class="sxs-lookup"><span data-stu-id="7c932-153">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="7c932-154">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="7c932-154">Start at a word boundary.</span></span>|  
|`an+`|<span data-ttu-id="7c932-155">比對 "a" 接著一或多個 "n" 字元。</span><span class="sxs-lookup"><span data-stu-id="7c932-155">Match an "a" followed by one or more "n" characters.</span></span>|  
|`\w*?`|<span data-ttu-id="7c932-156">比對單字字元零或多次，但次數愈少愈好。</span><span class="sxs-lookup"><span data-stu-id="7c932-156">Match a word character zero or more times, but as few times as possible.</span></span>|  
|`\b`|<span data-ttu-id="7c932-157">在字邊界結束。</span><span class="sxs-lookup"><span data-stu-id="7c932-157">End at a word boundary.</span></span>|  
  
### <a name="match-zero-or-one-time-"></a><span data-ttu-id="7c932-158">比對零或一次：?</span><span class="sxs-lookup"><span data-stu-id="7c932-158">Match Zero or One Time: ?</span></span>  
 <span data-ttu-id="7c932-159">`?`數量詞符合上述的零個或一個項目時間。</span><span class="sxs-lookup"><span data-stu-id="7c932-159">The `?` quantifier matches the preceding element zero or one time.</span></span> <span data-ttu-id="7c932-160">它相當於`{0,1}`。</span><span class="sxs-lookup"><span data-stu-id="7c932-160">It is equivalent to `{0,1}`.</span></span> <span data-ttu-id="7c932-161">`?`是窮盡數量詞，其延遲的對等項目是`??`。</span><span class="sxs-lookup"><span data-stu-id="7c932-161">`?` is a greedy quantifier whose lazy equivalent is `??`.</span></span>  
  
 <span data-ttu-id="7c932-162">例如，規則運算式 `\ban?\b` 會嘗試比對以字母 `a` 開頭、接著零或一個字母 `n` 的單字。</span><span class="sxs-lookup"><span data-stu-id="7c932-162">For example, the regular expression `\ban?\b` tries to match entire words that begin with the letter `a` followed by zero or one instances of the letter `n`.</span></span> <span data-ttu-id="7c932-163">換言之，它會嘗試比對單字 `a` 和 `an`。</span><span class="sxs-lookup"><span data-stu-id="7c932-163">In other words, it tries to match the words `a` and `an`.</span></span> <span data-ttu-id="7c932-164">下例會示範此規則運算式。</span><span class="sxs-lookup"><span data-stu-id="7c932-164">The following example illustrates this regular expression.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#3)]
 [!code-vb[RegularExpressions.Quantifiers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#3)]  
  
 <span data-ttu-id="7c932-165">規則運算式模式的定義如下表所示。</span><span class="sxs-lookup"><span data-stu-id="7c932-165">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="7c932-166">模式</span><span class="sxs-lookup"><span data-stu-id="7c932-166">Pattern</span></span>|<span data-ttu-id="7c932-167">描述</span><span class="sxs-lookup"><span data-stu-id="7c932-167">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="7c932-168">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="7c932-168">Start at a word boundary.</span></span>|  
|`an?`|<span data-ttu-id="7c932-169">比對 "a" 接著零或一個 "n" 字元。</span><span class="sxs-lookup"><span data-stu-id="7c932-169">Match an "a" followed by zero or one "n" character.</span></span>|  
|`\b`|<span data-ttu-id="7c932-170">在字邊界結束。</span><span class="sxs-lookup"><span data-stu-id="7c932-170">End at a word boundary.</span></span>|  
  
### <a name="match-exactly-n-times-n"></a><span data-ttu-id="7c932-171">確實比對 n 次：{n}</span><span class="sxs-lookup"><span data-stu-id="7c932-171">Match Exactly n Times: {n}</span></span>  
 <span data-ttu-id="7c932-172">`{`  *n*  `}`數量詞比對前面的項目剛好 *n* 次，其中 *n* 是任何整數。</span><span class="sxs-lookup"><span data-stu-id="7c932-172">The `{`*n*`}` quantifier matches the preceding element exactly *n* times, where *n* is any integer.</span></span> <span data-ttu-id="7c932-173">`{`*n*`}`是窮盡數量詞，其延遲的對等項目是`{`  *n*  `}?`。</span><span class="sxs-lookup"><span data-stu-id="7c932-173">`{`*n*`}` is a greedy quantifier whose lazy equivalent is `{`*n*`}?`.</span></span>  
  
 <span data-ttu-id="7c932-174">例如，規則運算式 `\b\d+\,\d{3}\b` 會嘗試比對出字邊界、接著一或多個十進位數字、再接三個十進位數字、接著字邊界的項目。</span><span class="sxs-lookup"><span data-stu-id="7c932-174">For example, the regular expression `\b\d+\,\d{3}\b` tries to match a word boundary followed by one or more decimal digits followed by three decimal digits followed by a word boundary.</span></span> <span data-ttu-id="7c932-175">下例會示範此規則運算式。</span><span class="sxs-lookup"><span data-stu-id="7c932-175">The following example illustrates this regular expression.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#4](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#4)]
 [!code-vb[RegularExpressions.Quantifiers#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#4)]  
  
 <span data-ttu-id="7c932-176">規則運算式模式的定義如下表所示。</span><span class="sxs-lookup"><span data-stu-id="7c932-176">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="7c932-177">模式</span><span class="sxs-lookup"><span data-stu-id="7c932-177">Pattern</span></span>|<span data-ttu-id="7c932-178">描述</span><span class="sxs-lookup"><span data-stu-id="7c932-178">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="7c932-179">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="7c932-179">Start at a word boundary.</span></span>|  
|`\d+`|<span data-ttu-id="7c932-180">比對一個或多個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="7c932-180">Match one or more decimal digits.</span></span>|  
|`\,`|<span data-ttu-id="7c932-181">比對逗號字元。</span><span class="sxs-lookup"><span data-stu-id="7c932-181">Match a comma character.</span></span>|  
|`\d{3}`|<span data-ttu-id="7c932-182">比對三個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="7c932-182">Match three decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="7c932-183">在字邊界結束。</span><span class="sxs-lookup"><span data-stu-id="7c932-183">End at a word boundary.</span></span>|  
  
### <a name="match-at-least-n-times-n"></a><span data-ttu-id="7c932-184">至少比對 n 次：{n,}</span><span class="sxs-lookup"><span data-stu-id="7c932-184">Match at Least n Times: {n,}</span></span>  
 <span data-ttu-id="7c932-185">`{`  *n*  `,}`數量詞比對前面的項目至少 *n* 次，其中 *n* 是任何整數。</span><span class="sxs-lookup"><span data-stu-id="7c932-185">The `{`*n*`,}` quantifier matches the preceding element at least *n* times, where *n* is any integer.</span></span> <span data-ttu-id="7c932-186">`{`*n*`,}`是窮盡數量詞，其延遲的對等項目是`{`  *n*  `}?`。</span><span class="sxs-lookup"><span data-stu-id="7c932-186">`{`*n*`,}` is a greedy quantifier whose lazy equivalent is `{`*n*`}?`.</span></span>  
  
 <span data-ttu-id="7c932-187">例如，規則運算式 `\b\d{2,}\b\D+` 會嘗試比對出字邊界、接著至少兩個數字、再接字邊界、然後非數字字元的項目。</span><span class="sxs-lookup"><span data-stu-id="7c932-187">For example, the regular expression `\b\d{2,}\b\D+` tries to match a word boundary followed by at least two digits followed by a word boundary and a non-digit character.</span></span> <span data-ttu-id="7c932-188">下例會示範此規則運算式。</span><span class="sxs-lookup"><span data-stu-id="7c932-188">The following example illustrates this regular expression.</span></span> <span data-ttu-id="7c932-189">規則運算式無法比對片語`"7 days"`因為它包含只在一個十進位數字，但已成功比對片語`"10 weeks and 300 years"`。</span><span class="sxs-lookup"><span data-stu-id="7c932-189">The regular expression fails to match the phrase `"7 days"` because it contains just one decimal digit, but it successfully matches the phrases `"10 weeks and 300 years"`.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#5)]
 [!code-vb[RegularExpressions.Quantifiers#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#5)]  
  
 <span data-ttu-id="7c932-190">規則運算式模式的定義如下表所示。</span><span class="sxs-lookup"><span data-stu-id="7c932-190">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="7c932-191">模式</span><span class="sxs-lookup"><span data-stu-id="7c932-191">Pattern</span></span>|<span data-ttu-id="7c932-192">描述</span><span class="sxs-lookup"><span data-stu-id="7c932-192">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="7c932-193">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="7c932-193">Start at a word boundary.</span></span>|  
|`\d{2,}`|<span data-ttu-id="7c932-194">至少比對兩個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="7c932-194">Match at least two decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="7c932-195">比對字邊界。</span><span class="sxs-lookup"><span data-stu-id="7c932-195">Match a word boundary.</span></span>|  
|`\D+`|<span data-ttu-id="7c932-196">至少比對一個非十進位數字。</span><span class="sxs-lookup"><span data-stu-id="7c932-196">Match at least one non-decimal digit.</span></span>|  
  
### <a name="match-between-n-and-m-times-nm"></a><span data-ttu-id="7c932-197">比對 n 到 m 次：{n,m}</span><span class="sxs-lookup"><span data-stu-id="7c932-197">Match Between n and m Times: {n,m}</span></span>  
 <span data-ttu-id="7c932-198">`{`  *n*  `,` *m* `}`數量詞比對前面的項目至少 *n* 次數，但不是能超過*m*次，其中 *n* 和*m*都是整數。</span><span class="sxs-lookup"><span data-stu-id="7c932-198">The `{`*n*`,`*m*`}` quantifier matches the preceding element at least *n* times, but no more than *m* times, where *n* and *m* are integers.</span></span> <span data-ttu-id="7c932-199">`{`*n*`,`*m* `}`是窮盡數量詞，其延遲的對等項目是`{`  *n*  `,` *m*`}?`。</span><span class="sxs-lookup"><span data-stu-id="7c932-199">`{`*n*`,`*m*`}` is a greedy quantifier whose lazy equivalent is `{`*n*`,`*m*`}?`.</span></span>  
  
 <span data-ttu-id="7c932-200">在下例中，規則運算式 `(00\s){2,4}` 會嘗試比對 2 至 4 次兩個數字零後接空格的項目。</span><span class="sxs-lookup"><span data-stu-id="7c932-200">In the following example, the regular expression `(00\s){2,4}` tries to match between two and four occurrences of two zero digits followed by a space.</span></span> <span data-ttu-id="7c932-201">請注意，輸入字串有此模式的最後部分出現了五次，而非上限四次。</span><span class="sxs-lookup"><span data-stu-id="7c932-201">Note that the final portion of the input string includes this pattern five times rather than the maximum of four.</span></span> <span data-ttu-id="7c932-202">但只有這個子字串的初始部分 (最多到空格和第五對零) 符合規則運算式模式。</span><span class="sxs-lookup"><span data-stu-id="7c932-202">However, only the initial portion of this substring (up to the space and the fifth pair of zeros) matches the regular expression pattern.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#6)]
 [!code-vb[RegularExpressions.Quantifiers#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#6)]  
  
### <a name="match-zero-or-more-times-lazy-match-"></a><span data-ttu-id="7c932-203">比對零或多次 (Lazy (忽略優先) 比對)：*?</span><span class="sxs-lookup"><span data-stu-id="7c932-203">Match Zero or More Times (Lazy Match): *?</span></span>  
 <span data-ttu-id="7c932-204">`*?`數量詞比對前面的項目零次或多次，但越少次越好。</span><span class="sxs-lookup"><span data-stu-id="7c932-204">The `*?` quantifier matches the preceding element zero or more times, but as few times as possible.</span></span> <span data-ttu-id="7c932-205">它是延遲的窮盡數量詞的對應項目`*`。</span><span class="sxs-lookup"><span data-stu-id="7c932-205">It is the lazy counterpart of the greedy quantifier `*`.</span></span>  
  
 <span data-ttu-id="7c932-206">在下例中，規則運算式 `\b\w*?oo\w*?\b` 會比對包含字串 `oo` 的所有文字。</span><span class="sxs-lookup"><span data-stu-id="7c932-206">In the following example, the regular expression `\b\w*?oo\w*?\b` matches all words that contain the string `oo`.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#7)]
 [!code-vb[RegularExpressions.Quantifiers#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#7)]  
  
 <span data-ttu-id="7c932-207">規則運算式模式的定義如下表所示。</span><span class="sxs-lookup"><span data-stu-id="7c932-207">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="7c932-208">模式</span><span class="sxs-lookup"><span data-stu-id="7c932-208">Pattern</span></span>|<span data-ttu-id="7c932-209">描述</span><span class="sxs-lookup"><span data-stu-id="7c932-209">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="7c932-210">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="7c932-210">Start at a word boundary.</span></span>|  
|`\w*?`|<span data-ttu-id="7c932-211">比對零或多個單字字元，但字元愈少愈好。</span><span class="sxs-lookup"><span data-stu-id="7c932-211">Match zero or more word characters, but as few characters as possible.</span></span>|  
|`oo`|<span data-ttu-id="7c932-212">比對字串 "oo"。</span><span class="sxs-lookup"><span data-stu-id="7c932-212">Match the string "oo".</span></span>|  
|`\w*?`|<span data-ttu-id="7c932-213">比對零或多個單字字元，但字元愈少愈好。</span><span class="sxs-lookup"><span data-stu-id="7c932-213">Match zero or more word characters, but as few characters as possible.</span></span>|  
|`\b`|<span data-ttu-id="7c932-214">在字邊界結束。</span><span class="sxs-lookup"><span data-stu-id="7c932-214">End on a word boundary.</span></span>|  
  
### <a name="match-one-or-more-times-lazy-match-"></a><span data-ttu-id="7c932-215">比對零或多次 (Lazy (忽略優先) 比對)：+?</span><span class="sxs-lookup"><span data-stu-id="7c932-215">Match One or More Times (Lazy Match): +?</span></span>  
 <span data-ttu-id="7c932-216">`+?`數量詞比對前面的項目一或多次，但越少次越好。</span><span class="sxs-lookup"><span data-stu-id="7c932-216">The `+?` quantifier matches the preceding element one or more times, but as few times as possible.</span></span> <span data-ttu-id="7c932-217">它是延遲的窮盡數量詞的對應項目`+`。</span><span class="sxs-lookup"><span data-stu-id="7c932-217">It is the lazy counterpart of the greedy quantifier `+`.</span></span>  
  
 <span data-ttu-id="7c932-218">例如，規則運算式 `\b\w+?\b` 會比對一或多個以字邊界分隔的字元。</span><span class="sxs-lookup"><span data-stu-id="7c932-218">For example, the regular expression `\b\w+?\b` matches one or more characters separated by word boundaries.</span></span> <span data-ttu-id="7c932-219">下例會示範此規則運算式。</span><span class="sxs-lookup"><span data-stu-id="7c932-219">The following example illustrates this regular expression.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#8)]
 [!code-vb[RegularExpressions.Quantifiers#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#8)]  
  
### <a name="match-zero-or-one-time-lazy-match-"></a><span data-ttu-id="7c932-220">比對零或一次 (Lazy (忽略優先) 比對)：??</span><span class="sxs-lookup"><span data-stu-id="7c932-220">Match Zero or One Time (Lazy Match): ??</span></span>  
 <span data-ttu-id="7c932-221">`??`數量詞符合上述的零個或一個項目的時間，但越少次越好。</span><span class="sxs-lookup"><span data-stu-id="7c932-221">The `??` quantifier matches the preceding element zero or one time, but as few times as possible.</span></span> <span data-ttu-id="7c932-222">它是延遲的窮盡數量詞的對應項目`?`。</span><span class="sxs-lookup"><span data-stu-id="7c932-222">It is the lazy counterpart of the greedy quantifier `?`.</span></span>  
  
 <span data-ttu-id="7c932-223">例如，規則運算式 `^\s*(System.)??Console.Write(Line)??\(??` 會嘗試比對字串 "Console.Write" 或 "Console.WriteLine"。</span><span class="sxs-lookup"><span data-stu-id="7c932-223">For example, the regular expression `^\s*(System.)??Console.Write(Line)??\(??` attempts to match the strings "Console.Write" or "Console.WriteLine".</span></span> <span data-ttu-id="7c932-224">字串也可以在 "Console" 前包含 "System."，</span><span class="sxs-lookup"><span data-stu-id="7c932-224">The string can also include "System."</span></span> <span data-ttu-id="7c932-225">後面也可以是左括號。</span><span class="sxs-lookup"><span data-stu-id="7c932-225">before "Console", and it can be followed by an opening parenthesis.</span></span> <span data-ttu-id="7c932-226">字串必須位在行的開頭，雖然前面可以是空格。</span><span class="sxs-lookup"><span data-stu-id="7c932-226">The string must be at the beginning of a line, although it can be preceded by white space.</span></span> <span data-ttu-id="7c932-227">下例會示範此規則運算式。</span><span class="sxs-lookup"><span data-stu-id="7c932-227">The following example illustrates this regular expression.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#9](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#9)]
 [!code-vb[RegularExpressions.Quantifiers#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#9)]  
  
 <span data-ttu-id="7c932-228">規則運算式模式的定義如下表所示。</span><span class="sxs-lookup"><span data-stu-id="7c932-228">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="7c932-229">模式</span><span class="sxs-lookup"><span data-stu-id="7c932-229">Pattern</span></span>|<span data-ttu-id="7c932-230">描述</span><span class="sxs-lookup"><span data-stu-id="7c932-230">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="7c932-231">比對輸入資料流的開頭。</span><span class="sxs-lookup"><span data-stu-id="7c932-231">Match the start of the input stream.</span></span>|  
|`\s*`|<span data-ttu-id="7c932-232">比對零個以上的空白字元。</span><span class="sxs-lookup"><span data-stu-id="7c932-232">Match zero or more white-space characters.</span></span>|  
|`(System.)??`|<span data-ttu-id="7c932-233">比對出現零或一次的字串 "System."。</span><span class="sxs-lookup"><span data-stu-id="7c932-233">Match zero or one occurrence of the string "System.".</span></span>|  
|`Console.Write`|<span data-ttu-id="7c932-234">比對字串 "Console.Write"。</span><span class="sxs-lookup"><span data-stu-id="7c932-234">Match the string "Console.Write".</span></span>|  
|`(Line)??`|<span data-ttu-id="7c932-235">比對出現零或一次的字串 "Line"。</span><span class="sxs-lookup"><span data-stu-id="7c932-235">Match zero or one occurrence of the string "Line".</span></span>|  
|`\(??`|<span data-ttu-id="7c932-236">比對出現零或一次的左括號。</span><span class="sxs-lookup"><span data-stu-id="7c932-236">Match zero or one occurrence of the opening parenthesis.</span></span>|  
  
### <a name="match-exactly-n-times-lazy-match-n"></a><span data-ttu-id="7c932-237">確實比對 n 次 (Lazy (忽略優先) 比對)：{n}?</span><span class="sxs-lookup"><span data-stu-id="7c932-237">Match Exactly n Times (Lazy Match): {n}?</span></span>  
 <span data-ttu-id="7c932-238">`{`  *n*  `}?`數量詞比對前面的項目剛好`n`次，其中 *n* 是任何整數。</span><span class="sxs-lookup"><span data-stu-id="7c932-238">The `{`*n*`}?` quantifier matches the preceding element exactly `n` times, where *n* is any integer.</span></span> <span data-ttu-id="7c932-239">它是延遲的窮盡數量詞的對應項目`{`  *n*  `}+`。</span><span class="sxs-lookup"><span data-stu-id="7c932-239">It is the lazy counterpart of the greedy quantifier `{`*n*`}+`.</span></span>  
  
 <span data-ttu-id="7c932-240">下例會使用規則運算式 `\b(\w{3,}?\.){2}?\w{3,}?\b` 來識別網站位址。</span><span class="sxs-lookup"><span data-stu-id="7c932-240">In the following example, the regular expression `\b(\w{3,}?\.){2}?\w{3,}?\b` is used to identify a Web site address.</span></span> <span data-ttu-id="7c932-241">請注意它會比對 "www.microsoft.com" 和 "msdn.microsoft.com"，但不比對 "mywebsite" 或 "mycompany.com"。</span><span class="sxs-lookup"><span data-stu-id="7c932-241">Note that it matches "www.microsoft.com" and "msdn.microsoft.com", but does not match "mywebsite" or "mycompany.com".</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#10](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#10)]
 [!code-vb[RegularExpressions.Quantifiers#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#10)]  
  
 <span data-ttu-id="7c932-242">規則運算式模式的定義如下表所示。</span><span class="sxs-lookup"><span data-stu-id="7c932-242">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="7c932-243">模式</span><span class="sxs-lookup"><span data-stu-id="7c932-243">Pattern</span></span>|<span data-ttu-id="7c932-244">描述</span><span class="sxs-lookup"><span data-stu-id="7c932-244">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="7c932-245">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="7c932-245">Start at a word boundary.</span></span>|  
|`(\w{3,}?\.)`|<span data-ttu-id="7c932-246">比對至少 3 個單字字元，但字元愈少愈好，後面接著點或句號字元。</span><span class="sxs-lookup"><span data-stu-id="7c932-246">Match at least 3 word characters, but as few characters as possible, followed by a dot or period character.</span></span> <span data-ttu-id="7c932-247">這是第一個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="7c932-247">This is the first capturing group.</span></span>|  
|`(\w{3,}?\.){2}?`|<span data-ttu-id="7c932-248">比對兩次第一個群組中的模式，但次數愈少愈好。</span><span class="sxs-lookup"><span data-stu-id="7c932-248">Match the pattern in the first group two times, but as few times as possible.</span></span>|  
|`\b`|<span data-ttu-id="7c932-249">結束字邊界比對。</span><span class="sxs-lookup"><span data-stu-id="7c932-249">End the match on a word boundary.</span></span>|  
  
### <a name="match-at-least-n-times-lazy-match-n"></a><span data-ttu-id="7c932-250">至少比對 n 次 (Lazy (忽略優先) 比對)：{n,}?</span><span class="sxs-lookup"><span data-stu-id="7c932-250">Match at Least n Times (Lazy Match): {n,}?</span></span>  
 <span data-ttu-id="7c932-251">`{`  *n*  `,}?`數量詞比對前面的項目至少`n`次，其中 *n* 是任何整數，但越少次越可能的。</span><span class="sxs-lookup"><span data-stu-id="7c932-251">The `{`*n*`,}?` quantifier matches the preceding element at least `n` times, where *n* is any integer, but as few times as possible.</span></span> <span data-ttu-id="7c932-252">它是延遲的窮盡數量詞的對應項目`{`  *n*  `,}`。</span><span class="sxs-lookup"><span data-stu-id="7c932-252">It is the lazy counterpart of the greedy quantifier `{`*n*`,}`.</span></span>  
  
 <span data-ttu-id="7c932-253">請參閱範例的`{`  *n*  `}?`數量詞，如需圖例上一節。</span><span class="sxs-lookup"><span data-stu-id="7c932-253">See the example for the `{`*n*`}?` quantifier in the previous section for an illustration.</span></span> <span data-ttu-id="7c932-254">在此範例中的規則運算式會使用`{`  *n*  `,}`數量詞比對後面接句號的至少三個字元的字串。</span><span class="sxs-lookup"><span data-stu-id="7c932-254">The regular expression in that example uses the `{`*n*`,}` quantifier to match a string that has at least three characters followed by a period.</span></span>  
  
### <a name="match-between-n-and-m-times-lazy-match-nm"></a><span data-ttu-id="7c932-255">比對 n 到 m 次 (Lazy (忽略優先) 比對)：{n,m}?</span><span class="sxs-lookup"><span data-stu-id="7c932-255">Match Between n and m Times (Lazy Match): {n,m}?</span></span>  
 <span data-ttu-id="7c932-256">`{`  *n*  `,` *m* `}?`數量詞比對前面的項目之間`n`和`m`次，其中*n* 和*m*都是整數，但越少次越好。</span><span class="sxs-lookup"><span data-stu-id="7c932-256">The `{`*n*`,`*m*`}?` quantifier matches the preceding element between `n` and `m` times, where *n* and *m* are integers, but as few times as possible.</span></span> <span data-ttu-id="7c932-257">它是延遲的窮盡數量詞的對應項目`{`  *n*  `,` *m*`}`。</span><span class="sxs-lookup"><span data-stu-id="7c932-257">It is the lazy counterpart of the greedy quantifier `{`*n*`,`*m*`}`.</span></span>  
  
 <span data-ttu-id="7c932-258">在下例中，規則運算式 `\b[A-Z](\w*\s+){1,10}?[.!?]` 會比對包含一到十個單字的句子。</span><span class="sxs-lookup"><span data-stu-id="7c932-258">In the following example, the regular expression `\b[A-Z](\w*\s+){1,10}?[.!?]` matches sentences that contain between one and ten words.</span></span> <span data-ttu-id="7c932-259">它會比對輸入字串中的所有句子，除了包含 18 個字的句子。</span><span class="sxs-lookup"><span data-stu-id="7c932-259">It matches all the sentences in the input string except for one sentence that contains 18 words.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#12](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#12)]
 [!code-vb[RegularExpressions.Quantifiers#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#12)]  
  
 <span data-ttu-id="7c932-260">規則運算式模式的定義如下表所示。</span><span class="sxs-lookup"><span data-stu-id="7c932-260">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="7c932-261">模式</span><span class="sxs-lookup"><span data-stu-id="7c932-261">Pattern</span></span>|<span data-ttu-id="7c932-262">描述</span><span class="sxs-lookup"><span data-stu-id="7c932-262">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="7c932-263">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="7c932-263">Start at a word boundary.</span></span>|  
|`[A-Z]`|<span data-ttu-id="7c932-264">比對從 A 到 Z 的大寫字元。</span><span class="sxs-lookup"><span data-stu-id="7c932-264">Match an uppercase character from A to Z.</span></span>|  
|`(\w*\s+)`|<span data-ttu-id="7c932-265">比對零或多個後接一或多個空白字元的單字字元。</span><span class="sxs-lookup"><span data-stu-id="7c932-265">Match zero or more word characters, followed by one or more white-space characters.</span></span> <span data-ttu-id="7c932-266">這是第一個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="7c932-266">This is the first capture group.</span></span>|  
|`{1,10}?`|<span data-ttu-id="7c932-267">比對 1 到 10 次上一個模式，但次數愈少愈好。</span><span class="sxs-lookup"><span data-stu-id="7c932-267">Match the previous pattern between 1 and 10 times, but as few times as possible.</span></span>|  
|`[.!?]`|<span data-ttu-id="7c932-268">比對任一標點符號字元 "."、"!" 或 "?"。</span><span class="sxs-lookup"><span data-stu-id="7c932-268">Match any one of the punctuation characters ".", "!", or "?".</span></span>|  
  
<a name="Greedy"></a>   
## <a name="greedy-and-lazy-quantifiers"></a><span data-ttu-id="7c932-269">Greedy (匹配優先) 與 Lazy (忽略優先) 量詞</span><span class="sxs-lookup"><span data-stu-id="7c932-269">Greedy and Lazy Quantifiers</span></span>  
 <span data-ttu-id="7c932-270">數個量詞有兩種版本︰</span><span class="sxs-lookup"><span data-stu-id="7c932-270">A number of the quantifiers have two versions:</span></span>  
  
-   <span data-ttu-id="7c932-271">Greedy (窮盡) 版本。</span><span class="sxs-lookup"><span data-stu-id="7c932-271">A greedy version.</span></span>  
  
     <span data-ttu-id="7c932-272">Greedy (窮盡) 數量詞會嘗試盡可能多次比對項目。</span><span class="sxs-lookup"><span data-stu-id="7c932-272">A greedy quantifier tries to match an element as many times as possible.</span></span>  
  
-   <span data-ttu-id="7c932-273">非窮盡 （或延遲） 的版本。</span><span class="sxs-lookup"><span data-stu-id="7c932-273">A non-greedy (or lazy) version.</span></span>  
  
     <span data-ttu-id="7c932-274">非 Greedy (窮盡) 數量詞會嘗試盡可能少比對項目。</span><span class="sxs-lookup"><span data-stu-id="7c932-274">A non-greedy quantifier tries to match an element as few times as possible.</span></span> <span data-ttu-id="7c932-275">您可以將窮盡數量詞 lazy 數量詞變成只要新增`?`。</span><span class="sxs-lookup"><span data-stu-id="7c932-275">You can turn a greedy quantifier into a lazy quantifier by simply adding a `?`.</span></span>  
  
 <span data-ttu-id="7c932-276">請考慮要擷取數字字串末四碼的簡單規則運算式，例如信用卡號碼。</span><span class="sxs-lookup"><span data-stu-id="7c932-276">Consider a simple regular expression that is intended to extract the last four digits from a string of numbers such as a credit card number.</span></span> <span data-ttu-id="7c932-277">使用規則運算式的新版`*`窮盡數量詞為`\b.*([0-9]{4})\b`。</span><span class="sxs-lookup"><span data-stu-id="7c932-277">The version of the regular expression that uses the `*` greedy quantifier is `\b.*([0-9]{4})\b`.</span></span> <span data-ttu-id="7c932-278">但若字串包含兩組數字，這個規則運算式只會比對第二組數字的末四碼，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="7c932-278">However, if a string contains two numbers, this regular expression matches the last four digits of the second number only, as the following example shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#1)]  
  
 <span data-ttu-id="7c932-279">規則運算式無法比對的第一個號碼，因為`*`數量詞嘗試比對上一個項目，盡可能在整個字串的次數，因此找到其比對字串的結尾。</span><span class="sxs-lookup"><span data-stu-id="7c932-279">The regular expression fails to match the first number because the `*` quantifier tries to match the previous element as many times as possible in the entire string, and so it finds its match at the end of the string.</span></span>  
  
 <span data-ttu-id="7c932-280">這不是我們所要的結果。</span><span class="sxs-lookup"><span data-stu-id="7c932-280">This is not the desired behavior.</span></span> <span data-ttu-id="7c932-281">相反地，您可以使用`*?`lazy 數量詞擷取這兩個編號，如下列範例所示的數字。</span><span class="sxs-lookup"><span data-stu-id="7c932-281">Instead, you can use the `*?`lazy quantifier to extract digits from both numbers, as the following example shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#2)]  
  
 <span data-ttu-id="7c932-282">在大部分情況下，有 Greedy (窮盡) 和 Lazy (最少) 數量詞的規則運算式會傳回相同的結果。</span><span class="sxs-lookup"><span data-stu-id="7c932-282">In most cases, regular expressions with greedy and lazy quantifiers return the same matches.</span></span> <span data-ttu-id="7c932-283">它們最常傳回不同的結果時搭配萬用字元 (`.`) 中繼字元，它會比對任何字元。</span><span class="sxs-lookup"><span data-stu-id="7c932-283">They most commonly return different results when they are used with the wildcard (`.`) metacharacter, which matches any character.</span></span>  
  
## <a name="quantifiers-and-empty-matches"></a><span data-ttu-id="7c932-284">量詞和空白比對</span><span class="sxs-lookup"><span data-stu-id="7c932-284">Quantifiers and Empty Matches</span></span>  
 <span data-ttu-id="7c932-285">數量詞`*`， `+`，和`{`  *n*  `,` *m* `}`和空後永遠不會重複其延遲的對應項目比對時已找到擷取的最小數目。</span><span class="sxs-lookup"><span data-stu-id="7c932-285">The quantifiers `*`, `+`, and `{`*n*`,`*m*`}` and their lazy counterparts never repeat after an empty match when the minimum number of captures has been found.</span></span> <span data-ttu-id="7c932-286">當可能群組擷取的最大數目是無限或接近無限時，此規則可防止數量詞在碰到空白子運算式比對時進入無限迴圈。</span><span class="sxs-lookup"><span data-stu-id="7c932-286">This rule prevents quantifiers from entering infinite loops on empty subexpression matches when the maximum number of possible group captures is infinite or near infinite.</span></span>  
  
 <span data-ttu-id="7c932-287">例如，下列程式碼顯示要呼叫的結果<xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType>方法與規則運算式模式`(a?)*`，會比對零個或一個"a"字元零次以上。</span><span class="sxs-lookup"><span data-stu-id="7c932-287">For example, the following code shows the result of a call to the <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> method with the regular expression pattern `(a?)*`, which matches zero or one "a" character zero or more times.</span></span> <span data-ttu-id="7c932-288">請注意，單一擷取群組會擷取每個"a"做為以及<xref:System.String.Empty?displayProperty=nameWithType>，但沒有第二個空白相符，因為第一個空白的相符項目會造成停止重複限定詞。</span><span class="sxs-lookup"><span data-stu-id="7c932-288">Note that the single capturing group captures each "a" as well as <xref:System.String.Empty?displayProperty=nameWithType>, but that there is no second empty match, because the first empty match causes the quantifier to stop repeating.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch1.vb#1)]  
  
 <span data-ttu-id="7c932-289">若要查看定義擷取數目上下限的擷取群組和定義固定擷取數目的擷取群組之間的實際差異，請考慮規則運算式模式 `(a\1|(?(1)\1)){0,2}` 和 `(a\1|(?(1)\1)){2}`。</span><span class="sxs-lookup"><span data-stu-id="7c932-289">To see the practical difference between a capturing group that defines a minimum and a maximum number of captures and one that defines a fixed number of captures, consider the regular expression patterns `(a\1|(?(1)\1)){0,2}` and `(a\1|(?(1)\1)){2}`.</span></span> <span data-ttu-id="7c932-290">這兩個規則運算式都是由單一擷取群組組成，如下表所示加以定義。</span><span class="sxs-lookup"><span data-stu-id="7c932-290">Both regular expressions consist of a single capturing group, which is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="7c932-291">模式</span><span class="sxs-lookup"><span data-stu-id="7c932-291">Pattern</span></span>|<span data-ttu-id="7c932-292">描述</span><span class="sxs-lookup"><span data-stu-id="7c932-292">Description</span></span>|  
|-------------|-----------------|  
|`(a\1`|<span data-ttu-id="7c932-293">比對 "a" 及第一個擷取的群組值...</span><span class="sxs-lookup"><span data-stu-id="7c932-293">Either match "a" along with the value of the first captured group …</span></span>|  
|`&#124;(?(1)`|<span data-ttu-id="7c932-294">…</span><span class="sxs-lookup"><span data-stu-id="7c932-294">…</span></span> <span data-ttu-id="7c932-295">或測試第一個擷取的群組是否已定義。</span><span class="sxs-lookup"><span data-stu-id="7c932-295">or test whether the first captured group has been defined.</span></span> <span data-ttu-id="7c932-296">(請注意，`(?(1)`建構不會定義的擷取群組。)</span><span class="sxs-lookup"><span data-stu-id="7c932-296">(Note that the `(?(1)` construct does not define a capturing group.)</span></span>|  
|`\1))`|<span data-ttu-id="7c932-297">如果第一個擷取的群組存在，即比對其值。</span><span class="sxs-lookup"><span data-stu-id="7c932-297">If the first captured group exists, match its value.</span></span> <span data-ttu-id="7c932-298">如果群組不存在，將符合的群組<xref:System.String.Empty?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="7c932-298">If the group does not exist, the group will match <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|  
  
 <span data-ttu-id="7c932-299">第一個規則運算式嘗試比對這種模式零到兩次，第二個不多不少就兩次。</span><span class="sxs-lookup"><span data-stu-id="7c932-299">The first regular expression tries to match this pattern between zero and two times; the second, exactly two times.</span></span> <span data-ttu-id="7c932-300">因為第一個模式達到其最小數目的其第一個擷取的擷取<xref:System.String.Empty?displayProperty=nameWithType>，永遠不會重複嘗試比對`a\1`;`{0,2}`數量詞允許空的相符項目中的最後一個反覆項目。</span><span class="sxs-lookup"><span data-stu-id="7c932-300">Because the first pattern reaches its minimum number of captures with its first capture of <xref:System.String.Empty?displayProperty=nameWithType>, it never repeats to try to match `a\1`; the `{0,2}` quantifier allows only empty matches in the last iteration.</span></span> <span data-ttu-id="7c932-301">相反地，第二個規則運算式不比對 "a"，因為它會評估 `a\1` 第二次，反覆的下限 2，會強制引擎在空白比對後重複。</span><span class="sxs-lookup"><span data-stu-id="7c932-301">In contrast, the second regular expression does match "a" because it evaluates `a\1` a second time; the minimum number of iterations, 2, forces the engine to repeat after an empty match.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch4.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch4.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="7c932-302">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c932-302">See Also</span></span>  
 [<span data-ttu-id="7c932-303">規則運算式語言 - 快速參考</span><span class="sxs-lookup"><span data-stu-id="7c932-303">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 [<span data-ttu-id="7c932-304">回溯</span><span class="sxs-lookup"><span data-stu-id="7c932-304">Backtracking</span></span>](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)
