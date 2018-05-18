---
title: 如何：將字串轉換成 DateTime
description: 了解剖析表示日期與時間的字串，以從日期與時間字串建立 DateTime 的技術。
ms.date: 02/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parsing strings, date and time strings
- date and time strings
- ParseExact method
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
- DateTime object
- time strings
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c093f22f77284d15e56c8f1d4a95afbeb75202d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="parsing-date-and-time-strings-in-net"></a>在 .NET 中剖析日期和時間字串

剖析字串以將之轉換成 <xref:System.DateTime> 物件時，會要求您指定如何將日期與時間以文字表示的相關資訊。 不同的文化特性會針對日期、月份與年份使用不同的順序。 某些時間表示法使用 24 小時制，其他則指定 "AM" 和 "PM"。 某些應用程式僅需要日期。 其他則僅需要時間。 而有部份則需要同時指定日期與時間。 將字串轉換為 <xref:System.DateTime> 物件的方法，可讓您提供所預期格式以及應用程式所需日期與時間元素的相關詳細資訊。 將文字正確轉換為 <xref:System.DateTime> 有三項子工作：

1. 您必須指定表示日期與時間的文字預期格式。
1. 您可以指定日期時間格式的文化特性。
1. 您可以指定文字表示法中遺漏的元件在日期與時間中設定的方式。

<xref:System.DateTime.Parse%2A> 和 <xref:System.DateTime.TryParse%2A> 方法會轉換許多常見的日期和時間表示法。 <xref:System.DateTime.ParseExact%2A> 和 <xref:System.DateTime.TryParseExact%2A> 方法會轉換符合日期和時間格式字串所指定模式的字串表示。 (如需詳細資訊，請參閱[標準日期和時間格式字串](standard-date-and-time-format-strings.md)以及[自訂日期和時間格式字串](custom-date-and-time-format-strings.md)相關文章)。


目前的 <xref:System.Globalization.DateTimeFormatInfo> 物件提供了將文字解譯為日期與時間的更多控制方式。 <xref:System.Globalization.DateTimeFormatInfo> 的屬性描述了日期和時間分隔符號，以及月、日和紀元的名稱，還有 "AM" 和 "PM" 指定的格式。 目前的執行緒文化特性提供可表示目前文化特性的 <xref:System.Globalization.DateTimeFormatInfo>。 若需要特定文化特性或自訂設定，您可以指定剖析方法的 <xref:System.IFormatProvider> 參數。 針對 <xref:System.IFormatProvider> 參數，指定代表文化特性的 <xref:System.Globalization.CultureInfo> 物件，或指定 <xref:System.Globalization.DateTimeFormatInfo> 物件。

表示日期或時間的文字可能會遺失一些資訊。 例如，大多數人會假設日期「3 月 12 日」表示目前的年份。 同樣地，「2018 年 3 月」表示 2018 年的 3 月份。 代表時間的文字也經常僅包含小時、分鐘和 AM/PM 指定。  剖析方法會使用合理的預設值，以處理此種遺失資訊：

- 當只有表示時間時，日期部分會使用目前的日期。
- 當只有表示日期時，時間部分則為午夜。
- 當日期中沒有指定年份時，會使用目前的年份。
- 當沒有指定月份日期時，會使用月份的第一天。

如果字串中有日期，則日期必須包含月份，和日期或年份兩者其中之一。 如果有時間，則時間必須包含小時，和分鐘或 AM/PM 指示項兩者其中之一。

您可以指定 <xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault> 常數來覆寫這些預設值。 當您使用該常數時，任何遺失的年份、月份或日期屬性都會設定為值 `1`。 [最後一個範例](#styles-example)會使用 <xref:System.DateTime.Parse%2A> 來示範此行為。

除了日期和時間元件外，日期和時間的字串表示可以包含表示時間與國際標準時間 (UTC) 差的位移。 例如，字串 "2/14/2007 5:32:00 -7:00" 定義的時間比 UTC 早 7 個小時。 如果時間的字串表示中省略了位移，剖析就會傳回 <xref:System.DateTime> 物件及其設為 <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> 的 <xref:System.DateTime.Kind%2A> 屬性。 如果指定了位移，剖析就會傳回 <xref:System.DateTime> 物件及其設為 <xref:System.DateTimeKind.Local?displayProperty=nameWithType> 的 <xref:System.DateTime.Kind%2A> 屬性，且其值會調整成您電腦的當地時區。 您可以搭配剖析方法使用 <xref:System.Globalization.DateTimeStyles> 值來修改此行為。
  
格式提供者也可以用來解譯不明確的數值日期。 "02/03/04" 字串並未明確表示代表月份、日期和年份的日期元件。 元件會根據格式提供者中的相似日期格式順序來解譯。

## <a name="parse"></a>Parse

下面的範例會示範如何使用 <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> 方法將 `string` 轉換成 <xref:System.DateTime>。 本範例會使用與目前執行緒相關聯的文化特性。 如果與目前文化特性相關聯的 <xref:System.Globalization.CultureInfo> 無法剖析輸入字串，則會擲回 <xref:System.FormatException>。

> [!TIP]
> 本文中所有的 C# 範例皆可在您的瀏覽器中執行。 按 [執行] 按鈕以查看輸出。 您也可以編輯它們以進行實驗。

> [!NOTE]
> 這些範例可在 [C#](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/conversions) 和 [VB](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/how-to/conversions) 兩者的 GitHub 文件存放庫中取得。 或者，您可以為 [C#](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/conversions.zip) 或 [VB](https://github.com/dotnet/samples/raw/master/snippets/visualbasic/how-to/conversions.zip)將專案下載為 ZIP 檔案。

[!code-csharp-interactive[Parsing.DateAndTime#1](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#1)]
[!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#1)]

您也可以明確地定義剖析字串時所使用的文化特性格式設定慣例。 您將指定由 <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> 屬性傳回的其中一個標準 <xref:System.Globalization.DateTimeFormatInfo> 物件。 下列範例使用格式提供者將德文字串剖析成 <xref:System.DateTime>。 它會建立代表 `de-DE` 文化特性的 <xref:System.Globalization.CultureInfo>。 `CultureInfo` 物件可確保成功剖析此特定字串。 這可排除 <xref:System.Threading.Thread.CurrentThread> 的 <xref:System.Threading.Thread.CurrentCulture> 有任何設定。  
  
[!code-csharp-interactive[Parsing.DateAndTime#2](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#2)]
[!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#2)]

不過，雖然您可以使用 <xref:System.DateTime.Parse%2A> 方法的多載來指定自訂的格式提供者，此方法卻不支援剖析非標準的格式。 若要剖析以非標準格式表示的日期和時間，請改用 <xref:System.DateTime.ParseExact%2A> 方法。  

<a name="styles-example"></a>下列範例使用 <xref:System.Globalization.DateTimeStyles> 列舉，以指定不應將目前的日期和時間資訊新增至 <xref:System.DateTime> 的未指定欄位中。  

[!code-csharp-interactive[Parsing.DateAndTime#3](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#3)]
[!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#3)]
 
## <a name="parseexact"></a>ParseExact

<xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> 方法會將符合其中一個指定字串模式的字串轉換為 <xref:System.DateTime> 物件。 當不是指定形式之一的字串傳遞至此方法時，就會擲回 <xref:System.FormatException>。 您可以指定標準日期和時間格式指定名稱之一，或指定自訂格式指定名稱的組合。 使用自訂格式指定名稱，您有機會建構自訂的辨識字串。 如需指定名稱的說明，請參閱[標準日期和時間格式字串](standard-date-and-time-format-strings.md)以及[自訂日期和時間格式字串](custom-date-and-time-format-strings.md)主題。  

在下列範例中，<xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> 方法收到了要剖析的字串物件，後面依序接著格式指定名稱和 <xref:System.Globalization.CultureInfo> 物件。 此 <xref:System.DateTime.ParseExact%2A> 方法只能剖析遵循 `en-US` 文化特性中完整日期模式的字串。  

[!code-csharp-interactive[Parsing.DateAndTime#4](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#4)]
[!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#4)]

<xref:System.DateTime.Parse%2A> 和 <xref:System.DateTime.ParseExact%2A> 方法的每個多載也都有 <xref:System.IFormatProvider> 參數，可提供有關設定字串格式的特定文化特性資訊。 此 <xref:System.IFormatProvider> 物件是代表標準文化特性的 <xref:System.Globalization.CultureInfo> 物件，或 <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> 屬性所傳回的 <xref:System.Globalization.DateTimeFormatInfo> 物件。  <xref:System.DateTime.ParseExact%2A> 也會使用可定義一或多個自訂日期和時間格式的額外字串或字串陣列引數。  

## <a name="see-also"></a>請參閱  
 [剖析字串](parsing-strings.md)  
 [格式化類型](formatting-types.md)  
 [.NET 中的類型轉換](type-conversion.md)  
 [標準日期和時間格式](standard-date-and-time-format-strings.md)  
 [自訂日期和時間格式字串](custom-date-and-time-format-strings.md)
