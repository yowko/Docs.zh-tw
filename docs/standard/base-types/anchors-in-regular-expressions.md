---
title: 規則運算式中的錨點
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- atomic zero-width assertions
- regular expressions, anchors
- regular expressions, atomic zero-width assertions
- anchors, in regular expressions
- metacharacters, atomic zero-width assertions
- metacharacters, anchors
- .NET Framework regular expressions, anchors
- .NET Framework regular expressions, atomic zero-width assertions
ms.assetid: 336391f6-2614-499b-8b1b-07a6837108a7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2cbf0ceb7d5f8e56955f8989e5eb4efba99540bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="anchors-in-regular-expressions"></a>規則運算式中的錨點
<a name="top"></a> 錨點或不可部分完成的無寬度判斷提示會指定字串中必須比對的位置。 當您在搜尋運算式中使用錨點時，規則運算式引擎不會在字串中前進或使用字元；它只會尋找指定位置中的相符項目。 例如， `^` 指定必須從行首或字串的開頭開始比對。 因此，僅當行首出現 "http:" 時，規則運算式 `^http:` 才會與其相符。 下表列出 .NET 中此規則運算式所支援的錨點。  
  
|錨點|描述|  
|------------|-----------------|  
|`^`|比對必須發生在字串的開頭或行首。 如需詳細資訊，請參閱 [字串開頭或行首](#Start)。|  
|`$`|比對必須發生在字串結尾或行尾，或是發生在字串結尾或行尾的 `\n` 之前。 如需詳細資訊，請參閱 [字串結尾或行尾](#End)。|  
|`\A`|比對只能發生在字串的開頭 (不支援多行)。 如需詳細資訊，請參閱 [僅字串開頭](#StartOnly)。|  
|`\Z`|比對必須發生在字串結尾，或發生在字串結尾的 `\n` 之前。 如需詳細資訊，請參閱 [字串結尾或結束新行之前](#EndOrNOnly)。|  
|`\z`|比對只能發生在字串結尾。 如需詳細資訊，請參閱 [僅字串結尾](#EndOnly)。|  
|`\G`|比對必須從上一個比對結束的位置開始。 如需詳細資訊，請參閱 [連續比對](#Contiguous)。|  
|`\b`|比對必須發生在字邊界上。 如需詳細資訊，請參閱 [字邊界](#WordBoundary)。|  
|`\B`|比對不可發生在字邊界上。 如需詳細資訊，請參閱 [非字邊界](#NonwordBoundary)。|  
  
<a name="Start"></a>   
## <a name="start-of-string-or-line-"></a>字串開頭或行首：^  
 `^` 錨點可讓您指定下列模式必須從字串的第一個字元位置開始。 如果您將 `^` 與 <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> 選項搭配使用 (請參閱[規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md))，則比對必須發生在每一行的行首。  
  
 下列範例會在規則運算式中使用 `^` 錨點，該規則運算式會擷取與某些職業棒球隊存在期間年份相關的資訊。 此範例會呼叫 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> 方法的兩個多載：  
  
-   在符合規則運算式模式的輸入字串中，對 <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29> 多載的呼叫只會尋找其中的第一個子字串。  
  
-   對 <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29> 參數的呼叫 (`options` 參數設為 <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>) 會尋找所有五個子字串。  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring1.vb#1)]  
  
 規則運算式模式 `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+` 的定義如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`^`|開始在輸入字串的開頭比對 (如果是使用 <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> 選項來呼叫此方法，則從行首開始比對)。|  
|`((\w+(\s?)){2,}`|比對一個或多個文字字元，後面接零，或接一個空格剛好兩次。 這是第一個擷取群組。 此運算式也定義了第二個和第三個擷取群組：第二個包含所擷取的文字，第三個則包含擷取到的空格。|  
|`,\s`|比對後面接著空白字元的逗號。|  
|`(\w+\s\w+)`|比對一或多個文字字元，後面接空格，再接一或多個文字字元。 這是第四個擷取群組。|  
|`,`|比對逗號。|  
|`\s\d{4}`|比對後面接著四個十進位數字的空格。|  
|<code>(-(\d{4}&#124;present))?</code>|比對出現零次或一次的連字號，後面接著四個十進位數字或字串 "present"。 這是第六個擷取群組。 它也包括第七個擷取群組。|  
|`,?`|比對出現零次或一次的逗號。|  
|<code>(\s\d{4}(-(\d{4}&#124;present))?,?)+</code>|比對出現一或多次的下列項目：空格、四個十進位數字、出現零或一次的連字號 (該連字號後面接著四個十進位數字或字串 "present")，以及零或一個逗號。 這是第五個擷取群組。|  
  
 [回到頁首](#top)  
  
<a name="End"></a>   
## <a name="end-of-string-or-line-"></a>字串結尾或行尾：$  
 `$` 錨點指定前述的模式必須發生在輸入字串的結尾，或輸入字串結尾的 `\n` 之前。  
  
 如果您將 `$` 與 <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> 選項搭配使用，則該比對也會在行尾發生。 請注意， `$` 會比對 `\n` ，但不會比對 `\r\n` (歸位字元與新行字元的組合，亦即 CR/LF)。 若要比對 CR/LF 字元組合，請在規則運算式模式中包含 `\r?$` 。  
  
 下列範例會將 `$` 錨點加入 [字串開頭或行首](#Start) 一節中範例所使用的規則運算式模式。 當與原始的輸入字串 (包括五行文字) 搭配使用時，<xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> 方法會找不到相符項目，因為第一行的結尾不符合 `$` 模式。 當原始的輸入字串分割成字串陣列時，<xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%29?displayProperty=nameWithType> 方法會成功地比對這五行。 當呼叫 <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> 方法且 `options` 參數設定為 <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> 時，會找不到相符項目，因為規則運算式模式並不考慮歸位字元項目 (\u+000D)。 不過，在將 `$` 取代為 `\r?$` 來修改規則運算式模式時，將 `options` 參數再次設定為 <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> 來呼叫 <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> 方法，則會找出五個相符項目。  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring1.vb#2)]  
  
 [回到頁首](#top)  
  
<a name="StartOnly"></a>   
## <a name="start-of-string-only-a"></a>僅字串開頭：\A  
 `\A` 錨點指定比對必須發生在輸入字串的開頭。 它與 `^` 錨點相同，不同處在於 `\A` 會忽略 <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> 選項。 因此，它可以只比對多行輸入字串中第一行的行首。  
  
 下列範例是類似於 `^` 和 `$` 錨點的範例。 它會在規則運算式中使用 `\A` 錨點，該規則運算式會擷取與某些職業棒球隊存在期間年份相關的資訊。 輸入字串包含五行。 在符合規則運算式模式的輸入字串中，對 <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> 方法的呼叫只會尋找其中的第一個子字串。 如範例所示， <xref:System.Text.RegularExpressions.RegexOptions.Multiline> 選項不會有任何作用。  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/startofstring2.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/startofstring2.vb#3)]  
  
 [回到頁首](#top)  
  
<a name="EndOrNOnly"></a>   
## <a name="end-of-string-or-before-ending-newline-z"></a>字串結尾或結束新行之前：\Z  
 `\Z` 錨點指定比對必須發生在輸入字串的結尾，或在輸入字串結尾的 `\n` 之前。 它與 `$` 錨點相同，不同處在於 `\Z` 會忽略 <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> 選項。 因此在多行字串中，它只會比對最後一行的結尾，或 `\n` 前的上一行。  
  
 請注意， `\Z` 會比對 `\n` ，但不會比對 `\r\n` (CR/LF 字元組合)。 若要比對 CR/LF，請將 `\r?\Z` 包含在規則運算式模式中。  
  
 下列範例會在規則運算式中使用 `\Z` 錨點，該規則運算式與 [字串開頭或行首](#Start) 一節中的範例類似，會擷取與某些職業棒球隊存在期間年份相關的資訊。 規則運算式 `\r?\Z` 中的子運算式 `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\Z` 會比對字串的結尾，也會比對以 `\n` 或 `\r\n`結尾的字串。 如此一來，陣列中的每個項目都會符合規則運算式模式。  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring2.cs#4)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring2.vb#4)]  
  
 [回到頁首](#top)  
  
<a name="EndOnly"></a>   
## <a name="end-of-string-only-z"></a>僅字串結尾：\z  
 `\z` 錨點指定比對必須發生在輸入字串的結尾。 與 `$` 語言項目相同，`\z` 會忽略 <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> 選項。 不像 `\Z` 語言項目，`\z` 不會比對字串結尾處的 `\n` 字元。 因此，它可以只比對輸入字串的最後一行。  
  
 下列範例會在規則運算式中使用 `\z` 錨點，該規則運算式與上一節中的範例不同，它會擷取與某些職業棒球隊存在期間年份相關的資訊。 這個範例會將字串陣列中的五個項目與規則運算模式 `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\z`進行比對。 有兩個字串以歸位字元與換行字元結尾，一個字串以換行字元結尾，以及兩個字串不以歸位字元也不以換行字元結尾。 如輸出所示，只有不含歸位字元或換行字元的字串會符合模式。  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/endofstring3.cs#5)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/endofstring3.vb#5)]  
  
 [回到頁首](#top)  
  
<a name="Contiguous"></a>   
## <a name="contiguous-matches-g"></a>連續比對：\G  
 `\G` 錨點指定比對必須發生在上一個比對結束的點。 當您將此錨點配合 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> 或 <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> 方法使用時，它可確保所有相符項目是連續的。  
  
 下列範例會使用規則運算式從逗點分隔的字串中擷取齧齒動物物種的名稱。  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/contiguous1.cs#6)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/contiguous1.vb#6)]  
  
 規則運算式 `\G(\w+\s?\w*),?` 的解譯方式如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`\G`|從上一次比對結束的地方開始。|  
|`\w+`|比對一個或多個文字字元。|  
|`\s?`|比對零或一個空格。|  
|`\w*`|比對零個或多個文字字元。|  
|`(\w+\s?\w*)`|比對一或多個文字字元，後面接零或一個空格，再接零或多個文字字元。 這是第一個擷取群組。|  
|`,?`|比對出現零次或一次的常值逗號字元。|  
  
 [回到頁首](#top)  
  
<a name="WordBoundary"></a>   
## <a name="word-boundary-b"></a>字邊界：\b  
 `\b` 錨點指定比對必須發生在文字字元 ( `\w` 語言項目) 和非文字字元 ( `\W` 語言項目) 之間的邊界上。 文字字元由英數字元及底線所組成；非文字字元是非英數字元或底線的任何字元。 (如需詳細資訊，請參閱[字元類別](../../../docs/standard/base-types/character-classes-in-regular-expressions.md)。)比對也可能會在字串開頭或結尾的字邊界上發生。  
  
 `\b` 錨點經常用來確保子運算式會比對整個字組，而非只比對字組的開頭或結尾。 在下列範例中的規則運算式 `\bare\w*\b` 說明這個的使用方式。 它會比對任何以子字串 "are" 為開頭的字組。 範例的輸出也說明了 `\b` 會比對輸入字串的開頭和結尾。  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/word1.cs#7)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/word1.vb#7)]  
  
 規則運算式模式的解譯方式如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`\b`|開始字緣比對。|  
|`are`|比對子字串 "are"。|  
|`\w*`|比對零個或多個文字字元。|  
|`\b`|結束字緣比對。|  
  
 [回到頁首](#top)  
  
<a name="NonwordBoundary"></a>   
## <a name="non-word-boundary-b"></a>非字邊界：\B  
 `\B` 錨點指定比對不得發生在字邊界上。 這和 `\b` 錨點相反。  
  
 下列範例使用 `\B` 錨點來尋找在字組中出現的子字串 "qu"。 規則運算式模式 `\Bqu\w+` 會比對以 "qu" 開頭的子字串，其中字組開頭並非 "qu"，並且會繼續比對到字組的結尾。  
  
 [!code-csharp[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.assertions/cs/nonword1.cs#8)]
 [!code-vb[Conceptual.RegEx.Language.Assertions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.assertions/vb/nonword1.vb#8)]  
  
 規則運算式模式的解譯方式如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`\B`|不要在字邊界開始比對。|  
|`qu`|比對子字串 "qu"。|  
|`\w+`|比對一個或多個文字字元。|  
  
## <a name="see-also"></a>請參閱  
 [規則運算式語言 - 快速參考](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 [規則運算式選項](../../../docs/standard/base-types/regular-expression-options.md)
