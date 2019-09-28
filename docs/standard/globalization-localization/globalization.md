---
title: 全球化
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- globalization [.NET Framework], about globalization
- global applications, globalization
- international applications [.NET Framework], globalization
- world-ready applications, globalization
- application development [.NET Framework], globalization
- culture, globalization
ms.assetid: 4e919934-6b19-42f2-b770-275a4fae87c9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce2f127858305a96b358c1661b98a359ae565f57
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71393128"
---
# <a name="globalization"></a>全球化

全球化涉及設計和開發世界性的應用程式，該類應用程式支援當地語系化的介面和地區資料，可供多種文化特性的使用者使用。 在開始設計階段之前，您應該先決定您的應用程式要支援哪些文化特性。 雖然應用程式將單一文化特性或區域作為預設，您仍可加以設計及撰寫，使其可輕易延伸至其他文化特性或地區的使用者。

身為開發人員，我們都會依據自身的文化特性對使用者介面及資料有所假設。 比方說，對位在美國且說英文的開發人員而言，將日期和時間資料以 `MM/dd/yyyy hh:mm:ss` 格式序列化為字串看起來非常合理。 然而，在不同文化特性的系統中將該字串還原序列化，則可能會擲回 <xref:System.FormatException> 例外狀況或產生不正確的資料。 全球化可讓我們辨識這類特定文化特性的假設，並確保其不會影響應用程式的設計或程式碼。

本文探討一些您應該考量的重要問題及您可遵循的最佳做法，範圍包括處理全球化應用程式中字串、日期和時間值，及數值。

## <a name="strings"></a>字串

由於各個文化特性或地區可能使用不同的字元和字元集，並以不同的方式加以排序，因此全球化會將處理字元和字串列入核心焦點。 本節提供在全球化應用程式中使用字串的建議。

### <a name="use-unicode-internally"></a>在內部使用 Unicode

根據預設，.NET 會使用 Unicode 字串。 Unicode 字串包含零個、一個或多個 <xref:System.Char> 物件，每個皆代表一個 UTF-16 程式碼單位。 有項全球使用的 Unicode 表示法適用於近乎每個字元集中的每個字元。

包括 Windows 作業系統在內的許多應用程式和作業系統，也可以使用字碼頁代表字元集。 字碼頁通常包含 0x00 到 0x7F 的標準 ASCII 值，並將其他字元對應到其餘從 0x80 到 0xFF 的值。 0x80 到 0xFF 值的解譯取決於特定字碼頁。 因此，您應該盡可能避免在全球化應用程式中使用字碼頁。

下列範例說明在系統上的預設字碼頁與儲存資料的字碼頁不同的情況下，解譯字碼頁資料所可能造成的危險性。 (為了模擬這項案例，此範例明確地指定不同的字碼頁。)首先，此範例會定義由希臘文字母大寫字元所組成的陣列。 它使用字碼頁 737 (也稱為 MS-DOS 希臘文) 將它們編碼成位元組陣列，並將其儲存至檔案。 如果擷取檔案，並使用字碼頁 737 將位元組陣列解碼，則會還原原始的字元。 然而，如果擷取檔案但使用字碼頁 1252 (也稱作 Windows-1252，代表拉丁字母的字元) 將位元組陣列解碼，則會遺失原始的字元。

[!code-csharp[Conceptual.Globalization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/codepages1.cs#1)]
[!code-vb[Conceptual.Globalization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/codepages1.vb#1)]

使用 Unicode 可確保相同的字碼單位一律對應到相同的字元，且相同的字元一律對應到相同的位元組陣列。

### <a name="use-resource-files"></a>使用資源檔

即使您正在開發的應用程式將單一文化特性或地區作為目標，您也應該使用資源檔來儲存字串及使用者介面中顯示的其他資源。 請一律不要將它們直接新增至您的程式碼。 使用資源檔有許多優點︰

- 所有的字串皆位於單一位置。 您不必搜尋整個原始程式碼，即可識別要針對特定語言或文化特性修改的字串。

- 無須複製字串。 開發人員若不使用資源檔，則通常會在多個原始程式碼檔中定義相同的字串。 此類的複製會增加修改字串時，忽略一或多個執行個體的機率。

- 您可以在資源檔中包含如影像或二進位資料等非字串資源，而無須將其儲存在個別的獨立檔案，進而輕鬆加以擷取。

如果您要建立當地語系化的應用程式，則使用資源檔具有特定的優點。 當您部署附屬組件中的資源時，通用語言執行平台會根據 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> 屬性所定義的使用者目前 UI 文化特性，自動選取適當的文化特性資源。 只要提供適當的特定文化特性資源，並正確地將 <xref:System.Resources.ResourceManager> 物件具現化或使用強型別的資源類別，執行階段即會處理擷取適當資源的細項。

如需有關建立資源檔的詳細資訊，請參閱[建立資源檔](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)。 如需有關建立及部署附屬組件的資訊，請參閱[建立附屬組件](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)和[封裝和部署資源](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)。

### <a name="search-and-compare-strings"></a>搜尋及比較字串

您應盡可能將字串作為完整的字串處理，而不是作為連續的個別字串處理。 這在排序或搜尋子字串時尤為重要，以避免發生剖析組合字元的相關問題。

> [!TIP]
> 您可以搭配 <xref:System.Globalization.StringInfo> 類別使用文字項目，而無須使用字串中的個別字元。

在字串搜尋和比較中，常見的錯誤是將字串視為字元的集合，且各個都由一個 <xref:System.Char> 物件表示。 事實上，單一字元可能由一個、兩個或多個 <xref:System.Char> 物件所形成。 若字母是由 Unicode 基本拉丁字元範圍 (U+0021 到 U+007E) 以外的字元所組成，則在此文化特性的字串中最常出現上述這類字元。 下列範例嘗試在字串中尋找拉丁大寫字母 A 帶抑音符號字元 (U+00C0) 的索引。 不過，此字元可以有兩種表示方式︰單一程式碼單位 (U+00C0)，或作為複合字元 (兩個程式碼單位：U+0021 與 U+007E)。 在此情況下，字元在字串執行個體中的表示方式為兩個 <xref:System.Char> 物件、U+0021 與 U+007E。 範例程式碼會呼叫 <xref:System.String.IndexOf%28System.Char%29?displayProperty=nameWithType> 和 <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> 多載，以在字串執行個體中尋找此字元的位置，但這些多載會傳回不同的結果。 第一個方法呼叫具有 <xref:System.Char> 引數；它會執行序數比較，因此找不到相符項目。 第二個呼叫具有 <xref:System.String> 引數；它會執行區分文化特性的比較，因此會找到相符項目。

[!code-csharp[Conceptual.Globalization#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/search1.cs#18)]
[!code-vb[Conceptual.Globalization#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/search1.vb#18)]

您可透過呼叫內含如 <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> 或 <xref:System.String.LastIndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> 等方法之 <xref:System.StringComparison> 參數的多載，進而避免此範例的模稜兩可情形 (呼叫至方法的兩個相似多載而傳回不同的結果)。

不過，搜尋不一定會區分文化特性。 如果搜尋的目的為制定安全性決策或是允許或不允許存取某些資源，則應為序數比較，如下一節所述。

### <a name="test-strings-for-equality"></a>測試字串是否相等

如果您想要測試兩個字串是否相等，而不是判斷其在排序次序方面的比較，請使用 <xref:System.String.Equals%2A?displayProperty=nameWithType> 方法，而不是使用如 <xref:System.String.Compare%2A?displayProperty=nameWithType> 或 <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType> 等字串比較方法。

若要有條件地存取某些資源，通常會執行相等比較。 例如，您可能會執行相等比較，以驗證密碼或確認檔案存在。 這類非語言比較應該一律是序數，而不區分文化特性。 一般而言，您應該使用 <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> 值 (適用於密碼等字串)，或 <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> 值 (適用於檔案名稱或 URI 等字串) 來呼叫執行個體 <xref:System.String.Equals%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> 方法或靜態 <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> 方法。

相等比較有時會涉及搜尋或子字串比較，而不是呼叫 <xref:System.String.Equals%2A?displayProperty=nameWithType> 方法。 在某些情況下，您可以使用子字串搜尋來判斷該子字串是否等於另一個字串。 如果這項比較的目的非關語言，仍應為序數而非區分文化特性的搜尋。

下列範例說明非語言資料的區分文化特性搜尋所帶來的危險。 `AccessesFileSystem` 方法設計用來禁止開頭為"FILE" 之子字串的 URI 存取檔案系統。 若要這樣做，它會使用字串 "FILE" 對 URI 開頭執行區分文化特性而不區分大小寫的比較。 因為存取檔案系統的 URI 可以使用 "FILE:" 或 "file:" 作為開頭，因此隱含假設該 "i" (U+0069) 一律為 "I" (U+0049) 的小寫對應項。 不過，在土耳其文和亞塞拜然文中，大寫版本的 "i" 為 "İ" (U+0130)。 有鑑於此差異，區分文化特性的比較可在應該禁止存取檔案系統時，允許予以使用。

[!code-csharp[Conceptual.Globalization#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals1.cs#12)]
[!code-vb[Conceptual.Globalization#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals1.vb#12)]

若要避免這個問題，您可以執行忽略大小寫的序數比較，如下列範例所示。

[!code-csharp[Conceptual.Globalization#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals2.cs#13)]
[!code-vb[Conceptual.Globalization#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals2.vb#13)]

### <a name="order-and-sort-strings"></a>順序及排序字串

一般而言，要在使用者介面中顯示的已排序字串應根據文化特性排序。 多數情況下，這類字串比較會在您呼叫如 <xref:System.Array.Sort%2A?displayProperty=nameWithType> 或 <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> 等可排序字串的方法時，由 .NET 隱含地處理。 根據預設，字串會使用目前文化特性的排序慣例來排序。 下列範例說明使用英文 (美國) 文化特性字串和瑞典文 (瑞典) 文化特性的慣例陣列來排序字串陣列時的差異。

[!code-csharp[Conceptual.Globalization#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sort1.cs#14)]
[!code-vb[Conceptual.Globalization#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sort1.vb#14)]

區分文化特性的字串比較由 <xref:System.Globalization.CompareInfo> 物件定義，其由各個文化特性的 <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> 屬性傳回。 使用 <xref:System.String.Compare%2A?displayProperty=nameWithType> 方法多載的區分文化特性字串比較同時也使用 <xref:System.Globalization.CompareInfo> 物件。

.NET 會使用資料表對字串資料執行區分文化特性 (Culture) 的排序。 這些資料表的內容包含排序權數以及字串正規化的資料，且由特定 .NET 版本實作的 Unicode Standard 版本決定。 下表列出由 .NET Framework 及 .NET Core 指定版本實作的 Unicode 版本。 請注意，這份支援的 Unicode 版本清單僅適用於字元比較和排序，並不適用於依類別來分類 Unicode 字元。 如需詳細資訊，請參閱 <xref:System.String> 文章中的＜字串及 Unicode 標準＞一節。

|.NET Framework 版本|作業系統|Unicode 版本|
|----------------------------|----------------------|---------------------|
|.NET Framework 2.0|所有作業系統|Unicode 4.1|
|.NET Framework 3.0|所有作業系統|Unicode 4.1|
|.NET Framework 3.5|所有作業系統|Unicode 4.1|
|.NET Framework 4|所有作業系統|Unicode 5.0|
|Windows 7 上的 .NET Framework 4.5 及更新版本|Unicode 5.0|
|Windows 8 及更新作業系統上的 .NET Framework 4.5 及更新版本|Unicode 6.3.0|
|.NET Core (所有版本)|取決於基礎作業系統所支援的 Unicode Standard 版本。|

在所有版本的 .NET Core 以及 4.5 版以上的 .NET Framework 中，字串比較和排序都會視作業系統而定。 在 Windows 7 上執行的 .NET Framework 4.5 及更新版本，會從其本身實作 Unicode 5.0 的資料表擷取資料。 在 Windows 8 上執行的 .NET Framework 4.5 及更新版本，會從實作 Unicode 6.3 的作業系統資料表擷取資料。 在 .NET Core 上，支援的 Unicode 版本取決於基礎作業系統。 如果您將區分文化特性 (Culture) 的已排序資料序列化，便可使用 <xref:System.Globalization.SortVersion> 類別判斷何時需要排序序列化的資料，使其與 .NET 及作業系統的排序次序一致。 如需範例，請參閱 <xref:System.Globalization.SortVersion> 類別主題。

如果您的應用程式執行字串資料的廣泛特定文化特性排序，則可使用 <xref:System.Globalization.SortKey> 類別來比較字串。 排序鍵會反映特定文化特性排序權數，包括字母、大小寫及特定字串的變音符號權數。 由於比較所使用的排序鍵為二進位，因此與隱含或明確使用 <xref:System.Globalization.CompareInfo> 物件的比較相比更為快速。 您透過將字串傳遞至 <xref:System.Globalization.CompareInfo.GetSortKey%2A?displayProperty=nameWithType> 方法，進而為特定字串建立特定文化特性的排序鍵。

下列範例類似於先前的範例。 不過，它會定義 <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> 實作，該實作會比較加以具現化並傳遞給 <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Collections.Generic.IComparer%7B%60%600%7D%29?displayProperty=nameWithType> 方法的排序鍵，而不是呼叫會隱含呼叫 <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType> 方法的 <xref:System.Array.Sort%28System.Array%29?displayProperty=nameWithType> 方法。

[!code-csharp[Conceptual.Globalization#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sortkey1.cs#15)]
[!code-vb[Conceptual.Globalization#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sortkey1.vb#15)]

### <a name="avoid-string-concatenation"></a>避免字串串連

請盡可能避免使用在執行階段建置和來自連結字詞的複合字串。 複合字串很難進行當地語系化，因為它們通常會使用應用程式的原始語言文法順序，而該文法順序不適用於其他當地語系化語言。

## <a name="handle-dates-and-times"></a>處理日期和時間

處理日期和時間值的方式取決於其是否會顯示在使用者介面中或是受到保存。 本節將探討這兩種使用方式。 同時討論如何處理時區差異及使用日期和時間時的算術運算。

### <a name="display-dates-and-times"></a>顯示日期和時間

一般而言，當日期和時間在使用者介面中顯示時，您應採用使用者文化特性的格式化慣例，其由 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> 屬性及 `CultureInfo.CurrentCulture.DateTimeFormat` 屬性所傳回的 <xref:System.Globalization.DateTimeFormatInfo> 物件所定義。 當您使用下列任何一種方法將日期格式化時，將自動使用目前文化特性的格式化慣例︰

- 無參數的 <xref:System.DateTime.ToString?displayProperty=nameWithType> 方法

- <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> 方法，其中包含格式字串

- 無參數的 <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType> 方法

- <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType>，其中包含格式字串

- [複合格式化](../../../docs/standard/base-types/composite-formatting.md)功能，搭配日期使用時

下列範例顯示兩次 2012 年 10 月 11 日的日出和日落資料。 首先將目前文化特性設為克羅埃西亞文 (克羅埃西亞)，然後再設為英文 (英國)。 在每個案例中，日期和時間會以適用於該文化特性的格式顯示。

[!code-csharp[Conceptual.Globalization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates1.cs#2)]
[!code-vb[Conceptual.Globalization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates1.vb#2)]

### <a name="persist-dates-and-times"></a>保存日期和時間

您的日期和時間資料保存格式一律不應因文化特性而有所不同。 此項常見的程式設計錯誤會導致資料損毀或發生執行階段例外狀況。 下列範例使用英文 (美國) 文化特性的格式化慣例，將 2013 年 1 月 9 日和 2013 年 8 月 18 日這兩個日期作為字串序列化。 使用英文 (美國) 文化特性的慣例擷取和剖析資料時，它會成功還原。 不過，使用英文 (英國) 文化特性的慣例擷取和剖析資料時，第一個日期會錯誤解譯為 9 月 1 日，而第二個日期會因為西曆沒有第十八個月而無法剖析。

[!code-csharp[Conceptual.Globalization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates2.cs#3)]
[!code-vb[Conceptual.Globalization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates2.vb#3)]

您可以使用以下任何一種方式避免此問題︰

- 以二進位格式將日期和時間序列化，而不是作為字串。

- 透過使用無論使用者的文化特性為何皆相同的自訂格式字串，儲存並剖析日期和時間的字串表示。

- 使用不區分文化特性的格式化慣例儲存字串。

下列範例將示範最後一項方法。 它使用靜態 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> 屬性所傳回的不區分文化特性的格式化慣例。

[!code-csharp[Conceptual.Globalization#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates3.cs#4)]
[!code-vb[Conceptual.Globalization#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates3.vb#4)]

### <a name="serialization-and-time-zone-awareness"></a>序列化和時區感知

日期和時間值可以有多個解譯，範圍從一般的時間 (「商店營業時間開始於 2013 年 1 月 2 日上午 9:00」) 到特定時間點 (「出生日期：2013 年 1 月 2 日上午 6:32:00」)。 當時間值代表特定時間點，且您將其從序列化的值還原時，您應確定它代表相同的時間點，無論使用者的地理位置或時區皆然。

下列範例說明此問題。 它會以三個[標準格式](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) (一般日期完整時間為 "G"、可排序日期/時間為 "s"，而來回日期/時間為 "o") 以及二進位格式，將單一本地日期和時間值當作字串儲存。

[!code-csharp[Conceptual.Globalization#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates4.cs#10)]
[!code-vb[Conceptual.Globalization#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates4.vb#10)]

當資料還原所在的系統與序列化所在的系統時區相同時，已還原序列化的日期和時間值會正確地反映原始值，如輸出所示︰

```console
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00.0000000-07:00' --> 3/30/2013 6:00:00 PM Local

3/30/2013 6:00:00 PM Local
```

不過，如果資料還原所在的系統時區不同，則只有使用 "o" (來回) 標準格式字串格式化的日期和時間值才會保存時區資訊，並因此代表相同的即時時間。 以下輸出為在羅馬標準時區系統上還原日期和時間資料︰

```console
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local

3/30/2013 6:00:00 PM Local
```

若要精確地反映代表單一時間點的時間和日期值，無論資料還原序列化所在系統的時區為何，您可以執行下列其中一項︰

- 使用 "o" (來回) 標準格式字串將值作為字串儲存。 然後在目標系統上將其還原序列化。

- 使用 "r" (RFC1123) 標準格式字串，將它轉換成 UTC 並將其儲存為字串。 然後在目標系統上將其還原序列化，並將它轉換為本地時間。

- 使用 "u" (國際可排序) 標準格式字串，將它轉換成 UTC 並將其儲存為字串。 然後在目標系統上將其還原序列化，並將它轉換為本地時間。

- 將它轉換成 UTC，並以二進位格式儲存。 然後在目標系統上將其還原序列化，並將它轉換為本地時間。

下列範例將說明各個技術。

[!code-csharp[Conceptual.Globalization#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates8.cs#11)]
[!code-vb[Conceptual.Globalization#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates8.vb#11)]

當資料序列化所在的系統為太平洋標準時間時區，且還原序列化所在的系統為羅馬標準時區，此範例會顯示下列輸出︰

```console
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local
'Sun, 31 Mar 2013 01:00:00 GMT' --> 3/31/2013 3:00:00 AM Local
'2013-03-31 01:00:00Z' --> 3/31/2013 3:00:00 AM Local

3/31/2013 3:00:00 AM Local
```

如需詳細資訊，請參閱[在各時區間轉換時間](../../../docs/standard/datetime/converting-between-time-zones.md)。

### <a name="perform-date-and-time-arithmetic"></a>執行日期和時間運算

<xref:System.DateTime> 和 <xref:System.DateTimeOffset> 類型皆支援算術運算。 您可以計算兩個日期值之間的差異，或是可以加入或減去日期值的特定時間間隔。 不過，日期和時間值的算術運算並不會將時區和時區調整規則列入考量。 基於此原因，以分鐘表示時間的值日期和時間運算，可能會傳回不正確的結果。

比方說，從太平洋標準時間轉換為太平洋日光節約時間發生在 3 月的第二個星期日，也就是 2013 年 3 月 10 日。 如下列範例所示，如果您計算的日期和時間是系統上太平洋標準時區 2013 年 3 月 9 日上午 10:30 後的 48 小時， 則結果 2013 年 3 月 11 日上午 10:30 不會將中介時間調整列入考量。

[!code-csharp[Conceptual.Globalization#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates5.cs#8)]
[!code-vb[Conceptual.Globalization#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates5.vb#8)]

若要確保日期和時間值的算術運算會產生精確的結果，請依照下列步驟執行︰

1. 將來源時區的時間轉換成 UTC。

2. 執行算術運算。

3. 如果結果是日期和時間值，將其從 UTC 轉換至來源時區的時間。

下列範例類似於先前範例，不同之處在於它會依照這三個步驟，將 48 小時正確加入 2013 年 3 月 9 日上午 10:30。

[!code-csharp[Conceptual.Globalization#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates6.cs#9)]
[!code-vb[Conceptual.Globalization#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates6.vb#9)]

如需詳細資訊，請參閱[使用日期和時間執行算術運算](../../../docs/standard/datetime/performing-arithmetic-operations.md)。

### <a name="use-culture-sensitive-names-for-date-elements"></a>為日期元素使用區分文化特性 (Culture) 的名稱

您的應用程式可能需要顯示月份名稱或一週天數。 若要這樣做，如下所示的程式碼相當常見。

[!code-csharp[Conceptual.Globalization#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname1.cs#19)]
[!code-vb[Conceptual.Globalization#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname1.vb#19)]

不過，此程式碼一律會以英文傳回一周天數的名稱。 擷取月份名稱的程式碼通常更沒有彈性。 它通常會以特定語言的月份名稱假設 12 個月的行事曆。

透過使用[自訂日期和時間格式字串](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)或 <xref:System.Globalization.DateTimeFormatInfo> 物件的屬性，便可輕易擷取以使用者的文化特性反映一週天數或月份名稱的字串，如下列範例所示。 它將目前文化特性變更至法文 (法國)，並顯示 2013 年 7 月 1 日的一周天數名稱和月份名稱。

[!code-csharp[Conceptual.Globalization#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname2.cs#20)]
[!code-vb[Conceptual.Globalization#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname2.vb#20)]

## <a name="numeric-values"></a>數值

處理數字的方式取決於其是否會顯示在使用者介面中或是受到保存。 本節將探討這兩種使用方式。

> [!NOTE]
> 在剖析和格式化作業中，.NET 僅可將基本拉丁字元 0 到 9 (U+0030 到 U+0039) 作為數值辨識。

### <a name="display-numeric-values"></a>顯示數值

一般而言，當數字在使用者介面中顯示時，您應採用使用者文化特性的格式化慣例，其由 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> 屬性及 `CultureInfo.CurrentCulture.NumberFormat` 屬性所傳回的 <xref:System.Globalization.NumberFormatInfo> 物件所定義。 當您使用下列任何一種方法將日期格式化時，將自動使用目前文化特性的格式化慣例︰

- 任何數值類型的無參數 `ToString` 方法

- 任何數值類型的 `ToString(String)` 方法，包括作為引數的格式字串

- [複合格式化](../../../docs/standard/base-types/composite-formatting.md)功能，搭配數值使用時

下列範例顯示法國巴黎的每月平均溫度。 它在顯示資料前將目前文化特性設為法文 (法國)，然後將其設為英文 (美國)。 在每個案例中，月份名稱和溫度會以適用於該文化特性的格式顯示。 請注意兩個文化特性在溫度值中使用不同的小數分隔符號。 也請注意，此範例使用 "MMMM" 自訂日期和時間格式字串來顯示完整月份名稱，並藉由判斷 <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType> 陣列中最長月份名稱的長度，為結果字串中的月份名稱配置適當的空間量。

[!code-csharp[Conceptual.Globalization#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers1.cs#5)]
[!code-vb[Conceptual.Globalization#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers1.vb#5)]

### <a name="persist-numeric-values"></a>保存數值

請一律不要以文化特性特定格式保存數值資料。 此項常見的程式設計錯誤會導致資料損毀或發生執行階段例外狀況。 下列範例會產生 10 個隨機浮點數，並使用英文 (美國) 文化特性的格式化慣例，將其序列化為字串。 使用英文 (美國) 文化特性的慣例擷取和剖析資料時，它會成功還原。 不過，使用法文 (法國) 文化特性的慣例加以擷取及剖析時，沒有任何數字可供剖析，因為文化特性使用不同的小數分隔符號。

[!code-csharp[Conceptual.Globalization#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers2.cs#6)]
[!code-vb[Conceptual.Globalization#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers2.vb#6)]

若要避免這個問題，您可以使用其中一種方法︰

- 透過使用無論使用者的文化特性為何皆相同的自訂格式字串，儲存並剖析數字的字串表示。

- 使用 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> 屬性所傳回的不區分文化特性格式化慣例，將數字儲存為字串。

- 將數字序列化為二進位檔，而不是字串格式。

下列範例將示範最後一項方法。 其將 <xref:System.Double> 值的陣列序列化，然後還原序列化，並使用英文 (美國) 和法文 (法國) 文化特性的格式化慣例加以顯示。

[!code-csharp[Conceptual.Globalization#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers3.cs#7)]
[!code-vb[Conceptual.Globalization#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers3.vb#7)]

貨幣值的序列化是特殊的情況。 由於貨幣值取決於其表示所在的貨幣單位，因此將其視為獨立的數值並無太大意義。 不過，如果您將貨幣值儲存為包含貨幣符號的格式化字串，它無法在預設文化特性使用不同貨幣符號的預設系統上還原序列化，如下列範例所示。

[!code-csharp[Conceptual.Globalization#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency1.cs#16)]
[!code-vb[Conceptual.Globalization#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency1.vb#16)]

相反地，您應將數值及一些文化特性資訊 (例如文化特性名稱) 序列化，讓值和其貨幣符號可在目前文化特性獨立進行還原序列化。 下列範例透過使用兩個成員 (<xref:System.Decimal> 值和值所屬的文化特性名稱) 定義 `CurrencyValue` 結構來完成上述項目。

[!code-csharp[Conceptual.Globalization#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency2.cs#17)]
[!code-vb[Conceptual.Globalization#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency2.vb#17)]

## <a name="work-with-culture-specific-settings"></a>使用文化特性 (Culture) 專屬的設定

在 .NET 中，<xref:System.Globalization.CultureInfo> 類別代表特定文化特性 (Culture) 或地區。 其部分屬性會傳回物件，提供文化特性某些方面的特定資訊︰

- <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> 屬性會傳回 <xref:System.Globalization.CompareInfo> 物件，其包含文化特性如何比較和排序字串的相關資訊。

- <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> 屬性會傳回 <xref:System.Globalization.DateTimeFormatInfo> 物件，其提供將日期和時間資料格式化所使用的特定文化特性資訊。

- <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> 屬性會傳回 <xref:System.Globalization.NumberFormatInfo> 物件，其提供將數值資料格式化所使用的特定文化特性資訊。

- <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> 屬性會傳回 <xref:System.Globalization.TextInfo> 物件，其提供文化特性寫入系統的相關資訊。

一般情況下，請勿假設特定 <xref:System.Globalization.CultureInfo> 屬性和其相關物件的值。 相反地，您應將特定文化特性資料視為隨時有可能變更，理由如下︰

- 個別屬性值經過一段時間可能會有變更及修訂，原因包括資料經更正、有更好的資料可用，或特定文化特性慣例的變更。

- 個別屬性值可能會因 .NET 或作業系統版本而有所不同。

- .NET 支援取代文化特性 (Culture)。 這可讓您定義新的自訂文化特性，進而補充現有標準文化特性，或完全加以取代。

- 在 Windows 系統上，使用者可透過使用 [控制台] 中的 [地區和語言] 應用程式，自訂文化特性 (Culture) 專屬的設定。 將 <xref:System.Globalization.CultureInfo> 物件具現化時，您可透過呼叫 <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> 建構函式來判斷其是否反映這些使用者自訂。 一般對終端使用者應用程式而言，您應該遵守使用者喜好設定，並以使用者所預期的格式呈現資料。

## <a name="see-also"></a>另請參閱

- [全球化和當地語系化](../../../docs/standard/globalization-localization/index.md)
- [使用字串的最佳做法](../../../docs/standard/base-types/best-practices-strings.md)
