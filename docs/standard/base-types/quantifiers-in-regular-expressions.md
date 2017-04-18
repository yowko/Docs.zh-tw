---
title: "規則運算式中的數量詞 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "規則運算式，數量詞"
  - "中繼字元，數量詞"
  - "最低比對數量詞"
  - "規則運算式中的數量詞"
  - ".NET Framework 規則運算式，數量詞"
  - "數量詞"
  - "暫緩數量詞"
ms.assetid: 36b81212-6511-49ed-a8f1-ff080415312f
caps.latest.revision: 22
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 22
---
# 規則運算式中的數量詞
數量詞會指定有多少個字元、群組或字元類別的執行個體必須存在於輸入中，才能讓比對找到。下表列出 .NET Framework 支援的數量詞。  
  
|窮盡數量詞|省略數量詞|說明|  
|-----------|-----------|--------|  
|`*`|`*?`|比對零次或多次。|  
|`+`|`+?`|比對一次或多次。|  
|`?`|`??`|比對零次或一次。|  
|`{` *n* `}`|`{` *n* `}?`|正好比對 *n* 次。|  
|`{` *n* `,}`|`{` *n* `,}?`|比對至少 *n* 次。|  
|`{` *n* `,` *m* `}`|`{` *n* `,` *m* `}?`|比對了 *n* 到 *m* 次。|  
  
 數量 `n` 和 `m` 是整數常數。  通常，數量詞是窮盡的，它們會讓規則運算式引擎盡可能多次比對特定的模式。  將 `?` 字元附加至限定詞會使它變得省略，它會讓規則運算式引擎盡可能比對最少次數。  如需窮盡和省略數量詞之間差異的完整說明，請參閱本主題稍後的[窮盡和省略數量詞](#Greedy)一節。  
  
> [!IMPORTANT]
>  巢狀數量詞 \(例如，規則運算式模式`(a*)*`\) 可以增加必須執行規則運算式引擎的比較數目，做為輸入字串中字元數目的指數函式。  如需關於此行為及其解決方法的詳細資訊，請參閱[回溯](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)。  
  
## 規則運算式數量詞  
 下一節列出 .NET Framework 規則運算式所支援的數量詞。  
  
> [!NOTE]
>  如果在規則運算式模式中遇到 \*、\+、？、{ 和 } 字元，規則運算式引擎會將它們解譯為數量詞或數量詞建構的一部分，除非它們包含在[字元類別](../../../docs/standard/base-types/character-classes-in-regular-expressions.md)中。  若要將這些解譯為字元類別外部的常值字元，您必須在前面以反斜線溢出它們。  例如，在規則運算式模式中的字串 `\*` 會被解譯為常值的星號 \("\*"\) 字元。  
  
### 比對零次或多次：\*  
 `*` 數量詞會比對前置項目零次或多次。  它相當於 `{0,}` 數量詞。  `*` 是窮盡數量詞，其省略的對等用法為 `*?`。  
  
 下列範例說明這個規則運算式。  在輸入字串的 9 組數字中，五個符合模式，而四個 \(`95`、`929`、`9129` 和 `9919`\) 則不符合。  
  
 [!code-csharp[RegularExpressions.Quantifiers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#1)]  
  
 此規則運算式模式的定義方式如下表所示。  
  
|模式|說明|  
|--------|--------|  
|`\b`|從字緣開始。|  
|`91*`|比對後接零個或多個 "1" 字元的 "9"。|  
|`9*`|比對零個或多個 "9" 字元。|  
|`\b`|在字緣結束。|  
  
### 比對一次或多次：\+  
 `+` 數量詞會比對前置項目一次或多次。  它就相當於 `{1,}`。  `+` 是窮盡數量詞，其省略的對等用法為 `+?`。  
  
 例如，規則運算式 `\ban+\w*?\b` 會嘗試比對開頭字母為 `a` 且後面接著一個或多個字母 `n` 的單字。  下列範例說明這個規則運算式。  這個規則運算式會比對出 `an`、`annual`、`announcement` 和 `antique` 等單字，但比對不出 `autumn` 和 `all`。  
  
 [!code-csharp[RegularExpressions.Quantifiers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#2)]  
  
 此規則運算式模式的定義方式如下表所示。  
  
|模式|說明|  
|--------|--------|  
|`\b`|從字緣開始。|  
|`an+`|比對後接一個或多個 "n" 字元的 "a"。|  
|`\w*?`|比對字組字元零次或多次，但盡可能減少次數。|  
|`\b`|在字緣結束。|  
  
### 比對零次或一次：?  
 `?` 數量詞會比對前置項目零次或一次。  它就相當於 `{0,1}`。  `?` 是窮盡數量詞，其省略的對等用法為 `??`。  
  
 例如，規則運算式 `\ban?\b` 會嘗試比對開頭字母為 `a` 且後面接著零個或多個字母 `n` 的單字。  換句話說，它會嘗試比對單字 `a` 和 `an`。  下列範例說明這個規則運算式。  
  
 [!code-csharp[RegularExpressions.Quantifiers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#3)]
 [!code-vb[RegularExpressions.Quantifiers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#3)]  
  
 此規則運算式模式的定義方式如下表所示。  
  
|模式|說明|  
|--------|--------|  
|`\b`|從字緣開始。|  
|`an?`|比對後接零個或一個 "n" 字元的 "a"。|  
|`\b`|在字緣結束。|  
  
### 比對正好 n 次：{n}  
 `{` *n* `}` 數量詞會比對前置項目剛好 *n* 次，其中 *n* 可以是任意整數。  `{`*n*`}` 是窮盡數量詞，其省略的對等用法為 `{`*n*`}?`。  
  
 例如，規則運算式 `\b\d+\,\d{3}\b` 會嘗試比對字組界限，後面接著一個或多個十進位數字，再接著三個十進位數字，最後接著字組界限。  下列範例說明這個規則運算式。  
  
 [!code-csharp[RegularExpressions.Quantifiers#4](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#4)]
 [!code-vb[RegularExpressions.Quantifiers#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#4)]  
  
 此規則運算式模式的定義方式如下表所示。  
  
|模式|說明|  
|--------|--------|  
|`\b`|從字緣開始。|  
|`\d+`|比對一個或多個十進位數字。|  
|`\,`|比對逗號字元。|  
|`\d{3}`|比對三個十進位數字。|  
|`\b`|在字緣結束。|  
  
### 比對至少 n 次：{n,}  
 `{` *n* `,}` 數量詞會比對前置項目至少 *n* 次，其中 *n* 可以是任何整數。  `{`*n*`,}` 是窮盡數量詞，其省略的對等用法為 `{`*n*`}?`。  
  
 例如，規則運算式 `\b\d{2,}\b\D+` 會嘗試比對字組界限，後面接著至少兩個數字，再接著字組界限和一個非數字字元。  下列範例說明這個規則運算式。  此規則運算式比對不出 `"7 days"` 詞組，因為它只有一個十進位數字，但可以成功比對出 `"10 weeks and 300 years"` 詞組。  
  
 [!code-csharp[RegularExpressions.Quantifiers#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#5)]
 [!code-vb[RegularExpressions.Quantifiers#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#5)]  
  
 此規則運算式模式的定義方式如下表所示。  
  
|模式|說明|  
|--------|--------|  
|`\b`|從字緣開始。|  
|`\d{2,}`|比對至少兩個十進位數字。|  
|`\b`|比對字緣。|  
|`\D+`|比對至少一個非十進位數字。|  
  
### 比對 n 和 m 之間的次數：{n,m}  
 `{` *n* `,` *m* `}` 數量詞會比對前置項目至少 *n* 次，但不會超過 *m* 次，其中 *n* 與 *m* 可以是任何整數。  `{`*n*`,`*m*`}` 是窮盡數量詞，其省略的對等用法為 `{`*n*`,`*m*`}?`。  
  
 在下列範例中，規則運算式 `(00\s){2,4}` 會嘗試比對出現兩次到四次的兩個零，後接一個空格。  請注意，輸入字串的最後部分包含此模式五次，而非四次上限。  不過，只有這個子字串的開頭部分 \(直到空格和第五組零\) 符合規則運算式模式。  
  
 [!code-csharp[RegularExpressions.Quantifiers#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#6)]
 [!code-vb[RegularExpressions.Quantifiers#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#6)]  
  
### 比對零次或多次 \(省略比對\)：\*?  
 `*?` 數量詞會比對前置項目零次或多次，但會盡可能減少次數。  它是窮盡數量詞 `*` 的對應省略數量詞。  
  
 在下列範例中，規則運算式 `\b\w*?oo\w*?\b`會比對包含 `oo` 字串的所有字組。  
  
 [!code-csharp[RegularExpressions.Quantifiers#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#7)]
 [!code-vb[RegularExpressions.Quantifiers#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#7)]  
  
 此規則運算式模式的定義方式如下表所示。  
  
|模式|說明|  
|--------|--------|  
|`\b`|從字緣開始。|  
|`\w*?`|比對零個或多個字組字元，但越少字元越好。|  
|`oo`|比對字串 "oo"。|  
|`\w*?`|比對零個或多個字組字元，但越少字元越好。|  
|`\b`|在字組界限上結束。|  
  
### 比對一次或多次 \(省略比對\)：\+?  
 `+?` 數量詞會比對前置項目一次或多次，但會盡可能減少次數。  它是窮盡數量詞 `+` 的對應省略數量詞。  
  
 例如，規則運算式 `\b\w+?\b` 會比對由字組界限隔開的一個或多個字元。  下列範例說明這個規則運算式。  
  
 [!code-csharp[RegularExpressions.Quantifiers#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#8)]
 [!code-vb[RegularExpressions.Quantifiers#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#8)]  
  
### 比對零次或一次 \(省略比對\)：??。  
 `??` 數量詞會比對前置項目零次或一次，但會盡可能減少次數。  它是窮盡數量詞 `?` 的對應省略數量詞。  
  
 例如，一般運算式`^\s*(System.)??Console.Write(Line)??\(??`會嘗試比對字串串"Console.Write" 或"Console.WriteLine"。  此字串也可在 "Console" 之前包含 "System."，而且後面可以接著左括號。  此字串必須位於行首，但前面可以是空格。  下列範例說明這個規則運算式。  
  
 [!code-csharp[RegularExpressions.Quantifiers#9](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#9)]
 [!code-vb[RegularExpressions.Quantifiers#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#9)]  
  
 此規則運算式模式的定義方式如下表所示。  
  
|模式|說明|  
|--------|--------|  
|`^`|比對輸入資料流的開頭。|  
|`\s*`|比對零個以上的空白字元。|  
|`(System.)??`|比對出現零次或一次的 "System" 字串。|  
|`Console.Write`|比對字串 "Console.Write"。|  
|`(Line)??`|比對零個或一個符合 "Line" 字串的項目。|  
|`\(??`|比對出現零次或一次的左括號。|  
  
### 比對至少 n 次 \(省略比對\)：{n}?  
 `{` *n* `}?` 數量詞會比對前置項目剛好 `n` 次，其中 *n* 可以是任意整數。  它是窮盡數量詞 `{`*n*`}+` 的對應省略數量詞。  
  
 在廈列範例中，規則運算式 `\b(\w{3,}?\.){2}?\w{3,}?\b`用於識別網址。  請注意，它會比對 "www.microsoft.com" 和 "msdn.microsoft.com"，但不會比對 "mywebsite" 或 "mycompany.com"。  
  
 [!code-csharp[RegularExpressions.Quantifiers#10](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#10)]
 [!code-vb[RegularExpressions.Quantifiers#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#10)]  
  
 此規則運算式模式的定義方式如下表所示。  
  
|模式|說明|  
|--------|--------|  
|`\b`|從字緣開始。|  
|`(\w{3,}?\.)`|比對至少 3 個字組字元，但盡可能減少次數，後接點或句號字元。  這是第一個擷取群組。|  
|`(\w{3,}?\.){2}?`|比對第一個群組中的模式兩次，但為盡可能減少次數。|  
|`\b`|結束字緣比對。|  
  
### 比對至少 n 次 \(省略比對\)：{n,}?  
 `{` *n* `,}?` 數量詞會比對前置項目至少 `n` 次，其中 *n* 可以是任何整數，但會盡可能減少次數。  它是窮盡數量詞 `{`*n*`,}` 的對應省略數量詞。  
  
 如需圖例，請參閱上一節中的 `{`*n*`}?` 數量詞。  該範例的規則運算式會使用 `{`*n*`,}` 數量詞來比對至少有三個字元並後接句點的字串。  
  
### 比對 n 和 m 之間的次數 \(省略比對\)：{n,m}?  
 `{` *n* `,` *m* `}?` 數量詞會比對前置項目 `n` 到 `m` 次，其中 *n* 與 *m* 是整數，但會盡可能減少次數。  它是窮盡數量詞 `{`*n*`,`*m*`}` 的對應省略數量詞。  
  
 在下列範例中，規則運算式 `\b[A-Z](../../../amples/snippets/visualbasic/VS_Snippets_Remoting/SoapAttributes1/VB/s.vb){1,10}?[.!?]` 會在包含一個到十個字的句子之間比對。  它會比對輸入字串中的所有句子，但包含 18 個字組的單一句子除外。  
  
 [!code-csharp[RegularExpressions.Quantifiers#12](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#12)]
 [!code-vb[RegularExpressions.Quantifiers#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#12)]  
  
 此規則運算式模式的定義方式如下表所示。  
  
|模式|說明|  
|--------|--------|  
|`\b`|從字緣開始。|  
|`[A-Z]`|比對從 A 到 Z 範圍的一個大寫字元。|  
|`(\w*\s+)`|比對零個或多個字組字元，後接一個或多個空格字元。  這是第一個擷取群組。|  
|`{1,10}?`|以 1 和 10 之間的次數比對上一個模式，但盡可能減少次數。|  
|`[.!?]`|比對任何一個標點符號字元 "."、"\!" 或 "?"。|  
  
<a name="Greedy"></a>   
## 窮盡與省略數量詞  
 許多數量詞都有兩種版本：  
  
-   窮盡版本  
  
     窮盡數量詞會嘗試盡可能多次比對項目。  
  
-   非窮盡 \(或省略\) 版本  
  
     非窮盡數量詞會嘗試盡可能減少比對項目的次數。  您可以藉由只新增 `?`，將窮盡數量詞轉變成靜態數量詞。  
  
 請考慮簡單的規則運算式，可擷取數字字串 \(例如信用卡號碼\) 的後四位數字。  使用 `*` 窮盡數量詞的規則運算式版本為 `\b.*([0-9]{4})\b`。  不過，如果字串包含兩個數字，此規則運算式就只會比對第二個數字的最後四個位數，如下列範例所示。  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#1)]  
  
 這個規則運算式無法比對第一組號碼，因為 `*` 數量詞會在整個字串中比對前置項目許多次，最後在字串結尾找到符合的項目。  
  
 這並不是我們預期的結果。  您可以改用 `*?` ``  省略數量詞從這兩個數字擷取位數，如下列範例所示。  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#2)]  
  
 在大部分情況下，使用窮盡和省略數量詞的規則運算式會傳回相同的結果。  它們一般是在與符合任何字元的萬用 \( `.` 中繼字元搭配使用時，才會傳回不同的結果。  
  
## 數量詞和空白比對  
 當數量詞 `*`、 `+` 和 `{`*n*`,`*m*`}`，以及其惰性對應詞找到最小數量的擷取項目時，就永遠不會在空白比對後重複。  當可能擷取的最大群組數是無限大或接近無限大時，這項規則會防止數量詞在空的子運算式比對上進入無限迴圈。  
  
 例如，下列程式碼顯示以一般運算式模式 `(a?)*` 叫用 <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=fullName> 方法的結果，該模式有零次以上符合零或一個 "a" 字元。  請注意，單一擷取群組會擷取每個 "a" 以及<xref:System.String.Empty?displayProperty=fullName>，但沒有第二個空的相符項目，因為第一個空的相符項目會導致數量詞停止重複。  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch1.vb#1)]  
  
 若要查看定義最小及最大擷取數量之擷取群組與定義固定擷取數量之擷取群組間的實際差異，請考慮規則運算式模式 `(a\1|(?(1)\1)){0,2}` 和 `(a\1|(?(1)\1)){2}`。  兩個規則運算式都包含單一擷取群組，其定義如下表所示。  
  
|模式|說明|  
|--------|--------|  
|`(a\1`|比對 "a" 和第一個擷取群組的值...|  
|`&#124;(?(1)`|… 或測試是否已定義第一個擷取到的群組。\(請注意，`(?(1)`構建未定義擷取群組。\)|  
|`\1))`|如果第一個擷取群組存在，則比對其值。  如果群組不存在，該群組會符合<xref:System.String.Empty?displayProperty=fullName>。|  
  
 第一個規則運算式嘗試比對此模式零次和兩次；第二個比對正好兩次。  因為第一種模式達到其最小的擷取數目與第一個 <xref:System.String.Empty?displayProperty=fullName> 擷取，因此不會重複嘗試比對 `a\1`；`{0,2}` 數量詞只允許最後一個反覆項目中的空符合項目。  相反地，因為會評估`a\1`第二次，因此第二個一般運算式確實會比對 "a"；而反覆運算的最小數值 2 會強制引擎在空白比對後重複。  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch4.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch4.vb#2)]  
  
## 請參閱  
 [規則運算式語言 \- 快速參考](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)   
 [回溯](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)