---
title: "標準日期和時間格式字串"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [.NET Framework], dates
- custom DateTime format string
- format specifiers, custom date and time
- format strings
- custom date and time format strings
- formatting [.NET Framework], time
- date and time strings
ms.assetid: bb79761a-ca08-44ee-b142-b06b3e2fc22b
caps.latest.revision: "92"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca51c13a8c25575080c56b8d1ffe5723f34b539e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="standard-date-and-time-format-strings"></a>標準日期和時間格式字串
標準日期和時間格式字串使用單一格式規範，定義日期和時間值的文字表示。 任何包含一個以上字元 (包括空白字元) 的日期和時間格式字串都會解譯為自訂日期和時間格式字串；如需詳細資訊，請參閱[自訂日期和時間格式字串](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)。 標準或自訂格式字串有兩種使用方式：  
  
-   定義執行格式化作業後所產生的字串。  
  
-   定義日期和時間值的文字表示，可藉由剖析作業轉換成 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 值。  
  
 標準日期和時間格式字串可以與 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 值搭配使用。  
  
> [!TIP]
>  您可以下載 [格式化公用程式](http://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)，這個應用程式可讓您將格式字串套用至數值或日期和時間值，並且顯示結果字串。  
  
<a name="table"></a>下表描述標準日期和時間的格式規範。 除非特別註明，否則特定標準日期和時間格式規範會產生相同的字串表示，無論是與 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 值搭配使用。 如需使用標準日期和時間格式字串的詳細資訊，請參閱[備註](#Notes)一節。  
  
|格式規範|描述|範例|  
|----------------------|-----------------|--------------|  
|"d"|簡短日期模式。<br /><br /> 詳細資訊：[簡短日期 ("d") 格式規範](#ShortDate)。|2009-06-15T13:45:30 -> 6/15/2009 (en-US)<br /><br /> 2009-06-15T13:45:30 -> 15/06/2009 (fr-FR)<br /><br /> 2009-06-15T13:45:30 -> 2009/06/15 (ja-JP)|  
|"D"|完整日期模式。<br /><br /> 詳細資訊：[完整日期 ("D") 格式規範](#LongDate)。|2009-06-15T13:45:30 -> Monday, June 15, 2009 (en-US)<br /><br /> 2009-06-15T13:45:30 -> 15 июня 2009 г (ru-RU)<br /><br /> 2009-06-15T13:45:30 -> Montag, 15 Juni 2009 (de-DE)|  
|"f"|完整日期/時間模式 (簡短時間)。<br /><br /> 詳細資訊：[完整日期簡短時間 ("f") 格式規範](#FullDateShortTime)。|2009-06-15T13:45:30 -> Monday, June 15, 2009 1:45 PM (en-US)<br /><br /> 2009-06-15T13:45:30 -> den 15 juni 2009 13:45 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 1:45 μμ (el-GR)|  
|"F"|完整日期/時間模式 (完整時間)。<br /><br /> 詳細資訊：[完整日期完整時間 ("F") 格式規範](#FullDateLongTime)。|2009-06-15T13:45:30 -> Monday, June 15, 2009 1:45:30 PM (en-US)<br /><br /> 2009-06-15T13:45:30 -> den 15 juni 2009 13:45:30 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 1:45:30 μμ (el-GR)|  
|"g"|一般日期/時間模式 (簡短時間)。<br /><br /> 詳細資訊：[一般日期簡短時間 ("g") 格式規範](#GeneralDateShortTime)。|2009-06-15T13:45:30 -> 6/15/2009 1:45 PM (en-US)<br /><br /> 2009-06-15T13:45:30 -> 15/06/2009 13:45 (es-ES)<br /><br /> 2009-06-15T13:45:30 -> 2009/6/15 13:45 (zh-CN)|  
|"G"|一般日期/時間模式 (完整時間)。<br /><br /> 詳細資訊：[一般日期完整時間 ("G") 格式規範](#GeneralDateLongTime)。|2009-06-15T13:45:30 -> 6/15/2009 1:45:30 PM (en-US)<br /><br /> 2009-06-15T13:45:30 -> 15/06/2009 13:45:30 (es-ES)<br /><br /> 2009-06-15T13:45:30 -> 2009/6/15 13:45:30 (zh-CN)|  
|"M"、"m"|月/日模式。<br /><br /> 詳細資訊：[月 ("M"、"m") 格式規範](#MonthDay)。|2009-06-15T13:45:30 -> June 15 (en-US)<br /><br /> 2009-06-15T13:45:30 -> 15 juni (da-DK)<br /><br /> 2009-06-15T13:45:30 -> 15 Juni (id-ID)|  
|"O"、"o"|來回日期/時間模式。<br /><br /> 詳細資訊：[來回 ("O"、"o") 格式規範](#Roundtrip)。|<xref:System.DateTime> 值：<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Local) --> 2009-06-15T13:45:30.0000000-07:00<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Utc) --> 2009-06-15T13:45:30.0000000Z<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Unspecified) --> 2009-06-15T13:45:30.0000000<br /><br /> <xref:System.DateTimeOffset> 值：<br /><br /> 2009-06-15T13:45:30-07:00 --> 2009-06-15T13:45:30.0000000-07:00|  
|"R"、"r"|RFC1123 模式。<br /><br /> 詳細資訊：[RFC1123 ("R"、"r") 格式規範](#RFC1123)。|2009-06-15T13:45:30 -> Mon, 15 Jun 2009 20:45:30 GMT|  
|"s"|可排序日期/時間模式。<br /><br /> 詳細資訊：[可排序 ("s") 格式規範](#Sortable)。|2009-06-15T13:45:30 (DateTimeKind.Local) -> 2009-06-15T13:45:30<br /><br /> 2009-06-15T13:45:30 (DateTimeKind.Utc) -> 2009-06-15T13:45:30|  
|"t"|簡短時間模式。<br /><br /> 詳細資訊：[簡短時間 ("t") 格式規範](#ShortTime)。|2009-06-15T13:45:30 -> 1:45 PM (en-US)<br /><br /> 2009-06-15T13:45:30 -> 13:45 (hr-HR)<br /><br /> 2009-06-15T13:45:30 -> 01:45 م (ar-EG)|  
|"T"|完整時間模式。<br /><br /> 詳細資訊：[完整時間 ("T") 格式規範](#LongTime)。|2009-06-15T13:45:30 -> 1:45:30 PM (en-US)<br /><br /> 2009-06-15T13:45:30 -> 13:45:30 (hr-HR)<br /><br /> 2009-06-15T13:45:30 -> 01:45:30 م (ar-EG)|  
|"u"|國際可排序日期/時間模式。<br /><br /> 詳細資訊：[國際可排序 ("u") 格式規範](#UniversalSortable)。|與<xref:System.DateTime>值： 2009年-06-15T13:45:30-> 2009年-06-15 13:45:30Z<br /><br /> 與<xref:System.DateTimeOffset>值： 2009年-06-15T13:45:30-> 2009年-06-15 20:45:30Z|  
|"U"|國際完整日期/時間模式。<br /><br /> 詳細資訊：[國際完整 ("U") 格式規範](#UniversalFull)。|2009-06-15T13:45:30 -> Monday, June 15, 2009 8:45:30 PM (en-US)<br /><br /> 2009-06-15T13:45:30 -> den 15 juni 2009 20:45:30 (sv-SE)<br /><br /> 2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 8:45:30 μμ (el-GR)|  
|"Y", "y"|年月模式。<br /><br /> 詳細資訊：[年月 ("Y") 格式規範](#YearMonth)。|2009-06-15T13:45:30 -> June, 2009 (en-US)<br /><br /> 2009-06-15T13:45:30 -> juni 2009 (da-DK)<br /><br /> 2009-06-15T13:45:30 -> Juni 2009 (id-ID)|  
|任何其他單一字元|未知的規範。|擲回執行階段 <xref:System.FormatException>。|  
  
## <a name="how-standard-format-strings-work"></a>標準格式字串的運作方式  
 在格式化作業中，標準格式字串只是自訂格式字串的別名。 使用別名來表示自訂格式字串的好處是，儘管別名保持不變，自訂格式字串本身則可有變化。 這點非常重要，因為日期和時間值的字串表示通常會因文化特性而不同。 例如，"d" 標準格式字串表示日期和時間值將使用簡短日期模式顯示。 在不因文化特性而異 (Invariant Culture) 的情況下，此模式為 "MM/dd/yyyy"。 若為 fr-FR 文化特性，則是 "dd/MM/yyyy"。 若為 ja-JP 文化特性，則是 "yyyy/MM/dd"。  
  
 如果格式化作業中的標準格式字串對應至特定文化特性的自訂格式字串，您的應用程式可以定義特定文化特性，以下列其中一種方式使用自訂格式字串：  
  
-   您可以使用預設 (或目前的) 文化特性。 下列範例顯示的日期使用了目前文化特性的簡短日期格式。 在此例中，目前的文化特性是 en-US。  
  
     [!code-csharp[System.DateTime.Conceptual.Formatting#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#1)]
     [!code-vb[System.DateTime.Conceptual.Formatting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#1)]  
  
-   您可以將表示要用來進行格式化之文化特性的 <xref:System.Globalization.CultureInfo> 物件傳遞至具有 <xref:System.IFormatProvider> 參數的方法。 下列範例顯示的日期使用了 pt-BR 文化特性的簡短日期格式。  
  
     [!code-csharp[System.DateTime.Conceptual.Formatting#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#2)]
     [!code-vb[System.DateTime.Conceptual.Formatting#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#2)]  
  
-   您可以將提供格式化資訊的 <xref:System.Globalization.DateTimeFormatInfo> 物件傳遞至具有 <xref:System.IFormatProvider> 參數的方法。 下列範例顯示的日期使用了取自於 hr-HR 文化特性之 <xref:System.Globalization.DateTimeFormatInfo> 物件的簡短日期格式。  
  
     [!code-csharp[System.DateTime.Conceptual.Formatting#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/cs/StandardFormats1.cs#3)]
     [!code-vb[System.DateTime.Conceptual.Formatting#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTime.Conceptual.Formatting/vb/StandardFormats1.vb#3)]  
  
> [!NOTE]
>  如需有關自訂格式化日期與時間值所使用之模式或字串的詳細資訊，請參閱 <xref:System.Globalization.NumberFormatInfo> 類別主題。  
  
 在某些情況下，標準格式字串可做為不變之長自訂格式字串的簡便縮寫。 有四個標準格式字串屬於此分類："O" (或 "o")、"R" (或 "r")、"s" 和 "u"。 這些字串相當於不因文化特性而異所定義的自訂格式字串。 它們針對日期和時間值所產生的字串表示在各文化特性中都相同。 下表提供這四種標準日期和時間格式字串的相關資訊。  
  
|標準格式字串|由 DateTimeFormatInfo.InvariantInfo 屬性定義|自訂格式字串|  
|----------------------------|----------------------------------------------------------|--------------------------|  
|"O" 或 "o"|無|yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffzz|  
|"R" 或 "r"|<xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A>|ddd、dd MMM yyyy HH':'mm':'ss 'GMT'|  
|"s"|<xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern%2A>|yyyy'-'MM'-'dd'T'HH':'mm':'ss|  
|"u"|<xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>|yyyy'-'MM'-'dd HH':'mm':'ss'Z'|  
  
 標準格式字串也可以在剖析作業中搭配 <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> 或 <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> 方法使用，這些方法都需要輸入字串完全符合特定模式，剖析作業才會成功。 許多標準格式字串都對應至多個自訂格式字串，因此日期和時間值可以用各種不同的格式表示，而剖析作業仍然會成功。 您可以藉由呼叫 <xref:System.Globalization.DateTimeFormatInfo.GetAllDateTimePatterns%28System.Char%29?displayProperty=nameWithType> 方法判斷對應至標準格式字串的自訂格式字串。 下列範例會顯示對應至 "d" (簡短日期模式) 標準格式字串的自訂格式字串。  
  
 [!code-csharp[Formatting.DateAndTime.Standard#17](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/stdandparsing1.cs#17)]
 [!code-vb[Formatting.DateAndTime.Standard#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/stdandparsing1.vb#17)]  
  
 下列各節描述 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 值的標準格式規範。  
  
<a name="ShortDate"></a>   
## <a name="the-short-date-d-format-specifier"></a>簡短日期 ("d") 格式規範  
 "d" 標準格式規範表示由特定文化特性之 <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> 屬性所定義的自訂日期和時間格式字串。 例如，不因文化特性而異的 <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A> 屬性傳回的自訂格式字串為 "MM/dd/yyyy"。  
  
 下表列出可控制傳回字串之格式設定的 <xref:System.Globalization.DateTimeFormatInfo> 物件屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A>|定義結果字串的整體格式。|  
|<xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A>|定義分隔日期之年份、月份和日期元件的字串。|  
  
 下列範例使用 "d" 格式規範來顯示日期和時間值。  
  
 [!code-csharp[Formatting.DateAndTime.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#1)]
 [!code-vb[Formatting.DateAndTime.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#1)]  
  
 [回到表格](#table)  
  
<a name="LongDate"></a>   
## <a name="the-long-date-d-format-specifier"></a>完整日期 ("D") 格式規範  
 "D" 標準格式規範表示由目前 <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> 屬性所定義的自訂日期和時間格式字串。 例如，不因文化特性而異的自訂格式字串為 "dddd, dd MMMM yyyy"。  
  
 下表列出 <xref:System.Globalization.DateTimeFormatInfo> 物件的屬性，這些屬性控制傳回之字串的格式設定。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A>|定義結果字串的整體格式。|  
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|定義可顯示在結果字串中的當地語系化日期名稱。|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|定義可顯示在結果字串中的當地語系化月份名稱。|  
  
 下列範例使用 "D" 格式規範來顯示日期和時間值。  
  
 [!code-csharp[Formatting.DateAndTime.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#2)]
 [!code-vb[Formatting.DateAndTime.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#2)]  
  
 [回到表格](#table)  
  
<a name="FullDateShortTime"></a>   
## <a name="the-full-date-short-time-f-format-specifier"></a>完整日期簡短時間 ("f") 格式規範  
 "f" 標準格式規範表示完整日期 ("D") 和簡短時間 ("t") 模式的組合，以空格分隔。  
  
 結果字串會受到特定 <xref:System.Globalization.DateTimeFormatInfo> 物件的格式設定資訊所影響。 下表列出可控制傳回字串之格式設定的 <xref:System.Globalization.DateTimeFormatInfo> 物件屬性。 由某些文化特性的 <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> 和 <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> 屬性所傳回的自訂格式規範，可能不會使用所有屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A>|定義結果字串之日期元件的格式。|  
|<xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A>|定義結果字串之時間元件的格式。|  
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|定義可顯示在結果字串中的當地語系化日期名稱。|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|定義可顯示在結果字串中的當地語系化月份名稱。|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|定義分隔時間之小時、分鐘和秒鐘元件的字串。|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|定義表示從午夜到中午之前時間 (12 小時制) 的字串。|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|定義表示從中午到午夜之前時間 (12 小時制) 的字串。|  
  
 下列範例使用 "f" 格式規範來顯示日期和時間值。  
  
 [!code-csharp[Formatting.DateAndTime.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#3)]
 [!code-vb[Formatting.DateAndTime.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#3)]  
  
 [回到表格](#table)  
  
<a name="FullDateLongTime"></a>   
## <a name="the-full-date-long-time-f-format-specifier"></a>完整日期完整時間 ("F") 格式規範  
 "F" 標準格式規範表示由目前 <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> 屬性所定義的自訂日期和時間格式字串。 例如，不因文化特性而異的自訂格式字串為 "dddd, dd MMMM yyyy HH:mm:ss"。  
  
 下表列出可控制傳回字串之格式設定的 <xref:System.Globalization.DateTimeFormatInfo> 物件屬性。 由某些文化特性的 <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A> 屬性所傳回的自訂格式規範，可能不會使用所有屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A>|定義結果字串的整體格式。|  
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|定義可顯示在結果字串中的當地語系化日期名稱。|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|定義可顯示在結果字串中的當地語系化月份名稱。|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|定義分隔時間之小時、分鐘和秒鐘元件的字串。|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|定義表示從午夜到中午之前時間 (12 小時制) 的字串。|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|定義表示從中午到午夜之前時間 (12 小時制) 的字串。|  
  
 下列範例使用 "F" 格式規範來顯示日期和時間值。  
  
 [!code-csharp[Formatting.DateAndTime.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#4)]
 [!code-vb[Formatting.DateAndTime.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#4)]  
  
 [回到表格](#table)  
  
<a name="GeneralDateShortTime"></a>   
## <a name="the-general-date-short-time-g-format-specifier"></a>一般日期簡短時間 ("g") 格式規範  
 "g" 標準格式規範表示簡短日期 ("d") 和簡短時間 ("t") 模式的組合，以空格分隔。  
  
 結果字串會受到特定 <xref:System.Globalization.DateTimeFormatInfo> 物件的格式設定資訊所影響。 下表列出可控制傳回字串之格式設定的 <xref:System.Globalization.DateTimeFormatInfo> 物件屬性。 由某些文化特性的 <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> 和 <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> 屬性所傳回的自訂格式規範，可能不會使用所有屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A>|定義結果字串之日期元件的格式。|  
|<xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A>|定義結果字串之時間元件的格式。|  
|<xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A>|定義分隔日期之年份、月份和日期元件的字串。|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|定義分隔時間之小時、分鐘和秒鐘元件的字串。|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|定義表示從午夜到中午之前時間 (12 小時制) 的字串。|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|定義表示從中午到午夜之前時間 (12 小時制) 的字串。|  
  
 下列範例使用 "g" 格式規範來顯示日期和時間值。  
  
 [!code-csharp[Formatting.DateAndTime.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#5)]  
  
 [回到表格](#table)  
  
<a name="GeneralDateLongTime"></a>   
## <a name="the-general-date-long-time-g-format-specifier"></a>一般日期完整時間 ("G") 格式規範  
 "G" 標準格式規範表示簡短日期 ("d") 和完整時間 ("T") 模式的組合，以空格分隔。  
  
 結果字串會受到特定 <xref:System.Globalization.DateTimeFormatInfo> 物件的格式設定資訊所影響。 下表列出可控制傳回字串之格式設定的 <xref:System.Globalization.DateTimeFormatInfo> 物件屬性。 由某些文化特性的 <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType> 和 <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> 屬性所傳回的自訂格式規範，可能不會使用所有屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A>|定義結果字串之日期元件的格式。|  
|<xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A>|定義結果字串之時間元件的格式。|  
|<xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A>|定義分隔日期之年份、月份和日期元件的字串。|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|定義分隔時間之小時、分鐘和秒鐘元件的字串。|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|定義表示從午夜到中午之前時間 (12 小時制) 的字串。|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|定義表示從中午到午夜之前時間 (12 小時制) 的字串。|  
  
 下列範例使用 "G" 格式規範來顯示日期和時間值。  
  
 [!code-csharp[Formatting.DateAndTime.Standard#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#6)]
 [!code-vb[Formatting.DateAndTime.Standard#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#6)]  
  
 [回到表格](#table)  
  
<a name="MonthDay"></a>   
## <a name="the-month-m-m-format-specifier"></a>月 ("M"、"m") 格式規範  
 "M" 或 "m" 標準格式規範表示由目前 <xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern%2A?displayProperty=nameWithType> 屬性所定義的自訂日期和時間格式字串。 例如，不因文化特性而異的自訂格式字串為 "MMMM dd"。  
  
 下表列出可控制傳回字串之格式設定的 <xref:System.Globalization.DateTimeFormatInfo> 物件屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern%2A>|定義結果字串的整體格式。|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|定義可顯示在結果字串中的當地語系化月份名稱。|  
  
 下列範例使用 "m" 格式規範來顯示日期和時間值。  
  
 [!code-csharp[Formatting.DateAndTime.Standard#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#7)]
 [!code-vb[Formatting.DateAndTime.Standard#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#7)]  
  
 [回到表格](#table)  
  
<a name="Roundtrip"></a>   
## <a name="the-round-trip-o-o-format-specifier"></a>來回 ("O"、"o") 格式規範  
 "O" 或 "o" 標準格式規範可表示使用保存時區資訊之模式的自訂日期和時間格式字串，並發出符合 ISO 8601 的結果字串。 若為 <xref:System.DateTime> 值，此格式規範是設計來以純文字保存日期和時間值以及 <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> 屬性。 如果將 <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> 或 <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> 方法的 `styles` 參數設定為 <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>，則可以使用這兩個方法來剖析還原格式化字串。  
  
 "O" 或 "o" 標準格式規範對應至 <xref:System.DateTime> 值的 "yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffK" 自訂格式字串，也對應至 <xref:System.DateTimeOffset> 值的 "yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffzzz" 自訂格式字串。 在此字串中，分隔個別字元 (例如連字號、冒號和字母 "T") 的各組單引號表示個別字元為不可變更的常值。 所有格符號不會出現在輸出字串中。  
  
 'O"或"o"標準格式規範 (以及"yyyy '-' MM'-'dd'T' HH': 'mm':'ss '。 'Ss'.'fffffffk"自訂格式字串） 利用 ISO 8601 表示時區的資訊，以保留的三種方式<xref:System.DateTime.Kind%2A>屬性<xref:System.DateTime>值：  
  
-   <xref:System.DateTimeKind.Local?displayProperty=nameWithType> 日期和時間值的時區元件是與 UTC 的時差 (例如，+01:00、-07:00)。 所有 <xref:System.DateTimeOffset> 值也都是以此格式表示。  
  
-   <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> 日期和時間值的時區元件使用 "Z" (代表零時差) 來表示 UTC。  
  
-   <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> 日期和時間值沒有時區資訊。  
  
 因為 "O" 或 "o" 標準格式規範符合國際標準，所以使用該規範的或剖析作業一律使用不因國別而異的文化特性和西曆。  
  
 傳遞至 `Parse` 和 `TryParse` 的 `ParseExact`、`TryParseExact`、<xref:System.DateTime> 和 <xref:System.DateTimeOffset> 方法的字串如果是這些格式，就可以使用 "O" 或 "o" 格式規範來剖析。 在 <xref:System.DateTime> 物件的案例中，您呼叫的剖析多載應該也要包含 `styles` 參數，且值為 <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>。 請注意，如果您呼叫剖析方法時，使用對應於 "O" 或 "o" 格式規範的自訂格式字串，將不會取得與 "O" 或 "o" 相同的結果。 這是因為使用自訂格式字串的剖析方法，無法剖析缺少時區元件或使用 "Z" 來指示 UTC 之日期和時間值的字串表示法。  
  
 下列範例使用 "o" 格式規範，在美國太平洋時區系統上顯示一連串的 <xref:System.DateTime> 值以及 <xref:System.DateTimeOffset> 值。  
  
 [!code-csharp[Formatting.DateAndTime.Standard#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/o1.cs#8)]
 [!code-vb[Formatting.DateAndTime.Standard#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/o1.vb#8)]  
  
 下列範例使用 "o" 格式規範建立格式化字串，然後呼叫日期和時間 `Parse` 方法來還原原始日期和時間值。  
  
 [!code-csharp[Formatting.DateandTime.Standard#16](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Roundtrip1.cs#16)]
 [!code-vb[Formatting.DateandTime.Standard#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/RoundTrip1.vb#16)]  
  
 [回到表格](#table)  
  
<a name="RFC1123"></a>   
## <a name="the-rfc1123-r-r-format-specifier"></a>RFC1123 ("R"、"r") 格式規範  
 "R" 或 "r" 標準格式規範表示由 <xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A?displayProperty=nameWithType> 屬性所定義的自訂日期和時間格式字串。 此模式反映已定義的標準，且屬性為唯讀。 因此，不論所使用的文化特性或提供的格式提供者為何，它一定會是相同的。 自訂格式字串為 "ddd, dd MMM yyyy HH':'mm':'ss 'GMT'"。 使用這個標準格式規範時，格式或剖析作業一律使用不因文化特性而異。  
  
 在表示不因文化特性而異之 <xref:System.Globalization.DateTimeFormatInfo> 屬性所傳回的 <xref:System.Globalization.DateTimeFormatInfo.InvariantInfo%2A?displayProperty=nameWithType> 物件中，有下列屬性會影響結果字串。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern%2A>|定義結果字串的格式。|  
|<xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A>|定義可顯示在結果字串中的縮寫日期名稱。|  
|<xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames%2A>|定義可顯示在結果字串中的縮寫月份名稱。|  
  
 雖然 RFC 1123 標準以國際標準時間 (UTC) 來表示時間，但對於要進行格式化的 <xref:System.DateTime> 物件，格式化作業並不會修改這些物件的值。 因此，您必須先呼叫 <xref:System.DateTime> 方法將 <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> 值轉換成 UTC，才能執行格式化作業。 相反地，<xref:System.DateTimeOffset> 值會自動執行這項轉換，因此在格式化作業之前，不需要呼叫 <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> 方法。  
  
 下列範例會使用 "r" 格式規範，在美國太平洋時區系統上顯示 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 值。  
  
 [!code-csharp[Formatting.DateAndTime.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#9)]
 [!code-vb[Formatting.DateAndTime.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#9)]  
  
 [回到表格](#table)  
  
<a name="Sortable"></a>   
## <a name="the-sortable-s-format-specifier"></a>可排序 ("s") 格式規範  
 "s" 標準格式規範表示由 <xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern%2A?displayProperty=nameWithType> 屬性所定義的自訂日期和時間格式字串。 此模式反映已定義的標準 (ISO 8601)，且屬性為唯讀。 因此，不論所使用的文化特性或提供的格式提供者為何，它一定會是相同的。 自訂格式字串為 "yyyy'-'MM'-'dd'T'HH':'mm':'ss"。  
  
 "s" 格式規範的目的在於產生結果字串時，能夠根據日期和時間值，一致地以遞增或遞減順序排序。 如此一來，雖然 "s" 標準格式規範會以一致的格式來表示日期和時間值，但是格式化作業不會修改日期和時間物件的值 (為了反映其 <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> 屬性或其 <xref:System.DateTimeOffset.Offset%2A?displayProperty=nameWithType> 值已格式化該值)。 例如，格式化日期和時間值 2014-11-15T18:32:17+00:00 和 2014-11-15T18:32:17+08:00 所產生的結果字串相同。  
  
 使用這個標準格式規範時，格式或剖析作業一律使用不因文化特性而異。  
  
 下列範例會使用 "s" 格式規範，在美國太平洋時區系統上顯示 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 值。  
  
 [!code-csharp[Formatting.DateAndTime.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#10)]
 [!code-vb[Formatting.DateAndTime.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#10)]  
  
 [回到表格](#table)  
  
<a name="ShortTime"></a>   
## <a name="the-short-time-t-format-specifier"></a>簡短時間 ("t") 格式規範  
 "t" 標準格式規範表示由目前 <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> 屬性所定義的自訂日期和時間格式字串。 例如，不因文化特性而異的自訂格式字串為 "HH:mm"。  
  
 結果字串會受到特定 <xref:System.Globalization.DateTimeFormatInfo> 物件的格式設定資訊所影響。 下表列出可控制傳回字串之格式設定的 <xref:System.Globalization.DateTimeFormatInfo> 物件屬性。 由某些文化特性的 <xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A?displayProperty=nameWithType> 屬性所傳回的自訂格式規範，可能不會使用所有屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern%2A>|定義結果字串之時間元件的格式。|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|定義分隔時間之小時、分鐘和秒鐘元件的字串。|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|定義表示從午夜到中午之前時間 (12 小時制) 的字串。|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|定義表示從中午到午夜之前時間 (12 小時制) 的字串。|  
  
 下列範例使用 "t" 格式規範來顯示日期和時間值。  
  
 [!code-csharp[Formatting.DateAndTime.Standard#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#11)]
 [!code-vb[Formatting.DateAndTime.Standard#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#11)]  
  
 [回到表格](#table)  
  
<a name="LongTime"></a>   
## <a name="the-long-time-t-format-specifier"></a>完整時間 ("T") 格式規範  
 "T" 標準格式規範表示由特定文化特性之 <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> 屬性所定義的自訂日期和時間格式字串。 例如，不因文化特性而異的自訂格式字串為 "HH:mm:ss"。  
  
 下表列出可控制傳回字串之格式設定的 <xref:System.Globalization.DateTimeFormatInfo> 物件屬性。 由某些文化特性的 <xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A?displayProperty=nameWithType> 屬性所傳回的自訂格式規範，可能不會使用所有屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.LongTimePattern%2A>|定義結果字串之時間元件的格式。|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|定義分隔時間之小時、分鐘和秒鐘元件的字串。|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|定義表示從午夜到中午之前時間 (12 小時制) 的字串。|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|定義表示從中午到午夜之前時間 (12 小時制) 的字串。|  
  
 下列範例使用 "T" 格式規範來顯示日期和時間值。  
  
 [!code-csharp[Formatting.DateAndTime.Standard#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#12)]
 [!code-vb[Formatting.DateAndTime.Standard#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#12)]  
  
 [回到表格](#table)  
  
<a name="UniversalSortable"></a>   
## <a name="the-universal-sortable-u-format-specifier"></a>國際可排序 ("u") 格式規範  
 "u" 標準格式規範表示由 <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A?displayProperty=nameWithType> 屬性所定義的自訂日期和時間格式字串。 此模式反映已定義的標準，且屬性為唯讀。 因此，不論所使用的文化特性或提供的格式提供者為何，它一定會是相同的。 自訂格式字串為 "yyyy'-'MM'-'dd HH':'mm':'ss'Z'"。 使用這個標準格式規範時，格式或剖析作業一律使用不因文化特性而異。  
  
 雖然結果字串應該以國際標準時間 (UTC) 來表示時間，但在格式化作業期間，原始 <xref:System.DateTime> 值不會執行任何轉換。 因此，您必須先呼叫 <xref:System.DateTime> 方法將 <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> 值轉換成 UTC，才能將它格式化。  相反地，<xref:System.DateTimeOffset> 值會自動執行這項轉換，因此在格式化作業之前，不需要呼叫 <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> 方法。  
  
 下列範例使用 "u" 格式規範來顯示日期和時間值。  
  
 [!code-csharp[Formatting.DateAndTime.Standard#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Standard#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#13)]  
  
 [回到表格](#table)  
  
<a name="UniversalFull"></a>   
## <a name="the-universal-full-u-format-specifier"></a>國際完整 ("U") 格式規範  
 "U" 標準格式規範表示由指定文化特性之 <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> 屬性所定義的自訂日期和時間格式字串。 此模式與 "F" 模式相同。 不過，<xref:System.DateTime> 值在格式化之前會自動轉換為 UTC。  
  
 下表列出可控制傳回字串之格式設定的 <xref:System.Globalization.DateTimeFormatInfo> 物件屬性。 由某些文化特性的 <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A> 屬性所傳回的自訂格式規範，可能不會使用所有屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A>|定義結果字串的整體格式。|  
|<xref:System.Globalization.DateTimeFormatInfo.DayNames%2A>|定義可顯示在結果字串中的當地語系化日期名稱。|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|定義可顯示在結果字串中的當地語系化月份名稱。|  
|<xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A>|定義分隔時間之小時、分鐘和秒鐘元件的字串。|  
|<xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A>|定義表示從午夜到中午之前時間 (12 小時制) 的字串。|  
|<xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A>|定義表示從中午到午夜之前時間 (12 小時制) 的字串。|  
  
 <xref:System.DateTimeOffset> 類型不支援 "U" 格式規範，如果使用它來格式化 <xref:System.FormatException> 值，則會擲回 <xref:System.DateTimeOffset>。  
  
 下列範例使用 "U" 格式規範來顯示日期和時間值。  
  
 [!code-csharp[Formatting.DateAndTime.Standard#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#14)]
 [!code-vb[Formatting.DateAndTime.Standard#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#14)]  
  
 [回到表格](#table)  
  
<a name="YearMonth"></a>   
## <a name="the-year-month-y-y-format-specifier"></a>年月 ("Y"、"y") 格式規範  
 "Y" 或 "y" 標準格式規範表示由指定文化特性之 <xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern%2A?displayProperty=nameWithType> 屬性所定義的自訂日期和時間格式字串。 例如，不因文化特性而異的自訂格式字串為 "yyyy MMMM"。  
  
 下表列出可控制傳回字串之格式設定的 <xref:System.Globalization.DateTimeFormatInfo> 物件屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern%2A>|定義結果字串的整體格式。|  
|<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A>|定義可顯示在結果字串中的當地語系化月份名稱。|  
  
 下列範例使用 "y" 格式規範來顯示日期和時間值。  
  
 [!code-csharp[Formatting.DateAndTime.Standard#15](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Standard/cs/Standard1.cs#15)]
 [!code-vb[Formatting.DateAndTime.Standard#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Standard/vb/Standard1.vb#15)]  
  
 [回到表格](#table)  
  
<a name="Notes"></a>   
## <a name="notes"></a>備註  
  
### <a name="control-panel-settings"></a>控制台設定值  
 [控制台] 中 [ **地區及語言選項]** 項目的設定會影響格式化作業所產生的結果字串。 這些設定是用來初始化與目前執行緒文化特性相關的 <xref:System.Globalization.DateTimeFormatInfo> 物件，該物件會提供用來管理格式的值。 使用不同設定的電腦會產生不同的結果字串。  
  
 此外，如果您使用<xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType>建構函式來具現化新<xref:System.Globalization.CultureInfo>物件，代表相同的文化特性與目前的系統文化特性，所建立的任何自訂**地區及語言選項**在控制台中的項目會套用至新<xref:System.Globalization.CultureInfo>物件。 您可以使用 <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> 建構函式來建立不反映系統自訂的 <xref:System.Globalization.CultureInfo> 物件。  
  
### <a name="datetimeformatinfo-properties"></a>DateTimeFormatInfo 屬性  
 格式會受到目前 <xref:System.Globalization.DateTimeFormatInfo> 物件的影響，而此物件是由目前執行緒文化特性隱含提供或由叫用格式之方法的 <xref:System.IFormatProvider> 參數明確提供。 針對 <xref:System.IFormatProvider> 參數，您的應用程式應指定代表文化特性的 <xref:System.Globalization.CultureInfo> 物件，或是指定代表特定文化特性之日期和時間格式化慣例的 <xref:System.Globalization.DateTimeFormatInfo> 物件。 許多標準日期和時間格式規範都是格式化模式的別名，這些模式是由目前 <xref:System.Globalization.DateTimeFormatInfo> 物件的屬性所定義。 您的應用程式可以變更對應 <xref:System.Globalization.DateTimeFormatInfo> 屬性的對應日期和時間格式模式，藉此改變某些標準日期和時間格式規範所產生的結果。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.DateTime?displayProperty=nameWithType>  
 <xref:System.DateTimeOffset?displayProperty=nameWithType>  
 [格式化類型](../../../docs/standard/base-types/formatting-types.md)  
 [Custom Date and Time Format Strings](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)  
 [範例：.NET Framework 4 格式化公用程式](http://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
