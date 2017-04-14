---
title: "規則運算式中的其他建構 | Microsoft Docs"
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
  - ".NET Framework 規則運算式, 其他建構"
  - "建構, 其他"
  - "規則運算式, 其他建構"
ms.assetid: 7d10d11f-680f-4721-b047-fb136316b4cd
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 規則運算式中的其他建構
.NET Framework 中的規則運算式包括三個其他的語言建構。  其中一個可讓您在規則運算式模式的中間，啟用或停用特定的比對選項。  剩餘兩個可讓您在規則運算式中包含註解。  
  
## 內嵌選項  
 您可以使用語法設定或停用部分規則運算式的特定模式比對選項  
  
```  
(?imnsx-imnsx)  
```  
  
 您在問號之後列出要啟用的選項，並在減號之後列出要停用的選項。  下表會說明每個選項。  如需每個選項的詳細資訊，請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)。  
  
|選項|說明|  
|--------|--------|  
|`i`|不區分大小寫的比對。|  
|`m`|多行模式，|  
|`n`|只有明確擷取。\(括號不會具有擷取群組的作用\)|  
|`s`|單行模式。|  
|`x`|忽略未逸出的空白字元，並允許 x 模式註解。|  
  
 `(?imnsx-imnsx)` 建構所定義規則運算式選項中的任何變更，其效果會一直維持到封入群組的結尾。  
  
> [!NOTE]
>  `(?imnsx-imnsx:`*subexpression*`)` 群組建構提供子運算式相同的功能。  如需詳細資訊，請參閱[群組建構](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)。  
  
 下列範例使用 `i`、 `n` 和 `x` 選項，在規則運算模式中啟用不區分大小寫和明確擷取，並略過規則運算式模式中的空白字元。  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous1.cs#1)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous1.vb#1)]  
  
 範例定義兩個規則運算式。  第一個 \(`\b(D\w+)\s(d\w+)\b`\) 符合以大寫「D」和小寫「d」開頭的兩個連續字組。  第二個規則運算式 \(`\b(D\w+)(?ixn) \s (d\w+) \b`\) 會使用內嵌選項來修改此模式，如下表所述。  結果的比較會確認 `(?ixn)` 建構的效果。  
  
|模式|說明|  
|--------|--------|  
|`\b`|從字緣開始。|  
|`(D\w+)`|比對後接一個或多個字組字元的大寫 "D"。  這是第一個擷取群組。|  
|`(?ixn)`|從這一刻起，進行不區分大小寫的比較，進行明確擷取，並呼略規則運算式模式中的空白字元。|  
|`\s`|比對空白字元。|  
|`(d\w+)`|比對後接一個或多個字組字元的大寫或小寫 "d"。  因為啟用 `n` \(明確擷取\) 選項，因此不會擷取此群組..|  
|`\b`|比對字緣。|  
  
## 內嵌註解  
 `(?#`  *comment* `)` 建構可讓您在規則運算式中包括內嵌註解。  規則運算式引擎不在模式比對中使用註解的任何一部分，雖然註解包含在 <xref:System.Text.RegularExpressions.Regex.ToString%2A?displayProperty=fullName> 方法所傳回的字串中。  註解會在第一個右括號結束。  
  
 下列範例會重複前一節範例中第一個規則運算式的模式。  它會將兩個內嵌註解加入規則運算式，以指示比較是否區分大小寫。  規則運算式模式 `\b((?# case-sensitive comparison)D\w+)\s((?#case-insensitive comparison)d\w+)\b` 的定義方式如下所示。  
  
|模式|說明|  
|--------|--------|  
|`\b`|從字緣開始。|  
|`(?# case-sensitive comparison)`|註解。  它並不會影響模式比對行為。|  
|`(D\w+)`|比對後接一個或多個字組字元的大寫 "D"。  這是第一個擷取群組。|  
|`\s`|比對空白字元。|  
|`(?ixn)`|從這一刻起，進行不區分大小寫的比較，進行明確擷取，並呼略規則運算式模式中的空白字元。|  
|`(?#case-insensitive comparison)`|註解。  它並不會影響模式比對行為。|  
|`(d\w+)`|比對後接一個或多個字組字元的大寫或小寫 "d"。  這是第二個擷取群組。|  
|`\b`|比對字緣。|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous2.cs#2)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous2.vb#2)]  
  
## 行結尾註解  
 數字符號 \(`#`\) 標記 x 模式註解，從未逸出的 \# 字元開始 \(位於規則運算式模式的結尾\)，並會繼續直到該行結束。  若要使用建構，您必須在執行個體化 <xref:System.Text.RegularExpressions.Regex> 物件或呼叫靜態 <xref:System.Text.RegularExpressions.Regex> 方法時啟用 `x` 選項 \(透過內嵌選項\)，或提供<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 值給 `option` 參數。  
  
 下列範例說明行結尾註解建構函式。  它會判斷字串是否為複合格式字串，其中包含至少一個格式項目。  下表說明規則運算式模式中的架構函式：  
  
 `\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item.`  
  
|模式|說明|  
|--------|--------|  
|`\{`|比對左大括號。|  
|`\d+`|比對一個或多個十進位數字。|  
|`(,-*\d+)*`|比對出現零次或一次的逗號，後接選擇性的減號，再後接一個或多個十進位數字。|  
|`(\:\w{1,4}?)*`|比對出現零次或一次的冒號，後接一個到四個空白字元，但盡可能要少量。|  
|`(?#case insensitive comparison)`|內嵌註解。  它並不會影響模式比對行為。|  
|`\}`|比對右邊的大括號。|  
|`(?x)`|啟用忽略模式空白字元選項，這樣即可辨認出行結尾註解。|  
|`# Looks for a composite format item.`|行結尾註解。|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous3.cs#3)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous3.vb#3)]  
  
 請注意，除了在規則運算式中提供 `(?x)` 建構，也可以藉由呼叫 <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=fullName> 方法，並將 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 列舉值傳遞給它以辨認註解。  
  
## 請參閱  
 [規則運算式語言 \- 快速參考](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)