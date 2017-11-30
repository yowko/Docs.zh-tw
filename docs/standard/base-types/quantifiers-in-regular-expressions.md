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
# <a name="quantifiers-in-regular-expressions"></a>規則運算式中的數量詞
數量詞指定輸入中要有多少字元、群組或字元類別的執行個體，才能找到相符項目。  下表列出 .NET 支援的數量詞。  
  
|Greedy (窮盡) 數量詞|Lazy (最少) 數量詞|說明|  
|-----------------------|---------------------|-----------------|  
|`*`|`*?`|比對零或多次。|  
|`+`|`+?`|比對一或多次。|  
|`?`|`??`|比對零或一次。|  
|`{` *n* `}`|`{` *n* `}?`|完全符合 *n* 時間。|  
|`{` *n* `,}`|`{` *n* `,}?`|符合至少 *n* 時間。|  
|`{` *n* `,` *m* `}`|`{` *n* `,` *m* `}?`|從符合 *n* 至*m*時間。|  
  
 將數量`n`和`m`都是整數常數。 數量詞通常是 Greedy (窮盡)。其會讓規則運算式引擎盡可能多地從每次出現的特定模式進行比對。 在量詞中加上 `?` 字元會使它 lazy (忽略優先)，造成規則運算式引擎比對的項目愈少愈好。 如需 greedy (匹配優先) 與 lazy (忽略優先) 量詞間差異的完整說明，請參閱本主題稍後的 [Greedy (匹配優先) 與 Lazy (忽略優先) 量詞](#Greedy)一節。  
  
> [!IMPORTANT]
>  巢狀數量詞 (如規則運算式模式 `(a*)*` 所做) 會增加規則運算式引擎必須執行的比較次數，如輸入字串中的字元數指數函數一樣。 如需有關此行為，以及其因應措施的詳細資訊，請參閱[回溯](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)。  
  
## <a name="regular-expression-quantifiers"></a>規則運算式量詞  
 下列章節會列出 .NET 規則運算式支援的數量詞。  
  
> [!NOTE]
>  如果 *，+，？，{，與} 字元在規則運算式模式中遇到，規則運算式引擎會將它們解譯為數量詞或組件的數量詞的建構除非它們包含在[字元類別](../../../docs/standard/base-types/character-classes-in-regular-expressions.md)。 若要在字元類別外將這些字元解譯為常值字元，您必須在它們前面加上反斜線以逸出字元。 例如，字串`\*`在規則運算式模式會解譯為常值的星號 ("\*") 字元。  
  
### <a name="match-zero-or-more-times-"></a>比對零或多次：*  
 `*` 數量詞會比對前置元素零次或多次。 它相當於`{0,}`數量詞。 `*`是窮盡數量詞，其延遲的對等項目是`*?`。  
  
 下例會示範此規則運算式。 在輸入字串的九個數字中，有五個符合模式，四個 (`95`、`929`、`9129` 和 `9919`) 不符合。  
  
 [!code-csharp[RegularExpressions.Quantifiers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#1)]  
  
 規則運算式模式的定義如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`\b`|從字緣開始。|  
|`91*`|比對後面接著零或多個 "1" 字元的 "9"。|  
|`9*`|比對零或多個 "9" 字元。|  
|`\b`|在字邊界結束。|  
  
### <a name="match-one-or-more-times-"></a>比對一或多次：+  
 `+`數量詞比對前面的項目一次以上。 它相當於`{1,}`。 `+`是窮盡數量詞，其延遲的對等項目是`+?`。  
  
 例如，規則運算式 `\ban+\w*?\b` 會嘗試比對以字母 `a` 開頭、接著一或多個字母 `n` 的單字。 下例會示範此規則運算式。 規則運算式會比對出單字 `an`、`annual`、`announcement` 和 `antique`，而不會比對出 `autumn` 和 `all`。  
  
 [!code-csharp[RegularExpressions.Quantifiers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#2)]  
  
 規則運算式模式的定義如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`\b`|從字緣開始。|  
|`an+`|比對 "a" 接著一或多個 "n" 字元。|  
|`\w*?`|比對單字字元零或多次，但次數愈少愈好。|  
|`\b`|在字邊界結束。|  
  
### <a name="match-zero-or-one-time-"></a>比對零或一次：?  
 `?`數量詞符合上述的零個或一個項目時間。 它相當於`{0,1}`。 `?`是窮盡數量詞，其延遲的對等項目是`??`。  
  
 例如，規則運算式 `\ban?\b` 會嘗試比對以字母 `a` 開頭、接著零或一個字母 `n` 的單字。 換言之，它會嘗試比對單字 `a` 和 `an`。 下例會示範此規則運算式。  
  
 [!code-csharp[RegularExpressions.Quantifiers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#3)]
 [!code-vb[RegularExpressions.Quantifiers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#3)]  
  
 規則運算式模式的定義如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`\b`|從字緣開始。|  
|`an?`|比對 "a" 接著零或一個 "n" 字元。|  
|`\b`|在字邊界結束。|  
  
### <a name="match-exactly-n-times-n"></a>確實比對 n 次：{n}  
 `{`  *n*  `}`數量詞比對前面的項目剛好 *n* 次，其中 *n* 是任何整數。 `{`*n*`}`是窮盡數量詞，其延遲的對等項目是`{`  *n*  `}?`。  
  
 例如，規則運算式 `\b\d+\,\d{3}\b` 會嘗試比對出字邊界、接著一或多個十進位數字、再接三個十進位數字、接著字邊界的項目。 下例會示範此規則運算式。  
  
 [!code-csharp[RegularExpressions.Quantifiers#4](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#4)]
 [!code-vb[RegularExpressions.Quantifiers#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#4)]  
  
 規則運算式模式的定義如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`\b`|從字緣開始。|  
|`\d+`|比對一個或多個十進位數字。|  
|`\,`|比對逗號字元。|  
|`\d{3}`|比對三個十進位數字。|  
|`\b`|在字邊界結束。|  
  
### <a name="match-at-least-n-times-n"></a>至少比對 n 次：{n,}  
 `{`  *n*  `,}`數量詞比對前面的項目至少 *n* 次，其中 *n* 是任何整數。 `{`*n*`,}`是窮盡數量詞，其延遲的對等項目是`{`  *n*  `}?`。  
  
 例如，規則運算式 `\b\d{2,}\b\D+` 會嘗試比對出字邊界、接著至少兩個數字、再接字邊界、然後非數字字元的項目。 下例會示範此規則運算式。 規則運算式無法比對片語`"7 days"`因為它包含只在一個十進位數字，但已成功比對片語`"10 weeks and 300 years"`。  
  
 [!code-csharp[RegularExpressions.Quantifiers#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#5)]
 [!code-vb[RegularExpressions.Quantifiers#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#5)]  
  
 規則運算式模式的定義如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`\b`|從字緣開始。|  
|`\d{2,}`|至少比對兩個十進位數字。|  
|`\b`|比對字邊界。|  
|`\D+`|至少比對一個非十進位數字。|  
  
### <a name="match-between-n-and-m-times-nm"></a>比對 n 到 m 次：{n,m}  
 `{`  *n*  `,` *m* `}`數量詞比對前面的項目至少 *n* 次數，但不是能超過*m*次，其中 *n* 和*m*都是整數。 `{`*n*`,`*m* `}`是窮盡數量詞，其延遲的對等項目是`{`  *n*  `,` *m*`}?`。  
  
 在下例中，規則運算式 `(00\s){2,4}` 會嘗試比對 2 至 4 次兩個數字零後接空格的項目。 請注意，輸入字串有此模式的最後部分出現了五次，而非上限四次。 但只有這個子字串的初始部分 (最多到空格和第五對零) 符合規則運算式模式。  
  
 [!code-csharp[RegularExpressions.Quantifiers#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#6)]
 [!code-vb[RegularExpressions.Quantifiers#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#6)]  
  
### <a name="match-zero-or-more-times-lazy-match-"></a>比對零或多次 (Lazy (忽略優先) 比對)：*?  
 `*?`數量詞比對前面的項目零次或多次，但越少次越好。 它是延遲的窮盡數量詞的對應項目`*`。  
  
 在下例中，規則運算式 `\b\w*?oo\w*?\b` 會比對包含字串 `oo` 的所有文字。  
  
 [!code-csharp[RegularExpressions.Quantifiers#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#7)]
 [!code-vb[RegularExpressions.Quantifiers#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#7)]  
  
 規則運算式模式的定義如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`\b`|從字緣開始。|  
|`\w*?`|比對零或多個單字字元，但字元愈少愈好。|  
|`oo`|比對字串 "oo"。|  
|`\w*?`|比對零或多個單字字元，但字元愈少愈好。|  
|`\b`|在字邊界結束。|  
  
### <a name="match-one-or-more-times-lazy-match-"></a>比對零或多次 (Lazy (忽略優先) 比對)：+?  
 `+?`數量詞比對前面的項目一或多次，但越少次越好。 它是延遲的窮盡數量詞的對應項目`+`。  
  
 例如，規則運算式 `\b\w+?\b` 會比對一或多個以字邊界分隔的字元。 下例會示範此規則運算式。  
  
 [!code-csharp[RegularExpressions.Quantifiers#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#8)]
 [!code-vb[RegularExpressions.Quantifiers#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#8)]  
  
### <a name="match-zero-or-one-time-lazy-match-"></a>比對零或一次 (Lazy (忽略優先) 比對)：??  
 `??`數量詞符合上述的零個或一個項目的時間，但越少次越好。 它是延遲的窮盡數量詞的對應項目`?`。  
  
 例如，規則運算式 `^\s*(System.)??Console.Write(Line)??\(??` 會嘗試比對字串 "Console.Write" 或 "Console.WriteLine"。 字串也可以在 "Console" 前包含 "System."， 後面也可以是左括號。 字串必須位在行的開頭，雖然前面可以是空格。 下例會示範此規則運算式。  
  
 [!code-csharp[RegularExpressions.Quantifiers#9](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#9)]
 [!code-vb[RegularExpressions.Quantifiers#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#9)]  
  
 規則運算式模式的定義如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`^`|比對輸入資料流的開頭。|  
|`\s*`|比對零個以上的空白字元。|  
|`(System.)??`|比對出現零或一次的字串 "System."。|  
|`Console.Write`|比對字串 "Console.Write"。|  
|`(Line)??`|比對出現零或一次的字串 "Line"。|  
|`\(??`|比對出現零或一次的左括號。|  
  
### <a name="match-exactly-n-times-lazy-match-n"></a>確實比對 n 次 (Lazy (忽略優先) 比對)：{n}?  
 `{`  *n*  `}?`數量詞比對前面的項目剛好`n`次，其中 *n* 是任何整數。 它是延遲的窮盡數量詞的對應項目`{`  *n*  `}+`。  
  
 下例會使用規則運算式 `\b(\w{3,}?\.){2}?\w{3,}?\b` 來識別網站位址。 請注意它會比對 "www.microsoft.com" 和 "msdn.microsoft.com"，但不比對 "mywebsite" 或 "mycompany.com"。  
  
 [!code-csharp[RegularExpressions.Quantifiers#10](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#10)]
 [!code-vb[RegularExpressions.Quantifiers#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#10)]  
  
 規則運算式模式的定義如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`\b`|從字緣開始。|  
|`(\w{3,}?\.)`|比對至少 3 個單字字元，但字元愈少愈好，後面接著點或句號字元。 這是第一個擷取群組。|  
|`(\w{3,}?\.){2}?`|比對兩次第一個群組中的模式，但次數愈少愈好。|  
|`\b`|結束字邊界比對。|  
  
### <a name="match-at-least-n-times-lazy-match-n"></a>至少比對 n 次 (Lazy (忽略優先) 比對)：{n,}?  
 `{`  *n*  `,}?`數量詞比對前面的項目至少`n`次，其中 *n* 是任何整數，但越少次越可能的。 它是延遲的窮盡數量詞的對應項目`{`  *n*  `,}`。  
  
 請參閱範例的`{`  *n*  `}?`數量詞，如需圖例上一節。 在此範例中的規則運算式會使用`{`  *n*  `,}`數量詞比對後面接句號的至少三個字元的字串。  
  
### <a name="match-between-n-and-m-times-lazy-match-nm"></a>比對 n 到 m 次 (Lazy (忽略優先) 比對)：{n,m}?  
 `{`  *n*  `,` *m* `}?`數量詞比對前面的項目之間`n`和`m`次，其中*n* 和*m*都是整數，但越少次越好。 它是延遲的窮盡數量詞的對應項目`{`  *n*  `,` *m*`}`。  
  
 在下例中，規則運算式 `\b[A-Z](\w*\s+){1,10}?[.!?]` 會比對包含一到十個單字的句子。 它會比對輸入字串中的所有句子，除了包含 18 個字的句子。  
  
 [!code-csharp[RegularExpressions.Quantifiers#12](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#12)]
 [!code-vb[RegularExpressions.Quantifiers#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#12)]  
  
 規則運算式模式的定義如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`\b`|從字緣開始。|  
|`[A-Z]`|比對從 A 到 Z 的大寫字元。|  
|`(\w*\s+)`|比對零或多個後接一或多個空白字元的單字字元。 這是第一個擷取群組。|  
|`{1,10}?`|比對 1 到 10 次上一個模式，但次數愈少愈好。|  
|`[.!?]`|比對任一標點符號字元 "."、"!" 或 "?"。|  
  
<a name="Greedy"></a>   
## <a name="greedy-and-lazy-quantifiers"></a>Greedy (匹配優先) 與 Lazy (忽略優先) 量詞  
 數個量詞有兩種版本︰  
  
-   Greedy (窮盡) 版本。  
  
     Greedy (窮盡) 數量詞會嘗試盡可能多次比對項目。  
  
-   非窮盡 （或延遲） 的版本。  
  
     非 Greedy (窮盡) 數量詞會嘗試盡可能少比對項目。 您可以將窮盡數量詞 lazy 數量詞變成只要新增`?`。  
  
 請考慮要擷取數字字串末四碼的簡單規則運算式，例如信用卡號碼。 使用規則運算式的新版`*`窮盡數量詞為`\b.*([0-9]{4})\b`。 但若字串包含兩組數字，這個規則運算式只會比對第二組數字的末四碼，如下列範例所示。  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#1)]  
  
 規則運算式無法比對的第一個號碼，因為`*`數量詞嘗試比對上一個項目，盡可能在整個字串的次數，因此找到其比對字串的結尾。  
  
 這不是我們所要的結果。 相反地，您可以使用`*?`lazy 數量詞擷取這兩個編號，如下列範例所示的數字。  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#2)]  
  
 在大部分情況下，有 Greedy (窮盡) 和 Lazy (最少) 數量詞的規則運算式會傳回相同的結果。 它們最常傳回不同的結果時搭配萬用字元 (`.`) 中繼字元，它會比對任何字元。  
  
## <a name="quantifiers-and-empty-matches"></a>量詞和空白比對  
 數量詞`*`， `+`，和`{`  *n*  `,` *m* `}`和空後永遠不會重複其延遲的對應項目比對時已找到擷取的最小數目。 當可能群組擷取的最大數目是無限或接近無限時，此規則可防止數量詞在碰到空白子運算式比對時進入無限迴圈。  
  
 例如，下列程式碼顯示要呼叫的結果<xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType>方法與規則運算式模式`(a?)*`，會比對零個或一個"a"字元零次以上。 請注意，單一擷取群組會擷取每個"a"做為以及<xref:System.String.Empty?displayProperty=nameWithType>，但沒有第二個空白相符，因為第一個空白的相符項目會造成停止重複限定詞。  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch1.vb#1)]  
  
 若要查看定義擷取數目上下限的擷取群組和定義固定擷取數目的擷取群組之間的實際差異，請考慮規則運算式模式 `(a\1|(?(1)\1)){0,2}` 和 `(a\1|(?(1)\1)){2}`。 這兩個規則運算式都是由單一擷取群組組成，如下表所示加以定義。  
  
|模式|描述|  
|-------------|-----------------|  
|`(a\1`|比對 "a" 及第一個擷取的群組值...|  
|`&#124;(?(1)`|… 或測試第一個擷取的群組是否已定義。 (請注意，`(?(1)`建構不會定義的擷取群組。)|  
|`\1))`|如果第一個擷取的群組存在，即比對其值。 如果群組不存在，將符合的群組<xref:System.String.Empty?displayProperty=nameWithType>。|  
  
 第一個規則運算式嘗試比對這種模式零到兩次，第二個不多不少就兩次。 因為第一個模式達到其最小數目的其第一個擷取的擷取<xref:System.String.Empty?displayProperty=nameWithType>，永遠不會重複嘗試比對`a\1`;`{0,2}`數量詞允許空的相符項目中的最後一個反覆項目。 相反地，第二個規則運算式不比對 "a"，因為它會評估 `a\1` 第二次，反覆的下限 2，會強制引擎在空白比對後重複。  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch4.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch4.vb#2)]  
  
## <a name="see-also"></a>另請參閱  
 [規則運算式語言 - 快速參考](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 [回溯](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)
