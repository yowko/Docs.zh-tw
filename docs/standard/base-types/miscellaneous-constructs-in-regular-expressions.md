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
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2018
ms.locfileid: "46580703"
---
# <a name="miscellaneous-constructs-in-regular-expressions"></a>規則運算式中的其他建構
.NET 中的規則運算式包含三個其他語言建構。 其中一個可讓您在規則運算式模式的中間，啟用或停用特定比對選項。 其餘兩個可讓您在規則運算式中包含註解。  
  
## <a name="inline-options"></a>內嵌選項  
 您可以使用下列語法，設定或停用部分規則運算式的特定模式比對選項  
  
```  
(?imnsx-imnsx)  
```  
  
 您在問號之後列出要啟用的選項，並在減號之後列出要停用的選項。 下表會說明每個選項。 如需每個選項的詳細資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)。  
  
|選項|描述|  
|------------|-----------------|  
|`i`|不區分大小寫的比對。|  
|`m`|多行模式。|  
|`n`|僅明確擷取 (括號不可作為擷取群組)。|  
|`s`|單行模式。|  
|`x`|忽略未逸出的空白字元，並允許 x 模式註解。|  
  
 `(?imnsx-imnsx)` 建構所定義之規則運算式選項中的任何變更，其效果會一直維持到封入群組的結尾。  
  
> [!NOTE]
>  `(?imnsx-imnsx:`*subexpression*`)` 群組建構會為子運算式提供完全相同的功能。 如需詳細資訊，請參閱[群組建構](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)。  
  
 下列範例會使用 `i`、`n` 及 `x` 選項來啟用不區分大小寫和明確擷取，並忽略規則運算式中間規則運算式模式中的空白字元。  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous1.cs#1)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous1.vb#1)]  
  
 此範例會定義兩個規則運算式。 第一個規則運算式 `\b(D\w+)\s(d\w+)\b` 會比對開頭為大寫 "D" 和小寫 "d" 的兩個連續字組。 第二個規則運算式 `\b(D\w+)(?ixn) \s (d\w+) \b` 會使用內嵌選項來修改此模式，如下表所述。 然後比較結果，以確認 `(?ixn)` 建構的效果。  
  
|模式|描述|  
|-------------|-----------------|  
|`\b`|從字緣開始。|  
|`(D\w+)`|比對後面接著一個或多個文字字元的大寫 "D"。 這是第一個擷取群組。|  
|`(?ixn)`|從這裡開始，進行不區分大小寫的比較、只進行明確擷取，並忽略規則運算式模式中的空白字元。|  
|`\s`|比對空白字元。|  
|`(d\w+)`|比對後面接著一個或多個文字字元的大寫或小寫 "d"。 因為已啟用 `n` (明確擷取) 選項，所以不會擷取此群組。|  
|`\b`|比對字邊界。|  
  
## <a name="inline-comment"></a>內嵌註解  
 `(?#` *comment*`)` 建構可讓您在規則運算式中包含內嵌註解。 規則運算式引擎不會在模式比對中使用註解的任一部分，不過，會將註解包含在 <xref:System.Text.RegularExpressions.Regex.ToString%2A?displayProperty=nameWithType> 方法所傳回的字串中。 註解會在第一個右括號結束。  
  
 下列範例會重複上一節範例中的第一個規則運算式模式。 它會將兩個內嵌註解加入規則運算式，以指出比較是否區分大小寫。 規則運算式模式 `\b((?# case-sensitive comparison)D\w+)\s(?ixn)((?#case-insensitive comparison)d\w+)\b` 定義如下。  
  
|模式|描述|  
|-------------|-----------------|  
|`\b`|從字緣開始。|  
|`(?# case-sensitive comparison)`|註解。 它不會影響模式比對行為。|  
|`(D\w+)`|比對後面接著一個或多個文字字元的大寫 "D"。 這是第一個擷取群組。|  
|`\s`|比對空白字元。|  
|`(?ixn)`|從這裡開始，進行不區分大小寫的比較、只進行明確擷取，並忽略規則運算式模式中的空白字元。|  
|`(?#case-insensitive comparison)`|註解。 它不會影響模式比對行為。|  
|`(d\w+)`|比對後面接著一個或多個文字字元的大寫或小寫 "d"。 這是第二個擷取群組。|  
|`\b`|比對字邊界。|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous2.cs#2)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous2.vb#2)]  
  
## <a name="end-of-line-comment"></a>行結尾註解  
 數字符號 (`#`) 會標記 x 模式註解，從規則運算式模式結尾中未逸出的 # 字元開始，並持續到該行結尾。 若要使用此建構，您必須在將 <xref:System.Text.RegularExpressions.Regex> 物件具現化或呼叫靜態 <xref:System.Text.RegularExpressions.Regex> 方法時，啟用 `x` 選項 (透過內嵌選項)，或將 <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> 值提供給 `option` 參數。  
  
 下列範例說明行結尾註解建構。 它會判斷字串是否為至少包含一個格式項目的複合格式字串。 下表說明規則運算式模式中的建構：  
  
 `\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item.`  
  
|模式|描述|  
|-------------|-----------------|  
|`\{`|比對左括號。|  
|`\d+`|比對一個或多個十進位數字。|  
|`(,-*\d+)*`|比對零個或一個出現的逗號，後面接著一個選擇性減號，再接著一個或多個十進位數字。|  
|`(\:\w{1,4}?)*`|比對零個或一個出現的冒號，後面接著一到四個 (但越少越好) 空白字元。|  
|`\}`|比對右括號。|  
|`(?x)`|啟用忽略模式空白字元選項，以辨識行結尾註解。|  
|`# Looks for a composite format item.`|行結尾註解。|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous3.cs#3)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous3.vb#3)]  
  
 請注意，除了在規則運算式中提供 `(?x)` 建構，也可以藉由呼叫 <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> 方法，並將 <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> 列舉值傳遞給此方法，來辨識註解。  
  
## <a name="see-also"></a>另請參閱

- [規則運算式語言 - 快速參考](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
