---
title: 規則運算式中的回溯
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework regular expressions, backtracking
- alternative matching patterns
- optional matching patterns
- searching with regular expressions, backtracking
- pattern-matching with regular expressions, backtracking
- backtracking
- regular expressions [.NET Framework], backtracking
- strings [.NET Framework], regular expressions
- parsing text with regular expressions, backtracking
ms.assetid: 34df1152-0b22-4a1c-a76c-3c28c47b70d8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7caf42ee45f31e374bd2cbf7c700992130281ff0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="backtracking-in-regular-expressions"></a>規則運算式中的回溯
<a name="top"></a> 回溯 (Backtracking) 會在規則運算式模式包含選擇性的 [數量詞](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md) 或 [交替建構](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md)，且規則運算式引擎返回之前儲存的狀態繼續搜尋相符項目時發生。 回溯是規則運算式的核心能力，可讓運算式功能強大且靈活，並且比對非常複雜的模式。 但同時，這項強大功能需付出相當的代價。 回溯經常是影響規則運算式引擎之效能最重要的一項因素。 幸好開發人員能夠掌控規則運算式引擎的行為，以及其使用回溯的方式。 本主題將說明回溯運作的方式，以及如何進行控制。  
  
> [!NOTE]
>  大致而言，像是 .NET 規則運算式引擎這類非決定性有限自動化 (NFA) 引擎將設計有效率且快速之規則運算式的責任交給了開發人員。  
  
 此主題包括下列章節：  
  
-   [不進行回溯的線性比較](#linear_comparison_without_backtracking)  
  
-   [含有選擇性數量詞或交替建構的回溯](#backtracking_with_optional_quantifiers_or_alternation_constructs)  
  
-   [含有巢狀選擇性數量詞的回溯](#backtracking_with_nested_optional_quantifiers)  
  
-   [控制回溯](#controlling_backtracking)  
  
<a name="linear_comparison_without_backtracking"></a>   
## <a name="linear-comparison-without-backtracking"></a>不進行回溯的線性比較  
 如果規則運算式模式沒有選擇性數量詞或交替建構，則規則運算式引擎會以線性時間執行。 也就是說，規則運算式引擎比對模式中的第一個語言項目與輸入字串中的文字之後，會嘗試比對模式中的下一個語言項目與輸入字串中的下一個字元或字元群組。 這項作業會繼續進行，直到比對成功或失敗為止。 無論成功或失敗，規則運算式引擎都會在輸入字串中一次前進一個字元。  
  
 下列範例提供一個實例。 規則運算式 `e{2}\w\b` 會尋找兩個出現字母 "e" 的位置，這後面接著任何文字字元，然後再接著字邊界。  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking1.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking1.vb#1)]  
  
 雖然這個規則運算式包括數量詞 `{2}`，但仍然會以線性方式進行評估。 規則運算式引擎不會回溯，因為 `{2}` 不是選擇性的數量詞，它指定了確切的數字，而不是前面的子運算式必須比對的可變次數。 因此，規則運算式引擎會嘗試比對規則運算式模式與輸入字串，如下表所示。  
  
|作業|模式中的位置|字串中的位置|結果|  
|---------------|-------------------------|------------------------|------------|  
|1|e|"needing a reed" (索引 0)|沒有符合的結果。|  
|2|e|"eeding a reed" (索引 1)|可能符合的結果。|  
|3|e{2}|"eding a reed" (索引 2)|可能符合的結果。|  
|4|\w|"ding a reed" (索引 3)|可能符合的結果。|  
|5|\b|"ing a reed" (索引 4)|可能符合的結果失敗。|  
|6|e|"eding a reed" (索引 2)|可能符合的結果。|  
|7|e{2}|"ding a reed" (索引 3)|可能符合的結果失敗。|  
|8|e|"ding a reed" (索引 3)|比對會失敗。|  
|9|e|"ing a reed" (索引 4)|沒有符合的結果。|  
|10|e|"ng a reed" (索引 5)|沒有符合的結果。|  
|11|e|"g a reed" (索引 6)|沒有符合的結果。|  
|12|e|" a reed" (索引 7)|沒有符合的結果。|  
|13|e|"a reed" (索引 8)|沒有符合的結果。|  
|14|e|" reed" (索引 9)|沒有符合的結果。|  
|15|e|"a reed" (索引 10)|沒有符合的結果|  
|16|e|"eed" (索引 11)|可能符合的結果。|  
|17|e{2}|"ed" (索引 12)|可能符合的結果。|  
|18|\w|"d" (索引 13)|可能符合的結果。|  
|19|\b|"" (索引 14)|符合的結果。|  
  
 如果規則運算式模式未包含選擇性數量詞或交替建構，則比對規則運算式模式與輸入字串所需的比較次數上限，約相當於輸入字串中的字元數。 在這個案例中，規則運算式引擎會使用 19 項比較找出這 13 個字元字串中可能的相符項目。  換句話說，如果沒有選擇性數量詞或交替建構，規則運算式引擎就會以近似線性時間執行。  
  
 [回到頁首](#top)  
  
<a name="backtracking_with_optional_quantifiers_or_alternation_constructs"></a>   
## <a name="backtracking-with-optional-quantifiers-or-alternation-constructs"></a>含有選擇性數量詞或交替建構的回溯  
 當規則運算式包含選擇性數量詞或交替建構時，輸入字串的評估就不再是線性。 與 NFA 引擎比對的模式是由規則運算式中的語言項目所引導，而不是由輸入字串中要比對的字元引導。 因此，規則運算式引擎會嘗試完整比對選擇性或替代子運算式。 當規則運算式引擎前進到子運算式中的下一個語言項目且比對失敗時，它可能會捨棄成功比對的一部分，並且返回之前儲存的狀態，以便完整比對規則運算式與輸入字串。 這個返回之前儲存狀態尋找符合結果的程序，就稱為回溯 (Backtracking)。  
  
 例如，想想規則運算式模式 `.*(es)`，它會比對字元 "es" 與其前面的所有字元。 如下列範例中所示，如果輸入字串為 "Essential services are provided by regular expressions."，則模式會比對整個字串直到 (且包含) "expressions" 中的 "es" 為止。  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking2.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking2.vb#2)]  
  
 為了進行這項比對，規則運算式引擎會使用回溯，如下所示：  
  
-   它會比對 `.*` (其會比對零個、一個或多個任意字元) 與整個輸入字串。  
  
-   它會嘗試比對規則運算式模式中的 "e"。 不過，輸入字串沒有其他可供比對的字元。  
  
-   接著它會回溯至上一個成功的比對結果 "Essential services are provided by regular expressions"，並嘗試比對 "e" 與句尾的句號。 比對會失敗。  
  
-   然後它會繼續回溯至前一個成功的比對結果，一次一個字元，直到暫時相符的子字串為 "Essential services are provided by regular expr"。 然後運算式會比較模式中的 "e" 與 "expressions" 中的第二個 "e"，並且尋找符合的結果。  
  
-   接著再比較模式中的 "s" 與相符的 "e" 字元後面接著的 "s" ("expressions" 中的第一個 "s")。 比對將會成功。  
  
 當您使用回溯時，比對規則運算式模式與長度 55 個字元的輸入字串需要進行 67 次比較作業。 有趣的是，如果規則運算式模式包含鬆散 (Lazy) 數量詞 .`*?(es)`，則比對規則運算式會需要進行更多次比較。 在這個案例中，規則運算式引擎不是從字串結尾回溯至 "expressions" 中的 "r"，而是必須一路回溯至字串開頭才能找到相符的 "Es"，而這個過程需要進行 113 次比較。 通常如果規則運算式模式包含單一交替建構或單一選擇性數量詞，則比對模式所需的比較作業次數會超過輸入字串中字元數的兩倍。  
  
 [回到頁首](#top)  
  
<a name="backtracking_with_nested_optional_quantifiers"></a>   
## <a name="backtracking-with-nested-optional-quantifiers"></a>含有巢狀選擇性數量詞的回溯  
 如果模式包含大量交替建構、包括巢狀交替建構，或是最常見的巢狀選擇性數量詞，則比對規則運算式模式所需的比較作業次數可能大幅增加。 例如，規則運算式模式 `^(a+)+$` 的設計為比對包含一個或多個 "a" 字元的完整字串。 範例中提供了兩個長度相同的輸入字串，但只有第一個字串與模式相符。 <xref:System.Diagnostics.Stopwatch?displayProperty=nameWithType> 類別可用來判斷比對作業進行的時間。  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking3.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking3.vb#3)]  
  
 如範例的輸出所示，規則運算式引擎耗費約為識別比對字串的兩倍時間，才發現輸入字串與模式不相符。 這是因為失敗的比對永遠代表最糟的狀況。 規則運算式引擎必須先使用規則運算式依循所有可能的途徑來處理資料，才能得到比對失敗的結果，而巢狀括號會製造許多額外的途徑來處理資料。 規則運算式引擎會藉由執行下列操作得出第二個字串與模式不相符的結果：  
  
-   它會檢查是否位於字串開頭，然後比對字串中的前五個字元與 `a+`模式。 然後判斷字串中沒有額外的 "a" 字元群組。 最後測試是否到達字串結尾。 由於字串中剩下一個額外的字串，因此比對失敗。 這個失敗的比對需要經過 9 次比較。 規則運算式引擎還會儲存 "a" (以下稱為符合結果 1)、"aa" (符合結果 2)、"aaa" (符合結果 3) 和 "aaaa" (符合結果 4) 這些符合結果的狀態資訊。  
  
-   它會返回之前儲存的符合結果 4。 然後判斷出有一個額外的 "a" 字元要指派至額外的擷取群組。 最後測試是否到達字串結尾。 由於字串中剩下一個額外的字串，因此比對失敗。 這個失敗的比對需要經過 4 次比較。 到目前為止，總共執行了 13 次比較。  
  
-   它會返回之前儲存的符合結果 3。 然後判斷出有兩個額外的 "a" 字元要指派至額外的擷取群組。 然而，字串結尾測試失敗。 接著它會返回符合結果 3，並嘗試比對兩個額外的擷取群組中的這兩個額外的 "a" 字元。 字串結尾測試仍然失敗。 這些失敗的比對需要經過 12 次比較。 到目前為止，總共執行了 25 次比較。  
  
 輸入字串與規則運算式的比較會依照這種方式繼續進行，直到規則運算式引擎嘗試過所有可能的比對組合，然後得到沒有符合的結果這個結論。 由於巢狀數量詞的關係，這個比較是 O(2<sup>n</sup>) 或指數運算，其中 *n* 是輸入字串中的字元數。 這表示，在最糟的情況下，包含 30 個字元的輸入字串約需要進行 1,073,741,824 次比較，而包含 40 個字元的輸入字串約需要進行 1,099,511,627,776 次比較。 如果您使用這類長度甚至更長的字串，則規則運算式方法處理不符合規則運算式模式的輸入時，可能需要相當長的時間才能完成。  
  
 [回到頁首](#top)  
  
<a name="controlling_backtracking"></a>   
## <a name="controlling-backtracking"></a>控制回溯  
 回溯可讓您建立強大、靈活的規則運算式。 不過，如上一節所示，這些好處可能伴隨著令人敬謝不敏的低落效能。 為了避免大量回溯，當您具現化 <xref:System.Text.RegularExpressions.Regex> 物件或呼叫靜態規則運算式比對方法時，應該定義逾時間隔。 下一節將討論這個部分。 此外，.NET 支援三個規則運算式語言元素，可限制或隱藏回溯並支援複雜的規則運算式，而且對效能的影響微不足道：[非回溯子運算式](#Nonbacktracking)、[左合樣判斷提示](#Lookbehind)和[右合樣判斷提示](#Lookahead)。 如需各語言項目的詳細資訊，請參閱 [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)。  
  
<a name="Timeout"></a>   
### <a name="defining-a-time-out-interval"></a>定義逾時間隔  
 從 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]開始，您可以設定逾時值，表示規則運算式引擎開始搜尋單一符合項目到放棄嘗試並擲回 <xref:System.Text.RegularExpressions.RegexMatchTimeoutException> 例外狀況之前的最長間隔。 您可以提供執行個體規則運算式之 <xref:System.TimeSpan> 建構函式的 <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> 值，藉此指定逾時間隔。 此外，每一個靜態模式比對方法都有 <xref:System.TimeSpan> 參數的多載，可讓您指定逾時值。 根據預設，逾時間隔會設為 <xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout?displayProperty=nameWithType>，表示規則運算式引擎不會逾時。  
  
> [!IMPORTANT]
>  如果您的規則運算式倚賴回溯，建議您一定要設定逾時間隔。  
  
 <xref:System.Text.RegularExpressions.RegexMatchTimeoutException> 例外狀況表示規則運算式引擎在指定的逾時間隔內找不到相符項目，但不會指出擲回例外狀況的原因。 這個原因可能是大量回溯，不過也有可能是對於擲回例外狀況當時的系統負載而言，設定的逾時間隔太低。 當您處理例外狀況時，可以選擇中放棄一步比對輸入字串，或增加逾時間隔並重試比對作業。  
  
 例如，下列程式碼會呼叫 <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> 建構函式來具現化逾時值為一秒的 <xref:System.Text.RegularExpressions.Regex> 物件。 規則運算式模式 `(a+)+$`會在行尾比對一個或多個 "a" 字元的一個或多個序列，並且受限於大量回溯。 如果擲回 <xref:System.Text.RegularExpressions.RegexMatchTimeoutException> ，則範例會將逾時值增加至最大間隔三秒。 在這個間隔之後，它就會放棄嘗試比對模式。  
  
 [!code-csharp[System.Text.RegularExpressions.Regex.ctor#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.text.regularexpressions.regex.ctor/cs/ctor1.cs#1)]
 [!code-vb[System.Text.RegularExpressions.Regex.ctor#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.text.regularexpressions.regex.ctor/vb/ctor1.vb#1)]  
  
<a name="Nonbacktracking"></a>   
### <a name="nonbacktracking-subexpression"></a>非回溯子運算式  
 `(?>` *子運算式*`)` 語言項目會隱藏子運算式中的回溯。 對於避免發生與比對失敗相關的效能問題相當有用。  
  
 下列範例說明隱藏回溯如何在使用巢狀數量詞時改善效能。 它會測量規則運算式引擎判斷出輸入字串與兩個規則運算式不相符所需的時間。 第一個規則運算式會使用回溯嘗試比對包含出現一次或多次的一個或多個十六進位數字的字串，後面接著一個冒號，再接著一個或多個十六進位數字，最後接著兩個冒號。 第二個規則運算式與第一個完全相同，但會停用回溯。 如範例的輸出所示，停用回溯使效能大幅提升。  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking4.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking4.vb#4)]  
  
<a name="Lookbehind"></a>   
### <a name="lookbehind-assertions"></a>左合樣判斷提示  
 .NET 包含兩個語言元素：`(?<=`*subexpression*`)` 和 `(?<!`*subexpression*`)`，這兩者會比對輸入字串中的前一個或多個字元。 這兩個語言項目都是零寬度判斷提示，也就是說，它們會判斷緊接著目前字元前面的字元是否可由 *子運算式*比對，而不需前進或回溯。  
  
 `(?<=` *子運算式* `)` 是左合樣判斷提示，也就是說，目前位置前面的字元必須符合 *子運算式*。 `(?<!`*子運算式*`)` 是左不合樣判斷提示，也就是說，目前位置前面的字元必須不符合 *子運算式*。 當 *子運算式* 為前一個子運算式的子集時，左合樣和左不合樣判斷提示最為實用。  
  
 下列範例使用兩個同等的規則運算式模式，來驗證電子郵件地址中的使用者名稱。 第一個模式因為進行大量回溯，而受限於低落的效能。 第二個模式修改了第一個規則運算式，將巢狀數量詞取代為左合樣判斷提示。 範例的輸入顯示 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> 方法的執行時間。  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking5.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking5.vb#5)]  
  
 第一個規則運算式模式 `^[0-9A-Z]([-.\w]*[0-9A-Z])*@`的定義如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`^`|從字串的開頭開始比對。|  
|`[0-9A-Z]`|比對英數字元。 這項比較不區分大小寫，因為 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> 方法是使用 <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> 選項呼叫。|  
|`[-.\w]*`|比對出現零次、一次或多次的連字號、句號或文字字元。|  
|`[0-9A-Z]`|比對英數字元。|  
|`([-.\w]*[0-9A-Z])*`|比對出現零次或多次的零個或多個連字號、句號或文字字元組合，後面接著英數字元。 這是第一個擷取群組。|  
|`@`|比對 "@" 記號。|  
  
 第二個規則運算式模式 `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])@`使用左合樣判斷提示。 其定義方式如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`^`|從字串的開頭開始比對。|  
|`[0-9A-Z]`|比對英數字元。 這項比較不區分大小寫，因為 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> 方法是使用 <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> 選項呼叫。|  
|`[-.\w]*`|比對出現零次或多次的連字號、句號或文字字元。|  
|`(?<=[0-9A-Z])`|如果是英數字，則向左合樣最後一個符合的字元並繼續比對。 請注意，英數字元是由句號、連字號和所有文字字元組成之集合的子集。|  
|`@`|比對 "@" 記號。|  
  
<a name="Lookahead"></a>   
### <a name="lookahead-assertions"></a>右合樣判斷提示  
 .NET 包含兩個語言元素：`(?=`*subexpression*`)` 和 `(?!`*subexpression*`)`，這兩者會比對輸入字串中的下一個或多個字元。 這兩個語言項目都是零寬度判斷提示，也就是說，它們會判斷緊接著目前字元後面的字元是否可由 *子運算式*比對，而不需前進或回溯。  
  
 `(?=` *子運算式* `)` 是右合樣判斷提示，也就是說，目前位置後面的字元必須符合 *子運算式*。 `(?!`*子運算式*`)` 是右不合樣判斷提示，也就是說，目前位置後面的字元必須不符合 *子運算式*。 當 *子運算式* 為下一個子運算式的子集時，右合樣和右不合樣判斷提示最為實用。  
  
 下列範例使用兩個同等的規則運算式模式，這兩個模式會驗證完整類型名稱。 第一個模式因為進行大量回溯，而受限於低落的效能。 第二個修改了第一個規則運算式，將巢狀數量詞取代為右合樣判斷提示。 範例的輸入顯示 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> 方法的執行時間。  
  
 [!code-csharp[Conceptual.RegularExpressions.Backtracking#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/cs/backtracking6.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.Backtracking#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.backtracking/vb/backtracking6.vb#6)]  
  
 第一個規則運算式模式 `^(([A-Z]\w*)+\.)*[A-Z]\w*$`的定義如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`^`|從字串的開頭開始比對。|  
|`([A-Z]\w*)+\.`|比對後面接著零個或多個文字字元的字母字元 (A-Z) 一次或多次，後面接著句號。 這項比較不區分大小寫，因為 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> 方法是使用 <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> 選項呼叫。|  
|`(([A-Z]\w*)+\.)*`|比對上一個模式零次或多次。|  
|`[A-Z]\w*`|比對後面接著零個或多個文字字元的字母字元。|  
|`$`|在輸入字串結尾結束比對。|  
  
 第二個規則運算式模式 `^((?=[A-Z])\w+\.)*[A-Z]\w*$`使用右合樣判斷提示。 其定義方式如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`^`|從字串的開頭開始比對。|  
|`(?=[A-Z])`|如果是字母 (A-Z)，則向右合樣至第一個字元並繼續比對。 這項比較不區分大小寫，因為 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> 方法是使用 <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> 選項呼叫。|  
|`\w+\.`|比對後面接著句號的零個或多個文字字元。|  
|`((?=[A-Z])\w+\.)*`|比對後面接句號的一個或多個文字字元這個模式一次或多次。 初始文字字元必須是字母。|  
|`[A-Z]\w*`|比對後面接著零個或多個文字字元的字母字元。|  
|`$`|在輸入字串結尾結束比對。|  
  
 [回到頁首](#top)  
  
## <a name="see-also"></a>請參閱  
 [.NET 規則運算式](../../../docs/standard/base-types/regular-expressions.md)  
 [規則運算式語言 - 快速參考](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 [數量詞](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)  
 [交替建構](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md)  
 [群組建構](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)
