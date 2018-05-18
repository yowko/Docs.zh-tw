---
title: .NET 中規則運算式的最佳做法
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework regular expressions, best practices
- regular expressions, best practices
ms.assetid: 618e5afb-3a97-440d-831a-70e4c526a51c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2bb1d9bdbd0874875939010ea5503fe791a2cd1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="best-practices-for-regular-expressions-in-net"></a>.NET 中規則運算式的最佳做法
<a name="top"></a> .NET 中的規則運算式引擎是一項強大且功能完整的工具，會依據模式比對而非比較與比對常值文字的方式處理文字。 在大部分情況下，它會快速且有效率地執行模式比對。 不過，在某些情況下，規則運算式引擎速度可能變得相當慢。 而只有鮮少情況下，它甚至可能在處理相對小的輸入卻耗費數小時甚至數天時停止回應。  
  
 本主題說明一些開發人員可以採用的最佳做法，確保其規則運算式達到最佳效能。 它包含以下各節：  
  
-   [考慮輸入來源](#InputSource)  
  
-   [適當處理物件具現化](#ObjectInstantiation)  
  
-   [控制回溯](#Backtracking)  
  
-   [使用逾時值](#Timeouts)  
  
-   [必要時擷取](#Capture)  
  
-   [相關主題](#RelatedTopics)  
  
<a name="InputSource"></a>   
## <a name="consider-the-input-source"></a>考慮輸入來源  
 一般而言，規則運算式可以接受兩種類型的輸入：受限制或未受限制。 受限制的輸入是來自已知或可靠來源，並且遵循預先定義格式的文字。 未受限制的輸入是來自不可靠來源 (例如 Web 使用者) 的文字，且可能未依循預先定義或預期的格式。  
  
 通常撰寫規則運算式模式的目的在於比對有效輸入。 也就是說，開發人員會檢查要比對的文字，然後撰寫比對該文字的規則運算式模式。 接著開發人員會利用多個有效的輸入項目進行測試，藉此判斷此模式是否需要更正或進一步詳述。 當模式符合所有假設的有效輸入時，即宣告準備好實際執行，並且可以納入已發行的應用程式中。 這種方式使得規則運算式模式相當適合比對限制的輸入， 不過卻不適合比對未受限制的輸入。  
  
 若要比對未受限制的輸入，規則運算式必須能夠有效率地處理三種文字：  
  
-   符合規則運算式模式的文字。  
  
-   不符合規則運算式模式的文字。  
  
-   幾乎符合規則運算式模式的文字。  
  
 最後一種文字對於專為處理受限制輸入的規則運算式而言尤其繁瑣。 如果該規則運算式也依賴大量[回溯](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)，則規則運算式引擎可能耗費相當長的時間 (有些情況需要許多小時或許多天) 處理看似無關緊要的文字。  
  
> [!WARNING]
>  下列範例將使用容易造成大量回溯，而且可能拒絕有效電子郵件地址的規則運算式。 這個規則運算式不應該在電子郵件驗證常式中使用。 如果您想要會驗證電子郵件地址的規則運算式，請參閱[如何：確認字串是否為有效的電子郵件格式](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md)。  
  
 例如，像是驗證電子郵件地址別名的規則運算式，這種規則運算式相當常用卻也極為繁瑣。 規則運算式 `^[0-9A-Z]([-.\w]*[0-9A-Z])*$` 主要用來處理一般視為有效的電子郵件地址，其中包含英數字元，後面接著零個或多個字元，而這些字元可以是英數字、句號或連字號。 規則運算式的結尾必須是英數字元。 不過，如下面的範例所示，雖然這個規則運算式可輕鬆處理有效的輸入，但是當它處理幾乎有效的輸入時就非常沒有效率。  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/design2.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/design2.vb#1)]  
  
 如範例的輸出所示，規則運算式引擎會以大致相同的時間間隔處理有效的電子郵件別名 (無論其長度為何)。 但另一方面，當幾乎有效的電子郵件地址包含超過五個字元時，字串中超出的每個字元其處理時間約為兩倍。 這表示，幾乎有效的 28 個字元字串需要超過一小時的處理時間，而幾乎有效的 33 個字元字串則需要將近一天來處理。  
  
 由於這個規則運算式單純是考量所要比對輸入的格式而開發，因此並未考慮不符合模式的輸入。 而這種情況就會讓幾乎符合規則運算式模式的未受限制輸入大幅降低效能。  
  
 若要解決這個問題，您可以執行下列操作：  
  
-   開發模式時，您應考慮回溯可能對規則運算式引擎的效能造成的影響，尤其是規則運算式的設計為處理未受限制的輸入。 如需詳細資訊，請參閱[控制回溯](#Backtracking)一節。  
  
-   使用無效或幾乎有效的輸入以及有效輸入徹底測試您的規則運算式。 若要針對特殊規則運算式隨機產生輸入，您可以使用 [Rex](https://www.microsoft.com/en-us/research/project/rex-regular-expression-exploration/)，這是 Microsoft Research 提供的規則運算式探索工具。  
  
 [回到頁首](#top)  
  
<a name="ObjectInstantiation"></a>   
## <a name="handle-object-instantiation-appropriately"></a>適當處理物件具現化  
 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> 類別是 .NET 規則運算式物件模型的核心，它代表規則運算式引擎。 使用 <xref:System.Text.RegularExpressions.Regex> 引擎的方式經常是影響規則運算式效能最重要的一項因素。 定義規則運算式的工作與結合規則運算式引擎和規則運算式模式息息相關。 無論是傳遞規則運算式模式給 <xref:System.Text.RegularExpressions.Regex> 物件的建構函式，藉此將該物件具現化，或是將規則運算式模式連同要分析的字串一併傳遞給靜態方法，藉此呼叫該方法，這個結合的過程都必然相當昂貴。  
  
> [!NOTE]
>  如需使用已解譯和已編譯規則運算式所造成不良效能影響的詳細討論，請參閱 BCL Team 部落格中的[將規則運算式的效能最佳化，第 II 部分：控制回溯](https://blogs.msdn.microsoft.com/bclteam/2010/08/03/optimizing-regular-expression-performance-part-ii-taking-charge-of-backtracking-ron-petrusha/) \(英文\)。  
  
 您可以結合規則運算式引擎與特定規則運算式模式，然後使用引擎透過數種方式比對文字：  
  
-   您可以呼叫靜態模式比對方法，例如 <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType>。 這樣就不需要具現化規則運算式物件。  
  
-   您可以具現化 <xref:System.Text.RegularExpressions.Regex> 物件，並且呼叫解譯之規則運算式的執行個體模式比對方法。 這是將規則運算式引擎繫結至規則運算式模式的預設方法。 這個方法會在 <xref:System.Text.RegularExpressions.Regex> 物件具現化，但是沒有包含 `options` 旗標的 <xref:System.Text.RegularExpressions.RegexOptions.Compiled> 引數時得出結果。  
  
-   您可以具現化 <xref:System.Text.RegularExpressions.Regex> 物件，並且呼叫編譯之規則運算式的執行個體模式比對方法。 當 <xref:System.Text.RegularExpressions.Regex> 物件具現化且包含 `options` 旗標的 <xref:System.Text.RegularExpressions.RegexOptions.Compiled> 引數時，規則運算式物件就會表示編譯的模式。  
  
-   您可以建立與特殊規則運算式模式緊密結合的特殊目的 <xref:System.Text.RegularExpressions.Regex> 物件、進行編譯，並且將它儲存到獨立的組件中。 您可以藉由呼叫 <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> 方法執行這項作業。  
  
 您呼叫規則運算式比對方法的特殊方式可能對應用程式造成大幅影響。 下列各節將討論何時使用靜態方法呼叫、解譯的規則運算式以及編譯的規則運算式改善應用程式的效能。  
  
> [!IMPORTANT]
>  如果在方法呼叫中重複使用相同的規則運算式，或是應用程式大量使用規則運算式物件，則方法呼叫的形式 (靜態、解譯、編譯) 就會影響效能。  
  
### <a name="static-regular-expressions"></a>靜態規則運算式  
 建議您使用靜態規則運算式方法來替代使用相同的規則運算式重複具現化規則運算式物件。 與規則運算式物件所使用的規則運算式模式不同的是，規則運算式引擎會在內部快取作業程式碼或是從執行個體方法呼叫中所使用模式編譯的 Microsoft intermediate language (MSIL)。  
  
 例如，事件處理常式經常會呼叫另一個方法來驗證使用者輸入。 下列程式碼中會反映這種情況，其中 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Click> 事件會用來呼叫名為 `IsValidCurrency` 的方法，該方法會檢查使用者是否已輸入貨幣符號且後面至少有一個十進位數字。  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static1.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static1.vb#2)]  
  
 下列範例示範非常沒有效率的 `IsValidCurrency` 方法實作。 請注意，每一個方法呼叫都會使用相同的模式重複具現化 <xref:System.Text.RegularExpressions.Regex> 物件。 而這表示，每次呼叫方法時都必須重新編譯規則運算式。  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static1.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static1.vb#3)]  
  
 您應該用呼叫靜態 <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> 方法取代這個沒有效率的程式碼。 這樣就不必在每次您想要呼叫模式比對方法時具現化 <xref:System.Text.RegularExpressions.Regex> 物件，並且可讓規則運算式引擎從其快取擷取編譯版的規則運算式。  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static2.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static2.vb#4)]  
  
 根據預設，會快取 15 個最近使用的靜態規則運算式模式。 針對需要大量快取之靜態規則運算式的應用程式，快取的大小可以透過設定 <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> 屬性加以調整。  
  
 這個範例中使用的規則運算式 `\p{Sc}+\s*\d+` 會驗證輸入字串是否包含貨幣符號和至少一個十進位數字。 模式的定義方式如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`\p{Sc}+`|比對 [Unicode Symbol, Currency] 分類中的一個或多個字元。|  
|`\s*`|比對零個以上的空白字元。|  
|`\d+`|比對一個或多個十進位數字。|  
  
<a name="Interpreted"></a>   
### <a name="interpreted-vs-compiled-regular-expressions"></a>解譯與編譯的規則運算式  
 未透過指定 <xref:System.Text.RegularExpressions.RegexOptions.Compiled> 選項繫結至規則運算式引擎的規則運算式模式會加以解譯。 具現化規則運算式物件時，規則運算式引擎會將規則運算式轉換成一組作業程式碼。 呼叫執行個體方法時，作業程式碼會轉換成 MSIL 並且由 JIT 編譯器執行。 同樣地，當呼叫靜態規則運算式方法而快取中找不到規則運算式時，規則運算式引擎會將規則運算式轉換成一組作業程式碼，並且將它們儲存到快取中。 然後引擎會將這些作業程式碼轉換成 MSIL，JIT 編譯器就可以執行這些作業程式碼。 解譯的規則運算式會藉由放慢執行時間來縮短啟動時間。 因此，在少數方法呼叫中使用規則運算式時，或是雖然不知道規則運算式方法呼叫的確實數目，但是期望數目很少時，最適合使用解譯的規則運算式。 隨著方法呼叫的數目增加，放慢執行速度就會壓縮掉縮短啟動時間所獲得的效能。  
  
 透過指定 <xref:System.Text.RegularExpressions.RegexOptions.Compiled> 選項繫結至規則運算式引擎的規則運算式模式會加以編譯。 這表示，當具現化規則運算式物件，或是當呼叫靜態規則運算式方法而快取中找不到規則運算式時，規則運算式引擎會將規則運算式轉換成一組中繼的作業程式碼，然後將這些程式碼轉換成 MSIL。 呼叫方法時，JIT 編譯器會執行 MSIL。 與解譯的規則運算式相反的是，編譯的規則運算式會延長啟動時間，但加快執行個別模式比對方法的速度。 因此，編譯規則運算式所獲得的效能優勢會與呼叫的規則運算式方法數目成比例。  
  
 簡言之，我們建議您在呼叫含有相對較不常用之特定規則運算式的規則運算式方法時，使用解譯的規則運算式。 而當您呼叫含有相對較常用之特定規則運算式的規則運算式方法時，則應該使用編譯的規則運算式。 無論是放慢解譯的規則運算式執行速度所提升的效能超過縮短的啟動時間，或是放慢編譯的規則運算式啟動時間所提升的效能超過加快執行速度，都不容易判斷出其確實的臨界值。 因為臨界值取決於各種不同的因素，包括規則運算式及其處理之特定資料的複雜度。 若要判斷究竟是解譯或編譯的規則運算式能為您的特殊應用程式案例提供最佳效能，您可以使用 <xref:System.Diagnostics.Stopwatch> 類別比較兩者的執行時間。  
  
 下列範例會比較已編譯和已解譯的規則運算式讀取 Theodore Dreiser 所著 *The Financier* 一文的前十個句子及讀取所有句子時的效能。 如範例的輸出所示，僅對規則運算式比對方法進行十次呼叫時，解譯的規則運算式能提供比編譯的規則運算式更佳的效能。 但是進行大量呼叫 (此案例中為超過 13,000 次) 時，編譯的規則運算式會提供較佳的效能。  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compare1.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compare1.vb#5)]  
  
 範例中所使用規則運算式模式 `\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]` 的定義方式如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`\b`|開始字緣比對。|  
|`\w+`|比對一個或多個文字字元。|  
|<code>(\r?\n)&#124;,?\s)</code>|比對後面接著新行字元的零個或一個歸位字元，或是後面接著空白字元的零個或一個逗號。|  
|<code>(\w+((\r?\n)&#124;,?\s))*</code>|比對出現零次或多次的一個或多個文字字元，其後面會接著零個或一個歸位字元和新行字元，或是後面接著空白字元的零個或一個逗號。|  
|`\w+`|比對一個或多個文字字元。|  
|`[.?:;!]`|比對句號、問號、冒號、分號或驚嘆號。|  
  
### <a name="regular-expressions-compiled-to-an-assembly"></a>規則運算式：編譯為組件  
 .NET 也可讓您建立包含已編譯規則運算式的組件。 這樣會將規則運算式編譯的效能影響從執行階段移至設計階段。 不過，它還包含了一些額外的工作：您必須事先定義規則運算式，並且將其編譯為組件。 接著編譯器就可在編譯使用組件之規則運算式的原始程式碼時參考這個組件。 組件中的每個編譯的規則運算式都會以衍生自 <xref:System.Text.RegularExpressions.Regex> 的類別表示。  
  
 若要將規則運算式編譯為組件，請呼叫 <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%28System.Text.RegularExpressions.RegexCompilationInfo%5B%5D%2CSystem.Reflection.AssemblyName%29?displayProperty=nameWithType> 方法，並且將代表要編譯之規則運算式的 <xref:System.Text.RegularExpressions.RegexCompilationInfo> 物件陣列，以及包含所要建立組件之相關資訊的 <xref:System.Reflection.AssemblyName> 物件傳遞給該方法。  
  
 建議您在下列情況下將規則運算式編譯為組件：  
  
-   如果您是元件開發人員，而且想要建立可重複使用的規則運算式程式庫。  
  
-   如果您希望不定次數 (從一、兩次到數千、數萬次) 地呼叫規則運算式的模式比對方法。 與編譯或解譯的規則運算式不同的是，無論方法呼叫的次數為何，編譯為個別組件的規則運算式都會提供一致的效能。  
  
 如果您要使用編譯的規則運算式來最佳化效能，則不應使用反映來建立組件、載入規則運算式引擎，以及執行其模式比對方法。 因此您就必須避免動態建置規則運算式模式，並且在建立組件時指定任何模式比對選項 (例如不區分大小寫的模式比對)。 另外，您也必須將建立組件的程式碼與使用規則運算式的程式碼分開。  
  
 下列範例示範如何建立內含編譯的規則運算式的組件。 範例中會建立名為 `RegexLib.dll` 且內含單一規則運算式類別 `SentencePattern` 的組件，其中包含[解譯與編譯的規則運算式](#Interpreted)一節中使用的句子比對規則運算式模式。  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compile1.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compile1.vb#6)]  
  
 當範例編譯為可執行檔並且執行時，會建立名為 `RegexLib.dll` 的組件。 規則運算式會以衍生自 `Utilities.RegularExpressions.SentencePattern` 且名為 <xref:System.Text.RegularExpressions.Regex> 的類別表示。 下列範例接著會使用已編譯的規則運算式來擷取 Theodore Dreiser 所著 *The Financier* 一文中的句子。  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compile2.cs#7)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compile2.vb#7)]  
  
 [回到頁首](#top)  
  
<a name="Backtracking"></a>   
## <a name="take-charge-of-backtracking"></a>控制回溯  
 通常規則運算式引擎會使用線性迴歸逐一處理輸入字串，並且與規則運算式模式比較。 不過，當規則運算式模式中使用不定數的數量詞 (例如 `*`、`+` 和 `?`) 時，規則運算式引擎可能會放棄一部分成功的部分符合結果，並且返回之前儲存的狀態，以便搜尋與整個模式完全相符的結果。 這個程序稱為「回溯」(Backtracking)。  
  
> [!NOTE]
>  如需有關回溯的詳細資訊，請參閱[規則運算式行為的詳細資料](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)和[回溯](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)。 如需有關回溯的詳細討論，請參閱 BCL Team 部落格中的[將規則運算式的效能最佳化，第 II 部分：控制回溯](https://blogs.msdn.microsoft.com/bclteam/2010/08/03/optimizing-regular-expression-performance-part-ii-taking-charge-of-backtracking-ron-petrusha/) \(英文\)。  
  
 支援回溯能讓規則運算式更強大且更靈活， 同時還能讓規則運算式開發人員負責掌控規則運算式引擎的作業。 由於開發人員經常忽略這個責任而誤用回溯或大量使用回溯，因而時常是造成規則運算式效能低落的最重要原因。 在最糟的情況下，輸入字串中每個超出字元的執行時間可能會倍增。 事實上，如果輸入幾乎符合規則運算式模式的話，大量使用回溯很容易製造相當於程式設計上的無窮迴圈，而規則運算式引擎可能需要數小時，甚至數天來處理相對來說很短的輸入字串。  
  
 儘管回溯並不是比對的要件，應用程式常常會因為使用回溯而影響效能。 例如，規則運算式 `\b\p{Lu}\w*\b` 會比對所有開頭為大寫字元的文字，如下表所示。  
  
|模式|描述|  
|-|-|  
|`\b`|開始字緣比對。|  
|`\p{Lu}`|比對大寫字元。|  
|`\w*`|比對零個或多個文字字元。|  
|`\b`|結束字緣比對。|  
  
 由於字緣與文字字元不同，也不是文字字元的子集，因此規則運算式引擎不可能在比對文字字元時跨越字緣。 這表示對於這個規則運算式來說，回溯不會使任何比對完全成功，只會造成效能降低，因為規則運算式引擎會被迫儲存每一個成功的初始文字字元比對的狀態。  
  
 如果您判定不需回溯，則可使用 `(?>``subexpression``)` 語言元素來停用它。 下列範例會使用兩個規則運算式剖析輸入字串。 首先，`\b\p{Lu}\w*\b` 會仰賴回溯。 第二，`\b\p{Lu}(?>\w*)\b` 會停用回溯。 如範例的輸出所示，兩者會產生相同的結果。  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/backtrack2.cs#10)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/backtrack2.vb#10)]  
  
 在許多情況下，回溯是比對規則運算式模式與輸入文字時所必要。 不過，大量回溯可能嚴重降低效能，並且製造應用程式停止回應的印象。 尤其是當數量詞為巢狀，而且符合外部子運算式的文字是符合內部子運算式之文字的子集時，就會發生這種情況。  
  
> [!WARNING]
>  除了避免大量回溯以外，您應該使用逾時功能確保大量回溯不會嚴重降低規則運算式的效能。 如需詳細資訊，請參閱[使用逾時值](#Timeouts)一節。  
  
 例如，規則運算式模式 `^[0-9A-Z]([-.\w]*[0-9A-Z])*\$$` 的目的在於比對至少包含一個英數字元的零件編號。 任何額外的字元都可能包含英數字元、連字號、底線或句號，不過最後一個字元必須是英數字。 $ 符號則結束零件編號。 在某些情況下，這個規則運算式模式可能顯現出極差的效能，因為數量詞為巢狀，而且子運算式 `[0-9A-Z]` 是 `[-.\w]*` 子運算式的子集。  
  
 在這類情況下，您可以移除巢狀數量詞，並且將外部子運算式取代為零寬度的右合樣或左合樣判斷提示，藉此最佳化規則運算式的效能。 右合樣和左合樣判斷提示是錨點，它們不會移動輸入字串中的指標，而是向右或向左合樣，以檢查是否符合指定的條件。 例如，零件編號規則運算式可以重寫為 `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$`。 這個規則運算式模式的定義方式如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`^`|在輸入字串的開頭開始比對。|  
|`[0-9A-Z]`|比對英數字元。 零件編號必須至少包含這個字元。|  
|`[-.\w]*`|比對出現零次或多次的任何文字字元、連字號或句號。|  
|`\$`|比對 $ 符號。|  
|`(?<=[0-9A-Z])`|向右合樣結尾的 $ 符號，確定前一個字元是英數字。|  
|`$`|在輸入字串結尾結束比對。|  
  
 下列範例說明如何使用這個規則運算式比對包含可能零件編號的陣列。  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/backtrack4.cs#11)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/backtrack4.vb#11)]  
  
 .NET 中的規則運算式語言包括下列語言項目，可讓您用來消除巢狀數量詞。 如需詳細資訊，請參閱[群組建構](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)。  
  
|語言項目|描述|  
|----------------------|-----------------|  
|`(?=` `subexpression` `)`|零寬度右合樣。 從目前的位置向右合樣，判斷 `subexpression` 是否符合輸入字串。|  
|`(?!` `subexpression` `)`|零寬度右不合樣。 從目前的位置向右合樣，判斷 `subexpression` 是否不符合輸入字串。|  
|`(?<=` `subexpression` `)`|零寬度左合樣。 從目前的位置向左合樣，判斷 `subexpression` 是否符合輸入字串。|  
|`(?<!` `subexpression` `)`|零寬度左不合樣。 從目前的位置向左合樣，判斷 `subexpression` 是否不符合輸入字串。|  
  
 [回到頁首](#top)  
  
<a name="Timeouts"></a>   
## <a name="use-time-out-values"></a>使用逾時值  
 如果您的規則運算式會處理幾乎符合規則運算式模式的輸入，它經常會依賴大量回溯，如此就會大幅影響其效能。 除了仔細考量使用回溯以及對幾乎符合的輸入進行規則運算式測試之外，務必要設定逾時值，以確保將大量回溯 (如發生的話) 的影響降至最低。  
  
 規則運算式逾時間隔會定義規則運算式引擎在逾時前，將尋找單一相符項目的一段時間。預設的逾時間隔是 <xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout?displayProperty=nameWithType>，這表示規則運算式不會逾時。您可以依照下述方式覆寫這個值並定義逾時間隔：  
  
-   在您呼叫 <xref:System.Text.RegularExpressions.Regex> 建構函式具現化 <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> 物件時提供逾時值。  
  
-   呼叫靜態模式比對方法，例如，包含 <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> 參數的 <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> 或 `matchTimeout`。  
  
-   若是藉由呼叫 <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> 方法所建立之編譯的規則運算式，則可呼叫具有 <xref:System.TimeSpan> 類型參數的建構函式。  
  
 如果您已定義逾時間隔，但是在該間隔結束時未找到相符項目，則規則運算式方法會擲回 <xref:System.Text.RegularExpressions.RegexMatchTimeoutException> 例外狀況。 在例外處理常式中，您可以選擇以較長的逾時間隔重試比對、放棄比對嘗試並假設沒有相符項目，或是放棄比對嘗試並記錄例外狀況資訊供未來進行分析。  
  
 下列範例將定義 `GetWordData` 方法，該方法會具現化逾時間隔為 350 毫秒的規則運算式，以計算文字文件中的字數和一個字的平均字元數。 如果比對作業逾時，則逾時間隔將增加 350 毫秒，並且重新具現化 <xref:System.Text.RegularExpressions.Regex> 物件。 如果新的逾時間隔超過 1 秒，則方法會重新擲回例外狀況至呼叫端。  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/timeout1.cs#12)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/timeout1.vb#12)]  
  
 [回到頁首](#top)  
  
<a name="Capture"></a>   
## <a name="capture-only-when-necessary"></a>必要時才擷取  
 .NET 中的規則運算式支援許多群組建構，可讓您將規則運算式模式與一或多個子運算式設為群組。 .NET 規則運算式語言中最常用的群組建構為 `(`*subexpression*`)` (用於定義已編號的擷取群組) 和 `(?<`*name*`>`*subexpression*`)` (用於定義具名擷取群組)。 群組建構是建立反向參考和定義套用數量詞之子運算式的要件。  
  
 不過，使用這些語言項目也有其代價。 這些語言項目會造成在 <xref:System.Text.RegularExpressions.GroupCollection> 屬性傳回的 <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> 物件中填入最近使用的未命名或具名擷取，而如果單一群組建構擷取了輸入字串中的多個子字串，則這些語言項目也會在特定擷取群組的 <xref:System.Text.RegularExpressions.CaptureCollection> 屬性傳回的 <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> 物件中填入多個 <xref:System.Text.RegularExpressions.Capture> 物件。  
  
 通常在規則運算式中使用群組建構的目的在於能夠套用數量詞，而且後續不會使用這些子運算式擷取的群組。 例如，規則運算式 `\b(\w+[;,]?\s?)+[.?!]` 是設計用來擷取整個句子。 下表描述這個規則運算式模式中的語言項目，及其對於 <xref:System.Text.RegularExpressions.Match> 物件的 <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> 和 <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> 集合造成的影響。  
  
|模式|描述|  
|-------------|-----------------|  
|`\b`|開始字緣比對。|  
|`\w+`|比對一個或多個文字字元。|  
|`[;,]?`|比對零個或一個逗號或分號。|  
|`\s?`|比對零個或一個空白字元。|  
|`(\w+[;,]?\s?)+`|比對出現一次或多次的一個或多個文字字元，後面接著選擇性的逗號或分號，再後面接著選擇性的空白字元。 這會定義必要的第一個擷取群組，如此多個文字字元 (也就是文字) 後面接著選擇性標點符號的組合才會重複，直到規則運算式引擎到達句尾為止。|  
|`[.?!]`|比對句號、問號或驚嘆號。|  
  
 如下列範例所示，找到符合的結果時，<xref:System.Text.RegularExpressions.GroupCollection> 和 <xref:System.Text.RegularExpressions.CaptureCollection> 物件中都會填入比對所擷取的項目。 在此案例中，擷取群組 `(\w+[;,]?\s?)` 會存在，如此 `+` 數量詞就能套用至其中，這樣就能讓規則運算式模式比對句子中的每個字。 否則就會比對句子中的最後一個字。  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/group1.cs#8)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/group1.vb#8)]  
  
 如果您使用子運算式的目的只是要在其中套用數量詞，對於擷取的文字並不感興趣，則應該停用群組擷取。 例如，`(?:``subexpression``)` 語言元素會阻止套用該語言元素的群組擷取相符的子字串。 在下列範例中，前一個範例的規則運算式模式會變成 `\b(?:\w+[;,]?\s?)+[.?!]`。 如輸出所示，它會阻止規則運算式引擎填入 <xref:System.Text.RegularExpressions.GroupCollection> 和 <xref:System.Text.RegularExpressions.CaptureCollection> 集合。  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/group2.cs#9)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/group2.vb#9)]  
  
 您可以透過下列其中一種方式停用擷取：  
  
-   使用 `(?:``subexpression``)` 語言元素。 這個項目會阻止在套用該項目的群組中擷取相符的子字串。 不過，它不會停用任何巢狀群組中的子字串擷取。  
  
-   使用 <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture> 選項。 這個選項會停用規則運算式模式中的所有未命名或隱含擷取。 當您使用這個選項時，只會擷取符合 `(?<``name``>``subexpression``)` 語言元素所定義之具名群組的子字串。 <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture> 旗標可以傳遞至 `options` 類別建構函式的 <xref:System.Text.RegularExpressions.Regex> 參數，或是 `options` 靜態比對方法的 <xref:System.Text.RegularExpressions.Regex> 參數。  
  
-   在 `n` 語言項目中使用 `(?imnsx)` 選項。 這個選項會從規則運算式模式中出現該項目的位置開始，停用所有未命名或隱含擷取。 在到達模式結尾或 `(-n)` 選項啟用未命名或隱含擷取之前，擷取都會是停用狀態。 如需詳細資訊，請參閱[其他建構](../../../docs/standard/base-types/miscellaneous-constructs-in-regular-expressions.md)。  
  
-   在 `n` 語言項目中使用 `(?imnsx:``subexpression``)` 選項。 這個選項會停用 `subexpression` 中的所有未命名或隱含擷取。 任何未命名或隱含巢狀擷取群組所進行的擷取也都會停用。  
  
 [回到頁首](#top)  
  
<a name="RelatedTopics"></a>   
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[規則運算式行為的詳細資訊](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)|檢查 .NET 中規則運算式引擎的實作。 本主題將強調規則運算式的靈活度，並且說明開發人員應負責確保規則運算式引擎有效率且穩定地運作。|  
|[回溯](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)|說明何謂回溯以及回溯如何影響規則運算式的效能，並且檢查提供回溯之替代方式的語言項目。|  
|[規則運算式語言 - 快速參考](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|描述 .NET 中規則運算式語言的項目，並且提供每個語言項目之詳細文件的連結。|
