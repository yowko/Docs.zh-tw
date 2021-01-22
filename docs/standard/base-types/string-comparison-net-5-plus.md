---
title: 比較 .NET 5 + 上的字串時的行為變更
description: 瞭解 Windows 上 .NET 5 和更新版本中的字串比較行為變更。
ms.topic: conceptual
ms.date: 12/07/2020
ms.openlocfilehash: 0db8477ce4e8c3a7167c719e2a29a32e5346a8e7
ms.sourcegitcommit: 4313614f57690f9a5119a37314f0a1fd738ebda2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2021
ms.locfileid: "98692691"
---
# <a name="behavior-changes-when-comparing-strings-on-net-5"></a>比較 .NET 5 + 上的字串時的行為變更

.NET 5.0 引進了執行時間行為變更，其中的全球化 Api 預設會在所有支援的平臺上 [使用 ICU](../../core/compatibility/globalization/5.0/icu-globalization-api.md) 。 這是舊版 .NET Core 和 .NET Framework 中的一項服務，它會在 Windows 上執行時，利用作業系統的國家語言支援 (NLS) 功能。 如需這些變更的詳細資訊，包括可還原行為變更的相容性參數，請參閱 [.net 全球化和 ICU](../globalization-localization/globalization-icu.md)。

## <a name="reason-for-change"></a>變更的原因

這是為了統一而引進的變更。在所有支援的作業系統上的淨全球化行為。 它也能讓應用程式組合自己的全球化程式庫，而不需要依賴作業系統的內建程式庫。 如需詳細資訊，請參閱 [重大變更通知](../../core/compatibility/globalization/5.0/icu-globalization-api.md)。

## <a name="behavioral-differences"></a>行為差異

如果您在 `string.IndexOf(string)` 不呼叫接受引數的多載的情況下使用像這樣的函 <xref:System.StringComparison> 式，您可能會想要執行 *序數* 搜尋，但您不小心相依于特定文化特性的行為。 由於 NLS 和 ICU 在其語言比較子中執行不同的邏輯，因此方法的結果 `string.IndexOf(string)` 可能會傳回非預期的值。

這可能會在您不希望全球化設施處於作用中的地方出現本身的資訊清單。 例如，下列程式碼可能會根據目前的執行時間產生不同的答案。

```cs
string s = "Hello\r\nworld!";
int idx = s.IndexOf("\n");
Console.WriteLine(idx);

// The snippet prints:
//
// '6' when running on .NET Framework (Windows)
// '6' when running on .NET Core 2.x - 3.x (Windows)
// '-1' when running on .NET 5 (Windows)
// '-1' when running on .NET Core 2.x - 3.x or .NET 5 (non-Windows)
// '6' when running on .NET Core 2.x or .NET 5 (in invariant mode)
```

## <a name="guard-against-unexpected-behavior"></a>防止非預期的行為

本節提供兩個選項來處理 .NET 5.0 中非預期的行為變更。

### <a name="enable-code-analyzers"></a>啟用程式碼分析器

程式[代碼分析器](../../fundamentals/code-analysis/overview.md)可以偵測到可能有錯誤的呼叫網站。 為了防止任何令人驚訝的行為，建議您在專案中啟用 .NET 編譯器平臺 (Roslyn) 分析器。 當有可能想要使用序數比較子時，分析器會協助旗標可能會不慎使用語言比較子的程式碼。 下列規則應有助於將這些問題加上旗標：

- [CA1307:指定 StringComparison 以提升明確性](../../fundamentals/code-analysis/quality-rules/ca1307.md)
- [CA1309:使用循序的 StringComparison](../../fundamentals/code-analysis/quality-rules/ca1309.md)
- [CA1310：指定 StringComparison 以提升正確性](../../fundamentals/code-analysis/quality-rules/ca1310.md)

預設不會啟用這些特定規則。 若要啟用它們並將任何違規顯示為組建錯誤，請在您的專案檔中設定下列屬性：

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
  <WarningsAsErrors>$(WarningsAsErrors);CA1307;CA1309;CA1310</WarningsAsErrors>
</PropertyGroup>
```

下列程式碼片段顯示的程式碼範例會產生相關的程式碼分析器警告或錯誤。

```cs
//
// Potentially incorrect code - answer might vary based on locale.
//
string s = GetString();
// Produces analyzer warning CA1310 for string; CA1307 matches on char ','
int idx = s.IndexOf(",");
Console.WriteLine(idx);

//
// Corrected code - matches the literal substring ",".
//
string s = GetString();
int idx = s.IndexOf(",", StringComparison.Ordinal);
Console.WriteLine(idx);

//
// Corrected code (alternative) - searches for the literal ',' character.
//
string s = GetString();
int idx = s.IndexOf(',');
Console.WriteLine(idx);
```

同樣地，當具現化已排序的字串集合或排序現有的以字串為基礎的集合時，請指定明確的比較子。

```cs
//
// Potentially incorrect code - behavior might vary based on locale.
//
SortedSet<string> mySet = new SortedSet<string>();
List<string> list = GetListOfStrings();
list.Sort();

//
// Corrected code - uses ordinal sorting; doesn't vary by locale.
//
SortedSet<string> mySet = new SortedSet<string>(StringComparer.Ordinal);
List<string> list = GetListOfStrings();
list.Sort(StringComparer.Ordinal);
```

### <a name="revert-back-to-nls-behaviors"></a>還原回 NLS 行為

若要在 Windows 上執行時，將 .NET 5 應用程式還原回較舊的 NLS 行為，請依照 [.Net 全球化和 ICU](../globalization-localization/globalization-icu.md)中的步驟執行。 您必須在應用層級設定此整個應用程式的相容性參數。 個別程式庫無法加入宣告或退出此行為。

> [!TIP]
> 強烈建議您啟用 [CA1307](../../fundamentals/code-analysis/quality-rules/ca1307.md)、 [CA1309](../../fundamentals/code-analysis/quality-rules/ca1309.md)和 [CA1310](../../fundamentals/code-analysis/quality-rules/ca1310.md) 程式碼分析規則，以協助改善程式碼的防護，並探索任何現有的潛在錯誤。 如需詳細資訊，請參閱 [啟用程式碼分析器](#enable-code-analyzers)。

## <a name="affected-apis"></a>受影響的 API

大部分的 .NET 應用程式都不會因為 .NET 5.0 中的變更而遇到任何未預期的行為。 不過，由於受影響的 Api 數目以及這些 Api 在更廣泛的 .NET 生態系統中的基礎，您應該瞭解 .NET 5.0 可能會引入不想要的行為，或公開應用程式中已經存在的潛在 bug。

受影響的 Api 包括：

- <xref:System.String.Compare%2A?displayProperty=fullName>
- <xref:System.String.EndsWith%2A?displayProperty=fullName>
- <xref:System.String.IndexOf%2A?displayProperty=fullName>
- <xref:System.String.StartsWith%2A?displayProperty=fullName>
- <xref:System.String.ToLower%2A?displayProperty=fullName>
- <xref:System.String.ToLowerInvariant%2A?displayProperty=fullName>
- <xref:System.String.ToUpper%2A?displayProperty=fullName>
- <xref:System.String.ToUpperInvariant%2A?displayProperty=fullName>
- <xref:System.Globalization.TextInfo?displayProperty=fullName> (大部分的成員) 
- <xref:System.Globalization.CompareInfo?displayProperty=fullName> (大部分的成員) 
- <xref:System.Array.Sort%2A?displayProperty=fullName> 排序字串陣列時 () 
- <xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> 當清單元素是字串時 () 
- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> 當索引鍵為字串時 () 
- <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> 當索引鍵為字串時 () 
- <xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> 當集合包含字串時 () 

> [!NOTE]
> 這不是受影響 Api 的詳盡清單。

上述所有 Api 預設會使用執行緒 [目前的文化](xref:System.Threading.Thread.CurrentCulture)特性進行 *語言* 字串搜尋和比較。 *語言* 和 *序數* 搜尋和比較之間的差異會在 [序數與語言搜尋和比較](#ordinal-vs-linguistic-search-and-comparison)中呼叫。

由於 ICU 會以不同于 NLS 的方式來執行語言字串比較，因此從舊版 .NET Core 或 .NET Framework 升級至 .NET 5.0 的 Windows 架構應用程式，以及呼叫其中一個受影響的 Api，可能會注意到 Api 開始出現不同的行為。

### <a name="exceptions"></a>例外狀況

* 如果 API 接受明確 `StringComparison` 或 `CultureInfo` 參數，該參數會覆寫 API 的預設行為。
* `System.String` 第一個參數屬於 (類型的成員 `char` ， <xref:System.String.IndexOf(System.Char)?displayProperty=nameWithType> 除非呼叫端傳遞明確 `StringComparison` 的引數來指定或，否則) 使用序數搜尋 `CurrentCulture[IgnoreCase]` `InvariantCulture[IgnoreCase]` 。

如需每個 API 預設行為的詳細分析 <xref:System.String> ，請參閱 [預設搜尋和比較類型](#default-search-and-comparison-types) 一節。

## <a name="ordinal-vs-linguistic-search-and-comparison"></a>序數與語言搜尋和比較

*序數* (也稱為 *非語言* 的) 搜尋和比較分解將字串轉換成個別的 `char` 元素，並執行逐字元搜尋或比較。 例如，在比較子 `"dog"` 下，字串和 `"dog"` 比較為 *相等* `Ordinal` ，因為兩個字串包含的字元順序完全相同。 但是， `"dog"` 和 `"Dog"` 比較 *不等於* 比較子 `Ordinal` ，因為它們不是由相同的字元序列所組成。 也就是說，大寫的程式碼 `'D'` 點 `U+0044` 會在小寫 `'d'` 的程式碼點之前發生 `U+0064` ，因此會 `"dog"` 先排序 `"Dog"` 。

`OrdinalIgnoreCase`比較子的運作方式仍是逐字元，但是在執行作業時，它會消除大小寫差異。 在比較子下 `OrdinalIgnoreCase` ，char 組 `'d'` 和 `'D'` 比較為 *相等*，與 char 配對 `'á'` 和 `'Á'` 。 但是非重音字元 `'a'` 會比較為 *不等於* 重音字元 `'á'` 。

下表提供一些範例：

| 字串 1 | 字串2 | `Ordinal` 比較 | `OrdinalIgnoreCase` 比較 |
|---|---|---|---|
| `"dog"` | `"dog"` | equal | equal |
| `"dog"` | `"Dog"` | 不等於 | equal |
| `"resume"` | `"Resume"` | 不等於 | equal |
| `"resume"` | `"résumé"` | 不等於 | 不等於 |

Unicode 也可讓字串擁有數個不同的記憶體內部標記法。 例如，您可以使用兩種可能的方式來表示電子銳 (日) ：

* 單一常值 `'é'` 字元 (也會寫入為 `'\u00E9'`) 。
* 常值的非重音 `'e'` 字元，後面接著結合輔色修飾詞字元 `'\u0301'` 。

這表示，在顯示時，下列 _四個_ 字串都會 `"résumé"` 出現，即使它們的組成片段不同也一樣。 字串會使用常值 `'é'` 字元或常值非重音 `'e'` 字元以及合併輔色修飾詞的組合 `'\u0301'` 。

* `"r\u00E9sum\u00E9"`
* `"r\u00E9sume\u0301"`
* `"re\u0301sum\u00E9"`
* `"re\u0301sume\u0301"`

在序數比較子下，這些字串的比較都不會相等。 這是因為它們都包含不同的基礎 char 序列，雖然它們會在螢幕上呈現時，但全都看起來相同。

執行作業時 `string.IndexOf(..., StringComparison.Ordinal)` ，執行時間會尋找完全相符的子字串。 結果如下所示。

```cs
Console.WriteLine("resume".IndexOf("e", StringComparison.Ordinal)); // prints '1'
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e", StringComparison.Ordinal)); // prints '-1'
Console.WriteLine("r\u00E9sume\u0301".IndexOf("e", StringComparison.Ordinal)); // prints '5'
Console.WriteLine("re\u0301sum\u00E9".IndexOf("e", StringComparison.Ordinal)); // prints '1'
Console.WriteLine("re\u0301sume\u0301".IndexOf("e", StringComparison.Ordinal)); // prints '1'
Console.WriteLine("resume".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '1'
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '-1'
Console.WriteLine("r\u00E9sume\u0301".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '5'
Console.WriteLine("re\u0301sum\u00E9".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '1'
Console.WriteLine("re\u0301sume\u0301".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '1'
```

序數搜尋和比較常式絕不會受到目前線程的文化特性設定影響。

*語言* 搜尋和比較常式會將字串分解成定 *序元素* ，並對這些元素執行搜尋或比較。 字串字元與其組成定序專案之間不一定要有1:1 對應。 例如，長度為2的字串只能包含單一定序元素。 當兩個字串以語言感知的方式進行比較時，比較子會檢查兩個字串的定序專案是否具有相同的語義意義，即使字串的常值字元不同也是一樣。

請再次考慮字串 `"résumé"` 和其四種不同的標記法。 下表顯示每個標記法細分為其定序元素。

| String | 作為定序元素 |
|---|---|
| `"r\u00E9sum\u00E9"` | `"r" + "\u00E9" + "s" + "u" + "m" + "\u00E9"` |
| `"r\u00E9sume\u0301"` | `"r" + "\u00E9" + "s" + "u" + "m" + "e\u0301"` |
| `"re\u0301sum\u00E9"` | `"r" + "e\u0301" + "s" + "u" + "m" + "\u00E9"` |
| `"re\u0301sume\u0301"` | `"r" + "e\u00E9" + "s" + "u" + "m" + "e\u0301"` |

定序專案相當於讀取器想要做為單一字元或字元叢集的內容。 它在概念上類似于 [語素簇](character-encoding-introduction.md#grapheme-clusters) 叢集，但包含較大的傘。

在語言比較子下，不需要完全相符。 定序專案會根據其語義意義而比較。 例如，語言比較子會將子字串 `"\u00E9"` 視為 `"e\u0301"` 相等，因為兩者都是以語義表示 "a 小寫 e with a 銳角修飾詞 這可讓 `IndexOf` 方法 `"e\u0301"` 比對包含語義相等子字串的大型字串中的子字串 `"\u00E9"` ，如下列程式碼範例所示。

```cs
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e")); // prints '-1' (not found)
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e\u00E9")); // prints '1'
Console.WriteLine("\u00E9".IndexOf("e\u00E9")); // prints '0'
```

如此一來，如果使用語言比較，則兩個不同長度的字串可能會比較相等。 呼叫端應該小心處理在這類案例中處理字串長度的特殊案例邏輯。

*文化特性感知* 搜尋和比較常式是一種特殊形式的語言搜尋和比較常式。 在可感知文化特性的比較子中，定序專案的概念會延伸，以包含指定文化特性的特定資訊。

例如， [在匈牙利文的字母中](https://en.wikipedia.org/wiki/Hungarian_alphabet)，當兩個字元 \<dz\> 再次出現時，它們會被視為與或不同的唯一字母 \<d\> \<z\> 。 這表示 \<dz\> 在字串中看到時，匈牙利文文化特性感知比較子會將它視為單一定序元素。

| String | 作為定序元素 | 備註 |
|---|---|---|
| `"endz"` | `"e" + "n" + "d" + "z"` | 使用標準語言比較子的 ()  |
| `"endz"` | `"e" + "n" + "dz"` |  (使用匈牙利文化特性感知比較子)  |

使用匈牙利文化特性感知比較子時，這表示字串不 `"endz"` *會* 以子字串結尾 `"z"` ，因為 < \dz \> 和 < \z \> 視為具有不同語義意義的定序元素。

```cs
// Set thread culture to Hungarian
CultureInfo.CurrentCulture = CultureInfo.GetCultureInfo("hu-HU");
Console.WriteLine("endz".EndsWith("z")); // Prints 'False'

// Set thread culture to invariant culture
CultureInfo.CurrentCulture = CultureInfo.InvariantCulture;
Console.WriteLine("endz".EndsWith("z")); // Prints 'True'
```

> [!NOTE]
>
> - 行為：語言和文化特性感知的比較子可能會在一段時間後進行行為調整。 ICU 和舊版 Windows NLS 設備都會更新，以說明世界語言的變化。 如需詳細資訊，請參閱 [ (文化特性) 資料](/archive/blogs/shawnste/locale-culture-data-churn)變換的 Blog 文章地區設定。 *序數* 比較子的行為永遠不會變更，因為它會執行精確的位搜尋和比較。 不過， *OrdinalIgnoreCase* 比較子的行為可能會隨著 Unicode 的成長而改變，以包含更多的字元集並修正現有大小寫資料中的遺漏。
> - 使用方式：比較子 `StringComparison.InvariantCulture` 和 `StringComparison.InvariantCultureIgnoreCase` 是不感知文化特性的語言比較子。 也就是說，這些比較子可瞭解概念，像是日有多個可能基礎標記法的重音字元，而且所有這類標記法都應該視為相等。 但是，非文化特性感知的語言比較子不會包含 \<dz\> 與或不同的特殊處理 \<d\> \<z\> ，如上所示。 它們也不會有像德文 Eszett (ß) 這類特殊字元。

.NET 也提供不 *變的全球化模式*。 這個加入宣告模式會停用處理語言搜尋和比較常式的程式碼路徑。 在此模式中，所有作業都會使用 *序數* 或 *OrdinalIgnoreCase* 行為，不論呼叫端提供的是什麼 `CultureInfo` 或 `StringComparison` 引數。 如需詳細資訊，請參閱全球化和[.Net Core 全球化不變模式](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)[的執行時間設定選項](../../core/run-time-config/globalization.md)。

如需詳細資訊，請參閱 [在 .net 中比較字串的最佳做法](best-practices-strings.md)。

## <a name="security-implications"></a>安全性影響

如果您的應用程式使用受影響的 API 進行篩選，我們建議您啟用 CA1307 和 CA1309 程式碼分析規則，以協助找出可能不慎使用語言搜尋而非序數搜尋的位置。 如下所示的程式碼模式可能會受到安全性攻擊。

```cs
//
// THIS SAMPLE CODE IS INCORRECT.
// DO NOT USE IT IN PRODUCTION.
//
public bool ContainsHtmlSensitiveCharacters(string input)
{
    if (input.IndexOf("<") >= 0) { return true; }
    if (input.IndexOf("&") >= 0) { return true; }
    return false;
}
```

因為此 `string.IndexOf(string)` 方法預設會使用語言搜尋，所以字串可能會包含常值 `'<'` 或 `'&'` 字元，而且常式會傳回 `string.IndexOf(string)` `-1` ，表示找不到搜尋子字串。 程式碼分析規則 CA1307 和 CA1309 旗標，例如呼叫網站，並向開發人員發出潛在問題。

## <a name="default-search-and-comparison-types"></a>預設搜尋和比較類型

下表列出各種字串和類似字串的 Api 之預設搜尋和比較類型。 如果呼叫端提供明確 `CultureInfo` 或 `StringComparison` 參數，則會對任何預設值接受該參數。

| API | 預設行為 | 備註 |
|---|---|---|
| `string.Compare` | CurrentCulture | |
| `string.CompareTo` | CurrentCulture | |
| `string.Contains` | 序數 | |
| `string.EndsWith` | 序數 | 當第一個參數為) 時 (`char` |
| `string.EndsWith` | CurrentCulture | 當第一個參數為) 時 (`string` |
| `string.Equals` | 序數 | |
| `string.GetHashCode` | 序數 | |
| `string.IndexOf` | 序數 | 當第一個參數為) 時 (`char` |
| `string.IndexOf` | CurrentCulture | 當第一個參數為) 時 (`string` |
| `string.IndexOfAny` | 序數 | |
| `string.LastIndexOf` | 序數 | 當第一個參數為) 時 (`char` |
| `string.LastIndexOf` | CurrentCulture | 當第一個參數為) 時 (`string` |
| `string.LastIndexOfAny` | 序數 | |
| `string.Replace` | 序數 | |
| `string.Split` | 序數 | |
| `string.StartsWith` | 序數 | 當第一個參數為) 時 (`char` |
| `string.StartsWith` | CurrentCulture | 當第一個參數為) 時 (`string` |
| `string.ToLower` | CurrentCulture | |
| `string.ToLowerInvariant` | InvariantCulture | |
| `string.ToUpper` | CurrentCulture | |
| `string.ToUpperInvariant` | InvariantCulture | |
| `string.Trim` | 序數 | |
| `string.TrimEnd` | 序數 | |
| `string.TrimStart` | 序數 | |
| `string == string` | 序數 | |
| `string != string` | 序數 | |

與 `string` api 不同的 `MemoryExtensions` 是，所有 api 預設會執行 *序數* 搜尋和比較，但有下列例外狀況。

| API | 預設行為 | 備註 |
|---|---|---|
| `MemoryExtensions.ToLower` | CurrentCulture | 傳遞 null `CultureInfo` 引數時 ()  |
| `MemoryExtensions.ToLowerInvariant` | InvariantCulture | |
| `MemoryExtensions.ToUpper` | CurrentCulture | 傳遞 null `CultureInfo` 引數時 ()  |
| `MemoryExtensions.ToUpperInvariant` | InvariantCulture | |

結果是，將程式碼轉換成取用的程式碼時 `string` `ReadOnlySpan<char>` ，可能會不慎引進行為變更。 範例如下所示。

```cs
string str = GetString();
if (str.StartsWith("Hello")) { /* do something */ } // this is a CULTURE-AWARE (linguistic) comparison

ReadOnlySpan<char> span = s.AsSpan();
if (span.StartsWith("Hello")) { /* do something */ } // this is an ORDINAL (non-linguistic) comparison
```

建議的解決方法是將明確 `StringComparison` 參數傳遞至這些 api。 程式碼分析規則 CA1307 和 CA1309 可以提供協助。

```cs
string str = GetString();
if (str.StartsWith("Hello", StringComparison.Ordinal)) { /* do something */ } // ordinal comparison

ReadOnlySpan<char> span = s.AsSpan();
if (span.StartsWith("Hello", StringComparison.Ordinal)) { /* do something */ } // ordinal comparison
```

## <a name="see-also"></a>另請參閱

- [全球化重大變更](../../core/compatibility/globalization.md)
- [在 .NET 中比較字串的最佳作法](best-practices-strings.md)
- [如何：在 C# 比較字串](../../csharp/how-to/compare-strings.md)
- [.NET 全球化和 ICU](../globalization-localization/globalization-icu.md)
- [序數與區分文化特性的字串作業](/dotnet/api/system.string#ordinal-vs-culture-sensitive-operations)
- [.NET source 程式碼分析總覽](../../fundamentals/code-analysis/overview.md)
