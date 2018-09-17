---
title: 規則運算式中的反向參考建構
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
ms.openlocfilehash: 7953e34f76e23e3f9f4913726adc4b2176b172c9
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45615322"
---
# <a name="backreference-constructs-in-regular-expressions"></a>規則運算式中的反向參考建構
反向參考提供便利的方式來識別字串內的重複字元或子字串。 例如，如果輸入字串包含多次出現的任意子字串，您可以比對第一個出現的子字串與擷取的群組，接著使用反向參考來比對隨後出現的子字串。  
  
> [!NOTE]
>  對於取代字串中的具名和編號擷取群組，會使用不同的語法來參考。 如需詳細資訊，請參閱 [Substitutions](substitutions-in-regular-expressions.md)。  
  
 .NET 會定義個別的語言項目，以參考編號和具名擷取群組。 如需擷取群組的詳細資訊，請參閱[群組建構](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)。  
  
## <a name="numbered-backreferences"></a>編號反向參考  
 編號反向參考會使用下列語法：  
  
 `\` *數字*  
  
 其中 *number* 是規則運算式中的擷取群組序數位置。 例如，`\4` 會比對第四個擷取群組的內容。 如果規則運算式模式中未定義 *number*，便會發生剖析錯誤，而規則運算式引擎會擲回 <xref:System.ArgumentException>。 例如，規則運算式 `\b(\w+)\s\1` 有效，因為 `(\w+)` 是運算式中第一個和唯一的擷取群組。 另一方面，`\b(\w+)\s\2` 無效並擲回引數例外狀況，因為沒有編號為 `\2` 的擷取群組。 此外，如果 *number* 識別在特定序數位置的擷取群組，但擷取群組已經被指派和其序數順序不同的數值名稱，則規則運算式剖析器也會擲回 <xref:System.ArgumentException>。 
  
 請注意八進位逸出字碼 (例如 `\16`) 與使用相同標記法之 `\`*number* 反向參考間的模稜兩可。 這個模棱兩可的情況已解決，如下所示：  
  
-   運算式 `\1` 到 `\9` 一律會解譯為反向參考，而不是八進位字碼。  
  
-   如果多位數運算式的第一個數字是 8 或 9 (例如 `\80` 或 `\91`)，該運算式會解譯為常值。  
  
-   從 `\10` 到更大值的運算式會視為反向參考 (如果有對應至該數字的反向參考)，否則會解譯為八進位字碼。  
  
-   如果規則運算式包含未定義之群組號碼的反向參考，便會發生剖析錯誤，而規則運算式引擎會擲回 <xref:System.ArgumentException>。  
  
 如果模擬兩可會造成問題，您可以使用 `\k<`*name*`>` 標記法，這樣就不會造成模擬兩可，而且不會與八進位字元碼混淆。 同樣地，十六進位字碼 (例如 `\xdd`) 不會不明確，而且不會與反向參考混淆。  
  
 下列範例會在字串中尋找雙字組字元。 它會定義由下列項目組成的規則運算式 `(\w)\1`。  
  
|元素|描述|  
|-------------|-----------------|  
|`(\w)`|比對文字字元，並將其指派給第一個擷取群組。|  
|`\1`|比對與第一個擷取群組之值相同的下一個字元。|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
 [!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]  
  
## <a name="named-backreferences"></a>具名反向參考  
 具名反向參考是使用下列語法來定義：  
  
 `\k<` *name* `>`  
  
 或：  
  
 `\k'` *name* `'`  
  
 其中 *name* 是規則運算式模式中所定義之擷取群組的名稱。 如果規則運算式模式中未定義 *name*，便會發生剖析錯誤，而規則運算式引擎會擲回 <xref:System.ArgumentException>。  
  
 下列範例會在字串中尋找雙字組字元。 它會定義由下列項目組成的規則運算式 `(?<char>\w)\k<char>`。  
  
|元素|描述|  
|-------------|-----------------|  
|`(?<char>\w)`|比對字組字元，並將其指派給名為 `char` 的擷取群組。|  
|`\k<char>`|比對下一個與 `char` 擷取群組值相同的字元。|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
 [!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]  

## <a name="named-numeric-backreferences"></a>具名的數值反向參考

在含有 `\k` 的具名反向參考中，*name* 也可以是數字的字串表示。 例如，下列範例會使用規則運算式 `(?<2>\w)\k<2>` 來尋找字串中的雙字組字元。 在此案例中，範例定義了明確地命名為 "2" 的擷取群組，而反向參考也相對應地命名為 "2"。 
  
 [!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
 [!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]  

如果 *name* 是數值的字串表示，且沒有擷取群組具有該名稱，則 `\k<`*name*`>` 和反向參考 `\`*number* 是相同的，其中 *number* 是擷取的序數位置。 在下列範例中，有名為 `char` 的單一擷取群組。 反向參考建構將它參考為 `\k<1>`。 如範例的輸出所示，因為 `char` 是第一個擷取群組，因此對 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> 的呼叫會成功。

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference6.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference6.vb)]  

不過，如果 *name* 是數值的字串表示，且在該位置的擷取群組已經明確地被指派數值名稱，則規則運算式剖析器無法根據擷取群組的序數位置識別它。 相反地，它會擲回 <xref:System.ArgumentException>。下列範例中的唯一擷取群組名為 "2"。 因為 `\k` 建構是用來定義名為 "1" 的反向參考，所以規則運算式剖析器無法識別第一個擷取群組並擲回例外狀況。

[!code-csharp[Ordinal.Backreference](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference7.cs)]
[!code-vb[Ordinal.BackReference](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference7.vb)]  

## <a name="what-backreferences-match"></a>反向參考比對的項目  
 反向參考會參考群組最近使用的定義 (由左至右比對時，最接近左邊的定義)。 當群組進行多個擷取時，反向參考會參考最近發生的擷取。  
  
 下列範例包含規則運算式模式 `(?<1>a)(?<1>\1b)*`，此模式可重新定義 \1 具名群組。 下表說明規則運算式中的每個模式。  
  
|模式|描述|  
|-------------|-----------------|  
|`(?<1>a)`|比對字元 "a"，並將結果指派給名為 `1` 的擷取群組。|  
|`(?<1>\1b)*`|比對出現 0 或 1 次且名稱由 `1` 和 "b" 組成的群組，並將結果指派給名為 `1` 的擷取群組。|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
 [!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]  
  
 在比較規則運算式與輸入字串 ("aababb") 時，規則運算式引擎會執行下列作業：  
  
1.  它會從該字串的開頭開始，並且成功地比對 "a" 與運算式 `(?<1>a)`。 `1` 群組的值現在是 "a"。  
  
2.  它會前進到第二個字元，並且成功地比對字串 "ab" 與運算式 `\1b`，或是 "ab"。 然後它會將結果 "ab" 指派給 `\1`。  
  
3.  它會前進到第四個字元。 運算式 `(?<1>\1b)` 要比對零次以上，才算成功地比對字串 "abb" 與運算式 `\1b`。 然後它會將結果 "abb" 指派回到 `\1`。  
  
 在此範例中，`*` 是迴圈數量詞，它會重複評估直到規則運算式引擎無法符合其所定義的模式為止。 迴圈數量詞並不會清除群組定義。  
  
 如果群組沒有擷取任何子字串，該群組的反向參考會是未定義的，而且永遠不會進行比對。 這可由定義如下的規則運算式模式 `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b` 來說明：  
  
|模式|描述|  
|-------------|-----------------|  
|`\b`|開始字邊界比對。|  
|`(\p{Lu}{2})`|比對兩個大寫字母。 這是第一個擷取群組。|  
|`(\d{2})?`|比對出現零次或一次的兩個十進位數字。 這是第二個擷取群組。|  
|`(\p{Lu}{2})`|比對兩個大寫字母。 這是第三個擷取群組。|  
|`\b`|結束字邊界比對。|  
  
 輸入字串可以符合這個規則運算式，即使不存在第二個擷取群組所定義的兩個十進位數字亦然。 下列範例顯示即使比對成功，仍會在兩個成功的擷取群組之間找到空的擷取群組。  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
 [!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]  
  
## <a name="see-also"></a>另請參閱

- [規則運算式語言 - 快速參考](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
