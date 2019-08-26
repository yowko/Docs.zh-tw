---
title: 在 .NET 中使用字串的最佳做法
description: 了解如何在 .NET 應用程式中有效地使用字串。
ms.date: 05/01/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET Framework],searching
- best practices,string comparison and sorting
- strings [.NET Framework],best practices
- strings [.NET Framework],basic string operations
- sorting strings
- strings [.NET Framework],sorting
- string comparison [.NET Framework],best practices
- string sorting
- comparing strings
- strings [.NET Framework],comparing
ms.assetid: b9f0bf53-e2de-4116-8ce9-d4f91a1df4f7
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: 50127f24bfee0c2fe49da8f285e5052d2f753696
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934931"
---
# <a name="best-practices-for-using-strings-in-net"></a>在 .NET 中使用字串的最佳做法
<a name="top"></a> .NET 可廣泛支援當地語系化和全球化應用程式的開發作業，使您在執行一般作業 (例如排序和顯示字串) 時，可輕鬆套用目前的文化特性或文化特性特定的慣例。 但是，排序或比較字串並不一定是區分文化特性的作業。 例如，應用程式內部使用的字串，通常應該跨所有文化特性皆進行相同處理。 若將與文化特性無關的字串資料 (例如 XML 標記、HTML 標記、使用者名稱、檔案路徑和系統物件的名稱) 進行區分文化特性的解譯時，應用程式程式碼可能會出現細微的 Bug、效能不佳，甚至在某些情況下，會產生安全性問題。  
  
 本主題詳述 .NET 中的字串排序、比較和大小寫方法，並提供選取適當字串處理方法的建議，以及有關字串處理方法的其他資訊。 它也會說明如何處理數值資料和日期與時間資料之類的格式化資料，以供顯示及儲存。  
  
 此主題包括下列章節：  
  
- [字串的使用方式建議](#recommendations_for_string_usage)  
  
- [明確指定字串比較](#specifying_string_comparisons_explicitly)  
  
- [字串比較的詳細資料](#the_details_of_string_comparison)  
  
- [針對方法呼叫選擇 StringComparison 成員](#choosing_a_stringcomparison_member_for_your_method_call)  
  
- [.NET 中常用的字串比較方法](#common_string_comparison_methods_in_the_net_framework)  
  
- [間接執行字串比較的方法](#methods_that_perform_string_comparison_indirectly)  
  
- [顯示和保存格式化的資料](#Formatted)  
  
<a name="recommendations_for_string_usage"></a>   
## <a name="recommendations-for-string-usage"></a>字串的使用方式建議  
 當您使用 .NET 進行開發時，請遵循下列簡單的字串使用建議：  
  
- 使用明確指定字串比較規則的多載來進行字串作業。 一般而言，這需要呼叫具有 <xref:System.StringComparison>類別參數的方法多載。  
  
- 將 <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> 或 <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> 做為安全的無從驗證文化特性字串預設比對，來進行比較。  
  
- 使用 <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> 或 <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> 來比較以提升效能。  
  
- 向使用者顯示輸出時，您可以使用依據 <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> 的字串作業。  
  
- 在進行語言無關的比較 (如符號) 時，使用非語言式 <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> 或 <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> 值，而不是依據 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> 的字串作業。  
  
- 正規化字串以進行比較，使用 <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> 方法，而非 <xref:System.String.ToLowerInvariant%2A?displayProperty=nameWithType> 方法。  
  
- 使用 <xref:System.String.Equals%2A?displayProperty=nameWithType> 方法的多載，來測試兩個字串是否相等。  
  
- 使用 <xref:System.String.Compare%2A?displayProperty=nameWithType> 和 <xref:System.String.CompareTo%2A?displayProperty=nameWithType> 方法來排序字串，而不檢查是否相等。  
  
- 使用區分文化特性的格式來顯示使用者介面中的非字串資料，例如數字和日期。 使用[不因文化特性而異](xref:System.Globalization.CultureInfo.InvariantCulture)的格式，來保存字串形式的非字串資料。  
  
 當您使用字串時，請避免下列作法：  
  
- 不要使用未明確或未隱含指定字串比較規則的多載來進行字串作業。  
  
- 在大部分情況下，請不要使用依據 <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> 的字串作業。 若您要保存具語言意義但無從驗證文化特性的資料，就是少數的例外狀況之一。  
  
- 不要使用 <xref:System.String.Compare%2A?displayProperty=nameWithType> 或 <xref:System.String.CompareTo%2A> 方法的多載以及傳回零值的測試，來判斷兩個字串是否相等。  
  
- 不要使用區分文化特性的格式來保存數值資料或字串形式的日期和時間資料。  
  
 [回到頁首](#top)  
  
<a name="specifying_string_comparisons_explicitly"></a>   
## <a name="specifying-string-comparisons-explicitly"></a>明確指定字串比較  
 在 .NET 中的字串操作方法大多都是多載。 一般而言，您可讓一或多個多載接受預設值，而其他不接受預設值的多載，則定義用來比較或操作字串的精確方式。 大部分不依賴預設值的方法都會包含 <xref:System.StringComparison>類型的參數，其為一種列舉類型，可明確指定依據文化特性和大小寫進行字串比較的規則。 下表說明 <xref:System.StringComparison> 列舉類型成員。  
  
|StringComparison 成員|說明|  
|-----------------------------|-----------------|  
|<xref:System.StringComparison.CurrentCulture>|使用目前文化特性執行區分大小寫的比較。|  
|<xref:System.StringComparison.CurrentCultureIgnoreCase>|使用目前文化特性執行不區分大小寫的比較。|  
|<xref:System.StringComparison.InvariantCulture>|使用不因國別而異的文化特性執行區分大小寫的比較。|  
|<xref:System.StringComparison.InvariantCultureIgnoreCase>|使用不因國別而異的文化特性執行不區分大小寫的比較。|  
|<xref:System.StringComparison.Ordinal>|執行序數比較。|  
|<xref:System.StringComparison.OrdinalIgnoreCase>|執行不區分大小寫的序數比較。|  
  
 例如， <xref:System.String.IndexOf%2A> 方法有下列九個多載，可傳回 <xref:System.String> 物件中符合某字元或某字串之子字串的索引：  
  
- <xref:System.String.IndexOf%28System.Char%29>、 <xref:System.String.IndexOf%28System.Char%2CSystem.Int32%29>和 <xref:System.String.IndexOf%28System.Char%2CSystem.Int32%2CSystem.Int32%29>會預設執行字串字元的序數 (區分大小寫且區分文化特性) 搜尋。  
  
- <xref:System.String.IndexOf%28System.String%29>、 <xref:System.String.IndexOf%28System.String%2CSystem.Int32%29>和 <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.Int32%29>會預設執行字串的子字元搜尋 (區分大小寫且區分文化特性)。  
  
- <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29>、 <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.StringComparison%29>和 <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.Int32%2CSystem.StringComparison%29>包括 <xref:System.StringComparison> 類型的參數，可指定比較形式。  
  
 基於下列原因，建議您選取不使用預設值的多載：  
  
- 有些使用預設參數的多載 (其會在字串執行個體中搜尋 <xref:System.Char> ) 會執行序數比較，而其他多載 (其會搜尋字串執行個體中的字串) 有區分文化特性。 使用者很難記住哪一種方法使用預設值，也很容易混淆多載。  
  
- 依賴預設值來執行方法呼叫的程式碼意圖並不清楚。 在下列使用預設值的範例中，我們難以知道開發人員要進行兩個字串的序數或語言比較，也很難判斷 `protocol` 和 "http" 之間的大小寫差異是否會造成相等測試傳回 `false`類別參數的方法多載。  
  
     [!code-csharp[Conceptual.Strings.BestPractices#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/explicitargs1.cs#1)]
     [!code-vb[Conceptual.Strings.BestPractices#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/explicitargs1.vb#1)]  
  
 一般而言，我們建議您呼叫不依賴預設值的方法，因為它會讓程式碼的意圖模稜兩可。 不過，這可讓程式碼更容易閱讀也更容易偵錯與維護。 下列範例將解決先前範例所引發的問題。 它會清楚指出使用序數比較，並且忽略大小寫差異。  
  
 [!code-csharp[Conceptual.Strings.BestPractices#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/explicitargs1.cs#2)]
 [!code-vb[Conceptual.Strings.BestPractices#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/explicitargs1.vb#2)]  
  
 [回到頁首](#top)  
  
<a name="the_details_of_string_comparison"></a>   
## <a name="the-details-of-string-comparison"></a>字串比較的詳細資料  
 字串比較是許多字串相關作業的核心，尤其是排序和測試是否相等這類作業。 字串依固定順序排序：在已排序的字串清單中，如果 "my" 在 "string" 之前出現，則 "my" 比較起來一定小於或等於 "string"。 此外，比較也隱含定義相等性。 比較作業會針對它認為相等的字串傳回零。 明言之，就是沒有任一字串比另一個字串更小。 最有意義的字串作業包含下列一或兩個程序：和其他字串進行比較，並執行定義完善的排序作業。  

> [!NOTE]
> 您可以下載[排序權數資料表](https://www.microsoft.com/download/details.aspx?id=10921)，該文字檔集合包含在 Windows 作業系統排序及比較作業中使用的字元權數資訊，以及下載[預設 Unicode 定序元素資料表](https://www.unicode.org/Public/UCA/latest/allkeys.txt) (適用於 Linux 和 macOS 的最新版本排序權數資料表)。 Linux 和 macOS 上的特定版本排序權數資料表，取決於在系統上安裝的 [International Components for Unicode](http://site.icu-project.org/) 程式庫。 如需其實作的 ICU 版本及 Unicode 版本詳細資訊，請參閱[下載 ICU](http://site.icu-project.org/download)。

 不過，評估兩個字串是否相等或決定排序順序不會產生單一的正確結果，而要取決於用來比較字串的準則而定。 特別是，如果字串比較是序數或根據目前文化特性或[不因文化特性而異](xref:System.Globalization.CultureInfo.InvariantCulture)的大小寫與排序慣例 (根據英文語言的無從驗證地區設定文化特性)，則可能會產生不同的結果。  

此外，使用不同版本 .NET 或使用不同作業系統或作業系統版本上 .NET 所做的字串比較，可能會傳回不同的結果。 如需詳細資訊，請參閱[字串及 Unicode 標準](xref:System.String#Unicode)。 

<a name="current_culture"></a>   
### <a name="string-comparisons-that-use-the-current-culture"></a>使用目前文化特性的字串比較  
 比較字串時，其中一個準則需使用目前文化特性的慣例。 如果比較是以目前文化特性為依據，就會使用執行緒的目前文化特性或地區設定。 如果使用者未設定文化特性，則會預設為控制台 [地區選項]  視窗中的設定。 當資料是語言相關資料，以及資料會反映區分文化特性的使用者互動時，請一律使用以目前文化特性為根據的比較。  
  
 不過，當文化特性變更時，.NET 中的比較和大小寫行為也會有所變更。 當執行應用程式的電腦其文化特性不同於開發應用程式的電腦時，或執行中的執行緒變更其文化特性時，會發生這種情況。 此種行為有其用意，但對許多開發人員來說並不容易注意到。 下列範例說明美國英文 ("en-US") 和瑞典文 ("sv-SE") 文化特性之間排序次序的差異。 請注意單字 "ångström"、"Windows" 和 "Visual Studio" 出現在已排序的字串陣列中的不同位置。  
  
 [!code-csharp[Conceptual.Strings.BestPractices#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison1.cs#3)]
 [!code-vb[Conceptual.Strings.BestPractices#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison1.vb#3)]  
  
 如果比較是使用目前文化特性且不區分大小寫，這類比較和區分文化特性的比較相同 (除了這些比較會忽略執行緒目前文化特性的大小寫要求以外)。 這種行為可能會以排序順序來呈現。  
  
 下列方法預設為執行使用目前文化特性之語意的比較：  
  
- 不含<xref:System.String.Compare%2A?displayProperty=nameWithType> 參數的 <xref:System.StringComparison> 多載。  
  
- <xref:System.String.CompareTo%2A?displayProperty=nameWithType> 多載。  
  
- 預設的 <xref:System.String.StartsWith%28System.String%29?displayProperty=nameWithType> 方法和含有 <xref:System.String.StartsWith%28System.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> null `null`<xref:System.Globalization.CultureInfo> 多載。  
  
- 預設的 <xref:System.String.EndsWith%28System.String%29?displayProperty=nameWithType> 方法和含有 <xref:System.String.EndsWith%28System.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> null `null`<xref:System.Globalization.CultureInfo> 多載。  
  
- 可接受<xref:System.String.IndexOf%2A?displayProperty=nameWithType> 做為搜尋參數且不含 <xref:System.String> 參數的 <xref:System.StringComparison> 多載。  
  
- 可接受<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> 做為搜尋參數且不含 <xref:System.String> 參數的 <xref:System.StringComparison> 多載。  
  
 在任何情況下，都建議您呼叫具有 <xref:System.StringComparison> 參數的多載，以讓呼叫方法的目的更清晰。  
  
 若以語言方式解譯非語言式的字串資料，或使用其他文化特性的慣例解譯來自特定文化特性的字串資料時，可能會出現微妙或不太微妙的 Bug。 標準範例是土耳其文 I 的問題。  
  
 對於幾乎所有拉丁字母 (包括美國英文)，字元 "i" (\u0069) 是字元 "I" (\u0049) 的小寫。 這種大小寫規則很快成為以這種文化特性進行程式設計的人所採用的預設規則。 不過，土耳其文 ("tr-TR") 字母包括「加上一點的 I」字元 "İ" (\u0130)，也就是 "i" 的大寫。 土耳其文中也包含「不含點的 i 」字元，"ı" (\u0131)，其大寫為 "I"。 亞塞拜然 ("az") 文化特性中也會發生這種行為。  
  
 因此，關於將 "i" 轉換成大寫或將 "I" 轉換成小寫的假設並不適用。 如果您針對字串比較常式使用預設多載，就會受限於文化特性之間的差異。 如果要比較的資料為非語言式，使用預設多載可能產生非預期的結果，如下列嘗試執行字串 "file" 和 "FILE" 之不區分大小寫的比較範例所示。  
  
 [!code-csharp[Conceptual.Strings.BestPractices#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#11)]
 [!code-vb[Conceptual.Strings.BestPractices#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#11)]  
  
 如果不小心將文化特性用於安全性相關設定 (如下列範例所示)，這項比較可能會造成重大的問題。 如果目前的文化特性是美國英文，方法呼叫 (如 `IsFileURI("file:")`) 會傳回 `true`；但若目前的文化特性為土耳其文，則傳回 `false`。 因此，在土耳其文的系統中，有心人士可以使用開頭為 "FILE:" 的 URI，來規避封鎖存取不區分大小寫之 URI 的安全性措施。  
  
 [!code-csharp[Conceptual.Strings.BestPractices#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#12)]
 [!code-vb[Conceptual.Strings.BestPractices#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#12)]  
  
 在此情況下，由於 "file:" 應解譯為非語言式、不區分文化特性的識別項，因此程式碼應改為下列範例：  
  
 [!code-csharp[Conceptual.Strings.BestPractices#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#13)]
 [!code-vb[Conceptual.Strings.BestPractices#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#13)]  
  
### <a name="ordinal-string-operations"></a>序數字串作業  
 在方法呼叫中指定 <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> 或 <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> 值意謂著非語言比較，其中忽略自然語言的特性。 若使用這類 <xref:System.StringComparison> 值來呼叫方法，方法就會以簡單的位元組比較來進行字串作業決策，而不以文化特性參數化的大小寫或對等項目資料表為根據。 在大部分情況下，這種方法非常適合預期的字串解譯，同時可讓程式碼更快速、可靠。  
  
 序數比較是一種字串比較，其會比較每個字串的每個位元組，而不進行語言解譯；例如，"windows" 不符合 "Windows"。 這基本上是對 C 執行階段 `strcmp` 函式的呼叫。 如果內容指出字串應該完全相符，或要求保守的比對原則時，請使用這項比較。 此外，序數比較在決定結果時不會套用任何語言規則，因此是最快速的比較作業。  
  
 .NET 中的字串可以包含內嵌的 Null 字元。 序數和區分文化特性的比較 (包括使用不因文化特性而異的比較) 其中一個最明顯差異在於，內嵌 Null 字元在字串中的處理方式。 當您使用 <xref:System.String.Compare%2A?displayProperty=nameWithType> 和 <xref:System.String.Equals%2A?displayProperty=nameWithType> 方法來執行區分文化特性的比較 (包括使用不因文化特性而異的比較) 時，會忽略這些字元。 如此一來，在區分文化特性的比較中，即可將包含內嵌 Null 字元的字串視為等於不含這類字元的字串。  
  
> [!IMPORTANT]
> 雖然字串比較方法可以忽略內嵌的 Null 字元，但 <xref:System.String.Contains%2A?displayProperty=nameWithType>、 <xref:System.String.EndsWith%2A?displayProperty=nameWithType>、 <xref:System.String.IndexOf%2A?displayProperty=nameWithType>、 <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>和 <xref:System.String.StartsWith%2A?displayProperty=nameWithType> 之類的字串搜尋方法就不能這麼做了。  
  
 下列範例會針對字串 "Aa" 以及 "A" 和 "a" 之間包含數個內嵌 Null 字元的類似字串，執行區分文化特性比較，並示範如何讓兩個字串被視為相等。  
  
 [!code-csharp[Conceptual.Strings.BestPractices#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/embeddednulls1.cs#19)]
 [!code-vb[Conceptual.Strings.BestPractices#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/embeddednulls1.vb#19)]  
  
 不過，當您使用序數比較時，字串就不會被視為相等，如下列範例所示。  
  
 [!code-csharp[Conceptual.Strings.BestPractices#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/embeddednulls2.cs#20)]
 [!code-vb[Conceptual.Strings.BestPractices#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/embeddednulls2.vb#20)]  
  
 第二種最保守的方式是不區分大小寫的序數比較。 這些比較會忽略大部分的大小寫；例如，"windows" 符合 "Windows"。 當處理 ASCII 字元時，這項原則相當於 <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>，不過它會忽略一般 ASCII 大小寫。 因此，[A, Z] (\u0041-\u005A) 中的任何字元會符合 [a,z] (\u0061-\007A) 中的對應字元。 ASCII 範圍之外的大小寫會使用不因文化特性而異的資料表。 因此，下列比較：  
  
 [!code-csharp[Conceptual.Strings.BestPractices#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison2.cs#4)]
 [!code-vb[Conceptual.Strings.BestPractices#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison2.vb#4)]  
  
 相當於下列比較 (而且更快)：  
  
 [!code-csharp[Conceptual.Strings.BestPractices#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison2.cs#5)]
 [!code-vb[Conceptual.Strings.BestPractices#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison2.vb#5)]  
  
 這些比較仍非常快速。  
  
> [!NOTE]
> <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType>最能代表檔案系統、登錄機碼和值及環境變數的字串行為。  
  
 <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> 和 <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> 兩者都直接使用二進位值，最適合用來比對。 當您不確定比較設定時，請使用這兩個值的其中一個。 不過，因為它們是以位元組為單位逐一比較，所以不會依照語言排序次序來排序 (就像英文字典一樣)，而是採用二進位排序次序。 因此，在大多數內容當中，使用者看到的結果可能很奇怪。  
  
 不包含 <xref:System.String.Equals%2A?displayProperty=nameWithType> 引數 (包括等號比較運算子) 的 <xref:System.StringComparison> 多載是以序數語意為預設。 在任何情況下，我們建議您呼叫具有 <xref:System.StringComparison> 參數的多載。  
  
### <a name="string-operations-that-use-the-invariant-culture"></a>使用不因文化特性而異的字串作業  
 採用不因文化特性而異的比較會使用靜態 <xref:System.Globalization.CultureInfo.CompareInfo%2A> 屬性傳回的 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> 屬性。 這種行為在所有系統上都相同，它會將其範圍之外的任何字元轉譯成它認為是相等非變異字元的字元。 這項原則很適合跨文化特性來維護一套字串行為，但通常會產生非預期的結果。  
  
 採用不因文化特性而異的不分區大小寫比較，也會使用靜態 <xref:System.Globalization.CultureInfo.CompareInfo%2A> 屬性所傳回的靜態 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> 屬性來取得比較資訊。 這些轉譯的字元之間的任何大小寫差異都會被忽略。  
  
 使用 <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> 和 <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> 的比較在 ASCII 字串上的運作方式完全相同。 不過，對於必須解譯成一組位元組的字串， <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> 所做的語言決策就可能不適合。 由 `CultureInfo.InvariantCulture.CompareInfo` 物件使 <xref:System.String.Compare%2A> 方法將多組字元解譯成相等。 例如，下列等式在不因國別而異的文化特性之下有效：  
  
 InvariantCulture: a + ̊ = å  
  
 拉丁小寫字母 A 字元 "a" (\u0061) 在緊鄰著結合上圓圈字元 "+ " ̊" (\u030a) 時，解譯成拉丁小寫字母 A 帶上圓圈字元 "å" (\u00e5)。 如下列範例如示，這種行為不同於序數比較。  
  
 [!code-csharp[Conceptual.Strings.BestPractices#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison3.cs#15)]
 [!code-vb[Conceptual.Strings.BestPractices#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison3.vb#15)]  
  
 在解譯檔名、Cookie 或可能出現像 "å" 一樣的組合的其他任何字串時，序數比較仍然會展現最明確和最適當的行為。  
  
 權衡來看，不因國別而異的文化特性只有非常少的屬性，因此適合用於比較。 不過，它會以語言相關的方式進行比較，這樣無法保證符號完全相等，因而不適合在任何文化特性中顯示。 使用 <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> 來比較有幾個理由，其中之一是保持已排序的資料在不同文化特性下顯示時完全相同。 例如，如果包含已排序之顯示識別項清單的大型資料檔案伴隨一個應用程式，則加入這份清單需要插入非變異樣式排序。  
  
 [回到頁首](#top)  
  
<a name="choosing_a_stringcomparison_member_for_your_method_call"></a>   
## <a name="choosing-a-stringcomparison-member-for-your-method-call"></a>針對方法呼叫選擇 StringComparison 成員  
 下表列出語意字串內容與 <xref:System.StringComparison> 列舉成員的對應。  
  
|資料|行為|對應的 System.StringComparison<br /><br /> value|  
|----------|--------------|-----------------------------------------------------|  
|區分大小寫的內部識別項。<br /><br /> 在標準中區分大小寫的識別項，例如 XML 和 HTTP。<br /><br /> 區分大小寫的安全性相關設定。|位元組完全相符的非語言識別項。|<xref:System.StringComparison.Ordinal>|  
|不區分大小寫的內部識別項。<br /><br /> 在標準中區分大小寫的識別項，例如 XML 和 HTTP。<br /><br /> 檔案路徑。<br /><br /> 登錄機碼和值。<br /><br /> 環境變數。<br /><br /> 資源識別項 (例如控制代碼名稱)。<br /><br /> 不區分大小寫的安全性相關設定。|大小寫不重要的非語言識別項，特別是大部分 Windows 系統服務中儲存的資料。|<xref:System.StringComparison.OrdinalIgnoreCase>|  
|某些永續性、語言相關的資料。<br /><br /> 需要固定排序次序之語言資料的顯示。|仍與語言相關之不區分文化特性的資料。|<xref:System.StringComparison.InvariantCulture><br /><br /> -或-<br /><br /> <xref:System.StringComparison.InvariantCultureIgnoreCase>|  
|向使用者顯示的資料。<br /><br /> 大部分的使用者輸入。|需要當地語言自訂的資料。|<xref:System.StringComparison.CurrentCulture><br /><br /> -或-<br /><br /> <xref:System.StringComparison.CurrentCultureIgnoreCase>|  
  
 [回到頁首](#top)  
  
<a name="common_string_comparison_methods_in_the_net_framework"></a>   
## <a name="common-string-comparison-methods-in-net"></a>.NET 中常用的字串比較方法  
 下列各節描述字串比較最常用的方法。  
  
### <a name="stringcompare"></a>String.Compare  
 預設解譯： <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>。  
  
 由於是字串解譯最主要的作業，這些方法呼叫的所有執行個體都應該經過檢查，以決定字串應該根據目前文化特性來解譯，還是與文化特性分開 (符號形式)。 通常是後者，所以應該改用 <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> 比較。  
  
 由 <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> 屬性傳回的 <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> 類別也包含 <xref:System.Globalization.CompareInfo.Compare%2A> 方法，這個方法透過 <xref:System.Globalization.CompareOptions> 旗標列舉，提供大量比對選項 (序數、忽略空白字元、忽略假名類型等)。  
  
### <a name="stringcompareto"></a>String.CompareTo  
 預設解譯： <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>。  
  
 這個方法目前未提供任何指定 <xref:System.StringComparison> 類型的多載。 通常可以將這個方法轉換成建議的 <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> 形式。  
  
 實作 <xref:System.IComparable> 和 <xref:System.IComparable%601> 介面的類型會實作這個方法。 由於它不提供 <xref:System.StringComparison> 參數的選項，所以實作這些型別通常可讓使用者在建構函式中指定 <xref:System.StringComparer> 。 下列範例定義 `FileName` 類別，該類別的類別建構函式包含 <xref:System.StringComparer> 參數。 然後在 <xref:System.StringComparer> 方法中使用這個 `FileName.CompareTo` 物件。  
  
 [!code-csharp[Conceptual.Strings.BestPractices#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/api1.cs#6)]
 [!code-vb[Conceptual.Strings.BestPractices#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/api1.vb#6)]  
  
### <a name="stringequals"></a>String.Equals  
 預設解譯： <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>。  
  
 <xref:System.String> 類別可讓您呼叫靜態或執行個體 <xref:System.String.Equals%2A> 方法多載，或使用靜態等號比較運算子，以測試是否相等。 多載和運算子預設會使用序數比較。 然而，即使您想要執行序數比較，我們還是建議您呼叫明確指定 <xref:System.StringComparison> 型別的多載，這樣可以很輕鬆在程式碼中搜尋特定的字串解譯。  
  
### <a name="stringtoupper-and-stringtolower"></a>String.ToUpper 和 String.ToLower  
 預設解譯： <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>。  
  
 請小心使用這些方法，因為強制將字串轉換為大寫或小寫，通常是做為比較不區分大小寫字串時的輕微正規化。 如果是這樣，請考慮使用不區分大小寫的比較。  
  
 您也可以使用 <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> 和 <xref:System.String.ToLowerInvariant%2A?displayProperty=nameWithType> 方法。 <xref:System.String.ToUpperInvariant%2A> 是將大小寫正規化的標準方式。 使用 <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> 進行的比較在行為上由兩次呼叫所構成：在兩個字串引數上都呼叫 <xref:System.String.ToUpperInvariant%2A> ，然後使用 <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>進行比較。  
  
 特定文化特性中，也可以使用多載將表示該文化特性的 <xref:System.Globalization.CultureInfo> 物件傳遞至這個方法，以轉換為大寫和小寫。  
  
### <a name="chartoupper-and-chartolower"></a>Char.ToUpper 和 Char.ToLower  
 預設解譯： <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>。  
  
 這些方法的運作類似於上一節描述的 <xref:System.String.ToUpper%2A?displayProperty=nameWithType> 和 <xref:System.String.ToLower%2A?displayProperty=nameWithType> 方法。  
  
### <a name="stringstartswith-and-stringendswith"></a>String.StartsWith 和 String.EndsWith  
 預設解譯： <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>。  
  
 根據預設，這兩個方法都會執行區分文化特性的比較。  
  
### <a name="stringindexof-and-stringlastindexof"></a>String.IndexOf 和 String.LastIndexOf  
 預設解譯： <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>。  
  
 這些方法的預設多載在執行比較時，作法並不一致。 所有包含 <xref:System.String.IndexOf%2A?displayProperty=nameWithType> 參數的 <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> 和 <xref:System.Char> 方法都執行序數比較，但包含 <xref:System.String.IndexOf%2A?displayProperty=nameWithType> 參數的預設 <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> 和 <xref:System.String> 方法會執行區分文化特性的比較。  
  
 如果您呼叫 <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> 或 <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> 方法，並將要在目前執行個體中尋找的字串傳遞至這個方法，我們建議您呼叫明確指定 <xref:System.StringComparison> 類型的多載。 包含 <xref:System.Char> 引數的多載不允許您指定 <xref:System.StringComparison> 類型。  
  
 [回到頁首](#top)  
  
<a name="methods_that_perform_string_comparison_indirectly"></a>   
## <a name="methods-that-perform-string-comparison-indirectly"></a>間接執行字串比較的方法  
 有一些以字串比較為主要作業的非字串方法會使用 <xref:System.StringComparer> 類型。 <xref:System.StringComparer> 類別包含六個靜態屬性，這些屬性會傳回 <xref:System.StringComparer> 執行個體，而這些執行個體的 <xref:System.StringComparer.Compare%2A?displayProperty=nameWithType> 方法可以執行下列類型的字串比較：  
  
- 使用目前文化特性的區分文化特性字串比較。 這個 <xref:System.StringComparer> 物件是由 <xref:System.StringComparer.CurrentCulture%2A?displayProperty=nameWithType> 屬性傳回。  
  
- 使用目前文化特性的不區分大小寫比較。 這個 <xref:System.StringComparer> 物件是由 <xref:System.StringComparer.CurrentCultureIgnoreCase%2A?displayProperty=nameWithType> 屬性傳回。  
  
- 使用不因文化特性而異之字組比較規則的不區分文化特性比較。 這個 <xref:System.StringComparer> 物件是由 <xref:System.StringComparer.InvariantCulture%2A?displayProperty=nameWithType> 屬性傳回。  
  
- 使用不因文化特性而異之字組比較規則的不區分大小寫和文化特性比較。 這個 <xref:System.StringComparer> 物件是由 <xref:System.StringComparer.InvariantCultureIgnoreCase%2A?displayProperty=nameWithType> 屬性傳回。  
  
- 序數比較。 這個 <xref:System.StringComparer> 物件是由 <xref:System.StringComparer.Ordinal%2A?displayProperty=nameWithType> 屬性傳回。  
  
- 不區分大小寫的序數比較。 這個 <xref:System.StringComparer> 物件是由 <xref:System.StringComparer.OrdinalIgnoreCase%2A?displayProperty=nameWithType> 屬性傳回。  
  
### <a name="arraysort-and-arraybinarysearch"></a>Array.Sort 和 Array.BinarySearch  
 預設解譯： <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>。  
  
 當您將任何資料儲存在集合中，或從檔案或資料庫將保存的資料讀入集合時，切換目前文化特性會使集合中的非變異失效。 <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> 方法假設要搜尋之陣列中的項目已排序。 若要排序陣列中的任何字串項目， <xref:System.Array.Sort%2A?displayProperty=nameWithType> 方法會呼叫 <xref:System.String.Compare%2A?displayProperty=nameWithType> 方法來排序個別項目。 從排序陣列到搜尋其內容這段時間當中，如果文化特性變更，則使用區分文化特性的比較子可能會有危險。 例如，在下列程式碼中，儲存和擷取作業在 `Thread.CurrentThread.CurrentCulture` 屬性。 如果文化特性在呼叫 `StoreNames` 和 `DoesNameExist`之間可能變更，尤其是如果陣列內容在這兩個方法呼叫之間保存在某處，則二進位搜尋可能會失敗。  
  
 [!code-csharp[Conceptual.Strings.BestPractices#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#7)]
 [!code-vb[Conceptual.Strings.BestPractices#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#7)]  
  
 下列範例中顯示建議的變化，其中使用相同的序數 (不區分文化特性) 比較方法來排序和搜尋陣列。 在這兩個範例中，標記為 `Line A` 和 `Line B` 的程式碼行中反映程式碼變更。  
  
 [!code-csharp[Conceptual.Strings.BestPractices#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#8)]
 [!code-vb[Conceptual.Strings.BestPractices#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#8)]  
  
 如果跨文化特性來保存和移動這項資料，且使用排序向使用者呈現這項資料，則您可以考慮使用 <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType>，這在語言上的表現會提供較佳的使用者輸出，且不受未來文化特性變更所影響。 下列範例修改前兩個範例，改用不因國別而異的文化特性來排序和搜尋陣列。  
  
 [!code-csharp[Conceptual.Strings.BestPractices#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#9)]
 [!code-vb[Conceptual.Strings.BestPractices#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#9)]  
  
### <a name="collections-example-hashtable-constructor"></a>集合範例：雜湊表建構函式  
 第二個受到字串比較方式而影響作業的範例是雜湊字串。  
  
 下列範例將 <xref:System.Collections.Hashtable> 屬性所傳回的 <xref:System.StringComparer> 物件傳遞至 <xref:System.StringComparer.OrdinalIgnoreCase%2A?displayProperty=nameWithType> 物件，以將後者物件執行個體化。 因為衍生自 <xref:System.StringComparer> 的類別 <xref:System.StringComparer> 實作 <xref:System.Collections.IEqualityComparer> 介面，所以其 <xref:System.Collections.IEqualityComparer.GetHashCode%2A> 方法會用於計算雜湊資料表中之字串的雜湊程式碼。  
  
 [!code-csharp[Conceptual.Strings.BestPractices#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect2.cs#10)]
 [!code-vb[Conceptual.Strings.BestPractices#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect2.vb#10)]  
  
 [回到頁首](#top)  
  
<a name="Formatted"></a>   
## <a name="displaying-and-persisting-formatted-data"></a>顯示和保存格式化的資料

當您向使用者顯示非字串資料 (例如數字及日期和時間) 時，請採用使用者的文化特性設定進行格式化。 根據預設，下列所有項目都會在格式化作業中使用目前執行緒文化特性：

- [C#](../../csharp/language-reference/tokens/interpolated.md) 和 [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) 編譯器支援的插入字串。

- 使用 [C#](../../csharp/language-reference/operators/addition-operator.md#string-concatenation) 或 [Visual Basic](../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md ) 串連運算子或直接呼叫 <xref:System.String.Concat%2A?displayProperty=nameWithType> 方法的字串串連作業。

- <xref:System.String.Format%2A?displayProperty=nameWithType> 方法

- 數值類型以及日期和時間類型的 `ToString` 方法。

若要明確指定應使用指定的文化特性慣例或[不因文化特性而異](xref:System.Globalization.CultureInfo.InvariantCulture)來格式化字串，您可以執行下列動作：

- 使用 <xref:System.String.Format%2A?displayProperty=nameWithType> 和 `ToString` 方法時，呼叫具有 `provider` 參數的多載 (例如 <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> 或 <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType>)，並為該多載傳遞給 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> 屬性 (表示所需文化特性的 <xref:System.Globalization.CultureInfo> 執行個體) 或 <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType> 屬性。  

- 針對字串串連，不允許編譯器執行任何隱含的轉換。 反之，藉由呼叫具有 `provider` 參數的 `ToString` 多載來執行明確轉換。 例如，在將 <xref:System.Double> 值轉換為下列 C# 程式碼中的字串時，編譯器會隱含地使用目前文化特性：

  [!code-csharp[Implicit String Conversion](~/samples/snippets/standard/base-types/string-practices/cs/tostring.cs#1)]

  您可以藉由呼叫 <xref:System.Double.ToString(System.IFormatProvider)?displayProperty=nameWithType> 方法來明確指定在轉換中使用格式化慣例的文化特性，如下列 C# 程式碼所示：

  [!code-csharp[Explicit String Conversion](~/samples/snippets/standard/base-types/string-practices/cs/tostring.cs#2)]

- 針對字串內插補點，請將插入字串指派給 <xref:System.FormattableString> 執行個體，而非 <xref:System.String>。 接著，您可以呼叫其 <xref:System.FormattableString.ToString?displayProperty=nameWithType> 方法產生會反映目前文化特性慣例的結果字串，也可以呼叫 <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> 方法產生會反映指定文化特性慣例的結果字串。 您也可以將可格式化字串傳遞給靜態的 <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> 方法，以產生會反映不因文化特性而異之慣例的結果字串。 下列範例將示範這個方法。 (此範例的輸出反映 en-US 目前文化特性。)

  [!code-csharp[String interpolation](~/samples/snippets/standard/base-types/string-practices/cs/formattable.cs)]
  [!code-vb[String interpolation](~/samples/snippets/standard/base-types/string-practices/vb/formattable.vb)]

您可將非字串資料保存為二進位資料或格式化的資料。 如果您選擇將它儲存為格式化的資料，您應該呼叫包含 `provider` 參數之格式化方法的多載，並將 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> 屬性傳遞給它。 針對獨立於文化特性和機器的格式化資料，不因國別而異的文化特性可提供一致的格式。 相較之下，如果資料並非使用不因國別而異的文化特性，而是使用其他文化特性來進行格式化，這類資料的保存會有許多限制：  
  
- 如果在具有不同文化特性的系統上擷取資料，或者，目前系統的使用者變更目前的文化特性，並嘗試擷取資料時，該資料可能會無法使用。  
  
- 特定電腦上的文化特性屬性可能不同於標準值。 使用者可以隨時自訂區分文化特性的顯示設定。 因為這個緣故，使用者自訂文化特性設定之後，可能無法讀取系統上儲存的格式化資料。 格式化資料在電腦之間的可攜性可能會有更多限制。  
  
- 當數字或日期和時間格式的規範標準 (不論全球、地區或國際標準) 隨著時間變更時，這些變更會併入 Windows 作業系統更新當中。 當格式化慣例改變時，使用先前慣例來格式化的資料可能會變成無法讀取。  
  
 下列範例說明使用區分文化特性的格式來保存資料時產生的可攜性限制。 此範例會將日期和時間值陣列儲存至檔案。 這些值是使用英文 (美國) 文化特性的慣例來進行格式化。 當應用程式將目前執行緒文化特性變更為法文 (瑞士) 後，它會嘗試使用目前文化特性的格式化慣例來讀取儲存的值。 嘗試讀取這兩樣資料項目後，會擲回 <xref:System.FormatException> 例外狀況，且日期陣列現在會包含兩個等於 <xref:System.DateTime.MinValue>的不正確項目。  
  
 [!code-csharp[Conceptual.Strings.BestPractices#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/persistence.cs#21)]
 [!code-vb[Conceptual.Strings.BestPractices#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/persistence.vb#21)]  
  
 不過，如果您在 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> 和 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> 的呼叫中將 <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> 屬性取代為 <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>，則保存的日期和時間資料將會成功還原，如下列輸出所示。  
  
```console  
06.05.1758 21:26  
05.05.1818 07:19  
22.04.1870 23:54  
08.09.1890 06:47  
18.02.1905 15:12  
```  
  
## <a name="see-also"></a>另請參閱

- [操作字串](../../../docs/standard/base-types/manipulating-strings.md)
