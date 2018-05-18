---
title: 在規則運算式中執行替代
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, substitutions
- replacement patterns
- metacharacters, substitutions
- .NET Framework regular expressions, substitutions
- constructs, substitutions
- substitutions
ms.assetid: d1f52431-1c7d-4dc6-8792-6b988256892e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53fd4ee63d49b3943fa0b1164591aaddaa764abc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="substitutions-in-regular-expressions"></a>在規則運算式中執行替代
<a name="Top"></a> 替代是指只有在取代模式內才能辨識的語言項目。 這些項目使用規則運算式模式定義要取代輸入字串中相符文字的全部或部分文字。 取代模式可以包含一個或多個替代，以及常值字元。 取代模式會提供給具有 <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> 參數的 `replacement` 方法多載，以及提供給 <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> 方法。 這些方法會將符合的模式取代為 `replacement` 參數所定義的模式。  
  
 .NET Framework 會定義下表列出的替代項目。  
  
|替代|描述|  
|------------------|-----------------|  
|`$` *數字*|包括在取代字串中與 *數字*所指定之擷取群組相符的最後一個子字串，其中 *數字* 是十進位值。 如需詳細資訊，請參閱 [替代編號群組](#Numbered)。|  
|`${` *name* `}`|包括在取代字串中與 `(?<`*名稱*`> )` 所指定之具名群組相符的最後一個子字串。 如需詳細資訊，請參閱 [替代具名群組](#Named)。|  
|`$$`|取代字串中包括單一 "$" 常值。 如需詳細資訊，請參閱 [替代 "$" 符號](#DollarSign)。|  
|`$&`|取代字串中包括整個相符項目的複本。 如需詳細資訊，請參閱 [替代整個相符項目](#EntireMatch)。|  
|<code>$\`</code>|取代字串中包括輸入字串中相符項目之前的所有文字。 如需詳細資訊，請參閱 [替代相符項目前的文字](#BeforeMatch)。|  
|`$'`|取代字串中包括輸入字串中相符項目之後的所有文字。 如需詳細資訊，請參閱 [替代相符項目後的文字](#AfterMatch)。|  
|`$+`|取代字串中包括最後擷取的群組。 如需詳細資訊，請參閱 [替代最後擷取的群組](#LastGroup)。|  
|`$_`|取代字串中包括整個輸入字串。 如需詳細資訊，請參閱 [替代整個輸入字串](#EntireString)。|  
  
## <a name="substitution-elements-and-replacement-patterns"></a>替代項目和取代模式  
 替代是取代模式中唯一能夠辨認的特殊建構。 不支援其他規則運算式語言項目，包括逸出字元和符合任何字元的句號 (`.`)。 同樣的，替代語言項目只有在取代模式中才能辨識，而且在規則運算式模式中永遠無效。  
  
 唯一能夠在規則運算式模式或替代中出現的字元是 `$` 字元，不過它在這兩種內容中的意義不同。 在規則運算式模式中， `$` 是比對字串結尾的錨點。 在取代模式中， `$` 表示替代開頭。  
  
> [!NOTE]
>  如需規則運算式內類似取代模式的功能，請使用反向參考。 如需反向參考的詳細資訊，請參閱 [反向參考建構](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md)。  
  
<a name="Numbered"></a>   
## <a name="substituting-a-numbered-group"></a>替代編號群組  
 `$`*數字* 語言項目包括取代字串中與 *數字* 擷取群組相符的最後一個子字串，其中 *數字* 是擷取群組的索引。 例如，取代模式 `$1` 表示第一個擷取的群組將取代相符的子字串。 如需編號擷取群組的詳細資訊，請參閱 [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)。  
  
 `$` 後面接著的所有數字都會解譯為屬於 *數字* 群組。 如果這不是您的目的，可以改為替代具名群組。 例如，您可以使用取代字串 `${1}1` 而非 `$11` ，將取代字串定義為第一個擷取之群組的值連同數字 "1"。 如需詳細資訊，請參閱 [替代具名群組](#Named)。  
  
 未使用 `(?<`*名稱*`>)` 語法明確指派名稱的擷取群組，會從一開始由左至右編號。 具名群組是從最後一個未命名群組的索引加一開始，由左至右編號。 例如，在規則運算式 `(\w)(?<digit>\d)`中， `digit` 具名群組的索引為 2。  
  
 如果 *數字* 沒有指定在規則運算式模式中定義的有效擷取群組， `$`*數字* 就會解譯為用以取代每個相符項目的常值字元序列。  
  
 下列範例使用 `$`*數字* 替代從十進位值中去除貨幣符號。 它會移除在貨幣數值的開頭或結尾找到的貨幣符號，並且辨識兩種最常見的十進位分隔符號 ("." 和 ",")。  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/numberedgroup1.cs#1)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/numberedgroup1.vb#1)]  
  
 規則運算式模式 `\p{Sc}*(\s?\d+[.,]?\d*)\p{Sc}*` 的定義如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`\p{Sc}*`|比對零個或多個貨幣符號字元。|  
|`\s?`|比對零個或一個空白字元。|  
|`\d+`|比對一個或多個十進位數字。|  
|`[.,]?`|比對零個或一個句號或逗號。|  
|`\d*`|比對零個或多個十進位數字。|  
|`(\s?\d+[.,]?\d*)`|比對空白字元後面接著一個或多個十進位數字，再接零個或一個句號或逗號，最後再接零個或多個十進位數字。 這是第一個擷取群組。 由於取代模式為 `$1`，因此呼叫 <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> 方法會將整個相符的子字串取代為這個擷取的群組。|  
  
 [回到頁首](#Top)  
  
<a name="Named"></a>   
## <a name="substituting-a-named-group"></a>替代具名群組  
 `${`*名稱*`}` 語言項目會替代與 *稱* 擷取群組相符的最後一個子字串，其中 *稱* 稱是由 `(?<`*名稱*`>)` 語言項目定義之擷取群組的名稱。 如需具名擷取群組的詳細資訊，請參閱 [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)。  
  
 如果 *名稱* 未指定規則運算式模式中定義的有效具名擷取群組，而包含數字，則 `${`*名稱*`}` 會解譯為編號的群組。  
  
 如果 *名稱* 未指定規則運算式模式中定義的有效具名擷取群組，也未定義有效的編號擷取群組，則 `${`*名稱*`}` 會解譯為用以取代每個相符項目的常值字元序列。  
  
 下列範例使用 `${`*稱*`}` 替代從十進位值中去除貨幣符號。 它會移除在貨幣數值的開頭或結尾找到的貨幣符號，並且辨識兩種最常見的十進位分隔符號 ("." 和 ",")。  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/namedgroup1.cs#2)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/namedgroup1.vb#2)]  
  
 規則運算式模式 `\p{Sc}*(?<amount>\s?\d[.,]?\d*)\p{Sc}*` 的定義如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`\p{Sc}*`|比對零個或多個貨幣符號字元。|  
|`\s?`|比對零個或一個空白字元。|  
|`\d+`|比對一個或多個十進位數字。|  
|`[.,]?`|比對零個或一個句號或逗號。|  
|`\d*`|比對零個或多個十進位數字。|  
|`(?<amount>\s?\d[.,]?\d*)`|比對空白字元，後面接著一個或多個十進位數字，再接零個或一個句號或逗號，最後再接零個或多個十進位數字。 這是名為 `amount`的擷取群組。 由於取代模式為 `${amount}`，因此呼叫 <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> 方法會將整個相符的子字串取代為這個擷取的群組。|  
  
 [回到頁首](#Top)  
  
<a name="DollarSign"></a>   
## <a name="substituting-a--character"></a>替代 "$" 字元  
 `$$` 替代會在取代的字串中插入常值 "$" 字元。  
  
 下列範例會使用 <xref:System.Globalization.NumberFormatInfo> 物件決定目前文化特性的貨幣符號，以及它在貨幣字串中的位置。 然後，它會動態建置規則運算式模式和取代模式。 如果這個範例是在目前文化特性為 zh-TW 的電腦上執行，則會產生規則運算式模式 `\b(\d+)(\.(\d+))?` 以及取代模式 `$$ $1$2`。 取代模式會將相符的文字取代為貨幣符號和空格，後面接著第一個和第二個擷取群組。  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/dollarsign1.cs#8)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/dollarsign1.vb#8)]  
  
 規則運算式模式 `\b(\d+)(\.(\d+))?` 的定義如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`\b`|在字邊界的開頭開始比對。|  
|`(\d+)`|比對一個或多個十進位數字。 這是第一個擷取群組。|  
|`\.`|比對句號 (十進位分隔符號)。|  
|`(\d+)`|比對一個或多個十進位數字。 這是第三個擷取群組。|  
|`(\.(\d+))?`|比對零個或一個句號，後面接著一個或多個十進位數字。 這是第二個擷取群組。|  
  
<a name="EntireMatch"></a>   
## <a name="substituting-the-entire-match"></a>替代整個相符項目  
 `$&` 替代會在取代字串中包含整個相符項目。 通常，它會用來將子字串加入至相符字串的開頭或結尾。 例如， `($&)` 取代模式會在每個相符項目的開頭和結尾加上括號。 如果沒有相符項目， `$&` 替代就不會有任何作用。  
  
 下列範例會使用 `$&` 替代，在字串陣列中所儲存的書名開頭和結尾加上引號。  
  
 [!code-csharp[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entirematch1.cs#3)]
 [!code-vb[Conceptual.RegEx.Language.Substitutions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entirematch1.vb#3)]  
  
 規則運算式模式 `^(\w+\s?)+$` 的定義如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`^`|在輸入字串的開頭開始比對。|  
|`(\w+\s?)+`|一次或多次比對一個或多個文字字元後面接著零或一個空白字元的模式。|  
|`$`|比對輸入字串的結尾。|  
  
 `"$&"` 取代模式會在每個相符項目的開頭和結尾加上常值引號。  
  
 [回到頁首](#Top)  
  
<a name="BeforeMatch"></a>   
## <a name="substituting-the-text-before-the-match"></a>替代相符項目前的文字  
 <code>$\`</code> 替代會將相符的字串取代為相符項目前的整個輸入字串。 也就是說，它在移除相符文字的同時，也會複製輸入字串直到相符項目前。 在結果字串中，相符文字後面接著的任何文字都會保持不變。 如果在輸入字串中有多個相符項目，取代文字就會衍生自原始輸入字串，而非其中文字已經由先前的相符項目取代的字串  \(這個範例將提供說明。\)如果沒有相符項目，<code>$\`</code> 替代就不會有任何作用。  
  
 下列範例會使用規則運算式模式 `\d+` ，比對輸入字串中的一或多個十進位數字序列。 取代字串 <code>$`</code> 會以相符文字前的文字取代這些數字。  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/before1.cs#4)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/before1.vb#4)]  
  
 在這個範例中，輸入字串 `"aa1bb2cc3dd4ee5"` 包含五個相符項目。 下表將說明 <code>$`</code> 替代如何使規則運算式引擎取代輸入字串中的每個相符項目。 插入的文字會以粗體顯示在結果資料行中。  
  
|比對|位置|相符項目前的字串|結果字串|  
|-----------|--------------|-------------------------|-------------------|  
|1|2|aa|aa**aa**bb2cc3dd4ee5|  
|2|5|aa1bb|aaaabb**aa1bb**cc3dd4ee5|  
|3|8|aa1bb2cc|aaaabbaa1bbcc**aa1bb2cc**dd4ee5|  
|4|11|aa1bb2cc3dd|aaaabbaa1bbccaa1bb2ccdd**aa1bb2cc3dd**ee5|  
|5|14|aa1bb2cc3dd4ee|aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddee**aa1bb2cc3dd4ee**|  
  
 [回到頁首](#Top)  
  
<a name="AfterMatch"></a>   
## <a name="substituting-the-text-after-the-match"></a>替代相符項目後的文字  
 `$'` 替代會以相符項目後的整個輸入字串取代相符的字串。 也就是說，它在移除相符文字的同時，也會在相符項目後複製輸入字串。 在結果字串中，相符文字之前的任何文字都會保持不變。 如果沒有相符項目，  `$'` 替代就不會有任何作用。  
  
 下列範例會使用規則運算式模式 `\d+` ，比對輸入字串中的一或多個十進位數字序列。 取代字串 `$'` 會以相符項目後的文字取代這些數字。  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/after1.cs#5)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/after1.vb#5)]  
  
 在這個範例中，輸入字串 `"aa1bb2cc3dd4ee5"` 包含五個相符項目。 下表將說明 `$'` 替代如何使規則運算式引擎取代輸入字串中的每個相符項目。 插入的文字會以粗體顯示在結果資料行中。  
  
|比對|位置|相符項目後的字串|結果字串|  
|-----------|--------------|------------------------|-------------------|  
|1|2|bb2cc3dd4ee5|aa**bb2cc3dd4ee5**bb2cc3dd4ee5|  
|2|5|cc3dd4ee5|aabb2cc3dd4ee5bb**cc3dd4ee5**cc3dd4ee5|  
|3|8|dd4ee5|aabb2cc3dd4ee5bbcc3dd4ee5cc**dd4ee5**dd4ee5|  
|4|11|ee5|aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5dd**ee5**ee5|  
|5|14|<xref:System.String.Empty?displayProperty=nameWithType>|aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5ddee5ee|  
  
 [回到頁首](#Top)  
  
<a name="LastGroup"></a>   
## <a name="substituting-the-last-captured-group"></a>替代最後擷取的群組  
 `$+` 替代會以最後擷取的群組取代相符的字串。 如果沒有擷取的群組，或者最後一個擷取群組的值是 <xref:System.String.Empty?displayProperty=nameWithType>，`$+` 替代就不會有任何作用。  
  
 下列範例會識別字串中的重複文字，並使用 `$+` 替代將這些文字取代為出現的單一文字。 <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> 選項是用來確保只有大小寫不同的相同單字，都會視為重複項目。  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/lastmatch1.cs#6)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/lastmatch1.vb#6)]  
  
 規則運算式模式 `\b(\w+)\s\1\b` 的定義如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`\b`|開始字緣比對。|  
|`(\w+)`|比對一個或多個文字字元。 這是第一個擷取群組。|  
|`\s`|比對空白字元。|  
|`\1`|比對第一個擷取的群組。|  
|`\b`|結束字緣比對。|  
  
 [回到頁首](#Top)  
  
<a name="EntireString"></a>   
## <a name="substituting-the-entire-input-string"></a>替代整個輸入字串  
 `$_` 替代會將相符的字串取代整個輸入字串。 也就是說，它會移除相符的文字，並會以整個字串來取代，包括相符的文字。  
  
 下列範例會比對輸入字串中的一個或多個十進位數字。 它會使用 `$_` 替代，以整個輸入字串來取代它們。  
  
 [!code-csharp[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.substitutions/cs/entire1.cs#7)]
 [!code-vb[Conceptual.Regex.Language.Substitutions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.substitutions/vb/entire1.vb#7)]  
  
 在這個範例中，輸入字串 `"ABC123DEF456"` 包含兩個相符項目。 下表將說明 `$_` 替代如何使規則運算式引擎取代輸入字串中的每個相符項目。 插入的文字會以粗體顯示在結果資料行中。  
  
|比對|位置|比對|結果字串|  
|-----------|--------------|-----------|-------------------|  
|1|3|123|ABC**ABC123DEF456**DEF456|  
|2|5|456|ABCABC123DEF456DEF**ABC123DEF456**|  
  
## <a name="see-also"></a>請參閱  
 [規則運算式語言 - 快速參考](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
