---
title: .NET 規則運算式中的反向參考建構
description: 了解如何在規則運算式中使用反向參考建構來識別重複的文字元素。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- backreferences
- constructs, backreference
- .NET Framework regular expressions, backreference constructs
- regular expressions, backreference constructs
ms.assetid: 567a4b8d-0e79-49dc-8df9-f4b1aa376a2a
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: 11df25617a618cdc835ca6555c671a187ce09f8d
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991650"
---
# <a name="backreference-constructs-in-regular-expressions"></a><span data-ttu-id="ba606-103">規則運算式中的反向參考建構</span><span class="sxs-lookup"><span data-stu-id="ba606-103">Backreference Constructs in Regular Expressions</span></span>

<span data-ttu-id="ba606-104">反向參考提供便利的方式來識別字串內的重複字元或子字串。</span><span class="sxs-lookup"><span data-stu-id="ba606-104">Backreferences provide a convenient way to identify a repeated character or substring within a string.</span></span> <span data-ttu-id="ba606-105">例如，如果輸入字串包含多次出現的任意子字串，您可以比對第一個出現的子字串與擷取的群組，接著使用反向參考來比對隨後出現的子字串。</span><span class="sxs-lookup"><span data-stu-id="ba606-105">For example, if the input string contains multiple occurrences of an arbitrary substring, you can match the first occurrence with a capturing group, and then use a backreference to match subsequent occurrences of the substring.</span></span>

> [!NOTE]
> <span data-ttu-id="ba606-106">對於取代字串中的具名和編號擷取群組，會使用不同的語法來參考。</span><span class="sxs-lookup"><span data-stu-id="ba606-106">A separate syntax is used to refer to named and numbered capturing groups in replacement strings.</span></span> <span data-ttu-id="ba606-107">如需詳細資訊，請參閱[替代](substitutions-in-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="ba606-107">For more information, see [Substitutions](substitutions-in-regular-expressions.md).</span></span>

<span data-ttu-id="ba606-108">.NET 會定義個別的語言項目，以參考編號和具名擷取群組。</span><span class="sxs-lookup"><span data-stu-id="ba606-108">.NET defines separate language elements to refer to numbered and named capturing groups.</span></span> <span data-ttu-id="ba606-109">如需擷取群組的詳細資訊，請參閱[群組建構](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="ba606-109">For more information about capturing groups, see [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).</span></span>

## <a name="numbered-backreferences"></a><span data-ttu-id="ba606-110">編號反向參考</span><span class="sxs-lookup"><span data-stu-id="ba606-110">Numbered Backreferences</span></span>

<span data-ttu-id="ba606-111">編號反向參考會使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="ba606-111">A numbered backreference uses the following syntax:</span></span>

<span data-ttu-id="ba606-112">`\` *number*</span><span class="sxs-lookup"><span data-stu-id="ba606-112">`\` *number*</span></span>

<span data-ttu-id="ba606-113">其中 *number* 是規則運算式中的擷取群組序數位置。</span><span class="sxs-lookup"><span data-stu-id="ba606-113">where *number* is the ordinal position of the capturing group in the regular expression.</span></span> <span data-ttu-id="ba606-114">例如，`\4` 會比對第四個擷取群組的內容。</span><span class="sxs-lookup"><span data-stu-id="ba606-114">For example, `\4` matches the contents of the fourth capturing group.</span></span> <span data-ttu-id="ba606-115">如果規則運算式模式中未定義 *number*，便會發生剖析錯誤，而規則運算式引擎會擲回 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="ba606-115">If *number* is not defined in the regular expression pattern, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="ba606-116">例如，規則運算式 `\b(\w+)\s\1` 有效，因為 `(\w+)` 是運算式中第一個和唯一的擷取群組。</span><span class="sxs-lookup"><span data-stu-id="ba606-116">For example, the regular expression `\b(\w+)\s\1` is valid, because `(\w+)` is the first and only capturing group in the expression.</span></span> <span data-ttu-id="ba606-117">另一方面，`\b(\w+)\s\2` 無效並擲回引數例外狀況，因為沒有編號為 `\2` 的擷取群組。</span><span class="sxs-lookup"><span data-stu-id="ba606-117">On the other hand, `\b(\w+)\s\2` is invalid and throws an argument exception, because there is no capturing group numbered `\2`.</span></span> <span data-ttu-id="ba606-118">此外，如果 *number* 識別在特定序數位置的擷取群組，但擷取群組已經被指派和其序數順序不同的數值名稱，則規則運算式剖析器也會擲回 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="ba606-118">In addition, if *number* identifies a capturing group in a particular ordinal position, but that capturing group has been assigned a numeric name different than its ordinal position, the regular expression parser also throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="ba606-119">請注意八進位逸出字碼 (例如 `\16`) 與使用相同標記法之 `\`*number* 反向參考間的模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="ba606-119">Note the ambiguity between octal escape codes (such as `\16`) and `\`*number* backreferences that use the same notation.</span></span> <span data-ttu-id="ba606-120">這個模棱兩可的情況已解決，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ba606-120">This ambiguity is resolved as follows:</span></span>

- <span data-ttu-id="ba606-121">運算式 `\1` 到 `\9` 一律會解譯為反向參考，而不是八進位字碼。</span><span class="sxs-lookup"><span data-stu-id="ba606-121">The expressions `\1` through `\9` are always interpreted as backreferences, and not as octal codes.</span></span>

- <span data-ttu-id="ba606-122">如果多位數運算式的第一個數字是 8 或 9 (例如 `\80` 或 `\91`)，該運算式會解譯為常值。</span><span class="sxs-lookup"><span data-stu-id="ba606-122">If the first digit of a multidigit expression is 8 or 9 (such as `\80` or `\91`), the expression as interpreted as a literal.</span></span>

- <span data-ttu-id="ba606-123">從 `\10` 到更大值的運算式會視為反向參考 (如果有對應至該數字的反向參考)，否則會解譯為八進位字碼。</span><span class="sxs-lookup"><span data-stu-id="ba606-123">Expressions from `\10` and greater are considered backreferences if there is a backreference corresponding to that number; otherwise, they are interpreted as octal codes.</span></span>

- <span data-ttu-id="ba606-124">如果規則運算式包含未定義之群組號碼的反向參考，便會發生剖析錯誤，而規則運算式引擎會擲回 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="ba606-124">If a regular expression contains a backreference to an undefined group number, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="ba606-125">如果模擬兩可會造成問題，您可以使用 `\k<`*name*`>` 標記法，這樣就不會造成模擬兩可，而且不會與八進位字元碼混淆。</span><span class="sxs-lookup"><span data-stu-id="ba606-125">If the ambiguity is a problem, you can use the `\k<`*name*`>` notation, which is unambiguous and cannot be confused with octal character codes.</span></span> <span data-ttu-id="ba606-126">同樣地，十六進位字碼 (例如 `\xdd`) 不會不明確，而且不會與反向參考混淆。</span><span class="sxs-lookup"><span data-stu-id="ba606-126">Similarly, hexadecimal codes such as `\xdd` are unambiguous and cannot be confused with backreferences.</span></span>

<span data-ttu-id="ba606-127">下列範例會在字串中尋找雙字組字元。</span><span class="sxs-lookup"><span data-stu-id="ba606-127">The following example finds doubled word characters in a string.</span></span> <span data-ttu-id="ba606-128">它會定義由下列項目組成的規則運算式 `(\w)\1`。</span><span class="sxs-lookup"><span data-stu-id="ba606-128">It defines a regular expression, `(\w)\1`, which consists of the following elements.</span></span>

|<span data-ttu-id="ba606-129">元素</span><span class="sxs-lookup"><span data-stu-id="ba606-129">Element</span></span>|<span data-ttu-id="ba606-130">描述</span><span class="sxs-lookup"><span data-stu-id="ba606-130">Description</span></span>|
|-------------|-----------------|
|`(\w)`|<span data-ttu-id="ba606-131">比對文字字元，並將其指派給第一個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="ba606-131">Match a word character and assign it to the first capturing group.</span></span>|
|`\1`|<span data-ttu-id="ba606-132">比對與第一個擷取群組之值相同的下一個字元。</span><span class="sxs-lookup"><span data-stu-id="ba606-132">Match the next character that is the same as the value of the first capturing group.</span></span>|

[!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
[!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]

## <a name="named-backreferences"></a><span data-ttu-id="ba606-133">具名反向參考</span><span class="sxs-lookup"><span data-stu-id="ba606-133">Named Backreferences</span></span>

<span data-ttu-id="ba606-134">具名反向參考是使用下列語法來定義：</span><span class="sxs-lookup"><span data-stu-id="ba606-134">A named backreference is defined by using the following syntax:</span></span>

<span data-ttu-id="ba606-135">`\k<` *name* `>`</span><span class="sxs-lookup"><span data-stu-id="ba606-135">`\k<` *name* `>`</span></span>

<span data-ttu-id="ba606-136">或：</span><span class="sxs-lookup"><span data-stu-id="ba606-136">or:</span></span>

<span data-ttu-id="ba606-137">`\k'` *name* `'`</span><span class="sxs-lookup"><span data-stu-id="ba606-137">`\k'` *name* `'`</span></span>

<span data-ttu-id="ba606-138">其中 *name* 是規則運算式模式中所定義之擷取群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="ba606-138">where *name* is the name of a capturing group defined in the regular expression pattern.</span></span> <span data-ttu-id="ba606-139">如果規則運算式模式中未定義 *name*，便會發生剖析錯誤，而規則運算式引擎會擲回 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="ba606-139">If *name* is not defined in the regular expression pattern, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="ba606-140">下列範例會在字串中尋找雙字組字元。</span><span class="sxs-lookup"><span data-stu-id="ba606-140">The following example finds doubled word characters in a string.</span></span> <span data-ttu-id="ba606-141">它會定義由下列項目組成的規則運算式 `(?<char>\w)\k<char>`。</span><span class="sxs-lookup"><span data-stu-id="ba606-141">It defines a regular expression, `(?<char>\w)\k<char>`, which consists of the following elements.</span></span>

|<span data-ttu-id="ba606-142">元素</span><span class="sxs-lookup"><span data-stu-id="ba606-142">Element</span></span>|<span data-ttu-id="ba606-143">說明</span><span class="sxs-lookup"><span data-stu-id="ba606-143">Description</span></span>|
|-------------|-----------------|
|`(?<char>\w)`|<span data-ttu-id="ba606-144">比對字組字元，並將其指派給名為 `char` 的擷取群組。</span><span class="sxs-lookup"><span data-stu-id="ba606-144">Match a word character and assign it to a capturing group named `char`.</span></span>|
|`\k<char>`|<span data-ttu-id="ba606-145">比對下一個與 `char` 擷取群組值相同的字元。</span><span class="sxs-lookup"><span data-stu-id="ba606-145">Match the next character that is the same as the value of the `char` capturing group.</span></span>|

[!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
[!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]

## <a name="named-numeric-backreferences"></a><span data-ttu-id="ba606-146">具名的數值反向參考</span><span class="sxs-lookup"><span data-stu-id="ba606-146">Named numeric backreferences</span></span>

<span data-ttu-id="ba606-147">在含有 `\k` 的具名反向參考中，*name* 也可以是數字的字串表示。</span><span class="sxs-lookup"><span data-stu-id="ba606-147">In a named backreference with `\k`, *name* can also be the string representation of a number.</span></span> <span data-ttu-id="ba606-148">例如，下列範例會使用規則運算式 `(?<2>\w)\k<2>` 來尋找字串中的雙字組字元。</span><span class="sxs-lookup"><span data-stu-id="ba606-148">For example, the following example uses the regular expression `(?<2>\w)\k<2>` to find doubled word characters in a string.</span></span> <span data-ttu-id="ba606-149">在此案例中，範例定義了明確地命名為 "2" 的擷取群組，而反向參考也相對應地命名為 "2"。</span><span class="sxs-lookup"><span data-stu-id="ba606-149">In this case, the example defines a capturing group that is explicitly named "2", and the backreference is correspondingly named "2".</span></span>

[!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
[!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]

<span data-ttu-id="ba606-150">如果 *name* 是數值的字串表示，且沒有擷取群組具有該名稱，則 `\k<`*name*`>` 和反向參考 `\`*number* 是相同的，其中 *number* 是擷取的序數位置。</span><span class="sxs-lookup"><span data-stu-id="ba606-150">If *name* is the string representation of a number, and no capturing group has that name, `\k<`*name*`>` is the same as the backreference `\`*number*, where *number* is the ordinal position of the capture.</span></span> <span data-ttu-id="ba606-151">在下列範例中，有名為 `char` 的單一擷取群組。</span><span class="sxs-lookup"><span data-stu-id="ba606-151">In the following example, there is a single capturing group named `char`.</span></span> <span data-ttu-id="ba606-152">反向參考建構將它參考為 `\k<1>`。</span><span class="sxs-lookup"><span data-stu-id="ba606-152">The backreference construct refers to it as `\k<1>`.</span></span> <span data-ttu-id="ba606-153">如範例的輸出所示，因為 `char` 是第一個擷取群組，因此對 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> 的呼叫會成功。</span><span class="sxs-lookup"><span data-stu-id="ba606-153">As the output from the example shows, the call to the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> succeeds because `char` is the first capturing group.</span></span>

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference6.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference6.vb)]

<span data-ttu-id="ba606-154">不過，如果 *name* 是數值的字串表示，且在該位置的擷取群組已經明確地被指派數值名稱，則規則運算式剖析器無法根據擷取群組的序數位置識別它。</span><span class="sxs-lookup"><span data-stu-id="ba606-154">However, if *name* is the string representation of a number and the capturing group in that position has been explicitly assigned a numeric name, the regular expression parser cannot identify the capturing group by its ordinal position.</span></span> <span data-ttu-id="ba606-155">相反地，它會<xref:System.ArgumentException>擲回。</span><span class="sxs-lookup"><span data-stu-id="ba606-155">Instead, it throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="ba606-156">下列範例中的唯一捕捉群組會命名為 "2"。</span><span class="sxs-lookup"><span data-stu-id="ba606-156">The only capturing group in the following example is named "2".</span></span> <span data-ttu-id="ba606-157">因為 `\k` 建構是用來定義名為 "1" 的反向參考，所以規則運算式剖析器無法識別第一個擷取群組並擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ba606-157">Because the `\k` construct is used to define a backreference named "1", the regular expression parser is unable to identify the first capturing group and throws an exception.</span></span>

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference7.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference7.vb)]

## <a name="what-backreferences-match"></a><span data-ttu-id="ba606-158">反向參考比對的項目</span><span class="sxs-lookup"><span data-stu-id="ba606-158">What Backreferences Match</span></span>

<span data-ttu-id="ba606-159">反向參考會參考群組最近使用的定義 (由左至右比對時，最接近左邊的定義)。</span><span class="sxs-lookup"><span data-stu-id="ba606-159">A backreference refers to the most recent definition of a group (the definition most immediately to the left, when matching left to right).</span></span> <span data-ttu-id="ba606-160">當群組進行多個擷取時，反向參考會參考最近發生的擷取。</span><span class="sxs-lookup"><span data-stu-id="ba606-160">When a group makes multiple captures, a backreference refers to the most recent capture.</span></span>

<span data-ttu-id="ba606-161">下列範例包含規則運算式模式 `(?<1>a)(?<1>\1b)*`，此模式可重新定義 \1 具名群組。</span><span class="sxs-lookup"><span data-stu-id="ba606-161">The following example includes a regular expression pattern, `(?<1>a)(?<1>\1b)*`, which redefines the \1 named group.</span></span> <span data-ttu-id="ba606-162">下表說明規則運算式中的每個模式。</span><span class="sxs-lookup"><span data-stu-id="ba606-162">The following table describes each pattern in the regular expression.</span></span>

|<span data-ttu-id="ba606-163">模式</span><span class="sxs-lookup"><span data-stu-id="ba606-163">Pattern</span></span>|<span data-ttu-id="ba606-164">描述</span><span class="sxs-lookup"><span data-stu-id="ba606-164">Description</span></span>|
|-------------|-----------------|
|`(?<1>a)`|<span data-ttu-id="ba606-165">比對字元 "a"，並將結果指派給名為 `1` 的擷取群組。</span><span class="sxs-lookup"><span data-stu-id="ba606-165">Match the character "a" and assign the result to the capturing group named `1`.</span></span>|
|`(?<1>\1b)*`|<span data-ttu-id="ba606-166">比對 0 或多次出現名為 `1` 和 "b" 之群組的情況，並將結果指派給名為 `1` 的擷取群組。</span><span class="sxs-lookup"><span data-stu-id="ba606-166">Match zero or more occurrences of the group named `1` along with a "b", and assign the result to the capturing group named `1`.</span></span>|

[!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
[!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]

<span data-ttu-id="ba606-167">在比較規則運算式與輸入字串 ("aababb") 時，規則運算式引擎會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="ba606-167">In comparing the regular expression with the input string ("aababb"), the regular expression engine performs the following operations:</span></span>

1. <span data-ttu-id="ba606-168">它會從該字串的開頭開始，並且成功地比對 "a" 與運算式 `(?<1>a)`。</span><span class="sxs-lookup"><span data-stu-id="ba606-168">It starts at the beginning of the string, and successfully matches "a" with the expression `(?<1>a)`.</span></span> <span data-ttu-id="ba606-169">`1` 群組的值現在是 "a"。</span><span class="sxs-lookup"><span data-stu-id="ba606-169">The value of the `1` group is now "a".</span></span>

2. <span data-ttu-id="ba606-170">它會前進到第二個字元，並且成功地比對字串 "ab" 與運算式 `\1b`，或是 "ab"。</span><span class="sxs-lookup"><span data-stu-id="ba606-170">It advances to the second character, and successfully matches the string "ab" with the expression `\1b`, or "ab".</span></span> <span data-ttu-id="ba606-171">然後它會將結果 "ab" 指派給 `\1`。</span><span class="sxs-lookup"><span data-stu-id="ba606-171">It then assigns the result, "ab" to `\1`.</span></span>

3. <span data-ttu-id="ba606-172">它會前進到第四個字元。</span><span class="sxs-lookup"><span data-stu-id="ba606-172">It advances to the fourth character.</span></span> <span data-ttu-id="ba606-173">運算式 `(?<1>\1b)*` 要比對零次以上，才算成功地比對字串 "abb" 與運算式 `\1b`。</span><span class="sxs-lookup"><span data-stu-id="ba606-173">The expression `(?<1>\1b)*` is to be matched zero or more times, so it successfully matches the string "abb" with the expression `\1b`.</span></span> <span data-ttu-id="ba606-174">然後它會將結果 "abb" 指派回到 `\1`。</span><span class="sxs-lookup"><span data-stu-id="ba606-174">It assigns the result, "abb", back to `\1`.</span></span>

<span data-ttu-id="ba606-175">在此範例中，`*` 是迴圈數量詞，它會重複評估直到規則運算式引擎無法符合其所定義的模式為止。</span><span class="sxs-lookup"><span data-stu-id="ba606-175">In this example, `*` is a looping quantifier -- it is evaluated repeatedly until the regular expression engine cannot match the pattern it defines.</span></span> <span data-ttu-id="ba606-176">迴圈數量詞並不會清除群組定義。</span><span class="sxs-lookup"><span data-stu-id="ba606-176">Looping quantifiers do not clear group definitions.</span></span>

<span data-ttu-id="ba606-177">如果群組沒有擷取任何子字串，該群組的反向參考會是未定義的，而且永遠不會進行比對。</span><span class="sxs-lookup"><span data-stu-id="ba606-177">If a group has not captured any substrings, a backreference to that group is undefined and never matches.</span></span> <span data-ttu-id="ba606-178">這可由定義如下的規則運算式模式 `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b` 來說明：</span><span class="sxs-lookup"><span data-stu-id="ba606-178">This is illustrated by the regular expression pattern `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, which is defined as follows:</span></span>

|<span data-ttu-id="ba606-179">模式</span><span class="sxs-lookup"><span data-stu-id="ba606-179">Pattern</span></span>|<span data-ttu-id="ba606-180">說明</span><span class="sxs-lookup"><span data-stu-id="ba606-180">Description</span></span>|
|-------------|-----------------|
|`\b`|<span data-ttu-id="ba606-181">開始字邊界比對。</span><span class="sxs-lookup"><span data-stu-id="ba606-181">Begin the match on a word boundary.</span></span>|
|`(\p{Lu}{2})`|<span data-ttu-id="ba606-182">比對兩個大寫字母。</span><span class="sxs-lookup"><span data-stu-id="ba606-182">Match two uppercase letters.</span></span> <span data-ttu-id="ba606-183">這是第一個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="ba606-183">This is the first capturing group.</span></span>|
|`(\d{2})?`|<span data-ttu-id="ba606-184">比對出現零次或一次的兩個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="ba606-184">Match zero or one occurrence of two decimal digits.</span></span> <span data-ttu-id="ba606-185">這是第二個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="ba606-185">This is the second capturing group.</span></span>|
|`(\p{Lu}{2})`|<span data-ttu-id="ba606-186">比對兩個大寫字母。</span><span class="sxs-lookup"><span data-stu-id="ba606-186">Match two uppercase letters.</span></span> <span data-ttu-id="ba606-187">這是第三個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="ba606-187">This is the third capturing group.</span></span>|
|`\b`|<span data-ttu-id="ba606-188">結束字邊界比對。</span><span class="sxs-lookup"><span data-stu-id="ba606-188">End the match on a word boundary.</span></span>|

<span data-ttu-id="ba606-189">輸入字串可以符合這個規則運算式，即使不存在第二個擷取群組所定義的兩個十進位數字亦然。</span><span class="sxs-lookup"><span data-stu-id="ba606-189">An input string can match this regular expression even if the two decimal digits that are defined by the second capturing group are not present.</span></span> <span data-ttu-id="ba606-190">下列範例顯示即使比對成功，仍會在兩個成功的擷取群組之間找到空的擷取群組。</span><span class="sxs-lookup"><span data-stu-id="ba606-190">The following example shows that even though the match is successful, an empty capturing group is found between two successful capturing groups.</span></span>

[!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
[!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]

## <a name="see-also"></a><span data-ttu-id="ba606-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba606-191">See also</span></span>

- [<span data-ttu-id="ba606-192">規則運算式語言 - 快速參考</span><span class="sxs-lookup"><span data-stu-id="ba606-192">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
