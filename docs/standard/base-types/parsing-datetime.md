---
title: "在 .NET Framework 中剖析日期和時間字串"
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
- parsing strings, date and time strings
- date and time strings
- ParseExact method
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
- DateTime object
- time strings
ms.assetid: 43bae51e-9b1d-41a6-a187-772c0d096d90
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6e3ef01abdb615b2850b5a9d07e1208ee22eda95
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="parsing-date-and-time-strings-in-net"></a>在 .NET 中剖析日期和時間字串
剖析方法會將日期和時間的字串表示轉換為同等的 <xref:System.DateTime> 物件。 <xref:System.DateTime.Parse%2A> 和 <xref:System.DateTime.TryParse%2A> 方法會轉換數種常見的日期和時間表示。 <xref:System.DateTime.ParseExact%2A> 和 <xref:System.DateTime.TryParseExact%2A> 方法會轉換符合日期和時間格式字串所指定模式的字串表示。 (請參閱[標準日期和時間格式字串](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)以及[自訂日期和時間格式字串](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)主題。)  
  
 剖析受到格式提供者的屬性影響，格式提供者提供的資訊為日期和時間分隔符號使用的字串，以及月份、日和紀元名稱等等。 格式提供者是目前的 <xref:System.Globalization.DateTimeFormatInfo> 物件，由目前執行緒文化特性隱含提供或由剖析方法的 <xref:System.IFormatProvider> 參數明確提供。 針對 <xref:System.IFormatProvider> 參數，指定代表文化特性的 <xref:System.Globalization.CultureInfo> 物件，或指定 <xref:System.Globalization.DateTimeFormatInfo> 物件。  
  
 要剖析的日期表示字串，必須包含月份以及至少天或年。 時間的字串表示必須包含小時，以及至少分鐘或 AM/PM 指示項。 但若有可能，剖析會為省略的元件提供預設值。 遺漏日期預設為目前的日期，遺漏的年份預設為目前的年份，遺漏的某月某日預設為該月第一天，而遺漏的時間預設為午夜。  
  
 如果字串表示只指定時間，剖析會傳回 <xref:System.DateTime> 物件及其設為 <xref:System.DateTime.Today%2A> 屬性對應值的 <xref:System.DateTime.Year%2A>、<xref:System.DateTime.Month%2A> 和 <xref:System.DateTime.Day%2A> 屬性。 不過，如果剖析方法中指定了 <xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault> 常數，則產生的 year、month 及 day 屬性值都會設為 `1`。  
  
 除了日期和時間元件外，日期和時間的字串表示可以包含表示時間與國際標準時間 (UTC) 差的位移。 例如，字串 "2/14/2007 5:32:00 -7:00" 定義的時間比 UTC 早 7 個小時。 如果時間的字串表示中省略了位移，剖析就會傳回 <xref:System.DateTime> 物件及其設為 <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> 的 <xref:System.DateTime.Kind%2A> 屬性。 如果指定了位移，剖析就會傳回 <xref:System.DateTime> 物件及其設為 <xref:System.DateTimeKind.Local> 的 <xref:System.DateTime.Kind%2A> 屬性，且其值會調整成您電腦的當地時區。 您可以搭配剖析方法使用 <xref:System.Globalization.DateTimeStyles> 常數來修改此行為。  
  
 格式提供者也可以用來解譯不明確的數值日期。 例如，在字串 "02/03/04" 中，不清楚那個日期元件表示月、日和年。 這種情況下，就會根據格式提供者中的相似日期格式順序來解譯元件。  
  
## <a name="parse"></a>Parse  
 下列程式碼範例示範如何使用 **Parse** 方法，將字串轉換為 **DateTime**。 本例會使用與目前執行緒相關聯的文化特性執行剖析。 如果與目前文化特性相關聯的 <xref:System.Globalization.CultureInfo> 無法剖析輸入字串，則會擲回 <xref:System.FormatException>。  
  
 [!code-csharp[Parsing.DateAndTime#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example.cs#1)]
 [!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example.vb#1)]  
  
 您也可以指定設為該物件所定義文化特性之一的 **CultureInfo**，或者指定 <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> 屬性傳回的標準 <xref:System.Globalization.DateTimeFormatInfo> 物件之一。 下列程式碼範例使用格式提供者，將德文字串剖析為 **DateTime**。 代表 de-DE 文化特性的 **CultureInfo** 會透過剖析的字串來定義及傳遞，以確保成功剖析這個特定的字串。 如此即可排除 **CurrentThread** 的 **CurrentCulture** 中所有設定。  
  
 [!code-csharp[Parsing.DateAndTime#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example2.cs#2)]
 [!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example2.vb#2)]  
  
 不過，雖然您可以使用 <xref:System.DateTime.Parse%2A> 方法的多載來指定自訂的格式提供者，此方法卻不支援使用非標準的格式提供者。 若要剖析以非標準格式表示的日期和時間，請改用 <xref:System.DateTime.ParseExact%2A> 方法。  
  
 下列程式碼範例使用 <xref:System.Globalization.DateTimeStyles> 列舉，來指定不應將目前的日期和時間資訊新增至字串未定義的欄位 **DateTime** 中。  
  
 [!code-csharp[Parsing.DateAndTime#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example3.cs#3)]
 [!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example3.vb#3)]  
  
## <a name="parseexact"></a>ParseExact  
 <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> 方法會將符合指定字串模式的字串轉換為 **DateTime** 物件。 將不是指定格式的字串傳遞至這個方法時，就會擲回 <xref:System.FormatException>。 您可以指定標準日期和時間格式指定名稱的其中之一，或自訂日期和時間格式指定名稱的有限組合。 使用自訂格式指定名稱，您有機會建構自訂的辨識字串。 如需指定名稱的說明，請參閱[標準日期和時間格式字串](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)以及[自訂日期和時間格式字串](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)主題。  
  
 <xref:System.DateTime.ParseExact%2A> 方法的每個多載也都有 <xref:System.IFormatProvider> 參數，通常會提供有關設定字串格式的特定文化特性資訊。 一般而言，這個 <xref:System.IFormatProvider> 物件是代表標準文化特性的 <xref:System.Globalization.CultureInfo> 物件，或 <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> 屬性所傳回的 <xref:System.Globalization.DateTimeFormatInfo> 物件。 不過，不同於其他日期和時間剖析函式，此方法也支援定義非標準日期和時間格式的 <xref:System.IFormatProvider>。  
  
 在下列程式碼範例中，**ParseExact** 方法收到了要剖析的字串物件，後面依序接著格式規範和 **CultureInfo** 物件。 這個 **ParseExact** 方法只能剖析以 en-US 文化特性展現完整日期模式的字串。  
  
 [!code-csharp[Parsing.DateAndTime#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example4.cs#4)]
 [!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example4.vb#4)]  
  
## <a name="see-also"></a>請參閱  
 [Parsing Strings](../../../docs/standard/base-types/parsing-strings.md)  
 [格式化類型](../../../docs/standard/base-types/formatting-types.md)  
 [.NET 中的類型轉換](../../../docs/standard/base-types/type-conversion.md)
