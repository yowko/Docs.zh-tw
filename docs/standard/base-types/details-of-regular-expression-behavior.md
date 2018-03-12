---
title: "規則運算式行為的詳細資訊"
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
- regular expressions, behavior
- .NET Framework regular expressions, behavior
ms.assetid: 0ee1a6b8-caac-41d2-917f-d35570021b10
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5b471cd8e934880fc8095fbad68b460174ec338c
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2018
---
# <a name="details-of-regular-expression-behavior"></a>規則運算式行為的詳細資訊
.NET Framework 規則運算式引擎是回溯規則運算式比對器，它結合了傳統的非決定性有限自動化 (NFA) 引擎，例如 Perl、Python、Emacs 和 Tcl 所使用的引擎。 這使得它與較快速、但限制較多的純規則運算式決定性有限自動化 (DFA) 引擎有所區別，例如 awk、egrep 或 lex 中的引擎。 這也和標準的但較緩慢的 POSIX NFA 有差異。 下節描述這三種規則運算式引擎，並說明為何要在 .NET Framework 中使用傳統 NFA 引擎來實作規則運算式。  
  
## <a name="benefits-of-the-nfa-engine"></a>NFA 引擎的優點  
 當 DFA 引擎執行模式比對時，其處理順序是由輸入字串所驅動。 引擎會從輸入字串的開頭開始執行，並循序地繼續判斷下一個字元是否符合規則運算式模式。 它們可以保證比對可能最長的字串。 因為 DFA 引擎絕不會測試相同的字元兩次，所以不支援回溯。 但因為 DFA 引擎只包含有限狀態，它不能以反向參考比對模式，並且因為它不建構明確的展開，所以不能擷取子運算式。  
  
 和 DFA 引擎不同，傳統 NFA 引擎在執行模式比對時，其處理順序是由規則運算式模式所驅動。 在處理某特定 language 元素時，引擎會使用 Greedy (窮盡) 比對，亦即盡可能比對輸入字串的最多內容。 但是，它也會在成功比對子運算式之後儲存其狀態。 如果比對最終失敗，此引擎可以回到儲存的狀態，以便嘗試其他比對。 放棄成功的子運算式比對，以便還能比對規則運算式中後續的語言元素，這個程序稱為「回溯」。 NFA 引擎會使用回溯依特定順序測試規則運算式的所有可能展開，並接受第一個符合項目。 因為傳統 NFA 引擎會為成功的比對建構規則運算式的特定展開，所以可以擷取子運算式符合項目和比對的反向參考。 但因為傳統 NFA 會回溯，所以可多次造訪相同的狀態，如果此狀態是經由不同的路徑到達。 結果最壞的情況是，它可以指數方式緩慢執行。 因為傳統 NFA 引擎接受找到的第一個符合項目，所以也可能發現不了其他 (可能是更長的) 符合項目。  
  
 POSIX NFA 引擎很像傳統 NFA 引擎，只是它們會繼續回溯直到能夠保證已經找到最長的可能符合項目。 結果，POSIX NFA 引擎比傳統 NFA 引擎更緩慢，而且當您使用 POSIX NFA 引擎時，您不能變更回溯搜尋的順序，讓較短的符合項目優先於較長的符合項目。  
  
 程式設計人員偏愛傳統 NFA 引擎，因為它們比 DFA 或 POSIX NFA 引擎更能夠掌控字串比對。 雖然最壞的情況是它們可能執行緩慢，但您可以使用減低模稜兩可並限制回溯的模式，操縱它們以線性或多項式時間尋找符合項目。 換言之，雖然 NFA 引擎是以效能換取功效和彈性，但是在大多數情況下，如果規則運算式撰寫得宜並可避免回溯指數衰減效能的話，它們所提供的效能還不錯。  
  
> [!NOTE]
>  如需大量回溯所造成效能影響的詳細資訊，以及撰寫規則運算式來解決問題的方式，請參閱[回溯](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)。  
  
## <a name="net-framework-engine-capabilities"></a>.NET framework 引擎功能  
 為利用傳統 NFA 引擎的優點，.NET Framework 規則運算式引擎包含了完整的建構集合，讓程式設計人員可以操縱回溯引擎。 這些建構可用於更快速尋找符合項目，或讓特定展開優先於其他展開。  
  
 .NET Framework 規則運算式引擎包含下列其他功能：  
  
-   Lazy (最少) 數量詞：`??`、`*?`、`+?`、`{`*n*`,`*m*`}?`。 這些建構告訴回溯引擎要先搜尋最小數目的重複。 相反地，一般 Greedy (窮盡) 數量詞會先嘗試比對最多的重複 項目。 下例會說明兩者間的差異。 規則運算式會比對以數字結尾的句子，以及用來擷取該數字的擷取群組。 規則運算式 `.+(\d+)\.` 包含 Greedy (窮盡) 數量詞 `.+`，這導致規則運算式引擎只會擷取數字的最後一個位數。 相反地，規則運算式 `.+?(\d+)\.` 包含 Lazy (最少) 數量詞 `.+?`，這導致規則運算式引擎會擷取整個數字。  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lazy1.cs#1)]
     [!code-vb[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lazy1.vb#1)]  
  
     此規則運算式的 Greedy (窮盡) 和 Lazy (最少) 版本定義如下表所示。  
  
    |模式|描述|  
    |-------------|-----------------|  
    |`.+` (Greedy (窮盡) 數量詞)|比對至少出現一次的任何字元。 這會導致規則運算式引擎比對整個字串，然後視需要進行回溯，以比對模式的其餘部分。|  
    |`.+?` (Lazy (最少) 數量詞)|出現的任何字元至少比對一次，但比對愈少愈好。|  
    |`(\d+)`|比對至少一個數值字元，並將它指派給第一個擷取群組。|  
    |`\.`|比對句點。|  
  
     如需 Lazy (最少) 數量詞的詳細資訊，請參閱[數量詞](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)。  
  
-   右合樣︰`(?=`*subexpression*`)`。 此功能允許回溯引擎在比對子運算式之後返回到文字的相同地方。 這對自相同位置開始驗證多個模式，以全面搜尋文字，很有用處。 它也可以讓引擎驗證子字串是否存在於符合項目的結尾，而不需在相符的文字中包含該子字串。 下例使用右合樣在句子中擷取後面未接標點符號的文字。  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead1.cs#2)]
     [!code-vb[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead1.vb#2)]  
  
     規則運算式 `\b[A-Z]+\b(?=\P{P})` 的定義如下表所示。  
  
    |模式|描述|  
    |-------------|-----------------|  
    |`\b`|開始字緣比對。|  
    |`[A-Z]+`|比對任何字母字元一或多次。 因為 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> 方法會使用 <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> 選項來呼叫，所以，比較不會區分大小寫。|  
    |`\b`|結束字緣比對。|  
    |`(?=\P{P})`|向右合樣以判斷下一個字元是否為標點符號。 如果不是，則比對成功。|  
  
     如需右合樣判斷提示的詳細資訊，請參閱[群組建構](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)。  
  
-   右不合樣︰`(?!`*subexpression*`)`。 此功能加入了只有子運算式無法比對時才會比對運算式的功能。 這在刪除搜尋時特別有功用，因為提供應該排除情況的運算式通常會比指供必須包含情況的運算式簡單。 例如，針對開頭不是 "non" 的單字撰寫運算式很困難。 下例使用右不合樣進行排除。  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead2.cs#3)]
     [!code-vb[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead2.vb#3)]  
  
     規則運算式模式 `\b(?!non)\w+\b` 的定義如下表所示。  
  
    |模式|描述|  
    |-------------|-----------------|  
    |`\b`|開始字緣比對。|  
    |`(?!non)`|向右合樣以確定目前的字串不是以 "non" 開頭。 如果是，則比對失敗。|  
    |`(\w+)`|比對一個或多個文字字元。|  
    |`\b`|結束字緣比對。|  
  
     如需右不合樣判斷提示的詳細資訊，請參閱[群組建構](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)。  
  
-   條件式評估︰`(?(`*expression*`)`*yes*`|`*no*`)` and `(?(`*name*`)`*yes*`|`*no*`)`，其中 *expression* 是要比對的子運算式，*name* 是擷取群組的名稱，*yes* 是要比對 *expression* 是否相符或 *name* 是否為有效且非空白擷取群組的字串，而 *no* 是要比對 *expression* 是否不相符或 *name* 是否不為有效且非空白擷取群組的子運算式。 此功能可讓引擎根據前一個子運算式比對的結果或零寬度判斷提示的結果，使用一個以上的替代模式進行搜尋。 這允許更強大的反向參考形式，例如允許根據前一個子運算式是否相符來比對子運算式。 下例中的規則運算式會比對同時可供公用和內部使用的段落。 僅供內部使用的段落會以 `<PRIVATE>` 標記開頭。 規則運算式模式 `^(?<Pvt>\<PRIVATE\>\s)?(?(Pvt)((\w+\p{P}?\s)+)|((\w+\p{P}?\s)+))\r?$` 會使用條件式評估，將可供公用和內部使用的段落內容指派給個別的擷取群組。 再以不同的方式來處理這些段落。  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/conditional1.cs#4)]
     [!code-vb[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/conditional1.vb#4)]  
  
     規則運算式模式的定義如下表所示。  
  
    |模式|描述|  
    |-------------|-----------------|  
    |`^`|在一行的開頭開始比對。|  
    |`(?<Pvt>\<PRIVATE\>\s)?`|比對出現零次或一次且後面接著空白字元的字串 `<PRIVATE>`。 將相符項目指派給名為 `Pvt` 的擷取群組。|  
    |`(?(Pvt)((\w+\p{P}?\s)+)`|如果 `Pvt` 擷取群組存在，則比對出現一或多次的一或多個單字字元，且該字元後面接著零或一個標點分隔符號和一個空白字元。 將子字串指派給第一個擷取群組。|  
    |<code>&#124;((\w+\p{P}?\s)+))<code>|如果 `Pvt` 擷取群組不存在，則比對出現一或多次的一或多個單字字元，且該字元後面接著零或一個標點分隔符號和一個空白字元。 將子字串指派給第三個擷取群組。|  
    |`\r?$`|比對行尾或字串結尾。|  
  
     如需條件式評估的詳細資訊，請參閱[替代建構](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md)。  
  
-   平衡群組定義︰`(?<`*name1*`-`*name2*`>` *subexpression*`)`。 此功能可讓規則運算式引擎追蹤巢狀建構，例如括號或左右中括弧。 如需範例，請參閱[群組建構](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)。  
  
-   非回溯子運算式 (也稱為 Greedy (窮盡) 子運算式)：`(?>`*subexpression*`)`。 此功能可讓回溯引擎保證子運算式只比對為該子運算式找到的第一個相符項目，就好像運算式的執行不受其包含運算式的影響。 如果不使用此建構，較大型運算式中的回溯搜尋可以變更子運算式的行為。 例如，規則運算式 `(a+)\w` 會比對一或多個 "a" 字元，以及緊接在 "a" 字元序列後面的單字字元，並將 "a" 字元序列指派給第一個擷取群組。但是，如果輸入字串的最後一個字元也是 "a"，則以 `\w` language 元素比對，且不包含在擷取的群組中。  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking2.vb#7)]  
  
     規則運算式 `((?>a+))\w` 可防止此行為發生。 因為不需要回溯，所有連續的 "a" 字元便已相符，所以第一個擷取群組會包含所有連續的 "a" 字元。 如果 "a" 字元後面未再接著至少一個 "a" 以外的字元，則比對失敗。  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking1.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking1.vb#8)]  
  
     如需非回溯子運算式的詳細資訊，請參閱[群組建構](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)。  
  
-   從右至左比對，將 <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> 選項提供給 <xref:System.Text.RegularExpressions.Regex> 類別建構函式或靜態執行個體比對方法，即可指定此種比對。 當從右至左搜尋取代從左至右搜尋時，或在從右邊部分 (而非自左邊) 開始比對模式較有效率的情況中，這項功能很有用處。 如下例所示，使用由右至左比對會變更 Greedy (窮盡) 數量詞的行為。 此範例會搜尋兩次以數字結尾的句子。 使用 Greedy (窮盡) 數量詞 `+` 的由左至右搜尋，會比對句子中的六個數字其中一個，而由右至左搜尋會比對全部六個數字。 如需規則運算式模式的說明，請參閱本節前文說明 lazy (忽略優先) 量詞的範例。  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/rtl1.cs#6)]
     [!code-vb[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/rtl1.vb#6)]  
  
     如需從右至左比對的詳細資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)。  
  
-   左合樣和左不合樣：`(?<=`*subexpression*`)` 適用於左合樣，而 `(?<!`*subexpression*`)` 適用於左不合樣。 此功能類似於本主題前文中所討論的向右合樣。 因為規則運算式引擎允許完整的由右至左比對，規則運算式允許無限制的向左合樣。 當巢狀子運算式為外部運算式的超集時，左合樣和左不合樣也可以用來避免產生巢狀數量詞。 具有此種巢狀數量詞的規則運算式通常效能不佳。 例如，下例會驗證字串是否以英數字元開頭和結尾，以及字串中的任何其他字元是否為較大子集之一。 它會構成用來驗證電子郵件地址之規則運算式的一部分；如需詳細資訊，請參閱[如何：確認字串是否為有效的電子郵件格式](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md)。  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookbehind1.cs#5)]
     [!code-vb[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookbehind1.vb#5)]  
  
     規則運算式 `^[A-Z0-9]([-!#$%&'.*+/=?^`{}|~\w])*(?<=[A-Z0-9])$` 的定義如下表所示。  
  
    |模式|描述|  
    |-------------|-----------------|  
    |`^`|從字串的開頭開始比對。|  
    |`[A-Z0-9]`|比對任何數值或英數字元。 (此比較不區分大小寫。)|  
    |<code>([-!#$%&'.*+/=?^\`{}&#124;~\w])*<code>|比對出現零或多次的任何文字字元，或下列任一個字元：-、!、#、$、%、&、'、.、*、+、/、=、?、^、\`、{、}、&#124; 或 ~。|  
    |`(?<=[A-Z0-9])`|向左合樣前一個字元，而該字元必須是數值或英數字元。 (此比較不區分大小寫。)|  
    |`$`|在字串的結尾結束比對。|  
  
     如需左合樣及左不合樣的詳細資訊，請參閱[群組建構](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[回溯](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)|提供規則運算式回溯如何擴展以尋找替代符合項目的相關資訊。|  
|[編譯及重複使用](../../../docs/standard/base-types/compilation-and-reuse-in-regular-expressions.md)|提供編譯和重複使用規則運算式以提升效能的相關資訊。|  
|[執行緒安全](../../../docs/standard/base-types/thread-safety-in-regular-expressions.md)|提供規則運算式執行緒安全的相關資訊，並說明何時應該同步處理規則運算式物件的存取。|  
|[.NET Framework 規則運算式](../../../docs/standard/base-types/regular-expressions.md)|提供規則運算式的程式設計語言方面的概觀。|  
|[規則運算式物件模型](../../../docs/standard/base-types/the-regular-expression-object-model.md)|提供說明規則運算式類別使用方式的資訊和程式碼範例。|  
|[規則運算式範例](../../../docs/standard/base-types/regular-expression-examples.md)|包含程式碼範例，說明規則運算式在常見應用程式中的使用方式。|  
|[規則運算式語言 - 快速參考](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|提供您可以用來定義規則運算式之字元、運算子和建構組合的資訊。|  
  
## <a name="reference"></a>參考資料  
 <xref:System.Text.RegularExpressions?displayProperty=nameWithType>
