---
title: 自訂日期和時間格式字串
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.assetid: 98b374e3-0cc2-4c78-ab44-efb671d71984
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f51e3f36594a6f66c5fad32214d84a11b78726a4
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2018
ms.locfileid: "47399342"
---
# <a name="custom-date-and-time-format-strings"></a>自訂日期和時間格式字串

日期和時間格式字串會定義對 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 值執行格式化作業後所產生的文字表示。 另外還會定義剖析作業所需日期和時間值的表示，以便成功地將字串轉換成日期和時間。 自訂格式字串是由一個或多個自訂日期和時間格式規範所組成。 任何不是[標準日期和時間格式字串](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)的字串都會被解譯為自訂日期和時間格式字串。

> [!TIP]
> 您可以下載[格式化公用程式](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)，這個應用程式可讓您將格式字串套用至日期和時間值或數值，並且顯示結果字串。

 自訂日期和時間格式字串可以與 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 值搭配使用。

[!INCLUDE[C# interactive-note](~/includes/csharp-interactive-with-utc-partial-note.md)] 

<a name="table"></a> 在格式化作業中，自訂日期和時間格式字串可以搭配日期和時間執行個體的 `ToString` 方法或是支援複合格式的方法使用。 以下範例說明這兩種用法。

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#17](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/custandformatting1.cs#17)]
 [!code-vb[Formatting.DateAndTime.Custom#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/custandformatting1.vb#17)]

 在剖析作業中，自訂日期和時間格式字串可以搭配 <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>、<xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>、<xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> 和 <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> 方法使用。 這些方法需要輸入字串完全符合特定模式，剖析作業才會成功。 下列範例說明呼叫 <xref:System.DateTimeOffset.ParseExact%28System.String%2CSystem.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> 方法來剖析必須包含日、月和兩位數年的日期。

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#18](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/custandparsing1.cs#18)]
 [!code-vb[Formatting.DateAndTime.Custom#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/custandparsing1.vb#18)]

 下表說明自訂日期和時間格式規範，並顯示每個格式規範所產生的結果字串。 根據預設，結果字串會反映 en-US 文化特性的格式設定慣例。 如果特定格式規範會產生當地語系化的結果字串，則範例也會註明結果字串適用的文化特性。 如需使用自訂日期和時間格式字串的詳細資訊，請參閱注意一節。

| 格式規範 | 描述 | 範例 |
| ---------------------- | ----------------- | -------------- |
|"d"|月份天數，從 1 到 31。<br /><br /> 詳細資訊：["d" 自訂格式規範](#dSpecifier)。|2009-06-01T13:45:30 -> 1<br /><br /> 2009-06-15T13:45:30 -> 15|
|"dd"|月份天數，從 01 到 31。<br /><br /> 詳細資訊：["dd" 自訂格式規範](#ddSpecifier)。|2009-06-01T13:45:30 -> 01<br /><br /> 2009-06-15T13:45:30 -> 15|
|"ddd"|星期幾的縮寫名稱。<br /><br /> 詳細資訊：["ddd" 自訂格式規範](#dddSpecifier)。|2009-06-15T13:45:30 -> Mon (en-US)<br /><br /> 2009-06-15T13:45:30 -> Пн (ru-RU)<br /><br /> 2009-06-15T13:45:30 -> lun. (fr-FR)|
|"dddd"|星期幾的完整名稱。<br /><br /> 詳細資訊：["dddd" 自訂格式規範](#ddddSpecifier)。|2009-06-15T13:45:30 -> Monday (en-US)<br /><br /> 2009-06-15T13:45:30 -> понедельник (ru-RU)<br /><br /> 2009-06-15T13:45:30 -> lundi (fr-FR)|
|"f"|日期和時間值中的十分之一秒。<br /><br /> 詳細資訊：["f" 自訂格式規範](#fSpecifier)。|2009-06-15T13:45:30.6170000 -> 6<br /><br /> 2009-06-15T13:45:30.05 -> 0|
|"ff"|日期和時間值中的百分之一秒。<br /><br /> 詳細資訊：["ff" 自訂格式規範](#ffSpecifier)。|2009-06-15T13:45:30.6170000 -> 61<br /><br /> 2009-06-15T13:45:30.0050000 -> 00|
|"fff"|日期和時間值中的千分之一秒。<br /><br /> 詳細資訊：["fff" 自訂格式規範](#fffSpecifier)。|6/15/2009 13:45:30.617 -> 617<br /><br /> 6/15/2009 13:45:30.0005 -> 000|
|"ffff"|日期和時間值中的萬分之一秒。<br /><br /> 詳細資訊：["ffff" 自訂格式規範](#ffffSpecifier)。|2009-06-15T13:45:30.6175000 -> 6175<br /><br /> 2009-06-15T13:45:30.0000500  -> 0000|
|"fffff"|日期和時間值中的十萬分之一秒。<br /><br /> 詳細資訊：["fffff" 自訂格式規範](#fffffSpecifier)。|2009-06-15T13:45:30.6175400 -> 61754<br /><br /> 6/15/2009 13:45:30.000005 -> 00000|
|"ffffff"|日期和時間值中的百萬分之一秒。<br /><br /> 詳細資訊：["ffffff" 自訂格式規範](#ffffffSpecifier)。|2009-06-15T13:45:30.6175420 -> 617542<br /><br /> 2009-06-15T13:45:30.0000005 -> 000000|
|"fffffff"|日期和時間值中的千萬分之一秒。<br /><br /> 詳細資訊：["fffffff" 自訂格式規範](#fffffffSpecifier)。|2009-06-15T13:45:30.6175425 -> 6175425<br /><br /> 2009-06-15T13:45:30.0001150 -> 0001150|
|"F"|如果不是零，則為日期和時間值中的十分之一秒。<br /><br /> 詳細資訊：["F" 自訂格式規範](#F_Specifier)。|2009-06-15T13:45:30.6170000 -> 6<br /><br /> 2009-06-15T13:45:30.0500000 -> (沒有輸出)|
|"FF"|如果不是零，則為日期和時間值中的百分之一秒。<br /><br /> 詳細資訊：["FF" 自訂格式規範](#FF_Specifier)。|2009-06-15T13:45:30.6170000 -> 61<br /><br /> 2009-06-15T13:45:30.0050000 -> (沒有輸出)|
|"FFF"|如果不是零，則為日期和時間值中的千分之一秒。<br /><br /> 詳細資訊：["FFF" 自訂格式規範](#FFF_Specifier)。|2009-06-15T13:45:30.6170000 -> 617<br /><br /> 2009-06-15T13:45:30.0005000 -> (沒有輸出)|
|"FFFF"|如果不是零，則為日期和時間值中的萬分之一秒。<br /><br /> 詳細資訊：["FFFF" 自訂格式規範](#FFFF_Specifier)。|2009-06-15T13:45:30.5275000 -> 5275<br /><br /> 2009-06-15T13:45:30.0000500 -> (沒有輸出)|
|"FFFFF"|如果不是零，則為日期和時間值中的十萬分之一秒。<br /><br /> 詳細資訊：["FFFFF" 自訂格式規範](#FFFFF_Specifier)。|2009-06-15T13:45:30.6175400 -> 61754<br /><br /> 2009-06-15T13:45:30.0000050 -> (沒有輸出)|
|"FFFFFF"|如果不是零，則為日期和時間值中的百萬分之一秒。<br /><br /> 詳細資訊：["FFFFFF" 自訂格式規範](#FFFFFF_Specifier)。|2009-06-15T13:45:30.6175420 -> 617542<br /><br /> 2009-06-15T13:45:30.0000005 -> (沒有輸出)|
|"FFFFFFF"|如果不是零，則為日期和時間值中的千萬分之一秒。<br /><br /> 詳細資訊：["FFFFFFF" 自訂格式規範](#FFFFFFF_Specifier)。|2009-06-15T13:45:30.6175425 -> 6175425<br /><br /> 2009-06-15T13:45:30.0001150 -> 000115|
|"g"、"gg"|週期或紀元。<br /><br /> 詳細資訊：["g" 或 "gg" 自訂格式規範](#gSpecifier)。|2009-06-15T13:45:30.6170000 -> A.D.|
|"h"|採用 12 小時制的小時，從 1 到 12。<br /><br /> 詳細資訊：["h" 自訂格式規範](#hSpecifier)。|2009-06-15T01:45:30 -> 1<br /><br /> 2009-06-15T13:45:30 -> 1|
|"hh"|採用 12 小時制的小時，從 01 到 12。<br /><br /> 詳細資訊：["hh" 自訂格式規範](#hhSpecifier)。|2009-06-15T01:45:30 -> 01<br /><br /> 2009-06-15T13:45:30 -> 01|
|"H"|採用 24 小時制的小時，從 0 到 23。<br /><br /> 詳細資訊：["H" 自訂格式規範](#H_Specifier)。|2009-06-15T01:45:30 -> 1<br /><br /> 2009-06-15T13:45:30 -> 13|
|"HH"|採用 24 小時制的小時，從 00 到 23。<br /><br /> 詳細資訊：["HH" 自訂格式規範](#HH_Specifier)。|2009-06-15T01:45:30 -> 01<br /><br /> 2009-06-15T13:45:30 -> 13|
|"K"|時區資訊。<br /><br /> 詳細資訊：["K" 自訂格式規範](#KSpecifier)。|搭配 <xref:System.DateTime> 值：<br /><br /> 2009-06-15T13:45:30, Kind Unspecified -><br /><br /> 2009-06-15T13:45:30, Kind Utc -> Z<br /><br /> 2009-06-15T13:45:30, Kind Local -> -07:00 (依據本機電腦設定)<br /><br /> 搭配 <xref:System.DateTimeOffset> 值：<br /><br /> 2009-06-15T01:45:30-07:00 --> -07:00<br /><br /> 2009-06-15T08:45:30+00:00 --> +00:00|
|"m"|分鐘，從 0 到 59。<br /><br /> 詳細資訊：["m" 自訂格式規範](#mSpecifier)。|2009-06-15T01:09:30 -> 9<br /><br /> 2009-06-15T13:29:30 -> 29|
|"mm"|分鐘，從 00 到 59。<br /><br /> 詳細資訊：["mm" 自訂格式規範](#mmSpecifier)。|2009-06-15T01:09:30 -> 09<br /><br /> 2009-06-15T01:45:30 -> 45|
|"M"|月份，從 1 到 12。<br /><br /> 詳細資訊：["M" 自訂格式規範](#M_Specifier)。|2009-06-15T13:45:30 -> 6|
|"MM"|月份，從 01 到 12。<br /><br /> 詳細資訊：["MM" 自訂格式規範](#MM_Specifier)。|2009-06-15T13:45:30 -> 06|
|"MMM"|月份的縮寫名稱。<br /><br /> 詳細資訊：["MMM" 自訂格式規範](#MMM_Specifier)。|2009-06-15T13:45:30 -> Jun (en-US)<br /><br /> 2009-06-15T13:45:30 -> juin (fr-FR)<br /><br /> 2009-06-15T13:45:30 -> Jun (zu-ZA)|
|"MMMM"|月份的完整名稱。<br /><br /> 詳細資訊：["MMMM" 自訂格式規範](#MMMM_Specifier)。|2009-06-15T13:45:30 -> June (en-US)<br /><br /> 2009-06-15T13:45:30 -> juni (da-DK)<br /><br /> 2009-06-15T13:45:30 -> uJuni (zu-ZA)|
|"s"|秒數，從 0 到 59。<br /><br /> 詳細資訊：["s" 自訂格式規範](#sSpecifier)。|2009-06-15T13:45:09 -> 9|
|"ss"|秒數，從 00 到 59。<br /><br /> 詳細資訊：["ss" 自訂格式規範](#ssSpecifier)。|2009-06-15T13:45:09 -> 09|
|"t"|AM/PM 指示項的第一個字元。<br /><br /> 詳細資訊：["t" 自訂格式規範](#tSpecifier)。|2009-06-15T13:45:30 -> P (en-US)<br /><br /> 2009-06-15T13:45:30 -> 午 (ja-JP)<br /><br /> 2009-06-15T13:45:30 ->  (fr-FR)|
|"tt"|AM/PM 指示項。<br /><br /> 詳細資訊：["tt" 自訂格式規範](#ttSpecifier)。|2009-06-15T13:45:30 -> PM (en-US)<br /><br /> 2009-06-15T13:45:30 -> 午後 (ja-JP)<br /><br /> 2009-06-15T13:45:30 ->  (fr-FR)|
|"y"|年份，從 0 到 99。<br /><br /> 詳細資訊：["y" 自訂格式規範](#ySpecifier)。|0001-01-01T00:00:00 -> 1<br /><br /> 0900-01-01T00:00:00 -> 0<br /><br /> 1900-01-01T00:00:00 -> 0<br /><br /> 2009-06-15T13:45:30 -> 9<br /><br /> 2019-06-15T13:45:30 -> 19|
|"yy"|年份，從 00 到 99。<br /><br /> 詳細資訊：["yy" 自訂格式規範](#yySpecifier)。|0001-01-01T00:00:00 -> 01<br /><br /> 0900-01-01T00:00:00 -> 00<br /><br /> 1900-01-01T00:00:00 -> 00<br /><br /> 2019-06-15T13:45:30 -> 19|
|"yyy"|年份，至少三位數。<br /><br /> 詳細資訊：["yyy" 自訂格式規範](#yyySpecifier)。|0001-01-01T00:00:00 -> 001<br /><br /> 0900-01-01T00:00:00 -> 900<br /><br /> 1900-01-01T00:00:00 -> 1900<br /><br /> 2009-06-15T13:45:30 -> 2009|
|"yyyy"|以四位數表示的年份。<br /><br /> 詳細資訊：["yyyy" 自訂格式規範](#yyyySpecifier)。|0001-01-01T00:00:00 -> 0001<br /><br /> 0900-01-01T00:00:00 -> 0900<br /><br /> 1900-01-01T00:00:00 -> 1900<br /><br /> 2009-06-15T13:45:30 -> 2009|
|"yyyyy"|以五位數表示的年份。<br /><br /> 詳細資訊：["yyyyy" 自訂格式規範](#yyyyySpecifier)。|0001-01-01T00:00:00 -> 00001<br /><br /> 2009-06-15T13:45:30 -> 02009|
|"z"|與 UTC 相差的時數，不加上前置零。<br /><br /> 詳細資訊：["z" 自訂格式規範](#zSpecifier)。|2009-06-15T13:45:30-07:00 -> -7|
|"zz"|與 UTC 相差的時數，單一位數值會加上前置零。<br /><br /> 詳細資訊：["zz" 自訂格式規範](#zzSpecifier)。|2009-06-15T13:45:30-07:00 -> -07|
|"zzz"|與 UTC 相差的時數和分鐘數。<br /><br /> 詳細資訊：["zzz" 自訂格式規範](#zzzSpecifier)。|2009-06-15T13:45:30-07:00 -> -07:00|
|":"|時間分隔符號。<br /><br /> 詳細資訊：[":" 自訂格式規範](#timeSeparator)。|2009-06-15T13:45:30 -> : (en-US)<br /><br /> 2009-06-15T13:45:30 -> . (it-IT)<br /><br /> 2009-06-15T13:45:30 -> : (ja-JP)|
|"/"|日期分隔符號。<br /><br /> 詳細資訊：["/" 自訂格式規範](#dateSeparator)。|2009-06-15T13:45:30 -> / (en-US)<br /><br /> 2009-06-15T13:45:30 -> - (ar-DZ)<br /><br /> 2009-06-15T13:45:30 -> . (tr-TR)|
|"*string*"<br /><br /> '*string*'|常值字串分隔符號。<br /><br /> 詳細資訊︰[字元常值](#Literals)。|2009-06-15T13:45:30 ("arr:" h:m t) -> arr: 1:45 P<br /><br /> 2009-06-15T13:45:30 ('arr:' h:m t) -> arr: 1:45 P|
|%|將下列字元定義為自訂格式規範。<br /><br /> 詳細資訊：[使用單一自訂格式規範](#UsingSingleSpecifiers)。|2009-06-15T13:45:30 (%h) -> 1|
|\\|逸出字元。<br /><br /> 詳細資訊︰[字元常值](#Literals)和[使用逸出字元](#escape)。|2009-06-15T13:45:30 (h \h) -> 1 h|
|任意字元|字元會原封不動地複製到結果字串。<br /><br /> 詳細資訊︰[字元常值](#Literals)。|2009-06-15T01:45:30 (arr hh:mm t) -> arr 01:45 A|

 下列各節提供每個自訂日期和時間格式規範的其他資訊。 除非特別註明，否則每個規範都會產生相同的字串表示，無論是與 <xref:System.DateTime> 值或 <xref:System.DateTimeOffset> 值搭配使用。

<a name="dSpecifier"></a> 

## <a name="the-d-custom-format-specifier"></a>"d" 自訂格式規範
 "d" 自訂格式規範以 1 到 31 的數字來表示月份天數。 單一位數的天數會格式化為沒有前置零的數字。

 如果單獨使用 "d" 格式規範，而沒有其他自訂格式規範，則會將它解譯為 "d" 標準日期和時間格式規範。 如需使用單一格式規範的詳細資訊，請參閱本主題稍後的[使用單一自訂格式規範](#UsingSingleSpecifiers)。

 下列範例會在幾個格式字串中加入 "d" 自訂格式規範。

 [!code-csharp[Formatting.DateAndTime.Custom#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#1)]
 [!code-vb[Formatting.DateAndTime.Custom#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#1)]

 [回到表格](#table)

<a name="ddSpecifier"></a> 

## <a name="the-dd-custom-format-specifier"></a>"dd" 自訂格式規範
 "dd" 自訂格式字串以 01 到 31 的數字來表示月份天數。 單一位數的天數會格式化為有前置零的數字。

 下列範例會在自訂格式字串中加入 "dd" 自訂格式規範。

 [!code-csharp[Formatting.DateAndTime.Custom#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#2)]
 [!code-vb[Formatting.DateAndTime.Custom#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#2)]

 [回到表格](#table)

<a name="dddSpecifier"></a> 

## <a name="the-ddd-custom-format-specifier"></a>"ddd" 自訂格式規範
 "ddd" 自訂格式規範表示星期幾的縮寫名稱。 星期幾的當地語系化縮寫名稱是擷取自目前或指定之文化特性的 <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A?displayProperty=nameWithType> 屬性。

 下列範例會在自訂格式字串中加入 "ddd" 自訂格式規範。

 [!code-csharp[Formatting.DateAndTime.Custom#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#3)]
 [!code-vb[Formatting.DateAndTime.Custom#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#3)]

 [回到表格](#table)

<a name="ddddSpecifier"></a> 

## <a name="the-dddd-custom-format-specifier"></a>"dddd" 自訂格式規範
 "dddd" 自訂格式規範 (加上任意個額外的 "d" 規範) 表示星期幾的完整名稱。 星期幾的當地語系化名稱是擷取自目前或指定之文化特性的 <xref:System.Globalization.DateTimeFormatInfo.DayNames%2A?displayProperty=nameWithType> 屬性。

 下列範例會在自訂格式字串中加入 "dddd" 自訂格式規範。

 [!code-csharp[Formatting.DateAndTime.Custom#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#4)]
 [!code-vb[Formatting.DateAndTime.Custom#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#4)]

 [回到表格](#table)

<a name="fSpecifier"></a> 

## <a name="the-f-custom-format-specifier"></a>"f" 自訂格式規範
 "f" 自訂格式規範表示秒數的一位有效小數位數，也就是說，它表示日期和時間值中的十分之一秒。

 如果單獨使用 "f" 格式規範，而沒有其他格式規範，則會將它解譯為 "f" 標準日期和時間格式規範。 如需使用單一格式規範的詳細資訊，請參閱本主題稍後的[使用單一自訂格式規範](#UsingSingleSpecifiers)。

 當您使用 "f" 格式規範做為提供給 <xref:System.DateTime.ParseExact%2A>、<xref:System.DateTime.TryParseExact%2A>、<xref:System.DateTimeOffset.ParseExact%2A> 或 <xref:System.DateTimeOffset.TryParseExact%2A> 方法的一部分格式字串時，"f" 格式規範的數目表示秒數部分最重要的小數位數，必須存在此小數位數才能成功剖析字串。

 下列範例會在自訂格式字串中加入 "f" 自訂格式規範。

 [!code-csharp[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

 [回到表格](#table)

<a name="ffSpecifier"></a> 

## <a name="the-ff-custom-format-specifier"></a>"ff" 自訂格式規範
 "ff" 自訂格式規範表示秒數的兩位有效小數位數，也就是說，它表示日期和時間值中的百分之一秒。

 下列範例會在自訂格式字串中加入 "ff" 自訂格式規範。

 [!code-csharp[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

 [回到表格](#table)

<a name="fffSpecifier"></a> 

## <a name="the-fff-custom-format-specifier"></a>"fff" 自訂格式規範
 "fff" 自訂格式規範表示秒數的三位有效小數位數，也就是說，它表示日期和時間值中的千分之一秒。

 下列範例會在自訂格式字串中加入 "fff" 自訂格式規範。

 [!code-csharp[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

 [回到表格](#table)

<a name="ffffSpecifier"></a> 

## <a name="the-ffff-custom-format-specifier"></a>"ffff" 自訂格式規範
 "ffff" 自訂格式規範表示秒數的四位有效小數位數，也就是說，它表示日期和時間值中的萬分之一秒。

 雖然時間值的秒數部分可以顯示到萬分之一秒，但該值可能沒有太大的意義。 日期和時間值的精確度會根據系統時鐘的解析度而定。 在 Windows NT 3.5 (含) 以上版本和 Windows Vista 作業系統中，時鐘的解析度大約為 10-15 毫秒。

 [回到表格](#table)

<a name="fffffSpecifier"></a> 

## <a name="the-fffff-custom-format-specifier"></a>"fffff" 自訂格式規範
 "fffff" 自訂格式規範表示秒數的五位有效小數位數，也就是說，它表示日期和時間值中的十萬分之一秒。

 雖然時間值的秒數部分可以顯示到十萬分之一秒，但該值可能沒有太大的意義。 日期和時間值的精確度會根據系統時鐘的解析度而定。 在 Windows NT 3.5 (含) 以上版本和 Windows Vista 作業系統中，時鐘的解析度大約為 10-15 毫秒。

 [回到表格](#table)

<a name="ffffffSpecifier"></a> 

## <a name="the-ffffff-custom-format-specifier"></a>"ffffff" 自訂格式規範
 "ffffff" 自訂格式規範表示秒數的六位有效小數位數，也就是說，它表示日期和時間值中的百萬分之一秒。

 雖然時間值的秒數部分可以顯示到百萬分之一秒，但該值可能沒有太大的意義。 日期和時間值的精確度會根據系統時鐘的解析度而定。 在 Windows NT 3.5 (含) 以上版本和 Windows Vista 作業系統中，時鐘的解析度大約為 10-15 毫秒。

 [回到表格](#table)

<a name="fffffffSpecifier"></a> 

## <a name="the-fffffff-custom-format-specifier"></a>"fffffff" 自訂格式規範
 "fffffff" 自訂格式規範表示秒數的七位有效小數位數，也就是說，它表示日期和時間值中的千萬分之一秒。

 雖然時間值的秒數部分可以顯示到千萬分之一秒，但該值可能沒有太大的意義。 日期和時間值的精確度會根據系統時鐘的解析度而定。 在 Windows NT 3.5 (含) 以上版本和 Windows Vista 作業系統中，時鐘的解析度大約為 10-15 毫秒。

 [回到表格](#table)

<a name="F_Specifier"></a> 

## <a name="the-f-custom-format-specifier"></a>"F" 自訂格式規範
 "F" 自訂格式規範表示秒數的一位有效小數位數，也就是說，它表示日期和時間值中的十分之一秒。 如果數字為零，則不會顯示任何內容。

 如果單獨使用 "F" 格式規範，而沒有其他格式規範，則會將它解譯為 "F" 標準日期和時間格式規範。 如需使用單一格式規範的詳細資訊，請參閱本主題稍後的[使用單一自訂格式規範](#UsingSingleSpecifiers)。

 與 <xref:System.DateTime.ParseExact%2A>、<xref:System.DateTime.TryParseExact%2A>、<xref:System.DateTimeOffset.ParseExact%2A> 或 <xref:System.DateTimeOffset.TryParseExact%2A> 方法搭配使用的 "F" 格式規範數目，表示秒數部分最重要小數位數的上限，要成功剖析字串就不能超過此小數位數。

 下列範例會在自訂格式字串中加入 "F" 自訂格式規範。

 [!code-csharp[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

 [回到表格](#table)

<a name="FF_Specifier"></a> 

## <a name="the-ff-custom-format-specifier"></a>"FF" 自訂格式規範
 "FF" 自訂格式規範表示秒數的兩位有效小數位數，也就是說，它表示日期和時間值中的百分之一秒。 不過，結尾的零或兩個零的數字都不會顯示。

 下列範例會在自訂格式字串中加入 "FF" 自訂格式規範。

 [!code-csharp[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

 [回到表格](#table)

<a name="FFF_Specifier"></a> 

## <a name="the-fff-custom-format-specifier"></a>"FFF" 自訂格式規範
 "FFF" 自訂格式規範表示秒數的三位有效小數位數，也就是說，它表示日期和時間值中的千分之一秒。 不過，結尾的零或三個零的數字都不會顯示。

 下列範例會在自訂格式字串中加入 "FFF" 自訂格式規範。

 [!code-csharp[Formatting.DateAndTime.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#5)]
 [!code-vb[Formatting.DateAndTime.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#5)]

 [回到表格](#table)

<a name="FFFF_Specifier"></a> 

## <a name="the-ffff-custom-format-specifier"></a>"FFFF" 自訂格式規範
 "FFFF" 自訂格式規範表示秒數的四位有效小數位數，也就是說，它表示日期和時間值中的萬分之一秒。 不過，結尾的零或四個零的數字都不會顯示。

 雖然時間值的秒數部分可以顯示到萬分之一秒，但該值可能沒有太大的意義。 日期和時間值的精確度會根據系統時鐘的解析度而定。 在 Windows NT 3.5 (含) 以上版本和 Windows Vista 作業系統中，時鐘的解析度大約為 10-15 毫秒。

 [回到表格](#table)

<a name="FFFFF_Specifier"></a> 

## <a name="the-fffff-custom-format-specifier"></a>"FFFFF" 自訂格式規範
 "FFFFF" 自訂格式規範表示秒數的五位有效小數位數，也就是說，它表示日期和時間值中的十萬分之一秒。 不過，結尾的零或五個零的數字都不會顯示。

 雖然時間值的秒數部分可以顯示到十萬分之一秒，但該值可能沒有太大的意義。 日期和時間值的精確度會根據系統時鐘的解析度而定。 在 Windows NT 3.5 (含) 以上版本和 Windows Vista 作業系統中，時鐘的解析度大約為 10-15 毫秒。

 [回到表格](#table)

<a name="FFFFFF_Specifier"></a> 

## <a name="the-ffffff-custom-format-specifier"></a>"FFFFFF" 自訂格式規範
 "FFFFFF" 自訂格式規範表示秒數的六位有效小數位數，也就是說，它表示日期和時間值中的百萬分之一秒。 不過，結尾的零或六個零的數字都不會顯示。

 雖然時間值的秒數部分可以顯示到百萬分之一秒，但該值可能沒有太大的意義。 日期和時間值的精確度會根據系統時鐘的解析度而定。 在 Windows NT 3.5 (含) 以上版本和 Windows Vista 作業系統中，時鐘的解析度大約為 10-15 毫秒。

 [回到表格](#table)

<a name="FFFFFFF_Specifier"></a> 

## <a name="the-fffffff-custom-format-specifier"></a>"FFFFFFF" 自訂格式規範
 "FFFFFFF" 自訂格式規範表示秒數的七位有效小數位數，也就是說，它表示日期和時間值中的千萬分之一秒。 不過，結尾的零或七個零的數字都不會顯示。

 雖然時間值的秒數部分可以顯示到千萬分之一秒，但該值可能沒有太大的意義。 日期和時間值的精確度會根據系統時鐘的解析度而定。 在 Windows NT 3.5 (含) 以上版本和 Windows Vista 作業系統中，時鐘的解析度大約為 10-15 毫秒。

 [回到表格](#table)

<a name="gSpecifier"></a> 

## <a name="the-g-or-gg-custom-format-specifier"></a>"g" 或 "gg" 自訂格式規範
 "g" 或 "gg" 自訂格式規範 (加上任意個額外的 "g" 規範) 表示時期或時代，例如 A.D。 如果要格式化的日期沒有關聯的時期或時代字串，則格式化作業會忽略這個規範。

 如果單獨使用 "g" 格式規範，而沒有其他自訂格式規範，則會將它解譯為 "g" 標準日期和時間格式規範。 如需使用單一格式規範的詳細資訊，請參閱本主題稍後的[使用單一自訂格式規範](#UsingSingleSpecifiers)。

 下列範例會在自訂格式字串中加入 "g" 自訂格式規範。

 [!code-csharp[Formatting.DateAndTime.Custom#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#6)]
 [!code-vb[Formatting.DateAndTime.Custom#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#6)]

 [回到表格](#table)

<a name="hSpecifier"></a> 

## <a name="the-h-custom-format-specifier"></a>"h" 自訂格式規範
 "h" 自訂格式規範以 1 到 12 的數字來表示小時，也就是以 12 小時制來表示小時，從午夜或中午開始計算整點時數。 午夜後的特定小時與下午的相同小時會難以區分。 小時是不進位的，而且單一位數的小時會格式化為沒有前置零的數字。 例如，假設時間為上午或下午 5:43，則此自訂格式規範會顯示 "5"。

 如果單獨使用 "h" 格式規範，而沒有其他自訂格式規範，則會將它解譯為標準日期和時間格式規範，並擲回 <xref:System.FormatException>。 如需使用單一格式規範的詳細資訊，請參閱本主題稍後的[使用單一自訂格式規範](#UsingSingleSpecifiers)。

 下列範例會在自訂格式字串中加入 "h" 自訂格式規範。

 [!code-csharp[Formatting.DateAndTime.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
 [!code-vb[Formatting.DateAndTime.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

 [回到表格](#table)

<a name="hhSpecifier"></a> 

## <a name="the-hh-custom-format-specifier"></a>"hh" 自訂格式規範
 "hh" 自訂格式規範 (加上任意個額外的 "h" 規範) 以 01 到 12 的數字來表示小時，也就是以 12 小時制來表示小時，從午夜或中午開始計算整點時數。 午夜後的特定小時與下午的相同小時會難以區分。 小時是不進位的，而且單一位數的小時會格式化為有前置零的數字。 例如，假設時間為上午或下午 5:43，則此格式規範會顯示 "05"。

 下列範例會在自訂格式字串中加入 "hh" 自訂格式規範。

 [!code-csharp[Formatting.DateAndTime.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
 [!code-vb[Formatting.DateAndTime.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

 [回到表格](#table)

<a name="H_Specifier"></a> 

## <a name="the-h-custom-format-specifier"></a>"H" 自訂格式規範
 "H" 自訂格式規範以 0 到 23 的數字來表示小時，也就是採用以零為起始的 24 小時制來表示小時，從午夜開始計算時數。 單一位數的小時會格式化為沒有前置零的數字。

 如果單獨使用 "H" 格式規範，而沒有其他自訂格式規範，則會將它解譯為標準日期和時間格式規範，並擲回 <xref:System.FormatException>。 如需使用單一格式規範的詳細資訊，請參閱本主題稍後的[使用單一自訂格式規範](#UsingSingleSpecifiers)。

 下列範例會在自訂格式字串中加入 "H" 自訂格式規範。

 [!code-csharp[Formatting.DateAndTime.Custom#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#9)]
 [!code-vb[Formatting.DateAndTime.Custom#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#9)]

 [回到表格](#table)

<a name="HH_Specifier"></a> 

## <a name="the-hh-custom-format-specifier"></a>"HH" 自訂格式規範
 "HH" 自訂格式規範 (加上任意個額外的 "H" 規範) 以 00 到 23 的數字來表示小時，也就是採用以零為起始的 24 小時制來表示小時，從午夜開始計算時數。 單一位數的小時會格式化為具有前置零的數字。

 下列範例會在自訂格式字串中加入 "HH" 自訂格式規範。

 [!code-csharp[Formatting.DateAndTime.Custom#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#10)]
 [!code-vb[Formatting.DateAndTime.Custom#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#10)]

 [回到表格](#table)

<a name="KSpecifier"></a> 

## <a name="the-k-custom-format-specifier"></a>"K" 自訂格式規範
 "K" 自訂格式規範表示日期和時間值的時區資訊。 與 <xref:System.DateTime> 值搭配使用這個格式規範時，結果字串會由 <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> 屬性的值定義：

-   若為本地時區 (<xref:System.DateTime.Kind%2A?displayProperty=nameWithType> 的 <xref:System.DateTimeKind.Local?displayProperty=nameWithType> 屬性值)，此規範相當於 "zzz" 規範，所產生的結果字串會包含本地與國際標準時間 (UTC) 之間的時差，例如 "-07:00"。

-   若為 UTC 時間 (<xref:System.DateTime.Kind%2A?displayProperty=nameWithType> 的 <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> 屬性值)，結果字串會包含 "Z" 字元來表示 UTC 日期。

-   若為未指定時區的時間 (<xref:System.DateTime.Kind%2A?displayProperty=nameWithType> 屬性等於 <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> 的時間)，結果就相當於 <xref:System.String.Empty?displayProperty=nameWithType>。

 若為 <xref:System.DateTimeOffset> 值，"K" 格式規範相當於 "zzz" 格式規範，所產生的結果字串會包含 <xref:System.DateTimeOffset> 值與 UTC 之間的時差。

 如果單獨使用 "K" 格式規範，而沒有其他自訂格式規範，則會將它解譯為標準日期和時間格式規範，並擲回 <xref:System.FormatException>。 如需使用單一格式規範的詳細資訊，請參閱本主題稍後的[使用單一自訂格式規範](#UsingSingleSpecifiers)。

 下列範例會顯示美國太平洋時區中，"K" 自訂格式規範與各種 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 值搭配使用所產生的結果字串。

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#12)]
 [!code-vb[Formatting.DateAndTime.Custom#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#12)]

 [回到表格](#table)

<a name="mSpecifier"></a> 

## <a name="the-m-custom-format-specifier"></a>"m" 自訂格式規範
 "m" 自訂格式規範以 0 到 59 的數字來表示分鐘。 分鐘表示自上個整點以來已經過的完整分鐘數。 單一位數的分鐘會格式化為沒有前置零的數字。

 如果單獨使用 "m" 格式規範，而沒有其他自訂格式規範，則會將它解譯為 "m" 標準日期和時間格式規範。 如需使用單一格式規範的詳細資訊，請參閱本主題稍後的[使用單一自訂格式規範](#UsingSingleSpecifiers)。

 下列範例會在自訂格式字串中加入 "m" 自訂格式規範。

 [!code-csharp[Formatting.DateAndTime.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
 [!code-vb[Formatting.DateAndTime.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

 [回到表格](#table)

<a name="mmSpecifier"></a> 

## <a name="the-mm-custom-format-specifier"></a>"mm" 自訂格式規範
 "mm" 自訂格式規範 (加上任意個額外的 "m" 規範) 以 00 到 59 的數字來表示分鐘。 分鐘表示自上個整點以來已經過的完整分鐘數。 單一位數的分鐘會格式化為具有前置零的數字。

 下列範例會在自訂格式字串中加入 "mm" 自訂格式規範。

 [!code-csharp[Formatting.DateAndTime.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
 [!code-vb[Formatting.DateAndTime.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

 [回到表格](#table)

<a name="M_Specifier"></a> 

## <a name="the-m-custom-format-specifier"></a>"M" 自訂格式規範
 "M" 自訂格式規範以 1 到 12 的數字來表示月份 (如果是有 13 個月的行事曆則從 1 到 13)。 單一位數的月份會格式化為沒有前置零的數字。

 如果單獨使用 "M" 格式規範，而沒有其他自訂格式規範，則會將它解譯為 "M" 標準日期和時間格式規範。 如需使用單一格式規範的詳細資訊，請參閱本主題稍後的[使用單一自訂格式規範](#UsingSingleSpecifiers)。

 下列範例會在自訂格式字串中加入 "M" 自訂格式規範。

 [!code-csharp[Formatting.DateAndTime.Custom#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#11)]
 [!code-vb[Formatting.DateAndTime.Custom#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#11)]

 [回到表格](#table)

<a name="MM_Specifier"></a> 

## <a name="the-mm-custom-format-specifier"></a>"MM" 自訂格式規範
 "MM" 自訂格式規範以 01 到 12 的數字來表示月份 (如果是有 13 個月的行事曆則從 1 到 13)。 單一位數的月份會格式化為有前置零的數字。

 下列範例會在自訂格式字串中加入 "MM" 自訂格式規範。

 [!code-csharp[Formatting.DateAndTime.Custom#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#2)]
 [!code-vb[Formatting.DateAndTime.Custom#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#2)]

 [回到表格](#table)

<a name="MMM_Specifier"></a> 

## <a name="the-mmm-custom-format-specifier"></a>"MMM" 自訂格式規範
 "MMM" 自訂格式規範表示月份的縮寫名稱。 月份的當地語系化縮寫名稱是擷取自目前或指定之文化特性的 <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames%2A?displayProperty=nameWithType> 屬性。

 下列範例會在自訂格式字串中加入 "MMM" 自訂格式規範。

 [!code-csharp[Formatting.DateAndTime.Custom#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#3)]
 [!code-vb[Formatting.DateAndTime.Custom#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#3)]

 [回到表格](#table)

<a name="MMMM_Specifier"></a> 

## <a name="the-mmmm-custom-format-specifier"></a>"MMMM" 自訂格式規範
 "MMMM" 自訂格式規範表示月份的完整名稱。 月份的當地語系化名稱是擷取自目前或指定之文化特性的 <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType> 屬性。

 下列範例會在自訂格式字串中加入 "MMMM" 自訂格式規範。

 [!code-csharp[Formatting.DateAndTime.Custom#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#4)]
 [!code-vb[Formatting.DateAndTime.Custom#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#4)]

 [回到表格](#table)

<a name="sSpecifier"></a> 

## <a name="the-s-custom-format-specifier"></a>"s" 自訂格式規範
 "s" 自訂格式規範以 0 到 59 的數字來表示秒數。 結果表示自上個分鐘以來已經過的完整秒數。 單一位數的秒數會格式化為沒有前置零的數字。

 如果單獨使用 "s" 格式規範，而沒有其他自訂格式規範，則會將它解譯為 "s" 標準日期和時間格式規範。 如需使用單一格式規範的詳細資訊，請參閱本主題稍後的[使用單一自訂格式規範](#UsingSingleSpecifiers)。

 下列範例會在自訂格式字串中加入 "s" 自訂格式規範。

 [!code-csharp[Formatting.DateAndTime.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
 [!code-vb[Formatting.DateAndTime.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

 [回到表格](#table)

<a name="ssSpecifier"></a> 

## <a name="the-ss-custom-format-specifier"></a>"ss" 自訂格式規範
 "ss" 自訂格式規範 (加上任意個額外的 "s" 規範) 以 00 到 59 的數字來表示秒數。 結果表示自上個分鐘以來已經過的完整秒數。 單一位數的秒數會格式化為具有前置零的數字。

 下列範例會在自訂格式字串中加入 "ss" 自訂格式規範。

 [!code-csharp[Formatting.DateAndTime.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
 [!code-vb[Formatting.DateAndTime.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

 [回到表格](#table)

<a name="tSpecifier"></a> 

## <a name="the-t-custom-format-specifier"></a>"t" 自訂格式規範
 "t" 自訂格式規範表示 AM/PM 指示項的第一個字元。 適當的當地語系化指示項是擷取自目前或特定文化特性的 <xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A?displayProperty=nameWithType> 或 <xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A?displayProperty=nameWithType> 屬性。 AM 指示項用於從 0:00:00 (午夜) 到 11:59:59.999 為止的所有時間。 PM 指示項用於從 12:00:00 (中午) 到 23:59:59.999 為止的所有時間。

 如果單獨使用 "t" 格式規範，而沒有其他自訂格式規範，則會將它解譯為 "t" 標準日期和時間格式規範。 如需使用單一格式規範的詳細資訊，請參閱本主題稍後的[使用單一自訂格式規範](#UsingSingleSpecifiers)。

 下列範例會在自訂格式字串中加入 "t" 自訂格式規範。

 [!code-csharp[Formatting.DateAndTime.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#7)]
 [!code-vb[Formatting.DateAndTime.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#7)]

 [回到表格](#table)

<a name="ttSpecifier"></a> 

## <a name="the-tt-custom-format-specifier"></a>"tt" 自訂格式規範
 "tt" 自訂格式規範 (加上任意個額外的 "t" 規範) 表示整個 AM/PM 指示項。 適當的當地語系化指示項是擷取自目前或特定文化特性的 <xref:System.Globalization.DateTimeFormatInfo.AMDesignator%2A?displayProperty=nameWithType> 或 <xref:System.Globalization.DateTimeFormatInfo.PMDesignator%2A?displayProperty=nameWithType> 屬性。 AM 指示項用於從 0:00:00 (午夜) 到 11:59:59.999 為止的所有時間。 PM 指示項用於從 12:00:00 (中午) 到 23:59:59.999 為止的所有時間。

 對於需要特別強調 AM 與 PM 的語言，請務必使用 "tt" 規範。 其中一種就是日文，日文的 AM 和 PM 指示項的第二個字元 (非第一個字元) 不同。

 下列範例會在自訂格式字串中加入 "tt" 自訂格式規範。

 [!code-csharp[Formatting.DateAndTime.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#8)]
 [!code-vb[Formatting.DateAndTime.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#8)]

 [回到表格](#table)

<a name="ySpecifier"></a> 

## <a name="the-y-custom-format-specifier"></a>"y" 自訂格式規範
 "y" 自訂格式規範以一位或兩位數來表示年份。 如果年份超過兩個位數，結果中只會出現兩個低位數字。 如果兩位數年份的第一個數字以零開始 (例如 2008)，則會格式化為沒有前置零的數字。

 如果單獨使用 "y" 格式規範，而沒有其他自訂格式規範，則會將它解譯為 "y" 標準日期和時間格式規範。 如需使用單一格式規範的詳細資訊，請參閱本主題稍後的[使用單一自訂格式規範](#UsingSingleSpecifiers)。

 下列範例會在自訂格式字串中加入 "y" 自訂格式規範。

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Custom#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

 [回到表格](#table)

<a name="yySpecifier"></a> 

## <a name="the-yy-custom-format-specifier"></a>"yy" 自訂格式規範
 "yy" 自訂格式規範以兩位數來表示年份。 如果年份超過兩個位數，結果中只會出現兩個低位數字。 如果兩位數年份少於兩個有效位數，則會以前置零填補此數字來產生兩位數。

 在剖析作業中，使用 "yy" 自訂格式規範所剖析的兩位數年份，是根據格式提供者現行曆法的 <xref:System.Globalization.Calendar.TwoDigitYearMax%2A?displayProperty=nameWithType> 屬性進行解譯。 下列範例會使用 en-US 文化特性的預設西曆 (在此案例中為目前的文化特性)，剖析具有兩位數年份之日期的字串表示。 接著它會將目前文化特性的 <xref:System.Globalization.CultureInfo> 物件變更為使用已修改 <xref:System.Globalization.GregorianCalendar> 屬性的 <xref:System.Globalization.GregorianCalendar.TwoDigitYearMax%2A> 物件。

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#19](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/parseexact2digityear1.cs#19)]
 [!code-vb[Formatting.DateAndTime.Custom#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/parseexact2digityear1.vb#19)]

 下列範例會在自訂格式字串中加入 "yy" 自訂格式規範。

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Custom#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

 [回到表格](#table)

<a name="yyySpecifier"></a> 

## <a name="the-yyy-custom-format-specifier"></a>"yyy" 自訂格式規範
 "yyy" 自訂格式規範以最少三位數來表示年份。 如果年份超過三個有效位數，它們會包含在結果字串中。 如果年份少於三個位數，則會以前置零填補此數字來產生三位數。

> [!NOTE]
>  對於可具有五位數年份的泰國佛教曆法，此格式規範會顯示全部有效位數。

 下列範例會在自訂格式字串中加入 "yyy" 自訂格式規範。

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Custom#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

 [回到表格](#table)

<a name="yyyySpecifier"></a> 

## <a name="the-yyyy-custom-format-specifier"></a>"yyyy" 自訂格式規範
 "yyyy" 自訂格式規範以最少四位數來表示年份。 如果年份超過四個有效位數，它們會包含在結果字串中。 如果年份少於四個位數，則會以前置零填補此數字，以產生四個位數。

> [!NOTE]
>  對於可具有五位數年份的泰國佛教曆法，此格式規範會顯示最少四個位數。

 下列範例會在自訂格式字串中加入 "yyyy" 自訂格式規範。

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Custom#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

 [回到表格](#table)

<a name="yyyyySpecifier"></a> 

## <a name="the-yyyyy-custom-format-specifier"></a>"yyyyy" 自訂格式規範
 "yyyyy" 自訂格式規範 (加上任意個額外的 "y" 規範) 以最少五位數來表示年份。 如果年份超過五個有效位數，它們會包含在結果字串中。 如果年份少於五位數，則會以前置零填補此數字來產生五位數。

 如果有更多 "y" 規範，則會視需要以前置零填補此數字，以產生該 "y" 規範數目的位數。

 下列範例會在自訂格式字串中加入 "yyyyy" 自訂格式規範。

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#13)]
 [!code-vb[Formatting.DateAndTime.Custom#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#13)]

 [回到表格](#table)

<a name="zSpecifier"></a> 

## <a name="the-z-custom-format-specifier"></a>"z" 自訂格式規範
 搭配 <xref:System.DateTime> 值使用時，"z" 自訂格式規範表示本地作業系統時區與國際標準時間 (UTC) 之間的時差 (帶正負號)，以小時為單位。 它不會反映執行個體的 <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> 屬性值。 因此，不建議將 "z" 格式規範搭配 <xref:System.DateTime> 值使用。

 搭配 <xref:System.DateTimeOffset> 值使用時，此格式規範表示 <xref:System.DateTimeOffset> 值與 UTC 之間的時差，以小時為單位。

 顯示時差時，一定會有前置正負號。 加號 (+) 表示早於 UTC 的時數，減號 (-) 表示晚於 UTC 的時數。 單一位數的時差會格式化為沒有前置零的數字。

 如果單獨使用 "z" 格式規範，而沒有其他自訂格式規範，則會將它解譯為標準日期和時間格式規範，並擲回 <xref:System.FormatException>。 如需使用單一格式規範的詳細資訊，請參閱本主題稍後的[使用單一自訂格式規範](#UsingSingleSpecifiers)。

 下列範例會在自訂格式字串中加入 "z" 自訂格式規範。

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
 [!code-vb[Formatting.DateAndTime.Custom#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

 [回到表格](#table)

<a name="zzSpecifier"></a> 

## <a name="the-zz-custom-format-specifier"></a>"zz" 自訂格式規範
 搭配 <xref:System.DateTime> 值使用時，"zz" 自訂格式規範表示本地作業系統時區與 UTC 之間的時差 (帶正負號)，以小時為單位。 它不會反映執行個體的 <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> 屬性值。 因此，不建議將 "zz" 格式規範搭配 <xref:System.DateTime> 值使用。

 搭配 <xref:System.DateTimeOffset> 值使用時，此格式規範表示 <xref:System.DateTimeOffset> 值與 UTC 之間的時差，以小時為單位。

 顯示時差時，一定會有前置正負號。 加號 (+) 表示早於 UTC 的時數，減號 (-) 表示晚於 UTC 的時數。 單一位數的時差會格式化為有前置零的數字。

 下列範例會在自訂格式字串中加入 "zz" 自訂格式規範。

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
 [!code-vb[Formatting.DateAndTime.Custom#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

 [回到表格](#table)

<a name="zzzSpecifier"></a> 

## <a name="the-zzz-custom-format-specifier"></a>"zzz" 自訂格式規範
 搭配 <xref:System.DateTime> 值使用時，"zzz" 自訂格式規範表示本地作業系統時區與 UTC 之間的時差 (帶正負號)，以小時和分鐘為單位。 它不會反映執行個體的 <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> 屬性值。 因此，不建議將 "zzz" 格式規範搭配 <xref:System.DateTime> 值使用。

 搭配 <xref:System.DateTimeOffset> 值使用時，此格式規範表示 <xref:System.DateTimeOffset> 值與 UTC 之間的時差，以小時和分鐘為單位。

 顯示時差時，一定會有前置正負號。 加號 (+) 表示早於 UTC 的時數，減號 (-) 表示晚於 UTC 的時數。 單一位數的時差會格式化為有前置零的數字。

 下列範例會在自訂格式字串中加入 "zzz" 自訂格式規範。

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/Custom1.cs#14)]
 [!code-vb[Formatting.DateAndTime.Custom#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/Custom1.vb#14)]

 [回到表格](#table)

<a name="timeSeparator"></a> 

## <a name="the--custom-format-specifier"></a>":" 自訂格式規範
 ":" 自訂格式規範表示時間分隔符號，用於區別時、分、秒。 適當的當地語系化時間分隔符號是擷取自目前或指定之文化特性的 <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A?displayProperty=nameWithType> 屬性。

> [!NOTE]
>  若要變更特定日期和時間字串的時間分隔符號，請在常值字串分隔符號內指定分隔字元。 例如，自訂格式字串 `hh'_'dd'_'ss` 產生的結果字串中，一律使用 "\_" (底線) 作為時間分隔符號。 若要變更文化特性所有日期的時間分隔符號，請變更目前文化特性的 <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A?displayProperty=nameWithType> 屬性值，或是具現化 <xref:System.Globalization.DateTimeFormatInfo> 物件、將字元指派給它的 <xref:System.Globalization.DateTimeFormatInfo.TimeSeparator%2A> 屬性，並呼叫包含 <xref:System.IFormatProvider> 參數的格式化方法之多載。

 如果單獨使用 ":" 格式規範，而沒有其他自訂格式規範，則會將它解譯為標準日期和時間格式規範，並擲回 <xref:System.FormatException>。 如需使用單一格式規範的詳細資訊，請參閱本主題稍後的[使用單一自訂格式規範](#UsingSingleSpecifiers)。

 [回到表格](#table)

<a name="dateSeparator"></a> 

## <a name="the--custom-format-specifier"></a>"/" 自訂格式規範
 "/" 自訂格式規範表示日期分隔符號，用於區別年、月、日。 適當的當地語系化日期分隔符號是擷取自目前或指定之文化特性的 <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A?displayProperty=nameWithType> 屬性。

> [!NOTE]
>  若要變更特定日期和時間字串的日期分隔符號，請在常值字串分隔符號內指定分隔字元。 例如，自訂格式字串 `mm'/'dd'/'yyyy` 產生的結果字串中，一律使用 "/" 作為日期分隔符號。 若要變更文化特性的所有日期之日期分隔符號，請變更目前文化特性的 <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A?displayProperty=nameWithType> 屬性值，或是具現化 <xref:System.Globalization.DateTimeFormatInfo> 物件、將字元指派給它的 <xref:System.Globalization.DateTimeFormatInfo.DateSeparator%2A> 屬性，並呼叫包含 <xref:System.IFormatProvider> 參數的格式化方法之多載。

 如果單獨使用 "/" 格式規範，而沒有其他自訂格式規範，則會將它解譯為標準日期和時間格式規範，並擲回 <xref:System.FormatException>。 如需使用單一格式規範的詳細資訊，請參閱本主題稍後的[使用單一自訂格式規範](#UsingSingleSpecifiers)。

 [回到表格](#table)

<a name="Literals"></a> 

## <a name="character-literals"></a>字元常值
 自訂日期和時間格式字串中的下列字元是保留字元，一律會解譯為格式字元；若是 "、'、/ 和 \\，則解譯為特殊字元。

||||||
|-|-|-|-|-|
|F|H|K|M|d|
|f|G|h|m|秒|
|t|y|z|%|:|
|/|"|'|\||

 所有其他字元一律會解譯為字元常值，並在格式化作業中，原封不動地包含在結果字串中。  在剖析作業中，它們必須完全符合輸入字串中的字元；這項比較會區分大小寫。

 下列範例包含常值字元 "PST" (太平洋標準時間) 和 "PDT" (太平洋日光節約時間)，以表示格式字串中的當地時區。 請注意，此字串會包含在結果字串中，而且包含當地時區字串的字串也會成功剖析。

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#20](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx1.cs#20)]
 [!code-vb[Formatting.DateAndTime.Custom#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx1.vb#20)]

 您可以使用兩種方式來指定將字元解譯為常值字元，而不是保留字元，以便包含在結果字串中，或在輸入字串中成功剖析：

- 將每個保留字元逸出。 如需詳細資訊，請參閱[使用逸出字元](#escape)。
  
  下列範例包含常值字元 "pst" (太平洋標準時間)，以表示格式字串中的當地時區。 由於 "s" 與 "t" 是自訂格式字串，因此必須逸出這兩個字元才能解譯為字元常值。
  
  [!code-csharp-interactive[Formatting.DateAndTime.Custom#21](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx2.cs#21)]
  [!code-vb[Formatting.DateAndTime.Custom#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx2.vb#21)]

- 以雙引號或單引號括住整個常值字串。 下列範例類似上一個範例，不同之處在於 "pst" 會以雙引號括住，以表示整個分隔的字串都應該解譯為字元常值。
  
  [!code-csharp-interactive[Formatting.DateAndTime.Custom#22](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/LiteralsEx3.cs#22)]
  [!code-vb[Formatting.DateAndTime.Custom#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/LiteralsEx3.vb#22)]

<a name="Notes"></a> 

## <a name="notes"></a>注意

<a name="UsingSingleSpecifiers"></a> 

### <a name="using-single-custom-format-specifiers"></a>使用單一自訂格式規範
 自訂日期和時間格式字串是由兩個或多個字元所組成。 日期和時間格式化方法會將任何單一字元字串解譯為標準日期和時間格式字串。 如果這些方法無法將該字元辨認為有效的格式規範，則會擲回 <xref:System.FormatException>。 例如，僅由規範 "h" 所組成的格式字串會解譯為標準日期和時間字串。 不過，在這種特殊情形下會擲回例外狀況，因為並沒有 "h" 標準日期和時間格式規範。

 若要使用任何自訂日期和時間格式規範做為格式字串中的唯一規範 (也就是單獨使用 "d"、"f"、"F"、"g"、"h"、"H"、"K"、"m"、"M"、"s"、"t"、"y"、"z"、":" 或 "/" 自訂格式規範)，請在規範之前或之後加上一個空格，或在單一自訂日期和時間規範之前加上一個百分比 ("%") 格式規範。

 例如，"`%h"` 會解譯為自訂日期和時間格式字串，該字串會顯示由目前日期和時間值所表示的小時。 您也可以使用 " h" 或 "h " 格式字串，然而這會在結果字串中的小時旁邊加上空格。 下列範例示範這三個格式字串。

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#16](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/literal1.cs#16)]
 [!code-vb[Formatting.DateAndTime.Custom#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/literal1.vb#16)]

<a name="escape"></a> 

### <a name="using-the-escape-character"></a>使用逸出字元
 格式字串中的 "d"、"f"、"F"、"g"、"h"、"H"、"K"、"m"、"M"、"s"、"t"、"y"、"z"、":" 或 "/" 字元會解譯為自訂格式規範，而不是常值字元。 若要避免將字元解譯為格式規範，您可以在前面加上反斜線 (\\)，這是逸出字元。 逸出字元表示接下來的字元是字元常值，應該原封不動地放入結果字串中。

 若要在結果字串中加上反斜線，您必須再加上一個反斜線 (變成`\\`)，才能將反斜線解譯為常值。

> [!NOTE]
>  某些編譯器 (例如 C++ 和 C# 編譯器) 也可能會將單一反斜線字元解譯為逸出字元。 為了確保字串在格式化時能夠正確獲得解譯，您可以在 C# 中的字串前面加上逐字字串常值字元 (@ 字元)，或在 C# 和 C++ 中的每個反斜線前面再加上一個反斜線字元。 下列 C# 範例示範這兩種做法。

 下列範例會使用逸出字元，以避免格式化作業將 "h" 和 "m" 字元解譯為格式規範。

 [!code-csharp-interactive[Formatting.DateAndTime.Custom#15](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.DateAndTime.Custom/cs/escape1.cs#15)]
 [!code-vb[Formatting.DateAndTime.Custom#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.DateAndTime.Custom/vb/escape1.vb#15)]

### <a name="control-panel-settings"></a>控制台設定
 [控制台] 中的 [地區及語言選項] 設定會影響格式化作業 (其中包含許多自訂日期和時間格式規範) 所產生的結果字串。 這些設定是用來初始化與目前執行緒文化特性相關的 <xref:System.Globalization.DateTimeFormatInfo> 物件，該物件會提供用來管理格式的值。 使用不同設定的電腦會產生不同的結果字串。

 此外，如果您使用 <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> 建構函式來將新的 <xref:System.Globalization.CultureInfo> 物件具現化，而此物件代表的文化特性與目前系統文化特性相同，則 [控制台] 中的 [地區及語言選項] 項目所建立的任何自訂都會套用至新的 <xref:System.Globalization.CultureInfo> 物件。 您可以使用 <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> 建構函式來建立不反映系統自訂的 <xref:System.Globalization.CultureInfo> 物件。

### <a name="datetimeformatinfo-properties"></a>DateTimeFormatInfo 屬性
 格式會受到目前 <xref:System.Globalization.DateTimeFormatInfo> 物件的影響，而此物件是由目前執行緒文化特性隱含提供或由叫用格式之方法的 <xref:System.IFormatProvider> 參數明確提供。 在 <xref:System.IFormatProvider> 參數中，您應該指定表示文化特性的 <xref:System.Globalization.CultureInfo> 物件，指定或 <xref:System.Globalization.DateTimeFormatInfo> 物件。

 許多自訂日期和時間格式規範所產生的結果字串，也取決於目前 <xref:System.Globalization.DateTimeFormatInfo> 物件的屬性。 您的應用程式可以變更對應的 <xref:System.Globalization.DateTimeFormatInfo> 屬性，藉此改變某些自訂日期和時間格式規範所產生的結果。 例如，"ddd" 格式規範會將 <xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames%2A> 字串陣列中找到的縮寫星期幾名稱加入至結果字串。 同樣地，"MMMM" 格式規範會將 <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A> 字串陣列中找到的完整月份名稱加到結果字串。

## <a name="see-also"></a>另請參閱

- <xref:System.DateTime?displayProperty=nameWithType>
- <xref:System.IFormatProvider?displayProperty=nameWithType>
- [格式化類型](../../../docs/standard/base-types/formatting-types.md)
- [標準日期和時間格式字串](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [範例：.NET Framework 4 格式化公用程式](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
