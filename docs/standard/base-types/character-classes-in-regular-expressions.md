---
title: .NET 規則運算式中的字元類別
description: 了解如何使用字元類別來代表 .NET 規則運算式中的一組字元。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- character classes
- regular expressions, character classes
- characters, matching syntax
- .NET Framework regular expressions, character classes
ms.assetid: 0f8bffab-ee0d-4e0e-9a96-2b4a252bb7e4
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: e577f376b347442f6693a7a5478757ce3b698752
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053007"
---
# <a name="character-classes-in-regular-expressions"></a><span data-ttu-id="8d9d4-103">規則運算式中的字元類別</span><span class="sxs-lookup"><span data-stu-id="8d9d4-103">Character classes in regular expressions</span></span>

<span data-ttu-id="8d9d4-104">字元類別會定義一組字元，其中任何字元都可在輸入字串中出現，以便讓比對成功。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-104">A character class defines a set of characters, any one of which can occur in an input string for a match to succeed.</span></span> <span data-ttu-id="8d9d4-105">.NET 中的規則運算式語言支援下列字元類別：</span><span class="sxs-lookup"><span data-stu-id="8d9d4-105">The regular expression language in .NET supports the following character classes:</span></span>  
  
- <span data-ttu-id="8d9d4-106">正字元群組。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-106">Positive character groups.</span></span> <span data-ttu-id="8d9d4-107">輸入字串中的字元必須符合指定字元集的其中一個字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-107">A character in the input string must match one of a specified set of characters.</span></span> <span data-ttu-id="8d9d4-108">如需詳細資訊，請參閱[正字元群組](#PositiveGroup)。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-108">For more information, see [Positive Character Group](#PositiveGroup).</span></span>  
  
- <span data-ttu-id="8d9d4-109">負字元群組。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-109">Negative character groups.</span></span> <span data-ttu-id="8d9d4-110">輸入字串中的字元不得符合指定字元集的其中一個字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-110">A character in the input string must not match one of a specified set of characters.</span></span> <span data-ttu-id="8d9d4-111">如需詳細資訊，請參閱[負字元群組](#NegativeGroup)。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-111">For more information, see [Negative Character Group](#NegativeGroup).</span></span>  
  
- <span data-ttu-id="8d9d4-112">任何字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-112">Any character.</span></span> <span data-ttu-id="8d9d4-113">在規則運算式中的 `.` (點或句號) 字元是萬用字元，可符合 `\n` 以外的任何字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-113">The `.` (dot or period) character in a regular expression is a wildcard character that matches any character except `\n`.</span></span> <span data-ttu-id="8d9d4-114">如需詳細資訊，請參閱[任何字元](#AnyCharacter)。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-114">For more information, see [Any Character](#AnyCharacter).</span></span>  
  
- <span data-ttu-id="8d9d4-115">一般 Unicode 分類或具名區塊。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-115">A general Unicode category or named block.</span></span> <span data-ttu-id="8d9d4-116">輸入字串中的字元必須是特定 Unicode 分類的成員，或者必須落在 Unicode 字元的連續範圍內，比對才會成功。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-116">A character in the input string must be a member of a particular Unicode category or must fall within a contiguous range of Unicode characters for a match to succeed.</span></span> <span data-ttu-id="8d9d4-117">如需詳細資訊，請參閱 [Unicode 分類或 Unicode 區塊](#CategoryOrBlock)。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-117">For more information, see [Unicode Category or Unicode Block](#CategoryOrBlock).</span></span>  
  
- <span data-ttu-id="8d9d4-118">負的一般 Unicode 分類或是具名區塊。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-118">A negative general Unicode category or named block.</span></span> <span data-ttu-id="8d9d4-119">輸入字串中的字元不得是特定 Unicode 分類的成員，或者不得落在 Unicode 字元的連續範圍內，比對才會成功。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-119">A character in the input string must not be a member of a particular Unicode category or must not fall within a contiguous range of Unicode characters for a match to succeed.</span></span> <span data-ttu-id="8d9d4-120">如需詳細資訊，請參閱[負 Unicode 分類或 Unicode 區塊](#NegativeCategoryOrBlock)。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-120">For more information, see [Negative Unicode Category or Unicode Block](#NegativeCategoryOrBlock).</span></span>  
  
- <span data-ttu-id="8d9d4-121">文字字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-121">A word character.</span></span> <span data-ttu-id="8d9d4-122">輸入字串中的字元可以隸屬於任何適用於文字字元的 Unicode 分類。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-122">A character in the input string can belong to any of the Unicode categories that are appropriate for characters in words.</span></span> <span data-ttu-id="8d9d4-123">如需詳細資訊，請參閱[文字字元](#WordCharacter)。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-123">For more information, see [Word Character](#WordCharacter).</span></span>  
  
- <span data-ttu-id="8d9d4-124">非文字字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-124">A non-word character.</span></span> <span data-ttu-id="8d9d4-125">輸入字串中的字元可以隸屬於任何非文字字元的 Unicode 分類。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-125">A character in the input string can belong to any Unicode category that is not a word character.</span></span> <span data-ttu-id="8d9d4-126">如需詳細資訊，請參閱[非文字字元](#NonWordCharacter)。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-126">For more information, see [Non-Word Character](#NonWordCharacter).</span></span>  
  
- <span data-ttu-id="8d9d4-127">空白字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-127">A white-space character.</span></span> <span data-ttu-id="8d9d4-128">輸入字串中的字元可以是任何 Unicode 分隔符號字元，以及任何一種控制字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-128">A character in the input string can be any Unicode separator character, as well as any one of a number of control characters.</span></span> <span data-ttu-id="8d9d4-129">如需詳細資訊，請參閱[空白字元](#WhitespaceCharacter)。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-129">For more information, see [White-Space Character](#WhitespaceCharacter).</span></span>  
  
- <span data-ttu-id="8d9d4-130">非空白字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-130">A non-white-space character.</span></span> <span data-ttu-id="8d9d4-131">輸入字串中的字元可以是空白字元以外的任何字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-131">A character in the input string can be any character that is not a white-space character.</span></span> <span data-ttu-id="8d9d4-132">如需詳細資訊，請參閱[非空白字元](#NonWhitespaceCharacter)。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-132">For more information, see [Non-White-Space Character](#NonWhitespaceCharacter).</span></span>  
  
- <span data-ttu-id="8d9d4-133">十進位數字。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-133">A decimal digit.</span></span> <span data-ttu-id="8d9d4-134">輸入字串中的字元可以是歸類為 Unicode 十進位數字的任何一個數字字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-134">A character in the input string can be any of a number of characters classified as Unicode decimal digits.</span></span> <span data-ttu-id="8d9d4-135">如需詳細資訊，請參閱[十進位數字字元](#DigitCharacter)。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-135">For more information, see [Decimal Digit Character](#DigitCharacter).</span></span>  
  
- <span data-ttu-id="8d9d4-136">非十進位數字。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-136">A non-decimal digit.</span></span> <span data-ttu-id="8d9d4-137">輸入字串中的字元可以是 Unicode 十進位數字以外的任何字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-137">A character in the input string can be anything other than a Unicode decimal digit.</span></span> <span data-ttu-id="8d9d4-138">如需詳細資訊，請參閱[十進位數字字元](#NonDigitCharacter)。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-138">For more information, see [Decimal Digit Character](#NonDigitCharacter).</span></span>  
  
 <span data-ttu-id="8d9d4-139">.NET 支援字元類別減法運算式，可讓您將一組字元定義為從某個字元類別中排除另一個字元類別的結果。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-139">.NET supports character class subtraction expressions, which enables you to define a set of characters as the result of excluding one character class from another character class.</span></span> <span data-ttu-id="8d9d4-140">如需詳細資訊，請參閱[字元類別減法](#CharacterClassSubtraction)。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-140">For more information, see [Character Class Subtraction](#CharacterClassSubtraction).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d9d4-141">依分類比對字元的字元類別 (例如，[\w](#WordCharacter) 會比對字組字元，或[\p{}](#CategoryOrBlock) 會比對 Unicode 分類) 會依賴 <xref:System.Globalization.CharUnicodeInfo> 類別來提供字元分類的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-141">Character classes that match characters by category, such as [\w](#WordCharacter) to match word characters or [\p{}](#CategoryOrBlock) to match a Unicode category, rely on the <xref:System.Globalization.CharUnicodeInfo> class to provide information about character categories.</span></span>  <span data-ttu-id="8d9d4-142">從 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 開始，字元類別根據 [Unicode 標準 8.0.0 版](https://www.unicode.org/versions/Unicode8.0.0/)。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-142">Starting with the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], character categories are based on [The Unicode Standard, Version 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/).</span></span> <span data-ttu-id="8d9d4-143">在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 至 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 中，它們根據 [Unicode 標準 6.3.0 版](https://www.unicode.org/versions/Unicode6.3.0/)。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-143">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] through the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], they are based on [The Unicode Standard, Version 6.3.0](https://www.unicode.org/versions/Unicode6.3.0/).</span></span>  
  
<a name="PositiveGroup"></a>   
## <a name="positive-character-group--"></a><span data-ttu-id="8d9d4-144">正字元群組：[ ]</span><span class="sxs-lookup"><span data-stu-id="8d9d4-144">Positive character group: [ ]</span></span>  
 <span data-ttu-id="8d9d4-145">正字元群組會指定一份字元清單，其中任何字元都可出現在輸入字串中，以便出現相符項目。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-145">A positive character group specifies a list of characters, any one of which may appear in an input string for a match to occur.</span></span> <span data-ttu-id="8d9d4-146">這份字元清單可以個別指定，也可以依範圍指定，或同時依兩種方式指定。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-146">This list of characters may be specified individually, as a range, or both.</span></span>  
  
 <span data-ttu-id="8d9d4-147">指定個別字元清單的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="8d9d4-147">The syntax for specifying a list of individual characters is as follows:</span></span>  
  
 <span data-ttu-id="8d9d4-148">[*character_group*]</span><span class="sxs-lookup"><span data-stu-id="8d9d4-148">[*character_group*]</span></span>  
  
 <span data-ttu-id="8d9d4-149">其中 *character_group* 是為了讓比對成功而可以出現在輸入字串中的個別字元清單。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-149">where *character_group* is a list of the individual characters that can appear in the input string for a match to succeed.</span></span> <span data-ttu-id="8d9d4-150">*character_group*可以由一或多個常值字元、[逸出字元](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md)或字元類別的任何組合所構成。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-150">*character_group* can consist of any combination of one or more literal characters, [escape characters](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md), or character classes.</span></span>  
  
 <span data-ttu-id="8d9d4-151">指定字元範圍的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="8d9d4-151">The syntax for specifying a range of characters is as follows:</span></span>  
  
```  
[firstCharacter-lastCharacter]  
```  
  
 <span data-ttu-id="8d9d4-152">其中 *firstCharacter* 是範圍開始的字元，而 *lastCharacter* 是範圍結束的字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-152">where *firstCharacter* is the character that begins the range and *lastCharacter* is the character that ends the range.</span></span> <span data-ttu-id="8d9d4-153">字元範圍是指一系列連續的字元，定義的方式是指定系列中的第一個字元、連字號 (-)，然後是系列中的最後一個字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-153">A character range is a contiguous series of characters defined by specifying the first character in the series, a hyphen (-), and then the last character in the series.</span></span> <span data-ttu-id="8d9d4-154">如果兩個字元具有相鄰的 Unicode 字碼指標，這兩個字元就是連續字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-154">Two characters are contiguous if they have adjacent Unicode code points.</span></span>  
  
 <span data-ttu-id="8d9d4-155">下表列出一些包含正字元類別的常見規則運算式模式。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-155">Some common regular expression patterns that contain positive character classes are listed in the following table.</span></span>  
  
|<span data-ttu-id="8d9d4-156">模式</span><span class="sxs-lookup"><span data-stu-id="8d9d4-156">Pattern</span></span>|<span data-ttu-id="8d9d4-157">說明</span><span class="sxs-lookup"><span data-stu-id="8d9d4-157">Description</span></span>|  
|-------------|-----------------|  
|`[aeiou]`|<span data-ttu-id="8d9d4-158">比對所有母音。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-158">Match all vowels.</span></span>|  
|`[\p{P}\d]`|<span data-ttu-id="8d9d4-159">比對所有標點符號和十進位數字字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-159">Match all punctuation and decimal digit characters.</span></span>|  
|`[\s\p{P}]`|<span data-ttu-id="8d9d4-160">比對所有空白字元與標點符號。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-160">Match all white space and punctuation.</span></span>|  
  
 <span data-ttu-id="8d9d4-161">下列範例會定義包含字元 "a" 和 "e" 的正字元群組，因此輸入字串必須包含文字 "grey" 或 "gray" 且後面接著另一個文字，才會出現相符項目。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-161">The following example defines a positive character group that contains the characters "a" and "e" so that the input string must contain the words "grey" or "gray" followed by another word for a match to occur.</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/positivecharclasses.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/positivecharclasses.vb#1)]  
  
 <span data-ttu-id="8d9d4-162">規則運算式 `gr[ae]y\s\S+?[\s|\p{P}]` 定義如下：</span><span class="sxs-lookup"><span data-stu-id="8d9d4-162">The regular expression `gr[ae]y\s\S+?[\s|\p{P}]` is defined as follows:</span></span>  
  
|<span data-ttu-id="8d9d4-163">模式</span><span class="sxs-lookup"><span data-stu-id="8d9d4-163">Pattern</span></span>|<span data-ttu-id="8d9d4-164">說明</span><span class="sxs-lookup"><span data-stu-id="8d9d4-164">Description</span></span>|  
|-------------|-----------------|  
|`gr`|<span data-ttu-id="8d9d4-165">比對常值字元 "gr"。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-165">Match the literal characters "gr".</span></span>|  
|`[ae]`|<span data-ttu-id="8d9d4-166">比對 "a" 或 "e"。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-166">Match either an "a" or an "e".</span></span>|  
|`y\s`|<span data-ttu-id="8d9d4-167">比對後面接著空白字元的常值字元 "y"。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-167">Match the literal character "y" followed by a white-space character.</span></span>|  
|`\S+?`|<span data-ttu-id="8d9d4-168">比對一個或多個非空白字元，但越少越好。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-168">Match one or more non-white-space characters, but as few as possible.</span></span>|  
|`[\s\p{P}]`|<span data-ttu-id="8d9d4-169">比對空白字元或標點符號。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-169">Match either a white-space character or a punctuation mark.</span></span>|  
  
 <span data-ttu-id="8d9d4-170">下列範例將比對以任何大寫字母開頭的文字。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-170">The following example matches words that begin with any capital letter.</span></span> <span data-ttu-id="8d9d4-171">範例將使用子運算式 `[A-Z]` 表示從 A 到 Z 的大寫字母範圍。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-171">It uses the subexpression `[A-Z]` to represent the range of capital letters from A to Z.</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/range.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/range.vb#3)]  
  
 <span data-ttu-id="8d9d4-172">規則運算式 `\b[A-Z]\w*\b` 的定義如下表所示。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-172">The regular expression `\b[A-Z]\w*\b` is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="8d9d4-173">模式</span><span class="sxs-lookup"><span data-stu-id="8d9d4-173">Pattern</span></span>|<span data-ttu-id="8d9d4-174">說明</span><span class="sxs-lookup"><span data-stu-id="8d9d4-174">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="8d9d4-175">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-175">Start at a word boundary.</span></span>|  
|`[A-Z]`|<span data-ttu-id="8d9d4-176">比對從 A 到 Z 的任何大寫字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-176">Match any uppercase character from A to Z.</span></span>|  
|`\w*`|<span data-ttu-id="8d9d4-177">比對零個或多個文字字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-177">Match zero or more word characters.</span></span>|  
|`\b`|<span data-ttu-id="8d9d4-178">比對字邊界。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-178">Match a word boundary.</span></span>|  
  
<a name="NegativeGroup"></a>   
## <a name="negative-character-group-"></a><span data-ttu-id="8d9d4-179">負字元群組：[^]</span><span class="sxs-lookup"><span data-stu-id="8d9d4-179">Negative character group: [^]</span></span>  
 <span data-ttu-id="8d9d4-180">負字元群組會指定一份字元清單，其中任何字元不得出現在輸入字串中，才會出現相符項目。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-180">A negative character group specifies a list of characters that must not appear in an input string for a match to occur.</span></span> <span data-ttu-id="8d9d4-181">字元清單可以個別指定，也可以依範圍指定，或同時依兩種方式指定。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-181">The list of characters may be specified individually, as a range, or both.</span></span>  
  
 <span data-ttu-id="8d9d4-182">指定個別字元清單的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="8d9d4-182">The syntax for specifying a list of individual characters is as follows:</span></span>  
  
 <span data-ttu-id="8d9d4-183">[*^character_group*]</span><span class="sxs-lookup"><span data-stu-id="8d9d4-183">[*^character_group*]</span></span>  
  
 <span data-ttu-id="8d9d4-184">其中 *character_group* 是為了讓比對成功而不可出現在輸入字串中的個別字元清單。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-184">where *character_group* is a list of the individual characters that cannot appear in the input string for a match to succeed.</span></span> <span data-ttu-id="8d9d4-185">*character_group*可以由一或多個常值字元、[逸出字元](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md)或字元類別的任何組合所構成。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-185">*character_group* can consist of any combination of one or more literal characters, [escape characters](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md), or character classes.</span></span>  
  
 <span data-ttu-id="8d9d4-186">指定字元範圍的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="8d9d4-186">The syntax for specifying a range of characters is as follows:</span></span>  
  
 <span data-ttu-id="8d9d4-187">[^*firstCharacter*-*lastCharacter*]</span><span class="sxs-lookup"><span data-stu-id="8d9d4-187">[^*firstCharacter*-*lastCharacter*]</span></span>  
  
 <span data-ttu-id="8d9d4-188">其中 *firstCharacter* 是範圍開始的字元，而 *lastCharacter* 是範圍結束的字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-188">where *firstCharacter* is the character that begins the range, and *lastCharacter* is the character that ends the range.</span></span> <span data-ttu-id="8d9d4-189">字元範圍是指一系列連續的字元，定義的方式是指定系列中的第一個字元、連字號 (-)，然後是系列中的最後一個字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-189">A character range is a contiguous series of characters defined by specifying the first character in the series, a hyphen (-), and then the last character in the series.</span></span> <span data-ttu-id="8d9d4-190">如果兩個字元具有相鄰的 Unicode 字碼指標，這兩個字元就是連續字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-190">Two characters are contiguous if they have adjacent Unicode code points.</span></span>  
  
 <span data-ttu-id="8d9d4-191">可以串連兩個或多個字元範圍。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-191">Two or more character ranges can be concatenated.</span></span> <span data-ttu-id="8d9d4-192">例如，若要指定從 "0" 到 "9" 的十進位數字範圍、從 "a" 到 "f" 的小寫字母範圍，以及從 "A" 到 "F" 的大寫字母範圍，可以使用 `[0-9a-fA-F]`。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-192">For example, to specify the range of decimal digits from "0" through "9", the range of lowercase letters from "a" through "f", and the range of uppercase letters from "A" through "F", use `[0-9a-fA-F]`.</span></span>  
  
 <span data-ttu-id="8d9d4-193">負字元群組中的前置 `^` 字元是必要的，它表示字元群組是負字元群組而非正字元群組。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-193">The leading carat character (`^`) in a negative character group is mandatory and indicates the character group is a negative character group instead of a positive character group.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8d9d4-194">較大規則運算式模式中的負字元群組不是零寬度的判斷提示。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-194">A negative character group in a larger regular expression pattern is not a zero-width assertion.</span></span> <span data-ttu-id="8d9d4-195">也就是說，在評估負字元群組之後，規則運算式引擎會在輸入字串中前進一個字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-195">That is, after evaluating the negative character group, the regular expression engine advances one character in the input string.</span></span>  
  
 <span data-ttu-id="8d9d4-196">下表列出一些包含負字元群組的常見規則運算式模式。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-196">Some common regular expression patterns that contain negative character groups are listed in the following table.</span></span>  
  
|<span data-ttu-id="8d9d4-197">模式</span><span class="sxs-lookup"><span data-stu-id="8d9d4-197">Pattern</span></span>|<span data-ttu-id="8d9d4-198">說明</span><span class="sxs-lookup"><span data-stu-id="8d9d4-198">Description</span></span>|  
|-------------|-----------------|  
|`[^aeiou]`|<span data-ttu-id="8d9d4-199">比對除了母音之外的所有字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-199">Match all characters except vowels.</span></span>|  
|`[^\p{P}\d]`|<span data-ttu-id="8d9d4-200">比對標點符號和十進位數字字元之外的所有字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-200">Match all characters except punctuation and decimal digit characters.</span></span>|  
  
 <span data-ttu-id="8d9d4-201">下列範例將比對任何開頭字元是 "th" 且後面不是接著 "o" 的文字。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-201">The following example matches any word that begins with the characters "th" and is not followed by an "o".</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/negativecharclasses.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/negativecharclasses.vb#2)]  
  
 <span data-ttu-id="8d9d4-202">規則運算式 `\bth[^o]\w+\b` 的定義如下表所示。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-202">The regular expression `\bth[^o]\w+\b` is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="8d9d4-203">模式</span><span class="sxs-lookup"><span data-stu-id="8d9d4-203">Pattern</span></span>|<span data-ttu-id="8d9d4-204">說明</span><span class="sxs-lookup"><span data-stu-id="8d9d4-204">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="8d9d4-205">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-205">Start at a word boundary.</span></span>|  
|`th`|<span data-ttu-id="8d9d4-206">比對常值字元 "th"。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-206">Match the literal characters "th".</span></span>|  
|`[^o]`|<span data-ttu-id="8d9d4-207">比對不是 "o" 的任何字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-207">Match any character that is not an "o".</span></span>|  
|`\w+`|<span data-ttu-id="8d9d4-208">比對一個或多個文字字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-208">Match one or more word characters.</span></span>|  
|`\b`|<span data-ttu-id="8d9d4-209">在字邊界結束。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-209">End at a word boundary.</span></span>|  
  
<a name="AnyCharacter"></a>   
## <a name="any-character-"></a><span data-ttu-id="8d9d4-210">任何字元：.</span><span class="sxs-lookup"><span data-stu-id="8d9d4-210">Any character: .</span></span>  
 <span data-ttu-id="8d9d4-211">句號字元 (.) 會比對 `\n` (新行字元 \u000A) 以外任何具有下列兩項資格的字元：</span><span class="sxs-lookup"><span data-stu-id="8d9d4-211">The period character (.) matches any character except `\n` (the newline character, \u000A), with the following two qualifications:</span></span>  
  
- <span data-ttu-id="8d9d4-212">如果 <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> 選項修改了規則運算式模式，或是 `.` 選項修改了模式中包含 `s` 字元類別的部分，`.` 就會符合任何字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-212">If a regular expression pattern is modified by the <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> option, or if the portion of the pattern that contains the `.` character class is modified by the `s` option, `.` matches any character.</span></span> <span data-ttu-id="8d9d4-213">如需詳細資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-213">For more information, see [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
     <span data-ttu-id="8d9d4-214">下列範例將示範 `.` 字元類別的預設行為與使用 <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> 選項的行為有何不同。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-214">The following example illustrates the different behavior of the `.` character class by default and with the <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> option.</span></span> <span data-ttu-id="8d9d4-215">規則運算式 `^.+` 會從字串開頭開始，比對每一個字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-215">The regular expression `^.+` starts at the beginning of the string and matches every character.</span></span> <span data-ttu-id="8d9d4-216">根據預設，比對會在第一行結尾結束。規則運算式模式會比對歸位字元 `\r` 或 \u000D，但不會比對 `\n`。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-216">By default, the match ends at the end of the first line; the regular expression pattern matches the carriage return character, `\r` or \u000D, but it does not match `\n`.</span></span> <span data-ttu-id="8d9d4-217">由於 <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> 選項會將整個輸入字串解譯為單行，因此它會比對輸入字串中的每個字元，包括 `\n`。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-217">Because the <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> option interprets the entire input string as a single line, it matches every character in the input string, including `\n`.</span></span>  
  
     [!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
     [!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]  
  
> [!NOTE]
>  <span data-ttu-id="8d9d4-218">由於它會比對 `\n` 以外的任何字元，因此 `.` 字元類別也會比對 `\r` (歸位字元 \u000D)。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-218">Because it matches any character except `\n`, the `.` character class also matches `\r` (the carriage return character, \u000D).</span></span>  
  
- <span data-ttu-id="8d9d4-219">在正或負字元群組中，句號會視為常值句號字元而非字元類別。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-219">In a positive or negative character group, a period is treated as a literal period character, and not as a character class.</span></span> <span data-ttu-id="8d9d4-220">如需詳細資訊，請參閱本主題前段的[正字元群組](#PositiveGroup)和[負字元群組](#NegativeGroup)。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-220">For more information, see [Positive Character Group](#PositiveGroup) and [Negative Character Group](#NegativeGroup) earlier in this topic.</span></span> <span data-ttu-id="8d9d4-221">下列範例將進行示範，定義包含句號字元 (`.`) 做為字元類別以及做為正字元群組成員的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-221">The following example provides an illustration by defining a regular expression that includes the period character (`.`) both as a character class and as a member of a positive character group.</span></span> <span data-ttu-id="8d9d4-222">規則運算式 `\b.*[.?!;:](\s|\z)` 會從字邊界開始比對所有字元，直到遇到包括句號的五個標點符號其中之一，然後比對空白字元或字串結尾。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-222">The regular expression `\b.*[.?!;:](\s|\z)` begins at a word boundary, matches any character until it encounters one of five punctuation marks, including a period, and then matches either a white-space character or the end of the string.</span></span>  
  
     [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any1.cs#4)]
     [!code-vb[Conceptual.RegEx.Language.CharacterClasses#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any1.vb#4)]  
  
> [!NOTE]
>  <span data-ttu-id="8d9d4-223">由於它會比對任何字元，因此如果規則運算式模式嘗試多次比對任何字元，`.` 語言項目就會經常與 lazy 數量詞搭配使用。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-223">Because it matches any character, the `.` language element is often used with a lazy quantifier if a regular expression pattern attempts to match any character multiple times.</span></span> <span data-ttu-id="8d9d4-224">如需詳細資訊，請參閱[數量詞](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-224">For more information, see [Quantifiers](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).</span></span>  
  
<a name="CategoryOrBlock"></a>   
## <a name="unicode-category-or-unicode-block-p"></a><span data-ttu-id="8d9d4-225">Unicode 類別或 Unicode 區塊：\p{}</span><span class="sxs-lookup"><span data-stu-id="8d9d4-225">Unicode category or Unicode block: \p{}</span></span>  
 <span data-ttu-id="8d9d4-226">Unicode 標準會為每個字元指派一種一般分類。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-226">The Unicode standard assigns each character a general category.</span></span> <span data-ttu-id="8d9d4-227">例如，特定字元可以是大寫字母 (以 `Lu` 分類表示)、十進位數字 (`Nd` 分類)、數學符號 (`Sm` 分類) 或段落分隔符號 (`Zl` 分類)。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-227">For example, a particular character can be an uppercase letter (represented by the `Lu` category), a decimal digit (the `Nd` category), a math symbol (the `Sm` category), or a paragraph separator (the `Zl` category).</span></span> <span data-ttu-id="8d9d4-228">Unicode 標準中的特定字元集也會佔據連續字碼指標的特定範圍或區塊。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-228">Specific character sets in the Unicode standard also occupy a specific range or block of consecutive code points.</span></span> <span data-ttu-id="8d9d4-229">例如，從 \u0000 到 \u007F 可找到基本拉丁字元集，從 \u0600 到 \u06FF 則可找到阿拉伯字元集。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-229">For example, the basic Latin character set is found from \u0000 through \u007F, while the Arabic character set is found from \u0600 through \u06FF.</span></span>  
  
 <span data-ttu-id="8d9d4-230">規則運算式建構</span><span class="sxs-lookup"><span data-stu-id="8d9d4-230">The regular expression construct</span></span>  
  
 <span data-ttu-id="8d9d4-231">`\p{` *name* `}`</span><span class="sxs-lookup"><span data-stu-id="8d9d4-231">`\p{` *name* `}`</span></span>  
  
 <span data-ttu-id="8d9d4-232">比對屬於 Unicode 一般分類或具名區塊的任何字元，其中 *name* 是分類縮寫或具名區塊名稱。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-232">matches any character that belongs to a Unicode general category or named block, where *name* is the category abbreviation or named block name.</span></span> <span data-ttu-id="8d9d4-233">如需分類縮寫的清單，請參閱本主題稍後的[支援的 Unicode 一般分類](#SupportedUnicodeGeneralCategories)一節。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-233">For a list of category abbreviations, see the [Supported Unicode General Categories](#SupportedUnicodeGeneralCategories) section later in this topic.</span></span> <span data-ttu-id="8d9d4-234">如需具名區塊清單，請參閱本主題稍後的[支援的具名區塊](#SupportedNamedBlocks)一節。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-234">For a list of named blocks, see the [Supported Named Blocks](#SupportedNamedBlocks) section later in this topic.</span></span>  
  
 <span data-ttu-id="8d9d4-235">下列範例會使用 `\p{`*name*`}` 建構同時比對 Unicode 一般類別 (在這個案例中是 `Pd`，或稱 Punctuation, Dash 分類) 以及具名區塊 (`IsGreek` 和 `IsBasicLatin` 具名區塊)。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-235">The following example uses the `\p{`*name*`}` construct to match both a Unicode general category (in this case, the `Pd`, or Punctuation, Dash category) and a named block (the `IsGreek` and `IsBasicLatin` named blocks).</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/category1.cs#6)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/category1.vb#6)]  
  
 <span data-ttu-id="8d9d4-236">規則運算式 `\b(\p{IsGreek}+(\s)?)+\p{Pd}\s(\p{IsBasicLatin}+(\s)?)+` 的定義如下表所示。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-236">The regular expression `\b(\p{IsGreek}+(\s)?)+\p{Pd}\s(\p{IsBasicLatin}+(\s)?)+` is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="8d9d4-237">模式</span><span class="sxs-lookup"><span data-stu-id="8d9d4-237">Pattern</span></span>|<span data-ttu-id="8d9d4-238">說明</span><span class="sxs-lookup"><span data-stu-id="8d9d4-238">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="8d9d4-239">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-239">Start at a word boundary.</span></span>|  
|`\p{IsGreek}+`|<span data-ttu-id="8d9d4-240">比對一個或多個希臘字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-240">Match one or more Greek characters.</span></span>|  
|`(\s)?`|<span data-ttu-id="8d9d4-241">比對零個或一個空白字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-241">Match zero or one white-space character.</span></span>|  
|`(\p{IsGreek}+(\s)?)+`|<span data-ttu-id="8d9d4-242">一次或多次比對一個或多個希臘字元後面接著零或一個空白字元的模式。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-242">Match the pattern of one or more Greek characters followed by zero or one white-space characters one or more times.</span></span>|  
|`\p{Pd}`|<span data-ttu-id="8d9d4-243">比對標點符號、虛線字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-243">Match a Punctuation, Dash character.</span></span>|  
|`\s`|<span data-ttu-id="8d9d4-244">比對空白字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-244">Match a white-space character.</span></span>|  
|`\p{IsBasicLatin}+`|<span data-ttu-id="8d9d4-245">比對一個或多個基本拉丁字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-245">Match one or more basic Latin characters.</span></span>|  
|`(\s)?`|<span data-ttu-id="8d9d4-246">比對零個或一個空白字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-246">Match zero or one white-space character.</span></span>|  
|`(\p{IsBasicLatin}+(\s)?)+`|<span data-ttu-id="8d9d4-247">一次或多次比對一個或多個基本拉丁字元後面接著零個或一個空白字元的模式。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-247">Match the pattern of one or more basic Latin characters followed by zero or one white-space characters one or more times.</span></span>|  
  
<a name="NegativeCategoryOrBlock"></a>   
## <a name="negative-unicode-category-or-unicode-block-p"></a><span data-ttu-id="8d9d4-248">負 Unicode 類別或 Unicode 區塊：\P{}</span><span class="sxs-lookup"><span data-stu-id="8d9d4-248">Negative Unicode category or Unicode block: \P{}</span></span>  
 <span data-ttu-id="8d9d4-249">Unicode 標準會為每個字元指派一種一般分類。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-249">The Unicode standard assigns each character a general category.</span></span> <span data-ttu-id="8d9d4-250">例如，特定字元可以是大寫字母 (以 `Lu` 分類表示)、十進位數字 (`Nd` 分類)、數學符號 (`Sm` 分類) 或段落分隔符號 (`Zl` 分類)。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-250">For example, a particular character can be an uppercase letter (represented by the `Lu` category), a decimal digit (the `Nd` category), a math symbol (the `Sm` category), or a paragraph separator (the `Zl` category).</span></span> <span data-ttu-id="8d9d4-251">Unicode 標準中的特定字元集也會佔據連續字碼指標的特定範圍或區塊。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-251">Specific character sets in the Unicode standard also occupy a specific range or block of consecutive code points.</span></span> <span data-ttu-id="8d9d4-252">例如，從 \u0000 到 \u007F 可找到基本拉丁字元集，從 \u0600 到 \u06FF 則可找到阿拉伯字元集。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-252">For example, the basic Latin character set is found from \u0000 through \u007F, while the Arabic character set is found from \u0600 through \u06FF.</span></span>  
  
 <span data-ttu-id="8d9d4-253">規則運算式建構</span><span class="sxs-lookup"><span data-stu-id="8d9d4-253">The regular expression construct</span></span>  
  
 <span data-ttu-id="8d9d4-254">`\P{` *name* `}`</span><span class="sxs-lookup"><span data-stu-id="8d9d4-254">`\P{` *name* `}`</span></span>  
  
 <span data-ttu-id="8d9d4-255">比對任何不屬於 Unicode 一般分類或具名區塊的字元，其中 *name* 是分類縮寫或是具名區塊名稱。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-255">matches any character that does not belong to a Unicode general category or named block, where *name* is the category abbreviation or named block name.</span></span> <span data-ttu-id="8d9d4-256">如需分類縮寫的清單，請參閱本主題稍後的[支援的 Unicode 一般分類](#SupportedUnicodeGeneralCategories)一節。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-256">For a list of category abbreviations, see the [Supported Unicode General Categories](#SupportedUnicodeGeneralCategories) section later in this topic.</span></span> <span data-ttu-id="8d9d4-257">如需具名區塊清單，請參閱本主題稍後的[支援的具名區塊](#SupportedNamedBlocks)一節。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-257">For a list of named blocks, see the [Supported Named Blocks](#SupportedNamedBlocks) section later in this topic.</span></span>  
  
 <span data-ttu-id="8d9d4-258">下列範例會使用 `\P{`*name*`}` 建構從數值字串中移除任何貨幣符號 (在這個案例中是 `Sc`，或稱 [符號、貨幣] 分類)。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-258">The following example uses the `\P{`*name*`}` construct to remove any currency symbols (in this case, the `Sc`, or Symbol, Currency category) from numeric strings.</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/notcategory1.cs#7)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/notcategory1.vb#7)]  
  
 <span data-ttu-id="8d9d4-259">規則運算式模式 `(\P{Sc})+` 會比對一個或多個不是貨幣符號的字元，並且會有效移除結果字串中的所有貨幣符號。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-259">The regular expression pattern `(\P{Sc})+` matches one or more characters that are not currency symbols; it effectively strips any currency symbol from the result string.</span></span>  
  
<a name="WordCharacter"></a>   
## <a name="word-character-w"></a><span data-ttu-id="8d9d4-260">文字字元：\w</span><span class="sxs-lookup"><span data-stu-id="8d9d4-260">Word character: \w</span></span>  
 <span data-ttu-id="8d9d4-261">`\w` 會比對任何文字字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-261">`\w` matches any word character.</span></span> <span data-ttu-id="8d9d4-262">文字字元是下表中所列的任何 Unicode 分類的成員。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-262">A word character is a member of any of the Unicode categories listed in the following table.</span></span>  
  
|<span data-ttu-id="8d9d4-263">分類</span><span class="sxs-lookup"><span data-stu-id="8d9d4-263">Category</span></span>|<span data-ttu-id="8d9d4-264">說明</span><span class="sxs-lookup"><span data-stu-id="8d9d4-264">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="8d9d4-265">Ll</span><span class="sxs-lookup"><span data-stu-id="8d9d4-265">Ll</span></span>|<span data-ttu-id="8d9d4-266">字母、小寫</span><span class="sxs-lookup"><span data-stu-id="8d9d4-266">Letter, Lowercase</span></span>|  
|<span data-ttu-id="8d9d4-267">Lu</span><span class="sxs-lookup"><span data-stu-id="8d9d4-267">Lu</span></span>|<span data-ttu-id="8d9d4-268">字母、大寫</span><span class="sxs-lookup"><span data-stu-id="8d9d4-268">Letter, Uppercase</span></span>|  
|<span data-ttu-id="8d9d4-269">Lt</span><span class="sxs-lookup"><span data-stu-id="8d9d4-269">Lt</span></span>|<span data-ttu-id="8d9d4-270">字母、字首大寫</span><span class="sxs-lookup"><span data-stu-id="8d9d4-270">Letter, Titlecase</span></span>|  
|<span data-ttu-id="8d9d4-271">Lo</span><span class="sxs-lookup"><span data-stu-id="8d9d4-271">Lo</span></span>|<span data-ttu-id="8d9d4-272">字母、其他</span><span class="sxs-lookup"><span data-stu-id="8d9d4-272">Letter, Other</span></span>|  
|<span data-ttu-id="8d9d4-273">Lm</span><span class="sxs-lookup"><span data-stu-id="8d9d4-273">Lm</span></span>|<span data-ttu-id="8d9d4-274">字母、修飾詞</span><span class="sxs-lookup"><span data-stu-id="8d9d4-274">Letter, Modifier</span></span>|  
|<span data-ttu-id="8d9d4-275">Mn</span><span class="sxs-lookup"><span data-stu-id="8d9d4-275">Mn</span></span>|<span data-ttu-id="8d9d4-276">記號，非間距</span><span class="sxs-lookup"><span data-stu-id="8d9d4-276">Mark, Nonspacing</span></span>|  
|<span data-ttu-id="8d9d4-277">Nd</span><span class="sxs-lookup"><span data-stu-id="8d9d4-277">Nd</span></span>|<span data-ttu-id="8d9d4-278">數字、十進位數字</span><span class="sxs-lookup"><span data-stu-id="8d9d4-278">Number, Decimal Digit</span></span>|  
|<span data-ttu-id="8d9d4-279">Pc</span><span class="sxs-lookup"><span data-stu-id="8d9d4-279">Pc</span></span>|<span data-ttu-id="8d9d4-280">標點符號、連接器。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-280">Punctuation, Connector.</span></span> <span data-ttu-id="8d9d4-281">這個分類包含十個字元，其中最常用的是 LOWLINE 字元 (_)，u+005F。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-281">This category includes ten characters, the most commonly used of which is the LOWLINE character (_), u+005F.</span></span>|  
  
 <span data-ttu-id="8d9d4-282">如果指定了符合 ECMAScript 的行為，`\w` 就等於 `[a-zA-Z_0-9]`。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-282">If ECMAScript-compliant behavior is specified, `\w` is equivalent to `[a-zA-Z_0-9]`.</span></span> <span data-ttu-id="8d9d4-283">如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)中的＜ECMAScript 相符行為＞一節。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-283">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d9d4-284">由於它會比對任何文字字元，因此，如果規則運算式模式嘗試多次比對任何文字字元且後面接著特定文字字元，`\w` 語言項目就會經常與 lazy 數量詞搭配使用。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-284">Because it matches any word character, the `\w` language element is often used with a lazy quantifier if a regular expression pattern attempts to match any word character multiple times, followed by a specific word character.</span></span> <span data-ttu-id="8d9d4-285">如需詳細資訊，請參閱[數量詞](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-285">For more information, see [Quantifiers](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="8d9d4-286">下列範例會使用 `\w` 語言項目比對文字中重複的字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-286">The following example uses the `\w` language element to match duplicate characters in a word.</span></span> <span data-ttu-id="8d9d4-287">這個範例會定義規則運算式模式 `(\w)\1`，該模式解譯如下。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-287">The example defines a regular expression pattern, `(\w)\1`, which can be interpreted as follows.</span></span>  
  
|<span data-ttu-id="8d9d4-288">元素</span><span class="sxs-lookup"><span data-stu-id="8d9d4-288">Element</span></span>|<span data-ttu-id="8d9d4-289">說明</span><span class="sxs-lookup"><span data-stu-id="8d9d4-289">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8d9d4-290">(\w)</span><span class="sxs-lookup"><span data-stu-id="8d9d4-290">(\w)</span></span>|<span data-ttu-id="8d9d4-291">比對文字字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-291">Match a word character.</span></span> <span data-ttu-id="8d9d4-292">這是第一個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-292">This is the first capturing group.</span></span>|  
|<span data-ttu-id="8d9d4-293">\1</span><span class="sxs-lookup"><span data-stu-id="8d9d4-293">\1</span></span>|<span data-ttu-id="8d9d4-294">比對第一個擷取的值。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-294">Match the value of the first capture.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/wordchar1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/wordchar1.vb#8)]  
  
<a name="NonWordCharacter"></a>   
## <a name="non-word-character-w"></a><span data-ttu-id="8d9d4-295">非文字字元：\W</span><span class="sxs-lookup"><span data-stu-id="8d9d4-295">Non-word character: \W</span></span>  
 <span data-ttu-id="8d9d4-296">`\W` 會比對任何非文字字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-296">`\W` matches any non-word character.</span></span> <span data-ttu-id="8d9d4-297">\W 語言項目相當於下列字元類別：</span><span class="sxs-lookup"><span data-stu-id="8d9d4-297">The \W language element is equivalent to the following character class:</span></span>  
  
```  
[^\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]  
```  
  
 <span data-ttu-id="8d9d4-298">換句話說，它會比對下表所列 Unicode 分類中字元以外的所有字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-298">In other words, it matches any character except for those in the Unicode categories listed in the following table.</span></span>  
  
|<span data-ttu-id="8d9d4-299">分類</span><span class="sxs-lookup"><span data-stu-id="8d9d4-299">Category</span></span>|<span data-ttu-id="8d9d4-300">說明</span><span class="sxs-lookup"><span data-stu-id="8d9d4-300">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="8d9d4-301">Ll</span><span class="sxs-lookup"><span data-stu-id="8d9d4-301">Ll</span></span>|<span data-ttu-id="8d9d4-302">字母、小寫</span><span class="sxs-lookup"><span data-stu-id="8d9d4-302">Letter, Lowercase</span></span>|  
|<span data-ttu-id="8d9d4-303">Lu</span><span class="sxs-lookup"><span data-stu-id="8d9d4-303">Lu</span></span>|<span data-ttu-id="8d9d4-304">字母、大寫</span><span class="sxs-lookup"><span data-stu-id="8d9d4-304">Letter, Uppercase</span></span>|  
|<span data-ttu-id="8d9d4-305">Lt</span><span class="sxs-lookup"><span data-stu-id="8d9d4-305">Lt</span></span>|<span data-ttu-id="8d9d4-306">字母、字首大寫</span><span class="sxs-lookup"><span data-stu-id="8d9d4-306">Letter, Titlecase</span></span>|  
|<span data-ttu-id="8d9d4-307">Lo</span><span class="sxs-lookup"><span data-stu-id="8d9d4-307">Lo</span></span>|<span data-ttu-id="8d9d4-308">字母、其他</span><span class="sxs-lookup"><span data-stu-id="8d9d4-308">Letter, Other</span></span>|  
|<span data-ttu-id="8d9d4-309">Lm</span><span class="sxs-lookup"><span data-stu-id="8d9d4-309">Lm</span></span>|<span data-ttu-id="8d9d4-310">字母、修飾詞</span><span class="sxs-lookup"><span data-stu-id="8d9d4-310">Letter, Modifier</span></span>|  
|<span data-ttu-id="8d9d4-311">Mn</span><span class="sxs-lookup"><span data-stu-id="8d9d4-311">Mn</span></span>|<span data-ttu-id="8d9d4-312">記號，非間距</span><span class="sxs-lookup"><span data-stu-id="8d9d4-312">Mark, Nonspacing</span></span>|  
|<span data-ttu-id="8d9d4-313">Nd</span><span class="sxs-lookup"><span data-stu-id="8d9d4-313">Nd</span></span>|<span data-ttu-id="8d9d4-314">數字、十進位數字</span><span class="sxs-lookup"><span data-stu-id="8d9d4-314">Number, Decimal Digit</span></span>|  
|<span data-ttu-id="8d9d4-315">Pc</span><span class="sxs-lookup"><span data-stu-id="8d9d4-315">Pc</span></span>|<span data-ttu-id="8d9d4-316">標點符號、連接器。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-316">Punctuation, Connector.</span></span> <span data-ttu-id="8d9d4-317">這個分類包含十個字元，其中最常用的是 LOWLINE 字元 (_)，u+005F。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-317">This category includes ten characters, the most commonly used of which is the LOWLINE character (_), u+005F.</span></span>|  
  
 <span data-ttu-id="8d9d4-318">如果指定了符合 ECMAScript 的行為，`\W` 就等於 `[^a-zA-Z_0-9]`。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-318">If ECMAScript-compliant behavior is specified, `\W` is equivalent to `[^a-zA-Z_0-9]`.</span></span> <span data-ttu-id="8d9d4-319">如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)中的＜ECMAScript 相符行為＞一節。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-319">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d9d4-320">由於它會比對任何非文字字元，因此，如果規則運算式模式嘗試多次比對任何非文字字元，且後面接著特定非文字字元，`\W` 語言項目就會經常與 lazy 數量詞搭配使用。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-320">Because it matches any non-word character, the `\W` language element is often used with a lazy quantifier if a regular expression pattern attempts to match any non-word character multiple times followed by a specific non-word character.</span></span> <span data-ttu-id="8d9d4-321">如需詳細資訊，請參閱[數量詞](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-321">For more information, see [Quantifiers](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="8d9d4-322">以下範例將說明 `\W` 字元類別。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-322">The following example illustrates the `\W` character class.</span></span>  <span data-ttu-id="8d9d4-323">它會定義規則運算式模式 `\b(\w+)(\W){1,2}`，該模式會比對後面接一個或多個非文字字元的文字，例如空白字元或標點符號。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-323">It defines a regular expression pattern, `\b(\w+)(\W){1,2}`, that matches a word followed by one or two non-word characters, such as white space or punctuation.</span></span> <span data-ttu-id="8d9d4-324">規則運算式的解譯方式如下表所示。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-324">The regular expression is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="8d9d4-325">元素</span><span class="sxs-lookup"><span data-stu-id="8d9d4-325">Element</span></span>|<span data-ttu-id="8d9d4-326">說明</span><span class="sxs-lookup"><span data-stu-id="8d9d4-326">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8d9d4-327">\b</span><span class="sxs-lookup"><span data-stu-id="8d9d4-327">\b</span></span>|<span data-ttu-id="8d9d4-328">開始字緣比對。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-328">Begin the match at a word boundary.</span></span>|  
|<span data-ttu-id="8d9d4-329">(\w+)</span><span class="sxs-lookup"><span data-stu-id="8d9d4-329">(\w+)</span></span>|<span data-ttu-id="8d9d4-330">比對一個或多個文字字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-330">Match one or more word characters.</span></span> <span data-ttu-id="8d9d4-331">這是第一個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-331">This is the first capturing group.</span></span>|  
|<span data-ttu-id="8d9d4-332">(\W){1,2}</span><span class="sxs-lookup"><span data-stu-id="8d9d4-332">(\W){1,2}</span></span>|<span data-ttu-id="8d9d4-333">比對一次或兩次非文字字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-333">Match a non-word character either one or two times.</span></span> <span data-ttu-id="8d9d4-334">這是第二個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-334">This is the second capturing group.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nonwordchar1.cs#9)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nonwordchar1.vb#9)]  
  
 <span data-ttu-id="8d9d4-335">由於第二個擷取群組的 <xref:System.Text.RegularExpressions.Group> 物件只包含單一擷取的非文字字元，因此這個範例會從 <xref:System.Text.RegularExpressions.CaptureCollection> 屬性所傳回之 <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> 物件擷取所有擷取的非文字字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-335">Because the <xref:System.Text.RegularExpressions.Group> object for the second capturing group contains only a single captured non-word character, the example retrieves all captured non-word characters from the <xref:System.Text.RegularExpressions.CaptureCollection> object that is returned by the <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> property.</span></span>  
  
<a name="WhitespaceCharacter"></a>   
## <a name="whitespace-character-s"></a><span data-ttu-id="8d9d4-336">空白字元：\s</span><span class="sxs-lookup"><span data-stu-id="8d9d4-336">Whitespace character: \s</span></span>  
 <span data-ttu-id="8d9d4-337">`\s` 會比對任何空白字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-337">`\s` matches any whitespace character.</span></span> <span data-ttu-id="8d9d4-338">它相當於下表列出的逸出序列和 Unicode 分類。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-338">It is equivalent to the escape sequences and Unicode categories listed in the following table.</span></span>  
  
|<span data-ttu-id="8d9d4-339">分類</span><span class="sxs-lookup"><span data-stu-id="8d9d4-339">Category</span></span>|<span data-ttu-id="8d9d4-340">說明</span><span class="sxs-lookup"><span data-stu-id="8d9d4-340">Description</span></span>|  
|--------------|-----------------|  
|`\f`|<span data-ttu-id="8d9d4-341">換頁字元 \u000C。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-341">The form feed character, \u000C.</span></span>|  
|`\n`|<span data-ttu-id="8d9d4-342">新行字元 \u000A。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-342">The newline character, \u000A.</span></span>|  
|`\r`|<span data-ttu-id="8d9d4-343">歸位字元 \u000D。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-343">The carriage return character, \u000D.</span></span>|  
|`\t`|<span data-ttu-id="8d9d4-344">定位字元 \u0009。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-344">The tab character, \u0009.</span></span>|  
|`\v`|<span data-ttu-id="8d9d4-345">垂直定位字元 \u000B。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-345">The vertical tab character, \u000B.</span></span>|  
|`\x85`|<span data-ttu-id="8d9d4-346">省略符號或 NEXT LINE (NEL) 字元 (…) \u0085。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-346">The ellipsis or NEXT LINE (NEL) character (…), \u0085.</span></span>|  
|`\p{Z}`|<span data-ttu-id="8d9d4-347">比對任何分隔符號字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-347">Matches any separator character.</span></span>|  
  
 <span data-ttu-id="8d9d4-348">如果指定了符合 ECMAScript 的行為，`\s` 就等於 `[ \f\n\r\t\v]`。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-348">If ECMAScript-compliant behavior is specified, `\s` is equivalent to `[ \f\n\r\t\v]`.</span></span> <span data-ttu-id="8d9d4-349">如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)中的＜ECMAScript 相符行為＞一節。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-349">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
 <span data-ttu-id="8d9d4-350">以下範例將說明 `\s` 字元類別。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-350">The following example illustrates the `\s` character class.</span></span> <span data-ttu-id="8d9d4-351">它會定義規則運算式模式 `\b\w+(e)?s(\s|$)`，該模式會比對結尾為 "s" 或 "es" 且後面加上空白字元或是輸入字串結尾的文字。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-351">It defines a regular expression pattern, `\b\w+(e)?s(\s|$)`, that matches a word ending in either "s" or "es" followed by either a white-space character or the end of the input string.</span></span> <span data-ttu-id="8d9d4-352">規則運算式的解譯方式如下表所示。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-352">The regular expression is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="8d9d4-353">元素</span><span class="sxs-lookup"><span data-stu-id="8d9d4-353">Element</span></span>|<span data-ttu-id="8d9d4-354">說明</span><span class="sxs-lookup"><span data-stu-id="8d9d4-354">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8d9d4-355">\b</span><span class="sxs-lookup"><span data-stu-id="8d9d4-355">\b</span></span>|<span data-ttu-id="8d9d4-356">開始字緣比對。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-356">Begin the match at a word boundary.</span></span>|  
|<span data-ttu-id="8d9d4-357">\w+</span><span class="sxs-lookup"><span data-stu-id="8d9d4-357">\w+</span></span>|<span data-ttu-id="8d9d4-358">比對一個或多個文字字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-358">Match one or more word characters.</span></span>|  
|<span data-ttu-id="8d9d4-359">(e)?</span><span class="sxs-lookup"><span data-stu-id="8d9d4-359">(e)?</span></span>|<span data-ttu-id="8d9d4-360">比對 "e" 零次或一次。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-360">Match an "e" either zero or one time.</span></span>|  
|<span data-ttu-id="8d9d4-361">秒</span><span class="sxs-lookup"><span data-stu-id="8d9d4-361">s</span></span>|<span data-ttu-id="8d9d4-362">比對 "s"。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-362">Match an "s".</span></span>|  
|<span data-ttu-id="8d9d4-363">(\s&#124;$)</span><span class="sxs-lookup"><span data-stu-id="8d9d4-363">(\s&#124;$)</span></span>|<span data-ttu-id="8d9d4-364">比對空白字元或輸入字串的結尾。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-364">Match either a white-space character or the end of the input string.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/whitespace1.cs#10)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/whitespace1.vb#10)]  
  
<a name="NonWhitespaceCharacter"></a>   
## <a name="non-whitespace-character-s"></a><span data-ttu-id="8d9d4-365">非空白字元：\S</span><span class="sxs-lookup"><span data-stu-id="8d9d4-365">Non-whitespace character: \S</span></span>  
 <span data-ttu-id="8d9d4-366">`\S` 會比對任何非空白字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-366">`\S` matches any non-white-space character.</span></span> <span data-ttu-id="8d9d4-367">它相當於 `[^\f\n\r\t\v\x85\p{Z}]` 規則運算式模式，或是規則運算式模式的相反模式，相當於會比對空白字元的 `\s`。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-367">It is equivalent to the `[^\f\n\r\t\v\x85\p{Z}]` regular expression pattern, or the opposite of the regular expression pattern that is equivalent to `\s`, which matches white-space characters.</span></span> <span data-ttu-id="8d9d4-368">如需詳細資訊，請參閱[空白字元：\s](#WhitespaceCharacter)。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-368">For more information, see [White-Space Character: \s](#WhitespaceCharacter).</span></span>  
  
 <span data-ttu-id="8d9d4-369">如果指定了符合 ECMAScript 的行為，`\S` 就等於 `[^ \f\n\r\t\v]`。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-369">If ECMAScript-compliant behavior is specified, `\S` is equivalent to  `[^ \f\n\r\t\v]`.</span></span> <span data-ttu-id="8d9d4-370">如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)中的＜ECMAScript 相符行為＞一節。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-370">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
 <span data-ttu-id="8d9d4-371">下列範例將說明 `\S` 語言項目。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-371">The following example illustrates the `\S` language element.</span></span> <span data-ttu-id="8d9d4-372">規則運算式模式 `\b(\S+)\s?` 會比對以空白字元分隔的字串。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-372">The regular expression pattern `\b(\S+)\s?` matches strings that are delimited by white-space characters.</span></span> <span data-ttu-id="8d9d4-373">在比對之 <xref:System.Text.RegularExpressions.GroupCollection> 物件中的第二個項目包含相符的字串。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-373">The second element in the match's <xref:System.Text.RegularExpressions.GroupCollection> object contains the matched string.</span></span> <span data-ttu-id="8d9d4-374">規則運算式的解譯方式如下表所示。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-374">The regular expression can be interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="8d9d4-375">元素</span><span class="sxs-lookup"><span data-stu-id="8d9d4-375">Element</span></span>|<span data-ttu-id="8d9d4-376">說明</span><span class="sxs-lookup"><span data-stu-id="8d9d4-376">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="8d9d4-377">開始字緣比對。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-377">Begin the match at a word boundary.</span></span>|  
|`(\S+)`|<span data-ttu-id="8d9d4-378">比對一個或多個非空白字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-378">Match one or more non-white-space characters.</span></span> <span data-ttu-id="8d9d4-379">這是第一個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-379">This is the first capturing group.</span></span>|  
|`\s?`|<span data-ttu-id="8d9d4-380">比對零個或一個空白字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-380">Match zero or one white-space character.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nonwhitespace1.cs#11)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nonwhitespace1.vb#11)]  
  
<a name="DigitCharacter"></a>   
## <a name="decimal-digit-character-d"></a><span data-ttu-id="8d9d4-381">十進位數字字元：\d</span><span class="sxs-lookup"><span data-stu-id="8d9d4-381">Decimal digit character: \d</span></span>  
 <span data-ttu-id="8d9d4-382">`\d` 會比對任何十進位數字。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-382">`\d` matches any decimal digit.</span></span> <span data-ttu-id="8d9d4-383">它相當於 `\p{Nd}` 規則運算式模式，其中包括標準的十進位數字 0-9，以及若干其他字元集的十進位數字。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-383">It is equivalent to the `\p{Nd}` regular expression pattern, which includes the standard decimal digits 0-9 as well as the decimal digits of a number of other character sets.</span></span>  
  
 <span data-ttu-id="8d9d4-384">如果指定了符合 ECMAScript 的行為，`\d` 就等於 `[0-9]`。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-384">If ECMAScript-compliant behavior is specified, `\d` is equivalent to  `[0-9]`.</span></span> <span data-ttu-id="8d9d4-385">如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)中的＜ECMAScript 相符行為＞一節。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-385">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
 <span data-ttu-id="8d9d4-386">下列範例將說明 `\d` 語言項目。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-386">The following example illustrates the `\d` language element.</span></span> <span data-ttu-id="8d9d4-387">它會測試輸入字串是否表示美國和加拿大的有效電話號碼。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-387">It tests whether an input string represents a valid telephone number in the United States and Canada.</span></span> <span data-ttu-id="8d9d4-388">規則運算式模式 `^(\(?\d{3}\)?[\s-])?\d{3}-\d{4}$` 的定義如下表所示。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-388">The regular expression pattern `^(\(?\d{3}\)?[\s-])?\d{3}-\d{4}$` is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="8d9d4-389">項目</span><span class="sxs-lookup"><span data-stu-id="8d9d4-389">Element</span></span>|<span data-ttu-id="8d9d4-390">說明</span><span class="sxs-lookup"><span data-stu-id="8d9d4-390">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="8d9d4-391">在輸入字串的開頭開始比對。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-391">Begin the match at the beginning of the input string.</span></span>|  
|`\(?`|<span data-ttu-id="8d9d4-392">比對零個或一個常值 "(" 字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-392">Match zero or one literal "(" character.</span></span>|  
|`\d{3}`|<span data-ttu-id="8d9d4-393">比對三個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-393">Match three decimal digits.</span></span>|  
|`\)?`|<span data-ttu-id="8d9d4-394">比對零個或一個常值 ")" 字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-394">Match zero or one literal ")" character.</span></span>|  
|`[\s-]`|<span data-ttu-id="8d9d4-395">比對連字號或空白字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-395">Match a hyphen or a white-space character.</span></span>|  
|`(\(?\d{3}\)?[\s-])?`|<span data-ttu-id="8d9d4-396">比對零次或一次選擇性的左括號，後面接著三個十進位數字、選擇性的右括號，以及空白字元或是連字號。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-396">Match an optional opening parenthesis followed by three decimal digits, an optional closing parenthesis, and either a white-space character or a hyphen zero or one time.</span></span> <span data-ttu-id="8d9d4-397">這是第一個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-397">This is the first capturing group.</span></span>|  
|`\d{3}-\d{4}`|<span data-ttu-id="8d9d4-398">比對三個十進位數字，後面接著連字號和另外四個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-398">Match three decimal digits followed by a hyphen and four more decimal digits.</span></span>|  
|`$`|<span data-ttu-id="8d9d4-399">比對輸入字串的結尾。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-399">Match the end of the input string.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/digit1.cs#12)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/digit1.vb#12)]  
  
<a name="NonDigitCharacter"></a>   
## <a name="non-digit-character-d"></a><span data-ttu-id="8d9d4-400">非數字字元：\D</span><span class="sxs-lookup"><span data-stu-id="8d9d4-400">Non-digit character: \D</span></span>  
 <span data-ttu-id="8d9d4-401">`\D` 會比對任何非數字字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-401">`\D` matches any non-digit character.</span></span> <span data-ttu-id="8d9d4-402">它相當於 `\P{Nd}` 規則運算式模式。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-402">It is equivalent to the `\P{Nd}` regular expression pattern.</span></span>  
  
 <span data-ttu-id="8d9d4-403">如果指定了符合 ECMAScript 的行為，`\D` 就等於 `[^0-9]`。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-403">If ECMAScript-compliant behavior is specified, `\D` is equivalent to  `[^0-9]`.</span></span> <span data-ttu-id="8d9d4-404">如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)中的＜ECMAScript 相符行為＞一節。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-404">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
 <span data-ttu-id="8d9d4-405">下列範例將說明 \D 語言項目。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-405">The following example illustrates the \D language element.</span></span> <span data-ttu-id="8d9d4-406">它會測試像是組件編號這類字串，是否由十進位和非十進位字元的適當組合所構成。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-406">It tests whether a string such as a part number consists of the appropriate combination of decimal and non-decimal characters.</span></span> <span data-ttu-id="8d9d4-407">規則運算式模式 `^\D\d{1,5}\D*$` 的定義如下表所示。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-407">The regular expression pattern `^\D\d{1,5}\D*$` is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="8d9d4-408">項目</span><span class="sxs-lookup"><span data-stu-id="8d9d4-408">Element</span></span>|<span data-ttu-id="8d9d4-409">說明</span><span class="sxs-lookup"><span data-stu-id="8d9d4-409">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="8d9d4-410">在輸入字串的開頭開始比對。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-410">Begin the match at the beginning of the input string.</span></span>|  
|`\D`|<span data-ttu-id="8d9d4-411">比對非數字字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-411">Match a non-digit character.</span></span>|  
|`\d{1,5}`|<span data-ttu-id="8d9d4-412">比對從一個到五個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-412">Match from one to five decimal digits.</span></span>|  
|`\D*`|<span data-ttu-id="8d9d4-413">比對零個、一個或更多非十進位字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-413">Match zero, one, or more non-decimal characters.</span></span>|  
|`$`|<span data-ttu-id="8d9d4-414">比對輸入字串的結尾。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-414">Match the end of the input string.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nondigit1.cs#13)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nondigit1.vb#13)]  
  
<a name="SupportedUnicodeGeneralCategories"></a>   
## <a name="supported-unicode-general-categories"></a><span data-ttu-id="8d9d4-415">支援的 Unicode 一般分類</span><span class="sxs-lookup"><span data-stu-id="8d9d4-415">Supported Unicode general categories</span></span>  
 <span data-ttu-id="8d9d4-416">Unicode 定義了下表中所列的一般類別。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-416">Unicode defines the general categories listed in the following table.</span></span> <span data-ttu-id="8d9d4-417">如需詳細資訊，請參閱 [Unicode Character Database](https://www.unicode.org/reports/tr44/) 中的 "UCD File Format" 和 "General Category Values" 副標題。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-417">For more information, see the "UCD File Format" and "General Category Values" subtopics at the [Unicode Character Database](https://www.unicode.org/reports/tr44/).</span></span>  
  
|<span data-ttu-id="8d9d4-418">分類</span><span class="sxs-lookup"><span data-stu-id="8d9d4-418">Category</span></span>|<span data-ttu-id="8d9d4-419">說明</span><span class="sxs-lookup"><span data-stu-id="8d9d4-419">Description</span></span>|  
|--------------|-----------------|  
|`Lu`|<span data-ttu-id="8d9d4-420">字母、大寫</span><span class="sxs-lookup"><span data-stu-id="8d9d4-420">Letter, Uppercase</span></span>|  
|`Ll`|<span data-ttu-id="8d9d4-421">字母、小寫</span><span class="sxs-lookup"><span data-stu-id="8d9d4-421">Letter, Lowercase</span></span>|  
|`Lt`|<span data-ttu-id="8d9d4-422">字母、字首大寫</span><span class="sxs-lookup"><span data-stu-id="8d9d4-422">Letter, Titlecase</span></span>|  
|`Lm`|<span data-ttu-id="8d9d4-423">字母、修飾詞</span><span class="sxs-lookup"><span data-stu-id="8d9d4-423">Letter, Modifier</span></span>|  
|`Lo`|<span data-ttu-id="8d9d4-424">字母、其他</span><span class="sxs-lookup"><span data-stu-id="8d9d4-424">Letter, Other</span></span>|  
|`L`|<span data-ttu-id="8d9d4-425">所有字母字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-425">All letter characters.</span></span> <span data-ttu-id="8d9d4-426">這包括 `Lu`、`Ll`、`Lt`、`Lm` 和 `Lo` 字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-426">This includes the `Lu`, `Ll`, `Lt`, `Lm`, and `Lo` characters.</span></span>|  
|`Mn`|<span data-ttu-id="8d9d4-427">記號，非間距</span><span class="sxs-lookup"><span data-stu-id="8d9d4-427">Mark, Nonspacing</span></span>|  
|`Mc`|<span data-ttu-id="8d9d4-428">記號，間距組合</span><span class="sxs-lookup"><span data-stu-id="8d9d4-428">Mark, Spacing Combining</span></span>|  
|`Me`|<span data-ttu-id="8d9d4-429">記號，封入</span><span class="sxs-lookup"><span data-stu-id="8d9d4-429">Mark, Enclosing</span></span>|  
|`M`|<span data-ttu-id="8d9d4-430">所有變音符號記號。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-430">All diacritic marks.</span></span> <span data-ttu-id="8d9d4-431">這包括 `Mn`、`Mc` 和 `Me` 分類。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-431">This includes the `Mn`, `Mc`, and `Me` categories.</span></span>|  
|`Nd`|<span data-ttu-id="8d9d4-432">數字、十進位數字</span><span class="sxs-lookup"><span data-stu-id="8d9d4-432">Number, Decimal Digit</span></span>|  
|`Nl`|<span data-ttu-id="8d9d4-433">數字，字母</span><span class="sxs-lookup"><span data-stu-id="8d9d4-433">Number, Letter</span></span>|  
|`No`|<span data-ttu-id="8d9d4-434">數字，其他</span><span class="sxs-lookup"><span data-stu-id="8d9d4-434">Number, Other</span></span>|  
|`N`|<span data-ttu-id="8d9d4-435">所有數字。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-435">All numbers.</span></span> <span data-ttu-id="8d9d4-436">這包括 `Nd`、`Nl` 和 `No` 分類。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-436">This includes the `Nd`, `Nl`, and `No` categories.</span></span>|  
|`Pc`|<span data-ttu-id="8d9d4-437">標點符號，連接器</span><span class="sxs-lookup"><span data-stu-id="8d9d4-437">Punctuation, Connector</span></span>|  
|`Pd`|<span data-ttu-id="8d9d4-438">標點符號，破折號</span><span class="sxs-lookup"><span data-stu-id="8d9d4-438">Punctuation, Dash</span></span>|  
|`Ps`|<span data-ttu-id="8d9d4-439">標點符號，左括號</span><span class="sxs-lookup"><span data-stu-id="8d9d4-439">Punctuation, Open</span></span>|  
|`Pe`|<span data-ttu-id="8d9d4-440">標點符號，右括號</span><span class="sxs-lookup"><span data-stu-id="8d9d4-440">Punctuation, Close</span></span>|  
|`Pi`|<span data-ttu-id="8d9d4-441">標點符號，左引號 (根據使用方式，作用可能像 Ps 或 Pe)</span><span class="sxs-lookup"><span data-stu-id="8d9d4-441">Punctuation, Initial quote (may behave like Ps or Pe depending on usage)</span></span>|  
|`Pf`|<span data-ttu-id="8d9d4-442">標點符號，右引號 (根據使用方式，作用可能像 Ps 或 Pe)</span><span class="sxs-lookup"><span data-stu-id="8d9d4-442">Punctuation, Final quote (may behave like Ps or Pe depending on usage)</span></span>|  
|`Po`|<span data-ttu-id="8d9d4-443">標點符號，其他</span><span class="sxs-lookup"><span data-stu-id="8d9d4-443">Punctuation, Other</span></span>|  
|`P`|<span data-ttu-id="8d9d4-444">所有標點符號字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-444">All punctuation characters.</span></span> <span data-ttu-id="8d9d4-445">這包括 `Pc`、`Pd`、`Ps`、`Pe`、`Pi`、`Pf` 和 `Po` 分類。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-445">This includes the `Pc`, `Pd`, `Ps`, `Pe`, `Pi`, `Pf`, and `Po` categories.</span></span>|  
|`Sm`|<span data-ttu-id="8d9d4-446">符號，數學</span><span class="sxs-lookup"><span data-stu-id="8d9d4-446">Symbol, Math</span></span>|  
|`Sc`|<span data-ttu-id="8d9d4-447">符號，貨幣</span><span class="sxs-lookup"><span data-stu-id="8d9d4-447">Symbol, Currency</span></span>|  
|`Sk`|<span data-ttu-id="8d9d4-448">符號，修飾詞</span><span class="sxs-lookup"><span data-stu-id="8d9d4-448">Symbol, Modifier</span></span>|  
|`So`|<span data-ttu-id="8d9d4-449">符號，其他</span><span class="sxs-lookup"><span data-stu-id="8d9d4-449">Symbol, Other</span></span>|  
|`S`|<span data-ttu-id="8d9d4-450">所有符號。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-450">All symbols.</span></span> <span data-ttu-id="8d9d4-451">這包括 `Sm`、`Sc`、`Sk` 和 `So` 分類。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-451">This includes the `Sm`, `Sc`, `Sk`, and `So` categories.</span></span>|  
|`Zs`|<span data-ttu-id="8d9d4-452">分隔符號，空格</span><span class="sxs-lookup"><span data-stu-id="8d9d4-452">Separator, Space</span></span>|  
|`Zl`|<span data-ttu-id="8d9d4-453">分隔符號，行</span><span class="sxs-lookup"><span data-stu-id="8d9d4-453">Separator, Line</span></span>|  
|`Zp`|<span data-ttu-id="8d9d4-454">分隔符號，段落</span><span class="sxs-lookup"><span data-stu-id="8d9d4-454">Separator, Paragraph</span></span>|  
|`Z`|<span data-ttu-id="8d9d4-455">所有分隔符號字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-455">All separator characters.</span></span> <span data-ttu-id="8d9d4-456">這包括 `Zs`、`Zl` 和 `Zp` 分類。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-456">This includes the `Zs`, `Zl`, and `Zp` categories.</span></span>|  
|`Cc`|<span data-ttu-id="8d9d4-457">其他，控制</span><span class="sxs-lookup"><span data-stu-id="8d9d4-457">Other, Control</span></span>|  
|`Cf`|<span data-ttu-id="8d9d4-458">其他，格式</span><span class="sxs-lookup"><span data-stu-id="8d9d4-458">Other, Format</span></span>|  
|`Cs`|<span data-ttu-id="8d9d4-459">其他，Surrogate</span><span class="sxs-lookup"><span data-stu-id="8d9d4-459">Other, Surrogate</span></span>|  
|`Co`|<span data-ttu-id="8d9d4-460">其他，專用</span><span class="sxs-lookup"><span data-stu-id="8d9d4-460">Other, Private Use</span></span>|  
|`Cn`|<span data-ttu-id="8d9d4-461">其他，未指派 (沒有字元擁有這個屬性)</span><span class="sxs-lookup"><span data-stu-id="8d9d4-461">Other, Not Assigned (no characters have this property)</span></span>|  
|`C`|<span data-ttu-id="8d9d4-462">所有控制字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-462">All control characters.</span></span> <span data-ttu-id="8d9d4-463">這包括 `Cc`、`Cf`、`Cs`、`Co` 和 `Cn` 分類。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-463">This includes the `Cc`, `Cf`, `Cs`, `Co`, and `Cn` categories.</span></span>|  
  
 <span data-ttu-id="8d9d4-464">您可以將任何特殊字元傳遞到 <xref:System.Char.GetUnicodeCategory%2A> 方法，以判斷該字元的 Unicode 分類。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-464">You can determine the Unicode category of any particular character by passing that character to the <xref:System.Char.GetUnicodeCategory%2A> method.</span></span> <span data-ttu-id="8d9d4-465">下列範例會使用 <xref:System.Char.GetUnicodeCategory%2A> 方法判斷包含所選取拉丁字元的陣列中，每個項目的分類。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-465">The following example uses the <xref:System.Char.GetUnicodeCategory%2A> method to determine the category of each element in an array that contains selected Latin characters.</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/getunicodecategory1.cs#14)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/getunicodecategory1.vb#14)]  
  
<a name="SupportedNamedBlocks"></a>   
## <a name="supported-named-blocks"></a><span data-ttu-id="8d9d4-466">支援的具名區塊</span><span class="sxs-lookup"><span data-stu-id="8d9d4-466">Supported named blocks</span></span>

<span data-ttu-id="8d9d4-467">.NET 提供下表所列的具名區塊。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-467">.NET provides the named blocks listed in the following table.</span></span> <span data-ttu-id="8d9d4-468">這一組支援的具名區塊是根據 Unicode 4.0 和 Perl 5.6。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-468">The set of supported named blocks is based on Unicode 4.0 and Perl 5.6.</span></span> <span data-ttu-id="8d9d4-469">針對使用具名區塊的規則運算式，請參閱 [Unicode 類別或 Unicode 區塊：\\p{}](#unicode-category-or-unicode-block-p) 一節。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-469">For a regular expression that uses named blocks, see the [Unicode category or Unicode block: \\p{}](#unicode-category-or-unicode-block-p) section.</span></span>  
  
|<span data-ttu-id="8d9d4-470">字碼指標範圍</span><span class="sxs-lookup"><span data-stu-id="8d9d4-470">Code point range</span></span>|<span data-ttu-id="8d9d4-471">區塊名稱</span><span class="sxs-lookup"><span data-stu-id="8d9d4-471">Block name</span></span>|  
|----------------------|----------------|  
|<span data-ttu-id="8d9d4-472">0000 - 007F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-472">0000 - 007F</span></span>|`IsBasicLatin`|  
|<span data-ttu-id="8d9d4-473">0080 - 00FF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-473">0080 - 00FF</span></span>|`IsLatin-1Supplement`|  
|<span data-ttu-id="8d9d4-474">0100 - 017F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-474">0100 - 017F</span></span>|`IsLatinExtended-A`|  
|<span data-ttu-id="8d9d4-475">0180 - 024F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-475">0180 - 024F</span></span>|`IsLatinExtended-B`|  
|<span data-ttu-id="8d9d4-476">0250 - 02AF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-476">0250 - 02AF</span></span>|`IsIPAExtensions`|  
|<span data-ttu-id="8d9d4-477">02B0 - 02FF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-477">02B0 - 02FF</span></span>|`IsSpacingModifierLetters`|  
|<span data-ttu-id="8d9d4-478">0300 - 036F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-478">0300 - 036F</span></span>|`IsCombiningDiacriticalMarks`|  
|<span data-ttu-id="8d9d4-479">0370 - 03FF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-479">0370 - 03FF</span></span>|`IsGreek`<br /><br /> <span data-ttu-id="8d9d4-480">-或-</span><span class="sxs-lookup"><span data-stu-id="8d9d4-480">-or-</span></span><br /><br /> `IsGreekandCoptic`|  
|<span data-ttu-id="8d9d4-481">0400 - 04FF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-481">0400 - 04FF</span></span>|`IsCyrillic`|  
|<span data-ttu-id="8d9d4-482">0500 - 052F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-482">0500 - 052F</span></span>|`IsCyrillicSupplement`|  
|<span data-ttu-id="8d9d4-483">0530 - 058F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-483">0530 - 058F</span></span>|`IsArmenian`|  
|<span data-ttu-id="8d9d4-484">0590 - 05FF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-484">0590 - 05FF</span></span>|`IsHebrew`|  
|<span data-ttu-id="8d9d4-485">0600 - 06FF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-485">0600 - 06FF</span></span>|`IsArabic`|  
|<span data-ttu-id="8d9d4-486">0700 - 074F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-486">0700 - 074F</span></span>|`IsSyriac`|  
|<span data-ttu-id="8d9d4-487">0780 - 07BF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-487">0780 - 07BF</span></span>|`IsThaana`|  
|<span data-ttu-id="8d9d4-488">0900 - 097F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-488">0900 - 097F</span></span>|`IsDevanagari`|  
|<span data-ttu-id="8d9d4-489">0980 - 09FF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-489">0980 - 09FF</span></span>|`IsBengali`|  
|<span data-ttu-id="8d9d4-490">0A00 - 0A7F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-490">0A00 - 0A7F</span></span>|`IsGurmukhi`|  
|<span data-ttu-id="8d9d4-491">0A80 - 0AFF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-491">0A80 - 0AFF</span></span>|`IsGujarati`|  
|<span data-ttu-id="8d9d4-492">0B00 - 0B7F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-492">0B00 - 0B7F</span></span>|`IsOriya`|  
|<span data-ttu-id="8d9d4-493">0B80 - 0BFF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-493">0B80 - 0BFF</span></span>|`IsTamil`|  
|<span data-ttu-id="8d9d4-494">0C00 - 0C7F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-494">0C00 - 0C7F</span></span>|`IsTelugu`|  
|<span data-ttu-id="8d9d4-495">0C80 - 0CFF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-495">0C80 - 0CFF</span></span>|`IsKannada`|  
|<span data-ttu-id="8d9d4-496">0D00 - 0D7F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-496">0D00 - 0D7F</span></span>|`IsMalayalam`|  
|<span data-ttu-id="8d9d4-497">0D80 - 0DFF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-497">0D80 - 0DFF</span></span>|`IsSinhala`|  
|<span data-ttu-id="8d9d4-498">0E00 - 0E7F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-498">0E00 - 0E7F</span></span>|`IsThai`|  
|<span data-ttu-id="8d9d4-499">0E80 - 0EFF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-499">0E80 - 0EFF</span></span>|`IsLao`|  
|<span data-ttu-id="8d9d4-500">0F00 - 0FFF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-500">0F00 - 0FFF</span></span>|`IsTibetan`|  
|<span data-ttu-id="8d9d4-501">1000 - 109F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-501">1000 - 109F</span></span>|`IsMyanmar`|  
|<span data-ttu-id="8d9d4-502">10A0 - 10FF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-502">10A0 - 10FF</span></span>|`IsGeorgian`|  
|<span data-ttu-id="8d9d4-503">1100 - 11FF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-503">1100 - 11FF</span></span>|`IsHangulJamo`|  
|<span data-ttu-id="8d9d4-504">1200 - 137F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-504">1200 - 137F</span></span>|`IsEthiopic`|  
|<span data-ttu-id="8d9d4-505">13A0 - 13FF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-505">13A0 - 13FF</span></span>|`IsCherokee`|  
|<span data-ttu-id="8d9d4-506">1400 - 167F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-506">1400 - 167F</span></span>|`IsUnifiedCanadianAboriginalSyllabics`|  
|<span data-ttu-id="8d9d4-507">1680 - 169F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-507">1680 - 169F</span></span>|`IsOgham`|  
|<span data-ttu-id="8d9d4-508">16A0 - 16FF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-508">16A0 - 16FF</span></span>|`IsRunic`|  
|<span data-ttu-id="8d9d4-509">1700 - 171F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-509">1700 - 171F</span></span>|`IsTagalog`|  
|<span data-ttu-id="8d9d4-510">1720 - 173F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-510">1720 - 173F</span></span>|`IsHanunoo`|  
|<span data-ttu-id="8d9d4-511">1740 - 175F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-511">1740 - 175F</span></span>|`IsBuhid`|  
|<span data-ttu-id="8d9d4-512">1760 - 177F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-512">1760 - 177F</span></span>|`IsTagbanwa`|  
|<span data-ttu-id="8d9d4-513">1780 - 17FF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-513">1780 - 17FF</span></span>|`IsKhmer`|  
|<span data-ttu-id="8d9d4-514">1800 - 18AF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-514">1800 - 18AF</span></span>|`IsMongolian`|  
|<span data-ttu-id="8d9d4-515">1900 - 194F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-515">1900 - 194F</span></span>|`IsLimbu`|  
|<span data-ttu-id="8d9d4-516">1950 - 197F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-516">1950 - 197F</span></span>|`IsTaiLe`|  
|<span data-ttu-id="8d9d4-517">19E0 - 19FF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-517">19E0 - 19FF</span></span>|`IsKhmerSymbols`|  
|<span data-ttu-id="8d9d4-518">1D00 - 1D7F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-518">1D00 - 1D7F</span></span>|`IsPhoneticExtensions`|  
|<span data-ttu-id="8d9d4-519">1E00 - 1EFF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-519">1E00 - 1EFF</span></span>|`IsLatinExtendedAdditional`|  
|<span data-ttu-id="8d9d4-520">1F00 - 1FFF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-520">1F00 - 1FFF</span></span>|`IsGreekExtended`|  
|<span data-ttu-id="8d9d4-521">2000 - 206F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-521">2000 - 206F</span></span>|`IsGeneralPunctuation`|  
|<span data-ttu-id="8d9d4-522">2070 - 209F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-522">2070 - 209F</span></span>|`IsSuperscriptsandSubscripts`|  
|<span data-ttu-id="8d9d4-523">20A0 - 20CF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-523">20A0 - 20CF</span></span>|`IsCurrencySymbols`|  
|<span data-ttu-id="8d9d4-524">20D0 - 20FF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-524">20D0 - 20FF</span></span>|`IsCombiningDiacriticalMarksforSymbols`<br /><br /> <span data-ttu-id="8d9d4-525">-或-</span><span class="sxs-lookup"><span data-stu-id="8d9d4-525">-or-</span></span><br /><br /> `IsCombiningMarksforSymbols`|  
|<span data-ttu-id="8d9d4-526">2100 - 214F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-526">2100 - 214F</span></span>|`IsLetterlikeSymbols`|  
|<span data-ttu-id="8d9d4-527">2150 - 218F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-527">2150 - 218F</span></span>|`IsNumberForms`|  
|<span data-ttu-id="8d9d4-528">2190 - 21FF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-528">2190 - 21FF</span></span>|`IsArrows`|  
|<span data-ttu-id="8d9d4-529">2200 - 22FF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-529">2200 - 22FF</span></span>|`IsMathematicalOperators`|  
|<span data-ttu-id="8d9d4-530">2300 - 23FF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-530">2300 - 23FF</span></span>|`IsMiscellaneousTechnical`|  
|<span data-ttu-id="8d9d4-531">2400 - 243F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-531">2400 - 243F</span></span>|`IsControlPictures`|  
|<span data-ttu-id="8d9d4-532">2440 - 245F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-532">2440 - 245F</span></span>|`IsOpticalCharacterRecognition`|  
|<span data-ttu-id="8d9d4-533">2460 - 24FF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-533">2460 - 24FF</span></span>|`IsEnclosedAlphanumerics`|  
|<span data-ttu-id="8d9d4-534">2500 - 257F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-534">2500 - 257F</span></span>|`IsBoxDrawing`|  
|<span data-ttu-id="8d9d4-535">2580 - 259F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-535">2580 - 259F</span></span>|`IsBlockElements`|  
|<span data-ttu-id="8d9d4-536">25A0 - 25FF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-536">25A0 - 25FF</span></span>|`IsGeometricShapes`|  
|<span data-ttu-id="8d9d4-537">2600 - 26FF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-537">2600 - 26FF</span></span>|`IsMiscellaneousSymbols`|  
|<span data-ttu-id="8d9d4-538">2700 - 27BF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-538">2700 - 27BF</span></span>|`IsDingbats`|  
|<span data-ttu-id="8d9d4-539">27C0 - 27EF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-539">27C0 - 27EF</span></span>|`IsMiscellaneousMathematicalSymbols-A`|  
|<span data-ttu-id="8d9d4-540">27F0 - 27FF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-540">27F0 - 27FF</span></span>|`IsSupplementalArrows-A`|  
|<span data-ttu-id="8d9d4-541">2800 - 28FF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-541">2800 - 28FF</span></span>|`IsBraillePatterns`|  
|<span data-ttu-id="8d9d4-542">2900 - 297F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-542">2900 - 297F</span></span>|`IsSupplementalArrows-B`|  
|<span data-ttu-id="8d9d4-543">2980 - 29FF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-543">2980 - 29FF</span></span>|`IsMiscellaneousMathematicalSymbols-B`|  
|<span data-ttu-id="8d9d4-544">2A00 - 2AFF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-544">2A00 - 2AFF</span></span>|`IsSupplementalMathematicalOperators`|  
|<span data-ttu-id="8d9d4-545">2B00 - 2BFF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-545">2B00 - 2BFF</span></span>|`IsMiscellaneousSymbolsandArrows`|  
|<span data-ttu-id="8d9d4-546">2E80 - 2EFF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-546">2E80 - 2EFF</span></span>|`IsCJKRadicalsSupplement`|  
|<span data-ttu-id="8d9d4-547">2F00 - 2FDF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-547">2F00 - 2FDF</span></span>|`IsKangxiRadicals`|  
|<span data-ttu-id="8d9d4-548">2FF0 - 2FFF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-548">2FF0 - 2FFF</span></span>|`IsIdeographicDescriptionCharacters`|  
|<span data-ttu-id="8d9d4-549">3000 - 303F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-549">3000 - 303F</span></span>|`IsCJKSymbolsandPunctuation`|  
|<span data-ttu-id="8d9d4-550">3040 - 309F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-550">3040 - 309F</span></span>|`IsHiragana`|  
|<span data-ttu-id="8d9d4-551">30A0 - 30FF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-551">30A0 - 30FF</span></span>|`IsKatakana`|  
|<span data-ttu-id="8d9d4-552">3100 - 312F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-552">3100 - 312F</span></span>|`IsBopomofo`|  
|<span data-ttu-id="8d9d4-553">3130 - 318F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-553">3130 - 318F</span></span>|`IsHangulCompatibilityJamo`|  
|<span data-ttu-id="8d9d4-554">3190 - 319F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-554">3190 - 319F</span></span>|`IsKanbun`|  
|<span data-ttu-id="8d9d4-555">31A0 - 31BF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-555">31A0 - 31BF</span></span>|`IsBopomofoExtended`|  
|<span data-ttu-id="8d9d4-556">31F0 - 31FF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-556">31F0 - 31FF</span></span>|`IsKatakanaPhoneticExtensions`|  
|<span data-ttu-id="8d9d4-557">3200 - 32FF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-557">3200 - 32FF</span></span>|`IsEnclosedCJKLettersandMonths`|  
|<span data-ttu-id="8d9d4-558">3300 - 33FF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-558">3300 - 33FF</span></span>|`IsCJKCompatibility`|  
|<span data-ttu-id="8d9d4-559">3400 - 4DBF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-559">3400 - 4DBF</span></span>|`IsCJKUnifiedIdeographsExtensionA`|  
|<span data-ttu-id="8d9d4-560">4DC0 - 4DFF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-560">4DC0 - 4DFF</span></span>|`IsYijingHexagramSymbols`|  
|<span data-ttu-id="8d9d4-561">4E00 - 9FFF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-561">4E00 - 9FFF</span></span>|`IsCJKUnifiedIdeographs`|  
|<span data-ttu-id="8d9d4-562">A000 - A48F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-562">A000 - A48F</span></span>|`IsYiSyllables`|  
|<span data-ttu-id="8d9d4-563">A490 - A4CF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-563">A490 - A4CF</span></span>|`IsYiRadicals`|  
|<span data-ttu-id="8d9d4-564">AC00 - D7AF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-564">AC00 - D7AF</span></span>|`IsHangulSyllables`|  
|<span data-ttu-id="8d9d4-565">D800 - DB7F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-565">D800 - DB7F</span></span>|`IsHighSurrogates`|  
|<span data-ttu-id="8d9d4-566">DB80 - DBFF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-566">DB80 - DBFF</span></span>|`IsHighPrivateUseSurrogates`|  
|<span data-ttu-id="8d9d4-567">DC00 - DFFF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-567">DC00 - DFFF</span></span>|`IsLowSurrogates`|  
|<span data-ttu-id="8d9d4-568">E000 - F8FF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-568">E000 - F8FF</span></span>|<span data-ttu-id="8d9d4-569">`IsPrivateUse` 或 `IsPrivateUseArea`</span><span class="sxs-lookup"><span data-stu-id="8d9d4-569">`IsPrivateUse` or `IsPrivateUseArea`</span></span>|  
|<span data-ttu-id="8d9d4-570">F900 - FAFF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-570">F900 - FAFF</span></span>|`IsCJKCompatibilityIdeographs`|  
|<span data-ttu-id="8d9d4-571">FB00 - FB4F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-571">FB00 - FB4F</span></span>|`IsAlphabeticPresentationForms`|  
|<span data-ttu-id="8d9d4-572">FB50 - FDFF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-572">FB50 - FDFF</span></span>|`IsArabicPresentationForms-A`|  
|<span data-ttu-id="8d9d4-573">FE00 - FE0F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-573">FE00 - FE0F</span></span>|`IsVariationSelectors`|  
|<span data-ttu-id="8d9d4-574">FE20 - FE2F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-574">FE20 - FE2F</span></span>|`IsCombiningHalfMarks`|  
|<span data-ttu-id="8d9d4-575">FE30 - FE4F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-575">FE30 - FE4F</span></span>|`IsCJKCompatibilityForms`|  
|<span data-ttu-id="8d9d4-576">FE50 - FE6F</span><span class="sxs-lookup"><span data-stu-id="8d9d4-576">FE50 - FE6F</span></span>|`IsSmallFormVariants`|  
|<span data-ttu-id="8d9d4-577">FE70 - FEFF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-577">FE70 - FEFF</span></span>|`IsArabicPresentationForms-B`|  
|<span data-ttu-id="8d9d4-578">FF00 - FFEF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-578">FF00 - FFEF</span></span>|`IsHalfwidthandFullwidthForms`|  
|<span data-ttu-id="8d9d4-579">FFF0 - FFFF</span><span class="sxs-lookup"><span data-stu-id="8d9d4-579">FFF0 - FFFF</span></span>|`IsSpecials`|  
  
<a name="CharacterClassSubtraction"></a>   
## <a name="character-class-subtraction-basegroup---excludedgroup"></a><span data-ttu-id="8d9d4-580">字元類別減法：[base_group - [excluded_group]]</span><span class="sxs-lookup"><span data-stu-id="8d9d4-580">Character class subtraction: [base_group - [excluded_group]]</span></span>  
 <span data-ttu-id="8d9d4-581">字元類別會定義字元集，</span><span class="sxs-lookup"><span data-stu-id="8d9d4-581">A character class defines a set of characters.</span></span> <span data-ttu-id="8d9d4-582">字元類別減法會產生字元集，這個字元集是將某一個字元類別中的字元從另一個字元類別中排除的結果。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-582">Character class subtraction yields a set of characters that is the result of excluding the characters in one character class from another character class.</span></span>  
  
 <span data-ttu-id="8d9d4-583">字元類別減法運算式的格式如下：</span><span class="sxs-lookup"><span data-stu-id="8d9d4-583">A character class subtraction expression has the following form:</span></span>  
  
 <span data-ttu-id="8d9d4-584">`[` *base_group* `-[` *excluded_group* `]]`</span><span class="sxs-lookup"><span data-stu-id="8d9d4-584">`[` *base_group* `-[` *excluded_group* `]]`</span></span>  
  
 <span data-ttu-id="8d9d4-585">方括號 (`[]`) 和連字號 (`-`) 為必要。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-585">The square brackets (`[]`) and hyphen (`-`) are mandatory.</span></span> <span data-ttu-id="8d9d4-586">*base_group* 是[正字元群組](#PositiveGroup)或[負字元群組](#NegativeGroup)。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-586">The *base_group* is a [positive character group](#PositiveGroup) or a [negative character group](#NegativeGroup).</span></span> <span data-ttu-id="8d9d4-587">*excluded_group* 元件是另一個正字元群組或負字元群組，或者是另一個字元類別減法運算式 (也就是說，您可以將字元類別減法運算式設為巢狀)。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-587">The *excluded_group* component is another positive or negative character group, or another character class subtraction expression (that is, you can nest character class subtraction expressions).</span></span>  
  
 <span data-ttu-id="8d9d4-588">例如，假設您有一個由 "a" 到 "z" 字元範圍組成的基底群組。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-588">For example, suppose you have a base group that consists of the character range from "a" through "z".</span></span> <span data-ttu-id="8d9d4-589">若要定義一組由基底群組所組成的字元，但不包括字元 "m"，則使用 `[a-z-[m]]`。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-589">To define the set of characters that consists of the base group except for the character "m", use `[a-z-[m]]`.</span></span> <span data-ttu-id="8d9d4-590">若要定義一組由基底群組所組成的字元，但不包括 "d"、"j" 和 "p" 這組字元，則使用 `[a-z-[djp]]`。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-590">To define the set of characters that consists of the base group except for the set of characters "d", "j", and "p", use `[a-z-[djp]]`.</span></span> <span data-ttu-id="8d9d4-591">若要定義一組由基底群組所組成的字元，但不包括 "m" 到 "p" 的字元範圍，則使用 `[a-z-[m-p]]`。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-591">To define the set of characters that consists of the base group except for the character range from "m" through "p", use `[a-z-[m-p]]`.</span></span>  
  
 <span data-ttu-id="8d9d4-592">請考慮使用巢狀字元類別減法運算式 `[a-z-[d-w-[m-o]]]`。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-592">Consider the nested character class subtraction expression, `[a-z-[d-w-[m-o]]]`.</span></span> <span data-ttu-id="8d9d4-593">這個運算式會從最內部的字元範圍向外評估。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-593">The expression is evaluated from the innermost character range outward.</span></span> <span data-ttu-id="8d9d4-594">首先從 "d" 到 "w" 字元範圍減去 "m" 到 "o" 字元範圍，這樣會產生從 "d" 到 "l" 及從 "p" 到 "w" 的字元集。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-594">First, the character range from "m" through "o" is subtracted from the character range "d" through "w", which yields the set of characters from "d" through "l" and "p" through "w".</span></span> <span data-ttu-id="8d9d4-595">接著會從字元範圍 "a" 到 "z" 中減去該字元集，此時會產生 `[abcmnoxyz]` 字元集。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-595">That set is then subtracted from the character range from "a" through "z", which yields the set of characters `[abcmnoxyz]`.</span></span>  
  
 <span data-ttu-id="8d9d4-596">您可以使用任何字元類別搭配字元類別減法。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-596">You can use any character class with character class subtraction.</span></span> <span data-ttu-id="8d9d4-597">若要定義由 \u0000 到 \uFFFF 的所有 Unicode 字元組成的字元集，但是不包含空白字元 (`\s`)、標點符號一般分類內的字元 (`\p{P}`)、`IsGreek` 具名區塊內的字元 (`\p{IsGreek}`) 以及 Unicode NEXT LINE 控制字元 (\x85)，請使用 `[\u0000-\uFFFF-[\s\p{P}\p{IsGreek}\x85]]`。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-597">To define the set of characters that consists of all Unicode characters from \u0000 through \uFFFF except white-space characters (`\s`), the characters in the punctuation general category (`\p{P}`), the characters in the `IsGreek` named block (`\p{IsGreek}`), and the Unicode NEXT LINE control character (\x85), use `[\u0000-\uFFFF-[\s\p{P}\p{IsGreek}\x85]]`.</span></span>  
  
 <span data-ttu-id="8d9d4-598">為字元類別減法運算式選擇將會產生有用結果的字元類別，</span><span class="sxs-lookup"><span data-stu-id="8d9d4-598">Choose character classes for a character class subtraction expression that will yield useful results.</span></span> <span data-ttu-id="8d9d4-599">避免選擇會產生空字元集的運算式，該運算式無法比對任何項目，也不要選擇相當於原始基底群組的運算式。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-599">Avoid an expression that yields an empty set of characters, which cannot match anything, or an expression that is equivalent to the original base group.</span></span> <span data-ttu-id="8d9d4-600">例如，空集合是 `[\p{IsBasicLatin}-[\x00-\x7F]]` 運算式的結果，該運算式會從 `IsBasicLatin` 一般分類中減去 `IsBasicLatin` 字元範圍中的所有字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-600">For example, the empty set is the result of the expression `[\p{IsBasicLatin}-[\x00-\x7F]]`, which subtracts all characters in the `IsBasicLatin` character range from the `IsBasicLatin` general category.</span></span> <span data-ttu-id="8d9d4-601">同樣地，原始基底群組是 `[a-z-[0-9]]` 運算式的結果。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-601">Similarly, the original base group is the result of the expression `[a-z-[0-9]]`.</span></span>  <span data-ttu-id="8d9d4-602">這是因為基底群組就是從 "a" 到 "z" 的字母字元範圍，該群組不包含已排除之群組中的任何字元，也就是從 "0" 到 "9" 的十進位數字字元範圍。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-602">This is because the base group, which is the character range of letters from "a" through "z", does not contain any characters in the excluded group, which is the character range of decimal digits from "0" through "9".</span></span>  
  
 <span data-ttu-id="8d9d4-603">下列範例會定義規則運算式 (`^[0-9-[2468]]+$`)，該運算式會比對輸入字串中的零和奇數數字。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-603">The following example defines a regular expression, `^[0-9-[2468]]+$`, that matches zero and odd digits in an input string.</span></span>  <span data-ttu-id="8d9d4-604">規則運算式的解譯方式如下表所示。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-604">The regular expression is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="8d9d4-605">元素</span><span class="sxs-lookup"><span data-stu-id="8d9d4-605">Element</span></span>|<span data-ttu-id="8d9d4-606">說明</span><span class="sxs-lookup"><span data-stu-id="8d9d4-606">Description</span></span>|  
|-------------|-----------------|  
|^|<span data-ttu-id="8d9d4-607">從輸入字串開頭開始比對。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-607">Begin the match at the start of the input string.</span></span>|  
|`[0-9-[2468]]+`|<span data-ttu-id="8d9d4-608">比對 0 到 9 中不包括 2、4、6 和 8 的任何出現一次或多次的字元。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-608">Match one or more occurrences of any character from 0 to 9 except for 2, 4, 6, and 8.</span></span> <span data-ttu-id="8d9d4-609">換句話說，就是比對出現一次或多次的零或奇數。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-609">In other words, match one or more occurrences of zero or an odd digit.</span></span>|  
|$|<span data-ttu-id="8d9d4-610">在輸入字串結尾結束比對。</span><span class="sxs-lookup"><span data-stu-id="8d9d4-610">End the match at the end of the input string.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/classsubtraction1.cs#15)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/classsubtraction1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="8d9d4-611">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d9d4-611">See also</span></span>

- <xref:System.Char.GetUnicodeCategory%2A>
- [<span data-ttu-id="8d9d4-612">規則運算式語言 - 快速參考</span><span class="sxs-lookup"><span data-stu-id="8d9d4-612">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [<span data-ttu-id="8d9d4-613">規則運算式選項</span><span class="sxs-lookup"><span data-stu-id="8d9d4-613">Regular Expression Options</span></span>](../../../docs/standard/base-types/regular-expression-options.md)
