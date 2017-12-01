---
title: "規則運算式中的字元類別"
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
- character classes
- regular expressions, character classes
- characters, matching syntax
- .NET Framework regular expressions, character classes
ms.assetid: 0f8bffab-ee0d-4e0e-9a96-2b4a252bb7e4
caps.latest.revision: "58"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 603633e1a0f385c061fe0928ea7361490d61fa3e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="character-classes-in-regular-expressions"></a>規則運算式中的字元類別
<a name="Top"></a> 字元類別會定義一組字元，其中任何字元都可在輸入字串中出現，以便讓比對成功。 .NET 中的規則運算式語言支援下列字元類別：  
  
-   正字元群組。 輸入字串中的字元必須符合指定字元集的其中一個字元。 如需詳細資訊，請參閱[正字元群組](#PositiveGroup)。  
  
-   負字元群組。 輸入字串中的字元不得符合指定字元集的其中一個字元。 如需詳細資訊，請參閱[負字元群組](#NegativeGroup)。  
  
-   任何字元。 在規則運算式中的 `.` (點或句號) 字元是萬用字元，可符合 `\n` 以外的任何字元。 如需詳細資訊，請參閱[任何字元](#AnyCharacter)。  
  
-   一般 Unicode 分類或具名區塊。 輸入字串中的字元必須是特定 Unicode 分類的成員，或者必須落在 Unicode 字元的連續範圍內，比對才會成功。 如需詳細資訊，請參閱 [Unicode 分類或 Unicode 區塊](#CategoryOrBlock)。  
  
-   負的一般 Unicode 分類或是具名區塊。 輸入字串中的字元不得是特定 Unicode 分類的成員，或者不得落在 Unicode 字元的連續範圍內，比對才會成功。 如需詳細資訊，請參閱[負 Unicode 分類或 Unicode 區塊](#NegativeCategoryOrBlock)。  
  
-   文字字元。 輸入字串中的字元可以隸屬於任何適用於文字字元的 Unicode 分類。 如需詳細資訊，請參閱[文字字元](#WordCharacter)。  
  
-   非文字字元。 輸入字串中的字元可以隸屬於任何非文字字元的 Unicode 分類。 如需詳細資訊，請參閱[非文字字元](#NonWordCharacter)。  
  
-   空白字元。 輸入字串中的字元可以是任何 Unicode 分隔符號字元，以及任何一種控制字元。 如需詳細資訊，請參閱[空白字元](#WhitespaceCharacter)。  
  
-   非空白字元。 輸入字串中的字元可以是空白字元以外的任何字元。 如需詳細資訊，請參閱[非空白字元](#NonWhitespaceCharacter)。  
  
-   十進位數字。 輸入字串中的字元可以是歸類為 Unicode 十進位數字的任何一個數字字元。 如需詳細資訊，請參閱[十進位數字字元](#DigitCharacter)。  
  
-   非十進位數字。 輸入字串中的字元可以是 Unicode 十進位數字以外的任何字元。 如需詳細資訊，請參閱[十進位數字字元](#NonDigitCharacter)。  
  
 .NET 支援字元類別減法運算式，可讓您將一組字元定義為從某個字元類別中排除另一個字元類別的結果。 如需詳細資訊，請參閱[字元類別減法](#CharacterClassSubtraction)。  
  
> [!NOTE]
>  字元類別，例如，依類別目錄，比對字元[\w](#WordCharacter)來比對文字字元或[\p {}](#CategoryOrBlock)要比對 Unicode 分類，依賴<xref:System.Globalization.CharUnicodeInfo>類別，以提供字元的相關資訊類別目錄。  從 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 開始，字元類別根據 [Unicode 標準 8.0.0 版](http://www.unicode.org/versions/Unicode8.0.0/)。 在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 至 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 中，它們根據 [Unicode 標準 6.3.0 版](http://www.unicode.org/versions/Unicode6.3.0/)。  
  
<a name="PositiveGroup"></a>   
## <a name="positive-character-group--"></a>正字元群組：[ ]  
 正字元群組會指定一份字元清單，其中任何字元都可出現在輸入字串中，以便出現相符項目。 這份字元清單可以個別指定，也可以依範圍指定，或同時依兩種方式指定。  
  
 指定個別字元清單的語法如下所示：  
  
 [*character_group*]  
  
 其中 *character_group* 是為了讓比對成功而可以出現在輸入字串中的個別字元清單。 *character_group*可以由一或多個常值字元、[逸出字元](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md)或字元類別的任何組合所構成。  
  
 指定字元範圍的語法如下所示：  
  
```  
[firstCharacter-lastCharacter]  
```  
  
 其中 *firstCharacter* 是範圍開始的字元，而 *lastCharacter* 是範圍結束的字元。 字元範圍是指一系列連續的字元，定義的方式是指定系列中的第一個字元、連字號 (-)，然後是系列中的最後一個字元。 如果兩個字元具有相鄰的 Unicode 字碼指標，這兩個字元就是連續字元。  
  
 下表列出一些包含正字元類別的常見規則運算式模式。  
  
|模式|描述|  
|-------------|-----------------|  
|`[aeiou]`|比對所有母音。|  
|`[\p{P}\d]`|比對所有標點符號和十進位數字字元。|  
|`[\s\p{P}]`|比對所有空白字元和標點符號。|  
  
 下列範例會定義包含字元 "a" 和 "e" 的正字元群組，因此輸入字串必須包含文字 "grey" 或 "gray" 且後面接著另一個文字，才會出現相符項目。  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/positivecharclasses.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/positivecharclasses.vb#1)]  
  
 規則運算式 `gr[ae]y\s\S+?[\s|\p{P}]` 定義如下：  
  
|模式|描述|  
|-------------|-----------------|  
|`gr`|比對常值字元 "gr"。|  
|`[ae]`|比對 "a" 或 "e"。|  
|`y\s`|比對後面接著空白字元的常值字元 "y"。|  
|`\S+?`|比對一個或多個非空白字元，但越少越好。|  
|`[\s\p{P}]`|比對空白字元或標點符號。|  
  
 下列範例將比對以任何大寫字母開頭的文字。 範例將使用子運算式 `[A-Z]` 表示從 A 到 Z 的大寫字母範圍。  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/range.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/range.vb#3)]  
  
 規則運算式 `\b[A-Z]\w*\b` 的定義如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`\b`|從字緣開始。|  
|`[A-Z]`|比對從 A 到 Z 的任何大寫字元。|  
|`\w*`|比對零個或多個文字字元。|  
|`\b`|比對字邊界。|  
  
 [回到頁首](#Top)  
  
<a name="NegativeGroup"></a>   
## <a name="negative-character-group-"></a>負字元群組：[^]  
 負字元群組會指定一份字元清單，其中任何字元不得出現在輸入字串中，才會出現相符項目。 字元清單可以個別指定，也可以依範圍指定，或同時依兩種方式指定。  
  
 指定個別字元清單的語法如下所示：  
  
 [*^character_group*]  
  
 其中 *character_group* 是為了讓比對成功而不可出現在輸入字串中的個別字元清單。 *character_group*可以由一或多個常值字元、[逸出字元](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md)或字元類別的任何組合所構成。  
  
 指定字元範圍的語法如下所示：  
  
 [^*firstCharacter*-*lastCharacter*]  
  
 其中 *firstCharacter* 是範圍開始的字元，而 *lastCharacter* 是範圍結束的字元。 字元範圍是指一系列連續的字元，定義的方式是指定系列中的第一個字元、連字號 (-)，然後是系列中的最後一個字元。 如果兩個字元具有相鄰的 Unicode 字碼指標，這兩個字元就是連續字元。  
  
 可以串連兩個或多個字元範圍。 例如，若要指定從 "0" 到 "9" 的十進位數字範圍、從 "a" 到 "f" 的小寫字母範圍，以及從 "A" 到 "F" 的大寫字母範圍，可以使用 `[0-9a-fA-F]`。  
  
 負字元群組中的前置 `^` 字元是必要的，它表示字元群組是負字元群組而非正字元群組。  
  
> [!IMPORTANT]
>  較大規則運算式模式中的負字元群組不是零寬度的判斷提示。 也就是說，在評估負字元群組之後，規則運算式引擎會在輸入字串中前進一個字元。  
  
 下表列出一些包含負字元群組的常見規則運算式模式。  
  
|模式|描述|  
|-------------|-----------------|  
|`[^aeiou]`|比對除了母音之外的所有字元。|  
|`[^\p{P}\d]`|比對標點符號和十進位數字字元之外的所有字元。|  
  
 下列範例將比對任何開頭字元是 "th" 且後面不是接著 "o" 的文字。  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/negativecharclasses.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/negativecharclasses.vb#2)]  
  
 規則運算式 `\bth[^o]\w+\b` 的定義如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`\b`|從字緣開始。|  
|`th`|比對常值字元 "th"。|  
|`[^o]`|比對不是 "o" 的任何字元。|  
|`\w+`|比對一個或多個文字字元。|  
|`\b`|在字邊界結束。|  
  
 [回到頁首](#Top)  
  
<a name="AnyCharacter"></a>   
## <a name="any-character-"></a>任何字元：  
 句號字元 (.) 會比對 `\n` (新行字元 \u000A) 以外任何具有下列兩項資格的字元：  
  
-   如果 <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> 選項修改了規則運算式模式，或是 `.` 選項修改了模式中包含 `s` 字元類別的部分，`.` 就會符合任何字元。 如需詳細資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)。  
  
     下列範例將示範 `.` 字元類別的預設行為與使用 <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> 選項的行為有何不同。 規則運算式 `^.+` 會從字串開頭開始，比對每一個字元。 根據預設，比對會在第一行結尾結束。規則運算式模式會比對歸位字元 `\r` 或 \u000D，但不會比對 `\n`。 由於 <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> 選項會將整個輸入字串解譯為單行，因此它會比對輸入字串中的每個字元，包括 `\n`。  
  
     [!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
     [!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]  
  
> [!NOTE]
>  由於它會比對 `\n` 以外的任何字元，因此 `.` 字元類別也會比對 `\r` (歸位字元 \u000D)。  
  
-   在正或負字元群組中，句號會視為常值句號字元而非字元類別。 如需詳細資訊，請參閱本主題前段的[正字元群組](#PositiveGroup)和[負字元群組](#NegativeGroup)。 下列範例將進行示範，定義包含句號字元 (`.`) 做為字元類別以及做為正字元群組成員的規則運算式。 規則運算式 `\b.*[.?!;:](\s|\z)` 會從字邊界開始比對所有字元，直到遇到包括句號的四個標點符號其中之一，然後比對空白字元或字串結尾。  
  
     [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any1.cs#4)]
     [!code-vb[Conceptual.RegEx.Language.CharacterClasses#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any1.vb#4)]  
  
> [!NOTE]
>  由於它會比對任何字元，因此如果規則運算式模式嘗試多次比對任何字元，`.` 語言項目就會經常與 lazy 數量詞搭配使用。 如需詳細資訊，請參閱[數量詞](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)。  
  
 [回到頁首](#Top)  
  
<a name="CategoryOrBlock"></a>   
## <a name="unicode-category-or-unicode-block-p"></a>Unicode 類別或 Unicode 區塊：\p{}  
 Unicode 標準會為每個字元指派一種一般分類。 例如，特定字元可以是大寫字母 (以 `Lu` 分類表示)、十進位數字 (`Nd` 分類)、數學符號 (`Sm` 分類) 或段落分隔符號 (`Zl` 分類)。 Unicode 標準中的特定字元集也會佔據連續字碼指標的特定範圍或區塊。 例如，從 \u0000 到 \u007F 可找到基本拉丁字元集，從 \u0600 到 \u06FF 則可找到阿拉伯字元集。  
  
 規則運算式建構  
  
 `\p{` *name* `}`  
  
 比對屬於 Unicode 一般分類或具名區塊的任何字元，其中 *name* 是分類縮寫或具名區塊名稱。 如需分類縮寫的清單，請參閱本主題稍後的[支援的 Unicode 一般分類](#SupportedUnicodeGeneralCategories)一節。 如需具名區塊清單，請參閱本主題稍後的[支援的具名區塊](#SupportedNamedBlocks)一節。  
  
 下列範例會使用 `\p{`*name*`}` 建構同時比對 Unicode 一般類別 (在這個案例中是 `Pd`，或稱 [標點符號、虛線] 分類) 以及具名區塊 (`IsGreek` 和 `IsBasicLatin` 具名區塊)。  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/category1.cs#6)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/category1.vb#6)]  
  
 規則運算式 `\b(\p{IsGreek}+(\s)?)+\p{Pd}\s(\p{IsBasicLatin}+(\s)?)+` 的定義如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`\b`|從字緣開始。|  
|`\p{IsGreek}+`|比對一個或多個希臘字元。|  
|`(\s)?`|比對零個或一個空白字元。|  
|`(\p{IsGreek}+(\s)?)+`|一次或多次比對一個或多個希臘字元後面接著零或一個空白字元的模式。|  
|`\p{Pd}`|比對標點符號、虛線字元。|  
|`\s`|比對空白字元。|  
|`\p{IsBasicLatin}+`|比對一個或多個基本拉丁字元。|  
|`(\s)?`|比對零個或一個空白字元。|  
|`(\p{IsBasicLatin}+(\s)?)+`|一次或多次比對一個或多個基本拉丁字元後面接著零個或一個空白字元的模式。|  
  
 [回到頁首](#Top)  
  
<a name="NegativeCategoryOrBlock"></a>   
## <a name="negative-unicode-category-or-unicode-block-p"></a>負 Unicode 分類或 Unicode 區塊：\P{}  
 Unicode 標準會為每個字元指派一種一般分類。 例如，特定字元可以是大寫字母 (以 `Lu` 分類表示)、十進位數字 (`Nd` 分類)、數學符號 (`Sm` 分類) 或段落分隔符號 (`Zl` 分類)。 Unicode 標準中的特定字元集也會佔據連續字碼指標的特定範圍或區塊。 例如，從 \u0000 到 \u007F 可找到基本拉丁字元集，從 \u0600 到 \u06FF 則可找到阿拉伯字元集。  
  
 規則運算式建構  
  
 `\P{` *name* `}`  
  
 比對任何不屬於 Unicode 一般分類或具名區塊的字元，其中 *name* 是分類縮寫或是具名區塊名稱。 如需分類縮寫的清單，請參閱本主題稍後的[支援的 Unicode 一般分類](#SupportedUnicodeGeneralCategories)一節。 如需具名區塊清單，請參閱本主題稍後的[支援的具名區塊](#SupportedNamedBlocks)一節。  
  
 下列範例會使用 `\P{`*name*`}` 建構從數值字串中移除任何貨幣符號 (在這個案例中是 `Sc`，或稱 [符號、貨幣] 分類)。  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/notcategory1.cs#7)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/notcategory1.vb#7)]  
  
 規則運算式模式 `(\P{Sc})+` 會比對一個或多個不是貨幣符號的字元，並且會有效移除結果字串中的所有貨幣符號。  
  
 [回到頁首](#Top)  
  
<a name="WordCharacter"></a>   
## <a name="word-character-w"></a>文字字元：\w  
 `\w` 會比對任何文字字元。 文字字元是下表中所列的任何 Unicode 分類的成員。  
  
|分類|描述|  
|--------------|-----------------|  
|Ll|字母、小寫|  
|Lu|字母、大寫|  
|Lt|字母、字首大寫|  
|Lo|字母、其他|  
|Lm|字母、修飾詞|  
|Mn|記號，非間距|  
|Nd|數字、十進位數字|  
|Pc|標點符號、連接器。 這個分類包含十個字元，其中最常用的是 LOWLINE 字元 (_)，u+005F。|  
  
 如果指定了符合 ECMAScript 的行為，`\w` 就等於 `[a-zA-Z_0-9]`。 如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)中的＜ECMAScript 相符行為＞一節。  
  
> [!NOTE]
>  由於它會比對任何文字字元，因此，如果規則運算式模式嘗試多次比對任何文字字元且後面接著特定文字字元，`\w` 語言項目就會經常與 lazy 數量詞搭配使用。 如需詳細資訊，請參閱[數量詞](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)。  
  
 下列範例會使用 `\w` 語言項目比對文字中重複的字元。 這個範例會定義規則運算式模式 `(\w)\1`，該模式解譯如下。  
  
|項目|描述|  
|-------------|-----------------|  
|(\w)|比對文字字元。 這是第一個擷取群組。|  
|\1|比對第一個擷取的值。|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/wordchar1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/wordchar1.vb#8)]  
  
 [回到頁首](#Top)  
  
<a name="NonWordCharacter"></a>   
## <a name="non-word-character-w"></a>非文字字元：\W  
 `\W` 會比對任何非文字字元。 \W 語言項目相當於下列字元類別：  
  
```  
[^\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]  
```  
  
 換句話說，它會比對下表所列 Unicode 分類中字元以外的所有字元。  
  
|分類|描述|  
|--------------|-----------------|  
|Ll|字母、小寫|  
|Lu|字母、大寫|  
|Lt|字母、字首大寫|  
|Lo|字母、其他|  
|Lm|字母、修飾詞|  
|Mn|記號，非間距|  
|Nd|數字、十進位數字|  
|Pc|標點符號、連接器。 這個分類包含十個字元，其中最常用的是 LOWLINE 字元 (_)，u+005F。|  
  
 如果指定了符合 ECMAScript 的行為，`\W` 就等於 `[^a-zA-Z_0-9]`。 如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)中的＜ECMAScript 相符行為＞一節。  
  
> [!NOTE]
>  由於它會比對任何非文字字元，因此，如果規則運算式模式嘗試多次比對任何非文字字元，且後面接著特定非文字字元，`\W` 語言項目就會經常與 lazy 數量詞搭配使用。 如需詳細資訊，請參閱[數量詞](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)。  
  
 以下範例將說明 `\W` 字元類別。  它會定義規則運算式模式 `\b(\w+)(\W){1,2}`，該模式會比對後面接一個或多個非文字字元的文字，例如空白字元或標點符號。 規則運算式的解譯方式如下表所示。  
  
|項目|描述|  
|-------------|-----------------|  
|\b|開始字緣比對。|  
|(\w+)|比對一個或多個文字字元。 這是第一個擷取群組。|  
|(\W){1,2}|比對一次或兩次非文字字元。 這是第二個擷取群組。|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nonwordchar1.cs#9)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nonwordchar1.vb#9)]  
  
 由於第二個擷取群組的 <xref:System.Text.RegularExpressions.Group> 物件只包含單一擷取的非文字字元，因此這個範例會從 <xref:System.Text.RegularExpressions.CaptureCollection> 屬性所傳回之 <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> 物件擷取所有擷取的非文字字元。  
  
 [回到頁首](#Top)  
  
<a name="WhitespaceCharacter"></a>   
## <a name="white-space-character-s"></a>空白字元：\s  
 `\s` 會比對任何空白字元。 它相當於下表列出的逸出序列和 Unicode 分類。  
  
|分類|描述|  
|--------------|-----------------|  
|`\f`|換頁字元 \u000C。|  
|`\n`|新行字元 \u000A。|  
|`\r`|歸位字元 \u000D。|  
|`\t`|定位字元 \u0009。|  
|`\v`|垂直定位字元 \u000B。|  
|`\x85`|省略符號或 NEXT LINE (NEL) 字元 (…) \u0085。|  
|`\p{Z}`|比對任何分隔符號字元。|  
  
 如果指定了符合 ECMAScript 的行為，`\s` 就等於 `[ \f\n\r\t\v]`。 如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)中的＜ECMAScript 相符行為＞一節。  
  
 以下範例將說明 `\s` 字元類別。 它會定義規則運算式模式 `\b\w+(e)?s(\s|$)`，該模式會比對結尾為 "s" 或 "es" 且後面加上空白字元或是輸入字串結尾的文字。 規則運算式的解譯方式如下表所示。  
  
|項目|描述|  
|-------------|-----------------|  
|\b|開始字緣比對。|  
|\w+|比對一個或多個文字字元。|  
|(e)?|比對 "e" 零次或一次。|  
|s|比對 "s"。|  
|(\s&#124;$)|比對空白字元或輸入字串的結尾。|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/whitespace1.cs#10)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/whitespace1.vb#10)]  
  
 [回到頁首](#Top)  
  
<a name="NonWhitespaceCharacter"></a>   
## <a name="non-white-space-character-s"></a>非空白字元：\S  
 `\S` 會比對任何非空白字元。 它相當於 `[^\f\n\r\t\v\x85\p{Z}]` 規則運算式模式，或是規則運算式模式的相反模式，相當於會比對空白字元的 `\s`。 如需詳細資訊，請參閱[空白字元：\s](#WhitespaceCharacter)。  
  
 如果指定了符合 ECMAScript 的行為，`\S` 就等於 `[^ \f\n\r\t\v]`。 如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)中的＜ECMAScript 相符行為＞一節。  
  
 下列範例將說明 `\S` 語言項目。 規則運算式模式 `\b(\S+)\s?` 會比對以空白字元分隔的字串。 在比對之 <xref:System.Text.RegularExpressions.GroupCollection> 物件中的第二個項目包含相符的字串。 規則運算式的解譯方式如下表所示。  
  
|項目|描述|  
|-------------|-----------------|  
|`\b`|開始字緣比對。|  
|`(\S+)`|比對一個或多個非空白字元。 這是第一個擷取群組。|  
|`\s?`|比對零個或一個空白字元。|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nonwhitespace1.cs#11)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nonwhitespace1.vb#11)]  
  
 [回到頁首](#Top)  
  
<a name="DigitCharacter"></a>   
## <a name="decimal-digit-character-d"></a>十進位數字字元：\d  
 `\d` 會比對任何十進位數字。 它相當於 `\p{Nd}` 規則運算式模式，其中包括標準的十進位數字 0-9，以及若干其他字元集的十進位數字。  
  
 如果指定了符合 ECMAScript 的行為，`\d` 就等於 `[0-9]`。 如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)中的＜ECMAScript 相符行為＞一節。  
  
 下列範例將說明 `\d` 語言項目。 它會測試輸入字串是否表示美國和加拿大的有效電話號碼。 規則運算式模式 `^(\(?\d{3}\)?[\s-])?\d{3}-\d{4}$` 的定義如下表所示。  
  
|項目|描述|  
|-------------|-----------------|  
|`^`|在輸入字串的開頭開始比對。|  
|`\(?`|比對零個或一個常值 "(" 字元。|  
|`\d{3}`|比對三個十進位數字。|  
|`\)?`|比對零個或一個常值 ")" 字元。|  
|`[\s-]`|比對連字號或空白字元。|  
|`(\(?\d{3}\)?[\s-])?`|比對零次或一次選擇性的左括號，後面接著三個十進位數字、選擇性的右括號，以及空白字元或是連字號。 這是第一個擷取群組。|  
|`\d{3}-\d{4}`|比對三個十進位數字，後面接著連字號和另外四個十進位數字。|  
|`$`|比對輸入字串的結尾。|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/digit1.cs#12)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/digit1.vb#12)]  
  
 [回到頁首](#Top)  
  
<a name="NonDigitCharacter"></a>   
## <a name="non-digit-character-d"></a>非數字字元：\D  
 `\D` 會比對任何非數字字元。 它相當於 `\P{Nd}` 規則運算式模式。  
  
 如果指定了符合 ECMAScript 的行為，`\D` 就等於 `[^0-9]`。 如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)中的＜ECMAScript 相符行為＞一節。  
  
 下列範例將說明 \D 語言項目。 它會測試像是組件編號這類字串，是否由十進位和非十進位字元的適當組合所構成。 規則運算式模式 `^\D\d{1,5}\D*$` 的定義如下表所示。  
  
|項目|描述|  
|-------------|-----------------|  
|`^`|在輸入字串的開頭開始比對。|  
|`\D`|比對非數字字元。|  
|`\d{1,5}`|比對從一個到五個十進位數字。|  
|`\D*`|比對零個、一個或更多非十進位字元。|  
|`$`|比對輸入字串的結尾。|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/nondigit1.cs#13)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/nondigit1.vb#13)]  
  
 [回到頁首](#Top)  
  
<a name="SupportedUnicodeGeneralCategories"></a>   
## <a name="supported-unicode-general-categories"></a>支援的 Unicode 一般分類  
 Unicode 定義了下表中所列的一般類別。 如需詳細資訊，請參閱 [Unicode Character Database](http://go.microsoft.com/fwlink/?LinkId=57650) 中的 "UCD File Format" 和 "General Category Values" 副標題。  
  
|分類|描述|  
|--------------|-----------------|  
|`Lu`|字母、大寫|  
|`Ll`|字母、小寫|  
|`Lt`|字母、字首大寫|  
|`Lm`|字母、修飾詞|  
|`Lo`|字母、其他|  
|`L`|所有字母字元。 這包括 `Lu`、`Ll`、`Lt`、`Lm` 和 `Lo` 字元。|  
|`Mn`|記號，非間距|  
|`Mc`|記號，間距組合|  
|`Me`|記號，封入|  
|`M`|所有變音符號記號。 這包括 `Mn`、`Mc` 和 `Me` 分類。|  
|`Nd`|數字、十進位數字|  
|`Nl`|數字，字母|  
|`No`|數字，其他|  
|`N`|所有數字。 這包括 `Nd`、`Nl` 和 `No` 分類。|  
|`Pc`|標點符號，連接器|  
|`Pd`|標點符號，破折號|  
|`Ps`|標點符號，左括號|  
|`Pe`|標點符號，右括號|  
|`Pi`|標點符號，左引號 (根據使用方式，作用可能像 Ps 或 Pe)|  
|`Pf`|標點符號，右引號 (根據使用方式，作用可能像 Ps 或 Pe)|  
|`Po`|標點符號，其他|  
|`P`|所有標點符號字元。 這包括 `Pc`、`Pd`、`Ps`、`Pe`、`Pi`、`Pf` 和 `Po` 分類。|  
|`Sm`|符號，數學|  
|`Sc`|符號，貨幣|  
|`Sk`|符號，修飾詞|  
|`So`|符號，其他|  
|`S`|所有符號。 這包括 `Sm`、`Sc`、`Sk` 和 `So` 分類。|  
|`Zs`|分隔符號，空格|  
|`Zl`|分隔符號，行|  
|`Zp`|分隔符號，段落|  
|`Z`|所有分隔符號字元。 這包括 `Zs`、`Zl` 和 `Zp` 分類。|  
|`Cc`|其他，控制|  
|`Cf`|其他，格式|  
|`Cs`|其他，Surrogate|  
|`Co`|其他，專用|  
|`Cn`|其他，未指派 (沒有字元擁有這個屬性)|  
|`C`|所有控制字元。 這包括 `Cc`、`Cf`、`Cs`、`Co` 和 `Cn` 分類。|  
  
 您可以將任何特殊字元傳遞到 <xref:System.Char.GetUnicodeCategory%2A> 方法，以判斷該字元的 Unicode 分類。 下列範例會使用 <xref:System.Char.GetUnicodeCategory%2A> 方法判斷包含所選取拉丁字元的陣列中，每個項目的分類。  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/getunicodecategory1.cs#14)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/getunicodecategory1.vb#14)]  
  
 [回到頁首](#Top)  
  
<a name="SupportedNamedBlocks"></a>   
## <a name="supported-named-blocks"></a>支援的具名區塊  
 .NET 提供下表所列的具名區塊。 這一組支援的具名區塊是根據 Unicode 4.0 和 Perl 5.6。  
  
|字碼指標範圍|區塊名稱|  
|----------------------|----------------|  
|0000 - 007F|`IsBasicLatin`|  
|0080 - 00FF|`IsLatin-1Supplement`|  
|0100 - 017F|`IsLatinExtended-A`|  
|0180 - 024F|`IsLatinExtended-B`|  
|0250 - 02AF|`IsIPAExtensions`|  
|02B0 - 02FF|`IsSpacingModifierLetters`|  
|0300 - 036F|`IsCombiningDiacriticalMarks`|  
|0370 - 03FF|`IsGreek`<br /><br /> -或-<br /><br /> `IsGreekandCoptic`|  
|0400 - 04FF|`IsCyrillic`|  
|0500 - 052F|`IsCyrillicSupplement`|  
|0530 - 058F|`IsArmenian`|  
|0590 - 05FF|`IsHebrew`|  
|0600 - 06FF|`IsArabic`|  
|0700 - 074F|`IsSyriac`|  
|0780 - 07BF|`IsThaana`|  
|0900 - 097F|`IsDevanagari`|  
|0980 - 09FF|`IsBengali`|  
|0A00 - 0A7F|`IsGurmukhi`|  
|0A80 - 0AFF|`IsGujarati`|  
|0B00 - 0B7F|`IsOriya`|  
|0B80 - 0BFF|`IsTamil`|  
|0C00 - 0C7F|`IsTelugu`|  
|0C80 - 0CFF|`IsKannada`|  
|0D00 - 0D7F|`IsMalayalam`|  
|0D80 - 0DFF|`IsSinhala`|  
|0E00 - 0E7F|`IsThai`|  
|0E80 - 0EFF|`IsLao`|  
|0F00 - 0FFF|`IsTibetan`|  
|1000 - 109F|`IsMyanmar`|  
|10A0 - 10FF|`IsGeorgian`|  
|1100 - 11FF|`IsHangulJamo`|  
|1200 - 137F|`IsEthiopic`|  
|13A0 - 13FF|`IsCherokee`|  
|1400 - 167F|`IsUnifiedCanadianAboriginalSyllabics`|  
|1680 - 169F|`IsOgham`|  
|16A0 - 16FF|`IsRunic`|  
|1700 - 171F|`IsTagalog`|  
|1720 - 173F|`IsHanunoo`|  
|1740 - 175F|`IsBuhid`|  
|1760 - 177F|`IsTagbanwa`|  
|1780 - 17FF|`IsKhmer`|  
|1800 - 18AF|`IsMongolian`|  
|1900 - 194F|`IsLimbu`|  
|1950 - 197F|`IsTaiLe`|  
|19E0 - 19FF|`IsKhmerSymbols`|  
|1D00 - 1D7F|`IsPhoneticExtensions`|  
|1E00 - 1EFF|`IsLatinExtendedAdditional`|  
|1F00 - 1FFF|`IsGreekExtended`|  
|2000 - 206F|`IsGeneralPunctuation`|  
|2070 - 209F|`IsSuperscriptsandSubscripts`|  
|20A0 - 20CF|`IsCurrencySymbols`|  
|20D0 - 20FF|`IsCombiningDiacriticalMarksforSymbols`<br /><br /> -或-<br /><br /> `IsCombiningMarksforSymbols`|  
|2100 - 214F|`IsLetterlikeSymbols`|  
|2150 - 218F|`IsNumberForms`|  
|2190 - 21FF|`IsArrows`|  
|2200 - 22FF|`IsMathematicalOperators`|  
|2300 - 23FF|`IsMiscellaneousTechnical`|  
|2400 - 243F|`IsControlPictures`|  
|2440 - 245F|`IsOpticalCharacterRecognition`|  
|2460 - 24FF|`IsEnclosedAlphanumerics`|  
|2500 - 257F|`IsBoxDrawing`|  
|2580 - 259F|`IsBlockElements`|  
|25A0 - 25FF|`IsGeometricShapes`|  
|2600 - 26FF|`IsMiscellaneousSymbols`|  
|2700 - 27BF|`IsDingbats`|  
|27C0 - 27EF|`IsMiscellaneousMathematicalSymbols-A`|  
|27F0 - 27FF|`IsSupplementalArrows-A`|  
|2800 - 28FF|`IsBraillePatterns`|  
|2900 - 297F|`IsSupplementalArrows-B`|  
|2980 - 29FF|`IsMiscellaneousMathematicalSymbols-B`|  
|2A00 - 2AFF|`IsSupplementalMathematicalOperators`|  
|2B00 - 2BFF|`IsMiscellaneousSymbolsandArrows`|  
|2E80 - 2EFF|`IsCJKRadicalsSupplement`|  
|2F00 - 2FDF|`IsKangxiRadicals`|  
|2FF0 - 2FFF|`IsIdeographicDescriptionCharacters`|  
|3000 - 303F|`IsCJKSymbolsandPunctuation`|  
|3040 - 309F|`IsHiragana`|  
|30A0 - 30FF|`IsKatakana`|  
|3100 - 312F|`IsBopomofo`|  
|3130 - 318F|`IsHangulCompatibilityJamo`|  
|3190 - 319F|`IsKanbun`|  
|31A0 - 31BF|`IsBopomofoExtended`|  
|31F0 - 31FF|`IsKatakanaPhoneticExtensions`|  
|3200 - 32FF|`IsEnclosedCJKLettersandMonths`|  
|3300 - 33FF|`IsCJKCompatibility`|  
|3400 - 4DBF|`IsCJKUnifiedIdeographsExtensionA`|  
|4DC0 - 4DFF|`IsYijingHexagramSymbols`|  
|4E00 - 9FFF|`IsCJKUnifiedIdeographs`|  
|A000 - A48F|`IsYiSyllables`|  
|A490 - A4CF|`IsYiRadicals`|  
|AC00 - D7AF|`IsHangulSyllables`|  
|D800 - DB7F|`IsHighSurrogates`|  
|DB80 - DBFF|`IsHighPrivateUseSurrogates`|  
|DC00 - DFFF|`IsLowSurrogates`|  
|E000 - F8FF|`IsPrivateUse` 或 `IsPrivateUseArea`|  
|F900 - FAFF|`IsCJKCompatibilityIdeographs`|  
|FB00 - FB4F|`IsAlphabeticPresentationForms`|  
|FB50 - FDFF|`IsArabicPresentationForms-A`|  
|FE00 - FE0F|`IsVariationSelectors`|  
|FE20 - FE2F|`IsCombiningHalfMarks`|  
|FE30 - FE4F|`IsCJKCompatibilityForms`|  
|FE50 - FE6F|`IsSmallFormVariants`|  
|FE70 - FEFF|`IsArabicPresentationForms-B`|  
|FF00 - FFEF|`IsHalfwidthandFullwidthForms`|  
|FFF0 - FFFF|`IsSpecials`|  
  
 [回到頁首](#Top)  
  
<a name="CharacterClassSubtraction"></a>   
## <a name="character-class-subtraction-basegroup---excludedgroup"></a>字元類別減法：[base_group - [excluded_group]]  
 字元類別會定義字元集， 字元類別減法會產生字元集，這個字元集是將某一個字元類別中的字元從另一個字元類別中排除的結果。  
  
 字元類別減法運算式的格式如下：  
  
 `[` *base_group* `-[` *excluded_group* `]]`  
  
 方括號 (`[]`) 和連字號 (`-`) 為必要。 *base_group* 是[正字元群組](#PositiveGroup)或[負字元群組](#NegativeGroup)。 *excluded_group* 元件是另一個正字元群組或負字元群組，或者是另一個字元類別減法運算式 (也就是說，您可以將字元類別減法運算式設為巢狀)。  
  
 例如，假設您有一個由 "a" 到 "z" 字元範圍組成的基底群組。 若要定義一組由基底群組所組成的字元，但不包括字元 "m"，則使用 `[a-z-[m]]`。 若要定義一組由基底群組所組成的字元，但不包括 "d"、"j" 和 "p" 這組字元，則使用 `[a-z-[djp]]`。 若要定義一組由基底群組所組成的字元，但不包括 "m" 到 "p" 的字元範圍，則使用 `[a-z-[m-p]]`。  
  
 請考慮使用巢狀字元類別減法運算式 `[a-z-[d-w-[m-o]]]`。 這個運算式會從最內部的字元範圍向外評估。 首先從 "d" 到 "w" 字元範圍減去 "m" 到 "o" 字元範圍，這樣會產生從 "d" 到 "l" 及從 "p" 到 "w" 的字元集。 接著會從字元範圍 "a" 到 "z" 中減去該字元集，此時會產生 `[abcmnoxyz]` 字元集。  
  
 您可以使用任何字元類別搭配字元類別減法。 若要定義由 \u0000 到 \uFFFF 的所有 Unicode 字元組成的字元集，但是不包含空白字元 (`\s`)、標點符號一般分類內的字元 (`\p{P}`)、`IsGreek` 具名區塊內的字元 (`\p{IsGreek}`) 以及 Unicode NEXT LINE 控制字元 (\x85)，請使用 `[\u0000-\uFFFF-[\s\p{P}\p{IsGreek}\x85]]`。  
  
 為字元類別減法運算式選擇將會產生有用結果的字元類別， 避免選擇會產生空字元集的運算式，該運算式無法比對任何項目，也不要選擇相當於原始基底群組的運算式。 例如，空集合是 `[\p{IsBasicLatin}-[\x00-\x7F]]` 運算式的結果，該運算式會從 `IsBasicLatin` 一般分類中減去 `IsBasicLatin` 字元範圍中的所有字元。 同樣地，原始基底群組是 `[a-z-[0-9]]` 運算式的結果。  這是因為基底群組就是從 "a" 到 "z" 的字母字元範圍，該群組不包含已排除之群組中的任何字元，也就是從 "0" 到 "9" 的十進位數字字元範圍。  
  
 下列範例會定義規則運算式 (`^[0-9-[2468]]+$`)，該運算式會比對輸入字串中的零和奇數數字。  規則運算式的解譯方式如下表所示。  
  
|項目|描述|  
|-------------|-----------------|  
|^|從輸入字串開頭開始比對。|  
|`[0-9-[2468]]+`|比對 0 到 9 中不包括 2、4、6 和 8 的任何出現一次或多次的字元。 換句話說，就是比對出現一次或多次的零或奇數。|  
|$|在輸入字串結尾結束比對。|  
  
 [!code-csharp[Conceptual.RegEx.Language.CharacterClasses#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/classsubtraction1.cs#15)]
 [!code-vb[Conceptual.RegEx.Language.CharacterClasses#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/classsubtraction1.vb#15)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Char.GetUnicodeCategory%2A>  
 [規則運算式語言 - 快速參考](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 [規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)
