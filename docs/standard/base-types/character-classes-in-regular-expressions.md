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
ms.openlocfilehash: 0b70545c2252d6e8b82d6f4d57522ac4bb2481d8
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490881"
---
# <a name="character-classes-in-regular-expressions"></a><span data-ttu-id="15ee7-103">規則運算式中的字元類別</span><span class="sxs-lookup"><span data-stu-id="15ee7-103">Character classes in regular expressions</span></span>

<span data-ttu-id="15ee7-104">字元類別會定義一組字元，其中任何字元都可在輸入字串中出現，以便讓比對成功。</span><span class="sxs-lookup"><span data-stu-id="15ee7-104">A character class defines a set of characters, any one of which can occur in an input string for a match to succeed.</span></span> <span data-ttu-id="15ee7-105">.NET 中的規則運算式語言支援下列字元類別：</span><span class="sxs-lookup"><span data-stu-id="15ee7-105">The regular expression language in .NET supports the following character classes:</span></span>  
  
- <span data-ttu-id="15ee7-106">正字元群組。</span><span class="sxs-lookup"><span data-stu-id="15ee7-106">Positive character groups.</span></span> <span data-ttu-id="15ee7-107">輸入字串中的字元必須符合指定字元集的其中一個字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-107">A character in the input string must match one of a specified set of characters.</span></span> <span data-ttu-id="15ee7-108">如需詳細資訊，請參閱[正字元群組](#PositiveGroup)。</span><span class="sxs-lookup"><span data-stu-id="15ee7-108">For more information, see [Positive Character Group](#PositiveGroup).</span></span>  
  
- <span data-ttu-id="15ee7-109">負字元群組。</span><span class="sxs-lookup"><span data-stu-id="15ee7-109">Negative character groups.</span></span> <span data-ttu-id="15ee7-110">輸入字串中的字元不得符合指定字元集的其中一個字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-110">A character in the input string must not match one of a specified set of characters.</span></span> <span data-ttu-id="15ee7-111">如需詳細資訊，請參閱[負字元群組](#NegativeGroup)。</span><span class="sxs-lookup"><span data-stu-id="15ee7-111">For more information, see [Negative Character Group](#NegativeGroup).</span></span>  
  
- <span data-ttu-id="15ee7-112">任何字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-112">Any character.</span></span> <span data-ttu-id="15ee7-113">在規則運算式中的 `.` (點或句號) 字元是萬用字元，可符合 `\n` 以外的任何字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-113">The `.` (dot or period) character in a regular expression is a wildcard character that matches any character except `\n`.</span></span> <span data-ttu-id="15ee7-114">如需詳細資訊，請參閱[任何字元](#AnyCharacter)。</span><span class="sxs-lookup"><span data-stu-id="15ee7-114">For more information, see [Any Character](#AnyCharacter).</span></span>  
  
- <span data-ttu-id="15ee7-115">一般 Unicode 分類或具名區塊。</span><span class="sxs-lookup"><span data-stu-id="15ee7-115">A general Unicode category or named block.</span></span> <span data-ttu-id="15ee7-116">輸入字串中的字元必須是特定 Unicode 分類的成員，或者必須落在 Unicode 字元的連續範圍內，比對才會成功。</span><span class="sxs-lookup"><span data-stu-id="15ee7-116">A character in the input string must be a member of a particular Unicode category or must fall within a contiguous range of Unicode characters for a match to succeed.</span></span> <span data-ttu-id="15ee7-117">如需詳細資訊，請參閱 [Unicode 分類或 Unicode 區塊](#CategoryOrBlock)。</span><span class="sxs-lookup"><span data-stu-id="15ee7-117">For more information, see [Unicode Category or Unicode Block](#CategoryOrBlock).</span></span>  
  
- <span data-ttu-id="15ee7-118">負的一般 Unicode 分類或是具名區塊。</span><span class="sxs-lookup"><span data-stu-id="15ee7-118">A negative general Unicode category or named block.</span></span> <span data-ttu-id="15ee7-119">輸入字串中的字元不得是特定 Unicode 分類的成員，或者不得落在 Unicode 字元的連續範圍內，比對才會成功。</span><span class="sxs-lookup"><span data-stu-id="15ee7-119">A character in the input string must not be a member of a particular Unicode category or must not fall within a contiguous range of Unicode characters for a match to succeed.</span></span> <span data-ttu-id="15ee7-120">如需詳細資訊，請參閱[負 Unicode 分類或 Unicode 區塊](#NegativeCategoryOrBlock)。</span><span class="sxs-lookup"><span data-stu-id="15ee7-120">For more information, see [Negative Unicode Category or Unicode Block](#NegativeCategoryOrBlock).</span></span>  
  
- <span data-ttu-id="15ee7-121">文字字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-121">A word character.</span></span> <span data-ttu-id="15ee7-122">輸入字串中的字元可以隸屬於任何適用於文字字元的 Unicode 分類。</span><span class="sxs-lookup"><span data-stu-id="15ee7-122">A character in the input string can belong to any of the Unicode categories that are appropriate for characters in words.</span></span> <span data-ttu-id="15ee7-123">如需詳細資訊，請參閱[文字字元](#WordCharacter)。</span><span class="sxs-lookup"><span data-stu-id="15ee7-123">For more information, see [Word Character](#WordCharacter).</span></span>  
  
- <span data-ttu-id="15ee7-124">非文字字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-124">A non-word character.</span></span> <span data-ttu-id="15ee7-125">輸入字串中的字元可以隸屬於任何非文字字元的 Unicode 分類。</span><span class="sxs-lookup"><span data-stu-id="15ee7-125">A character in the input string can belong to any Unicode category that is not a word character.</span></span> <span data-ttu-id="15ee7-126">如需詳細資訊，請參閱[非文字字元](#NonWordCharacter)。</span><span class="sxs-lookup"><span data-stu-id="15ee7-126">For more information, see [Non-Word Character](#NonWordCharacter).</span></span>  
  
- <span data-ttu-id="15ee7-127">空白字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-127">A white-space character.</span></span> <span data-ttu-id="15ee7-128">輸入字串中的字元可以是任何 Unicode 分隔符號字元，以及任何一種控制字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-128">A character in the input string can be any Unicode separator character, as well as any one of a number of control characters.</span></span> <span data-ttu-id="15ee7-129">如需詳細資訊，請參閱[空白字元](#WhitespaceCharacter)。</span><span class="sxs-lookup"><span data-stu-id="15ee7-129">For more information, see [White-Space Character](#WhitespaceCharacter).</span></span>  
  
- <span data-ttu-id="15ee7-130">非空白字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-130">A non-white-space character.</span></span> <span data-ttu-id="15ee7-131">輸入字串中的字元可以是空白字元以外的任何字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-131">A character in the input string can be any character that is not a white-space character.</span></span> <span data-ttu-id="15ee7-132">如需詳細資訊，請參閱[非空白字元](#NonWhitespaceCharacter)。</span><span class="sxs-lookup"><span data-stu-id="15ee7-132">For more information, see [Non-White-Space Character](#NonWhitespaceCharacter).</span></span>  
  
- <span data-ttu-id="15ee7-133">十進位數字。</span><span class="sxs-lookup"><span data-stu-id="15ee7-133">A decimal digit.</span></span> <span data-ttu-id="15ee7-134">輸入字串中的字元可以是歸類為 Unicode 十進位數字的任何一個數字字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-134">A character in the input string can be any of a number of characters classified as Unicode decimal digits.</span></span> <span data-ttu-id="15ee7-135">如需詳細資訊，請參閱[十進位數字字元](#DigitCharacter)。</span><span class="sxs-lookup"><span data-stu-id="15ee7-135">For more information, see [Decimal Digit Character](#DigitCharacter).</span></span>  
  
- <span data-ttu-id="15ee7-136">非十進位數字。</span><span class="sxs-lookup"><span data-stu-id="15ee7-136">A non-decimal digit.</span></span> <span data-ttu-id="15ee7-137">輸入字串中的字元可以是 Unicode 十進位數字以外的任何字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-137">A character in the input string can be anything other than a Unicode decimal digit.</span></span> <span data-ttu-id="15ee7-138">如需詳細資訊，請參閱[十進位數字字元](#NonDigitCharacter)。</span><span class="sxs-lookup"><span data-stu-id="15ee7-138">For more information, see [Decimal Digit Character](#NonDigitCharacter).</span></span>  
  
 <span data-ttu-id="15ee7-139">.NET 支援字元類別減法運算式，可讓您將一組字元定義為從某個字元類別中排除另一個字元類別的結果。</span><span class="sxs-lookup"><span data-stu-id="15ee7-139">.NET supports character class subtraction expressions, which enables you to define a set of characters as the result of excluding one character class from another character class.</span></span> <span data-ttu-id="15ee7-140">如需詳細資訊，請參閱[字元類別減法](#CharacterClassSubtraction)。</span><span class="sxs-lookup"><span data-stu-id="15ee7-140">For more information, see [Character Class Subtraction](#CharacterClassSubtraction).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15ee7-141">依分類比對字元的字元類別 (例如，[\w](#WordCharacter) 會比對字組字元，或[\p{}](#CategoryOrBlock) 會比對 Unicode 分類) 會依賴 <xref:System.Globalization.CharUnicodeInfo> 類別來提供字元分類的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="15ee7-141">Character classes that match characters by category, such as [\w](#WordCharacter) to match word characters or [\p{}](#CategoryOrBlock) to match a Unicode category, rely on the <xref:System.Globalization.CharUnicodeInfo> class to provide information about character categories.</span></span>  <span data-ttu-id="15ee7-142">從 .NET Framework 4.6.2 開始，字元類別根據 [Unicode 標準 8.0.0 版](https://www.unicode.org/versions/Unicode8.0.0/)。</span><span class="sxs-lookup"><span data-stu-id="15ee7-142">Starting with the .NET Framework 4.6.2, character categories are based on [The Unicode Standard, Version 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/).</span></span> <span data-ttu-id="15ee7-143">在 .NET Framework 4 至 .NET Framework 4.6.1 中，則是根據 [Unicode 標準 6.3.0 版](https://www.unicode.org/versions/Unicode6.3.0/)。</span><span class="sxs-lookup"><span data-stu-id="15ee7-143">In the .NET Framework 4 through the .NET Framework 4.6.1, they are based on [The Unicode Standard, Version 6.3.0](https://www.unicode.org/versions/Unicode6.3.0/).</span></span>  
  
<a name="PositiveGroup"></a>   
## <a name="positive-character-group--"></a><span data-ttu-id="15ee7-144">正字元群組：[ ]</span><span class="sxs-lookup"><span data-stu-id="15ee7-144">Positive character group: [ ]</span></span>  
 <span data-ttu-id="15ee7-145">正字元群組會指定一份字元清單，其中任何字元都可出現在輸入字串中，以便出現相符項目。</span><span class="sxs-lookup"><span data-stu-id="15ee7-145">A positive character group specifies a list of characters, any one of which may appear in an input string for a match to occur.</span></span> <span data-ttu-id="15ee7-146">這份字元清單可以個別指定，也可以依範圍指定，或同時依兩種方式指定。</span><span class="sxs-lookup"><span data-stu-id="15ee7-146">This list of characters may be specified individually, as a range, or both.</span></span>  
  
 <span data-ttu-id="15ee7-147">指定個別字元清單的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="15ee7-147">The syntax for specifying a list of individual characters is as follows:</span></span>  

```  
[*character_group*]  
```

 <span data-ttu-id="15ee7-148">其中 *character_group* 是為了讓比對成功而可以出現在輸入字串中的個別字元清單。</span><span class="sxs-lookup"><span data-stu-id="15ee7-148">where *character_group* is a list of the individual characters that can appear in the input string for a match to succeed.</span></span> <span data-ttu-id="15ee7-149">*character_group*可以由一或多個常值字元、[逸出字元](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md)或字元類別的任何組合所構成。</span><span class="sxs-lookup"><span data-stu-id="15ee7-149">*character_group* can consist of any combination of one or more literal characters, [escape characters](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md), or character classes.</span></span>  
  
 <span data-ttu-id="15ee7-150">指定字元範圍的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="15ee7-150">The syntax for specifying a range of characters is as follows:</span></span>  
  
```  
[firstCharacter-lastCharacter]  
```  
  
 <span data-ttu-id="15ee7-151">其中 *firstCharacter* 是範圍開始的字元，而 *lastCharacter* 是範圍結束的字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-151">where *firstCharacter* is the character that begins the range and *lastCharacter* is the character that ends the range.</span></span> <span data-ttu-id="15ee7-152">字元範圍是指一系列連續的字元，定義的方式是指定系列中的第一個字元、連字號 (-)，然後是系列中的最後一個字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-152">A character range is a contiguous series of characters defined by specifying the first character in the series, a hyphen (-), and then the last character in the series.</span></span> <span data-ttu-id="15ee7-153">如果兩個字元具有相鄰的 Unicode 字碼指標，這兩個字元就是連續字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-153">Two characters are contiguous if they have adjacent Unicode code points.</span></span> <span data-ttu-id="15ee7-154">*firstCharacter* 必須是較低字碼指標的字元，*lastCharacter* 必須是較高字碼指標的字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-154">*firstCharacter* must be the character with the lower code point, and *lastCharacter* must be the character with the higher code point.</span></span>

> [!NOTE]
> <span data-ttu-id="15ee7-155">由於正字元群組可以包含一組字元和一個範圍的字元，因此連字號字元 (`-`) 會一律解譯成範圍分隔符號，除非該字元是群組的第一個或最後一個字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-155">Because a positive character group can include both a set of characters and a character range, a hyphen character (`-`) is always interpreted as the range separator unless it is the first or last character of the group.</span></span>

<span data-ttu-id="15ee7-156">下表列出一些包含正字元類別的常見規則運算式模式。</span><span class="sxs-lookup"><span data-stu-id="15ee7-156">Some common regular expression patterns that contain positive character classes are listed in the following table.</span></span>  
  
|<span data-ttu-id="15ee7-157">模式</span><span class="sxs-lookup"><span data-stu-id="15ee7-157">Pattern</span></span>|<span data-ttu-id="15ee7-158">說明</span><span class="sxs-lookup"><span data-stu-id="15ee7-158">Description</span></span>|  
|-------------|-----------------|  
|`[aeiou]`|<span data-ttu-id="15ee7-159">比對所有母音。</span><span class="sxs-lookup"><span data-stu-id="15ee7-159">Match all vowels.</span></span>|  
|`[\p{P}\d]`|<span data-ttu-id="15ee7-160">比對所有標點符號和十進位數字字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-160">Match all punctuation and decimal digit characters.</span></span>|  
|`[\s\p{P}]`|<span data-ttu-id="15ee7-161">比對所有空白字元與標點符號。</span><span class="sxs-lookup"><span data-stu-id="15ee7-161">Match all white space and punctuation.</span></span>|  
  
 <span data-ttu-id="15ee7-162">下列範例會定義包含字元 "a" 和 "e" 的正字元群組，因此輸入字串必須包含文字 "grey" 或 "gray" 且後面接著另一個文字，才會出現相符項目。</span><span class="sxs-lookup"><span data-stu-id="15ee7-162">The following example defines a positive character group that contains the characters "a" and "e" so that the input string must contain the words "grey" or "gray" followed by another word for a match to occur.</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/positivecharclasses.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/positivecharclasses.vb#1)]  
  
 <span data-ttu-id="15ee7-163">規則運算式 `gr[ae]y\s\S+?[\s|\p{P}]` 定義如下：</span><span class="sxs-lookup"><span data-stu-id="15ee7-163">The regular expression `gr[ae]y\s\S+?[\s|\p{P}]` is defined as follows:</span></span>  
  
|<span data-ttu-id="15ee7-164">模式</span><span class="sxs-lookup"><span data-stu-id="15ee7-164">Pattern</span></span>|<span data-ttu-id="15ee7-165">說明</span><span class="sxs-lookup"><span data-stu-id="15ee7-165">Description</span></span>|  
|-------------|-----------------|  
|`gr`|<span data-ttu-id="15ee7-166">比對常值字元 "gr"。</span><span class="sxs-lookup"><span data-stu-id="15ee7-166">Match the literal characters "gr".</span></span>|  
|`[ae]`|<span data-ttu-id="15ee7-167">比對 "a" 或 "e"。</span><span class="sxs-lookup"><span data-stu-id="15ee7-167">Match either an "a" or an "e".</span></span>|  
|`y\s`|<span data-ttu-id="15ee7-168">比對後面接著空白字元的常值字元 "y"。</span><span class="sxs-lookup"><span data-stu-id="15ee7-168">Match the literal character "y" followed by a white-space character.</span></span>|  
|`\S+?`|<span data-ttu-id="15ee7-169">比對一個或多個非空白字元，但越少越好。</span><span class="sxs-lookup"><span data-stu-id="15ee7-169">Match one or more non-white-space characters, but as few as possible.</span></span>|  
|`[\s\p{P}]`|<span data-ttu-id="15ee7-170">比對空白字元或標點符號。</span><span class="sxs-lookup"><span data-stu-id="15ee7-170">Match either a white-space character or a punctuation mark.</span></span>|  
  
 <span data-ttu-id="15ee7-171">下列範例將比對以任何大寫字母開頭的文字。</span><span class="sxs-lookup"><span data-stu-id="15ee7-171">The following example matches words that begin with any capital letter.</span></span> <span data-ttu-id="15ee7-172">範例將使用子運算式 `[A-Z]` 表示從 A 到 Z 的大寫字母範圍。</span><span class="sxs-lookup"><span data-stu-id="15ee7-172">It uses the subexpression `[A-Z]` to represent the range of capital letters from A to Z.</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/range.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/range.vb#3)]  
  
 <span data-ttu-id="15ee7-173">規則運算式 `\b[A-Z]\w*\b` 的定義如下表所示。</span><span class="sxs-lookup"><span data-stu-id="15ee7-173">The regular expression `\b[A-Z]\w*\b` is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="15ee7-174">模式</span><span class="sxs-lookup"><span data-stu-id="15ee7-174">Pattern</span></span>|<span data-ttu-id="15ee7-175">說明</span><span class="sxs-lookup"><span data-stu-id="15ee7-175">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="15ee7-176">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="15ee7-176">Start at a word boundary.</span></span>|  
|`[A-Z]`|<span data-ttu-id="15ee7-177">比對從 A 到 Z 的任何大寫字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-177">Match any uppercase character from A to Z.</span></span>|  
|`\w*`|<span data-ttu-id="15ee7-178">比對零個或多個文字字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-178">Match zero or more word characters.</span></span>|  
|`\b`|<span data-ttu-id="15ee7-179">比對字邊界。</span><span class="sxs-lookup"><span data-stu-id="15ee7-179">Match a word boundary.</span></span>|  
  
<a name="NegativeGroup"></a>   
## <a name="negative-character-group-"></a><span data-ttu-id="15ee7-180">負字元群組：[^]</span><span class="sxs-lookup"><span data-stu-id="15ee7-180">Negative character group: [^]</span></span>  
 <span data-ttu-id="15ee7-181">負字元群組會指定一份字元清單，其中任何字元不得出現在輸入字串中，才會出現相符項目。</span><span class="sxs-lookup"><span data-stu-id="15ee7-181">A negative character group specifies a list of characters that must not appear in an input string for a match to occur.</span></span> <span data-ttu-id="15ee7-182">字元清單可以個別指定，也可以依範圍指定，或同時依兩種方式指定。</span><span class="sxs-lookup"><span data-stu-id="15ee7-182">The list of characters may be specified individually, as a range, or both.</span></span>  
  
<span data-ttu-id="15ee7-183">指定個別字元清單的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="15ee7-183">The syntax for specifying a list of individual characters is as follows:</span></span>  

```
[*^character_group*]  
```

 <span data-ttu-id="15ee7-184">其中 *character_group* 是為了讓比對成功而不可出現在輸入字串中的個別字元清單。</span><span class="sxs-lookup"><span data-stu-id="15ee7-184">where *character_group* is a list of the individual characters that cannot appear in the input string for a match to succeed.</span></span> <span data-ttu-id="15ee7-185">*character_group*可以由一或多個常值字元、[逸出字元](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md)或字元類別的任何組合所構成。</span><span class="sxs-lookup"><span data-stu-id="15ee7-185">*character_group* can consist of any combination of one or more literal characters, [escape characters](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md), or character classes.</span></span>  
  
 <span data-ttu-id="15ee7-186">指定字元範圍的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="15ee7-186">The syntax for specifying a range of characters is as follows:</span></span>  

```
[^*firstCharacter*-*lastCharacter*]  
```

<span data-ttu-id="15ee7-187">其中 *firstCharacter* 是範圍開始的字元，而 *lastCharacter* 是範圍結束的字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-187">where *firstCharacter* is the character that begins the range and *lastCharacter* is the character that ends the range.</span></span> <span data-ttu-id="15ee7-188">字元範圍是指一系列連續的字元，定義的方式是指定系列中的第一個字元、連字號 (-)，然後是系列中的最後一個字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-188">A character range is a contiguous series of characters defined by specifying the first character in the series, a hyphen (-), and then the last character in the series.</span></span> <span data-ttu-id="15ee7-189">如果兩個字元具有相鄰的 Unicode 字碼指標，這兩個字元就是連續字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-189">Two characters are contiguous if they have adjacent Unicode code points.</span></span> <span data-ttu-id="15ee7-190">*firstCharacter* 必須是較低字碼指標的字元，*lastCharacter* 必須是較高字碼指標的字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-190">*firstCharacter* must be the character with the lower code point, and *lastCharacter* must be the character with the higher code point.</span></span>

> [!NOTE]
> <span data-ttu-id="15ee7-191">由於負字元群組可以包含一組字元和一個範圍的字元，因此連字號字元 (`-`) 會一律解譯成範圍分隔符號，除非該字元是群組的第一個或最後一個字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-191">Because a negative character group can include both a set of characters and a character range, a hyphen character (`-`) is always interpreted as the range separator unless it is the first or last character of the group.</span></span>
  
 <span data-ttu-id="15ee7-192">可以串連兩個或多個字元範圍。</span><span class="sxs-lookup"><span data-stu-id="15ee7-192">Two or more character ranges can be concatenated.</span></span> <span data-ttu-id="15ee7-193">例如，若要指定從 "0" 到 "9" 的十進位數字範圍、從 "a" 到 "f" 的小寫字母範圍，以及從 "A" 到 "F" 的大寫字母範圍，可以使用 `[0-9a-fA-F]`。</span><span class="sxs-lookup"><span data-stu-id="15ee7-193">For example, to specify the range of decimal digits from "0" through "9", the range of lowercase letters from "a" through "f", and the range of uppercase letters from "A" through "F", use `[0-9a-fA-F]`.</span></span>  
  
 <span data-ttu-id="15ee7-194">負字元群組中的前置 `^` 字元是必要的，它表示字元群組是負字元群組而非正字元群組。</span><span class="sxs-lookup"><span data-stu-id="15ee7-194">The leading carat character (`^`) in a negative character group is mandatory and indicates the character group is a negative character group instead of a positive character group.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="15ee7-195">較大規則運算式模式中的負字元群組不是零寬度的判斷提示。</span><span class="sxs-lookup"><span data-stu-id="15ee7-195">A negative character group in a larger regular expression pattern is not a zero-width assertion.</span></span> <span data-ttu-id="15ee7-196">也就是說，在評估負字元群組之後，規則運算式引擎會在輸入字串中前進一個字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-196">That is, after evaluating the negative character group, the regular expression engine advances one character in the input string.</span></span>  
  
 <span data-ttu-id="15ee7-197">下表列出一些包含負字元群組的常見規則運算式模式。</span><span class="sxs-lookup"><span data-stu-id="15ee7-197">Some common regular expression patterns that contain negative character groups are listed in the following table.</span></span>  
  
|<span data-ttu-id="15ee7-198">模式</span><span class="sxs-lookup"><span data-stu-id="15ee7-198">Pattern</span></span>|<span data-ttu-id="15ee7-199">說明</span><span class="sxs-lookup"><span data-stu-id="15ee7-199">Description</span></span>|  
|-------------|-----------------|  
|`[^aeiou]`|<span data-ttu-id="15ee7-200">比對除了母音之外的所有字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-200">Match all characters except vowels.</span></span>|  
|`[^\p{P}\d]`|<span data-ttu-id="15ee7-201">比對標點符號和十進位數字字元之外的所有字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-201">Match all characters except punctuation and decimal digit characters.</span></span>|  
  
 <span data-ttu-id="15ee7-202">下列範例將比對任何開頭字元是 "th" 且後面不是接著 "o" 的文字。</span><span class="sxs-lookup"><span data-stu-id="15ee7-202">The following example matches any word that begins with the characters "th" and is not followed by an "o".</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/negativecharclasses.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/negativecharclasses.vb#2)]  
  
 <span data-ttu-id="15ee7-203">規則運算式 `\bth[^o]\w+\b` 的定義如下表所示。</span><span class="sxs-lookup"><span data-stu-id="15ee7-203">The regular expression `\bth[^o]\w+\b` is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="15ee7-204">模式</span><span class="sxs-lookup"><span data-stu-id="15ee7-204">Pattern</span></span>|<span data-ttu-id="15ee7-205">說明</span><span class="sxs-lookup"><span data-stu-id="15ee7-205">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="15ee7-206">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="15ee7-206">Start at a word boundary.</span></span>|  
|`th`|<span data-ttu-id="15ee7-207">比對常值字元 "th"。</span><span class="sxs-lookup"><span data-stu-id="15ee7-207">Match the literal characters "th".</span></span>|  
|`[^o]`|<span data-ttu-id="15ee7-208">比對不是 "o" 的任何字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-208">Match any character that is not an "o".</span></span>|  
|`\w+`|<span data-ttu-id="15ee7-209">比對一個或多個文字字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-209">Match one or more word characters.</span></span>|  
|`\b`|<span data-ttu-id="15ee7-210">在字邊界結束。</span><span class="sxs-lookup"><span data-stu-id="15ee7-210">End at a word boundary.</span></span>|  
  
<a name="AnyCharacter"></a>   
## <a name="any-character-"></a><span data-ttu-id="15ee7-211">任何字元：.</span><span class="sxs-lookup"><span data-stu-id="15ee7-211">Any character: .</span></span>  
 <span data-ttu-id="15ee7-212">句號字元 (.) 會比對 `\n` (新行字元 \u000A) 以外任何具有下列兩項資格的字元：</span><span class="sxs-lookup"><span data-stu-id="15ee7-212">The period character (.) matches any character except `\n` (the newline character, \u000A), with the following two qualifications:</span></span>  
  
- <span data-ttu-id="15ee7-213">如果 <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> 選項修改了規則運算式模式，或是 `.` 選項修改了模式中包含 `s` 字元類別的部分，`.` 就會符合任何字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-213">If a regular expression pattern is modified by the <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> option, or if the portion of the pattern that contains the `.` character class is modified by the `s` option, `.` matches any character.</span></span> <span data-ttu-id="15ee7-214">如需詳細資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)。</span><span class="sxs-lookup"><span data-stu-id="15ee7-214">For more information, see [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
     <span data-ttu-id="15ee7-215">下列範例將示範 `.` 字元類別的預設行為與使用 <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> 選項的行為有何不同。</span><span class="sxs-lookup"><span data-stu-id="15ee7-215">The following example illustrates the different behavior of the `.` character class by default and with the <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> option.</span></span> <span data-ttu-id="15ee7-216">規則運算式 `^.+` 會從字串開頭開始，比對每一個字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-216">The regular expression `^.+` starts at the beginning of the string and matches every character.</span></span> <span data-ttu-id="15ee7-217">根據預設，比對會在第一行結尾結束。規則運算式模式會比對歸位字元 `\r` 或 \u000D，但不會比對 `\n`。</span><span class="sxs-lookup"><span data-stu-id="15ee7-217">By default, the match ends at the end of the first line; the regular expression pattern matches the carriage return character, `\r` or \u000D, but it does not match `\n`.</span></span> <span data-ttu-id="15ee7-218">由於 <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> 選項會將整個輸入字串解譯為單行，因此它會比對輸入字串中的每個字元，包括 `\n`。</span><span class="sxs-lookup"><span data-stu-id="15ee7-218">Because the <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> option interprets the entire input string as a single line, it matches every character in the input string, including `\n`.</span></span>  
  
     [!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
     [!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]  
  
> [!NOTE]
>  <span data-ttu-id="15ee7-219">由於它會比對 `\n` 以外的任何字元，因此 `.` 字元類別也會比對 `\r` (歸位字元 \u000D)。</span><span class="sxs-lookup"><span data-stu-id="15ee7-219">Because it matches any character except `\n`, the `.` character class also matches `\r` (the carriage return character, \u000D).</span></span>  
  
- <span data-ttu-id="15ee7-220">在正或負字元群組中，句號會視為常值句號字元而非字元類別。</span><span class="sxs-lookup"><span data-stu-id="15ee7-220">In a positive or negative character group, a period is treated as a literal period character, and not as a character class.</span></span> <span data-ttu-id="15ee7-221">如需詳細資訊，請參閱本主題前段的[正字元群組](#PositiveGroup)和[負字元群組](#NegativeGroup)。</span><span class="sxs-lookup"><span data-stu-id="15ee7-221">For more information, see [Positive Character Group](#PositiveGroup) and [Negative Character Group](#NegativeGroup) earlier in this topic.</span></span> <span data-ttu-id="15ee7-222">下列範例將進行示範，定義包含句號字元 (`.`) 做為字元類別以及做為正字元群組成員的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="15ee7-222">The following example provides an illustration by defining a regular expression that includes the period character (`.`) both as a character class and as a member of a positive character group.</span></span> <span data-ttu-id="15ee7-223">規則運算式 `\b.*[.?!;:](\s|\z)` 會從字邊界開始比對所有字元，直到遇到包括句號的五個標點符號其中之一，然後比對空白字元或字串結尾。</span><span class="sxs-lookup"><span data-stu-id="15ee7-223">The regular expression `\b.*[.?!;:](\s|\z)` begins at a word boundary, matches any character until it encounters one of five punctuation marks, including a period, and then matches either a white-space character or the end of the string.</span></span>  
  
     [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any1.cs#4)]
     [!code-vb[Conceptual.RegEx.Language.CharacterClasses#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any1.vb#4)]  
  
> [!NOTE]
>  <span data-ttu-id="15ee7-224">由於它會比對任何字元，因此如果規則運算式模式嘗試多次比對任何字元，`.` 語言項目就會經常與 lazy 數量詞搭配使用。</span><span class="sxs-lookup"><span data-stu-id="15ee7-224">Because it matches any character, the `.` language element is often used with a lazy quantifier if a regular expression pattern attempts to match any character multiple times.</span></span> <span data-ttu-id="15ee7-225">如需詳細資訊，請參閱[數量詞](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="15ee7-225">For more information, see [Quantifiers](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).</span></span>  
  
<a name="CategoryOrBlock"></a>   
## <a name="unicode-category-or-unicode-block-p"></a><span data-ttu-id="15ee7-226">Unicode 類別或 Unicode 區塊：\p{}</span><span class="sxs-lookup"><span data-stu-id="15ee7-226">Unicode category or Unicode block: \p{}</span></span>  
 <span data-ttu-id="15ee7-227">Unicode 標準會為每個字元指派一種一般分類。</span><span class="sxs-lookup"><span data-stu-id="15ee7-227">The Unicode standard assigns each character a general category.</span></span> <span data-ttu-id="15ee7-228">例如，特定字元可以是大寫字母 (以 `Lu` 分類表示)、十進位數字 (`Nd` 分類)、數學符號 (`Sm` 分類) 或段落分隔符號 (`Zl` 分類)。</span><span class="sxs-lookup"><span data-stu-id="15ee7-228">For example, a particular character can be an uppercase letter (represented by the `Lu` category), a decimal digit (the `Nd` category), a math symbol (the `Sm` category), or a paragraph separator (the `Zl` category).</span></span> <span data-ttu-id="15ee7-229">Unicode 標準中的特定字元集也會佔據連續字碼指標的特定範圍或區塊。</span><span class="sxs-lookup"><span data-stu-id="15ee7-229">Specific character sets in the Unicode standard also occupy a specific range or block of consecutive code points.</span></span> <span data-ttu-id="15ee7-230">例如，從 \u0000 到 \u007F 可找到基本拉丁字元集，從 \u0600 到 \u06FF 則可找到阿拉伯字元集。</span><span class="sxs-lookup"><span data-stu-id="15ee7-230">For example, the basic Latin character set is found from \u0000 through \u007F, while the Arabic character set is found from \u0600 through \u06FF.</span></span>  
  
 <span data-ttu-id="15ee7-231">規則運算式建構</span><span class="sxs-lookup"><span data-stu-id="15ee7-231">The regular expression construct</span></span>  
  
 <span data-ttu-id="15ee7-232">`\p{` *name* `}`</span><span class="sxs-lookup"><span data-stu-id="15ee7-232">`\p{` *name* `}`</span></span>  
  
 <span data-ttu-id="15ee7-233">比對屬於 Unicode 一般分類或具名區塊的任何字元，其中 *name* 是分類縮寫或具名區塊名稱。</span><span class="sxs-lookup"><span data-stu-id="15ee7-233">matches any character that belongs to a Unicode general category or named block, where *name* is the category abbreviation or named block name.</span></span> <span data-ttu-id="15ee7-234">如需分類縮寫的清單，請參閱本主題稍後的[支援的 Unicode 一般分類](#SupportedUnicodeGeneralCategories)一節。</span><span class="sxs-lookup"><span data-stu-id="15ee7-234">For a list of category abbreviations, see the [Supported Unicode General Categories](#SupportedUnicodeGeneralCategories) section later in this topic.</span></span> <span data-ttu-id="15ee7-235">如需具名區塊清單，請參閱本主題稍後的[支援的具名區塊](#SupportedNamedBlocks)一節。</span><span class="sxs-lookup"><span data-stu-id="15ee7-235">For a list of named blocks, see the [Supported Named Blocks](#SupportedNamedBlocks) section later in this topic.</span></span>  
  
 <span data-ttu-id="15ee7-236">下列範例會使用 `\p{`*name*`}` 建構同時比對 Unicode 一般類別 (在這個案例中是 `Pd`，或稱 Punctuation, Dash 分類) 以及具名區塊 (`IsGreek` 和 `IsBasicLatin` 具名區塊)。</span><span class="sxs-lookup"><span data-stu-id="15ee7-236">The following example uses the `\p{`*name*`}` construct to match both a Unicode general category (in this case, the `Pd`, or Punctuation, Dash category) and a named block (the `IsGreek` and `IsBasicLatin` named blocks).</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/category1.cs#6)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/category1.vb#6)]  
  
 <span data-ttu-id="15ee7-237">規則運算式 `\b(\p{IsGreek}+(\s)?)+\p{Pd}\s(\p{IsBasicLatin}+(\s)?)+` 的定義如下表所示。</span><span class="sxs-lookup"><span data-stu-id="15ee7-237">The regular expression `\b(\p{IsGreek}+(\s)?)+\p{Pd}\s(\p{IsBasicLatin}+(\s)?)+` is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="15ee7-238">模式</span><span class="sxs-lookup"><span data-stu-id="15ee7-238">Pattern</span></span>|<span data-ttu-id="15ee7-239">說明</span><span class="sxs-lookup"><span data-stu-id="15ee7-239">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="15ee7-240">從字緣開始。</span><span class="sxs-lookup"><span data-stu-id="15ee7-240">Start at a word boundary.</span></span>|  
|`\p{IsGreek}+`|<span data-ttu-id="15ee7-241">比對一個或多個希臘字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-241">Match one or more Greek characters.</span></span>|  
|`(\s)?`|<span data-ttu-id="15ee7-242">比對零個或一個空白字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-242">Match zero or one white-space character.</span></span>|  
|`(\p{IsGreek}+(\s)?)+`|<span data-ttu-id="15ee7-243">一次或多次比對一個或多個希臘字元後面接著零或一個空白字元的模式。</span><span class="sxs-lookup"><span data-stu-id="15ee7-243">Match the pattern of one or more Greek characters followed by zero or one white-space characters one or more times.</span></span>|  
|`\p{Pd}`|<span data-ttu-id="15ee7-244">比對標點符號、虛線字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-244">Match a Punctuation, Dash character.</span></span>|  
|`\s`|<span data-ttu-id="15ee7-245">比對空白字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-245">Match a white-space character.</span></span>|  
|`\p{IsBasicLatin}+`|<span data-ttu-id="15ee7-246">比對一個或多個基本拉丁字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-246">Match one or more basic Latin characters.</span></span>|  
|`(\s)?`|<span data-ttu-id="15ee7-247">比對零個或一個空白字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-247">Match zero or one white-space character.</span></span>|  
|`(\p{IsBasicLatin}+(\s)?)+`|<span data-ttu-id="15ee7-248">一次或多次比對一個或多個基本拉丁字元後面接著零個或一個空白字元的模式。</span><span class="sxs-lookup"><span data-stu-id="15ee7-248">Match the pattern of one or more basic Latin characters followed by zero or one white-space characters one or more times.</span></span>|  
  
<a name="NegativeCategoryOrBlock"></a>   
## <a name="negative-unicode-category-or-unicode-block-p"></a><span data-ttu-id="15ee7-249">負 Unicode 類別或 Unicode 區塊：\P{}</span><span class="sxs-lookup"><span data-stu-id="15ee7-249">Negative Unicode category or Unicode block: \P{}</span></span>  
 <span data-ttu-id="15ee7-250">Unicode 標準會為每個字元指派一種一般分類。</span><span class="sxs-lookup"><span data-stu-id="15ee7-250">The Unicode standard assigns each character a general category.</span></span> <span data-ttu-id="15ee7-251">例如，特定字元可以是大寫字母 (以 `Lu` 分類表示)、十進位數字 (`Nd` 分類)、數學符號 (`Sm` 分類) 或段落分隔符號 (`Zl` 分類)。</span><span class="sxs-lookup"><span data-stu-id="15ee7-251">For example, a particular character can be an uppercase letter (represented by the `Lu` category), a decimal digit (the `Nd` category), a math symbol (the `Sm` category), or a paragraph separator (the `Zl` category).</span></span> <span data-ttu-id="15ee7-252">Unicode 標準中的特定字元集也會佔據連續字碼指標的特定範圍或區塊。</span><span class="sxs-lookup"><span data-stu-id="15ee7-252">Specific character sets in the Unicode standard also occupy a specific range or block of consecutive code points.</span></span> <span data-ttu-id="15ee7-253">例如，從 \u0000 到 \u007F 可找到基本拉丁字元集，從 \u0600 到 \u06FF 則可找到阿拉伯字元集。</span><span class="sxs-lookup"><span data-stu-id="15ee7-253">For example, the basic Latin character set is found from \u0000 through \u007F, while the Arabic character set is found from \u0600 through \u06FF.</span></span>  
  
 <span data-ttu-id="15ee7-254">規則運算式建構</span><span class="sxs-lookup"><span data-stu-id="15ee7-254">The regular expression construct</span></span>  
  
 <span data-ttu-id="15ee7-255">`\P{` *name* `}`</span><span class="sxs-lookup"><span data-stu-id="15ee7-255">`\P{` *name* `}`</span></span>  
  
 <span data-ttu-id="15ee7-256">比對任何不屬於 Unicode 一般分類或具名區塊的字元，其中 *name* 是分類縮寫或是具名區塊名稱。</span><span class="sxs-lookup"><span data-stu-id="15ee7-256">matches any character that does not belong to a Unicode general category or named block, where *name* is the category abbreviation or named block name.</span></span> <span data-ttu-id="15ee7-257">如需分類縮寫的清單，請參閱本主題稍後的[支援的 Unicode 一般分類](#SupportedUnicodeGeneralCategories)一節。</span><span class="sxs-lookup"><span data-stu-id="15ee7-257">For a list of category abbreviations, see the [Supported Unicode General Categories](#SupportedUnicodeGeneralCategories) section later in this topic.</span></span> <span data-ttu-id="15ee7-258">如需具名區塊清單，請參閱本主題稍後的[支援的具名區塊](#SupportedNamedBlocks)一節。</span><span class="sxs-lookup"><span data-stu-id="15ee7-258">For a list of named blocks, see the [Supported Named Blocks](#SupportedNamedBlocks) section later in this topic.</span></span>  
  
 <span data-ttu-id="15ee7-259">下列範例會使用 `\P{`*name*`}` 建構從數值字串中移除任何貨幣符號 (在這個案例中是 `Sc`，或稱 [符號、貨幣] 分類)。</span><span class="sxs-lookup"><span data-stu-id="15ee7-259">The following example uses the `\P{`*name*`}` construct to remove any currency symbols (in this case, the `Sc`, or Symbol, Currency category) from numeric strings.</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/notcategory1.cs#7)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/notcategory1.vb#7)]  
  
 <span data-ttu-id="15ee7-260">規則運算式模式 `(\P{Sc})+` 會比對一個或多個不是貨幣符號的字元，並且會有效移除結果字串中的所有貨幣符號。</span><span class="sxs-lookup"><span data-stu-id="15ee7-260">The regular expression pattern `(\P{Sc})+` matches one or more characters that are not currency symbols; it effectively strips any currency symbol from the result string.</span></span>  
  
<a name="WordCharacter"></a>   
## <a name="word-character-w"></a><span data-ttu-id="15ee7-261">文字字元：\w</span><span class="sxs-lookup"><span data-stu-id="15ee7-261">Word character: \w</span></span>  
 <span data-ttu-id="15ee7-262">`\w` 會比對任何文字字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-262">`\w` matches any word character.</span></span> <span data-ttu-id="15ee7-263">文字字元是下表中所列的任何 Unicode 分類的成員。</span><span class="sxs-lookup"><span data-stu-id="15ee7-263">A word character is a member of any of the Unicode categories listed in the following table.</span></span>  
  
|<span data-ttu-id="15ee7-264">分類</span><span class="sxs-lookup"><span data-stu-id="15ee7-264">Category</span></span>|<span data-ttu-id="15ee7-265">說明</span><span class="sxs-lookup"><span data-stu-id="15ee7-265">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="15ee7-266">Ll</span><span class="sxs-lookup"><span data-stu-id="15ee7-266">Ll</span></span>|<span data-ttu-id="15ee7-267">字母、小寫</span><span class="sxs-lookup"><span data-stu-id="15ee7-267">Letter, Lowercase</span></span>|  
|<span data-ttu-id="15ee7-268">Lu</span><span class="sxs-lookup"><span data-stu-id="15ee7-268">Lu</span></span>|<span data-ttu-id="15ee7-269">字母、大寫</span><span class="sxs-lookup"><span data-stu-id="15ee7-269">Letter, Uppercase</span></span>|  
|<span data-ttu-id="15ee7-270">Lt</span><span class="sxs-lookup"><span data-stu-id="15ee7-270">Lt</span></span>|<span data-ttu-id="15ee7-271">字母、字首大寫</span><span class="sxs-lookup"><span data-stu-id="15ee7-271">Letter, Titlecase</span></span>|  
|<span data-ttu-id="15ee7-272">Lo</span><span class="sxs-lookup"><span data-stu-id="15ee7-272">Lo</span></span>|<span data-ttu-id="15ee7-273">字母、其他</span><span class="sxs-lookup"><span data-stu-id="15ee7-273">Letter, Other</span></span>|  
|<span data-ttu-id="15ee7-274">Lm</span><span class="sxs-lookup"><span data-stu-id="15ee7-274">Lm</span></span>|<span data-ttu-id="15ee7-275">字母、修飾詞</span><span class="sxs-lookup"><span data-stu-id="15ee7-275">Letter, Modifier</span></span>|  
|<span data-ttu-id="15ee7-276">Mn</span><span class="sxs-lookup"><span data-stu-id="15ee7-276">Mn</span></span>|<span data-ttu-id="15ee7-277">記號，非間距</span><span class="sxs-lookup"><span data-stu-id="15ee7-277">Mark, Nonspacing</span></span>|  
|<span data-ttu-id="15ee7-278">Nd</span><span class="sxs-lookup"><span data-stu-id="15ee7-278">Nd</span></span>|<span data-ttu-id="15ee7-279">數字、十進位數字</span><span class="sxs-lookup"><span data-stu-id="15ee7-279">Number, Decimal Digit</span></span>|  
|<span data-ttu-id="15ee7-280">Pc</span><span class="sxs-lookup"><span data-stu-id="15ee7-280">Pc</span></span>|<span data-ttu-id="15ee7-281">標點符號、連接器。</span><span class="sxs-lookup"><span data-stu-id="15ee7-281">Punctuation, Connector.</span></span> <span data-ttu-id="15ee7-282">這個分類包含十個字元，其中最常用的是 LOWLINE 字元 (_)，u+005F。</span><span class="sxs-lookup"><span data-stu-id="15ee7-282">This category includes ten characters, the most commonly used of which is the LOWLINE character (_), u+005F.</span></span>|  
  
 <span data-ttu-id="15ee7-283">如果指定了符合 ECMAScript 的行為，`\w` 就等於 `[a-zA-Z_0-9]`。</span><span class="sxs-lookup"><span data-stu-id="15ee7-283">If ECMAScript-compliant behavior is specified, `\w` is equivalent to `[a-zA-Z_0-9]`.</span></span> <span data-ttu-id="15ee7-284">如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)中的＜ECMAScript 相符行為＞一節。</span><span class="sxs-lookup"><span data-stu-id="15ee7-284">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15ee7-285">由於它會比對任何文字字元，因此，如果規則運算式模式嘗試多次比對任何文字字元且後面接著特定文字字元，`\w` 語言項目就會經常與 lazy 數量詞搭配使用。</span><span class="sxs-lookup"><span data-stu-id="15ee7-285">Because it matches any word character, the `\w` language element is often used with a lazy quantifier if a regular expression pattern attempts to match any word character multiple times, followed by a specific word character.</span></span> <span data-ttu-id="15ee7-286">如需詳細資訊，請參閱[數量詞](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="15ee7-286">For more information, see [Quantifiers](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="15ee7-287">下列範例會使用 `\w` 語言項目比對文字中重複的字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-287">The following example uses the `\w` language element to match duplicate characters in a word.</span></span> <span data-ttu-id="15ee7-288">這個範例會定義規則運算式模式 `(\w)\1`，該模式解譯如下。</span><span class="sxs-lookup"><span data-stu-id="15ee7-288">The example defines a regular expression pattern, `(\w)\1`, which can be interpreted as follows.</span></span>  
  
|<span data-ttu-id="15ee7-289">元素</span><span class="sxs-lookup"><span data-stu-id="15ee7-289">Element</span></span>|<span data-ttu-id="15ee7-290">說明</span><span class="sxs-lookup"><span data-stu-id="15ee7-290">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="15ee7-291">(\w)</span><span class="sxs-lookup"><span data-stu-id="15ee7-291">(\w)</span></span>|<span data-ttu-id="15ee7-292">比對文字字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-292">Match a word character.</span></span> <span data-ttu-id="15ee7-293">這是第一個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="15ee7-293">This is the first capturing group.</span></span>|  
|<span data-ttu-id="15ee7-294">\1</span><span class="sxs-lookup"><span data-stu-id="15ee7-294">\1</span></span>|<span data-ttu-id="15ee7-295">比對第一個擷取的值。</span><span class="sxs-lookup"><span data-stu-id="15ee7-295">Match the value of the first capture.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/wordchar1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/wordchar1.vb#8)]  
  
<a name="NonWordCharacter"></a>   
## <a name="non-word-character-w"></a><span data-ttu-id="15ee7-296">非文字字元：\W</span><span class="sxs-lookup"><span data-stu-id="15ee7-296">Non-word character: \W</span></span>  
 <span data-ttu-id="15ee7-297">`\W` 會比對任何非文字字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-297">`\W` matches any non-word character.</span></span> <span data-ttu-id="15ee7-298">\W 語言項目相當於下列字元類別：</span><span class="sxs-lookup"><span data-stu-id="15ee7-298">The \W language element is equivalent to the following character class:</span></span>  
  
```  
[^\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]  
```  
  
 <span data-ttu-id="15ee7-299">換句話說，它會比對下表所列 Unicode 分類中字元以外的所有字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-299">In other words, it matches any character except for those in the Unicode categories listed in the following table.</span></span>  
  
|<span data-ttu-id="15ee7-300">分類</span><span class="sxs-lookup"><span data-stu-id="15ee7-300">Category</span></span>|<span data-ttu-id="15ee7-301">說明</span><span class="sxs-lookup"><span data-stu-id="15ee7-301">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="15ee7-302">Ll</span><span class="sxs-lookup"><span data-stu-id="15ee7-302">Ll</span></span>|<span data-ttu-id="15ee7-303">字母、小寫</span><span class="sxs-lookup"><span data-stu-id="15ee7-303">Letter, Lowercase</span></span>|  
|<span data-ttu-id="15ee7-304">Lu</span><span class="sxs-lookup"><span data-stu-id="15ee7-304">Lu</span></span>|<span data-ttu-id="15ee7-305">字母、大寫</span><span class="sxs-lookup"><span data-stu-id="15ee7-305">Letter, Uppercase</span></span>|  
|<span data-ttu-id="15ee7-306">Lt</span><span class="sxs-lookup"><span data-stu-id="15ee7-306">Lt</span></span>|<span data-ttu-id="15ee7-307">字母、字首大寫</span><span class="sxs-lookup"><span data-stu-id="15ee7-307">Letter, Titlecase</span></span>|  
|<span data-ttu-id="15ee7-308">Lo</span><span class="sxs-lookup"><span data-stu-id="15ee7-308">Lo</span></span>|<span data-ttu-id="15ee7-309">字母、其他</span><span class="sxs-lookup"><span data-stu-id="15ee7-309">Letter, Other</span></span>|  
|<span data-ttu-id="15ee7-310">Lm</span><span class="sxs-lookup"><span data-stu-id="15ee7-310">Lm</span></span>|<span data-ttu-id="15ee7-311">字母、修飾詞</span><span class="sxs-lookup"><span data-stu-id="15ee7-311">Letter, Modifier</span></span>|  
|<span data-ttu-id="15ee7-312">Mn</span><span class="sxs-lookup"><span data-stu-id="15ee7-312">Mn</span></span>|<span data-ttu-id="15ee7-313">記號，非間距</span><span class="sxs-lookup"><span data-stu-id="15ee7-313">Mark, Nonspacing</span></span>|  
|<span data-ttu-id="15ee7-314">Nd</span><span class="sxs-lookup"><span data-stu-id="15ee7-314">Nd</span></span>|<span data-ttu-id="15ee7-315">數字、十進位數字</span><span class="sxs-lookup"><span data-stu-id="15ee7-315">Number, Decimal Digit</span></span>|  
|<span data-ttu-id="15ee7-316">Pc</span><span class="sxs-lookup"><span data-stu-id="15ee7-316">Pc</span></span>|<span data-ttu-id="15ee7-317">標點符號、連接器。</span><span class="sxs-lookup"><span data-stu-id="15ee7-317">Punctuation, Connector.</span></span> <span data-ttu-id="15ee7-318">這個分類包含十個字元，其中最常用的是 LOWLINE 字元 (_)，u+005F。</span><span class="sxs-lookup"><span data-stu-id="15ee7-318">This category includes ten characters, the most commonly used of which is the LOWLINE character (_), u+005F.</span></span>|  
  
 <span data-ttu-id="15ee7-319">如果指定了符合 ECMAScript 的行為，`\W` 就等於 `[^a-zA-Z_0-9]`。</span><span class="sxs-lookup"><span data-stu-id="15ee7-319">If ECMAScript-compliant behavior is specified, `\W` is equivalent to `[^a-zA-Z_0-9]`.</span></span> <span data-ttu-id="15ee7-320">如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)中的＜ECMAScript 相符行為＞一節。</span><span class="sxs-lookup"><span data-stu-id="15ee7-320">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15ee7-321">由於它會比對任何非文字字元，因此，如果規則運算式模式嘗試多次比對任何非文字字元，且後面接著特定非文字字元，`\W` 語言項目就會經常與 lazy 數量詞搭配使用。</span><span class="sxs-lookup"><span data-stu-id="15ee7-321">Because it matches any non-word character, the `\W` language element is often used with a lazy quantifier if a regular expression pattern attempts to match any non-word character multiple times followed by a specific non-word character.</span></span> <span data-ttu-id="15ee7-322">如需詳細資訊，請參閱[數量詞](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="15ee7-322">For more information, see [Quantifiers](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="15ee7-323">以下範例將說明 `\W` 字元類別。</span><span class="sxs-lookup"><span data-stu-id="15ee7-323">The following example illustrates the `\W` character class.</span></span>  <span data-ttu-id="15ee7-324">它會定義規則運算式模式 `\b(\w+)(\W){1,2}`，該模式會比對後面接一個或多個非文字字元的文字，例如空白字元或標點符號。</span><span class="sxs-lookup"><span data-stu-id="15ee7-324">It defines a regular expression pattern, `\b(\w+)(\W){1,2}`, that matches a word followed by one or two non-word characters, such as white space or punctuation.</span></span> <span data-ttu-id="15ee7-325">規則運算式的解譯方式如下表所示。</span><span class="sxs-lookup"><span data-stu-id="15ee7-325">The regular expression is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="15ee7-326">元素</span><span class="sxs-lookup"><span data-stu-id="15ee7-326">Element</span></span>|<span data-ttu-id="15ee7-327">說明</span><span class="sxs-lookup"><span data-stu-id="15ee7-327">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="15ee7-328">\b</span><span class="sxs-lookup"><span data-stu-id="15ee7-328">\b</span></span>|<span data-ttu-id="15ee7-329">開始字緣比對。</span><span class="sxs-lookup"><span data-stu-id="15ee7-329">Begin the match at a word boundary.</span></span>|  
|<span data-ttu-id="15ee7-330">(\w+)</span><span class="sxs-lookup"><span data-stu-id="15ee7-330">(\w+)</span></span>|<span data-ttu-id="15ee7-331">比對一個或多個文字字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-331">Match one or more word characters.</span></span> <span data-ttu-id="15ee7-332">這是第一個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="15ee7-332">This is the first capturing group.</span></span>|  
|<span data-ttu-id="15ee7-333">(\W){1,2}</span><span class="sxs-lookup"><span data-stu-id="15ee7-333">(\W){1,2}</span></span>|<span data-ttu-id="15ee7-334">比對一次或兩次非文字字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-334">Match a non-word character either one or two times.</span></span> <span data-ttu-id="15ee7-335">這是第二個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="15ee7-335">This is the second capturing group.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nonwordchar1.cs#9)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nonwordchar1.vb#9)]  
  
 <span data-ttu-id="15ee7-336">由於第二個擷取群組的 <xref:System.Text.RegularExpressions.Group> 物件只包含單一擷取的非文字字元，因此這個範例會從 <xref:System.Text.RegularExpressions.CaptureCollection> 屬性所傳回之 <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> 物件擷取所有擷取的非文字字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-336">Because the <xref:System.Text.RegularExpressions.Group> object for the second capturing group contains only a single captured non-word character, the example retrieves all captured non-word characters from the <xref:System.Text.RegularExpressions.CaptureCollection> object that is returned by the <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> property.</span></span>  
  
<a name="WhitespaceCharacter"></a>   
## <a name="whitespace-character-s"></a><span data-ttu-id="15ee7-337">空白字元：\s</span><span class="sxs-lookup"><span data-stu-id="15ee7-337">Whitespace character: \s</span></span>  
 <span data-ttu-id="15ee7-338">`\s` 會比對任何空白字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-338">`\s` matches any whitespace character.</span></span> <span data-ttu-id="15ee7-339">它相當於下表列出的逸出序列和 Unicode 分類。</span><span class="sxs-lookup"><span data-stu-id="15ee7-339">It is equivalent to the escape sequences and Unicode categories listed in the following table.</span></span>  
  
|<span data-ttu-id="15ee7-340">分類</span><span class="sxs-lookup"><span data-stu-id="15ee7-340">Category</span></span>|<span data-ttu-id="15ee7-341">說明</span><span class="sxs-lookup"><span data-stu-id="15ee7-341">Description</span></span>|  
|--------------|-----------------|  
|`\f`|<span data-ttu-id="15ee7-342">換頁字元 \u000C。</span><span class="sxs-lookup"><span data-stu-id="15ee7-342">The form feed character, \u000C.</span></span>|  
|`\n`|<span data-ttu-id="15ee7-343">新行字元 \u000A。</span><span class="sxs-lookup"><span data-stu-id="15ee7-343">The newline character, \u000A.</span></span>|  
|`\r`|<span data-ttu-id="15ee7-344">歸位字元 \u000D。</span><span class="sxs-lookup"><span data-stu-id="15ee7-344">The carriage return character, \u000D.</span></span>|  
|`\t`|<span data-ttu-id="15ee7-345">定位字元 \u0009。</span><span class="sxs-lookup"><span data-stu-id="15ee7-345">The tab character, \u0009.</span></span>|  
|`\v`|<span data-ttu-id="15ee7-346">垂直定位字元 \u000B。</span><span class="sxs-lookup"><span data-stu-id="15ee7-346">The vertical tab character, \u000B.</span></span>|  
|`\x85`|<span data-ttu-id="15ee7-347">省略符號或 NEXT LINE (NEL) 字元 (…) \u0085。</span><span class="sxs-lookup"><span data-stu-id="15ee7-347">The ellipsis or NEXT LINE (NEL) character (…), \u0085.</span></span>|  
|`\p{Z}`|<span data-ttu-id="15ee7-348">比對任何分隔符號字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-348">Matches any separator character.</span></span>|  
  
 <span data-ttu-id="15ee7-349">如果指定了符合 ECMAScript 的行為，`\s` 就等於 `[ \f\n\r\t\v]`。</span><span class="sxs-lookup"><span data-stu-id="15ee7-349">If ECMAScript-compliant behavior is specified, `\s` is equivalent to `[ \f\n\r\t\v]`.</span></span> <span data-ttu-id="15ee7-350">如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)中的＜ECMAScript 相符行為＞一節。</span><span class="sxs-lookup"><span data-stu-id="15ee7-350">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
 <span data-ttu-id="15ee7-351">以下範例將說明 `\s` 字元類別。</span><span class="sxs-lookup"><span data-stu-id="15ee7-351">The following example illustrates the `\s` character class.</span></span> <span data-ttu-id="15ee7-352">它會定義規則運算式模式 `\b\w+(e)?s(\s|$)`，該模式會比對結尾為 "s" 或 "es" 且後面加上空白字元或是輸入字串結尾的文字。</span><span class="sxs-lookup"><span data-stu-id="15ee7-352">It defines a regular expression pattern, `\b\w+(e)?s(\s|$)`, that matches a word ending in either "s" or "es" followed by either a white-space character or the end of the input string.</span></span> <span data-ttu-id="15ee7-353">規則運算式的解譯方式如下表所示。</span><span class="sxs-lookup"><span data-stu-id="15ee7-353">The regular expression is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="15ee7-354">元素</span><span class="sxs-lookup"><span data-stu-id="15ee7-354">Element</span></span>|<span data-ttu-id="15ee7-355">說明</span><span class="sxs-lookup"><span data-stu-id="15ee7-355">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="15ee7-356">\b</span><span class="sxs-lookup"><span data-stu-id="15ee7-356">\b</span></span>|<span data-ttu-id="15ee7-357">開始字緣比對。</span><span class="sxs-lookup"><span data-stu-id="15ee7-357">Begin the match at a word boundary.</span></span>|  
|<span data-ttu-id="15ee7-358">\w+</span><span class="sxs-lookup"><span data-stu-id="15ee7-358">\w+</span></span>|<span data-ttu-id="15ee7-359">比對一個或多個文字字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-359">Match one or more word characters.</span></span>|  
|<span data-ttu-id="15ee7-360">(e)?</span><span class="sxs-lookup"><span data-stu-id="15ee7-360">(e)?</span></span>|<span data-ttu-id="15ee7-361">比對 "e" 零次或一次。</span><span class="sxs-lookup"><span data-stu-id="15ee7-361">Match an "e" either zero or one time.</span></span>|  
|<span data-ttu-id="15ee7-362">秒</span><span class="sxs-lookup"><span data-stu-id="15ee7-362">s</span></span>|<span data-ttu-id="15ee7-363">比對 "s"。</span><span class="sxs-lookup"><span data-stu-id="15ee7-363">Match an "s".</span></span>|  
|<span data-ttu-id="15ee7-364">(\s&#124;$)</span><span class="sxs-lookup"><span data-stu-id="15ee7-364">(\s&#124;$)</span></span>|<span data-ttu-id="15ee7-365">比對空白字元或輸入字串的結尾。</span><span class="sxs-lookup"><span data-stu-id="15ee7-365">Match either a white-space character or the end of the input string.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/whitespace1.cs#10)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/whitespace1.vb#10)]  
  
<a name="NonWhitespaceCharacter"></a>   
## <a name="non-whitespace-character-s"></a><span data-ttu-id="15ee7-366">非空白字元：\S</span><span class="sxs-lookup"><span data-stu-id="15ee7-366">Non-whitespace character: \S</span></span>  
 <span data-ttu-id="15ee7-367">`\S` 會比對任何非空白字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-367">`\S` matches any non-white-space character.</span></span> <span data-ttu-id="15ee7-368">它相當於 `[^\f\n\r\t\v\x85\p{Z}]` 規則運算式模式，或是規則運算式模式的相反模式，相當於會比對空白字元的 `\s`。</span><span class="sxs-lookup"><span data-stu-id="15ee7-368">It is equivalent to the `[^\f\n\r\t\v\x85\p{Z}]` regular expression pattern, or the opposite of the regular expression pattern that is equivalent to `\s`, which matches white-space characters.</span></span> <span data-ttu-id="15ee7-369">如需詳細資訊，請參閱[空白字元：\s](#WhitespaceCharacter)。</span><span class="sxs-lookup"><span data-stu-id="15ee7-369">For more information, see [White-Space Character: \s](#WhitespaceCharacter).</span></span>  
  
 <span data-ttu-id="15ee7-370">如果指定了符合 ECMAScript 的行為，`\S` 就等於 `[^ \f\n\r\t\v]`。</span><span class="sxs-lookup"><span data-stu-id="15ee7-370">If ECMAScript-compliant behavior is specified, `\S` is equivalent to  `[^ \f\n\r\t\v]`.</span></span> <span data-ttu-id="15ee7-371">如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)中的＜ECMAScript 相符行為＞一節。</span><span class="sxs-lookup"><span data-stu-id="15ee7-371">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
 <span data-ttu-id="15ee7-372">下列範例將說明 `\S` 語言項目。</span><span class="sxs-lookup"><span data-stu-id="15ee7-372">The following example illustrates the `\S` language element.</span></span> <span data-ttu-id="15ee7-373">規則運算式模式 `\b(\S+)\s?` 會比對以空白字元分隔的字串。</span><span class="sxs-lookup"><span data-stu-id="15ee7-373">The regular expression pattern `\b(\S+)\s?` matches strings that are delimited by white-space characters.</span></span> <span data-ttu-id="15ee7-374">在比對之 <xref:System.Text.RegularExpressions.GroupCollection> 物件中的第二個項目包含相符的字串。</span><span class="sxs-lookup"><span data-stu-id="15ee7-374">The second element in the match's <xref:System.Text.RegularExpressions.GroupCollection> object contains the matched string.</span></span> <span data-ttu-id="15ee7-375">規則運算式的解譯方式如下表所示。</span><span class="sxs-lookup"><span data-stu-id="15ee7-375">The regular expression can be interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="15ee7-376">元素</span><span class="sxs-lookup"><span data-stu-id="15ee7-376">Element</span></span>|<span data-ttu-id="15ee7-377">說明</span><span class="sxs-lookup"><span data-stu-id="15ee7-377">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="15ee7-378">開始字緣比對。</span><span class="sxs-lookup"><span data-stu-id="15ee7-378">Begin the match at a word boundary.</span></span>|  
|`(\S+)`|<span data-ttu-id="15ee7-379">比對一個或多個非空白字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-379">Match one or more non-white-space characters.</span></span> <span data-ttu-id="15ee7-380">這是第一個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="15ee7-380">This is the first capturing group.</span></span>|  
|`\s?`|<span data-ttu-id="15ee7-381">比對零個或一個空白字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-381">Match zero or one white-space character.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nonwhitespace1.cs#11)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nonwhitespace1.vb#11)]  
  
<a name="DigitCharacter"></a>   
## <a name="decimal-digit-character-d"></a><span data-ttu-id="15ee7-382">十進位數字字元：\d</span><span class="sxs-lookup"><span data-stu-id="15ee7-382">Decimal digit character: \d</span></span>  
 <span data-ttu-id="15ee7-383">`\d` 會比對任何十進位數字。</span><span class="sxs-lookup"><span data-stu-id="15ee7-383">`\d` matches any decimal digit.</span></span> <span data-ttu-id="15ee7-384">它相當於 `\p{Nd}` 規則運算式模式，其中包括標準的十進位數字 0-9，以及若干其他字元集的十進位數字。</span><span class="sxs-lookup"><span data-stu-id="15ee7-384">It is equivalent to the `\p{Nd}` regular expression pattern, which includes the standard decimal digits 0-9 as well as the decimal digits of a number of other character sets.</span></span>  
  
 <span data-ttu-id="15ee7-385">如果指定了符合 ECMAScript 的行為，`\d` 就等於 `[0-9]`。</span><span class="sxs-lookup"><span data-stu-id="15ee7-385">If ECMAScript-compliant behavior is specified, `\d` is equivalent to  `[0-9]`.</span></span> <span data-ttu-id="15ee7-386">如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)中的＜ECMAScript 相符行為＞一節。</span><span class="sxs-lookup"><span data-stu-id="15ee7-386">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
 <span data-ttu-id="15ee7-387">下列範例將說明 `\d` 語言項目。</span><span class="sxs-lookup"><span data-stu-id="15ee7-387">The following example illustrates the `\d` language element.</span></span> <span data-ttu-id="15ee7-388">它會測試輸入字串是否表示美國和加拿大的有效電話號碼。</span><span class="sxs-lookup"><span data-stu-id="15ee7-388">It tests whether an input string represents a valid telephone number in the United States and Canada.</span></span> <span data-ttu-id="15ee7-389">規則運算式模式 `^(\(?\d{3}\)?[\s-])?\d{3}-\d{4}$` 的定義如下表所示。</span><span class="sxs-lookup"><span data-stu-id="15ee7-389">The regular expression pattern `^(\(?\d{3}\)?[\s-])?\d{3}-\d{4}$` is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="15ee7-390">項目</span><span class="sxs-lookup"><span data-stu-id="15ee7-390">Element</span></span>|<span data-ttu-id="15ee7-391">說明</span><span class="sxs-lookup"><span data-stu-id="15ee7-391">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="15ee7-392">在輸入字串的開頭開始比對。</span><span class="sxs-lookup"><span data-stu-id="15ee7-392">Begin the match at the beginning of the input string.</span></span>|  
|`\(?`|<span data-ttu-id="15ee7-393">比對零個或一個常值 "(" 字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-393">Match zero or one literal "(" character.</span></span>|  
|`\d{3}`|<span data-ttu-id="15ee7-394">比對三個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="15ee7-394">Match three decimal digits.</span></span>|  
|`\)?`|<span data-ttu-id="15ee7-395">比對零個或一個常值 ")" 字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-395">Match zero or one literal ")" character.</span></span>|  
|`[\s-]`|<span data-ttu-id="15ee7-396">比對連字號或空白字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-396">Match a hyphen or a white-space character.</span></span>|  
|`(\(?\d{3}\)?[\s-])?`|<span data-ttu-id="15ee7-397">比對零次或一次選擇性的左括號，後面接著三個十進位數字、選擇性的右括號，以及空白字元或是連字號。</span><span class="sxs-lookup"><span data-stu-id="15ee7-397">Match an optional opening parenthesis followed by three decimal digits, an optional closing parenthesis, and either a white-space character or a hyphen zero or one time.</span></span> <span data-ttu-id="15ee7-398">這是第一個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="15ee7-398">This is the first capturing group.</span></span>|  
|`\d{3}-\d{4}`|<span data-ttu-id="15ee7-399">比對三個十進位數字，後面接著連字號和另外四個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="15ee7-399">Match three decimal digits followed by a hyphen and four more decimal digits.</span></span>|  
|`$`|<span data-ttu-id="15ee7-400">比對輸入字串的結尾。</span><span class="sxs-lookup"><span data-stu-id="15ee7-400">Match the end of the input string.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/digit1.cs#12)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/digit1.vb#12)]  
  
<a name="NonDigitCharacter"></a>   
## <a name="non-digit-character-d"></a><span data-ttu-id="15ee7-401">非數字字元：\D</span><span class="sxs-lookup"><span data-stu-id="15ee7-401">Non-digit character: \D</span></span>  
 <span data-ttu-id="15ee7-402">`\D` 會比對任何非數字字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-402">`\D` matches any non-digit character.</span></span> <span data-ttu-id="15ee7-403">它相當於 `\P{Nd}` 規則運算式模式。</span><span class="sxs-lookup"><span data-stu-id="15ee7-403">It is equivalent to the `\P{Nd}` regular expression pattern.</span></span>  
  
 <span data-ttu-id="15ee7-404">如果指定了符合 ECMAScript 的行為，`\D` 就等於 `[^0-9]`。</span><span class="sxs-lookup"><span data-stu-id="15ee7-404">If ECMAScript-compliant behavior is specified, `\D` is equivalent to  `[^0-9]`.</span></span> <span data-ttu-id="15ee7-405">如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)中的＜ECMAScript 相符行為＞一節。</span><span class="sxs-lookup"><span data-stu-id="15ee7-405">For information on ECMAScript regular expressions, see the "ECMAScript Matching Behavior" section in [Regular Expression Options](../../../docs/standard/base-types/regular-expression-options.md).</span></span>  
  
 <span data-ttu-id="15ee7-406">下列範例將說明 \D 語言項目。</span><span class="sxs-lookup"><span data-stu-id="15ee7-406">The following example illustrates the \D language element.</span></span> <span data-ttu-id="15ee7-407">它會測試像是組件編號這類字串，是否由十進位和非十進位字元的適當組合所構成。</span><span class="sxs-lookup"><span data-stu-id="15ee7-407">It tests whether a string such as a part number consists of the appropriate combination of decimal and non-decimal characters.</span></span> <span data-ttu-id="15ee7-408">規則運算式模式 `^\D\d{1,5}\D*$` 的定義如下表所示。</span><span class="sxs-lookup"><span data-stu-id="15ee7-408">The regular expression pattern `^\D\d{1,5}\D*$` is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="15ee7-409">項目</span><span class="sxs-lookup"><span data-stu-id="15ee7-409">Element</span></span>|<span data-ttu-id="15ee7-410">說明</span><span class="sxs-lookup"><span data-stu-id="15ee7-410">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="15ee7-411">在輸入字串的開頭開始比對。</span><span class="sxs-lookup"><span data-stu-id="15ee7-411">Begin the match at the beginning of the input string.</span></span>|  
|`\D`|<span data-ttu-id="15ee7-412">比對非數字字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-412">Match a non-digit character.</span></span>|  
|`\d{1,5}`|<span data-ttu-id="15ee7-413">比對從一個到五個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="15ee7-413">Match from one to five decimal digits.</span></span>|  
|`\D*`|<span data-ttu-id="15ee7-414">比對零個、一個或更多非十進位字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-414">Match zero, one, or more non-decimal characters.</span></span>|  
|`$`|<span data-ttu-id="15ee7-415">比對輸入字串的結尾。</span><span class="sxs-lookup"><span data-stu-id="15ee7-415">Match the end of the input string.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nondigit1.cs#13)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nondigit1.vb#13)]  
  
<a name="SupportedUnicodeGeneralCategories"></a>   
## <a name="supported-unicode-general-categories"></a><span data-ttu-id="15ee7-416">支援的 Unicode 一般分類</span><span class="sxs-lookup"><span data-stu-id="15ee7-416">Supported Unicode general categories</span></span>  
 <span data-ttu-id="15ee7-417">Unicode 定義了下表中所列的一般類別。</span><span class="sxs-lookup"><span data-stu-id="15ee7-417">Unicode defines the general categories listed in the following table.</span></span> <span data-ttu-id="15ee7-418">如需詳細資訊，請參閱 [Unicode Character Database](https://www.unicode.org/reports/tr44/) 中的 "UCD File Format" 和 "General Category Values" 副標題。</span><span class="sxs-lookup"><span data-stu-id="15ee7-418">For more information, see the "UCD File Format" and "General Category Values" subtopics at the [Unicode Character Database](https://www.unicode.org/reports/tr44/).</span></span>  
  
|<span data-ttu-id="15ee7-419">分類</span><span class="sxs-lookup"><span data-stu-id="15ee7-419">Category</span></span>|<span data-ttu-id="15ee7-420">說明</span><span class="sxs-lookup"><span data-stu-id="15ee7-420">Description</span></span>|  
|--------------|-----------------|  
|`Lu`|<span data-ttu-id="15ee7-421">字母、大寫</span><span class="sxs-lookup"><span data-stu-id="15ee7-421">Letter, Uppercase</span></span>|  
|`Ll`|<span data-ttu-id="15ee7-422">字母、小寫</span><span class="sxs-lookup"><span data-stu-id="15ee7-422">Letter, Lowercase</span></span>|  
|`Lt`|<span data-ttu-id="15ee7-423">字母、字首大寫</span><span class="sxs-lookup"><span data-stu-id="15ee7-423">Letter, Titlecase</span></span>|  
|`Lm`|<span data-ttu-id="15ee7-424">字母、修飾詞</span><span class="sxs-lookup"><span data-stu-id="15ee7-424">Letter, Modifier</span></span>|  
|`Lo`|<span data-ttu-id="15ee7-425">字母、其他</span><span class="sxs-lookup"><span data-stu-id="15ee7-425">Letter, Other</span></span>|  
|`L`|<span data-ttu-id="15ee7-426">所有字母字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-426">All letter characters.</span></span> <span data-ttu-id="15ee7-427">這包括 `Lu`、`Ll`、`Lt`、`Lm` 和 `Lo` 字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-427">This includes the `Lu`, `Ll`, `Lt`, `Lm`, and `Lo` characters.</span></span>|  
|`Mn`|<span data-ttu-id="15ee7-428">記號，非間距</span><span class="sxs-lookup"><span data-stu-id="15ee7-428">Mark, Nonspacing</span></span>|  
|`Mc`|<span data-ttu-id="15ee7-429">記號，間距組合</span><span class="sxs-lookup"><span data-stu-id="15ee7-429">Mark, Spacing Combining</span></span>|  
|`Me`|<span data-ttu-id="15ee7-430">記號，封入</span><span class="sxs-lookup"><span data-stu-id="15ee7-430">Mark, Enclosing</span></span>|  
|`M`|<span data-ttu-id="15ee7-431">所有變音符號記號。</span><span class="sxs-lookup"><span data-stu-id="15ee7-431">All diacritic marks.</span></span> <span data-ttu-id="15ee7-432">這包括 `Mn`、`Mc` 和 `Me` 分類。</span><span class="sxs-lookup"><span data-stu-id="15ee7-432">This includes the `Mn`, `Mc`, and `Me` categories.</span></span>|  
|`Nd`|<span data-ttu-id="15ee7-433">數字、十進位數字</span><span class="sxs-lookup"><span data-stu-id="15ee7-433">Number, Decimal Digit</span></span>|  
|`Nl`|<span data-ttu-id="15ee7-434">數字，字母</span><span class="sxs-lookup"><span data-stu-id="15ee7-434">Number, Letter</span></span>|  
|`No`|<span data-ttu-id="15ee7-435">數字，其他</span><span class="sxs-lookup"><span data-stu-id="15ee7-435">Number, Other</span></span>|  
|`N`|<span data-ttu-id="15ee7-436">所有數字。</span><span class="sxs-lookup"><span data-stu-id="15ee7-436">All numbers.</span></span> <span data-ttu-id="15ee7-437">這包括 `Nd`、`Nl` 和 `No` 分類。</span><span class="sxs-lookup"><span data-stu-id="15ee7-437">This includes the `Nd`, `Nl`, and `No` categories.</span></span>|  
|`Pc`|<span data-ttu-id="15ee7-438">標點符號，連接器</span><span class="sxs-lookup"><span data-stu-id="15ee7-438">Punctuation, Connector</span></span>|  
|`Pd`|<span data-ttu-id="15ee7-439">標點符號，破折號</span><span class="sxs-lookup"><span data-stu-id="15ee7-439">Punctuation, Dash</span></span>|  
|`Ps`|<span data-ttu-id="15ee7-440">標點符號，左括號</span><span class="sxs-lookup"><span data-stu-id="15ee7-440">Punctuation, Open</span></span>|  
|`Pe`|<span data-ttu-id="15ee7-441">標點符號，右括號</span><span class="sxs-lookup"><span data-stu-id="15ee7-441">Punctuation, Close</span></span>|  
|`Pi`|<span data-ttu-id="15ee7-442">標點符號，左引號 (根據使用方式，作用可能像 Ps 或 Pe)</span><span class="sxs-lookup"><span data-stu-id="15ee7-442">Punctuation, Initial quote (may behave like Ps or Pe depending on usage)</span></span>|  
|`Pf`|<span data-ttu-id="15ee7-443">標點符號，右引號 (根據使用方式，作用可能像 Ps 或 Pe)</span><span class="sxs-lookup"><span data-stu-id="15ee7-443">Punctuation, Final quote (may behave like Ps or Pe depending on usage)</span></span>|  
|`Po`|<span data-ttu-id="15ee7-444">標點符號，其他</span><span class="sxs-lookup"><span data-stu-id="15ee7-444">Punctuation, Other</span></span>|  
|`P`|<span data-ttu-id="15ee7-445">所有標點符號字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-445">All punctuation characters.</span></span> <span data-ttu-id="15ee7-446">這包括 `Pc`、`Pd`、`Ps`、`Pe`、`Pi`、`Pf` 和 `Po` 分類。</span><span class="sxs-lookup"><span data-stu-id="15ee7-446">This includes the `Pc`, `Pd`, `Ps`, `Pe`, `Pi`, `Pf`, and `Po` categories.</span></span>|  
|`Sm`|<span data-ttu-id="15ee7-447">符號，數學</span><span class="sxs-lookup"><span data-stu-id="15ee7-447">Symbol, Math</span></span>|  
|`Sc`|<span data-ttu-id="15ee7-448">符號，貨幣</span><span class="sxs-lookup"><span data-stu-id="15ee7-448">Symbol, Currency</span></span>|  
|`Sk`|<span data-ttu-id="15ee7-449">符號，修飾詞</span><span class="sxs-lookup"><span data-stu-id="15ee7-449">Symbol, Modifier</span></span>|  
|`So`|<span data-ttu-id="15ee7-450">符號，其他</span><span class="sxs-lookup"><span data-stu-id="15ee7-450">Symbol, Other</span></span>|  
|`S`|<span data-ttu-id="15ee7-451">所有符號。</span><span class="sxs-lookup"><span data-stu-id="15ee7-451">All symbols.</span></span> <span data-ttu-id="15ee7-452">這包括 `Sm`、`Sc`、`Sk` 和 `So` 分類。</span><span class="sxs-lookup"><span data-stu-id="15ee7-452">This includes the `Sm`, `Sc`, `Sk`, and `So` categories.</span></span>|  
|`Zs`|<span data-ttu-id="15ee7-453">分隔符號，空格</span><span class="sxs-lookup"><span data-stu-id="15ee7-453">Separator, Space</span></span>|  
|`Zl`|<span data-ttu-id="15ee7-454">分隔符號，行</span><span class="sxs-lookup"><span data-stu-id="15ee7-454">Separator, Line</span></span>|  
|`Zp`|<span data-ttu-id="15ee7-455">分隔符號，段落</span><span class="sxs-lookup"><span data-stu-id="15ee7-455">Separator, Paragraph</span></span>|  
|`Z`|<span data-ttu-id="15ee7-456">所有分隔符號字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-456">All separator characters.</span></span> <span data-ttu-id="15ee7-457">這包括 `Zs`、`Zl` 和 `Zp` 分類。</span><span class="sxs-lookup"><span data-stu-id="15ee7-457">This includes the `Zs`, `Zl`, and `Zp` categories.</span></span>|  
|`Cc`|<span data-ttu-id="15ee7-458">其他，控制</span><span class="sxs-lookup"><span data-stu-id="15ee7-458">Other, Control</span></span>|  
|`Cf`|<span data-ttu-id="15ee7-459">其他，格式</span><span class="sxs-lookup"><span data-stu-id="15ee7-459">Other, Format</span></span>|  
|`Cs`|<span data-ttu-id="15ee7-460">其他，Surrogate</span><span class="sxs-lookup"><span data-stu-id="15ee7-460">Other, Surrogate</span></span>|  
|`Co`|<span data-ttu-id="15ee7-461">其他，專用</span><span class="sxs-lookup"><span data-stu-id="15ee7-461">Other, Private Use</span></span>|  
|`Cn`|<span data-ttu-id="15ee7-462">其他，未指派 (沒有字元擁有這個屬性)</span><span class="sxs-lookup"><span data-stu-id="15ee7-462">Other, Not Assigned (no characters have this property)</span></span>|  
|`C`|<span data-ttu-id="15ee7-463">所有控制字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-463">All control characters.</span></span> <span data-ttu-id="15ee7-464">這包括 `Cc`、`Cf`、`Cs`、`Co` 和 `Cn` 分類。</span><span class="sxs-lookup"><span data-stu-id="15ee7-464">This includes the `Cc`, `Cf`, `Cs`, `Co`, and `Cn` categories.</span></span>|  
  
 <span data-ttu-id="15ee7-465">您可以將任何特殊字元傳遞到 <xref:System.Char.GetUnicodeCategory%2A> 方法，以判斷該字元的 Unicode 分類。</span><span class="sxs-lookup"><span data-stu-id="15ee7-465">You can determine the Unicode category of any particular character by passing that character to the <xref:System.Char.GetUnicodeCategory%2A> method.</span></span> <span data-ttu-id="15ee7-466">下列範例會使用 <xref:System.Char.GetUnicodeCategory%2A> 方法判斷包含所選取拉丁字元的陣列中，每個項目的分類。</span><span class="sxs-lookup"><span data-stu-id="15ee7-466">The following example uses the <xref:System.Char.GetUnicodeCategory%2A> method to determine the category of each element in an array that contains selected Latin characters.</span></span>  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/getunicodecategory1.cs#14)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/getunicodecategory1.vb#14)]  
  
<a name="SupportedNamedBlocks"></a>   
## <a name="supported-named-blocks"></a><span data-ttu-id="15ee7-467">支援的具名區塊</span><span class="sxs-lookup"><span data-stu-id="15ee7-467">Supported named blocks</span></span>

<span data-ttu-id="15ee7-468">.NET 提供下表所列的具名區塊。</span><span class="sxs-lookup"><span data-stu-id="15ee7-468">.NET provides the named blocks listed in the following table.</span></span> <span data-ttu-id="15ee7-469">這一組支援的具名區塊是根據 Unicode 4.0 和 Perl 5.6。</span><span class="sxs-lookup"><span data-stu-id="15ee7-469">The set of supported named blocks is based on Unicode 4.0 and Perl 5.6.</span></span> <span data-ttu-id="15ee7-470">針對使用具名區塊的規則運算式，請參閱 [Unicode 類別或 Unicode 區塊：\\p{}](#unicode-category-or-unicode-block-p) 一節。</span><span class="sxs-lookup"><span data-stu-id="15ee7-470">For a regular expression that uses named blocks, see the [Unicode category or Unicode block: \\p{}](#unicode-category-or-unicode-block-p) section.</span></span>  
  
|<span data-ttu-id="15ee7-471">字碼指標範圍</span><span class="sxs-lookup"><span data-stu-id="15ee7-471">Code point range</span></span>|<span data-ttu-id="15ee7-472">區塊名稱</span><span class="sxs-lookup"><span data-stu-id="15ee7-472">Block name</span></span>|  
|----------------------|----------------|  
|<span data-ttu-id="15ee7-473">0000 - 007F</span><span class="sxs-lookup"><span data-stu-id="15ee7-473">0000 - 007F</span></span>|`IsBasicLatin`|  
|<span data-ttu-id="15ee7-474">0080 - 00FF</span><span class="sxs-lookup"><span data-stu-id="15ee7-474">0080 - 00FF</span></span>|`IsLatin-1Supplement`|  
|<span data-ttu-id="15ee7-475">0100 - 017F</span><span class="sxs-lookup"><span data-stu-id="15ee7-475">0100 - 017F</span></span>|`IsLatinExtended-A`|  
|<span data-ttu-id="15ee7-476">0180 - 024F</span><span class="sxs-lookup"><span data-stu-id="15ee7-476">0180 - 024F</span></span>|`IsLatinExtended-B`|  
|<span data-ttu-id="15ee7-477">0250 - 02AF</span><span class="sxs-lookup"><span data-stu-id="15ee7-477">0250 - 02AF</span></span>|`IsIPAExtensions`|  
|<span data-ttu-id="15ee7-478">02B0 - 02FF</span><span class="sxs-lookup"><span data-stu-id="15ee7-478">02B0 - 02FF</span></span>|`IsSpacingModifierLetters`|  
|<span data-ttu-id="15ee7-479">0300 - 036F</span><span class="sxs-lookup"><span data-stu-id="15ee7-479">0300 - 036F</span></span>|`IsCombiningDiacriticalMarks`|  
|<span data-ttu-id="15ee7-480">0370 - 03FF</span><span class="sxs-lookup"><span data-stu-id="15ee7-480">0370 - 03FF</span></span>|`IsGreek`<br /><br /> <span data-ttu-id="15ee7-481">-或-</span><span class="sxs-lookup"><span data-stu-id="15ee7-481">-or-</span></span><br /><br /> `IsGreekandCoptic`|  
|<span data-ttu-id="15ee7-482">0400 - 04FF</span><span class="sxs-lookup"><span data-stu-id="15ee7-482">0400 - 04FF</span></span>|`IsCyrillic`|  
|<span data-ttu-id="15ee7-483">0500 - 052F</span><span class="sxs-lookup"><span data-stu-id="15ee7-483">0500 - 052F</span></span>|`IsCyrillicSupplement`|  
|<span data-ttu-id="15ee7-484">0530 - 058F</span><span class="sxs-lookup"><span data-stu-id="15ee7-484">0530 - 058F</span></span>|`IsArmenian`|  
|<span data-ttu-id="15ee7-485">0590 - 05FF</span><span class="sxs-lookup"><span data-stu-id="15ee7-485">0590 - 05FF</span></span>|`IsHebrew`|  
|<span data-ttu-id="15ee7-486">0600 - 06FF</span><span class="sxs-lookup"><span data-stu-id="15ee7-486">0600 - 06FF</span></span>|`IsArabic`|  
|<span data-ttu-id="15ee7-487">0700 - 074F</span><span class="sxs-lookup"><span data-stu-id="15ee7-487">0700 - 074F</span></span>|`IsSyriac`|  
|<span data-ttu-id="15ee7-488">0780 - 07BF</span><span class="sxs-lookup"><span data-stu-id="15ee7-488">0780 - 07BF</span></span>|`IsThaana`|  
|<span data-ttu-id="15ee7-489">0900 - 097F</span><span class="sxs-lookup"><span data-stu-id="15ee7-489">0900 - 097F</span></span>|`IsDevanagari`|  
|<span data-ttu-id="15ee7-490">0980 - 09FF</span><span class="sxs-lookup"><span data-stu-id="15ee7-490">0980 - 09FF</span></span>|`IsBengali`|  
|<span data-ttu-id="15ee7-491">0A00 - 0A7F</span><span class="sxs-lookup"><span data-stu-id="15ee7-491">0A00 - 0A7F</span></span>|`IsGurmukhi`|  
|<span data-ttu-id="15ee7-492">0A80 - 0AFF</span><span class="sxs-lookup"><span data-stu-id="15ee7-492">0A80 - 0AFF</span></span>|`IsGujarati`|  
|<span data-ttu-id="15ee7-493">0B00 - 0B7F</span><span class="sxs-lookup"><span data-stu-id="15ee7-493">0B00 - 0B7F</span></span>|`IsOriya`|  
|<span data-ttu-id="15ee7-494">0B80 - 0BFF</span><span class="sxs-lookup"><span data-stu-id="15ee7-494">0B80 - 0BFF</span></span>|`IsTamil`|  
|<span data-ttu-id="15ee7-495">0C00 - 0C7F</span><span class="sxs-lookup"><span data-stu-id="15ee7-495">0C00 - 0C7F</span></span>|`IsTelugu`|  
|<span data-ttu-id="15ee7-496">0C80 - 0CFF</span><span class="sxs-lookup"><span data-stu-id="15ee7-496">0C80 - 0CFF</span></span>|`IsKannada`|  
|<span data-ttu-id="15ee7-497">0D00 - 0D7F</span><span class="sxs-lookup"><span data-stu-id="15ee7-497">0D00 - 0D7F</span></span>|`IsMalayalam`|  
|<span data-ttu-id="15ee7-498">0D80 - 0DFF</span><span class="sxs-lookup"><span data-stu-id="15ee7-498">0D80 - 0DFF</span></span>|`IsSinhala`|  
|<span data-ttu-id="15ee7-499">0E00 - 0E7F</span><span class="sxs-lookup"><span data-stu-id="15ee7-499">0E00 - 0E7F</span></span>|`IsThai`|  
|<span data-ttu-id="15ee7-500">0E80 - 0EFF</span><span class="sxs-lookup"><span data-stu-id="15ee7-500">0E80 - 0EFF</span></span>|`IsLao`|  
|<span data-ttu-id="15ee7-501">0F00 - 0FFF</span><span class="sxs-lookup"><span data-stu-id="15ee7-501">0F00 - 0FFF</span></span>|`IsTibetan`|  
|<span data-ttu-id="15ee7-502">1000 - 109F</span><span class="sxs-lookup"><span data-stu-id="15ee7-502">1000 - 109F</span></span>|`IsMyanmar`|  
|<span data-ttu-id="15ee7-503">10A0 - 10FF</span><span class="sxs-lookup"><span data-stu-id="15ee7-503">10A0 - 10FF</span></span>|`IsGeorgian`|  
|<span data-ttu-id="15ee7-504">1100 - 11FF</span><span class="sxs-lookup"><span data-stu-id="15ee7-504">1100 - 11FF</span></span>|`IsHangulJamo`|  
|<span data-ttu-id="15ee7-505">1200 - 137F</span><span class="sxs-lookup"><span data-stu-id="15ee7-505">1200 - 137F</span></span>|`IsEthiopic`|  
|<span data-ttu-id="15ee7-506">13A0 - 13FF</span><span class="sxs-lookup"><span data-stu-id="15ee7-506">13A0 - 13FF</span></span>|`IsCherokee`|  
|<span data-ttu-id="15ee7-507">1400 - 167F</span><span class="sxs-lookup"><span data-stu-id="15ee7-507">1400 - 167F</span></span>|`IsUnifiedCanadianAboriginalSyllabics`|  
|<span data-ttu-id="15ee7-508">1680 - 169F</span><span class="sxs-lookup"><span data-stu-id="15ee7-508">1680 - 169F</span></span>|`IsOgham`|  
|<span data-ttu-id="15ee7-509">16A0 - 16FF</span><span class="sxs-lookup"><span data-stu-id="15ee7-509">16A0 - 16FF</span></span>|`IsRunic`|  
|<span data-ttu-id="15ee7-510">1700 - 171F</span><span class="sxs-lookup"><span data-stu-id="15ee7-510">1700 - 171F</span></span>|`IsTagalog`|  
|<span data-ttu-id="15ee7-511">1720 - 173F</span><span class="sxs-lookup"><span data-stu-id="15ee7-511">1720 - 173F</span></span>|`IsHanunoo`|  
|<span data-ttu-id="15ee7-512">1740 - 175F</span><span class="sxs-lookup"><span data-stu-id="15ee7-512">1740 - 175F</span></span>|`IsBuhid`|  
|<span data-ttu-id="15ee7-513">1760 - 177F</span><span class="sxs-lookup"><span data-stu-id="15ee7-513">1760 - 177F</span></span>|`IsTagbanwa`|  
|<span data-ttu-id="15ee7-514">1780 - 17FF</span><span class="sxs-lookup"><span data-stu-id="15ee7-514">1780 - 17FF</span></span>|`IsKhmer`|  
|<span data-ttu-id="15ee7-515">1800 - 18AF</span><span class="sxs-lookup"><span data-stu-id="15ee7-515">1800 - 18AF</span></span>|`IsMongolian`|  
|<span data-ttu-id="15ee7-516">1900 - 194F</span><span class="sxs-lookup"><span data-stu-id="15ee7-516">1900 - 194F</span></span>|`IsLimbu`|  
|<span data-ttu-id="15ee7-517">1950 - 197F</span><span class="sxs-lookup"><span data-stu-id="15ee7-517">1950 - 197F</span></span>|`IsTaiLe`|  
|<span data-ttu-id="15ee7-518">19E0 - 19FF</span><span class="sxs-lookup"><span data-stu-id="15ee7-518">19E0 - 19FF</span></span>|`IsKhmerSymbols`|  
|<span data-ttu-id="15ee7-519">1D00 - 1D7F</span><span class="sxs-lookup"><span data-stu-id="15ee7-519">1D00 - 1D7F</span></span>|`IsPhoneticExtensions`|  
|<span data-ttu-id="15ee7-520">1E00 - 1EFF</span><span class="sxs-lookup"><span data-stu-id="15ee7-520">1E00 - 1EFF</span></span>|`IsLatinExtendedAdditional`|  
|<span data-ttu-id="15ee7-521">1F00 - 1FFF</span><span class="sxs-lookup"><span data-stu-id="15ee7-521">1F00 - 1FFF</span></span>|`IsGreekExtended`|  
|<span data-ttu-id="15ee7-522">2000 - 206F</span><span class="sxs-lookup"><span data-stu-id="15ee7-522">2000 - 206F</span></span>|`IsGeneralPunctuation`|  
|<span data-ttu-id="15ee7-523">2070 - 209F</span><span class="sxs-lookup"><span data-stu-id="15ee7-523">2070 - 209F</span></span>|`IsSuperscriptsandSubscripts`|  
|<span data-ttu-id="15ee7-524">20A0 - 20CF</span><span class="sxs-lookup"><span data-stu-id="15ee7-524">20A0 - 20CF</span></span>|`IsCurrencySymbols`|  
|<span data-ttu-id="15ee7-525">20D0 - 20FF</span><span class="sxs-lookup"><span data-stu-id="15ee7-525">20D0 - 20FF</span></span>|`IsCombiningDiacriticalMarksforSymbols`<br /><br /> <span data-ttu-id="15ee7-526">-或-</span><span class="sxs-lookup"><span data-stu-id="15ee7-526">-or-</span></span><br /><br /> `IsCombiningMarksforSymbols`|  
|<span data-ttu-id="15ee7-527">2100 - 214F</span><span class="sxs-lookup"><span data-stu-id="15ee7-527">2100 - 214F</span></span>|`IsLetterlikeSymbols`|  
|<span data-ttu-id="15ee7-528">2150 - 218F</span><span class="sxs-lookup"><span data-stu-id="15ee7-528">2150 - 218F</span></span>|`IsNumberForms`|  
|<span data-ttu-id="15ee7-529">2190 - 21FF</span><span class="sxs-lookup"><span data-stu-id="15ee7-529">2190 - 21FF</span></span>|`IsArrows`|  
|<span data-ttu-id="15ee7-530">2200 - 22FF</span><span class="sxs-lookup"><span data-stu-id="15ee7-530">2200 - 22FF</span></span>|`IsMathematicalOperators`|  
|<span data-ttu-id="15ee7-531">2300 - 23FF</span><span class="sxs-lookup"><span data-stu-id="15ee7-531">2300 - 23FF</span></span>|`IsMiscellaneousTechnical`|  
|<span data-ttu-id="15ee7-532">2400 - 243F</span><span class="sxs-lookup"><span data-stu-id="15ee7-532">2400 - 243F</span></span>|`IsControlPictures`|  
|<span data-ttu-id="15ee7-533">2440 - 245F</span><span class="sxs-lookup"><span data-stu-id="15ee7-533">2440 - 245F</span></span>|`IsOpticalCharacterRecognition`|  
|<span data-ttu-id="15ee7-534">2460 - 24FF</span><span class="sxs-lookup"><span data-stu-id="15ee7-534">2460 - 24FF</span></span>|`IsEnclosedAlphanumerics`|  
|<span data-ttu-id="15ee7-535">2500 - 257F</span><span class="sxs-lookup"><span data-stu-id="15ee7-535">2500 - 257F</span></span>|`IsBoxDrawing`|  
|<span data-ttu-id="15ee7-536">2580 - 259F</span><span class="sxs-lookup"><span data-stu-id="15ee7-536">2580 - 259F</span></span>|`IsBlockElements`|  
|<span data-ttu-id="15ee7-537">25A0 - 25FF</span><span class="sxs-lookup"><span data-stu-id="15ee7-537">25A0 - 25FF</span></span>|`IsGeometricShapes`|  
|<span data-ttu-id="15ee7-538">2600 - 26FF</span><span class="sxs-lookup"><span data-stu-id="15ee7-538">2600 - 26FF</span></span>|`IsMiscellaneousSymbols`|  
|<span data-ttu-id="15ee7-539">2700 - 27BF</span><span class="sxs-lookup"><span data-stu-id="15ee7-539">2700 - 27BF</span></span>|`IsDingbats`|  
|<span data-ttu-id="15ee7-540">27C0 - 27EF</span><span class="sxs-lookup"><span data-stu-id="15ee7-540">27C0 - 27EF</span></span>|`IsMiscellaneousMathematicalSymbols-A`|  
|<span data-ttu-id="15ee7-541">27F0 - 27FF</span><span class="sxs-lookup"><span data-stu-id="15ee7-541">27F0 - 27FF</span></span>|`IsSupplementalArrows-A`|  
|<span data-ttu-id="15ee7-542">2800 - 28FF</span><span class="sxs-lookup"><span data-stu-id="15ee7-542">2800 - 28FF</span></span>|`IsBraillePatterns`|  
|<span data-ttu-id="15ee7-543">2900 - 297F</span><span class="sxs-lookup"><span data-stu-id="15ee7-543">2900 - 297F</span></span>|`IsSupplementalArrows-B`|  
|<span data-ttu-id="15ee7-544">2980 - 29FF</span><span class="sxs-lookup"><span data-stu-id="15ee7-544">2980 - 29FF</span></span>|`IsMiscellaneousMathematicalSymbols-B`|  
|<span data-ttu-id="15ee7-545">2A00 - 2AFF</span><span class="sxs-lookup"><span data-stu-id="15ee7-545">2A00 - 2AFF</span></span>|`IsSupplementalMathematicalOperators`|  
|<span data-ttu-id="15ee7-546">2B00 - 2BFF</span><span class="sxs-lookup"><span data-stu-id="15ee7-546">2B00 - 2BFF</span></span>|`IsMiscellaneousSymbolsandArrows`|  
|<span data-ttu-id="15ee7-547">2E80 - 2EFF</span><span class="sxs-lookup"><span data-stu-id="15ee7-547">2E80 - 2EFF</span></span>|`IsCJKRadicalsSupplement`|  
|<span data-ttu-id="15ee7-548">2F00 - 2FDF</span><span class="sxs-lookup"><span data-stu-id="15ee7-548">2F00 - 2FDF</span></span>|`IsKangxiRadicals`|  
|<span data-ttu-id="15ee7-549">2FF0 - 2FFF</span><span class="sxs-lookup"><span data-stu-id="15ee7-549">2FF0 - 2FFF</span></span>|`IsIdeographicDescriptionCharacters`|  
|<span data-ttu-id="15ee7-550">3000 - 303F</span><span class="sxs-lookup"><span data-stu-id="15ee7-550">3000 - 303F</span></span>|`IsCJKSymbolsandPunctuation`|  
|<span data-ttu-id="15ee7-551">3040 - 309F</span><span class="sxs-lookup"><span data-stu-id="15ee7-551">3040 - 309F</span></span>|`IsHiragana`|  
|<span data-ttu-id="15ee7-552">30A0 - 30FF</span><span class="sxs-lookup"><span data-stu-id="15ee7-552">30A0 - 30FF</span></span>|`IsKatakana`|  
|<span data-ttu-id="15ee7-553">3100 - 312F</span><span class="sxs-lookup"><span data-stu-id="15ee7-553">3100 - 312F</span></span>|`IsBopomofo`|  
|<span data-ttu-id="15ee7-554">3130 - 318F</span><span class="sxs-lookup"><span data-stu-id="15ee7-554">3130 - 318F</span></span>|`IsHangulCompatibilityJamo`|  
|<span data-ttu-id="15ee7-555">3190 - 319F</span><span class="sxs-lookup"><span data-stu-id="15ee7-555">3190 - 319F</span></span>|`IsKanbun`|  
|<span data-ttu-id="15ee7-556">31A0 - 31BF</span><span class="sxs-lookup"><span data-stu-id="15ee7-556">31A0 - 31BF</span></span>|`IsBopomofoExtended`|  
|<span data-ttu-id="15ee7-557">31F0 - 31FF</span><span class="sxs-lookup"><span data-stu-id="15ee7-557">31F0 - 31FF</span></span>|`IsKatakanaPhoneticExtensions`|  
|<span data-ttu-id="15ee7-558">3200 - 32FF</span><span class="sxs-lookup"><span data-stu-id="15ee7-558">3200 - 32FF</span></span>|`IsEnclosedCJKLettersandMonths`|  
|<span data-ttu-id="15ee7-559">3300 - 33FF</span><span class="sxs-lookup"><span data-stu-id="15ee7-559">3300 - 33FF</span></span>|`IsCJKCompatibility`|  
|<span data-ttu-id="15ee7-560">3400 - 4DBF</span><span class="sxs-lookup"><span data-stu-id="15ee7-560">3400 - 4DBF</span></span>|`IsCJKUnifiedIdeographsExtensionA`|  
|<span data-ttu-id="15ee7-561">4DC0 - 4DFF</span><span class="sxs-lookup"><span data-stu-id="15ee7-561">4DC0 - 4DFF</span></span>|`IsYijingHexagramSymbols`|  
|<span data-ttu-id="15ee7-562">4E00 - 9FFF</span><span class="sxs-lookup"><span data-stu-id="15ee7-562">4E00 - 9FFF</span></span>|`IsCJKUnifiedIdeographs`|  
|<span data-ttu-id="15ee7-563">A000 - A48F</span><span class="sxs-lookup"><span data-stu-id="15ee7-563">A000 - A48F</span></span>|`IsYiSyllables`|  
|<span data-ttu-id="15ee7-564">A490 - A4CF</span><span class="sxs-lookup"><span data-stu-id="15ee7-564">A490 - A4CF</span></span>|`IsYiRadicals`|  
|<span data-ttu-id="15ee7-565">AC00 - D7AF</span><span class="sxs-lookup"><span data-stu-id="15ee7-565">AC00 - D7AF</span></span>|`IsHangulSyllables`|  
|<span data-ttu-id="15ee7-566">D800 - DB7F</span><span class="sxs-lookup"><span data-stu-id="15ee7-566">D800 - DB7F</span></span>|`IsHighSurrogates`|  
|<span data-ttu-id="15ee7-567">DB80 - DBFF</span><span class="sxs-lookup"><span data-stu-id="15ee7-567">DB80 - DBFF</span></span>|`IsHighPrivateUseSurrogates`|  
|<span data-ttu-id="15ee7-568">DC00 - DFFF</span><span class="sxs-lookup"><span data-stu-id="15ee7-568">DC00 - DFFF</span></span>|`IsLowSurrogates`|  
|<span data-ttu-id="15ee7-569">E000 - F8FF</span><span class="sxs-lookup"><span data-stu-id="15ee7-569">E000 - F8FF</span></span>|<span data-ttu-id="15ee7-570">`IsPrivateUse` 或 `IsPrivateUseArea`</span><span class="sxs-lookup"><span data-stu-id="15ee7-570">`IsPrivateUse` or `IsPrivateUseArea`</span></span>|  
|<span data-ttu-id="15ee7-571">F900 - FAFF</span><span class="sxs-lookup"><span data-stu-id="15ee7-571">F900 - FAFF</span></span>|`IsCJKCompatibilityIdeographs`|  
|<span data-ttu-id="15ee7-572">FB00 - FB4F</span><span class="sxs-lookup"><span data-stu-id="15ee7-572">FB00 - FB4F</span></span>|`IsAlphabeticPresentationForms`|  
|<span data-ttu-id="15ee7-573">FB50 - FDFF</span><span class="sxs-lookup"><span data-stu-id="15ee7-573">FB50 - FDFF</span></span>|`IsArabicPresentationForms-A`|  
|<span data-ttu-id="15ee7-574">FE00 - FE0F</span><span class="sxs-lookup"><span data-stu-id="15ee7-574">FE00 - FE0F</span></span>|`IsVariationSelectors`|  
|<span data-ttu-id="15ee7-575">FE20 - FE2F</span><span class="sxs-lookup"><span data-stu-id="15ee7-575">FE20 - FE2F</span></span>|`IsCombiningHalfMarks`|  
|<span data-ttu-id="15ee7-576">FE30 - FE4F</span><span class="sxs-lookup"><span data-stu-id="15ee7-576">FE30 - FE4F</span></span>|`IsCJKCompatibilityForms`|  
|<span data-ttu-id="15ee7-577">FE50 - FE6F</span><span class="sxs-lookup"><span data-stu-id="15ee7-577">FE50 - FE6F</span></span>|`IsSmallFormVariants`|  
|<span data-ttu-id="15ee7-578">FE70 - FEFF</span><span class="sxs-lookup"><span data-stu-id="15ee7-578">FE70 - FEFF</span></span>|`IsArabicPresentationForms-B`|  
|<span data-ttu-id="15ee7-579">FF00 - FFEF</span><span class="sxs-lookup"><span data-stu-id="15ee7-579">FF00 - FFEF</span></span>|`IsHalfwidthandFullwidthForms`|  
|<span data-ttu-id="15ee7-580">FFF0 - FFFF</span><span class="sxs-lookup"><span data-stu-id="15ee7-580">FFF0 - FFFF</span></span>|`IsSpecials`|  
  
<a name="CharacterClassSubtraction"></a>   
## <a name="character-class-subtraction-basegroup---excludedgroup"></a><span data-ttu-id="15ee7-581">字元類別減法：[base_group - [excluded_group]]</span><span class="sxs-lookup"><span data-stu-id="15ee7-581">Character class subtraction: [base_group - [excluded_group]]</span></span>  
 <span data-ttu-id="15ee7-582">字元類別會定義字元集，</span><span class="sxs-lookup"><span data-stu-id="15ee7-582">A character class defines a set of characters.</span></span> <span data-ttu-id="15ee7-583">字元類別減法會產生字元集，這個字元集是將某一個字元類別中的字元從另一個字元類別中排除的結果。</span><span class="sxs-lookup"><span data-stu-id="15ee7-583">Character class subtraction yields a set of characters that is the result of excluding the characters in one character class from another character class.</span></span>  
  
 <span data-ttu-id="15ee7-584">字元類別減法運算式的格式如下：</span><span class="sxs-lookup"><span data-stu-id="15ee7-584">A character class subtraction expression has the following form:</span></span>  
  
 <span data-ttu-id="15ee7-585">`[` *base_group* `-[` *excluded_group* `]]`</span><span class="sxs-lookup"><span data-stu-id="15ee7-585">`[` *base_group* `-[` *excluded_group* `]]`</span></span>  
  
 <span data-ttu-id="15ee7-586">方括號 (`[]`) 和連字號 (`-`) 為必要。</span><span class="sxs-lookup"><span data-stu-id="15ee7-586">The square brackets (`[]`) and hyphen (`-`) are mandatory.</span></span> <span data-ttu-id="15ee7-587">*base_group* 是[正字元群組](#PositiveGroup)或[負字元群組](#NegativeGroup)。</span><span class="sxs-lookup"><span data-stu-id="15ee7-587">The *base_group* is a [positive character group](#PositiveGroup) or a [negative character group](#NegativeGroup).</span></span> <span data-ttu-id="15ee7-588">*excluded_group* 元件是另一個正字元群組或負字元群組，或者是另一個字元類別減法運算式 (也就是說，您可以將字元類別減法運算式設為巢狀)。</span><span class="sxs-lookup"><span data-stu-id="15ee7-588">The *excluded_group* component is another positive or negative character group, or another character class subtraction expression (that is, you can nest character class subtraction expressions).</span></span>  
  
 <span data-ttu-id="15ee7-589">例如，假設您有一個由 "a" 到 "z" 字元範圍組成的基底群組。</span><span class="sxs-lookup"><span data-stu-id="15ee7-589">For example, suppose you have a base group that consists of the character range from "a" through "z".</span></span> <span data-ttu-id="15ee7-590">若要定義一組由基底群組所組成的字元，但不包括字元 "m"，則使用 `[a-z-[m]]`。</span><span class="sxs-lookup"><span data-stu-id="15ee7-590">To define the set of characters that consists of the base group except for the character "m", use `[a-z-[m]]`.</span></span> <span data-ttu-id="15ee7-591">若要定義一組由基底群組所組成的字元，但不包括 "d"、"j" 和 "p" 這組字元，則使用 `[a-z-[djp]]`。</span><span class="sxs-lookup"><span data-stu-id="15ee7-591">To define the set of characters that consists of the base group except for the set of characters "d", "j", and "p", use `[a-z-[djp]]`.</span></span> <span data-ttu-id="15ee7-592">若要定義一組由基底群組所組成的字元，但不包括 "m" 到 "p" 的字元範圍，則使用 `[a-z-[m-p]]`。</span><span class="sxs-lookup"><span data-stu-id="15ee7-592">To define the set of characters that consists of the base group except for the character range from "m" through "p", use `[a-z-[m-p]]`.</span></span>  
  
 <span data-ttu-id="15ee7-593">請考慮使用巢狀字元類別減法運算式 `[a-z-[d-w-[m-o]]]`。</span><span class="sxs-lookup"><span data-stu-id="15ee7-593">Consider the nested character class subtraction expression, `[a-z-[d-w-[m-o]]]`.</span></span> <span data-ttu-id="15ee7-594">這個運算式會從最內部的字元範圍向外評估。</span><span class="sxs-lookup"><span data-stu-id="15ee7-594">The expression is evaluated from the innermost character range outward.</span></span> <span data-ttu-id="15ee7-595">首先從 "d" 到 "w" 字元範圍減去 "m" 到 "o" 字元範圍，這樣會產生從 "d" 到 "l" 及從 "p" 到 "w" 的字元集。</span><span class="sxs-lookup"><span data-stu-id="15ee7-595">First, the character range from "m" through "o" is subtracted from the character range "d" through "w", which yields the set of characters from "d" through "l" and "p" through "w".</span></span> <span data-ttu-id="15ee7-596">接著會從字元範圍 "a" 到 "z" 中減去該字元集，此時會產生 `[abcmnoxyz]` 字元集。</span><span class="sxs-lookup"><span data-stu-id="15ee7-596">That set is then subtracted from the character range from "a" through "z", which yields the set of characters `[abcmnoxyz]`.</span></span>  
  
 <span data-ttu-id="15ee7-597">您可以使用任何字元類別搭配字元類別減法。</span><span class="sxs-lookup"><span data-stu-id="15ee7-597">You can use any character class with character class subtraction.</span></span> <span data-ttu-id="15ee7-598">若要定義由 \u0000 到 \uFFFF 的所有 Unicode 字元組成的字元集，但是不包含空白字元 (`\s`)、標點符號一般分類內的字元 (`\p{P}`)、`IsGreek` 具名區塊內的字元 (`\p{IsGreek}`) 以及 Unicode NEXT LINE 控制字元 (\x85)，請使用 `[\u0000-\uFFFF-[\s\p{P}\p{IsGreek}\x85]]`。</span><span class="sxs-lookup"><span data-stu-id="15ee7-598">To define the set of characters that consists of all Unicode characters from \u0000 through \uFFFF except white-space characters (`\s`), the characters in the punctuation general category (`\p{P}`), the characters in the `IsGreek` named block (`\p{IsGreek}`), and the Unicode NEXT LINE control character (\x85), use `[\u0000-\uFFFF-[\s\p{P}\p{IsGreek}\x85]]`.</span></span>  
  
 <span data-ttu-id="15ee7-599">為字元類別減法運算式選擇將會產生有用結果的字元類別，</span><span class="sxs-lookup"><span data-stu-id="15ee7-599">Choose character classes for a character class subtraction expression that will yield useful results.</span></span> <span data-ttu-id="15ee7-600">避免選擇會產生空字元集的運算式，該運算式無法比對任何項目，也不要選擇相當於原始基底群組的運算式。</span><span class="sxs-lookup"><span data-stu-id="15ee7-600">Avoid an expression that yields an empty set of characters, which cannot match anything, or an expression that is equivalent to the original base group.</span></span> <span data-ttu-id="15ee7-601">例如，空集合是 `[\p{IsBasicLatin}-[\x00-\x7F]]` 運算式的結果，該運算式會從 `IsBasicLatin` 一般分類中減去 `IsBasicLatin` 字元範圍中的所有字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-601">For example, the empty set is the result of the expression `[\p{IsBasicLatin}-[\x00-\x7F]]`, which subtracts all characters in the `IsBasicLatin` character range from the `IsBasicLatin` general category.</span></span> <span data-ttu-id="15ee7-602">同樣地，原始基底群組是 `[a-z-[0-9]]` 運算式的結果。</span><span class="sxs-lookup"><span data-stu-id="15ee7-602">Similarly, the original base group is the result of the expression `[a-z-[0-9]]`.</span></span>  <span data-ttu-id="15ee7-603">這是因為基底群組就是從 "a" 到 "z" 的字母字元範圍，該群組不包含已排除之群組中的任何字元，也就是從 "0" 到 "9" 的十進位數字字元範圍。</span><span class="sxs-lookup"><span data-stu-id="15ee7-603">This is because the base group, which is the character range of letters from "a" through "z", does not contain any characters in the excluded group, which is the character range of decimal digits from "0" through "9".</span></span>  
  
 <span data-ttu-id="15ee7-604">下列範例會定義規則運算式 (`^[0-9-[2468]]+$`)，該運算式會比對輸入字串中的零和奇數數字。</span><span class="sxs-lookup"><span data-stu-id="15ee7-604">The following example defines a regular expression, `^[0-9-[2468]]+$`, that matches zero and odd digits in an input string.</span></span>  <span data-ttu-id="15ee7-605">規則運算式的解譯方式如下表所示。</span><span class="sxs-lookup"><span data-stu-id="15ee7-605">The regular expression is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="15ee7-606">元素</span><span class="sxs-lookup"><span data-stu-id="15ee7-606">Element</span></span>|<span data-ttu-id="15ee7-607">說明</span><span class="sxs-lookup"><span data-stu-id="15ee7-607">Description</span></span>|  
|-------------|-----------------|  
|^|<span data-ttu-id="15ee7-608">從輸入字串開頭開始比對。</span><span class="sxs-lookup"><span data-stu-id="15ee7-608">Begin the match at the start of the input string.</span></span>|  
|`[0-9-[2468]]+`|<span data-ttu-id="15ee7-609">比對 0 到 9 中不包括 2、4、6 和 8 的任何出現一次或多次的字元。</span><span class="sxs-lookup"><span data-stu-id="15ee7-609">Match one or more occurrences of any character from 0 to 9 except for 2, 4, 6, and 8.</span></span> <span data-ttu-id="15ee7-610">換句話說，就是比對出現一次或多次的零或奇數。</span><span class="sxs-lookup"><span data-stu-id="15ee7-610">In other words, match one or more occurrences of zero or an odd digit.</span></span>|  
|$|<span data-ttu-id="15ee7-611">在輸入字串結尾結束比對。</span><span class="sxs-lookup"><span data-stu-id="15ee7-611">End the match at the end of the input string.</span></span>|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/classsubtraction1.cs#15)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/classsubtraction1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="15ee7-612">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15ee7-612">See also</span></span>

- <xref:System.Char.GetUnicodeCategory%2A>
- [<span data-ttu-id="15ee7-613">規則運算式語言 - 快速參考</span><span class="sxs-lookup"><span data-stu-id="15ee7-613">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [<span data-ttu-id="15ee7-614">規則運算式選項</span><span class="sxs-lookup"><span data-stu-id="15ee7-614">Regular Expression Options</span></span>](../../../docs/standard/base-types/regular-expression-options.md)
