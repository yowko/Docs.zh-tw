---
title: 使用日曆
ms.date: 04/01/2019
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
ms.openlocfilehash: c30af36b3426c4abbdf9c55f6c9062a5d8fc8c23
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824248"
---
# <a name="work-with-calendars"></a>使用行事曆

雖然日期和時間值代表一個時間點，但是其字串表示區分文化特性，而且同時取決於用於顯示特定文化特性之日期和時間值的慣例，以及該文化特性所使用的曆法。 本主題將探討如何在 .NET 中使用行事曆，並討論在使用日期值時，行事曆類別的使用方式。

## <a name="calendars-in-net"></a>.NET 中的行事曆

.NET 中的所有行事曆都衍生自 <xref:System.Globalization.Calendar?displayProperty=nameWithType> 類別，該類別會提供基本行事曆執行。 其中一個衍生自 <xref:System.Globalization.Calendar> 類別的類別是 <xref:System.Globalization.EastAsianLunisolarCalendar> 類別，其為所有陰陽曆的基底類別。 .NET 包含下列行事曆執行：

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

- 做為特定文化特性使用的曆法。 每個 <xref:System.Globalization.CultureInfo> 物件都有現行的曆法，也就是物件目前使用的曆法。 所有日期和時間值的字串表示都會自動反映目前的文化特性及其現行曆法。 通常現行曆法是文化特性的預設曆法。 <xref:System.Globalization.CultureInfo> 物件也有選用的行事曆，包括文化特性可以使用的其他行事曆。

- 做為與特定文化特性無關的獨立曆法。 這種情況下會使用 <xref:System.Globalization.Calendar> 方法以反映曆法的值表達日期。

請注意，這六種曆法類別 <xref:System.Globalization.ChineseLunisolarCalendar>、<xref:System.Globalization.JapaneseLunisolarCalendar>、<xref:System.Globalization.JulianCalendar>、<xref:System.Globalization.KoreanLunisolarCalendar>、<xref:System.Globalization.PersianCalendar> 和 <xref:System.Globalization.TaiwanLunisolarCalendar> 只能做為獨立曆法使用。 這些類別不會由任何文化特性做為預設曆法或選擇性曆法使用。

## <a name="calendars-and-cultures"></a>行事曆和文化特性

每一種文化特性都有預設曆法，該曆法是由 <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> 屬性所定義。 <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> 屬性會傳回 <xref:System.Globalization.Calendar> 物件的陣列，該陣列會指定特定文化特性支援的所有曆法，包括該文化特性的預設曆法。

下列範例說明 <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> 和 <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> 屬性。 範例中會為泰文 (泰國) 和日文 (日本) 文化特性建立 `CultureInfo` 物件，並且顯示其預設和選擇性曆法。 請注意，在這兩種情況下，文化特性的預設曆法也會包含在 <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> 集合中。

[!code-csharp[Conceptual.Calendars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/calendarinfo1.cs#1)]
[!code-vb[Conceptual.Calendars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/calendarinfo1.vb#1)]

特定 <xref:System.Globalization.CultureInfo> 物件目前使用的曆法是由文化特性的 <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> 屬性定義。 文化特性的 <xref:System.Globalization.DateTimeFormatInfo> 物件是由 <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> 屬性所傳回。 建立文化特性時，其預設值與 <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> 屬性的值相同。 不過，您可以將文化特性的現行曆法變更為 <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> 屬性所傳回陣列中包含的任何曆法。 如果您嘗試將現行曆法設定為不包括在 <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> 屬性值中的曆法，則會顯示 <xref:System.ArgumentException>。

下列範例會變更阿拉伯文 (沙烏地阿拉伯) 文化特性使用的曆法。 首先會具現化 <xref:System.DateTime> 值，並且使用現行文化特性 (此案例中是英文 (美國)) 和目前文化特性的曆法 (此案例中是西曆) 顯示該值。 接著會將目前的文化特性變更為阿拉伯文 (沙烏地阿拉伯)，並且使用其預設的 Um Al-Qura 曆法顯示日期。 最後呼叫 `CalendarExists` 方法，判斷阿拉伯文 (沙烏地阿拉伯) 文化特性是否支援回曆。 由於支援此曆法，因此會將現行曆法變更為回曆，並且再次顯示日期。 請注意，在各案例中，日期會使用目前文化特性的現行曆法顯示。

[!code-csharp[Conceptual.Calendars#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/changecalendar2.cs#2)]
[!code-vb[Conceptual.Calendars#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/changecalendar2.vb#2)]

## <a name="dates-and-calendars"></a>日期和行事曆

除了包括 <xref:System.Globalization.Calendar> 類型的參數且允許日期的項目 (也就是月、日和年) 以指定的曆法反映值的建構函式之外，<xref:System.DateTime> 和 <xref:System.DateTimeOffset> 這兩個值永遠以西曆為主。 例如，這表示 <xref:System.DateTime.Year%2A?displayProperty=nameWithType> 屬性會傳回西曆的年，而 <xref:System.DateTime.Day%2A?displayProperty=nameWithType> 屬性會傳回西曆的月份日期。

> [!IMPORTANT]
> 務必記得，日期值及其字串表示之間有一項差異。 前者是以西曆為主，後者是以特定文化特性的現行曆法為主。

下列範例會說明 <xref:System.DateTime> 屬性及其對應的 <xref:System.Globalization.Calendar> 方法之間的這項差異。 在此範例中，目前文化特性為阿拉伯文 (埃及)，而現行曆法為 Um Al Qura。 <xref:System.DateTime> 值會設定為 2011 年第七個月的第 15 天。 很清楚這個日期是解譯為西曆日期，因為這些相同值是 <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> 方法在使用不因文化特性而異的慣例時所傳回。 使用目前文化特性格式化之日期的字串表示為 14/08/32，其為 Um Al Qura 曆法的同等日期。 其次，`DateTime` 和 `Calendar` 的成員會用來傳回 <xref:System.DateTime> 值的日、月和年。 在各案例中，<xref:System.DateTime> 成員傳回的值會反映西曆的值，而 <xref:System.Globalization.UmAlQuraCalendar> 成員傳回的值則會反映 Uum al-Qura 曆法的值。

[!code-csharp[Conceptual.Calendars#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/datesandcalendars2.cs#3)]
[!code-vb[Conceptual.Calendars#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/datesandcalendars2.vb#3)]

### <a name="instantiate-dates-based-on-a-calendar"></a>以行事曆為基礎來具現化日期

由於 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 值是以西曆為主，因此，如果您想要使用不同曆法的日、月或年值，則必須呼叫包含 <xref:System.Globalization.Calendar> 類型之參數的多載建構函式來具現化日期值。 您也可以呼叫特定曆法之 <xref:System.Globalization.Calendar.ToDateTime%2A?displayProperty=nameWithType> 方法的其中一個多載，依據特殊曆法的值具現化 <xref:System.DateTime> 物件。

下列範例會藉由將 <xref:System.DateTime> 物件傳遞至 <xref:System.Globalization.HebrewCalendar> 建構函式具現化一個 <xref:System.DateTime> 值，並且藉由呼叫 <xref:System.DateTime> 方法具現化另一個 <xref:System.Globalization.HebrewCalendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> 值。 由於這兩個值是使用希伯來曆法的相同值所建立，因此呼叫 <xref:System.DateTime.Equals%2A?displayProperty=nameWithType> 方法會顯示這兩個 <xref:System.DateTime> 值相等。

[!code-csharp[Conceptual.Calendars#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatehcdate1.cs#4)]
[!code-vb[Conceptual.Calendars#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatehcdate1.vb#4)]

### <a name="represent-dates-in-the-current-calendar"></a>表示目前行事曆中的日期

日期和時間格式化方法會固定使用現行曆法將日期轉換為字串。 這表示年、月和月份日期的字串表示會反映現行曆法，而且不一定會反映西曆。

下列範例顯示現行曆法如何影響日期的字串表示。 它會將目前文化特性變更為中文 (繁體，台灣)，並且具現化日期值。 接著會顯示現行曆法和日期，將現行曆法變更為 <xref:System.Globalization.TaiwanCalendar>，然後再次顯示現行曆法和日期。 第一次顯示日期時，該日期會以西曆日期表示。 第二次顯示日期時，該日期會以台灣曆法的日期表示。

[!code-csharp[Conceptual.Calendars#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/currentcalendar1.cs#5)]
[!code-vb[Conceptual.Calendars#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/currentcalendar1.vb#5)]

### <a name="represent-dates-in-a-non-current-calendar"></a>代表非目前行事曆中的日期

若要使用不是特定文化特性的現行曆法來表示日期，您必須呼叫該 <xref:System.Globalization.Calendar> 物件的方法。 例如，<xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>、<xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType> 和 <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> 方法會將年、月和日轉換成反映特定曆法的值。

> [!WARNING]
> 由於某些曆法並非任何文化特性的選擇性曆法，因此使用這些曆法表示日期一定要呼叫曆法方法。 所有衍生自 <xref:System.Globalization.EastAsianLunisolarCalendar>、<xref:System.Globalization.JulianCalendar> 和 <xref:System.Globalization.PersianCalendar> 類別的曆法都要這樣做。

下列範例使用 <xref:System.Globalization.JulianCalendar> 物件具現化凱撒曆法的日期 1905 年 1 月 9 日。 使用預設曆法 (西曆) 顯示這個日期時，該日期會表示為 1905 年 1 月 22 日。 呼叫個別 <xref:System.Globalization.JulianCalendar> 方法即可使用凱撒曆法表示日期。

[!code-csharp[Conceptual.Calendars#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/noncurrentcalendar1.cs#6)]
[!code-vb[Conceptual.Calendars#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/noncurrentcalendar1.vb#6)]

### <a name="calendars-and-date-ranges"></a>行事曆和日期範圍

曆法所支援的最早日期是由該曆法的 <xref:System.Globalization.Calendar.MinSupportedDateTime%2A?displayProperty=nameWithType> 屬性所表示。 如果是 <xref:System.Globalization.GregorianCalendar> 類別，該日期是公元 0001 年 1 月 1 日。 .NET 中大部分的其他行事曆都支援未來的日期。 嘗試處理早於曆法所支援最早日期的日期和時間值，會擲回 <xref:System.ArgumentOutOfRangeException> 例外狀況。

不過，有一個重要的例外狀況。 <xref:System.DateTime> 物件和 <xref:System.DateTimeOffset> 物件的預設值 (未初始化的值) 相當於 <xref:System.Globalization.GregorianCalendar.MinSupportedDateTime%2A?displayProperty=nameWithType> 值。 如果您嘗試在不支援西元0001年1月1日的行事曆中格式化此日期 您未提供格式規範，格式方法會使用 "s" (可排序日期/時間模式) 格式規範，而不是 "G" (一般日期/時間模式) 格式規範。 結果，格式化作業並不會擲回 <xref:System.ArgumentOutOfRangeException> 例外狀況， 而是傳回不支援的日期。 下列範例將說明這種情況，當目前文化特性設為日文 (日本) 並採用日本曆法，以及設為阿拉伯文 (埃及) 並採用 Um Al Qura 曆法時，會顯示 <xref:System.DateTime.MinValue?displayProperty=nameWithType> 值。 另外也會將目前文化特性設為英文 (美國)，並且對每一個 <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType> 物件呼叫 <xref:System.Globalization.CultureInfo> 方法。 在每個案例中，日期是使用可排序日期/時間模式顯示。

[!code-csharp[Conceptual.Calendars#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/minsupporteddatetime1.cs#11)]
[!code-vb[Conceptual.Calendars#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/minsupporteddatetime1.vb#11)]

## <a name="work-with-eras"></a>使用紀元

曆法通常會將日期細分成紀元。 不過， <xref:System.Globalization.Calendar> .net 中的類別不支援行事曆所定義的每個紀元，而大部分的 <xref:System.Globalization.Calendar> 類別只支援單一紀元。 只有 <xref:System.Globalization.JapaneseCalendar> 和 <xref:System.Globalization.JapaneseLunisolarCalendar> 類別支援多個紀元。

> [!IMPORTANT]
> Reiwa 紀元是和中的新時代 <xref:System.Globalization.JapaneseCalendar> <xref:System.Globalization.JapaneseLunisolarCalendar> ，從2019年5月1日開始。 這項改變對所有使用這些日曆的應用程式都有影響。 如需詳細資訊，請參閱下列文章：
>
> - 在[.net 的日文日曆中處理新的時代](https://devblogs.microsoft.com/dotnet/handling-a-new-era-in-the-japanese-calendar-in-net/)，這會記載新增至 .net 的功能，以支援具有多個紀元的行事曆，並討論處理多個年代行事歷時使用的最佳做法。
> - [為您的應用程式做好日文時代的變更](/windows/uwp/design/globalizing/japanese-era-change)，以提供在 Windows 上測試應用程式的相關資訊，以確保其在紀元方面的就緒程度變更。
> - [.NET Framework 的新日文時代更新摘要](https://support.microsoft.com/help/4477957/new-japanese-era-updates-for-net-framework)，其中列出與新的日文日曆時代相關之個別 Windows 版本的 .NET Framework 更新、提供多個支援的新 .NET Framework 功能，以及在測試應用程式時要尋找的專案。

大部分行事曆中的紀元表示非常長的時間週期。 例如，在西曆中，目前的紀元跨越兩個以上的千年來。 在 <xref:System.Globalization.JapaneseCalendar> 和 <xref:System.Globalization.JapaneseLunisolarCalendar> 中，支援多個紀元的兩個行事曆不是這種情況。 紀元會對應到天皇的統治期間。 支援多個紀元，特別是當目前紀元的上限未知時，會帶來特殊的挑戰。

### <a name="eras-and-era-names"></a>紀元和紀元名稱

在 .NET 中，代表特定行事曆實所支援之紀元的整數會以反向順序儲存在 <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> 陣列中。 目前的紀元 (是具有最新時間範圍) 的紀元位於索引零，而針對 <xref:System.Globalization.Calendar> 支援多個紀元的類別，每個後續的索引都會反映先前的紀元。 靜態 <xref:System.Globalization.Calendar.CurrentEra?displayProperty=nameWithType> 屬性會定義 <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> 陣列中目前紀元的索引，它是一個常數，且其值永遠為零。 個別 <xref:System.Globalization.Calendar> 類別也會包含傳回目前紀元值的靜態欄位。 下表中列出這些欄位。

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

對應特定紀元數的名稱可藉由將紀元數傳遞至 <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> 或 <xref:System.Globalization.DateTimeFormatInfo.GetAbbreviatedEraName%2A?displayProperty=nameWithType> 方法的方式擷取。 下列範例會呼叫這些方法來擷取 <xref:System.Globalization.GregorianCalendar> 類別中紀元支援的相關資訊。 它會顯示西曆日期，該日期與目前紀元的第二年1月1日相對應，以及對應至每個支援之日文日曆紀元第二年1月1日的西曆日期。

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb)]

此外，"g" 自訂日期和時間格式字串包括曆法的紀元名稱，該名稱為日期和時間的字串表示。 如需詳細資訊，請參閱 [自訂日期和時間格式字串](../base-types/custom-date-and-time-format-strings.md)。

### <a name="instantiatie-a-date-with-an-era"></a>Instantiatie 具有紀元的日期

針對 <xref:System.Globalization.Calendar> 支援多個紀元的兩個類別，包含特定年、月和日值的日期可能不明確。 例如，所支援的所有紀元 <xref:System.Globalization.JapaneseCalendar> 都有年份，其數目為1。 一般而言，如果未指定紀元，日期和時間及曆法方法都會假設這些值屬於目前紀元。 這適用于 <xref:System.DateTime.%23ctor%2A> 和 <xref:System.DateTimeOffset.%23ctor%2A> 包含型別參數的和函式 <xref:System.Globalization.Calendar> ，以及 [JapaneseCalendar. ToDateTime](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)) 和 [JapaneseLunisolarCalendar. ToDateTime](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)) 方法。 下列範例會具現化代表未指定紀元中第二年1月1日的日期。 如果您在 Reiwa 紀元是目前的紀元時執行範例，日期會被視為 Reiwa 紀元的第二年。 紀元（令和）在方法所傳回之字串中的年份之前， <xref:System.DateTime.ToString(System.String,System.IFormatProvider)?displayProperty=nameWithType> 並對應至西曆中的2020年1月1日。  (Reiwa 紀元于西曆年2019年開始。 ) 

[!code-csharp[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/cs/program.cs)]
[!code-vb[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/vb/program.vb)]

但是，如果紀元變更，則此程式碼的意圖會變得不明確。 這是要代表目前紀元的第二年的日期，還是要代表 Heisei 紀元的第二年？ 有兩種方式可避免這種混淆：

- 使用預設類別來具現化日期和時間值 <xref:System.Globalization.GregorianCalendar> 。 然後，您可以使用日文行事曆或日文陰陽曆來表示日期的字串表示，如下列範例所示。

  [!code-csharp[Insantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/cs/program.cs)]
  [!code-vb[Instantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/vb/program.vb)]

- 呼叫明確指定紀元的日期和時間方法。 這包括下列方法︰

  - <xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)>或類別的方法 <xref:System.Globalization.JapaneseCalendar> <xref:System.Globalization.JapaneseLunisolarCalendar> 。

  - <xref:System.DateTime>或 <xref:System.DateTimeOffset> 剖析方法（例如 <xref:System.DateTime.Parse%2A> 、 <xref:System.DateTime.TryParse%2A> 、 <xref:System.DateTime.ParseExact%2A> 或）， <xref:System.DateTime.TryParseExact%2A> 其中包含要剖析的字串，以及選擇性的 <xref:System.Globalization.DateTimeStyles> 引數（如果目前的文化特性是 Japanese-Japan ( "ja-jp" ) 且文化特性的行事曆為） <xref:System.Globalization.JapaneseCalendar> 。 要剖析的字串必須包含紀元。

  - <xref:System.DateTime>或 <xref:System.DateTimeOffset> 剖析方法，其中包含 `provider` 類型的參數 <xref:System.IFormatProvider> 。 `provider` 必須是 <xref:System.Globalization.CultureInfo> 代表 Japanese-Japan ( "ja-jp" ) 文化特性的物件，其目前的行事曆是 <xref:System.Globalization.JapaneseCalendar> 或 <xref:System.Globalization.DateTimeFormatInfo> 其 <xref:System.Globalization.DateTimeFormatInfo.Calendar> 屬性為的物件 <xref:System.Globalization.JapaneseCalendar> 。 要剖析的字串必須包含紀元。

  下列範例會使用這三種方法來具現化 Meiji 紀元中的日期和時間（從1868年9月8日開始），並于1912年7月29日結束。

  [!code-csharp[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/cs/program.cs)]
  [!code-vb[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/vb/program.vb)]

> [!TIP]
> 使用支援多個紀元的行事歷時，請 *一律* 使用西曆日期來具現化日期，或在您根據該行事歷來具現化日期和時間時，指定紀元。

在指定紀元給 <xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)> 方法時，您會在行事曆的屬性中提供紀元的索引 <xref:System.Globalization.Calendar.Eras> 。 不過，對於其紀元有可能變更的行事曆，這些索引不是常數值;目前的紀元位於索引0，而最舊的紀元位於索引處 `Eras.Length - 1` 。 當新的紀元新增至行事歷時，前一個紀元的索引會增加1。 您可以提供適當的紀元索引，如下所示：

- 針對目前紀元中的日期，請一律使用行事曆的 <xref:System.Globalization.Calendar.CurrentEra> 屬性。

- 針對指定紀元中的日期，請使用 <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> 方法來取出對應于指定之紀元名稱的索引。 這需要 <xref:System.Globalization.JapaneseCalendar> 是 <xref:System.Globalization.CultureInfo> 代表 ja-jp 文化特性之物件的目前行事曆。   (這項技術也適用于 <xref:System.Globalization.JapaneseLunisolarCalendar> ，因為它支援與相同的紀元 <xref:System.Globalization.JapaneseCalendar> 。 ) 上一個範例說明這種方法。

### <a name="calendars-eras-and-date-ranges-relaxed-range-checks"></a>行事曆、紀元和日期範圍：寬鬆的範圍檢查

和個別行事曆都有支援的日期範圍，和類別中的紀元 <xref:System.Globalization.JapaneseCalendar> <xref:System.Globalization.JapaneseLunisolarCalendar> 也有支援的範圍。 先前，.NET 使用嚴格的紀元範圍檢查，以確保紀元特定日期在該紀元的範圍內。 也就是說，如果日期超出指定紀元的範圍，則方法會擲回 <xref:System.ArgumentOutOfRangeException> 。 目前，.NET 預設會使用寬鬆的範圍檢查。 所有 .NET 版本的更新引進了寬鬆的紀元範圍檢查;嘗試將指定的紀元範圍以外的特定時間範圍，具現化為下列紀元，且不會擲回例外狀況。

下列範例會嘗試在 Showa 紀元的65th 年中具現化日期，其開始時間為1926年12月25日，並于1989年1月7日結束。 此日期對應于1990年1月9日，在中的 Showa 紀元範圍之外 <xref:System.Globalization.JapaneseCalendar> 。 如範例的輸出所示，此範例顯示的日期為1990年1月9日（Heisei 紀元的第二年）。

  [!code-csharp[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/cs/program.cs)]
  [!code-vb[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/vb/program.vb)]

如果不需要寬鬆的範圍檢查，您可以透過數種方式還原嚴格的範圍檢查，端視您的應用程式執行所在的 .NET 版本而定：

- **.Net Core：** 將下列內容新增至設定檔 *上的.netcore.runtime.js* ：

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.EnforceJapaneseEraYearRanges": true
    }
  }
  ```

- **.NET Framework 4.6 或更新版本：** 在 *app.config* 檔案中設定下列 AppCoNtext 參數：

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceJapaneseEraYearRanges=true" />
    </runtime>
  </configuration>
  ```

- **.NET Framework 4.5.2 或更早版本：** 設定下列登錄值：

   |  |  |
   |--|--|
   | **Key** | **HKEY_LOCAL_MACHINE\Software\Microsoft\\ 。NETFramework\AppCoNtext** |
   | **Name** | Switch.System。全球化. EnforceJapaneseEraYearRanges |
   | **型別** | REG_SZ |
   | **值** | true |

啟用 strict 範圍檢查後，上述範例會擲回 <xref:System.ArgumentOutOfRangeException> ，並顯示下列輸出：

```console
Unhandled Exception: System.ArgumentOutOfRangeException: Valid values are between 1 and 64, inclusive.
Parameter name: year
   at System.Globalization.GregorianCalendarHelper.GetYearOffset(Int32 year, Int32 era, Boolean throwOnError)
   at System.Globalization.GregorianCalendarHelper.ToDateTime(Int32 year, Int32 month, Int32 day, Int32 hour, Int32 minute, Int32 second, Int32 millisecond, Int32 era)
   at Example.Main()
```

### <a name="represent-dates-in-calendars-with-multiple-eras"></a>以多個紀元表示日曆中的日期

如果 <xref:System.Globalization.Calendar> 物件支援紀元而且是 <xref:System.Globalization.CultureInfo> 物件的現行曆法，則紀元會包含在完整日期和時間模式、完整日期模式及簡短日期模式之日期和時間值的字串表示中。 下列範例顯示目前文化特性為日本 (日文) 且現行曆法為日本曆法時的這些日期模式。

[!code-csharp[Conceptual.Calendars#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings1.cs#8)]
[!code-vb[Conceptual.Calendars#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings1.vb#8)]

> [!WARNING]
> <xref:System.Globalization.JapaneseCalendar>類別是 .net 中唯一的行事曆類別，其支援多個紀元中的日期，而且可以是物件的目前行事曆 <xref:System.Globalization.CultureInfo> ，特別是 <xref:System.Globalization.CultureInfo> 代表日文 (日本) 文化特性的物件。

針對所有曆法，"g" 自訂格式規範會在結果字串中包含紀元。 下列範例在現行曆法為西曆時，使用 "MM-dd-yyyy g" 自訂格式字串在結果字串中包含紀元。

[!code-csharp[Conceptual.Calendars#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings2.cs#9)]
[!code-vb[Conceptual.Calendars#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings2.vb#9)]

在日期的字串表示不是以現行曆法表示的情況下，<xref:System.Globalization.Calendar> 類別會包含 <xref:System.Globalization.Calendar.GetEra%2A?displayProperty=nameWithType> 方法，該方法可搭配 <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>、<xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType> 和 <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> 方法用來明確指出日期，以及該日期所屬的紀元。 下列範例使用 <xref:System.Globalization.JapaneseLunisolarCalendar> 類別提供圖例。 不過請注意，若要在結果字串中包含代表紀元的有意義名稱或縮寫而非整數，必須將 <xref:System.Globalization.DateTimeFormatInfo> 物件具現化，並且讓 <xref:System.Globalization.JapaneseCalendar> 成為現行曆法  (<xref:System.Globalization.JapaneseLunisolarCalendar> 曆法不得為任何文化特性的現行曆法，但在這個案例中，兩個曆法共用相同的紀元)。

[!code-csharp[Conceptual.Calendars#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings3.cs#10)]
[!code-vb[Conceptual.Calendars#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings3.vb#10)]

在日文日曆中，紀元的第一年稱為 Gannen (元年) 。 例如，不是 Heisei 1，Heisei 紀元的第一年可以描述為 Heisei Gannen。 當使用下列標準或自訂日期和時間格式字串搭配 <xref:System.Globalization.CultureInfo> 代表 Japanese-Japan ( "ja-jp" ) 文化特性與類別的物件時，.net 會採用此慣例來格式化日期和時間格式的作業 <xref:System.Globalization.JapaneseCalendar> ：

- [完整日期模式](../base-types/standard-date-and-time-format-strings.md#LongDate)，以 "D" 標準日期和時間格式字串表示。
- [完整日期完整時間模式](../base-types/standard-date-and-time-format-strings.md#FullDateLongTime)，以 "F" 標準日期和時間格式字串表示。
- [完整日期簡短時間模式](../base-types/standard-date-and-time-format-strings.md#FullDateShortTime)，以 "f" 標準日期和時間格式字串表示。
- [Year/month 模式](../base-types/standard-date-and-time-format-strings.md#YearMonth)，以 Y "或" y "標準日期和時間格式字串表示。
- [Ggy ' 年 ' "或" ggy年 " [自訂日期和時間格式字串](../base-types/custom-date-and-time-format-strings.md)。

例如，下列範例會在中顯示 Heisei 紀元的第一年中的日期 <xref:System.Globalization.JapaneseCalendar> 。

  [!code-csharp[gannen](~/samples/snippets/standard/datetime/calendars/gannen/cs/program.cs)]
  [!code-vb[gannen](~/samples/snippets/standard/datetime/calendars/gannen/vb/gannen-fmt.vb)]

如果在格式化作業中不需要這種行為，您可以藉由執行下列動作（視 .NET 的版本而定）來還原先前的行為，此行為一律會將紀元的第一年表示為 "1"，而不是 "Gannen"：

- **.Net Core：** 將下列內容新增至設定檔 *上的.netcore.runtime.js* ：

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.FormatJapaneseFirstYearAsANumber": true
    }
  }
  ```

- **.NET Framework 4.6 或更新版本：** 在 *app.config* 檔案中設定下列 AppCoNtext 參數：

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.FormatJapaneseFirstYearAsANumber=true" />
    </runtime>
  </configuration>
  ```

- **.NET Framework 4.5.2 或更早版本：** 設定下列登錄值：

   |  |  |
   |--|--|
   | **Key** | **HKEY_LOCAL_MACHINE\Software\Microsoft\\ 。NETFramework\AppCoNtext** |
   | **Name** | Switch.System。全球化. FormatJapaneseFirstYearAsANumber |
   | **型別** | REG_SZ |
   | **值** | true |

在停用格式化作業的 gannen 支援之後，上述範例會顯示下列輸出：

```console
Japanese calendar date: 平成1年8月18日 (Gregorian: Friday, August 18, 1989)
```

.NET 也已更新，讓日期和時間剖析作業支援包含以 "1" 或 Gannen 表示之年份的字串。 雖然您不應該這麼做，但您可以還原先前的行為，將「1」視為紀元的第一年。 您可以依照下列方式執行這項作業，視 .NET 的版本而定：

- **.Net Core：** 將下列內容新增至設定檔 *上的.netcore.runtime.js* ：

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.EnforceLegacyJapaneseDateParsing": true
    }
  }
  ```

- **.NET Framework 4.6 或更新版本：** 在 *app.config* 檔案中設定下列 AppCoNtext 參數：

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceLegacyJapaneseDateParsing=true" />
    </runtime>
  </configuration>
  ```

- **.NET Framework 4.5.2 或更早版本：** 設定下列登錄值：

   |  |  |
   |--|--|
   | **Key** | **HKEY_LOCAL_MACHINE\Software\Microsoft\\ 。NETFramework\AppCoNtext** |
   | **Name** | Switch.System。全球化. EnforceLegacyJapaneseDateParsing |
   | **型別** | REG_SZ |
   | **值** | true |

## <a name="see-also"></a>請參閱

- [如何：在非西曆中顯示日期](../base-types/how-to-display-dates-in-non-gregorian-calendars.md)
- [範例：行事曆周範圍公用程式](https://code.msdn.microsoft.com/NET-Framework-4-Calendar-3360a84a)
- [曆法類別](xref:System.Globalization.Calendar)
