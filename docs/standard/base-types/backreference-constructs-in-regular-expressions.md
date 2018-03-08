---
title: "規則運算式中的反向參考建構"
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
- backreferences
- constructs, backreference
- .NET Framework regular expressions, backreference constructs
- regular expressions, backreference constructs
ms.assetid: 567a4b8d-0e79-49dc-8df9-f4b1aa376a2a
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2ec92933bdf123412a3d489fc493d76c4a0dc0d0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="backreference-constructs-in-regular-expressions"></a><span data-ttu-id="82848-102">規則運算式中的反向參考建構</span><span class="sxs-lookup"><span data-stu-id="82848-102">Backreference Constructs in Regular Expressions</span></span>
<span data-ttu-id="82848-103">反向參考提供便利的方式來識別字串內的重複字元或子字串。</span><span class="sxs-lookup"><span data-stu-id="82848-103">Backreferences provide a convenient way to identify a repeated character or substring within a string.</span></span> <span data-ttu-id="82848-104">例如，如果輸入字串包含多次出現的任意子字串，您可以比對第一個出現的子字串與擷取的群組，接著使用反向參考來比對隨後出現的子字串。</span><span class="sxs-lookup"><span data-stu-id="82848-104">For example, if the input string contains multiple occurrences of an arbitrary substring, you can match the first occurrence with a capturing group, and then use a backreference to match subsequent occurrences of the substring.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82848-105">對於取代字串中的具名和編號擷取群組，會使用不同的語法來參考。</span><span class="sxs-lookup"><span data-stu-id="82848-105">A separate syntax is used to refer to named and numbered capturing groups in replacement strings.</span></span> <span data-ttu-id="82848-106">如需詳細資訊，請參閱 [Substitutions](substitutions-in-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="82848-106">For more information, see [Substitutions](substitutions-in-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="82848-107">.NET 會定義個別的語言項目，以參考編號和具名擷取群組。</span><span class="sxs-lookup"><span data-stu-id="82848-107">.NET defines separate language elements to refer to numbered and named capturing groups.</span></span> <span data-ttu-id="82848-108">如需擷取群組的詳細資訊，請參閱[群組建構](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="82848-108">For more information about capturing groups, see [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).</span></span>  
  
## <a name="numbered-backreferences"></a><span data-ttu-id="82848-109">編號反向參考</span><span class="sxs-lookup"><span data-stu-id="82848-109">Numbered Backreferences</span></span>  
 <span data-ttu-id="82848-110">編號反向參考會使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="82848-110">A numbered backreference uses the following syntax:</span></span>  
  
 <span data-ttu-id="82848-111">`\` *數字*</span><span class="sxs-lookup"><span data-stu-id="82848-111">`\` *number*</span></span>  
  
 <span data-ttu-id="82848-112">其中 *number* 是規則運算式中的擷取群組序數位置。</span><span class="sxs-lookup"><span data-stu-id="82848-112">where *number* is the ordinal position of the capturing group in the regular expression.</span></span> <span data-ttu-id="82848-113">例如，`\4` 會比對第四個擷取群組的內容。</span><span class="sxs-lookup"><span data-stu-id="82848-113">For example, `\4` matches the contents of the fourth capturing group.</span></span> <span data-ttu-id="82848-114">如果規則運算式模式中未定義 *number*，便會發生剖析錯誤，而規則運算式引擎會擲回 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="82848-114">If *number* is not defined in the regular expression pattern, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="82848-115">例如，規則運算式 `\b(\w+)\s\1` 有效，因為 `(\w+)` 是運算式中第一個和唯一的擷取群組。</span><span class="sxs-lookup"><span data-stu-id="82848-115">For example, the regular expression `\b(\w+)\s\1` is valid, because `(\w+)` is the first and only capturing group in the expression.</span></span> <span data-ttu-id="82848-116">另一方面，`\b(\w+)\s\2` 無效並擲回引數例外狀況，因為沒有編號為 `\2` 的擷取群組。</span><span class="sxs-lookup"><span data-stu-id="82848-116">On the other hand, `\b(\w+)\s\2` is invalid and throws an argument exception, because there is no capturing group numbered `\2`.</span></span>  
  
 <span data-ttu-id="82848-117">請注意八進位逸出字碼 (例如 `\16`) 與使用相同標記法之 `\`*number* 反向參考間的模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="82848-117">Note the ambiguity between octal escape codes (such as `\16`) and `\`*number* backreferences that use the same notation.</span></span> <span data-ttu-id="82848-118">這個模棱兩可的情況已解決，如下所示：</span><span class="sxs-lookup"><span data-stu-id="82848-118">This ambiguity is resolved as follows:</span></span>  
  
-   <span data-ttu-id="82848-119">運算式 `\1` 到 `\9` 一律會解譯為反向參考，而不是八進位字碼。</span><span class="sxs-lookup"><span data-stu-id="82848-119">The expressions `\1` through `\9` are always interpreted as backreferences, and not as octal codes.</span></span>  
  
-   <span data-ttu-id="82848-120">如果多位數運算式的第一個數字是 8 或 9 (例如 `\80` 或 `\91`)，該運算式會解譯為常值。</span><span class="sxs-lookup"><span data-stu-id="82848-120">If the first digit of a multidigit expression is 8 or 9 (such as `\80` or `\91`), the expression as interpreted as a literal.</span></span>  
  
-   <span data-ttu-id="82848-121">從 `\10` 到更大值的運算式會視為反向參考 (如果有對應至該數字的反向參考)，否則會解譯為八進位字碼。</span><span class="sxs-lookup"><span data-stu-id="82848-121">Expressions from `\10` and greater are considered backreferences if there is a backreference corresponding to that number; otherwise, they are interpreted as octal codes.</span></span>  
  
-   <span data-ttu-id="82848-122">如果規則運算式包含未定義之群組號碼的反向參考，便會發生剖析錯誤，而規則運算式引擎會擲回 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="82848-122">If a regular expression contains a backreference to an undefined group number, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span>  
  
 <span data-ttu-id="82848-123">如果模擬兩可會造成問題，您可以使用 `\k<`*name*`>` 標記法，這樣就不會造成模擬兩可，而且不會與八進位字元碼混淆。</span><span class="sxs-lookup"><span data-stu-id="82848-123">If the ambiguity is a problem, you can use the `\k<`*name*`>` notation, which is unambiguous and cannot be confused with octal character codes.</span></span> <span data-ttu-id="82848-124">同樣地，十六進位字碼 (例如 `\xdd`) 不會不明確，而且不會與反向參考混淆。</span><span class="sxs-lookup"><span data-stu-id="82848-124">Similarly, hexadecimal codes such as `\xdd` are unambiguous and cannot be confused with backreferences.</span></span>  
  
 <span data-ttu-id="82848-125">下列範例會在字串中尋找雙字組字元。</span><span class="sxs-lookup"><span data-stu-id="82848-125">The following example finds doubled word characters in a string.</span></span> <span data-ttu-id="82848-126">它會定義由下列項目組成的規則運算式 `(\w)\1`。</span><span class="sxs-lookup"><span data-stu-id="82848-126">It defines a regular expression, `(\w)\1`, which consists of the following elements.</span></span>  
  
|<span data-ttu-id="82848-127">元素</span><span class="sxs-lookup"><span data-stu-id="82848-127">Element</span></span>|<span data-ttu-id="82848-128">描述</span><span class="sxs-lookup"><span data-stu-id="82848-128">Description</span></span>|  
|-------------|-----------------|  
|`(\w)`|<span data-ttu-id="82848-129">比對文字字元，並將其指派給第一個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="82848-129">Match a word character and assign it to the first capturing group.</span></span>|  
|`\1`|<span data-ttu-id="82848-130">比對與第一個擷取群組之值相同的下一個字元。</span><span class="sxs-lookup"><span data-stu-id="82848-130">Match the next character that is the same as the value of the first capturing group.</span></span>|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
 [!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]  
  
## <a name="named-backreferences"></a><span data-ttu-id="82848-131">具名反向參考</span><span class="sxs-lookup"><span data-stu-id="82848-131">Named Backreferences</span></span>  
 <span data-ttu-id="82848-132">具名反向參考是使用下列語法來定義：</span><span class="sxs-lookup"><span data-stu-id="82848-132">A named backreference is defined by using the following syntax:</span></span>  
  
 <span data-ttu-id="82848-133">`\k<` *name* `>`</span><span class="sxs-lookup"><span data-stu-id="82848-133">`\k<` *name* `>`</span></span>  
  
 <span data-ttu-id="82848-134">或：</span><span class="sxs-lookup"><span data-stu-id="82848-134">or:</span></span>  
  
 <span data-ttu-id="82848-135">`\k'` *name* `'`</span><span class="sxs-lookup"><span data-stu-id="82848-135">`\k'` *name* `'`</span></span>  
  
 <span data-ttu-id="82848-136">其中 *name* 是規則運算式模式中所定義之擷取群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="82848-136">where *name* is the name of a capturing group defined in the regular expression pattern.</span></span> <span data-ttu-id="82848-137">如果規則運算式模式中未定義 *name*，便會發生剖析錯誤，而規則運算式引擎會擲回 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="82848-137">If *name* is not defined in the regular expression pattern, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span>  
  
 <span data-ttu-id="82848-138">下列範例會在字串中尋找雙字組字元。</span><span class="sxs-lookup"><span data-stu-id="82848-138">The following example finds doubled word characters in a string.</span></span> <span data-ttu-id="82848-139">它會定義由下列項目組成的規則運算式 `(?<char>\w)\k<char>`。</span><span class="sxs-lookup"><span data-stu-id="82848-139">It defines a regular expression, `(?<char>\w)\k<char>`, which consists of the following elements.</span></span>  
  
|<span data-ttu-id="82848-140">元素</span><span class="sxs-lookup"><span data-stu-id="82848-140">Element</span></span>|<span data-ttu-id="82848-141">描述</span><span class="sxs-lookup"><span data-stu-id="82848-141">Description</span></span>|  
|-------------|-----------------|  
|`(?<char>\w)`|<span data-ttu-id="82848-142">比對字組字元，並將其指派給名為 `char` 的擷取群組。</span><span class="sxs-lookup"><span data-stu-id="82848-142">Match a word character and assign it to a capturing group named `char`.</span></span>|  
|`\k<char>`|<span data-ttu-id="82848-143">比對下一個與 `char` 擷取群組值相同的字元。</span><span class="sxs-lookup"><span data-stu-id="82848-143">Match the next character that is the same as the value of the `char` capturing group.</span></span>|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
 [!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]  
  
 <span data-ttu-id="82848-144">請注意，*name* 也可以是數字的字串表示。</span><span class="sxs-lookup"><span data-stu-id="82848-144">Note that *name* can also be the string representation of a number.</span></span> <span data-ttu-id="82848-145">例如，下列範例會使用規則運算式 `(?<2>\w)\k<2>` 來尋找字串中的雙字組字元。</span><span class="sxs-lookup"><span data-stu-id="82848-145">For example, the following example uses the regular expression `(?<2>\w)\k<2>` to find doubled word characters in a string.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
 [!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]  
  
## <a name="what-backreferences-match"></a><span data-ttu-id="82848-146">反向參考比對的項目</span><span class="sxs-lookup"><span data-stu-id="82848-146">What Backreferences Match</span></span>  
 <span data-ttu-id="82848-147">反向參考會參考群組最近使用的定義 (由左至右比對時，最接近左邊的定義)。</span><span class="sxs-lookup"><span data-stu-id="82848-147">A backreference refers to the most recent definition of a group (the definition most immediately to the left, when matching left to right).</span></span> <span data-ttu-id="82848-148">當群組進行多個擷取時，反向參考會參考最近發生的擷取。</span><span class="sxs-lookup"><span data-stu-id="82848-148">When a group makes multiple captures, a backreference refers to the most recent capture.</span></span>  
  
 <span data-ttu-id="82848-149">下列範例包含規則運算式模式 `(?<1>a)(?<1>\1b)*`，此模式可重新定義 \1 具名群組。</span><span class="sxs-lookup"><span data-stu-id="82848-149">The following example includes a regular expression pattern, `(?<1>a)(?<1>\1b)*`, which redefines the \1 named group.</span></span> <span data-ttu-id="82848-150">下表說明規則運算式中的每個模式。</span><span class="sxs-lookup"><span data-stu-id="82848-150">The following table describes each pattern in the regular expression.</span></span>  
  
|<span data-ttu-id="82848-151">模式</span><span class="sxs-lookup"><span data-stu-id="82848-151">Pattern</span></span>|<span data-ttu-id="82848-152">描述</span><span class="sxs-lookup"><span data-stu-id="82848-152">Description</span></span>|  
|-------------|-----------------|  
|`(?<1>a)`|<span data-ttu-id="82848-153">比對字元 "a"，並將結果指派給名為 `1` 的擷取群組。</span><span class="sxs-lookup"><span data-stu-id="82848-153">Match the character "a" and assign the result to the capturing group named `1`.</span></span>|  
|`(?<1>\1b)*`|<span data-ttu-id="82848-154">比對出現 0 或 1 次且名稱由 `1` 和 "b" 組成的群組，並將結果指派給名為 `1` 的擷取群組。</span><span class="sxs-lookup"><span data-stu-id="82848-154">Match 0 or 1 occurrence of the group named `1` along with a "b", and assign the result to the capturing group named `1`.</span></span>|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
 [!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]  
  
 <span data-ttu-id="82848-155">在比較規則運算式與輸入字串 ("aababb") 時，規則運算式引擎會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="82848-155">In comparing the regular expression with the input string ("aababb"), the regular expression engine performs the following operations:</span></span>  
  
1.  <span data-ttu-id="82848-156">它會從該字串的開頭開始，並且成功地比對 "a" 與運算式 `(?<1>a)`。</span><span class="sxs-lookup"><span data-stu-id="82848-156">It starts at the beginning of the string, and successfully matches "a" with the expression `(?<1>a)`.</span></span> <span data-ttu-id="82848-157">`1` 群組的值現在是 "a"。</span><span class="sxs-lookup"><span data-stu-id="82848-157">The value of the `1` group is now "a".</span></span>  
  
2.  <span data-ttu-id="82848-158">它會前進到第二個字元，並且成功地比對字串 "ab" 與運算式 `\1b`，或是 "ab"。</span><span class="sxs-lookup"><span data-stu-id="82848-158">It advances to the second character, and successfully matches the string "ab" with the expression `\1b`, or "ab".</span></span> <span data-ttu-id="82848-159">然後它會將結果 "ab" 指派給 `\1`。</span><span class="sxs-lookup"><span data-stu-id="82848-159">It then assigns the result, "ab" to `\1`.</span></span>  
  
3.  <span data-ttu-id="82848-160">它會前進到第四個字元。</span><span class="sxs-lookup"><span data-stu-id="82848-160">It advances to the fourth character.</span></span> <span data-ttu-id="82848-161">運算式 `(?<1>\1b)` 要比對零次以上，才算成功地比對字串 "abb" 與運算式 `\1b`。</span><span class="sxs-lookup"><span data-stu-id="82848-161">The expression `(?<1>\1b)` is to be matched zero or more times, so it successfully matches the string "abb" with the expression `\1b`.</span></span> <span data-ttu-id="82848-162">然後它會將結果 "abb" 指派回到 `\1`。</span><span class="sxs-lookup"><span data-stu-id="82848-162">It assigns the result, "abb", back to `\1`.</span></span>  
  
 <span data-ttu-id="82848-163">在此範例中，`*` 是迴圈數量詞，它會重複評估直到規則運算式引擎無法符合其所定義的模式為止。</span><span class="sxs-lookup"><span data-stu-id="82848-163">In this example, `*` is a looping quantifier -- it is evaluated repeatedly until the regular expression engine cannot match the pattern it defines.</span></span> <span data-ttu-id="82848-164">迴圈數量詞並不會清除群組定義。</span><span class="sxs-lookup"><span data-stu-id="82848-164">Looping quantifiers do not clear group definitions.</span></span>  
  
 <span data-ttu-id="82848-165">如果群組沒有擷取任何子字串，該群組的反向參考會是未定義的，而且永遠不會進行比對。</span><span class="sxs-lookup"><span data-stu-id="82848-165">If a group has not captured any substrings, a backreference to that group is undefined and never matches.</span></span> <span data-ttu-id="82848-166">這可由定義如下的規則運算式模式 `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b` 來說明：</span><span class="sxs-lookup"><span data-stu-id="82848-166">This is illustrated by the regular expression pattern `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, which is defined as follows:</span></span>  
  
|<span data-ttu-id="82848-167">模式</span><span class="sxs-lookup"><span data-stu-id="82848-167">Pattern</span></span>|<span data-ttu-id="82848-168">描述</span><span class="sxs-lookup"><span data-stu-id="82848-168">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="82848-169">開始字邊界比對。</span><span class="sxs-lookup"><span data-stu-id="82848-169">Begin the match on a word boundary.</span></span>|  
|`(\p{Lu}{2})`|<span data-ttu-id="82848-170">比對兩個大寫字母。</span><span class="sxs-lookup"><span data-stu-id="82848-170">Match two uppercase letters.</span></span> <span data-ttu-id="82848-171">這是第一個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="82848-171">This is the first capturing group.</span></span>|  
|`(\d{2})?`|<span data-ttu-id="82848-172">比對出現零次或一次的兩個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="82848-172">Match zero or one occurrence of two decimal digits.</span></span> <span data-ttu-id="82848-173">這是第二個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="82848-173">This is the second capturing group.</span></span>|  
|`(\p{Lu}{2})`|<span data-ttu-id="82848-174">比對兩個大寫字母。</span><span class="sxs-lookup"><span data-stu-id="82848-174">Match two uppercase letters.</span></span> <span data-ttu-id="82848-175">這是第三個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="82848-175">This is the third capturing group.</span></span>|  
|`\b`|<span data-ttu-id="82848-176">結束字邊界比對。</span><span class="sxs-lookup"><span data-stu-id="82848-176">End the match on a word boundary.</span></span>|  
  
 <span data-ttu-id="82848-177">輸入字串可以符合這個規則運算式，即使不存在第二個擷取群組所定義的兩個十進位數字亦然。</span><span class="sxs-lookup"><span data-stu-id="82848-177">An input string can match this regular expression even if the two decimal digits that are defined by the second capturing group are not present.</span></span> <span data-ttu-id="82848-178">下列範例顯示即使比對成功，仍會在兩個成功的擷取群組之間找到空的擷取群組。</span><span class="sxs-lookup"><span data-stu-id="82848-178">The following example shows that even though the match is successful, an empty capturing group is found between two successful capturing groups.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
 [!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="82848-179">請參閱</span><span class="sxs-lookup"><span data-stu-id="82848-179">See Also</span></span>  
 [<span data-ttu-id="82848-180">規則運算式語言 - 快速參考</span><span class="sxs-lookup"><span data-stu-id="82848-180">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
