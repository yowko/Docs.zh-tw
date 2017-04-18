---
title: "規則運算式中的反向參考建構 | Microsoft Docs"
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
  - ".NET Framework 規則運算式, 反向參考建構"
  - "反向參考"
  - "建構, 反向參考"
  - "規則運算式, 反向參考建構"
ms.assetid: 567a4b8d-0e79-49dc-8df9-f4b1aa376a2a
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 規則運算式中的反向參考建構
反向參考提供便利的方式來識別字串內的重複字元或子字串。  例如，如果輸入字串包含多次出現的任意子字串，您可以比對第一個出現的子字串與擷取的群組，接著使用反向參考來比對隨後出現的子字串。  
  
> [!NOTE]
>  對於取代字串中的具名和編號擷取群組，會使用不同的語法用來參照。  如需詳細資訊，請參閱[替代](../../../docs/standard/base-types/substitutions-in-regular-expressions.md)。  
  
 .NET Framework 會定義個別的語言項目，以參考編號和具名的擷取群組。  如需擷取群組的詳細資訊，請參閱[群組建構](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)。  
  
## 編號的反向參考  
 編號的反向參考會使用下列語法：  
  
 `\` *number*  
  
 其中 *number* 是規則運算式中的擷取群組序數位置。  例如，`\4` 會比對第四個擷取群組的內容。  如果在規則運算式模式中未定義 *number*，便會發生剖析錯誤，而且規則運算式引擎會擲回 <xref:System.ArgumentException>。  例如，規則運算式 `\b(\w+)\s\1` 有效，因為 `(\w+)` 是運算式中第一個和唯一的擷取群組。  另一方面，`\b(\w+)\s\2` 無效並擲回引數例外狀況，因為沒有編號為 `\2` 的擷取群組。  
  
 請注意，八進位逸出程式碼 \(例如 `\16` 和 `\`*number*\) 和使用相同標記法之反向參考間的模稜兩可。  這個模棱兩可的情況已解決，如下所示：  
  
-   運算式 `\1` 到 `\9` 永遠解譯為反向參考，而不是八進位代碼。  
  
-   如果多位數運算式的第一個數字是 8 或 9 \(例如 `\80` 或 `\91`\)，該運算式便會被解譯為常值。  
  
-   從 `\10` 到更大值的運算式會被視為反向參考 \(如果沒有對應至該數字的反向參考\)，否則，它們會被解譯為八進位代碼。  
  
-   如果規則運算式包含未定義之群組號碼的反向參考，便會發生剖析錯誤，規則運算式引擎會擲回 <xref:System.ArgumentException>。  
  
 如果有模稜兩可的問題，您可以使用 `\k<` *name*`>` 標記法，這樣不會模稜兩可，而且不會與八進位字元碼混淆。  同樣地，十六進位的代碼，例如 `\xdd` 不會模稜兩可，而且不會與反向參考混淆。  
  
 下列範例會在字串中尋找雙字組字元。  它會定義規則運算式 `(\w)\1`，由下列項目組成。  
  
|元素|說明|  
|--------|--------|  
|`(\w)`|比對字組字元，並將其指派給第一個擷取群組。|  
|`\1`|比對與第一個擷取群組之值相同的下一個字元。|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
 [!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]  
  
## 具名反向參考  
 具名的反向參考是使用下列語法來定義的：  
  
 `\k<` *name* `>`  
  
 或：  
  
 `\k'` *name* `'`  
  
 其中 *name* 是規則運算式模式中所定義的擷取群組的名稱。  如果在規則運算式模式中未定義 *name*，便會發生剖析錯誤，而且規則運算式引擎會擲回 <xref:System.ArgumentException>。  
  
 下列範例會在字串中尋找雙字組字元。  它會定義規則運算式 `(?<char>\w)\k<char>`，由下列項目組成。  
  
|元素|說明|  
|--------|--------|  
|`(?<char>\w)`|比對字組字元，並將其指派給名為 `char` 的擷取群組。|  
|`\k<char>`|比對與 `char` 擷取群組之值相同的下一個字元。|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
 [!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]  
  
 請注意，該 *name*也可以是數字的字串表示。  例如，下列範例會使用規則運算式 `(?<2>\w)\k<2>` 來尋找字串中的雙字組字元。  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
 [!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]  
  
## 反向參考比對的項目  
 反向參考會參照群組最近使用的定義 \(由左至右比對時，最接近左邊的定義\)。  當群組進行多個擷取時，反向參考會參照最近發生的擷取。  
  
 以下範例包含規則運算式模式 `(?<1>a)(?<1>\1b)*`，此模式可重新定義 \\ 1 具名群組。  下表說明規則運算式中的每個模式。  
  
|模式|說明|  
|--------|--------|  
|`(?<1>a)`|比對字元 "a"，並將結果指派給名為 `1` 的擷取群組。|  
|`(?<1>\1b)*`|比對出現 0 或 1 次，名為 `1` 的群組連同 "b"，並將結果指派至名為 `1` 的擷取群組。|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
 [!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]  
  
 在比較規則運算式與輸入字串 \("aababb"\) 時，規則運算式引擎會執行下列作業：  
  
1.  它會從該字串的開頭開始，並成功地以運算式 `(?<1>a)` 比對 "a"。  `1` 群組的值現在是「a」。  
  
2.  它會前進到第二個字元，並且成功地比對字串 "ab" 與運算式 `\1b`，或是 "ab"。  然後它會將結果 "ab" 指派至 `\1`。  
  
3.  它會前進到第四個字元。  運算式 `(?<1>\1b)` 應比對零次以上，才能成功符合字串「abb」與運算式 `\1b`。  它會將結果 "abb" 指派回到 `\1`。  
  
 在此範例中，`*` 是迴圈數量詞，它會重複評估直到規則運算式引擎無法符合其所定義的模式為止。  迴圈數量詞並不會清除群組定義。  
  
 如果群組沒有擷取任何子字串，該群組的反向參考會是未定義的，而且從來不會比對。  這由定義如下的規則運算式模式 `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b` 說明：  
  
|模式|說明|  
|--------|--------|  
|`\b`|開始字緣比對。|  
|`(\p{Lu}{2})`|比對兩個大寫字母。  這是第一個擷取群組。|  
|`(\d{2})?`|比對出現零次或一次的兩個十進位數字。  這是第二個擷取群組。|  
|`(\p{Lu}{2})`|比對兩個大寫字母。  這是第三個擷取群組。|  
|`\b`|結束字緣比對。|  
  
 輸入的字串可以符合這個規則運算式，即使不存在第二個擷取群組所定義的兩個十進位數字也是如此。  下列範例顯示即使比對成功，仍會在兩個成功的擷取群組之間找到空的擷取群組。  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
 [!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]  
  
## 請參閱  
 [規則運算式語言 \- 快速參考](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)