---
title: 使用日曆
ms.date: 04/01/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- globalization [.NET], calendars
- calendars, global applications
- global applications, calendars
- world-ready applications, calendars
- international applications [.NET], calendars
- culture, calendars
ms.assetid: 0c1534e5-979b-4c8a-a588-1c24301aefb3
ms.openlocfilehash: de8e5a03c769a22f3320c7785706555898bf8c1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400586"
---
# <a name="work-with-calendars"></a>使用日曆

雖然日期和時間值代表一個時間點，但是其字串表示區分文化特性，而且同時取決於用於顯示特定文化特性之日期和時間值的慣例，以及該文化特性所使用的曆法。 本主題將探討對 .NET 中日曆的支援，並討論在使用日期值時日曆類的使用。

## <a name="calendars-in-net"></a>.NET 中的日曆

.NET 中的所有日曆都派生自類<xref:System.Globalization.Calendar?displayProperty=nameWithType>，該類提供基本日曆實現。 其中一個衍生自 <xref:System.Globalization.Calendar> 類別的類別是 <xref:System.Globalization.EastAsianLunisolarCalendar> 類別，其為所有陰陽曆的基底類別。 .NET 包括以下日曆實現：

- <xref:System.Globalization.ChineseLunisolarCalendar>，表示中文陰陽曆。

- <xref:System.Globalization.GregorianCalendar>，表示西曆。 這個曆法會進一步細分成子類型 (例如阿拉伯和中東法文)，這些子類別是由 <xref:System.Globalization.GregorianCalendarTypes?displayProperty=nameWithType> 列舉類型所定義。 <xref:System.Globalization.GregorianCalendar.CalendarType%2A?displayProperty=nameWithType> 屬性會指定西曆的子類型。

- <xref:System.Globalization.HebrewCalendar>，表示希伯來曆法。

- <xref:System.Globalization.HijriCalendar>，表示回曆。

- <xref:System.Globalization.JapaneseCalendar>，表示日本曆法。

- <xref:System.Globalization.JapaneseLunisolarCalendar>，表示日文陰陽曆。

- <xref:System.Globalization.JulianCalendar>，表示凱撒曆法。

- <xref:System.Globalization.KoreanCalendar>，表示韓國曆法。

- <xref:System.Globalization.KoreanLunisolarCalendar>，表示韓文陰陽曆。

- <xref:System.Globalization.PersianCalendar>，表示波斯曆。

- <xref:System.Globalization.TaiwanCalendar>，表示台灣曆法。

- <xref:System.Globalization.TaiwanLunisolarCalendar>，表示台灣使用的陰陽曆。

- <xref:System.Globalization.ThaiBuddhistCalendar>，表示泰國佛教曆法。

- <xref:System.Globalization.UmAlQuraCalendar>，表示 Um Al Qura 曆法。

曆法的使用方式有兩種：

- 做為特定文化特性使用的曆法。 每個 <xref:System.Globalization.CultureInfo> 物件都有現行的曆法，也就是物件目前使用的曆法。 所有日期和時間值的字串表示都會自動反映目前的文化特性及其現行曆法。 通常現行曆法是文化特性的預設曆法。 <xref:System.Globalization.CultureInfo>物件還具有可選日曆，其中包括區域性可以使用的其他日曆。

- 做為與特定文化特性無關的獨立曆法。 這種情況下會使用 <xref:System.Globalization.Calendar> 方法以反映曆法的值表達日期。

請注意，這六種曆法類別 <xref:System.Globalization.ChineseLunisolarCalendar>、<xref:System.Globalization.JapaneseLunisolarCalendar>、<xref:System.Globalization.JulianCalendar>、<xref:System.Globalization.KoreanLunisolarCalendar>、<xref:System.Globalization.PersianCalendar> 和 <xref:System.Globalization.TaiwanLunisolarCalendar> 只能做為獨立曆法使用。 這些類別不會由任何文化特性做為預設曆法或選擇性曆法使用。

## <a name="calendars-and-cultures"></a>日曆和文化

每一種文化特性都有預設曆法，該曆法是由 <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> 屬性所定義。 <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> 屬性會傳回 <xref:System.Globalization.Calendar> 物件的陣列，該陣列會指定特定文化特性支援的所有曆法，包括該文化特性的預設曆法。

下列範例說明 <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> 和 <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> 屬性。 範例中會為泰文 (泰國) 和日文 (日本) 文化特性建立 `CultureInfo` 物件，並且顯示其預設和選擇性曆法。 請注意，在這兩種情況下，文化特性的預設曆法也會包含在 <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> 集合中。

[!code-csharp[Conceptual.Calendars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/calendarinfo1.cs#1)]
[!code-vb[Conceptual.Calendars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/calendarinfo1.vb#1)]

特定 <xref:System.Globalization.CultureInfo> 物件目前使用的曆法是由文化特性的 <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> 屬性定義。 文化特性的 <xref:System.Globalization.DateTimeFormatInfo> 物件是由 <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> 屬性所傳回。 建立文化特性時，其預設值與 <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> 屬性的值相同。 不過，您可以將文化特性的現行曆法變更為 <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> 屬性所傳回陣列中包含的任何曆法。 如果您嘗試將現行曆法設定為不包括在 <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> 屬性值中的曆法，則會顯示 <xref:System.ArgumentException>。

下列範例會變更阿拉伯文 (沙烏地阿拉伯) 文化特性使用的曆法。 首先會具現化 <xref:System.DateTime> 值，並且使用現行文化特性 (此案例中是英文 (美國)) 和目前文化特性的曆法 (此案例中是西曆) 顯示該值。 接著會將目前的文化特性變更為阿拉伯文 (沙烏地阿拉伯)，並且使用其預設的 Um Al-Qura 曆法顯示日期。 最後呼叫 `CalendarExists` 方法，判斷阿拉伯文 (沙烏地阿拉伯) 文化特性是否支援回曆。 由於支援此曆法，因此會將現行曆法變更為回曆，並且再次顯示日期。 請注意，在各案例中，日期會使用目前文化特性的現行曆法顯示。

[!code-csharp[Conceptual.Calendars#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/changecalendar2.cs#2)]
[!code-vb[Conceptual.Calendars#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/changecalendar2.vb#2)]

## <a name="dates-and-calendars"></a>日期和日曆

除了包括 <xref:System.Globalization.Calendar> 類型的參數且允許日期的項目 (也就是月、日和年) 以指定的曆法反映值的建構函式之外，<xref:System.DateTime> 和 <xref:System.DateTimeOffset> 這兩個值永遠以西曆為主。 例如，這表示 <xref:System.DateTime.Year%2A?displayProperty=nameWithType> 屬性會傳回西曆的年，而 <xref:System.DateTime.Day%2A?displayProperty=nameWithType> 屬性會傳回西曆的月份日期。

> [!IMPORTANT]
> 務必記得，日期值及其字串表示之間有一項差異。 前者是以西曆為主，後者是以特定文化特性的現行曆法為主。

下列範例會說明 <xref:System.DateTime> 屬性及其對應的 <xref:System.Globalization.Calendar> 方法之間的這項差異。 在此範例中，目前文化特性為阿拉伯文 (埃及)，而現行曆法為 Um Al Qura。 <xref:System.DateTime> 值會設定為 2011 年第七個月的第 15 天。 很清楚這個日期是解譯為西曆日期，因為這些相同值是 <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> 方法在使用不因文化特性而異的慣例時所傳回。 使用目前文化特性格式化之日期的字串表示為 14/08/32，其為 Um Al Qura 曆法的同等日期。 其次，`DateTime` 和 `Calendar` 的成員會用來傳回 <xref:System.DateTime> 值的日、月和年。 在各案例中，<xref:System.DateTime> 成員傳回的值會反映西曆的值，而 <xref:System.Globalization.UmAlQuraCalendar> 成員傳回的值則會反映 Uum al-Qura 曆法的值。

[!code-csharp[Conceptual.Calendars#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/datesandcalendars2.cs#3)]
[!code-vb[Conceptual.Calendars#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/datesandcalendars2.vb#3)]

### <a name="instantiate-dates-based-on-a-calendar"></a>基於日曆的具現化日期

由於 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 值是以西曆為主，因此，如果您想要使用不同曆法的日、月或年值，則必須呼叫包含 <xref:System.Globalization.Calendar> 類型之參數的多載建構函式來具現化日期值。 您也可以呼叫特定曆法之 <xref:System.Globalization.Calendar.ToDateTime%2A?displayProperty=nameWithType> 方法的其中一個多載，依據特殊曆法的值具現化 <xref:System.DateTime> 物件。

下列範例會藉由將 <xref:System.DateTime> 物件傳遞至 <xref:System.Globalization.HebrewCalendar> 建構函式具現化一個 <xref:System.DateTime> 值，並且藉由呼叫 <xref:System.DateTime> 方法具現化另一個 <xref:System.Globalization.HebrewCalendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> 值。 由於這兩個值是使用希伯來曆法的相同值所建立，因此呼叫 <xref:System.DateTime.Equals%2A?displayProperty=nameWithType> 方法會顯示這兩個 <xref:System.DateTime> 值相等。

[!code-csharp[Conceptual.Calendars#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatehcdate1.cs#4)]
[!code-vb[Conceptual.Calendars#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatehcdate1.vb#4)]

### <a name="represent-dates-in-the-current-calendar"></a>在當前日曆中表示日期

日期和時間格式化方法會固定使用現行曆法將日期轉換為字串。 這表示年、月和月份日期的字串表示會反映現行曆法，而且不一定會反映西曆。

下列範例顯示現行曆法如何影響日期的字串表示。 它會將目前文化特性變更為中文 (繁體，台灣)，並且具現化日期值。 接著會顯示現行曆法和日期，將現行曆法變更為 <xref:System.Globalization.TaiwanCalendar>，然後再次顯示現行曆法和日期。 第一次顯示日期時，該日期會以西曆日期表示。 第二次顯示日期時，該日期會以台灣曆法的日期表示。

[!code-csharp[Conceptual.Calendars#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/currentcalendar1.cs#5)]
[!code-vb[Conceptual.Calendars#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/currentcalendar1.vb#5)]

### <a name="represent-dates-in-a-non-current-calendar"></a>在非當前日曆中表示日期

若要使用不是特定文化特性的現行曆法來表示日期，您必須呼叫該 <xref:System.Globalization.Calendar> 物件的方法。 例如，<xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>、<xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType> 和 <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> 方法會將年、月和日轉換成反映特定曆法的值。

> [!WARNING]
> 由於某些曆法並非任何文化特性的選擇性曆法，因此使用這些曆法表示日期一定要呼叫曆法方法。 所有衍生自 <xref:System.Globalization.EastAsianLunisolarCalendar>、<xref:System.Globalization.JulianCalendar> 和 <xref:System.Globalization.PersianCalendar> 類別的曆法都要這樣做。

下列範例使用 <xref:System.Globalization.JulianCalendar> 物件具現化凱撒曆法的日期 1905 年 1 月 9 日。 使用預設曆法 (西曆) 顯示這個日期時，該日期會表示為 1905 年 1 月 22 日。 呼叫個別 <xref:System.Globalization.JulianCalendar> 方法即可使用凱撒曆法表示日期。

[!code-csharp[Conceptual.Calendars#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/noncurrentcalendar1.cs#6)]
[!code-vb[Conceptual.Calendars#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/noncurrentcalendar1.vb#6)]

### <a name="calendars-and-date-ranges"></a>日曆和日期範圍

曆法所支援的最早日期是由該曆法的 <xref:System.Globalization.Calendar.MinSupportedDateTime%2A?displayProperty=nameWithType> 屬性所表示。 如果是 <xref:System.Globalization.GregorianCalendar> 類別，該日期是公元 0001 年 1 月 1 日。 .NET 中的大多數其他日曆都支援較晚的日期。 嘗試處理早於曆法所支援最早日期的日期和時間值，會擲回 <xref:System.ArgumentOutOfRangeException> 例外狀況。

不過，有一個重要的例外狀況。 <xref:System.DateTime> 物件和 <xref:System.DateTimeOffset> 物件的預設值 (未初始化的值) 相當於 <xref:System.Globalization.GregorianCalendar.MinSupportedDateTime%2A?displayProperty=nameWithType> 值。 如果您嘗試在不支援 1 月 1，0001 C.E 的日曆中設置此日期的格式。 並且您不提供格式指定器，格式方法使用"s"（可排序日期/時間模式）格式指定器，而不是"G"（一般日期/時間模式）格式指定器。 結果，格式化作業並不會擲回 <xref:System.ArgumentOutOfRangeException> 例外狀況， 而是傳回不支援的日期。 下列範例將說明這種情況，當目前文化特性設為日文 (日本) 並採用日本曆法，以及設為阿拉伯文 (埃及) 並採用 Um Al Qura 曆法時，會顯示 <xref:System.DateTime.MinValue?displayProperty=nameWithType> 值。 另外也會將目前文化特性設為英文 (美國)，並且對每一個 <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType> 物件呼叫 <xref:System.Globalization.CultureInfo> 方法。 在每個案例中，日期是使用可排序日期/時間模式顯示。

[!code-csharp[Conceptual.Calendars#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/minsupporteddatetime1.cs#11)]
[!code-vb[Conceptual.Calendars#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/minsupporteddatetime1.vb#11)]

## <a name="work-with-eras"></a>使用時代

曆法通常會將日期細分成紀元。 但是，.NET<xref:System.Globalization.Calendar>中的類不支援由日曆定義的每個紀元，並且大多數<xref:System.Globalization.Calendar>類僅支援單個紀元。 只有 <xref:System.Globalization.JapaneseCalendar> 和 <xref:System.Globalization.JapaneseLunisolarCalendar> 類別支援多個紀元。

> [!IMPORTANT]
> Reiwa 時代，在<xref:System.Globalization.JapaneseCalendar>和<xref:System.Globalization.JapaneseLunisolarCalendar>的新時代，開始于 2019 年 5 月 1 日。 這項改變對所有使用這些日曆的應用程式都有影響。 如需詳細資訊，請參閱下列文章：
>
> - [在 .NET 中處理日語日曆中的新時代](https://devblogs.microsoft.com/dotnet/handling-a-new-era-in-the-japanese-calendar-in-net/)，其中記錄添加到 .NET 的功能以支援具有多個時代的日曆，並討論了在處理多紀元日曆時使用的最佳做法。
> - [為日本時代的變化準備您的應用程式](/windows/uwp/design/globalizing/japanese-era-change)，它提供有關在 Windows 上測試應用程式的資訊，以確保它們準備好迎接時代的變化。
> - [.NET Framework 的新日語時代更新摘要](https://support.microsoft.com/help/4477957/new-japanese-era-updates-for-net-framework)（列出與新日本日曆時代相關的單個 Windows 版本的 .NET Framework）更新，其中列出了用於多時代支援的新 .NET Framework 功能，並包含在測試應用程式時要查找的內容。

大多數日曆中的時代表示一個極長的時間段。 例如，在西曆中，當前時代跨越兩千年以上。 對於<xref:System.Globalization.JapaneseCalendar>和<xref:System.Globalization.JapaneseLunisolarCalendar>， 支援多個年代的兩個日曆， 情況並非如此。 一個時代對應于皇帝統治時期。 對多個時代的支援，特別是在目前時代的上限未知時，提出了特殊的挑戰。

### <a name="eras-and-era-names"></a>時代和時代名稱

在 .NET 中，表示特定日曆實現支援的 eras 的整數在<xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType>陣列中按相反順序存儲。 當前時代（是具有最新時間範圍的年代）位於索引零，對於<xref:System.Globalization.Calendar>支援多個時代的類，每個連續索引都反映前一個時代。 靜態 <xref:System.Globalization.Calendar.CurrentEra?displayProperty=nameWithType> 屬性會定義 <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> 陣列中目前紀元的索引，它是一個常數，且其值永遠為零。 個別 <xref:System.Globalization.Calendar> 類別也會包含傳回目前紀元值的靜態欄位。 下表中列出這些欄位。

| 曆法類別                                        | 目前紀元欄位                                                 |
| ----------------------------------------------------- | ----------------------------------------------------------------- |
| <xref:System.Globalization.ChineseLunisolarCalendar>  | <xref:System.Globalization.ChineseLunisolarCalendar.ChineseEra>   |
| <xref:System.Globalization.GregorianCalendar>         | <xref:System.Globalization.GregorianCalendar.ADEra>               |
| <xref:System.Globalization.HebrewCalendar>            | <xref:System.Globalization.HebrewCalendar.HebrewEra>              |
| <xref:System.Globalization.HijriCalendar>             | <xref:System.Globalization.HijriCalendar.HijriEra>                |
| <xref:System.Globalization.JapaneseLunisolarCalendar> | <xref:System.Globalization.JapaneseLunisolarCalendar.JapaneseEra> |
| <xref:System.Globalization.JulianCalendar>            | <xref:System.Globalization.JulianCalendar.JulianEra>              |
| <xref:System.Globalization.KoreanCalendar>            | <xref:System.Globalization.KoreanCalendar.KoreanEra>              |
| <xref:System.Globalization.KoreanLunisolarCalendar>   | <xref:System.Globalization.KoreanLunisolarCalendar.GregorianEra>  |
| <xref:System.Globalization.PersianCalendar>           | <xref:System.Globalization.PersianCalendar.PersianEra>            |
| <xref:System.Globalization.ThaiBuddhistCalendar>      | <xref:System.Globalization.ThaiBuddhistCalendar.ThaiBuddhistEra>  |
| <xref:System.Globalization.UmAlQuraCalendar>          | <xref:System.Globalization.UmAlQuraCalendar.UmAlQuraEra>          |

對應特定紀元數的名稱可藉由將紀元數傳遞至 <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> 或 <xref:System.Globalization.DateTimeFormatInfo.GetAbbreviatedEraName%2A?displayProperty=nameWithType> 方法的方式擷取。 下列範例會呼叫這些方法來擷取 <xref:System.Globalization.GregorianCalendar> 類別中紀元支援的相關資訊。 它顯示對應于當前紀元第二年 1 月 1 的西曆日期，以及對應于每個受支援的日本日曆時代第二年的 1 月 1 日的西曆日期。

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb)]

此外，"g" 自訂日期和時間格式字串包括曆法的紀元名稱，該名稱為日期和時間的字串表示。 有關詳細資訊，請參閱[自訂日期和時間格式字串](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)。

### <a name="instantiatie-a-date-with-an-era"></a>即時使用時代的日期

對於支援多個<xref:System.Globalization.Calendar>時代兩個相同的類，由特定年份、月份和月份值組成的日期可能不明確。 例如，由 支援<xref:System.Globalization.JapaneseCalendar>的所有時代都有數位為 1 的年份。 一般而言，如果未指定紀元，日期和時間及曆法方法都會假設這些值屬於目前紀元。 包含<xref:System.DateTime.%23ctor%2A>類型<xref:System.Globalization.Calendar>參數的 和<xref:System.DateTimeOffset.%23ctor%2A>建構函式以及[日語日曆.Datetime](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32))和[日語 LunisolarCalendar.ToDateTime](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32))方法也是如此。 下面的示例具現化了表示未指定時代第二年 1 月 1 日的日期。 如果在 Reiwa 時代是當前時代時執行該示例，則該日期將解釋為 Reiwa 時代的第二年。 在<xref:System.DateTime.ToString(System.String,System.IFormatProvider)?displayProperty=nameWithType>方法返回的字串中，該紀元早于年份，對應于西曆中的 2020 年 1 月 1 日。 （雷瓦時代始于西曆的 2019 年。

[!code-csharp[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/cs/program.cs)]
[!code-vb[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/vb/program.vb)]

但是，如果時代發生變化，則此代碼的意圖變得不明確。 日期是代表當前時代的第二年，還是打算代表海西時代的第二年？ 有兩種方法可以避免這種歧義：

- 使用預設<xref:System.Globalization.GregorianCalendar>類具現化日期和時間值。 然後，您可以使用日曆或日語 Lunisolar 日曆來表示日期的字串表示形式，如下例所示。

  [!code-csharp[Insantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/cs/program.cs)]
  [!code-vb[Instantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/vb/program.vb)]

- 調用顯式指定紀元紀元的日期和時間方法。 這包括下列方法︰

  - <xref:System.Globalization.JapaneseCalendar>或<xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)><xref:System.Globalization.JapaneseLunisolarCalendar>類的方法。

  - 或<xref:System.DateTime><xref:System.DateTimeOffset>解析<xref:System.DateTime.Parse%2A>方法，如 ，、 <xref:System.DateTime.TryParse%2A> <xref:System.DateTime.ParseExact%2A>、 或<xref:System.DateTime.TryParseExact%2A>， 包括要解析的字串，如果目前範圍性為<xref:System.Globalization.DateTimeStyles>日本-日本 （"ja-JP"）並且該區域性的日曆為<xref:System.Globalization.JapaneseCalendar>， 則可選地作為參數。 要解析的字串必須包括紀元。

  - 包含<xref:System.DateTime>類型`provider`<xref:System.DateTimeOffset><xref:System.IFormatProvider>參數 的 或 分析方法。 `provider`必須是表示當前日曆<xref:System.Globalization.CultureInfo>為 的日本-日本 （"ja-JP"） 區域性的物件<xref:System.Globalization.JapaneseCalendar>，或者其<xref:System.Globalization.DateTimeFormatInfo><xref:System.Globalization.DateTimeFormatInfo.Calendar>屬性為<xref:System.Globalization.JapaneseCalendar>的物件。 要解析的字串必須包括紀元。

  下面的示例使用其中三種方法具現化明治時代的日期和時間，明治時代始于 1868 年 9 月 8 日，于 1912 年 7 月 29 日結束。

  [!code-csharp[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/cs/program.cs)]
  [!code-vb[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/vb/program.vb)]

> [!TIP]
> 使用支援多個時代的日曆時，*始終*使用西曆日期具現化日期，或指定基於該日曆具現化日期和時間的年代。

在指定方法的紀元<xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)>時，在日曆<xref:System.Globalization.Calendar.Eras>的屬性中提供紀元索引。 但是，對於那些時代可能會發生變化的日曆，這些索引不是常量值;對於那些時代可能會發生變化的日曆，這些索引不是常量值。當前時代為索引 0，而最古老的時代是索引`Eras.Length - 1`。 將新時代添加到日曆時，前一個時代的索引將增加一個。 您可以提供相應的時代指數，如下所示：

- 對於當前時代的日期，始終使用日曆的屬性<xref:System.Globalization.Calendar.CurrentEra>。

- 對於指定時代中的日期，使用 方法<xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType>檢索對應于指定紀元名稱的索引。 這要求 是<xref:System.Globalization.JapaneseCalendar>表示 ja-JP<xref:System.Globalization.CultureInfo>區域性的物件的當前日曆。  （此技術也適用于，<xref:System.Globalization.JapaneseLunisolarCalendar>因為它支援與<xref:System.Globalization.JapaneseCalendar>相同的時代。前面的示例說明了此方法。

### <a name="calendars-eras-and-date-ranges-relaxed-range-checks"></a>日曆、時數和日期範圍：放寬範圍檢查

非常類似于單個日曆支援日期範圍，在 和<xref:System.Globalization.JapaneseCalendar><xref:System.Globalization.JapaneseLunisolarCalendar>類中也有支援範圍的年代。 以前，.NET 使用嚴格的紀元範圍檢查來確保特定紀元的日期在那個時代的範圍內。 也就是說，如果日期超出指定時間的範圍，則方法將引發 。 <xref:System.ArgumentOutOfRangeException> 目前，.NET 預設使用寬鬆的範圍檢查。 對 .NET 的所有版本的更新引入了寬鬆的時代範圍檢查;試圖具現化超出指定時代範圍的特定于紀元的日期"溢出"到下一個時代，並且不會引發異常。

以下示例嘗試具現化 Showa 時代第 65 年的日期，該日期從 1926 年 12 月 25 日開始，到 1989 年 1 月 7 日結束。 此日期對應于 1990 年 1 月 9 日，這超出了 中的<xref:System.Globalization.JapaneseCalendar>Showa 時代的範圍。 如示例的輸出所示，該示例顯示的日期為 1990 年 1 月 9 日，即海西時代的第二年。

  [!code-csharp[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/cs/program.cs)]
  [!code-vb[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/vb/program.vb)]

如果不需要放鬆的範圍檢查，則可以根據應用程式運行的 .NET 版本，以多種方式恢復嚴格的範圍檢查：

- **.NET 核心：** 將以下內容添加到 *.netcore.runtime.json*設定檔：

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.EnforceJapaneseEraYearRanges": true
    }
  }
  ```

- **.NET 框架 4.6 或更高版本：** 在*App.config*檔中設置以下 AppCoNtext 開關：

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceJapaneseEraYearRanges=true" />
    </runtime>
  </configuration>
  ```

- **.NET 框架 4.5.2 或更早版本：** 設置以下註冊表值：

   |  |  |
   |--|--|
   | **關鍵** | **HKEY_LOCAL_MACHINE軟體\微軟\\。NETFramework_應用程式上下文** |
   | **名稱** | 開關.系統.全球化.執行日本拉年範圍 |
   | **類型** | REG_SZ |
   | **價值** | true |

啟用了嚴格的範圍檢查後，前面的示例將引發<xref:System.ArgumentOutOfRangeException>並顯示以下輸出：

```console
Unhandled Exception: System.ArgumentOutOfRangeException: Valid values are between 1 and 64, inclusive.
Parameter name: year
   at System.Globalization.GregorianCalendarHelper.GetYearOffset(Int32 year, Int32 era, Boolean throwOnError)
   at System.Globalization.GregorianCalendarHelper.ToDateTime(Int32 year, Int32 month, Int32 day, Int32 hour, Int32 minute, Int32 second, Int32 millisecond, Int32 era)
   at Example.Main()
```

### <a name="represent-dates-in-calendars-with-multiple-eras"></a>在具有多個時代曆的日曆中表示日期

如果 <xref:System.Globalization.Calendar> 物件支援紀元而且是 <xref:System.Globalization.CultureInfo> 物件的現行曆法，則紀元會包含在完整日期和時間模式、完整日期模式及簡短日期模式之日期和時間值的字串表示中。 下列範例顯示目前文化特性為日本 (日文) 且現行曆法為日本曆法時的這些日期模式。

[!code-csharp[Conceptual.Calendars#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings1.cs#8)]
[!code-vb[Conceptual.Calendars#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings1.vb#8)]

> [!WARNING]
> 該<xref:System.Globalization.JapaneseCalendar>類是 .NET 中唯一<xref:System.Globalization.CultureInfo><xref:System.Globalization.CultureInfo>一個同時支援多個時代日期的日曆類，可以是物件的當前日曆-特別是表示日本（日本）區域性的物件的當前日曆。

針對所有曆法，"g" 自訂格式規範會在結果字串中包含紀元。 下列範例在現行曆法為西曆時，使用 "MM-dd-yyyy g" 自訂格式字串在結果字串中包含紀元。

[!code-csharp[Conceptual.Calendars#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings2.cs#9)]
[!code-vb[Conceptual.Calendars#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings2.vb#9)]

在日期的字串表示不是以現行曆法表示的情況下，<xref:System.Globalization.Calendar> 類別會包含 <xref:System.Globalization.Calendar.GetEra%2A?displayProperty=nameWithType> 方法，該方法可搭配 <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>、<xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType> 和 <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> 方法用來明確指出日期，以及該日期所屬的紀元。 下列範例使用 <xref:System.Globalization.JapaneseLunisolarCalendar> 類別提供圖例。 不過請注意，若要在結果字串中包含代表紀元的有意義名稱或縮寫而非整數，必須將 <xref:System.Globalization.DateTimeFormatInfo> 物件具現化，並且讓 <xref:System.Globalization.JapaneseCalendar> 成為現行曆法  (<xref:System.Globalization.JapaneseLunisolarCalendar> 曆法不得為任何文化特性的現行曆法，但在這個案例中，兩個曆法共用相同的紀元)。

[!code-csharp[Conceptual.Calendars#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings3.cs#10)]
[!code-vb[Conceptual.Calendars#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings3.vb#10)]

在日本曆法中，一個時代的第一年叫做甘甯（*）。 例如，海西時代的第一年可以描述為海西·甘甯，而不是海西1。 .NET 在格式化使用以下標準或自訂日期和時間格式字串的日期和時間操作時採用此約定，當這些日期和時間字串與表示日語（"ja-JP"）區域性<xref:System.Globalization.CultureInfo>的物件使用時，使用<xref:System.Globalization.JapaneseCalendar>該類：

- [長日期模式](../base-types/standard-date-and-time-format-strings.md#LongDate)，由"D"標準日期和時間格式字串指示。
- [完整日期長時間模式](../base-types/standard-date-and-time-format-strings.md#FullDateLongTime)，由"F"標準日期和時間格式字串指示。
- [全日期短時間模式](../base-types/standard-date-and-time-format-strings.md#FullDateShortTime)，由"f"標準日期和時間格式字串指示。
- [年/月模式](../base-types/standard-date-and-time-format-strings.md#YearMonth)，由 Y"或"y"標準日期和時間格式字串指示。
- ["ggy''"或"ggy"[自訂日期和時間格式字串](../base-types/custom-date-and-time-format-strings.md)。

例如，下面的示例顯示 海西時代第一年在 中<xref:System.Globalization.JapaneseCalendar>的日期。

  [!code-csharp[gannen](~/samples/snippets/standard/datetime/calendars/gannen/cs/program.cs)]
  [!code-vb[gannen](~/samples/snippets/standard/datetime/calendars/gannen/vb/gannen-fmt.vb)]

如果此行為在格式化操作中是不可取的，則可以根據 .NET 的版本執行以下操作，將以前的行為還原為"1"而不是"Gannen"的時代的第一年：

- **.NET 核心：** 將以下內容添加到 *.netcore.runtime.json*設定檔：

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.FormatJapaneseFirstYearAsANumber": true
    }
  }
  ```

- **.NET 框架 4.6 或更高版本：** 在*App.config*檔中設置以下 AppCoNtext 開關：

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.FormatJapaneseFirstYearAsANumber=true" />
    </runtime>
  </configuration>
  ```

- **.NET 框架 4.5.2 或更早版本：** 設置以下註冊表值：

   |  |  |
   |--|--|
   | **關鍵** | **HKEY_LOCAL_MACHINE軟體\微軟\\。NETFramework_應用程式上下文** |
   | **名稱** | 開關.系統.全球化.日本第一年數位 |
   | **類型** | REG_SZ |
   | **價值** | true |

禁用加甯支援格式化操作後，前面的示例將顯示以下輸出：

```console
Japanese calendar date: 平成1年8月18日 (Gregorian: Friday, August 18, 1989)
```

.NET 也已更新，以便日期和時間分析操作支援包含表示為"1"或 Gannen 的年份的字串。 儘管不需要執行此操作，但可以還原以前的行為，僅識別"1"作為時代的第一年。 您可以按照如下方式執行此操作，具體取決於 .NET 的版本：

- **.NET 核心：** 將以下內容添加到 *.netcore.runtime.json*設定檔：

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.EnforceLegacyJapaneseDateParsing": true
    }
  }
  ```

- **.NET 框架 4.6 或更高版本：** 在*App.config*檔中設置以下 AppCoNtext 開關：

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceLegacyJapaneseDateParsing=true" />
    </runtime>
  </configuration>
  ```

- **.NET 框架 4.5.2 或更早版本：** 設置以下註冊表值：

   |  |  |
   |--|--|
   | **關鍵** | **HKEY_LOCAL_MACHINE軟體\微軟\\。NETFramework_應用程式上下文** |
   | **名稱** | 開關.系統.全球化.強制執行傳統日本日期計算 |
   | **類型** | REG_SZ |
   | **價值** | true |

## <a name="see-also"></a>另請參閱

- [如何：在非西曆中顯示日期](../../../docs/standard/base-types/how-to-display-dates-in-non-gregorian-calendars.md)
- [示例：日曆周範圍實用程式](https://code.msdn.microsoft.com/NET-Framework-4-Calendar-3360a84a)
- [曆法類別](xref:System.Globalization.Calendar)
