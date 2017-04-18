---
title: "規則運算式選項 | Microsoft Docs"
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
  - "規則運算式選項"
  - "建構選項"
  - ".NET framework 規則運算式選項"
  - "內嵌選項建構"
  - "選項參數"
ms.assetid: c82dc689-7e82-4767-a18d-cd24ce5f05e9
caps.latest.revision: 27
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 27
---
# 規則運算式選項
<a name="Top"></a>根據預設，將輸入字串與規則運算式模式中任何常值字元的比較會區分大小寫、 規則運算式模式中的泛空白字元會解譯為常值的空格字元和規則運算式中的擷取群組命名隱含也明確。 您可以藉由指定規則運算式選項來修改這些預設規則運算式行為和幾個其他方面。 這些選項 (列示於下表) 可以內嵌為規則運算式模式的部分，或是提供給 <xref:System.Text.RegularExpressions.Regex?displayProperty=fullName> 類別建構函式或靜態模式比對方法，以作為 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 列舉值。  
  
|RegexOptions 成員|內嵌字元|作用|  
|-------------------------|----------------------|------------|  
|<xref:System.Text.RegularExpressions.RegexOptions>|無法使用|使用預設行為。 如需詳細資訊，請參閱[預設選項](#Default)。|  
|<xref:System.Text.RegularExpressions.RegexOptions>|`i`|使用不區分大小寫的比對方式。 如需詳細資訊，請參閱[不區分大小寫比對](#Case)。|  
|<xref:System.Text.RegularExpressions.RegexOptions>|`m`|使用多行模式，其中 `^` 和 `$` 會比對每一行的開頭與結尾 (而不是輸入字串的開頭和結尾)。 如需詳細資訊，請參閱[多行模式](#Multiline)。|  
|<xref:System.Text.RegularExpressions.RegexOptions>|`s`|使用單行模式，其中句點 (.) 會比對每個字元 (而不是 `\n` 以外的每個字元)。 如需詳細資訊，請參閱[單行模式](#Singleline)。|  
|<xref:System.Text.RegularExpressions.RegexOptions>|`n`|不擷取未命名的群組。 明確命名或編號群組表單的唯一有效的擷取`(?<`*名稱*`>` *subexpression*`)`。 如需詳細資訊，請參閱[僅明確擷取](#Explicit)。|  
|<xref:System.Text.RegularExpressions.RegexOptions>|無法使用|將規則運算式編譯為組件。 如需詳細資訊，請參閱[編譯的規則運算式](#Compiled)。|  
|<xref:System.Text.RegularExpressions.RegexOptions>|`x`|在模式中排除未逸出的空白字元，並且在數字符號 (`#`) 後面啟用註解。 如需詳細資訊，請參閱[忽略空白字元](#Whitespace)。|  
|<xref:System.Text.RegularExpressions.RegexOptions>|無法使用|變更搜尋方向。 搜尋方向為由右至左，而不是由左至右。 如需詳細資訊，請參閱[由右至左模式](#RightToLeft)。|  
|<xref:System.Text.RegularExpressions.RegexOptions>|無法使用|為運算式啟用符合 ECMAScript 的行為。 如需詳細資訊，請參閱 [ECMAScript 相符行為](#ECMAScript)。|  
|<xref:System.Text.RegularExpressions.RegexOptions>|無法使用|忽略語言中的文化特性差異。 如需詳細資訊，請參閱[使用不因國別而異的文化特性比較](#Invariant)。|  
  
## <a name="specifying-the-options"></a>指定選項  
 指定規則運算式選項的方式有三種：  
  
-   在`options`參數<xref:System.Text.RegularExpressions.Regex?displayProperty=fullName>類別建構函式或靜態 (`Shared`在 Visual Basic 中) 模式比對方法，例如<xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=fullName>或<xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=fullName>。 `options`參數是位元 OR 組合的<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>列舉值。  
  
     選項會提供給<xref:System.Text.RegularExpressions.Regex>所使用的執行個體`options`類別建構函式的參數，指派給<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>屬性。 不過，<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 屬性不會在規則運算式模式中反映內嵌選項。  
  
     下列範例提供一個實例。 它會使用`options`參數<xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=fullName>方法來啟用不區分大小寫的比對，並識別以字母"d"開頭的文字時，忽略模式空白字元。  
  
     [!code-csharp[Conceptual.Regex.Language.Options#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#6)]
     [!code-vb[Conceptual.Regex.Language.Options#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#6)]  
  
-   使用語法 `(?imnsx-imnsx)`，在規則運算式模式中套用內嵌選項。 此選項會從定義選項的位置開始套用至模式，直到模式結尾，或是有其他內嵌選項取消定義選項為止。 請注意，<xref:System.Text.RegularExpressions.Regex> 執行個體的 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 屬性 不會反映這些內嵌選項。 如需詳細資訊，請參閱[其他建構](../../../docs/standard/base-types/miscellaneous-constructs-in-regular-expressions.md)主題。  
  
     下列範例提供一個實例。 其使用內嵌選項來啟用不區分大小寫比對，並且在識別以字母 "d" 開頭的文字時，忽略模式空白字元。  
  
     [!code-csharp[Conceptual.Regex.Language.Options#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#7)]
     [!code-vb[Conceptual.Regex.Language.Options#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#7)]  
  
-   在語法與規則運算式模式的特定群組中套用內嵌選項建構`(?imnsx-imnsx:` *subexpression*`)`。 如果選項集前面沒有符號，會開啟選項集；如果選項集前面有減號，則會關閉選項集。 (`?` 是語言建構語法的固定部分，無論啟用或停用選項，都需要此部分。)此選項僅適用於該群組。 如需詳細資訊，請參閱[群組建構](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)。  
  
     下列範例提供一個實例。 其使用群組建構中的內嵌選項來啟用不區分大小寫比對，並且在識別以字母 "d" 開頭的文字時，忽略模式空白字元。  
  
     [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
     [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]  
  
 如果將選項指定為內嵌，選項或選項集前面的減號 (`-`) 會關閉那些選項。 例如，內嵌建構`(?ix-ms)`開啟<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>和<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>選項，並關閉<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>和<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>選項。 依預設，會關閉所有規則運算式選項。  
  
> [!NOTE]
>  如果建構函式或方法呼叫的 `options` 參數指定的規則運算式選項，與規則運算式模式中指定內嵌的選項相衝突，則會使用內嵌選項。  
  
 選項參數和內嵌都可以用來設定下列五個規則運算式選項：  
  
-   <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>  
  
 下列五個規則運算式選項可以用 `options` 參數來設定，但不能設定內嵌：  
  
-   <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>  
  
## <a name="determining-the-options"></a>決定選項  
 您可以判定，在擷取唯讀 <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=fullName> 屬性的值來將物件具現化時，提供了哪些選項給 <xref:System.Text.RegularExpressions.Regex> 物件。 這個屬性是適合用來決定所建立之編譯規則運算式所定義的選項<xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=fullName>方法。  
  
 若要測試任何選項 (<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 除外) 是否存在，請使用 <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=fullName> 屬性的值和您感興趣的 <xref:System.Text.RegularExpressions.RegexOptions> 值來執行 AND 作業。 然後測試結果是否等於 <xref:System.Text.RegularExpressions.RegexOptions> 值。 下列範例會測試是否已設定 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 選項。  
  
 [!code-csharp[Conceptual.Regex.Language.Options#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#19)]
 [!code-vb[Conceptual.Regex.Language.Options#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#19)]  
  
 若要測試的<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>，判斷是否值<xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=fullName>屬性等於<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>，如下列範例所示。  
  
 [!code-csharp[Conceptual.Regex.Language.Options#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#20)]
 [!code-vb[Conceptual.Regex.Language.Options#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#20)]  
  
 以下各節會列出 .NET Framework 中的規則運算式所支援的選項。  
  
<a name="Default"></a>   
## <a name="default-options"></a>預設選項  
 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 選項指出未指定任何選項，而規則運算式引擎使用其預設行為。 其中包括下列項目：  
  
-   模式被解譯為標準規則運算式，而不是 ECMAScript 規則運算式。  
  
-   在輸入字串中，由左至右比對規則運算式模式。  
  
-   比較會區分大小寫。  
  
-   `^` 和 `$` 語言項目會比對輸入字串的開頭和結尾。  
  
-   `.` 語言項目會比對 `\n` 以外的每個字元。  
  
-   規則運算式模式中的任何空白字元會被解譯成常值空白字元。  
  
-   將模式與輸入字串比較時，會使用目前文化特性的慣例。  
  
-   規則運算式模式中的擷取群組是隱含的，也是明確的。  
  
> [!NOTE]
>  <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 選項沒有內嵌對等項目。 將規則運算式選項套用為內嵌時，會關閉特定選項，依據各選項逐一還原預設行為。 例如，`(?i)` 會開啟不區分大小寫比較，而 `(?-i)` 會還原預設區分大小寫比較。  
  
 因為 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 選項代表規則運算式引擎的預設行為，所以很少明確地指定在方法呼叫中， 而是會呼叫不含 `options` 參數的建構函式或靜態模式比對方法。  
  
 [回到頁首](#Top)  
  
<a name="Case"></a>   
## <a name="case-insensitive-matching"></a>不區分大小寫比對  
 <xref:System.Text.RegularExpressions.RegexOptions>選項，或`i`內嵌選項，提供不區分大小寫的比對。 依預設，會使用目前文化特性的大小寫慣例。  
  
 下列範例定義規則運算式模式 `\bthe\w*\b`，它會比對以 "the" 開頭的所有文字。 因為第一次呼叫<xref:System.Text.RegularExpressions.Regex.Match%2A>方法是使用預設的區分大小寫比較，輸出會指出不相符 開頭的字串"The"句子。 選項設為 <xref:System.Text.RegularExpressions.RegexOptions> 來呼叫 <xref:System.Text.RegularExpressions.Regex.Match%2A> 方法時，才會加以比對。  
  
 [!code-csharp[Conceptual.Regex.Language.Options#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case1.cs#1)]
 [!code-vb[Conceptual.Regex.Language.Options#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case1.vb#1)]  
  
 下列範例會修改上一個範例中的規則運算式模式，改為使用內嵌選項，而不是使用 `options` 參數，以提供不區分大小寫比較。 第一個模式在群組建構中定義不區分大小寫選項，只套用於字串 "the" 中的字母 "t"。 因為選項建構出現在模式開頭，所以第二個模式會將不區分大小寫選項套用於整個規則運算式。  
  
 [!code-csharp[Conceptual.Regex.Language.Options#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case2.cs#2)]
 [!code-vb[Conceptual.Regex.Language.Options#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case2.vb#2)]  
  
 [回到頁首](#Top)  
  
<a name="Multiline"></a>   
## <a name="multiline-mode"></a>多行模式  
 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>選項，或`m`內嵌選項，可讓規則運算式引擎處理構成多行輸入的字串。 它會變更 `^` 和 `$` 語言項目的解譯，以便比對字行的開頭和結尾，而不是輸入字串的開頭和結尾。  
  
 依預設，`$` 只會比對輸入字串的結尾。 如果您指定<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>選項時，它會比對新行字元 (`\n`) 或輸入字串的結尾。 不過，並不會比對歸位字元/換行字元組合。 若要順利比對，請使用子運算式 `\r?$`，而不只是使用 `$`。  
  
 下列範例會擷取保齡球名字和分數，並將它們加入至<xref:System.Collections.Generic.SortedList%602>以遞減順序排序的集合。</TKey, TValue> 呼叫 <xref:System.Text.RegularExpressions.Regex.Matches%2A> 方法兩次。 在第一次呼叫方法時，規則運算式為 `^(\w+)\s(\d+)$`，且沒有設定選項。 如輸出所示，因為規則運算式引擎無法隨著輸入字串的開頭和結尾來比對輸入模式，所以沒有找到相符項目。 在第二次呼叫方法時，規則運算式變更為 `^(\w+)\s(\d+)\r?$`，且選項設為 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>。 如輸出所示，已成功比對名字和分數，且分數以遞減順序顯示。  
  
 [!code-csharp[Conceptual.Regex.Language.Options#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline1.cs#3)]
 [!code-vb[Conceptual.Regex.Language.Options#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline1.vb#3)]  
  
 規則運算式模式 `^(\w+)\s(\d+)\r*$` 的定義如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`^`|從字行開頭開始。|  
|`(\w+)`|比對一個或多個文字字元。 這是第一個擷取群組。|  
|`\s`|比對空白字元。|  
|`(\d+)`|比對一個或多個十進位數字。 這是第二個擷取群組。|  
|`\r?`|比對零或一個歸位字元。|  
|`$`|在字行結尾結束。|  
  
 下列範例與上一個範例相同，只是下列範例是使用內嵌選項 `(?m)` 來設定多行選項。  
  
 [!code-csharp[Conceptual.Regex.Language.Options#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline2.cs#4)]
 [!code-vb[Conceptual.Regex.Language.Options#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline2.vb#4)]  
  
 [回到頁首](#Top)  
  
<a name="Singleline"></a>   
## <a name="single-line-mode"></a>單行模式  
 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>選項，或`s`內嵌選項會使規則運算式引擎將輸入的字串當作其包含單行。 其作法是變更句點 (`.`) 語言項目的行為，使其比對每個字元，而不是比對新行字元 `\n` 或 \u000A 以外的每個字元。  
  
 下列範例說明如何的行為`.`語言項目變更，當您使用<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>選項。 規則運算式 `^.+` 會從字串開頭開始，比對每一個字元。 根據預設，比對會在第一行結尾結束。規則運算式模式會比對歸位字元 `\r` 或 \u000D，但不會比對 `\n`。 因為<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>選項會解譯成單一線條的整個輸入的字串，它會比對輸入字串中的每個字元包括`\n`。  
  
 [!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
 [!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]  
  
 下列範例與上一個範例相同，只是下列範例是使用內嵌選項 `(?s)` 來啟用單行模式。  
  
 [!code-csharp[Conceptual.Regex.Language.Options#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/singleline1.cs#5)]
 [!code-vb[Conceptual.Regex.Language.Options#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/singleline1.vb#5)]  
  
 [回到頁首](#Top)  
  
<a name="Explicit"></a>   
## <a name="explicit-captures-only"></a>僅明確擷取  
 依預設，擷取群組的定義方式是在規則運算式模式中使用括號。 具名的群組指派名稱或編號`(?<`*名稱*`>`*subexpression* `)`語言選項，而未具名的群組是由索引存取。 在 <xref:System.Text.RegularExpressions.GroupCollection> 物件中，未具名群組的前面是具名群組。  
  
 群組建構通常只用來將數量詞套用至多個語言項目，我們對所擷取的子字串並不感興趣。 例如，如果下列運算式：  
  
```  
\b\(?((\w+),?\s?)+[\.!?]\)?  
```  
  
 目的只是要從文件中擷取以句點、驚嘆號或問號結尾的句子，則我們只對所產生的句子 (由 <xref:System.Text.RegularExpressions.Match> 物件代表) 感興趣。 我們對集合中的個別文字並不感興趣。  
  
 非後續使用的擷取群組可能會耗用很多資源，因為規則運算式引擎必須同時填入 <xref:System.Text.RegularExpressions.GroupCollection> 和 <xref:System.Text.RegularExpressions.CaptureCollection> 集合物件。 或者，您也可以使用<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>選項或`n`內嵌選項，指定唯一有效的擷取是明確命名或編號群組所指定的`(?<`*名稱*`>` *subexpression* `)`建構。  
  
 下列範例顯示，當呼叫 <xref:System.Text.RegularExpressions.Regex.Match%2A> 方法時，如果沒有使用 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 選項，`\b\(?((\w+),?\s?)+[\.!?]\)?` 規則運算式模式所傳回的比對相關資訊。 當第一個方法呼叫的輸出顯示時，規則運算式引擎會以擷取子字串的相關資訊完整填入 <xref:System.Text.RegularExpressions.GroupCollection> 和 <xref:System.Text.RegularExpressions.CaptureCollection> 集合物件。 因為第二個方法呼叫時`options`設<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>，所以沒有擷取群組的詳細資訊。  
  
 [!code-csharp[Conceptual.Regex.Language.Options#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit1.cs#9)]
 [!code-vb[Conceptual.Regex.Language.Options#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit1.vb#9)]  
  
 規則運算式模式`\b\(?((?>\w+),?\s?)+[\.!?]\)?`下表所示加以定義。  
  
|模式|描述|  
|-------------|-----------------|  
|`\b`|從字邊界開始。|  
|`\(?`|比對出現零或一次的左括號 ("(")。|  
|`(?>\w+),?`|比對後面接著零或一個逗號的一或多個文字字元。 比對文字字元時，請勿回溯。|  
|`\s?`|比對零個或一個空白字元。|  
|`((\w+),?\s?)+`|一或多次比對一或多個文字字元、零或一個逗號及零或一個空白字元的組合。|  
|`[\.!?]\)?`|比對這三種標點符號中的任一種，後面接零或一個右括號 (")")。|  
  
 您也可以使用 `(?n)` 內嵌元素來隱藏自動擷取。 下列範例會修改上一個規則運算式模式使用`(?n)`內嵌項目，而不是<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>選項。  
  
 [!code-csharp[Conceptual.Regex.Language.Options#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit2.cs#10)]
 [!code-vb[Conceptual.Regex.Language.Options#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit2.vb#10)]  
  
 最後，您可以使用內嵌群組項目 `(?n:)`，針對每個群組逐一隱藏自動擷取。 下列範例會修改上一個模式，以隱藏外部群組 `((?>\w+),?\s?)` 中的未具名擷取。 請注意，這也會隱藏內部群組中的未具名擷取。  
  
 [!code-csharp[Conceptual.Regex.Language.Options#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit3.cs#11)]
 [!code-vb[Conceptual.Regex.Language.Options#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit3.vb#11)]  
  
 [回到頁首](#Top)  
  
<a name="Compiled"></a>   
## <a name="compiled-regular-expressions"></a>編譯的規則運算式  
 依預設，會解譯 .NET Framework 中的規則運算式。 將 <xref:System.Text.RegularExpressions.Regex> 物件具現化，或是呼叫靜態 <xref:System.Text.RegularExpressions.Regex> 方法時，會將規則運算式模式剖析成一組自訂作業碼，而解譯器會使用這些作業碼來執行規則運算式。 這需要有所取捨：要將初始化規則運算式引擎的成本降到最低，就會犧牲執行時期效能。  
  
 您可以使用 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 選項，以編譯的規則運算式來取代解譯的規則運算式。 在這個情況下，將模式傳遞至規則運算式時，會將該模式剖析成一組自訂作業碼，然後再轉換成 Microsoft 中繼語言 (MSIL)，可直接傳遞至通用語言執行平台。 編譯的規則運算式可充分提升執行時期效能，但會犧牲初始化時間。  
  
> [!NOTE]
>  可以編譯規則運算式，只是藉由提供<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>值`options`參數<xref:System.Text.RegularExpressions.Regex>類別建構函式或靜態模式比對方法。 無法以內嵌選項來提供此值。  
  
 在呼叫靜態和執行個體規則運算式時，都可以使用編譯的規則運算式。 在靜態規則運算式， <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>選項傳遞至`options`規則運算式模式比對方法的參數。 在執行個體規則運算式，它會傳遞至`options`參數<xref:System.Text.RegularExpressions.Regex>類別建構函式。 在這兩個情況中，都會增強效能。  
  
 不過，只有在下列條件下，效能才會提升：  
  
-   在對規則運算式模式比對方法的多個呼叫中，都會使用代表特定規則運算式的 <xref:System.Text.RegularExpressions.Regex> 物件。  
  
-   <xref:System.Text.RegularExpressions.Regex> 物件不能超出範圍，因此可以重複使用。  
  
-   在對規則運算式模式比對方法的多個呼叫中，會使用靜態規則運算式。 (效能提升是有可能的，因為規則運算式引擎會快取靜態方法呼叫中所使用的規則運算式。)  
  
> [!NOTE]
>  <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>選項無關<xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=fullName>方法，它會建立特殊用途的組件包含預先定義的已編譯規則運算式。  
  
 [回到頁首](#Top)  
  
<a name="Whitespace"></a>   
## <a name="ignore-white-space"></a>忽略空白字元  
 依預設，規則運算式模式中的空白字元很重要；它會強制規則運算式引擎比對輸入字串中的空白字元。 因此，規則運算式"`\b\w+\s`"和"`\b\w+` "是大致相等的規則運算式。 此外，在規則運算式模式中遇到數字符號 (#) 時，會將其解譯成常值字元，以供比對。  
  
 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>選項，或`x`內嵌選項，變更此預設行為，如下所示︰  
  
-   規則運算式模式中未逸出的空白字元會被忽略。 若要在規則運算式模式，必須逸出空白字元 (例如`\s`或 「`\` 」)。  
  
-   數字符號 (#) 會解譯成註解的開頭，而不是常值字元。 規則運算式模式中，從 # 字元到字串結尾的所有文字會被解譯成註解。  
  
 不過，在下列案例中，即使您使用 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 選項，也不會忽略規則運算式中的空白字元：  
  
-   字元類別中的空白字元一律解譯為常值。 例如，規則運算式模式 `[ .,;:]` 會比對任何單一空白字元、句點、逗號、分號或冒號。  
  
-   White space isn't allowed within a bracketed quantifier, such as `{`*n*`}`, `{`*n*`,}`, and `{`*n*`,`*m*`}`. 例如，規則運算式模式 `\d{1. 3}` 無法比對從一到三位數的任何數字序列，因為其中包含空白字元。  
  
-   引進語言項目的字元序列中，不允許空白字元。 例如：  
  
    -   語言項目`(?:`*子運算式*`)`代表非擷取群組，而`(?:`部分的項目不能有內嵌空格。 模式`(? :`*子運算式*`)`會擲回<xref:System.ArgumentException>在執行時間，因為規則運算式引擎無法剖析該模式，而模式`( ?:` *subexpression* `)`無法比對*子運算式*。  
  
    -   語言項目`\p{`*名稱*`}`，代表 Unicode 類別或具名資料區塊，不能包含內嵌的空格中`\p{`的部分。 如果包含空白字元，則此項目會在執行時期擲回 <xref:System.ArgumentException>。  
  
 啟用此選項有助於簡化通常很難剖析及了解的規則運算式。 其增進了可讀性，並且讓規則運算式可以被記載下來。  
  
 下列範例定義下列規則運算式模式：  
  
 `\b \(? ( (?>\w+) ,?\s? )+  [\.!?] \)? # Matches an entire sentence.`  
  
 此模式類似[僅明確擷取](#Explicit)一節中定義的模式，只是其使用 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 選項來忽略模式空白字元。  
  
 [!code-csharp[Conceptual.Regex.Language.Options#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace1.cs#12)]
 [!code-vb[Conceptual.Regex.Language.Options#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace1.vb#12)]  
  
 下列範例使用內嵌選項 `(?x)` 來忽略模式空白字元。  
  
 [!code-csharp[Conceptual.Regex.Language.Options#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace2.cs#13)]
 [!code-vb[Conceptual.Regex.Language.Options#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace2.vb#13)]  
  
 [回到頁首](#Top)  
  
<a name="RightToLeft"></a>   
## <a name="right-to-left-mode"></a>由右至左模式  
 依預設，規則運算式引擎會由左至右搜尋。 您可以使用 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 選項來反轉搜尋方向。 此搜尋會自動從字串最後一個字元的位置開始。 針對包含開始位置參數的模式比對方法，例如 <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.Int32%29?displayProperty=fullName>，開始位置是要開始搜尋之最右邊字元位置的索引。  
  
> [!NOTE]
>  由右至左模式，就可以使用僅提供<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>值`options`參數<xref:System.Text.RegularExpressions.Regex>類別建構函式或靜態模式比對方法。 無法以內嵌選項來提供此值。  
  
 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 選項只會變更搜尋方向，並不會由右至左解譯規則運算式模式。 例如，規則運算式 `\bb\w+\s` 會比對字母 "b" 開頭、後接空白字元的文字。 在下列範例中，輸入字串是由包含一或數個 "b" 字元的三個單字所組成。 第一個單字以 "b" 開頭，第二個單字以 "b" 結尾，而第三個單字中間包含兩個 "b" 字元。 如範例輸出所示，只有第一個單字符合規則運算式模式。  
  
 [!code-csharp[Conceptual.Regex.Language.Options#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft1.cs#17)]
 [!code-vb[Conceptual.Regex.Language.Options#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft1.vb#17)]  
  
 另外請注意，右合樣判斷提示 ( `(?=` *subexpression* `)`語言項目) 和左合樣判斷提示 ( `(?<=`*子運算式*`)`語言項目) 沒有變更方向。 右合樣判斷提示朝右看，而左合樣判斷提示朝左看。 例如，規則運算式 `(?<=\d{1,2}\s)\w+,?\s\d{4}` 使用左合樣判斷提示來測試月份名稱前面的日期。 然後規則運算式會比對月和年。 如需右合樣和左合樣 assertsions 資訊，請參閱[群組建構](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)。  
  
 [!code-csharp[Conceptual.Regex.Language.Options#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft2.cs#18)]
 [!code-vb[Conceptual.Regex.Language.Options#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft2.vb#18)]  
  
 規則運算式模式的定義如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`(?<=\d{1,2}\s)`|相符項目的開頭前面必須要有一個或兩個十進位數字後接空格。|  
|`\w+`|比對一個或多個文字字元。|  
|`,?`|比對零或一個逗號字元。|  
|`\s`|比對空白字元。|  
|`\d{4}`|比對四個十進位數字。|  
  
 [回到頁首](#Top)  
  
<a name="ECMAScript"></a>   
## <a name="ecmascript-matching-behavior"></a>ECMAScript 相符行為  
 依預設，在比對規則運算式模式與輸入文字時，規則運算式引擎會使用標準行為。 不過，您可以指定 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 選項，以指示規則運算式引擎使用 ECMAScript 相符行為。  
  
> [!NOTE]
>  符合 ECMAScript 的行為，就可以使用僅提供<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>值`options`參數<xref:System.Text.RegularExpressions.Regex>類別建構函式或靜態模式比對方法。 無法以內嵌選項來提供此值。  
  
 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 選項只能結合 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 和 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 選項。 在規則運算式中使用任何其他選項將會導致 <xref:System.ArgumentOutOfRangeException>。  
  
 ECMAScript 的行為與標準規則運算式有三個不同層面：字元類別語法、自我參考擷取群組，以及八進位與反向參考解譯。  
  
-   字元類別語法。 因為標準規則運算式支援 Unicode，而 ECMAScript 不支援，所以 ECMAScript 中的字元類別有較多的語法限制，而且有些字元類別語言項目有不同的意義。 例如，ECMAScript 不支援語言項目 (例如 Unicode 類別) 或資料區塊項目 `\p` 和 `\P`。 同樣地，使用 ECMAScript 時，`\w` 項目 (用來比對文字字元) 同等於 `[a-zA-Z_0-9]` 字元類別，使用標準行為時，同等於 `[\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]`。 如需詳細資訊，請參閱[字元類別](../../../docs/standard/base-types/character-classes-in-regular-expressions.md)。  
  
     下列範例說明標準與 ECMAScript 模式比對之間的差異。 其定義規則運算式 `\b(\w+\s*)+`，可比對後接空白字元的文字。 該輸入包含兩個字串，一個使用 Latin 字元集，另一個使用 Cyrillic 字元集。 如輸出所示，呼叫使用 ECMAScript 比對的 <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=fullName> 方法時，無法比對 Cyrillic 文字，而使用標準比對的方法呼叫則可比對這些文字。  
  
     [!code-csharp[Conceptual.Regex.Language.Options#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript1.cs#16)]
     [!code-vb[Conceptual.Regex.Language.Options#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript1.vb#16)]  
  
-   自我參考擷取群組。 具有自我反向參考的規則運算式擷取類別必須以每個擷取反覆項目來更新。 如下列範例所示，使用 ECMAScript 時，此功能可讓規則運算式 `((a+)(\1) ?)+` 比對輸入字串 " aa aaaa aaaaaa "，使用標準比對時則不能。  
  
     [!code-csharp[Conceptual.Regex.Language.Options#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript2.cs#21)]
     [!code-vb[Conceptual.Regex.Language.Options#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript2.vb#21)]  
  
     規則運算式的定義如下表所示。  
  
    |模式|描述|  
    |-------------|-----------------|  
    |(a+)|比對字母 "a" 一次或多次。 這是第二個擷取群組。|  
    |(\1)|比對第一個擷取群組所擷取的子字串。 這是第三個擷取群組。|  
    |?|比對零或一個空白字元。|  
    |((a+)(\1) ?)+|一次或多次比對一個或多個 "a" 字元，後面接符合第一個擷取群組的字串，後面再接零或一個空白字元。 這是第一個擷取群組。|  
  
-   八進位逸出與反向參考之間模棱兩可的解決方案。 下表總結以標準和 ECMAScript 規則運算式來進行八進位與反向參考解譯的差異。  
  
    |規則運算式|標準行為|ECMAScript 行為|  
    |------------------------|------------------------|-------------------------|  
    |`\0` 後接 0 到 2 個八進位數字|解譯成八進位。 例如，`\044` 一律解譯成八進位值，且意思是 "$"。|相同行為。|  
    |`\` 後接 1 到 9 的數字，後面不再接其他十進位數字。|解譯成反向參考。 例如，`\9` 一律表示反向參考 9，即使第 9 個擷取群組不存在也一樣。 如果擷取群組不存在，規則運算式剖析器會擲回<xref:System.ArgumentException>。|如果單一十進位數字擷取群組存在，則反向參考至該數字。 否則，會將該值解譯成常值。|  
    |`\` 後接 1 到 9 的數字，後面再接其他十進位數字。|將這些數字解譯成十進位值。 如果該擷取群組存在，則將運算式解譯成反向參考。<br /><br /> 否則，解譯前置八進位數字至八進位 377；也就是說，僅考慮該值的低 8 位元。 將其餘數字解譯成常值。 例如，在運算式 `\3000` 中，如果擷取群組 300 存在，則解譯成反向參考 300；如果擷取群組 300 不存在，則解譯成八進位 300 後接 0。|盡可能將多位數字轉換成可以參考擷取的十進位值，以解譯成反向參考。 如果沒有數字可供轉換，則使用前置八進位數字至八進位 377，以解譯成八進位；將其餘數字解譯成常值。|  
  
 [回到頁首](#Top)  
  
<a name="Invariant"></a>   
## <a name="comparison-using-the-invariant-culture"></a>使用不因國別而異的文化特性比較  
 依預設，當規則運算式引擎執行不區分大小寫比較時，會使用目前文化特性的大小寫慣例來判定相等的大小寫字元。  
  
 不過，某些類型的比較並不希望有此行為，尤其是將使用者輸入與系統資源名稱 (例如密碼、檔案或 URL) 做比較時。 下列範例說明這種案例。 程式碼用來封鎖存取的 URL 前面加上任何資源**FILE://**。 規則運算式使用規則運算式 `$FILE://`，嘗試不區分大小寫來比對字串。 不過，當目前系統文化特性為 tr-TR (Turkish-Turkey) 時，"I" 並不是 "i" 的相等大寫字元。 如此一來，呼叫<xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=fullName>方法會傳回`false`，並允許存取檔案。  
  
 [!code-csharp[Conceptual.Regex.Language.Options#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#14)]
 [!code-vb[Conceptual.Regex.Language.Options#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#14)]  
  
> [!NOTE]
>  如需區分大小寫和使用不因國別而異的文化特性之字串比較的詳細資訊，請參閱[在 .NET Framework 中使用字串的最佳作法](../../../docs/standard/base-types/best-practices-strings.md)。  
  
 您可以不要使用不因國別而異的文化特性的不區分大小寫比較，而是指定 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 選項來忽略語言中的文化特性差異，並使用不因國別而異的文化特性的慣例。  
  
> [!NOTE]
>  使用文化特性而異的比較，就可以使用僅提供<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>值`options`參數<xref:System.Text.RegularExpressions.Regex>類別建構函式或靜態模式比對方法。 無法以內嵌選項來提供此值。  
  
 下列範例與上一個範例相同，差別在於呼叫靜態 <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=fullName> 方法時，是使用包含 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 的選項。 即使目前的文化特性設為 Turkish (Turkey)，規則運算式引擎還是可以成功比對 "FILE" 和 "file"，並封鎖存取檔案資源。  
  
 [!code-csharp[Conceptual.Regex.Language.Options#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#15)]
 [!code-vb[Conceptual.Regex.Language.Options#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#15)]  
  
## <a name="see-also"></a>另請參閱  
 [規則運算式語言-快速參考](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)