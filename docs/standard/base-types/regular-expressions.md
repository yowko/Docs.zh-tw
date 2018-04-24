---
title: .NET Framework 規則運算式
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pattern-matching with regular expressions, about pattern-matching
- substrings
- searching with regular expressions, about regular expressions
- pattern-matching with regular expressions
- searching with regular expressions
- parsing text with regular expressions
- regular expressions [.NET Framework], about regular expressions
- regular expressions [.NET Framework]
- .NET Framework regular expressions, about
- characters [.NET Framework], regular expressions
- parsing text with regular expressions, overview
- .NET Framework regular expressions
- strings [.NET Framework], regular expressions
ms.assetid: 521b3f6d-f869-42e1-93e5-158c54a6895d
caps.latest.revision: 24
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5d0ec5572776368fa9943a87fa72280a4ebeb03d
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="net-regular-expressions"></a>.NET 規則運算式
規則運算式提供功能強大、彈性且有效率的方法來處理文字。 規則運算式的廣泛模式比對標記法可讓您快速剖析大量文字，以尋找特定的字元模式；驗證文字，以確保其符合預先定義的模式 (例如電子郵件地址)；擷取、編輯、取代或刪除文字子字串；以及將擷取的字串加入至集合，以產生報告。 對許多處理字串或剖析大型文字區塊的應用程式而言，規則運算式是不可或缺的工具。  
  
## <a name="how-regular-expressions-work"></a>規則運算式的運作方式  
 使用規則運算式來處理文字的核心是規則運算式引擎，以 .NET 中的 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> 物件來表示。 使用規則運算式來處理文字時，至少需要提供規則運算式引擎以及下列兩個資訊項目：  
  
-   要在文字中識別的規則運算式模式。  
  
     在 .NET 中，規則運算式模式是以特殊的語法或語言來定義，其相容於 Perl 5 規則運算式，並新增一些其他功能，例如由右至左比對。 如需詳細資訊，請參閱[規則運算式語言 - 快速參考](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)。  
  
-   要為規則運算式模式剖析的文字。  
  
 <xref:System.Text.RegularExpressions.Regex> 類別的方法可讓您執行下列作業：  
  
-   呼叫 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> 方法，以判定規則運算式模式是否出現在輸入文字中。 如需使用 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> 方法來驗證文字的範例，請參閱[如何：確認字串是否為有效的電子郵件格式](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md)。  
  
-   呼叫 <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> 或 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> 方法，以擷取符合規則運算式模式的所有文字。 前一個方法會傳回 <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> 物件，提供相符文字的相關資訊。 後一個方法會傳回 <xref:System.Text.RegularExpressions.MatchCollection> 物件，其中針對在所剖析文字中找到的每個相符項目，各包含一個 <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> 物件。  
  
-   呼叫 <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> 方法，以取代符合規則運算式模式的文字。 如需使用 <xref:System.Text.RegularExpressions.Regex.Replace%2A> 方法來變更日期格式，以及移除字串中無效字元的範例，請參閱[如何：從字串中刪除無效的字元](../../../docs/standard/base-types/how-to-strip-invalid-characters-from-a-string.md)和[如何：變更日期格式](../../../docs/standard/base-types/regular-expression-example-changing-date-formats.md)。  
  
 如需規則運算式物件模型概觀，請參閱[規則運算式物件模型](../../../docs/standard/base-types/the-regular-expression-object-model.md)。  
  
 如需規則運算式語言的詳細資訊，請參閱[規則運算式語言 - 快速參考](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)，或下載並列印下列其中一本小手冊：  
  
 [Word (.docx) 格式的快速參考](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [PDF (.pdf) 格式的快速參考](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)  
  
## <a name="regular-expression-examples"></a>規則運算式範例  
 <xref:System.String> 類別包含數種字串搜尋和取代方法，可供您在大型字串中尋找常值字串時使用。 當您想要在大型字串中尋找數個子字串時，或是當您想要識別字串中的模式時，規則運算式最為好用，如下列範例所示。  
  
### <a name="example-1-replacing-substrings"></a>範例 1：取代子字串  
 假設郵寄清單包含的名稱有時候會包括稱謂 (Mr.、Mrs.、Miss 或 Ms.) 以及姓名。 當您從清單產生信封標籤時，如果不想包括稱謂，就可以使用規則運算式來移除稱謂，如下列範例所示。  
  
 [!code-csharp[Conceptual.Regex#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example1.cs#2)]
 [!code-vb[Conceptual.Regex#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example1.vb#2)]  
  
 規則運算式模式 `(Mr\.? |Mrs\.? |Miss |Ms\.? )` 會比對所出現的任何 "Mr "、"Mr. "、"Mrs "、"Mrs. "、"Miss "、"Ms 或 "Ms. "。 呼叫 <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> 方法會將相符的字串取代為 <xref:System.String.Empty?displayProperty=nameWithType>；換句話說，就是將其從原始字串中移除。  
  
### <a name="example-2-identifying-duplicated-words"></a>範例 2：識別重複的文字  
 不小心重複文字是作者常犯的錯誤。 規則運算式可用來識別重複的文字，如下列範例所示。  
  
 [!code-csharp[Conceptual.Regex#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example2.cs#3)]
 [!code-vb[Conceptual.Regex#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example2.vb#3)]  
  
 規則運算式模式 `\b(\w+?)\s\1\b` 可解譯如下：  
  
|||  
|-|-|  
|`\b`|從字緣開始。|  
|(\w+?)|比對一或多個字元，但字元數愈少愈好。 這些一起構成可稱之為 `\1` 的群組。|  
|`\s`|比對空白字元。|  
|`\1`|比對等同於名為 `\1` 之群組的子字串。|  
|`\b`|比對字邊界。|  
  
 呼叫 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> 方法時，規則運算式選項設為 <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>。 因此，比對作業不區分大小寫，而且此範例會將子字串 "This this" 視為重複。  
  
 請注意，輸入字串包括子字串 "this? This"。 不過，因為中間有標點符號，所以不會將其視為重複。  
  
### <a name="example-3-dynamically-building-a-culture-sensitive-regular-expression"></a>範例 3：動態建立區分文化特性的規則運算式  
 下列範例說明規則運算式結合 .NET 全球化功能所提供的彈性，功能有多麼強大。 它會使用 <xref:System.Globalization.NumberFormatInfo> 物件來判定系統目前文化特性中的幣值格式， 然後利用該資訊動態建構可從文字擷取幣值的規則運算式。 針對每個比對，它會擷取僅包含數值字串的子群組，將其轉換成 <xref:System.Decimal> 值，並計算執行總計。  
  
 [!code-csharp[Conceptual.Regex#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example.cs#1)]
 [!code-vb[Conceptual.Regex#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example.vb#1)]  
  
 在目前文化特性為 English - United States (en-US) 的電腦上，此範例會動態建立規則運算式 `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`。 此規則運算式模式可解譯如下：  
  
|||  
|-|-|  
|`\$`|在輸入字串中尋找單獨出現的貨幣符號 ($)。 規則運算式模式字串包含反斜線，表示貨幣符號要解譯為字面意義，而不是規則運算式錨點。 ($ 符號單獨出現表示規則運算式引擎應該嘗試在字串結尾處開始其比對。)為了確保目前文化特性的貨幣符號不會誤譯為規則運算式符號，此範例呼叫 <xref:System.Text.RegularExpressions.Regex.Escape%2A> 方法以逸出字元。|  
|`\s*`|尋找出現零或多次的空格字元。|  
|`[-+]?`|尋找出現一或多次的正號或負號。|  
|`([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`|此運算式外面括號將其定義成擷取群組或子運算式。 如果找到相符項目，從 <xref:System.Text.RegularExpressions.Group> 屬性傳回之 <xref:System.Text.RegularExpressions.GroupCollection> 物件中的第二個 <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> 物件，擷取此部分比對字串的相關資訊。 (集合中的第一個項目代表整個比對。)|  
|`[0-9]{0,3}`|尋找出現零到三次的十進位數字 0 到 9。|  
|`(,[0-9]{3})*`|尋找出現零或多次、後面接三個十進位數字的群組分隔符號。|  
|`\.`|尋找單次出現的十進位分隔符號。|  
|`[0-9]+`|尋找一或多個十進位數字。|  
|`(\.[0-9]+)?`|尋找出現零或一次、後接至少一個十進位數字的十進位分隔符號。|  
  
 如果在輸入字串中找到上述每個子模式，則比對成功，並且會將包含此比對相關資訊的 <xref:System.Text.RegularExpressions.Match> 物件加入至 <xref:System.Text.RegularExpressions.MatchCollection> 物件。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[規則運算式語言 - 快速參考](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|提供您可以用來定義規則運算式之字元、運算子和建構組合的資訊。|  
|[規則運算式物件模型](../../../docs/standard/base-types/the-regular-expression-object-model.md)|提供資訊和程式碼範例，說明如何使用規則運算式類別。|  
|[規則運算式行為的詳細資訊](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)|提供 .NET 規則運算式之功能和行為的相關資訊。|  
|[規則運算式範例](../../../docs/standard/base-types/regular-expression-examples.md)|提供程式碼範例，以說明規則運算式的一般用法。|  
  
## <a name="reference"></a>參考資料  
 <xref:System.Text.RegularExpressions?displayProperty=nameWithType>  
 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>  
 [規則運算式 - 快速參考 (以 Word 格式下載)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [規則運算式 - 快速參考 (以 PDF 格式下載)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
