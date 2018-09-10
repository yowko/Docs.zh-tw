---
title: 規則運算式中的其他建構
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- constructs, miscellaneous
- .NET Framework regular expressions, miscellaneous constructs
- regular expressions, miscellaneous constructs
ms.assetid: 7d10d11f-680f-4721-b047-fb136316b4cd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8956726915ebe1c0b1c7654e62e2e28620274b4a
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44251650"
---
# <a name="miscellaneous-constructs-in-regular-expressions"></a><span data-ttu-id="10b38-102">規則運算式中的其他建構</span><span class="sxs-lookup"><span data-stu-id="10b38-102">Miscellaneous Constructs in Regular Expressions</span></span>
<span data-ttu-id="10b38-103">.NET 中的規則運算式包含三個其他語言建構。</span><span class="sxs-lookup"><span data-stu-id="10b38-103">Regular expressions in .NET include three miscellaneous language constructs.</span></span> <span data-ttu-id="10b38-104">其中一個可讓您在規則運算式模式的中間，啟用或停用特定比對選項。</span><span class="sxs-lookup"><span data-stu-id="10b38-104">One lets you enable or disable particular matching options in the middle of a regular expression pattern.</span></span> <span data-ttu-id="10b38-105">其餘兩個可讓您在規則運算式中包含註解。</span><span class="sxs-lookup"><span data-stu-id="10b38-105">The remaining two let you include comments in a regular expression.</span></span>  
  
## <a name="inline-options"></a><span data-ttu-id="10b38-106">內嵌選項</span><span class="sxs-lookup"><span data-stu-id="10b38-106">Inline Options</span></span>  
 <span data-ttu-id="10b38-107">您可以使用下列語法，設定或停用部分規則運算式的特定模式比對選項</span><span class="sxs-lookup"><span data-stu-id="10b38-107">You can set or disable specific pattern matching options for part of a regular expression by using the syntax</span></span>  
  
```  
(?imnsx-imnsx)  
```  
  
 <span data-ttu-id="10b38-108">您在問號之後列出要啟用的選項，並在減號之後列出要停用的選項。</span><span class="sxs-lookup"><span data-stu-id="10b38-108">You list the options you want to enable after the question mark, and the options you want to disable after the minus sign.</span></span> <span data-ttu-id="10b38-109">下表會說明每個選項。</span><span class="sxs-lookup"><span data-stu-id="10b38-109">The following table describes each option.</span></span> <span data-ttu-id="10b38-110">如需每個選項的詳細資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)。</span><span class="sxs-lookup"><span data-stu-id="10b38-110">For more information about each option, see [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
|<span data-ttu-id="10b38-111">選項</span><span class="sxs-lookup"><span data-stu-id="10b38-111">Option</span></span>|<span data-ttu-id="10b38-112">描述</span><span class="sxs-lookup"><span data-stu-id="10b38-112">Description</span></span>|  
|------------|-----------------|  
|`i`|<span data-ttu-id="10b38-113">不區分大小寫的比對。</span><span class="sxs-lookup"><span data-stu-id="10b38-113">Case-insensitive matching.</span></span>|  
|`m`|<span data-ttu-id="10b38-114">多行模式。</span><span class="sxs-lookup"><span data-stu-id="10b38-114">Multiline mode.</span></span>|  
|`n`|<span data-ttu-id="10b38-115">僅明確擷取</span><span class="sxs-lookup"><span data-stu-id="10b38-115">Explicit captures only.</span></span> <span data-ttu-id="10b38-116">(括號不可作為擷取群組)。</span><span class="sxs-lookup"><span data-stu-id="10b38-116">(Parentheses do not act as capturing groups.)</span></span>|  
|`s`|<span data-ttu-id="10b38-117">單行模式。</span><span class="sxs-lookup"><span data-stu-id="10b38-117">Single-line mode.</span></span>|  
|`x`|<span data-ttu-id="10b38-118">忽略未逸出的空白字元，並允許 x 模式註解。</span><span class="sxs-lookup"><span data-stu-id="10b38-118">Ignore unescaped white space, and allow x-mode comments.</span></span>|  
  
 <span data-ttu-id="10b38-119">`(?imnsx-imnsx)` 建構所定義之規則運算式選項中的任何變更，其效果會一直維持到封入群組的結尾。</span><span class="sxs-lookup"><span data-stu-id="10b38-119">Any change in regular expression options defined by the `(?imnsx-imnsx)` construct remains in effect until the end of the enclosing group.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10b38-120">`(?imnsx-imnsx:`*subexpression*`)` 群組建構會為子運算式提供完全相同的功能。</span><span class="sxs-lookup"><span data-stu-id="10b38-120">The `(?imnsx-imnsx:`*subexpression*`)` grouping construct provides identical functionality for a subexpression.</span></span> <span data-ttu-id="10b38-121">如需詳細資訊，請參閱[群組建構](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="10b38-121">For more information, see [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="10b38-122">下列範例會使用 `i`、`n` 及 `x` 選項來啟用不區分大小寫和明確擷取，並忽略規則運算式中間規則運算式模式中的空白字元。</span><span class="sxs-lookup"><span data-stu-id="10b38-122">The following example uses the `i`, `n`, and `x` options to enable case insensitivity and explicit captures, and to ignore white space in the regular expression pattern in the middle of a regular expression.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous1.cs#1)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous1.vb#1)]  
  
 <span data-ttu-id="10b38-123">此範例會定義兩個規則運算式。</span><span class="sxs-lookup"><span data-stu-id="10b38-123">The example defines two regular expressions.</span></span> <span data-ttu-id="10b38-124">第一個規則運算式 `\b(D\w+)\s(d\w+)\b` 會比對開頭為大寫 "D" 和小寫 "d" 的兩個連續字組。</span><span class="sxs-lookup"><span data-stu-id="10b38-124">The first, `\b(D\w+)\s(d\w+)\b`, matches two consecutive words that begin with an uppercase "D" and a lowercase "d".</span></span> <span data-ttu-id="10b38-125">第二個規則運算式 `\b(D\w+)(?ixn) \s (d\w+) \b` 會使用內嵌選項來修改此模式，如下表所述。</span><span class="sxs-lookup"><span data-stu-id="10b38-125">The second regular expression, `\b(D\w+)(?ixn) \s (d\w+) \b`, uses inline options to modify this pattern, as described in the following table.</span></span> <span data-ttu-id="10b38-126">然後比較結果，以確認 `(?ixn)` 建構的效果。</span><span class="sxs-lookup"><span data-stu-id="10b38-126">A comparison of the results confirms the effect of the `(?ixn)` construct.</span></span>  
  
|<span data-ttu-id="10b38-127">模式</span><span class="sxs-lookup"><span data-stu-id="10b38-127">Pattern</span></span>|<span data-ttu-id="10b38-128">描述</span><span class="sxs-lookup"><span data-stu-id="10b38-128">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="10b38-129">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="10b38-129">Start at a word boundary.</span></span>|  
|`(D\w+)`|<span data-ttu-id="10b38-130">比對後面接著一個或多個文字字元的大寫 "D"。</span><span class="sxs-lookup"><span data-stu-id="10b38-130">Match a capital "D" followed by one or more word characters.</span></span> <span data-ttu-id="10b38-131">這是第一個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="10b38-131">This is the first capture group.</span></span>|  
|`(?ixn)`|<span data-ttu-id="10b38-132">從這裡開始，進行不區分大小寫的比較、只進行明確擷取，並忽略規則運算式模式中的空白字元。</span><span class="sxs-lookup"><span data-stu-id="10b38-132">From this point on, make comparisons case-insensitive, make only explicit captures, and ignore white space in the regular expression pattern.</span></span>|  
|`\s`|<span data-ttu-id="10b38-133">比對空白字元。</span><span class="sxs-lookup"><span data-stu-id="10b38-133">Match a white-space character.</span></span>|  
|`(d\w+)`|<span data-ttu-id="10b38-134">比對後面接著一個或多個文字字元的大寫或小寫 "d"。</span><span class="sxs-lookup"><span data-stu-id="10b38-134">Match an uppercase or lowercase "d" followed by one or more word characters.</span></span> <span data-ttu-id="10b38-135">因為已啟用 `n` (明確擷取) 選項，所以不會擷取此群組。</span><span class="sxs-lookup"><span data-stu-id="10b38-135">This group is not captured because the `n` (explicit capture) option was enabled..</span></span>|  
|`\b`|<span data-ttu-id="10b38-136">比對字邊界。</span><span class="sxs-lookup"><span data-stu-id="10b38-136">Match a word boundary.</span></span>|  
  
## <a name="inline-comment"></a><span data-ttu-id="10b38-137">內嵌註解</span><span class="sxs-lookup"><span data-stu-id="10b38-137">Inline Comment</span></span>  
 <span data-ttu-id="10b38-138">`(?#` *comment*`)` 建構可讓您在規則運算式中包含內嵌註解。</span><span class="sxs-lookup"><span data-stu-id="10b38-138">The `(?#` *comment*`)` construct lets you include an inline comment in a regular expression.</span></span> <span data-ttu-id="10b38-139">規則運算式引擎不會在模式比對中使用註解的任一部分，不過，會將註解包含在 <xref:System.Text.RegularExpressions.Regex.ToString%2A?displayProperty=nameWithType> 方法所傳回的字串中。</span><span class="sxs-lookup"><span data-stu-id="10b38-139">The regular expression engine does not use any part of the comment in pattern matching, although the comment is included in the string that is returned by the <xref:System.Text.RegularExpressions.Regex.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="10b38-140">註解會在第一個右括號結束。</span><span class="sxs-lookup"><span data-stu-id="10b38-140">The comment ends at the first closing parenthesis.</span></span>  
  
 <span data-ttu-id="10b38-141">下列範例會重複上一節範例中的第一個規則運算式模式。</span><span class="sxs-lookup"><span data-stu-id="10b38-141">The following example repeats the first regular expression pattern from the example in the previous section.</span></span> <span data-ttu-id="10b38-142">它會將兩個內嵌註解加入規則運算式，以指出比較是否區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="10b38-142">It adds two inline comments to the regular expression to indicate whether the comparison is case-sensitive.</span></span> <span data-ttu-id="10b38-143">規則運算式模式 `\b((?# case-sensitive comparison)D\w+)\s(?ixn)((?#case-insensitive comparison)d\w+)\b` 定義如下。</span><span class="sxs-lookup"><span data-stu-id="10b38-143">The regular expression pattern, `\b((?# case-sensitive comparison)D\w+)\s(?ixn)((?#case-insensitive comparison)d\w+)\b`, is defined as follows.</span></span>  
  
|<span data-ttu-id="10b38-144">模式</span><span class="sxs-lookup"><span data-stu-id="10b38-144">Pattern</span></span>|<span data-ttu-id="10b38-145">描述</span><span class="sxs-lookup"><span data-stu-id="10b38-145">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="10b38-146">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="10b38-146">Start at a word boundary.</span></span>|  
|`(?# case-sensitive comparison)`|<span data-ttu-id="10b38-147">註解。</span><span class="sxs-lookup"><span data-stu-id="10b38-147">A comment.</span></span> <span data-ttu-id="10b38-148">它不會影響模式比對行為。</span><span class="sxs-lookup"><span data-stu-id="10b38-148">It does not affect pattern-matching behavior.</span></span>|  
|`(D\w+)`|<span data-ttu-id="10b38-149">比對後面接著一個或多個文字字元的大寫 "D"。</span><span class="sxs-lookup"><span data-stu-id="10b38-149">Match a capital "D" followed by one or more word characters.</span></span> <span data-ttu-id="10b38-150">這是第一個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="10b38-150">This is the first capturing group.</span></span>|  
|`\s`|<span data-ttu-id="10b38-151">比對空白字元。</span><span class="sxs-lookup"><span data-stu-id="10b38-151">Match a white-space character.</span></span>|  
|`(?ixn)`|<span data-ttu-id="10b38-152">從這裡開始，進行不區分大小寫的比較、只進行明確擷取，並忽略規則運算式模式中的空白字元。</span><span class="sxs-lookup"><span data-stu-id="10b38-152">From this point on, make comparisons case-insensitive, make only explicit captures, and ignore white space in the regular expression pattern.</span></span>|  
|`(?#case-insensitive comparison)`|<span data-ttu-id="10b38-153">註解。</span><span class="sxs-lookup"><span data-stu-id="10b38-153">A comment.</span></span> <span data-ttu-id="10b38-154">它不會影響模式比對行為。</span><span class="sxs-lookup"><span data-stu-id="10b38-154">It does not affect pattern-matching behavior.</span></span>|  
|`(d\w+)`|<span data-ttu-id="10b38-155">比對後面接著一個或多個文字字元的大寫或小寫 "d"。</span><span class="sxs-lookup"><span data-stu-id="10b38-155">Match an uppercase or lowercase "d" followed by one or more word characters.</span></span> <span data-ttu-id="10b38-156">這是第二個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="10b38-156">This is the second capture group.</span></span>|  
|`\b`|<span data-ttu-id="10b38-157">比對字邊界。</span><span class="sxs-lookup"><span data-stu-id="10b38-157">Match a word boundary.</span></span>|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous2.cs#2)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous2.vb#2)]  
  
## <a name="end-of-line-comment"></a><span data-ttu-id="10b38-158">行結尾註解</span><span class="sxs-lookup"><span data-stu-id="10b38-158">End-of-Line Comment</span></span>  
 <span data-ttu-id="10b38-159">數字符號 (`#`) 會標記 x 模式註解，從規則運算式模式結尾中未逸出的 # 字元開始，並持續到該行結尾。</span><span class="sxs-lookup"><span data-stu-id="10b38-159">A number sign (`#`)marks an x-mode comment, which starts at the unescaped # character at the end of the regular expression pattern and continues until the end of the line.</span></span> <span data-ttu-id="10b38-160">若要使用此建構，您必須在將 <xref:System.Text.RegularExpressions.Regex> 物件具現化或呼叫靜態 <xref:System.Text.RegularExpressions.Regex> 方法時，啟用 `x` 選項 (透過內嵌選項)，或將 <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> 值提供給 `option` 參數。</span><span class="sxs-lookup"><span data-stu-id="10b38-160">To use this construct, you must either enable the `x` option (through inline options) or supply the <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> value to the `option` parameter when instantiating the <xref:System.Text.RegularExpressions.Regex> object or calling a static <xref:System.Text.RegularExpressions.Regex> method.</span></span>  
  
 <span data-ttu-id="10b38-161">下列範例說明行結尾註解建構。</span><span class="sxs-lookup"><span data-stu-id="10b38-161">The following example illustrates the end-of-line comment construct.</span></span> <span data-ttu-id="10b38-162">它會判斷字串是否為至少包含一個格式項目的複合格式字串。</span><span class="sxs-lookup"><span data-stu-id="10b38-162">It determines whether a string is a composite format string that includes at least one format item.</span></span> <span data-ttu-id="10b38-163">下表說明規則運算式模式中的建構：</span><span class="sxs-lookup"><span data-stu-id="10b38-163">The following table describes the constructs in the regular expression pattern:</span></span>  
  
 `\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item.`  
  
|<span data-ttu-id="10b38-164">模式</span><span class="sxs-lookup"><span data-stu-id="10b38-164">Pattern</span></span>|<span data-ttu-id="10b38-165">描述</span><span class="sxs-lookup"><span data-stu-id="10b38-165">Description</span></span>|  
|-------------|-----------------|  
|`\{`|<span data-ttu-id="10b38-166">比對左括號。</span><span class="sxs-lookup"><span data-stu-id="10b38-166">Match an opening brace.</span></span>|  
|`\d+`|<span data-ttu-id="10b38-167">比對一個或多個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="10b38-167">Match one or more decimal digits.</span></span>|  
|`(,-*\d+)*`|<span data-ttu-id="10b38-168">比對零個或一個出現的逗號，後面接著一個選擇性減號，再接著一個或多個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="10b38-168">Match zero or one occurrence of a comma, followed by an optional minus sign, followed by one or more decimal digits.</span></span>|  
|`(\:\w{1,4}?)*`|<span data-ttu-id="10b38-169">比對零個或一個出現的冒號，後面接著一到四個 (但越少越好) 空白字元。</span><span class="sxs-lookup"><span data-stu-id="10b38-169">Match zero or one occurrence of a colon, followed by one to four, but as few as possible, white-space characters.</span></span>|  
|`\}`|<span data-ttu-id="10b38-170">比對右括號。</span><span class="sxs-lookup"><span data-stu-id="10b38-170">Match a closing brace.</span></span>|  
|`(?x)`|<span data-ttu-id="10b38-171">啟用忽略模式空白字元選項，以辨識行結尾註解。</span><span class="sxs-lookup"><span data-stu-id="10b38-171">Enable the ignore pattern white-space option so that the end-of-line comment will be recognized.</span></span>|  
|`# Looks for a composite format item.`|<span data-ttu-id="10b38-172">行結尾註解。</span><span class="sxs-lookup"><span data-stu-id="10b38-172">An end-of-line comment.</span></span>|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous3.cs#3)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous3.vb#3)]  
  
 <span data-ttu-id="10b38-173">請注意，除了在規則運算式中提供 `(?x)` 建構，也可以藉由呼叫 <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> 方法，並將 <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> 列舉值傳遞給此方法，來辨識註解。</span><span class="sxs-lookup"><span data-stu-id="10b38-173">Note that, instead of providing the `(?x)` construct in the regular expression, the comment could also have been recognized by calling the <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> method and passing it the <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> enumeration value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10b38-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10b38-174">See also</span></span>

- [<span data-ttu-id="10b38-175">規則運算式語言 - 快速參考</span><span class="sxs-lookup"><span data-stu-id="10b38-175">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
