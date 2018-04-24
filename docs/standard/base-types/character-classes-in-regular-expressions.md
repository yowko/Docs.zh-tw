---
title: 規則運算式中的字元類別
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- character classes
- regular expressions, character classes
- characters, matching syntax
- .NET Framework regular expressions, character classes
ms.assetid: 0f8bffab-ee0d-4e0e-9a96-2b4a252bb7e4
caps.latest.revision: 58
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 538aa21712f1e2290fb009c24774059098c60c1e
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="character-classes-in-regular-expressions"></a><span data-ttu-id="4dc0b-102">規則運算式中的字元類別</span><span class="sxs-lookup"><span data-stu-id="4dc0b-102">Character Classes in Regular Expressions</span></span>
<a name="Top"></a> <span data-ttu-id="4dc0b-103">字元類別會定義一組字元，其中任何字元都可在輸入字串中出現，以便讓比對成功。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-103">A character class defines a set of characters, any one of which can occur in an input string for a match to succeed.</span></span> <span data-ttu-id="4dc0b-104">.NET 中的規則運算式語言支援下列字元類別：</span><span class="sxs-lookup"><span data-stu-id="4dc0b-104">The regular expression language in .NET supports the following character classes:</span></span>  
  
-   <span data-ttu-id="4dc0b-105">正字元群組。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-105">Positive character groups.</span></span> <span data-ttu-id="4dc0b-106">輸入字串中的字元必須符合指定字元集的其中一個字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-106">A character in the input string must match one of a specified set of characters.</span></span> <span data-ttu-id="4dc0b-107">如需詳細資訊，請參閱[正字元群組](#PositiveGroup)。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-107">For more information, see [Positive Character Group](#PositiveGroup).</span></span>  
  
-   <span data-ttu-id="4dc0b-108">負字元群組。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-108">Negative character groups.</span></span> <span data-ttu-id="4dc0b-109">輸入字串中的字元不得符合指定字元集的其中一個字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-109">A character in the input string must not match one of a specified set of characters.</span></span> <span data-ttu-id="4dc0b-110">如需詳細資訊，請參閱[負字元群組](#NegativeGroup)。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-110">For more information, see [Negative Character Group](#NegativeGroup).</span></span>  
  
-   <span data-ttu-id="4dc0b-111">任何字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-111">Any character.</span></span> <span data-ttu-id="4dc0b-112">在規則運算式中的 `.` (點或句號) 字元是萬用字元，可符合 `\n` 以外的任何字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-112">The `.` (dot or period) character in a regular expression is a wildcard character that matches any character except `\n`.</span></span> <span data-ttu-id="4dc0b-113">如需詳細資訊，請參閱[任何字元](#AnyCharacter)。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-113">For more information, see [Any Character](#AnyCharacter).</span></span>  
  
-   <span data-ttu-id="4dc0b-114">一般 Unicode 分類或具名區塊。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-114">A general Unicode category or named block.</span></span> <span data-ttu-id="4dc0b-115">輸入字串中的字元必須是特定 Unicode 分類的成員，或者必須落在 Unicode 字元的連續範圍內，比對才會成功。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-115">A character in the input string must be a member of a particular Unicode category or must fall within a contiguous range of Unicode characters for a match to succeed.</span></span> <span data-ttu-id="4dc0b-116">如需詳細資訊，請參閱 [Unicode 分類或 Unicode 區塊](#CategoryOrBlock)。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-116">For more information, see [Unicode Category or Unicode Block](#CategoryOrBlock).</span></span>  
  
-   <span data-ttu-id="4dc0b-117">負的一般 Unicode 分類或是具名區塊。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-117">A negative general Unicode category or named block.</span></span> <span data-ttu-id="4dc0b-118">輸入字串中的字元不得是特定 Unicode 分類的成員，或者不得落在 Unicode 字元的連續範圍內，比對才會成功。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-118">A character in the input string must not be a member of a particular Unicode category or must not fall within a contiguous range of Unicode characters for a match to succeed.</span></span> <span data-ttu-id="4dc0b-119">如需詳細資訊，請參閱[負 Unicode 分類或 Unicode 區塊](#NegativeCategoryOrBlock)。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-119">For more information, see [Negative Unicode Category or Unicode Block](#NegativeCategoryOrBlock).</span></span>  
  
-   <span data-ttu-id="4dc0b-120">文字字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-120">A word character.</span></span> <span data-ttu-id="4dc0b-121">輸入字串中的字元可以隸屬於任何適用於文字字元的 Unicode 分類。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-121">A character in the input string can belong to any of the Unicode categories that are appropriate for characters in words.</span></span> <span data-ttu-id="4dc0b-122">如需詳細資訊，請參閱[文字字元](#WordCharacter)。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-122">For more information, see [Word Character](#WordCharacter).</span></span>  
  
-   <span data-ttu-id="4dc0b-123">非文字字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-123">A non-word character.</span></span> <span data-ttu-id="4dc0b-124">輸入字串中的字元可以隸屬於任何非文字字元的 Unicode 分類。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-124">A character in the input string can belong to any Unicode category that is not a word character.</span></span> <span data-ttu-id="4dc0b-125">如需詳細資訊，請參閱[非文字字元](#NonWordCharacter)。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-125">For more information, see [Non-Word Character](#NonWordCharacter).</span></span>  
  
-   <span data-ttu-id="4dc0b-126">空白字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-126">A white-space character.</span></span> <span data-ttu-id="4dc0b-127">輸入字串中的字元可以是任何 Unicode 分隔符號字元，以及任何一種控制字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-127">A character in the input string can be any Unicode separator character, as well as any one of a number of control characters.</span></span> <span data-ttu-id="4dc0b-128">如需詳細資訊，請參閱[空白字元](#WhitespaceCharacter)。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-128">For more information, see [White-Space Character](#WhitespaceCharacter).</span></span>  
  
-   <span data-ttu-id="4dc0b-129">非空白字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-129">A non-white-space character.</span></span> <span data-ttu-id="4dc0b-130">輸入字串中的字元可以是空白字元以外的任何字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-130">A character in the input string can be any character that is not a white-space character.</span></span> <span data-ttu-id="4dc0b-131">如需詳細資訊，請參閱[非空白字元](#NonWhitespaceCharacter)。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-131">For more information, see [Non-White-Space Character](#NonWhitespaceCharacter).</span></span>  
  
-   <span data-ttu-id="4dc0b-132">十進位數字。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-132">A decimal digit.</span></span> <span data-ttu-id="4dc0b-133">輸入字串中的字元可以是歸類為 Unicode 十進位數字的任何一個數字字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-133">A character in the input string can be any of a number of characters classified as Unicode decimal digits.</span></span> <span data-ttu-id="4dc0b-134">如需詳細資訊，請參閱[十進位數字字元](#DigitCharacter)。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-134">For more information, see [Decimal Digit Character](#DigitCharacter).</span></span>  
  
-   <span data-ttu-id="4dc0b-135">非十進位數字。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-135">A non-decimal digit.</span></span> <span data-ttu-id="4dc0b-136">輸入字串中的字元可以是 Unicode 十進位數字以外的任何字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-136">A character in the input string can be anything other than a Unicode decimal digit.</span></span> <span data-ttu-id="4dc0b-137">如需詳細資訊，請參閱[十進位數字字元](#NonDigitCharacter)。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-137">For more information, see [Decimal Digit Character](#NonDigitCharacter).</span></span>  
  
 <span data-ttu-id="4dc0b-138">.NET 支援字元類別減法運算式，可讓您將一組字元定義為從某個字元類別中排除另一個字元類別的結果。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-138">.NET supports character class subtraction expressions, which enables you to define a set of characters as the result of excluding one character class from another character class.</span></span> <span data-ttu-id="4dc0b-139">如需詳細資訊，請參閱[字元類別減法](#CharacterClassSubtraction)。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-139">For more information, see [Character Class Subtraction](#CharacterClassSubtraction).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4dc0b-140">依分類比對字元的字元類別 (例如，[\w](#WordCharacter) 會比對字組字元，或[\p{}](#CategoryOrBlock) 會比對 Unicode 分類) 會依賴 <xref:System.Globalization.CharUnicodeInfo> 類別來提供字元分類的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-140">Character classes that match characters by category, such as [\w](#WordCharacter) to match word characters or [\p{}](#CategoryOrBlock) to match a Unicode category, rely on the <xref:System.Globalization.CharUnicodeInfo> class to provide information about character categories.</span></span>  <span data-ttu-id="4dc0b-141">從 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 開始，字元類別根據 [Unicode 標準 8.0.0 版](https://www.unicode.org/versions/Unicode8.0.0/)。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-141">Starting with the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], character categories are based on [The Unicode Standard, Version 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/).</span></span> <span data-ttu-id="4dc0b-142">在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 至 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 中，它們根據 [Unicode 標準 6.3.0 版](https://www.unicode.org/versions/Unicode6.3.0/)。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-142">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] through the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], they are based on [The Unicode Standard, Version 6.3.0](https://www.unicode.org/versions/Unicode6.3.0/).</span></span>  
  
<a name="PositiveGroup"></a>   
## <a name="positive-character-group--"></a><span data-ttu-id="4dc0b-143">正字元群組：[ ]</span><span class="sxs-lookup"><span data-stu-id="4dc0b-143">Positive Character Group: [ ]</span></span>  
 <span data-ttu-id="4dc0b-144">正字元群組會指定一份字元清單，其中任何字元都可出現在輸入字串中，以便出現相符項目。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-144">A positive character group specifies a list of characters, any one of which may appear in an input string for a match to occur.</span></span> <span data-ttu-id="4dc0b-145">這份字元清單可以個別指定，也可以依範圍指定，或同時依兩種方式指定。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-145">This list of characters may be specified individually, as a range, or both.</span></span>  
  
 <span data-ttu-id="4dc0b-146">指定個別字元清單的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="4dc0b-146">The syntax for specifying a list of individual characters is as follows:</span></span>  
  
 <span data-ttu-id="4dc0b-147">[*character_group*]</span><span class="sxs-lookup"><span data-stu-id="4dc0b-147">[*character_group*]</span></span>  
  
 <span data-ttu-id="4dc0b-148">其中 *character_group* 是為了讓比對成功而可以出現在輸入字串中的個別字元清單。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-148">where *character_group* is a list of the individual characters that can appear in the input string for a match to succeed.</span></span> <span data-ttu-id="4dc0b-149">*character_group*可以由一或多個常值字元、[逸出字元](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md)或字元類別的任何組合所構成。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-149">*character_group* can consist of any combination of one or more literal characters, [escape characters](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md), or character classes.</span></span>  
  
 <span data-ttu-id="4dc0b-150">指定字元範圍的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="4dc0b-150">The syntax for specifying a range of characters is as follows:</span></span>  
  
```  
[firstCharacter-lastCharacter]  
```  
  
 <span data-ttu-id="4dc0b-151">其中 *firstCharacter* 是範圍開始的字元，而 *lastCharacter* 是範圍結束的字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-151">where *firstCharacter* is the character that begins the range and *lastCharacter* is the character that ends the range.</span></span> <span data-ttu-id="4dc0b-152">字元範圍是指一系列連續的字元，定義的方式是指定系列中的第一個字元、連字號 (-)，然後是系列中的最後一個字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-152">A character range is a contiguous series of characters defined by specifying the first character in the series, a hyphen (-), and then the last character in the series.</span></span> <span data-ttu-id="4dc0b-153">如果兩個字元具有相鄰的 Unicode 字碼指標，這兩個字元就是連續字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-153">Two characters are contiguous if they have adjacent Unicode code points.</span></span>  
  
 <span data-ttu-id="4dc0b-154">下表列出一些包含正字元類別的常見規則運算式模式。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-154">Some common regular expression patterns that contain positive character classes are listed in the following table.</span></span>  
  
|<span data-ttu-id="4dc0b-155">模式</span><span class="sxs-lookup"><span data-stu-id="4dc0b-155">Pattern</span></span>|<span data-ttu-id="4dc0b-156">描述</span><span class="sxs-lookup"><span data-stu-id="4dc0b-156">Description</span></span>|  
|-------------|-----------------|  
|`[aeiou]`|<span data-ttu-id="4dc0b-157">比對所有母音。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-157">Match all vowels.</span></span>|  
|`[\p{P}\d]`|<span data-ttu-id="4dc0b-158">比對所有標點符號和十進位數字字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-158">Match all punctuation and decimal digit characters.</span></span>|  
|`[\s\p{P}]`|<span data-ttu-id="4dc0b-159">比對所有空白字元與標點符號。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-159">Match all white space and punctuation.</span></span>|  
  
 <span data-ttu-id="4dc0b-160">下列範例會定義包含字元 "a" 和 "e" 的正字元群組，因此輸入字串必須包含文字 "grey" 或 "gray" 且後面接著另一個文字，才會出現相符項目。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-160">The following example defines a positive character group that contains the characters "a" and "e" so that the input string must contain the words "grey" or "gray" followed by another word for a match to occur.</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/positivecharclasses.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/positivecharclasses.vb#1)]  
  
 <span data-ttu-id="4dc0b-161">規則運算式 `gr[ae]y\s\S+?[\s|\p{P}]` 定義如下：</span><span class="sxs-lookup"><span data-stu-id="4dc0b-161">The regular expression `gr[ae]y\s\S+?[\s|\p{P}]` is defined as follows:</span></span>  
  
|<span data-ttu-id="4dc0b-162">模式</span><span class="sxs-lookup"><span data-stu-id="4dc0b-162">Pattern</span></span>|<span data-ttu-id="4dc0b-163">描述</span><span class="sxs-lookup"><span data-stu-id="4dc0b-163">Description</span></span>|  
|-------------|-----------------|  
|`gr`|<span data-ttu-id="4dc0b-164">比對常值字元 "gr"。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-164">Match the literal characters "gr".</span></span>|  
|`[ae]`|<span data-ttu-id="4dc0b-165">比對 "a" 或 "e"。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-165">Match either an "a" or an "e".</span></span>|  
|`y\s`|<span data-ttu-id="4dc0b-166">比對後面接著空白字元的常值字元 "y"。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-166">Match the literal character "y" followed by a white-space character.</span></span>|  
|`\S+?`|<span data-ttu-id="4dc0b-167">比對一個或多個非空白字元，但越少越好。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-167">Match one or more non-white-space characters, but as few as possible.</span></span>|  
|`[\s\p{P}]`|<span data-ttu-id="4dc0b-168">比對空白字元或標點符號。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-168">Match either a white-space character or a punctuation mark.</span></span>|  
  
 <span data-ttu-id="4dc0b-169">下列範例將比對以任何大寫字母開頭的文字。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-169">The following example matches words that begin with any capital letter.</span></span> <span data-ttu-id="4dc0b-170">範例將使用子運算式 `[A-Z]` 表示從 A 到 Z 的大寫字母範圍。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-170">It uses the subexpression `[A-Z]` to represent the range of capital letters from A to Z.</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/range.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/range.vb#3)]  
  
 <span data-ttu-id="4dc0b-171">規則運算式 `\b[A-Z]\w*\b` 的定義如下表所示。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-171">The regular expression `\b[A-Z]\w*\b` is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="4dc0b-172">模式</span><span class="sxs-lookup"><span data-stu-id="4dc0b-172">Pattern</span></span>|<span data-ttu-id="4dc0b-173">描述</span><span class="sxs-lookup"><span data-stu-id="4dc0b-173">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="4dc0b-174">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-174">Start at a word boundary.</span></span>|  
|`[A-Z]`|<span data-ttu-id="4dc0b-175">比對從 A 到 Z 的任何大寫字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-175">Match any uppercase character from A to Z.</span></span>|  
|`\w*`|<span data-ttu-id="4dc0b-176">比對零個或多個文字字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-176">Match zero or more word characters.</span></span>|  
|`\b`|<span data-ttu-id="4dc0b-177">比對字邊界。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-177">Match a word boundary.</span></span>|  
  
 [<span data-ttu-id="4dc0b-178">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4dc0b-178">Back to Top</span></span>](#Top)  
  
<a name="NegativeGroup"></a>   
## <a name="negative-character-group-"></a><span data-ttu-id="4dc0b-179">負字元群組：[^]</span><span class="sxs-lookup"><span data-stu-id="4dc0b-179">Negative Character Group: [^]</span></span>  
 <span data-ttu-id="4dc0b-180">負字元群組會指定一份字元清單，其中任何字元不得出現在輸入字串中，才會出現相符項目。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-180">A negative character group specifies a list of characters that must not appear in an input string for a match to occur.</span></span> <span data-ttu-id="4dc0b-181">字元清單可以個別指定，也可以依範圍指定，或同時依兩種方式指定。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-181">The list of characters may be specified individually, as a range, or both.</span></span>  
  
 <span data-ttu-id="4dc0b-182">指定個別字元清單的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="4dc0b-182">The syntax for specifying a list of individual characters is as follows:</span></span>  
  
 <span data-ttu-id="4dc0b-183">[*^character_group*]</span><span class="sxs-lookup"><span data-stu-id="4dc0b-183">[*^character_group*]</span></span>  
  
 <span data-ttu-id="4dc0b-184">其中 *character_group* 是為了讓比對成功而不可出現在輸入字串中的個別字元清單。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-184">where *character_group* is a list of the individual characters that cannot appear in the input string for a match to succeed.</span></span> <span data-ttu-id="4dc0b-185">*character_group*可以由一或多個常值字元、[逸出字元](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md)或字元類別的任何組合所構成。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-185">*character_group* can consist of any combination of one or more literal characters, [escape characters](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md), or character classes.</span></span>  
  
 <span data-ttu-id="4dc0b-186">指定字元範圍的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="4dc0b-186">The syntax for specifying a range of characters is as follows:</span></span>  
  
 <span data-ttu-id="4dc0b-187">[^*firstCharacter*-*lastCharacter*]</span><span class="sxs-lookup"><span data-stu-id="4dc0b-187">[^*firstCharacter*-*lastCharacter*]</span></span>  
  
 <span data-ttu-id="4dc0b-188">其中 *firstCharacter* 是範圍開始的字元，而 *lastCharacter* 是範圍結束的字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-188">where *firstCharacter* is the character that begins the range, and *lastCharacter* is the character that ends the range.</span></span> <span data-ttu-id="4dc0b-189">字元範圍是指一系列連續的字元，定義的方式是指定系列中的第一個字元、連字號 (-)，然後是系列中的最後一個字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-189">A character range is a contiguous series of characters defined by specifying the first character in the series, a hyphen (-), and then the last character in the series.</span></span> <span data-ttu-id="4dc0b-190">如果兩個字元具有相鄰的 Unicode 字碼指標，這兩個字元就是連續字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-190">Two characters are contiguous if they have adjacent Unicode code points.</span></span>  
  
 <span data-ttu-id="4dc0b-191">可以串連兩個或多個字元範圍。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-191">Two or more character ranges can be concatenated.</span></span> <span data-ttu-id="4dc0b-192">例如，若要指定從 "0" 到 "9" 的十進位數字範圍、從 "a" 到 "f" 的小寫字母範圍，以及從 "A" 到 "F" 的大寫字母範圍，可以使用 `[0-9a-fA-F]`。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-192">For example, to specify the range of decimal digits from "0" through "9", the range of lowercase letters from "a" through "f", and the range of uppercase letters from "A" through "F", use `[0-9a-fA-F]`.</span></span>  
  
 <span data-ttu-id="4dc0b-193">負字元群組中的前置 `^` 字元是必要的，它表示字元群組是負字元群組而非正字元群組。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-193">The leading carat character (`^`) in a negative character group is mandatory and indicates the character group is a negative character group instead of a positive character group.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4dc0b-194">較大規則運算式模式中的負字元群組不是零寬度的判斷提示。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-194">A negative character group in a larger regular expression pattern is not a zero-width assertion.</span></span> <span data-ttu-id="4dc0b-195">也就是說，在評估負字元群組之後，規則運算式引擎會在輸入字串中前進一個字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-195">That is, after evaluating the negative character group, the regular expression engine advances one character in the input string.</span></span>  
  
 <span data-ttu-id="4dc0b-196">下表列出一些包含負字元群組的常見規則運算式模式。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-196">Some common regular expression patterns that contain negative character groups are listed in the following table.</span></span>  
  
|<span data-ttu-id="4dc0b-197">模式</span><span class="sxs-lookup"><span data-stu-id="4dc0b-197">Pattern</span></span>|<span data-ttu-id="4dc0b-198">描述</span><span class="sxs-lookup"><span data-stu-id="4dc0b-198">Description</span></span>|  
|-------------|-----------------|  
|`[^aeiou]`|<span data-ttu-id="4dc0b-199">比對除了母音之外的所有字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-199">Match all characters except vowels.</span></span>|  
|`[^\p{P}\d]`|<span data-ttu-id="4dc0b-200">比對標點符號和十進位數字字元之外的所有字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-200">Match all characters except punctuation and decimal digit characters.</span></span>|  
  
 <span data-ttu-id="4dc0b-201">下列範例將比對任何開頭字元是 "th" 且後面不是接著 "o" 的文字。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-201">The following example matches any word that begins with the characters "th" and is not followed by an "o".</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/negativecharclasses.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/negativecharclasses.vb#2)]  
  
 <span data-ttu-id="4dc0b-202">規則運算式 `\bth[^o]\w+\b` 的定義如下表所示。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-202">The regular expression `\bth[^o]\w+\b` is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="4dc0b-203">模式</span><span class="sxs-lookup"><span data-stu-id="4dc0b-203">Pattern</span></span>|<span data-ttu-id="4dc0b-204">描述</span><span class="sxs-lookup"><span data-stu-id="4dc0b-204">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="4dc0b-205">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-205">Start at a word boundary.</span></span>|  
|`th`|<span data-ttu-id="4dc0b-206">比對常值字元 "th"。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-206">Match the literal characters "th".</span></span>|  
|`[^o]`|<span data-ttu-id="4dc0b-207">比對不是 "o" 的任何字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-207">Match any character that is not an "o".</span></span>|  
|`\w+`|<span data-ttu-id="4dc0b-208">比對一個或多個文字字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-208">Match one or more word characters.</span></span>|  
|`\b`|<span data-ttu-id="4dc0b-209">在字邊界結束。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-209">End at a word boundary.</span></span>|  
  
 [<span data-ttu-id="4dc0b-210">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4dc0b-210">Back to Top</span></span>](#Top)  
  
<a name="AnyCharacter"></a>   
## <a name="any-character-"></a><span data-ttu-id="4dc0b-211">任何字元：</span><span class="sxs-lookup"><span data-stu-id="4dc0b-211">Any Character: .</span></span>  
 <span data-ttu-id="4dc0b-212">句號字元 (.) 會比對 `\n` (新行字元 \u000A) 以外任何具有下列兩項資格的字元：</span><span class="sxs-lookup"><span data-stu-id="4dc0b-212">The period character (.) matches any character except `\n` (the newline character, \u000A), with the following two qualifications:</span></span>  
  
-   <span data-ttu-id="4dc0b-213">如果 <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> 選項修改了規則運算式模式，或是 `.` 選項修改了模式中包含 `s` 字元類別的部分，`.` 就會符合任何字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-213">If a regular expression pattern is modified by the <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> option, or if the portion of the pattern that contains the `.` character class is modified by the `s` option, `.` matches any character.</span></span> <span data-ttu-id="4dc0b-214">如需詳細資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-214">For more information, see [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
     <span data-ttu-id="4dc0b-215">下列範例將示範 `.` 字元類別的預設行為與使用 <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> 選項的行為有何不同。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-215">The following example illustrates the different behavior of the `.` character class by default and with the <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> option.</span></span> <span data-ttu-id="4dc0b-216">規則運算式 `^.+` 會從字串開頭開始，比對每一個字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-216">The regular expression `^.+` starts at the beginning of the string and matches every character.</span></span> <span data-ttu-id="4dc0b-217">根據預設，比對會在第一行結尾結束。規則運算式模式會比對歸位字元 `\r` 或 \u000D，但不會比對 `\n`。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-217">By default, the match ends at the end of the first line; the regular expression pattern matches the carriage return character, `\r` or \u000D, but it does not match `\n`.</span></span> <span data-ttu-id="4dc0b-218">由於 <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> 選項會將整個輸入字串解譯為單行，因此它會比對輸入字串中的每個字元，包括 `\n`。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-218">Because the <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> option interprets the entire input string as a single line, it matches every character in the input string, including `\n`.</span></span>  
  
     [!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
     [!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]  
  
> [!NOTE]
>  <span data-ttu-id="4dc0b-219">由於它會比對 `\n` 以外的任何字元，因此 `.` 字元類別也會比對 `\r` (歸位字元 \u000D)。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-219">Because it matches any character except `\n`, the `.` character class also matches `\r` (the carriage return character, \u000D).</span></span>  
  
-   <span data-ttu-id="4dc0b-220">在正或負字元群組中，句號會視為常值句號字元而非字元類別。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-220">In a positive or negative character group, a period is treated as a literal period character, and not as a character class.</span></span> <span data-ttu-id="4dc0b-221">如需詳細資訊，請參閱本主題前段的[正字元群組](#PositiveGroup)和[負字元群組](#NegativeGroup)。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-221">For more information, see [Positive Character Group](#PositiveGroup) and [Negative Character Group](#NegativeGroup) earlier in this topic.</span></span> <span data-ttu-id="4dc0b-222">下列範例將進行示範，定義包含句號字元 (`.`) 做為字元類別以及做為正字元群組成員的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-222">The following example provides an illustration by defining a regular expression that includes the period character (`.`) both as a character class and as a member of a positive character group.</span></span> <span data-ttu-id="4dc0b-223">規則運算式 `\b.*[.?!;:](\s|\z)` 會從字邊界開始比對所有字元，直到遇到包括句號的四個標點符號其中之一，然後比對空白字元或字串結尾。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-223">The regular expression `\b.*[.?!;:](\s|\z)` begins at a word boundary, matches any character until it encounters one of four punctuation marks, including a period, and then matches either a white-space character or the end of the string.</span></span>  
  
     [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any1.cs#4)]
     [!code-vb[Conceptual.RegEx.Language.CharacterClasses#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any1.vb#4)]  
  
> [!NOTE]
>  <span data-ttu-id="4dc0b-224">由於它會比對任何字元，因此如果規則運算式模式嘗試多次比對任何字元，`.` 語言項目就會經常與 lazy 數量詞搭配使用。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-224">Because it matches any character, the `.` language element is often used with a lazy quantifier if a regular expression pattern attempts to match any character multiple times.</span></span> <span data-ttu-id="4dc0b-225">如需詳細資訊，請參閱[數量詞](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-225">For more information, see [Quantifiers](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).</span></span>  
  
 [<span data-ttu-id="4dc0b-226">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4dc0b-226">Back to Top</span></span>](#Top)  
  
<a name="CategoryOrBlock"></a>   
## <a name="unicode-category-or-unicode-block-p"></a><span data-ttu-id="4dc0b-227">Unicode 類別或 Unicode 區塊：\p{}</span><span class="sxs-lookup"><span data-stu-id="4dc0b-227">Unicode Category or Unicode Block: \p{}</span></span>  
 <span data-ttu-id="4dc0b-228">Unicode 標準會為每個字元指派一種一般分類。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-228">The Unicode standard assigns each character a general category.</span></span> <span data-ttu-id="4dc0b-229">例如，特定字元可以是大寫字母 (以 `Lu` 分類表示)、十進位數字 (`Nd` 分類)、數學符號 (`Sm` 分類) 或段落分隔符號 (`Zl` 分類)。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-229">For example, a particular character can be an uppercase letter (represented by the `Lu` category), a decimal digit (the `Nd` category), a math symbol (the `Sm` category), or a paragraph separator (the `Zl` category).</span></span> <span data-ttu-id="4dc0b-230">Unicode 標準中的特定字元集也會佔據連續字碼指標的特定範圍或區塊。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-230">Specific character sets in the Unicode standard also occupy a specific range or block of consecutive code points.</span></span> <span data-ttu-id="4dc0b-231">例如，從 \u0000 到 \u007F 可找到基本拉丁字元集，從 \u0600 到 \u06FF 則可找到阿拉伯字元集。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-231">For example, the basic Latin character set is found from \u0000 through \u007F, while the Arabic character set is found from \u0600 through \u06FF.</span></span>  
  
 <span data-ttu-id="4dc0b-232">規則運算式建構</span><span class="sxs-lookup"><span data-stu-id="4dc0b-232">The regular expression construct</span></span>  
  
 <span data-ttu-id="4dc0b-233">`\p{` *name* `}`</span><span class="sxs-lookup"><span data-stu-id="4dc0b-233">`\p{` *name* `}`</span></span>  
  
 <span data-ttu-id="4dc0b-234">比對屬於 Unicode 一般分類或具名區塊的任何字元，其中 *name* 是分類縮寫或具名區塊名稱。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-234">matches any character that belongs to a Unicode general category or named block, where *name* is the category abbreviation or named block name.</span></span> <span data-ttu-id="4dc0b-235">如需分類縮寫的清單，請參閱本主題稍後的[支援的 Unicode 一般分類](#SupportedUnicodeGeneralCategories)一節。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-235">For a list of category abbreviations, see the [Supported Unicode General Categories](#SupportedUnicodeGeneralCategories) section later in this topic.</span></span> <span data-ttu-id="4dc0b-236">如需具名區塊清單，請參閱本主題稍後的[支援的具名區塊](#SupportedNamedBlocks)一節。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-236">For a list of named blocks, see the [Supported Named Blocks](#SupportedNamedBlocks) section later in this topic.</span></span>  
  
 <span data-ttu-id="4dc0b-237">下列範例會使用 `\p{`*name*`}` 建構同時比對 Unicode 一般類別 (在這個案例中是 `Pd`，或稱 [標點符號、虛線] 分類) 以及具名區塊 (`IsGreek` 和 `IsBasicLatin` 具名區塊)。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-237">The following example uses the `\p{`*name*`}` construct to match both a Unicode general category (in this case, the `Pd`, or Punctuation,Dash category) and a named block (the `IsGreek` and `IsBasicLatin` named blocks).</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/category1.cs#6)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/category1.vb#6)]  
  
 <span data-ttu-id="4dc0b-238">規則運算式 `\b(\p{IsGreek}+(\s)?)+\p{Pd}\s(\p{IsBasicLatin}+(\s)?)+` 的定義如下表所示。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-238">The regular expression `\b(\p{IsGreek}+(\s)?)+\p{Pd}\s(\p{IsBasicLatin}+(\s)?)+` is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="4dc0b-239">模式</span><span class="sxs-lookup"><span data-stu-id="4dc0b-239">Pattern</span></span>|<span data-ttu-id="4dc0b-240">描述</span><span class="sxs-lookup"><span data-stu-id="4dc0b-240">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="4dc0b-241">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-241">Start at a word boundary.</span></span>|  
|`\p{IsGreek}+`|<span data-ttu-id="4dc0b-242">比對一個或多個希臘字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-242">Match one or more Greek characters.</span></span>|  
|`(\s)?`|<span data-ttu-id="4dc0b-243">比對零個或一個空白字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-243">Match zero or one white-space character.</span></span>|  
|`(\p{IsGreek}+(\s)?)+`|<span data-ttu-id="4dc0b-244">一次或多次比對一個或多個希臘字元後面接著零或一個空白字元的模式。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-244">Match the pattern of one or more Greek characters followed by zero or one white-space characters one or more times.</span></span>|  
|`\p{Pd}`|<span data-ttu-id="4dc0b-245">比對標點符號、虛線字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-245">Match a Punctuation, Dash character.</span></span>|  
|`\s`|<span data-ttu-id="4dc0b-246">比對空白字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-246">Match a white-space character.</span></span>|  
|`\p{IsBasicLatin}+`|<span data-ttu-id="4dc0b-247">比對一個或多個基本拉丁字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-247">Match one or more basic Latin characters.</span></span>|  
|`(\s)?`|<span data-ttu-id="4dc0b-248">比對零個或一個空白字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-248">Match zero or one white-space character.</span></span>|  
|`(\p{IsBasicLatin}+(\s)?)+`|<span data-ttu-id="4dc0b-249">一次或多次比對一個或多個基本拉丁字元後面接著零個或一個空白字元的模式。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-249">Match the pattern of one or more basic Latin characters followed by zero or one white-space characters one or more times.</span></span>|  
  
 [<span data-ttu-id="4dc0b-250">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4dc0b-250">Back to Top</span></span>](#Top)  
  
<a name="NegativeCategoryOrBlock"></a>   
## <a name="negative-unicode-category-or-unicode-block-p"></a><span data-ttu-id="4dc0b-251">負 Unicode 分類或 Unicode 區塊：\P{}</span><span class="sxs-lookup"><span data-stu-id="4dc0b-251">Negative Unicode Category or Unicode Block: \P{}</span></span>  
 <span data-ttu-id="4dc0b-252">Unicode 標準會為每個字元指派一種一般分類。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-252">The Unicode standard assigns each character a general category.</span></span> <span data-ttu-id="4dc0b-253">例如，特定字元可以是大寫字母 (以 `Lu` 分類表示)、十進位數字 (`Nd` 分類)、數學符號 (`Sm` 分類) 或段落分隔符號 (`Zl` 分類)。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-253">For example, a particular character can be an uppercase letter (represented by the `Lu` category), a decimal digit (the `Nd` category), a math symbol (the `Sm` category), or a paragraph separator (the `Zl` category).</span></span> <span data-ttu-id="4dc0b-254">Unicode 標準中的特定字元集也會佔據連續字碼指標的特定範圍或區塊。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-254">Specific character sets in the Unicode standard also occupy a specific range or block of consecutive code points.</span></span> <span data-ttu-id="4dc0b-255">例如，從 \u0000 到 \u007F 可找到基本拉丁字元集，從 \u0600 到 \u06FF 則可找到阿拉伯字元集。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-255">For example, the basic Latin character set is found from \u0000 through \u007F, while the Arabic character set is found from \u0600 through \u06FF.</span></span>  
  
 <span data-ttu-id="4dc0b-256">規則運算式建構</span><span class="sxs-lookup"><span data-stu-id="4dc0b-256">The regular expression construct</span></span>  
  
 <span data-ttu-id="4dc0b-257">`\P{` *name* `}`</span><span class="sxs-lookup"><span data-stu-id="4dc0b-257">`\P{` *name* `}`</span></span>  
  
 <span data-ttu-id="4dc0b-258">比對任何不屬於 Unicode 一般分類或具名區塊的字元，其中 *name* 是分類縮寫或是具名區塊名稱。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-258">matches any character that does not belong to a Unicode general category or named block, where *name* is the category abbreviation or named block name.</span></span> <span data-ttu-id="4dc0b-259">如需分類縮寫的清單，請參閱本主題稍後的[支援的 Unicode 一般分類](#SupportedUnicodeGeneralCategories)一節。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-259">For a list of category abbreviations, see the [Supported Unicode General Categories](#SupportedUnicodeGeneralCategories) section later in this topic.</span></span> <span data-ttu-id="4dc0b-260">如需具名區塊清單，請參閱本主題稍後的[支援的具名區塊](#SupportedNamedBlocks)一節。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-260">For a list of named blocks, see the [Supported Named Blocks](#SupportedNamedBlocks) section later in this topic.</span></span>  
  
 <span data-ttu-id="4dc0b-261">下列範例會使用 `\P{`*name*`}` 建構從數值字串中移除任何貨幣符號 (在這個案例中是 `Sc`，或稱 [符號、貨幣] 分類)。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-261">The following example uses the `\P{`*name*`}` construct to remove any currency symbols (in this case, the `Sc`, or Symbol, Currency category) from numeric strings.</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/notcategory1.cs#7)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/notcategory1.vb#7)]  
  
 <span data-ttu-id="4dc0b-262">規則運算式模式 `(\P{Sc})+` 會比對一個或多個不是貨幣符號的字元，並且會有效移除結果字串中的所有貨幣符號。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-262">The regular expression pattern `(\P{Sc})+` matches one or more characters that are not currency symbols; it effectively strips any currency symbol from the result string.</span></span>  
  
 [<span data-ttu-id="4dc0b-263">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4dc0b-263">Back to Top</span></span>](#Top)  
  
<a name="WordCharacter"></a>   
## <a name="word-character-w"></a><span data-ttu-id="4dc0b-264">文字字元：\w</span><span class="sxs-lookup"><span data-stu-id="4dc0b-264">Word Character: \w</span></span>  
 <span data-ttu-id="4dc0b-265">`\w` 會比對任何文字字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-265">`\w` matches any word character.</span></span> <span data-ttu-id="4dc0b-266">文字字元是下表中所列的任何 Unicode 分類的成員。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-266">A word character is a member of any of the Unicode categories listed in the following table.</span></span>  
  
|<span data-ttu-id="4dc0b-267">分類</span><span class="sxs-lookup"><span data-stu-id="4dc0b-267">Category</span></span>|<span data-ttu-id="4dc0b-268">描述</span><span class="sxs-lookup"><span data-stu-id="4dc0b-268">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="4dc0b-269">Ll</span><span class="sxs-lookup"><span data-stu-id="4dc0b-269">Ll</span></span>|<span data-ttu-id="4dc0b-270">字母、小寫</span><span class="sxs-lookup"><span data-stu-id="4dc0b-270">Letter, Lowercase</span></span>|  
|<span data-ttu-id="4dc0b-271">Lu</span><span class="sxs-lookup"><span data-stu-id="4dc0b-271">Lu</span></span>|<span data-ttu-id="4dc0b-272">字母、大寫</span><span class="sxs-lookup"><span data-stu-id="4dc0b-272">Letter, Uppercase</span></span>|  
|<span data-ttu-id="4dc0b-273">Lt</span><span class="sxs-lookup"><span data-stu-id="4dc0b-273">Lt</span></span>|<span data-ttu-id="4dc0b-274">字母、字首大寫</span><span class="sxs-lookup"><span data-stu-id="4dc0b-274">Letter, Titlecase</span></span>|  
|<span data-ttu-id="4dc0b-275">Lo</span><span class="sxs-lookup"><span data-stu-id="4dc0b-275">Lo</span></span>|<span data-ttu-id="4dc0b-276">字母、其他</span><span class="sxs-lookup"><span data-stu-id="4dc0b-276">Letter, Other</span></span>|  
|<span data-ttu-id="4dc0b-277">Lm</span><span class="sxs-lookup"><span data-stu-id="4dc0b-277">Lm</span></span>|<span data-ttu-id="4dc0b-278">字母、修飾詞</span><span class="sxs-lookup"><span data-stu-id="4dc0b-278">Letter, Modifier</span></span>|  
|<span data-ttu-id="4dc0b-279">Mn</span><span class="sxs-lookup"><span data-stu-id="4dc0b-279">Mn</span></span>|<span data-ttu-id="4dc0b-280">記號，非間距</span><span class="sxs-lookup"><span data-stu-id="4dc0b-280">Mark, Nonspacing</span></span>|  
|<span data-ttu-id="4dc0b-281">Nd</span><span class="sxs-lookup"><span data-stu-id="4dc0b-281">Nd</span></span>|<span data-ttu-id="4dc0b-282">數字、十進位數字</span><span class="sxs-lookup"><span data-stu-id="4dc0b-282">Number, Decimal Digit</span></span>|  
|<span data-ttu-id="4dc0b-283">Pc</span><span class="sxs-lookup"><span data-stu-id="4dc0b-283">Pc</span></span>|<span data-ttu-id="4dc0b-284">標點符號、連接器。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-284">Punctuation, Connector.</span></span> <span data-ttu-id="4dc0b-285">這個分類包含十個字元，其中最常用的是 LOWLINE 字元 (_)，u+005F。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-285">This category includes ten characters, the most commonly used of which is the LOWLINE character (_), u+005F.</span></span>|  
  
 <span data-ttu-id="4dc0b-286">如果指定了符合 ECMAScript 的行為，`\w` 就等於 `[a-zA-Z_0-9]`。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-286">If ECMAScript-compliant behavior is specified, `\w` is equivalent to `[a-zA-Z_0-9]`.</span></span> <span data-ttu-id="4dc0b-287">如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)中的＜ECMAScript 相符行為＞一節。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-287">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4dc0b-288">由於它會比對任何文字字元，因此，如果規則運算式模式嘗試多次比對任何文字字元且後面接著特定文字字元，`\w` 語言項目就會經常與 lazy 數量詞搭配使用。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-288">Because it matches any word character, the `\w` language element is often used with a lazy quantifier if a regular expression pattern attempts to match any word character multiple times, followed by a specific word character.</span></span> <span data-ttu-id="4dc0b-289">如需詳細資訊，請參閱[數量詞](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-289">For more information, see [Quantifiers](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="4dc0b-290">下列範例會使用 `\w` 語言項目比對文字中重複的字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-290">The following example uses the `\w` language element to match duplicate characters in a word.</span></span> <span data-ttu-id="4dc0b-291">這個範例會定義規則運算式模式 `(\w)\1`，該模式解譯如下。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-291">The example defines a regular expression pattern, `(\w)\1`, which can be interpreted as follows.</span></span>  
  
|<span data-ttu-id="4dc0b-292">元素</span><span class="sxs-lookup"><span data-stu-id="4dc0b-292">Element</span></span>|<span data-ttu-id="4dc0b-293">描述</span><span class="sxs-lookup"><span data-stu-id="4dc0b-293">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4dc0b-294">(\w)</span><span class="sxs-lookup"><span data-stu-id="4dc0b-294">(\w)</span></span>|<span data-ttu-id="4dc0b-295">比對文字字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-295">Match a word character.</span></span> <span data-ttu-id="4dc0b-296">這是第一個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-296">This is the first capturing group.</span></span>|  
|<span data-ttu-id="4dc0b-297">\1</span><span class="sxs-lookup"><span data-stu-id="4dc0b-297">\1</span></span>|<span data-ttu-id="4dc0b-298">比對第一個擷取的值。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-298">Match the value of the first capture.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/wordchar1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/wordchar1.vb#8)]  
  
 [<span data-ttu-id="4dc0b-299">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4dc0b-299">Back to Top</span></span>](#Top)  
  
<a name="NonWordCharacter"></a>   
## <a name="non-word-character-w"></a><span data-ttu-id="4dc0b-300">非文字字元：\W</span><span class="sxs-lookup"><span data-stu-id="4dc0b-300">Non-Word Character: \W</span></span>  
 <span data-ttu-id="4dc0b-301">`\W` 會比對任何非文字字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-301">`\W` matches any non-word character.</span></span> <span data-ttu-id="4dc0b-302">\W 語言項目相當於下列字元類別：</span><span class="sxs-lookup"><span data-stu-id="4dc0b-302">The \W language element is equivalent to the following character class:</span></span>  
  
```  
[^\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]  
```  
  
 <span data-ttu-id="4dc0b-303">換句話說，它會比對下表所列 Unicode 分類中字元以外的所有字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-303">In other words, it matches any character except for those in the Unicode categories listed in the following table.</span></span>  
  
|<span data-ttu-id="4dc0b-304">分類</span><span class="sxs-lookup"><span data-stu-id="4dc0b-304">Category</span></span>|<span data-ttu-id="4dc0b-305">描述</span><span class="sxs-lookup"><span data-stu-id="4dc0b-305">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="4dc0b-306">Ll</span><span class="sxs-lookup"><span data-stu-id="4dc0b-306">Ll</span></span>|<span data-ttu-id="4dc0b-307">字母、小寫</span><span class="sxs-lookup"><span data-stu-id="4dc0b-307">Letter, Lowercase</span></span>|  
|<span data-ttu-id="4dc0b-308">Lu</span><span class="sxs-lookup"><span data-stu-id="4dc0b-308">Lu</span></span>|<span data-ttu-id="4dc0b-309">字母、大寫</span><span class="sxs-lookup"><span data-stu-id="4dc0b-309">Letter, Uppercase</span></span>|  
|<span data-ttu-id="4dc0b-310">Lt</span><span class="sxs-lookup"><span data-stu-id="4dc0b-310">Lt</span></span>|<span data-ttu-id="4dc0b-311">字母、字首大寫</span><span class="sxs-lookup"><span data-stu-id="4dc0b-311">Letter, Titlecase</span></span>|  
|<span data-ttu-id="4dc0b-312">Lo</span><span class="sxs-lookup"><span data-stu-id="4dc0b-312">Lo</span></span>|<span data-ttu-id="4dc0b-313">字母、其他</span><span class="sxs-lookup"><span data-stu-id="4dc0b-313">Letter, Other</span></span>|  
|<span data-ttu-id="4dc0b-314">Lm</span><span class="sxs-lookup"><span data-stu-id="4dc0b-314">Lm</span></span>|<span data-ttu-id="4dc0b-315">字母、修飾詞</span><span class="sxs-lookup"><span data-stu-id="4dc0b-315">Letter, Modifier</span></span>|  
|<span data-ttu-id="4dc0b-316">Mn</span><span class="sxs-lookup"><span data-stu-id="4dc0b-316">Mn</span></span>|<span data-ttu-id="4dc0b-317">記號，非間距</span><span class="sxs-lookup"><span data-stu-id="4dc0b-317">Mark, Nonspacing</span></span>|  
|<span data-ttu-id="4dc0b-318">Nd</span><span class="sxs-lookup"><span data-stu-id="4dc0b-318">Nd</span></span>|<span data-ttu-id="4dc0b-319">數字、十進位數字</span><span class="sxs-lookup"><span data-stu-id="4dc0b-319">Number, Decimal Digit</span></span>|  
|<span data-ttu-id="4dc0b-320">Pc</span><span class="sxs-lookup"><span data-stu-id="4dc0b-320">Pc</span></span>|<span data-ttu-id="4dc0b-321">標點符號、連接器。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-321">Punctuation, Connector.</span></span> <span data-ttu-id="4dc0b-322">這個分類包含十個字元，其中最常用的是 LOWLINE 字元 (_)，u+005F。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-322">This category includes ten characters, the most commonly used of which is the LOWLINE character (_), u+005F.</span></span>|  
  
 <span data-ttu-id="4dc0b-323">如果指定了符合 ECMAScript 的行為，`\W` 就等於 `[^a-zA-Z_0-9]`。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-323">If ECMAScript-compliant behavior is specified, `\W` is equivalent to `[^a-zA-Z_0-9]`.</span></span> <span data-ttu-id="4dc0b-324">如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)中的＜ECMAScript 相符行為＞一節。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-324">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4dc0b-325">由於它會比對任何非文字字元，因此，如果規則運算式模式嘗試多次比對任何非文字字元，且後面接著特定非文字字元，`\W` 語言項目就會經常與 lazy 數量詞搭配使用。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-325">Because it matches any non-word character, the `\W` language element is often used with a lazy quantifier if a regular expression pattern attempts to match any non-word character multiple times followed by a specific non-word character.</span></span> <span data-ttu-id="4dc0b-326">如需詳細資訊，請參閱[數量詞](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-326">For more information, see [Quantifiers](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="4dc0b-327">以下範例將說明 `\W` 字元類別。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-327">The following example illustrates the `\W` character class.</span></span>  <span data-ttu-id="4dc0b-328">它會定義規則運算式模式 `\b(\w+)(\W){1,2}`，該模式會比對後面接一個或多個非文字字元的文字，例如空白字元或標點符號。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-328">It defines a regular expression pattern, `\b(\w+)(\W){1,2}`, that matches a word followed by one or two non-word characters, such as white space or punctuation.</span></span> <span data-ttu-id="4dc0b-329">規則運算式的解譯方式如下表所示。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-329">The regular expression is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="4dc0b-330">元素</span><span class="sxs-lookup"><span data-stu-id="4dc0b-330">Element</span></span>|<span data-ttu-id="4dc0b-331">描述</span><span class="sxs-lookup"><span data-stu-id="4dc0b-331">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4dc0b-332">\b</span><span class="sxs-lookup"><span data-stu-id="4dc0b-332">\b</span></span>|<span data-ttu-id="4dc0b-333">開始字緣比對。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-333">Begin the match at a word boundary.</span></span>|  
|<span data-ttu-id="4dc0b-334">(\w+)</span><span class="sxs-lookup"><span data-stu-id="4dc0b-334">(\w+)</span></span>|<span data-ttu-id="4dc0b-335">比對一個或多個文字字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-335">Match one or more word characters.</span></span> <span data-ttu-id="4dc0b-336">這是第一個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-336">This is the first capturing group.</span></span>|  
|<span data-ttu-id="4dc0b-337">(\W){1,2}</span><span class="sxs-lookup"><span data-stu-id="4dc0b-337">(\W){1,2}</span></span>|<span data-ttu-id="4dc0b-338">比對一次或兩次非文字字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-338">Match a non-word character either one or two times.</span></span> <span data-ttu-id="4dc0b-339">這是第二個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-339">This is the second capturing group.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nonwordchar1.cs#9)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nonwordchar1.vb#9)]  
  
 <span data-ttu-id="4dc0b-340">由於第二個擷取群組的 <xref:System.Text.RegularExpressions.Group> 物件只包含單一擷取的非文字字元，因此這個範例會從 <xref:System.Text.RegularExpressions.CaptureCollection> 屬性所傳回之 <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> 物件擷取所有擷取的非文字字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-340">Because the <xref:System.Text.RegularExpressions.Group> object for the second capturing group contains only a single captured non-word character, the example retrieves all captured non-word characters from the <xref:System.Text.RegularExpressions.CaptureCollection> object that is returned by the <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> property.</span></span>  
  
 [<span data-ttu-id="4dc0b-341">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4dc0b-341">Back to Top</span></span>](#Top)  
  
<a name="WhitespaceCharacter"></a>   
## <a name="white-space-character-s"></a><span data-ttu-id="4dc0b-342">空白字元：\s</span><span class="sxs-lookup"><span data-stu-id="4dc0b-342">White-Space Character: \s</span></span>  
 <span data-ttu-id="4dc0b-343">`\s` 會比對任何空白字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-343">`\s` matches any white-space character.</span></span> <span data-ttu-id="4dc0b-344">它相當於下表列出的逸出序列和 Unicode 分類。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-344">It is equivalent to the escape sequences and Unicode categories listed in the following table.</span></span>  
  
|<span data-ttu-id="4dc0b-345">分類</span><span class="sxs-lookup"><span data-stu-id="4dc0b-345">Category</span></span>|<span data-ttu-id="4dc0b-346">描述</span><span class="sxs-lookup"><span data-stu-id="4dc0b-346">Description</span></span>|  
|--------------|-----------------|  
|`\f`|<span data-ttu-id="4dc0b-347">換頁字元 \u000C。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-347">The form feed character, \u000C.</span></span>|  
|`\n`|<span data-ttu-id="4dc0b-348">新行字元 \u000A。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-348">The newline character, \u000A.</span></span>|  
|`\r`|<span data-ttu-id="4dc0b-349">歸位字元 \u000D。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-349">The carriage return character, \u000D.</span></span>|  
|`\t`|<span data-ttu-id="4dc0b-350">定位字元 \u0009。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-350">The tab character, \u0009.</span></span>|  
|`\v`|<span data-ttu-id="4dc0b-351">垂直定位字元 \u000B。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-351">The vertical tab character, \u000B.</span></span>|  
|`\x85`|<span data-ttu-id="4dc0b-352">省略符號或 NEXT LINE (NEL) 字元 (…) \u0085。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-352">The ellipsis or NEXT LINE (NEL) character (…), \u0085.</span></span>|  
|`\p{Z}`|<span data-ttu-id="4dc0b-353">比對任何分隔符號字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-353">Matches any separator character.</span></span>|  
  
 <span data-ttu-id="4dc0b-354">如果指定了符合 ECMAScript 的行為，`\s` 就等於 `[ \f\n\r\t\v]`。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-354">If ECMAScript-compliant behavior is specified, `\s` is equivalent to `[ \f\n\r\t\v]`.</span></span> <span data-ttu-id="4dc0b-355">如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)中的＜ECMAScript 相符行為＞一節。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-355">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
 <span data-ttu-id="4dc0b-356">以下範例將說明 `\s` 字元類別。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-356">The following example illustrates the `\s` character class.</span></span> <span data-ttu-id="4dc0b-357">它會定義規則運算式模式 `\b\w+(e)?s(\s|$)`，該模式會比對結尾為 "s" 或 "es" 且後面加上空白字元或是輸入字串結尾的文字。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-357">It defines a regular expression pattern, `\b\w+(e)?s(\s|$)`, that matches a word ending in either "s" or "es" followed by either a white-space character or the end of the input string.</span></span> <span data-ttu-id="4dc0b-358">規則運算式的解譯方式如下表所示。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-358">The regular expression is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="4dc0b-359">元素</span><span class="sxs-lookup"><span data-stu-id="4dc0b-359">Element</span></span>|<span data-ttu-id="4dc0b-360">描述</span><span class="sxs-lookup"><span data-stu-id="4dc0b-360">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4dc0b-361">\b</span><span class="sxs-lookup"><span data-stu-id="4dc0b-361">\b</span></span>|<span data-ttu-id="4dc0b-362">開始字緣比對。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-362">Begin the match at a word boundary.</span></span>|  
|<span data-ttu-id="4dc0b-363">\w+</span><span class="sxs-lookup"><span data-stu-id="4dc0b-363">\w+</span></span>|<span data-ttu-id="4dc0b-364">比對一個或多個文字字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-364">Match one or more word characters.</span></span>|  
|<span data-ttu-id="4dc0b-365">(e)?</span><span class="sxs-lookup"><span data-stu-id="4dc0b-365">(e)?</span></span>|<span data-ttu-id="4dc0b-366">比對 "e" 零次或一次。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-366">Match an "e" either zero or one time.</span></span>|  
|<span data-ttu-id="4dc0b-367">s</span><span class="sxs-lookup"><span data-stu-id="4dc0b-367">s</span></span>|<span data-ttu-id="4dc0b-368">比對 "s"。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-368">Match an "s".</span></span>|  
|<span data-ttu-id="4dc0b-369">(\s&#124;$)</span><span class="sxs-lookup"><span data-stu-id="4dc0b-369">(\s&#124;$)</span></span>|<span data-ttu-id="4dc0b-370">比對空白字元或輸入字串的結尾。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-370">Match either a white-space character or the end of the input string.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/whitespace1.cs#10)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/whitespace1.vb#10)]  
  
 [<span data-ttu-id="4dc0b-371">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4dc0b-371">Back to Top</span></span>](#Top)  
  
<a name="NonWhitespaceCharacter"></a>   
## <a name="non-white-space-character-s"></a><span data-ttu-id="4dc0b-372">非空白字元：\S</span><span class="sxs-lookup"><span data-stu-id="4dc0b-372">Non-White-Space Character: \S</span></span>  
 <span data-ttu-id="4dc0b-373">`\S` 會比對任何非空白字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-373">`\S` matches any non-white-space character.</span></span> <span data-ttu-id="4dc0b-374">它相當於 `[^\f\n\r\t\v\x85\p{Z}]` 規則運算式模式，或是規則運算式模式的相反模式，相當於會比對空白字元的 `\s`。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-374">It is equivalent to the `[^\f\n\r\t\v\x85\p{Z}]` regular expression pattern, or the opposite of the regular expression pattern that is equivalent to `\s`, which matches white-space characters.</span></span> <span data-ttu-id="4dc0b-375">如需詳細資訊，請參閱[空白字元：\s](#WhitespaceCharacter)。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-375">For more information, see [White-Space Character: \s](#WhitespaceCharacter).</span></span>  
  
 <span data-ttu-id="4dc0b-376">如果指定了符合 ECMAScript 的行為，`\S` 就等於 `[^ \f\n\r\t\v]`。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-376">If ECMAScript-compliant behavior is specified, `\S` is equivalent to  `[^ \f\n\r\t\v]`.</span></span> <span data-ttu-id="4dc0b-377">如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)中的＜ECMAScript 相符行為＞一節。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-377">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
 <span data-ttu-id="4dc0b-378">下列範例將說明 `\S` 語言項目。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-378">The following example illustrates the `\S` language element.</span></span> <span data-ttu-id="4dc0b-379">規則運算式模式 `\b(\S+)\s?` 會比對以空白字元分隔的字串。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-379">The regular expression pattern `\b(\S+)\s?` matches strings that are delimited by white-space characters.</span></span> <span data-ttu-id="4dc0b-380">在比對之 <xref:System.Text.RegularExpressions.GroupCollection> 物件中的第二個項目包含相符的字串。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-380">The second element in the match's <xref:System.Text.RegularExpressions.GroupCollection> object contains the matched string.</span></span> <span data-ttu-id="4dc0b-381">規則運算式的解譯方式如下表所示。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-381">The regular expression can be interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="4dc0b-382">元素</span><span class="sxs-lookup"><span data-stu-id="4dc0b-382">Element</span></span>|<span data-ttu-id="4dc0b-383">描述</span><span class="sxs-lookup"><span data-stu-id="4dc0b-383">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="4dc0b-384">開始字緣比對。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-384">Begin the match at a word boundary.</span></span>|  
|`(\S+)`|<span data-ttu-id="4dc0b-385">比對一個或多個非空白字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-385">Match one or more non-white-space characters.</span></span> <span data-ttu-id="4dc0b-386">這是第一個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-386">This is the first capturing group.</span></span>|  
|`\s?`|<span data-ttu-id="4dc0b-387">比對零個或一個空白字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-387">Match zero or one white-space character.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nonwhitespace1.cs#11)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nonwhitespace1.vb#11)]  
  
 [<span data-ttu-id="4dc0b-388">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4dc0b-388">Back to Top</span></span>](#Top)  
  
<a name="DigitCharacter"></a>   
## <a name="decimal-digit-character-d"></a><span data-ttu-id="4dc0b-389">十進位數字字元：\d</span><span class="sxs-lookup"><span data-stu-id="4dc0b-389">Decimal Digit Character: \d</span></span>  
 <span data-ttu-id="4dc0b-390">`\d` 會比對任何十進位數字。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-390">`\d` matches any decimal digit.</span></span> <span data-ttu-id="4dc0b-391">它相當於 `\p{Nd}` 規則運算式模式，其中包括標準的十進位數字 0-9，以及若干其他字元集的十進位數字。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-391">It is equivalent to the `\p{Nd}` regular expression pattern, which includes the standard decimal digits 0-9 as well as the decimal digits of a number of other character sets.</span></span>  
  
 <span data-ttu-id="4dc0b-392">如果指定了符合 ECMAScript 的行為，`\d` 就等於 `[0-9]`。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-392">If ECMAScript-compliant behavior is specified, `\d` is equivalent to  `[0-9]`.</span></span> <span data-ttu-id="4dc0b-393">如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)中的＜ECMAScript 相符行為＞一節。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-393">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
 <span data-ttu-id="4dc0b-394">下列範例將說明 `\d` 語言項目。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-394">The following example illustrates the `\d` language element.</span></span> <span data-ttu-id="4dc0b-395">它會測試輸入字串是否表示美國和加拿大的有效電話號碼。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-395">It tests whether an input string represents a valid telephone number in the United States and Canada.</span></span> <span data-ttu-id="4dc0b-396">規則運算式模式 `^(\(?\d{3}\)?[\s-])?\d{3}-\d{4}$` 的定義如下表所示。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-396">The regular expression pattern `^(\(?\d{3}\)?[\s-])?\d{3}-\d{4}$` is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="4dc0b-397">項目</span><span class="sxs-lookup"><span data-stu-id="4dc0b-397">Element</span></span>|<span data-ttu-id="4dc0b-398">描述</span><span class="sxs-lookup"><span data-stu-id="4dc0b-398">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="4dc0b-399">在輸入字串的開頭開始比對。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-399">Begin the match at the beginning of the input string.</span></span>|  
|`\(?`|<span data-ttu-id="4dc0b-400">比對零個或一個常值 "(" 字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-400">Match zero or one literal "(" character.</span></span>|  
|`\d{3}`|<span data-ttu-id="4dc0b-401">比對三個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-401">Match three decimal digits.</span></span>|  
|`\)?`|<span data-ttu-id="4dc0b-402">比對零個或一個常值 ")" 字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-402">Match zero or one literal ")" character.</span></span>|  
|`[\s-]`|<span data-ttu-id="4dc0b-403">比對連字號或空白字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-403">Match a hyphen or a white-space character.</span></span>|  
|`(\(?\d{3}\)?[\s-])?`|<span data-ttu-id="4dc0b-404">比對零次或一次選擇性的左括號，後面接著三個十進位數字、選擇性的右括號，以及空白字元或是連字號。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-404">Match an optional opening parenthesis followed by three decimal digits, an optional closing parenthesis, and either a white-space character or a hyphen zero or one time.</span></span> <span data-ttu-id="4dc0b-405">這是第一個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-405">This is the first capturing group.</span></span>|  
|`\d{3}-\d{4}`|<span data-ttu-id="4dc0b-406">比對三個十進位數字，後面接著連字號和另外四個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-406">Match three decimal digits followed by a hyphen and four more decimal digits.</span></span>|  
|`$`|<span data-ttu-id="4dc0b-407">比對輸入字串的結尾。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-407">Match the end of the input string.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/digit1.cs#12)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/digit1.vb#12)]  
  
 [<span data-ttu-id="4dc0b-408">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4dc0b-408">Back to Top</span></span>](#Top)  
  
<a name="NonDigitCharacter"></a>   
## <a name="non-digit-character-d"></a><span data-ttu-id="4dc0b-409">非數字字元：\D</span><span class="sxs-lookup"><span data-stu-id="4dc0b-409">Non-Digit Character: \D</span></span>  
 <span data-ttu-id="4dc0b-410">`\D` 會比對任何非數字字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-410">`\D` matches any non-digit character.</span></span> <span data-ttu-id="4dc0b-411">它相當於 `\P{Nd}` 規則運算式模式。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-411">It is equivalent to the `\P{Nd}` regular expression pattern.</span></span>  
  
 <span data-ttu-id="4dc0b-412">如果指定了符合 ECMAScript 的行為，`\D` 就等於 `[^0-9]`。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-412">If ECMAScript-compliant behavior is specified, `\D` is equivalent to  `[^0-9]`.</span></span> <span data-ttu-id="4dc0b-413">如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)中的＜ECMAScript 相符行為＞一節。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-413">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
 <span data-ttu-id="4dc0b-414">下列範例將說明 \D 語言項目。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-414">The following example illustrates the \D language element.</span></span> <span data-ttu-id="4dc0b-415">它會測試像是組件編號這類字串，是否由十進位和非十進位字元的適當組合所構成。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-415">It tests whether a string such as a part number consists of the appropriate combination of decimal and non-decimal characters.</span></span> <span data-ttu-id="4dc0b-416">規則運算式模式 `^\D\d{1,5}\D*$` 的定義如下表所示。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-416">The regular expression pattern `^\D\d{1,5}\D*$` is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="4dc0b-417">項目</span><span class="sxs-lookup"><span data-stu-id="4dc0b-417">Element</span></span>|<span data-ttu-id="4dc0b-418">描述</span><span class="sxs-lookup"><span data-stu-id="4dc0b-418">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="4dc0b-419">在輸入字串的開頭開始比對。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-419">Begin the match at the beginning of the input string.</span></span>|  
|`\D`|<span data-ttu-id="4dc0b-420">比對非數字字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-420">Match a non-digit character.</span></span>|  
|`\d{1,5}`|<span data-ttu-id="4dc0b-421">比對從一個到五個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-421">Match from one to five decimal digits.</span></span>|  
|`\D*`|<span data-ttu-id="4dc0b-422">比對零個、一個或更多非十進位字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-422">Match zero, one, or more non-decimal characters.</span></span>|  
|`$`|<span data-ttu-id="4dc0b-423">比對輸入字串的結尾。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-423">Match the end of the input string.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nondigit1.cs#13)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nondigit1.vb#13)]  
  
 [<span data-ttu-id="4dc0b-424">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4dc0b-424">Back to Top</span></span>](#Top)  
  
<a name="SupportedUnicodeGeneralCategories"></a>   
## <a name="supported-unicode-general-categories"></a><span data-ttu-id="4dc0b-425">支援的 Unicode 一般分類</span><span class="sxs-lookup"><span data-stu-id="4dc0b-425">Supported Unicode General Categories</span></span>  
 <span data-ttu-id="4dc0b-426">Unicode 定義了下表中所列的一般類別。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-426">Unicode defines the general categories listed in the following table.</span></span> <span data-ttu-id="4dc0b-427">如需詳細資訊，請參閱 [Unicode Character Database](https://www.unicode.org/reports/tr44/) 中的 "UCD File Format" 和 "General Category Values" 副標題。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-427">For more information, see the "UCD File Format" and "General Category Values" subtopics at the [Unicode Character Database](https://www.unicode.org/reports/tr44/).</span></span>  
  
|<span data-ttu-id="4dc0b-428">分類</span><span class="sxs-lookup"><span data-stu-id="4dc0b-428">Category</span></span>|<span data-ttu-id="4dc0b-429">描述</span><span class="sxs-lookup"><span data-stu-id="4dc0b-429">Description</span></span>|  
|--------------|-----------------|  
|`Lu`|<span data-ttu-id="4dc0b-430">字母、大寫</span><span class="sxs-lookup"><span data-stu-id="4dc0b-430">Letter, Uppercase</span></span>|  
|`Ll`|<span data-ttu-id="4dc0b-431">字母、小寫</span><span class="sxs-lookup"><span data-stu-id="4dc0b-431">Letter, Lowercase</span></span>|  
|`Lt`|<span data-ttu-id="4dc0b-432">字母、字首大寫</span><span class="sxs-lookup"><span data-stu-id="4dc0b-432">Letter, Titlecase</span></span>|  
|`Lm`|<span data-ttu-id="4dc0b-433">字母、修飾詞</span><span class="sxs-lookup"><span data-stu-id="4dc0b-433">Letter, Modifier</span></span>|  
|`Lo`|<span data-ttu-id="4dc0b-434">字母、其他</span><span class="sxs-lookup"><span data-stu-id="4dc0b-434">Letter, Other</span></span>|  
|`L`|<span data-ttu-id="4dc0b-435">所有字母字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-435">All letter characters.</span></span> <span data-ttu-id="4dc0b-436">這包括 `Lu`、`Ll`、`Lt`、`Lm` 和 `Lo` 字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-436">This includes the `Lu`, `Ll`, `Lt`, `Lm`, and `Lo` characters.</span></span>|  
|`Mn`|<span data-ttu-id="4dc0b-437">記號，非間距</span><span class="sxs-lookup"><span data-stu-id="4dc0b-437">Mark, Nonspacing</span></span>|  
|`Mc`|<span data-ttu-id="4dc0b-438">記號，間距組合</span><span class="sxs-lookup"><span data-stu-id="4dc0b-438">Mark, Spacing Combining</span></span>|  
|`Me`|<span data-ttu-id="4dc0b-439">記號，封入</span><span class="sxs-lookup"><span data-stu-id="4dc0b-439">Mark, Enclosing</span></span>|  
|`M`|<span data-ttu-id="4dc0b-440">所有變音符號記號。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-440">All diacritic marks.</span></span> <span data-ttu-id="4dc0b-441">這包括 `Mn`、`Mc` 和 `Me` 分類。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-441">This includes the `Mn`, `Mc`, and `Me` categories.</span></span>|  
|`Nd`|<span data-ttu-id="4dc0b-442">數字、十進位數字</span><span class="sxs-lookup"><span data-stu-id="4dc0b-442">Number, Decimal Digit</span></span>|  
|`Nl`|<span data-ttu-id="4dc0b-443">數字，字母</span><span class="sxs-lookup"><span data-stu-id="4dc0b-443">Number, Letter</span></span>|  
|`No`|<span data-ttu-id="4dc0b-444">數字，其他</span><span class="sxs-lookup"><span data-stu-id="4dc0b-444">Number, Other</span></span>|  
|`N`|<span data-ttu-id="4dc0b-445">所有數字。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-445">All numbers.</span></span> <span data-ttu-id="4dc0b-446">這包括 `Nd`、`Nl` 和 `No` 分類。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-446">This includes the `Nd`, `Nl`, and `No` categories.</span></span>|  
|`Pc`|<span data-ttu-id="4dc0b-447">標點符號，連接器</span><span class="sxs-lookup"><span data-stu-id="4dc0b-447">Punctuation, Connector</span></span>|  
|`Pd`|<span data-ttu-id="4dc0b-448">標點符號，破折號</span><span class="sxs-lookup"><span data-stu-id="4dc0b-448">Punctuation, Dash</span></span>|  
|`Ps`|<span data-ttu-id="4dc0b-449">標點符號，左括號</span><span class="sxs-lookup"><span data-stu-id="4dc0b-449">Punctuation, Open</span></span>|  
|`Pe`|<span data-ttu-id="4dc0b-450">標點符號，右括號</span><span class="sxs-lookup"><span data-stu-id="4dc0b-450">Punctuation, Close</span></span>|  
|`Pi`|<span data-ttu-id="4dc0b-451">標點符號，左引號 (根據使用方式，作用可能像 Ps 或 Pe)</span><span class="sxs-lookup"><span data-stu-id="4dc0b-451">Punctuation, Initial quote (may behave like Ps or Pe depending on usage)</span></span>|  
|`Pf`|<span data-ttu-id="4dc0b-452">標點符號，右引號 (根據使用方式，作用可能像 Ps 或 Pe)</span><span class="sxs-lookup"><span data-stu-id="4dc0b-452">Punctuation, Final quote (may behave like Ps or Pe depending on usage)</span></span>|  
|`Po`|<span data-ttu-id="4dc0b-453">標點符號，其他</span><span class="sxs-lookup"><span data-stu-id="4dc0b-453">Punctuation, Other</span></span>|  
|`P`|<span data-ttu-id="4dc0b-454">所有標點符號字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-454">All punctuation characters.</span></span> <span data-ttu-id="4dc0b-455">這包括 `Pc`、`Pd`、`Ps`、`Pe`、`Pi`、`Pf` 和 `Po` 分類。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-455">This includes the `Pc`, `Pd`, `Ps`, `Pe`, `Pi`, `Pf`, and `Po` categories.</span></span>|  
|`Sm`|<span data-ttu-id="4dc0b-456">符號，數學</span><span class="sxs-lookup"><span data-stu-id="4dc0b-456">Symbol, Math</span></span>|  
|`Sc`|<span data-ttu-id="4dc0b-457">符號，貨幣</span><span class="sxs-lookup"><span data-stu-id="4dc0b-457">Symbol, Currency</span></span>|  
|`Sk`|<span data-ttu-id="4dc0b-458">符號，修飾詞</span><span class="sxs-lookup"><span data-stu-id="4dc0b-458">Symbol, Modifier</span></span>|  
|`So`|<span data-ttu-id="4dc0b-459">符號，其他</span><span class="sxs-lookup"><span data-stu-id="4dc0b-459">Symbol, Other</span></span>|  
|`S`|<span data-ttu-id="4dc0b-460">所有符號。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-460">All symbols.</span></span> <span data-ttu-id="4dc0b-461">這包括 `Sm`、`Sc`、`Sk` 和 `So` 分類。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-461">This includes the `Sm`, `Sc`, `Sk`, and `So` categories.</span></span>|  
|`Zs`|<span data-ttu-id="4dc0b-462">分隔符號，空格</span><span class="sxs-lookup"><span data-stu-id="4dc0b-462">Separator, Space</span></span>|  
|`Zl`|<span data-ttu-id="4dc0b-463">分隔符號，行</span><span class="sxs-lookup"><span data-stu-id="4dc0b-463">Separator, Line</span></span>|  
|`Zp`|<span data-ttu-id="4dc0b-464">分隔符號，段落</span><span class="sxs-lookup"><span data-stu-id="4dc0b-464">Separator, Paragraph</span></span>|  
|`Z`|<span data-ttu-id="4dc0b-465">所有分隔符號字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-465">All separator characters.</span></span> <span data-ttu-id="4dc0b-466">這包括 `Zs`、`Zl` 和 `Zp` 分類。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-466">This includes the `Zs`, `Zl`, and `Zp` categories.</span></span>|  
|`Cc`|<span data-ttu-id="4dc0b-467">其他，控制</span><span class="sxs-lookup"><span data-stu-id="4dc0b-467">Other, Control</span></span>|  
|`Cf`|<span data-ttu-id="4dc0b-468">其他，格式</span><span class="sxs-lookup"><span data-stu-id="4dc0b-468">Other, Format</span></span>|  
|`Cs`|<span data-ttu-id="4dc0b-469">其他，Surrogate</span><span class="sxs-lookup"><span data-stu-id="4dc0b-469">Other, Surrogate</span></span>|  
|`Co`|<span data-ttu-id="4dc0b-470">其他，專用</span><span class="sxs-lookup"><span data-stu-id="4dc0b-470">Other, Private Use</span></span>|  
|`Cn`|<span data-ttu-id="4dc0b-471">其他，未指派 (沒有字元擁有這個屬性)</span><span class="sxs-lookup"><span data-stu-id="4dc0b-471">Other, Not Assigned (no characters have this property)</span></span>|  
|`C`|<span data-ttu-id="4dc0b-472">所有控制字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-472">All control characters.</span></span> <span data-ttu-id="4dc0b-473">這包括 `Cc`、`Cf`、`Cs`、`Co` 和 `Cn` 分類。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-473">This includes the `Cc`, `Cf`, `Cs`, `Co`, and `Cn` categories.</span></span>|  
  
 <span data-ttu-id="4dc0b-474">您可以將任何特殊字元傳遞到 <xref:System.Char.GetUnicodeCategory%2A> 方法，以判斷該字元的 Unicode 分類。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-474">You can determine the Unicode category of any particular character by passing that character to the <xref:System.Char.GetUnicodeCategory%2A> method.</span></span> <span data-ttu-id="4dc0b-475">下列範例會使用 <xref:System.Char.GetUnicodeCategory%2A> 方法判斷包含所選取拉丁字元的陣列中，每個項目的分類。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-475">The following example uses the <xref:System.Char.GetUnicodeCategory%2A> method to determine the category of each element in an array that contains selected Latin characters.</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/getunicodecategory1.cs#14)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/getunicodecategory1.vb#14)]  
  
 [<span data-ttu-id="4dc0b-476">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4dc0b-476">Back to Top</span></span>](#Top)  
  
<a name="SupportedNamedBlocks"></a>   
## <a name="supported-named-blocks"></a><span data-ttu-id="4dc0b-477">支援的具名區塊</span><span class="sxs-lookup"><span data-stu-id="4dc0b-477">Supported Named Blocks</span></span>  
 <span data-ttu-id="4dc0b-478">.NET 提供下表所列的具名區塊。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-478">.NET provides the named blocks listed in the following table.</span></span> <span data-ttu-id="4dc0b-479">這一組支援的具名區塊是根據 Unicode 4.0 和 Perl 5.6。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-479">The set of supported named blocks is based on Unicode 4.0 and Perl 5.6.</span></span>  
  
|<span data-ttu-id="4dc0b-480">字碼指標範圍</span><span class="sxs-lookup"><span data-stu-id="4dc0b-480">Code point range</span></span>|<span data-ttu-id="4dc0b-481">區塊名稱</span><span class="sxs-lookup"><span data-stu-id="4dc0b-481">Block name</span></span>|  
|----------------------|----------------|  
|<span data-ttu-id="4dc0b-482">0000 - 007F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-482">0000 - 007F</span></span>|`IsBasicLatin`|  
|<span data-ttu-id="4dc0b-483">0080 - 00FF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-483">0080 - 00FF</span></span>|`IsLatin-1Supplement`|  
|<span data-ttu-id="4dc0b-484">0100 - 017F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-484">0100 - 017F</span></span>|`IsLatinExtended-A`|  
|<span data-ttu-id="4dc0b-485">0180 - 024F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-485">0180 - 024F</span></span>|`IsLatinExtended-B`|  
|<span data-ttu-id="4dc0b-486">0250 - 02AF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-486">0250 - 02AF</span></span>|`IsIPAExtensions`|  
|<span data-ttu-id="4dc0b-487">02B0 - 02FF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-487">02B0 - 02FF</span></span>|`IsSpacingModifierLetters`|  
|<span data-ttu-id="4dc0b-488">0300 - 036F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-488">0300 - 036F</span></span>|`IsCombiningDiacriticalMarks`|  
|<span data-ttu-id="4dc0b-489">0370 - 03FF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-489">0370 - 03FF</span></span>|`IsGreek`<br /><br /> <span data-ttu-id="4dc0b-490">-或-</span><span class="sxs-lookup"><span data-stu-id="4dc0b-490">-or-</span></span><br /><br /> `IsGreekandCoptic`|  
|<span data-ttu-id="4dc0b-491">0400 - 04FF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-491">0400 - 04FF</span></span>|`IsCyrillic`|  
|<span data-ttu-id="4dc0b-492">0500 - 052F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-492">0500 - 052F</span></span>|`IsCyrillicSupplement`|  
|<span data-ttu-id="4dc0b-493">0530 - 058F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-493">0530 - 058F</span></span>|`IsArmenian`|  
|<span data-ttu-id="4dc0b-494">0590 - 05FF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-494">0590 - 05FF</span></span>|`IsHebrew`|  
|<span data-ttu-id="4dc0b-495">0600 - 06FF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-495">0600 - 06FF</span></span>|`IsArabic`|  
|<span data-ttu-id="4dc0b-496">0700 - 074F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-496">0700 - 074F</span></span>|`IsSyriac`|  
|<span data-ttu-id="4dc0b-497">0780 - 07BF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-497">0780 - 07BF</span></span>|`IsThaana`|  
|<span data-ttu-id="4dc0b-498">0900 - 097F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-498">0900 - 097F</span></span>|`IsDevanagari`|  
|<span data-ttu-id="4dc0b-499">0980 - 09FF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-499">0980 - 09FF</span></span>|`IsBengali`|  
|<span data-ttu-id="4dc0b-500">0A00 - 0A7F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-500">0A00 - 0A7F</span></span>|`IsGurmukhi`|  
|<span data-ttu-id="4dc0b-501">0A80 - 0AFF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-501">0A80 - 0AFF</span></span>|`IsGujarati`|  
|<span data-ttu-id="4dc0b-502">0B00 - 0B7F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-502">0B00 - 0B7F</span></span>|`IsOriya`|  
|<span data-ttu-id="4dc0b-503">0B80 - 0BFF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-503">0B80 - 0BFF</span></span>|`IsTamil`|  
|<span data-ttu-id="4dc0b-504">0C00 - 0C7F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-504">0C00 - 0C7F</span></span>|`IsTelugu`|  
|<span data-ttu-id="4dc0b-505">0C80 - 0CFF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-505">0C80 - 0CFF</span></span>|`IsKannada`|  
|<span data-ttu-id="4dc0b-506">0D00 - 0D7F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-506">0D00 - 0D7F</span></span>|`IsMalayalam`|  
|<span data-ttu-id="4dc0b-507">0D80 - 0DFF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-507">0D80 - 0DFF</span></span>|`IsSinhala`|  
|<span data-ttu-id="4dc0b-508">0E00 - 0E7F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-508">0E00 - 0E7F</span></span>|`IsThai`|  
|<span data-ttu-id="4dc0b-509">0E80 - 0EFF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-509">0E80 - 0EFF</span></span>|`IsLao`|  
|<span data-ttu-id="4dc0b-510">0F00 - 0FFF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-510">0F00 - 0FFF</span></span>|`IsTibetan`|  
|<span data-ttu-id="4dc0b-511">1000 - 109F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-511">1000 - 109F</span></span>|`IsMyanmar`|  
|<span data-ttu-id="4dc0b-512">10A0 - 10FF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-512">10A0 - 10FF</span></span>|`IsGeorgian`|  
|<span data-ttu-id="4dc0b-513">1100 - 11FF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-513">1100 - 11FF</span></span>|`IsHangulJamo`|  
|<span data-ttu-id="4dc0b-514">1200 - 137F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-514">1200 - 137F</span></span>|`IsEthiopic`|  
|<span data-ttu-id="4dc0b-515">13A0 - 13FF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-515">13A0 - 13FF</span></span>|`IsCherokee`|  
|<span data-ttu-id="4dc0b-516">1400 - 167F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-516">1400 - 167F</span></span>|`IsUnifiedCanadianAboriginalSyllabics`|  
|<span data-ttu-id="4dc0b-517">1680 - 169F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-517">1680 - 169F</span></span>|`IsOgham`|  
|<span data-ttu-id="4dc0b-518">16A0 - 16FF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-518">16A0 - 16FF</span></span>|`IsRunic`|  
|<span data-ttu-id="4dc0b-519">1700 - 171F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-519">1700 - 171F</span></span>|`IsTagalog`|  
|<span data-ttu-id="4dc0b-520">1720 - 173F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-520">1720 - 173F</span></span>|`IsHanunoo`|  
|<span data-ttu-id="4dc0b-521">1740 - 175F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-521">1740 - 175F</span></span>|`IsBuhid`|  
|<span data-ttu-id="4dc0b-522">1760 - 177F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-522">1760 - 177F</span></span>|`IsTagbanwa`|  
|<span data-ttu-id="4dc0b-523">1780 - 17FF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-523">1780 - 17FF</span></span>|`IsKhmer`|  
|<span data-ttu-id="4dc0b-524">1800 - 18AF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-524">1800 - 18AF</span></span>|`IsMongolian`|  
|<span data-ttu-id="4dc0b-525">1900 - 194F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-525">1900 - 194F</span></span>|`IsLimbu`|  
|<span data-ttu-id="4dc0b-526">1950 - 197F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-526">1950 - 197F</span></span>|`IsTaiLe`|  
|<span data-ttu-id="4dc0b-527">19E0 - 19FF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-527">19E0 - 19FF</span></span>|`IsKhmerSymbols`|  
|<span data-ttu-id="4dc0b-528">1D00 - 1D7F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-528">1D00 - 1D7F</span></span>|`IsPhoneticExtensions`|  
|<span data-ttu-id="4dc0b-529">1E00 - 1EFF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-529">1E00 - 1EFF</span></span>|`IsLatinExtendedAdditional`|  
|<span data-ttu-id="4dc0b-530">1F00 - 1FFF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-530">1F00 - 1FFF</span></span>|`IsGreekExtended`|  
|<span data-ttu-id="4dc0b-531">2000 - 206F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-531">2000 - 206F</span></span>|`IsGeneralPunctuation`|  
|<span data-ttu-id="4dc0b-532">2070 - 209F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-532">2070 - 209F</span></span>|`IsSuperscriptsandSubscripts`|  
|<span data-ttu-id="4dc0b-533">20A0 - 20CF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-533">20A0 - 20CF</span></span>|`IsCurrencySymbols`|  
|<span data-ttu-id="4dc0b-534">20D0 - 20FF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-534">20D0 - 20FF</span></span>|`IsCombiningDiacriticalMarksforSymbols`<br /><br /> <span data-ttu-id="4dc0b-535">-或-</span><span class="sxs-lookup"><span data-stu-id="4dc0b-535">-or-</span></span><br /><br /> `IsCombiningMarksforSymbols`|  
|<span data-ttu-id="4dc0b-536">2100 - 214F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-536">2100 - 214F</span></span>|`IsLetterlikeSymbols`|  
|<span data-ttu-id="4dc0b-537">2150 - 218F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-537">2150 - 218F</span></span>|`IsNumberForms`|  
|<span data-ttu-id="4dc0b-538">2190 - 21FF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-538">2190 - 21FF</span></span>|`IsArrows`|  
|<span data-ttu-id="4dc0b-539">2200 - 22FF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-539">2200 - 22FF</span></span>|`IsMathematicalOperators`|  
|<span data-ttu-id="4dc0b-540">2300 - 23FF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-540">2300 - 23FF</span></span>|`IsMiscellaneousTechnical`|  
|<span data-ttu-id="4dc0b-541">2400 - 243F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-541">2400 - 243F</span></span>|`IsControlPictures`|  
|<span data-ttu-id="4dc0b-542">2440 - 245F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-542">2440 - 245F</span></span>|`IsOpticalCharacterRecognition`|  
|<span data-ttu-id="4dc0b-543">2460 - 24FF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-543">2460 - 24FF</span></span>|`IsEnclosedAlphanumerics`|  
|<span data-ttu-id="4dc0b-544">2500 - 257F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-544">2500 - 257F</span></span>|`IsBoxDrawing`|  
|<span data-ttu-id="4dc0b-545">2580 - 259F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-545">2580 - 259F</span></span>|`IsBlockElements`|  
|<span data-ttu-id="4dc0b-546">25A0 - 25FF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-546">25A0 - 25FF</span></span>|`IsGeometricShapes`|  
|<span data-ttu-id="4dc0b-547">2600 - 26FF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-547">2600 - 26FF</span></span>|`IsMiscellaneousSymbols`|  
|<span data-ttu-id="4dc0b-548">2700 - 27BF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-548">2700 - 27BF</span></span>|`IsDingbats`|  
|<span data-ttu-id="4dc0b-549">27C0 - 27EF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-549">27C0 - 27EF</span></span>|`IsMiscellaneousMathematicalSymbols-A`|  
|<span data-ttu-id="4dc0b-550">27F0 - 27FF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-550">27F0 - 27FF</span></span>|`IsSupplementalArrows-A`|  
|<span data-ttu-id="4dc0b-551">2800 - 28FF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-551">2800 - 28FF</span></span>|`IsBraillePatterns`|  
|<span data-ttu-id="4dc0b-552">2900 - 297F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-552">2900 - 297F</span></span>|`IsSupplementalArrows-B`|  
|<span data-ttu-id="4dc0b-553">2980 - 29FF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-553">2980 - 29FF</span></span>|`IsMiscellaneousMathematicalSymbols-B`|  
|<span data-ttu-id="4dc0b-554">2A00 - 2AFF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-554">2A00 - 2AFF</span></span>|`IsSupplementalMathematicalOperators`|  
|<span data-ttu-id="4dc0b-555">2B00 - 2BFF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-555">2B00 - 2BFF</span></span>|`IsMiscellaneousSymbolsandArrows`|  
|<span data-ttu-id="4dc0b-556">2E80 - 2EFF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-556">2E80 - 2EFF</span></span>|`IsCJKRadicalsSupplement`|  
|<span data-ttu-id="4dc0b-557">2F00 - 2FDF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-557">2F00 - 2FDF</span></span>|`IsKangxiRadicals`|  
|<span data-ttu-id="4dc0b-558">2FF0 - 2FFF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-558">2FF0 - 2FFF</span></span>|`IsIdeographicDescriptionCharacters`|  
|<span data-ttu-id="4dc0b-559">3000 - 303F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-559">3000 - 303F</span></span>|`IsCJKSymbolsandPunctuation`|  
|<span data-ttu-id="4dc0b-560">3040 - 309F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-560">3040 - 309F</span></span>|`IsHiragana`|  
|<span data-ttu-id="4dc0b-561">30A0 - 30FF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-561">30A0 - 30FF</span></span>|`IsKatakana`|  
|<span data-ttu-id="4dc0b-562">3100 - 312F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-562">3100 - 312F</span></span>|`IsBopomofo`|  
|<span data-ttu-id="4dc0b-563">3130 - 318F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-563">3130 - 318F</span></span>|`IsHangulCompatibilityJamo`|  
|<span data-ttu-id="4dc0b-564">3190 - 319F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-564">3190 - 319F</span></span>|`IsKanbun`|  
|<span data-ttu-id="4dc0b-565">31A0 - 31BF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-565">31A0 - 31BF</span></span>|`IsBopomofoExtended`|  
|<span data-ttu-id="4dc0b-566">31F0 - 31FF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-566">31F0 - 31FF</span></span>|`IsKatakanaPhoneticExtensions`|  
|<span data-ttu-id="4dc0b-567">3200 - 32FF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-567">3200 - 32FF</span></span>|`IsEnclosedCJKLettersandMonths`|  
|<span data-ttu-id="4dc0b-568">3300 - 33FF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-568">3300 - 33FF</span></span>|`IsCJKCompatibility`|  
|<span data-ttu-id="4dc0b-569">3400 - 4DBF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-569">3400 - 4DBF</span></span>|`IsCJKUnifiedIdeographsExtensionA`|  
|<span data-ttu-id="4dc0b-570">4DC0 - 4DFF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-570">4DC0 - 4DFF</span></span>|`IsYijingHexagramSymbols`|  
|<span data-ttu-id="4dc0b-571">4E00 - 9FFF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-571">4E00 - 9FFF</span></span>|`IsCJKUnifiedIdeographs`|  
|<span data-ttu-id="4dc0b-572">A000 - A48F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-572">A000 - A48F</span></span>|`IsYiSyllables`|  
|<span data-ttu-id="4dc0b-573">A490 - A4CF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-573">A490 - A4CF</span></span>|`IsYiRadicals`|  
|<span data-ttu-id="4dc0b-574">AC00 - D7AF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-574">AC00 - D7AF</span></span>|`IsHangulSyllables`|  
|<span data-ttu-id="4dc0b-575">D800 - DB7F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-575">D800 - DB7F</span></span>|`IsHighSurrogates`|  
|<span data-ttu-id="4dc0b-576">DB80 - DBFF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-576">DB80 - DBFF</span></span>|`IsHighPrivateUseSurrogates`|  
|<span data-ttu-id="4dc0b-577">DC00 - DFFF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-577">DC00 - DFFF</span></span>|`IsLowSurrogates`|  
|<span data-ttu-id="4dc0b-578">E000 - F8FF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-578">E000 - F8FF</span></span>|<span data-ttu-id="4dc0b-579">`IsPrivateUse` 或 `IsPrivateUseArea`</span><span class="sxs-lookup"><span data-stu-id="4dc0b-579">`IsPrivateUse` or `IsPrivateUseArea`</span></span>|  
|<span data-ttu-id="4dc0b-580">F900 - FAFF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-580">F900 - FAFF</span></span>|`IsCJKCompatibilityIdeographs`|  
|<span data-ttu-id="4dc0b-581">FB00 - FB4F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-581">FB00 - FB4F</span></span>|`IsAlphabeticPresentationForms`|  
|<span data-ttu-id="4dc0b-582">FB50 - FDFF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-582">FB50 - FDFF</span></span>|`IsArabicPresentationForms-A`|  
|<span data-ttu-id="4dc0b-583">FE00 - FE0F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-583">FE00 - FE0F</span></span>|`IsVariationSelectors`|  
|<span data-ttu-id="4dc0b-584">FE20 - FE2F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-584">FE20 - FE2F</span></span>|`IsCombiningHalfMarks`|  
|<span data-ttu-id="4dc0b-585">FE30 - FE4F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-585">FE30 - FE4F</span></span>|`IsCJKCompatibilityForms`|  
|<span data-ttu-id="4dc0b-586">FE50 - FE6F</span><span class="sxs-lookup"><span data-stu-id="4dc0b-586">FE50 - FE6F</span></span>|`IsSmallFormVariants`|  
|<span data-ttu-id="4dc0b-587">FE70 - FEFF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-587">FE70 - FEFF</span></span>|`IsArabicPresentationForms-B`|  
|<span data-ttu-id="4dc0b-588">FF00 - FFEF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-588">FF00 - FFEF</span></span>|`IsHalfwidthandFullwidthForms`|  
|<span data-ttu-id="4dc0b-589">FFF0 - FFFF</span><span class="sxs-lookup"><span data-stu-id="4dc0b-589">FFF0 - FFFF</span></span>|`IsSpecials`|  
  
 [<span data-ttu-id="4dc0b-590">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4dc0b-590">Back to Top</span></span>](#Top)  
  
<a name="CharacterClassSubtraction"></a>   
## <a name="character-class-subtraction-basegroup---excludedgroup"></a><span data-ttu-id="4dc0b-591">字元類別減法：[base_group - [excluded_group]]</span><span class="sxs-lookup"><span data-stu-id="4dc0b-591">Character Class Subtraction: [base_group - [excluded_group]]</span></span>  
 <span data-ttu-id="4dc0b-592">字元類別會定義字元集，</span><span class="sxs-lookup"><span data-stu-id="4dc0b-592">A character class defines a set of characters.</span></span> <span data-ttu-id="4dc0b-593">字元類別減法會產生字元集，這個字元集是將某一個字元類別中的字元從另一個字元類別中排除的結果。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-593">Character class subtraction yields a set of characters that is the result of excluding the characters in one character class from another character class.</span></span>  
  
 <span data-ttu-id="4dc0b-594">字元類別減法運算式的格式如下：</span><span class="sxs-lookup"><span data-stu-id="4dc0b-594">A character class subtraction expression has the following form:</span></span>  
  
 <span data-ttu-id="4dc0b-595">`[` *base_group* `-[` *excluded_group* `]]`</span><span class="sxs-lookup"><span data-stu-id="4dc0b-595">`[` *base_group* `-[` *excluded_group* `]]`</span></span>  
  
 <span data-ttu-id="4dc0b-596">方括號 (`[]`) 和連字號 (`-`) 為必要。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-596">The square brackets (`[]`) and hyphen (`-`) are mandatory.</span></span> <span data-ttu-id="4dc0b-597">*base_group* 是[正字元群組](#PositiveGroup)或[負字元群組](#NegativeGroup)。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-597">The *base_group* is a [positive character group](#PositiveGroup) or a [negative character group](#NegativeGroup).</span></span> <span data-ttu-id="4dc0b-598">*excluded_group* 元件是另一個正字元群組或負字元群組，或者是另一個字元類別減法運算式 (也就是說，您可以將字元類別減法運算式設為巢狀)。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-598">The *excluded_group* component is another positive or negative character group, or another character class subtraction expression (that is, you can nest character class subtraction expressions).</span></span>  
  
 <span data-ttu-id="4dc0b-599">例如，假設您有一個由 "a" 到 "z" 字元範圍組成的基底群組。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-599">For example, suppose you have a base group that consists of the character range from "a" through "z".</span></span> <span data-ttu-id="4dc0b-600">若要定義一組由基底群組所組成的字元，但不包括字元 "m"，則使用 `[a-z-[m]]`。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-600">To define the set of characters that consists of the base group except for the character "m", use `[a-z-[m]]`.</span></span> <span data-ttu-id="4dc0b-601">若要定義一組由基底群組所組成的字元，但不包括 "d"、"j" 和 "p" 這組字元，則使用 `[a-z-[djp]]`。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-601">To define the set of characters that consists of the base group except for the set of characters "d", "j", and "p", use `[a-z-[djp]]`.</span></span> <span data-ttu-id="4dc0b-602">若要定義一組由基底群組所組成的字元，但不包括 "m" 到 "p" 的字元範圍，則使用 `[a-z-[m-p]]`。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-602">To define the set of characters that consists of the base group except for the character range from "m" through "p", use `[a-z-[m-p]]`.</span></span>  
  
 <span data-ttu-id="4dc0b-603">請考慮使用巢狀字元類別減法運算式 `[a-z-[d-w-[m-o]]]`。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-603">Consider the nested character class subtraction expression, `[a-z-[d-w-[m-o]]]`.</span></span> <span data-ttu-id="4dc0b-604">這個運算式會從最內部的字元範圍向外評估。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-604">The expression is evaluated from the innermost character range outward.</span></span> <span data-ttu-id="4dc0b-605">首先從 "d" 到 "w" 字元範圍減去 "m" 到 "o" 字元範圍，這樣會產生從 "d" 到 "l" 及從 "p" 到 "w" 的字元集。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-605">First, the character range from "m" through "o" is subtracted from the character range "d" through "w", which yields the set of characters from "d" through "l" and "p" through "w".</span></span> <span data-ttu-id="4dc0b-606">接著會從字元範圍 "a" 到 "z" 中減去該字元集，此時會產生 `[abcmnoxyz]` 字元集。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-606">That set is then subtracted from the character range from "a" through "z", which yields the set of characters `[abcmnoxyz]`.</span></span>  
  
 <span data-ttu-id="4dc0b-607">您可以使用任何字元類別搭配字元類別減法。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-607">You can use any character class with character class subtraction.</span></span> <span data-ttu-id="4dc0b-608">若要定義由 \u0000 到 \uFFFF 的所有 Unicode 字元組成的字元集，但是不包含空白字元 (`\s`)、標點符號一般分類內的字元 (`\p{P}`)、`IsGreek` 具名區塊內的字元 (`\p{IsGreek}`) 以及 Unicode NEXT LINE 控制字元 (\x85)，請使用 `[\u0000-\uFFFF-[\s\p{P}\p{IsGreek}\x85]]`。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-608">To define the set of characters that consists of all Unicode characters from \u0000 through \uFFFF except white-space characters (`\s`), the characters in the punctuation general category (`\p{P}`), the characters in the `IsGreek` named block (`\p{IsGreek}`), and the Unicode NEXT LINE control character (\x85), use `[\u0000-\uFFFF-[\s\p{P}\p{IsGreek}\x85]]`.</span></span>  
  
 <span data-ttu-id="4dc0b-609">為字元類別減法運算式選擇將會產生有用結果的字元類別，</span><span class="sxs-lookup"><span data-stu-id="4dc0b-609">Choose character classes for a character class subtraction expression that will yield useful results.</span></span> <span data-ttu-id="4dc0b-610">避免選擇會產生空字元集的運算式，該運算式無法比對任何項目，也不要選擇相當於原始基底群組的運算式。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-610">Avoid an expression that yields an empty set of characters, which cannot match anything, or an expression that is equivalent to the original base group.</span></span> <span data-ttu-id="4dc0b-611">例如，空集合是 `[\p{IsBasicLatin}-[\x00-\x7F]]` 運算式的結果，該運算式會從 `IsBasicLatin` 一般分類中減去 `IsBasicLatin` 字元範圍中的所有字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-611">For example, the empty set is the result of the expression `[\p{IsBasicLatin}-[\x00-\x7F]]`, which subtracts all characters in the `IsBasicLatin` character range from the `IsBasicLatin` general category.</span></span> <span data-ttu-id="4dc0b-612">同樣地，原始基底群組是 `[a-z-[0-9]]` 運算式的結果。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-612">Similarly, the original base group is the result of the expression `[a-z-[0-9]]`.</span></span>  <span data-ttu-id="4dc0b-613">這是因為基底群組就是從 "a" 到 "z" 的字母字元範圍，該群組不包含已排除之群組中的任何字元，也就是從 "0" 到 "9" 的十進位數字字元範圍。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-613">This is because the base group, which is the character range of letters from "a" through "z", does not contain any characters in the excluded group, which is the character range of decimal digits from "0" through "9".</span></span>  
  
 <span data-ttu-id="4dc0b-614">下列範例會定義規則運算式 (`^[0-9-[2468]]+$`)，該運算式會比對輸入字串中的零和奇數數字。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-614">The following example defines a regular expression, `^[0-9-[2468]]+$`, that matches zero and odd digits in an input string.</span></span>  <span data-ttu-id="4dc0b-615">規則運算式的解譯方式如下表所示。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-615">The regular expression is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="4dc0b-616">元素</span><span class="sxs-lookup"><span data-stu-id="4dc0b-616">Element</span></span>|<span data-ttu-id="4dc0b-617">描述</span><span class="sxs-lookup"><span data-stu-id="4dc0b-617">Description</span></span>|  
|-------------|-----------------|  
|^|<span data-ttu-id="4dc0b-618">從輸入字串開頭開始比對。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-618">Begin the match at the start of the input string.</span></span>|  
|`[0-9-[2468]]+`|<span data-ttu-id="4dc0b-619">比對 0 到 9 中不包括 2、4、6 和 8 的任何出現一次或多次的字元。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-619">Match one or more occurrences of any character from 0 to 9 except for 2, 4, 6, and 8.</span></span> <span data-ttu-id="4dc0b-620">換句話說，就是比對出現一次或多次的零或奇數。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-620">In other words, match one or more occurrences of zero or an odd digit.</span></span>|  
|$|<span data-ttu-id="4dc0b-621">在輸入字串結尾結束比對。</span><span class="sxs-lookup"><span data-stu-id="4dc0b-621">End the match at the end of the input string.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/classsubtraction1.cs#15)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/classsubtraction1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="4dc0b-622">請參閱</span><span class="sxs-lookup"><span data-stu-id="4dc0b-622">See Also</span></span>  
 <xref:System.Char.GetUnicodeCategory%2A>  
 [<span data-ttu-id="4dc0b-623">規則運算式語言 - 快速參考</span><span class="sxs-lookup"><span data-stu-id="4dc0b-623">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 [<span data-ttu-id="4dc0b-624">規則運算式選項</span><span class="sxs-lookup"><span data-stu-id="4dc0b-624">Regular Expression Options</span></span>](../../../docs/standard/base-types/regular-expression-options.md)
