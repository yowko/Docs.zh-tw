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
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1beceb2b2d32c500e73cd7786c480fcd84c3001c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="parsing-date-and-time-strings-in-net"></a>剖析日期和時間字串，在.NET 中
剖析方法會將日期和時間的字串表示轉換為對等<xref:System.DateTime>物件。 <xref:System.DateTime.Parse%2A>和<xref:System.DateTime.TryParse%2A>方法會將數個共通的表示的日期和時間的任何轉換。 <xref:System.DateTime.ParseExact%2A>和<xref:System.DateTime.TryParseExact%2A>方法會將符合的字串表示轉換成日期和時間格式字串所指定的模式。 (請參閱[標準日期和時間格式字串](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)以及[自訂日期和時間格式字串](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)主題。)  
  
 剖析受到格式提供者的屬性影響，格式提供者提供的資訊為日期和時間分隔符號使用的字串，以及月份、日和紀元名稱等等。 格式提供者是目前<xref:System.Globalization.DateTimeFormatInfo>物件，由目前執行緒文化特性或明確地以隱含方式提供<xref:System.IFormatProvider>剖析方法的參數。 如<xref:System.IFormatProvider>參數，指定<xref:System.Globalization.CultureInfo>物件，代表文化特性，或<xref:System.Globalization.DateTimeFormatInfo>物件。  
  
 要剖析的日期表示字串，必須包含月份以及至少天或年。 時間的字串表示必須包含小時，以及至少分鐘或 AM/PM 指示項。 但若有可能，剖析會為省略的元件提供預設值。 遺漏日期預設為目前的日期，遺漏的年份預設為目前的年份，遺漏的某月某日預設為該月第一天，而遺漏的時間預設為午夜。  
  
 如果指定了只有時間的字串表示，剖析傳回<xref:System.DateTime>物件及其<xref:System.DateTime.Year%2A>， <xref:System.DateTime.Month%2A>，和<xref:System.DateTime.Day%2A>屬性設定為對應的值<xref:System.DateTime.Today%2A>屬性。 不過，如果<xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault>剖析方法，產生的年份、 月份，以指定常數，且日期內容設定為值`1`。  
  
 除了日期和時間元件外，日期和時間的字串表示可以包含表示時間與國際標準時間 (UTC) 差的位移。 例如，字串 "2/14/2007 5:32:00 -7:00" 定義的時間比 UTC 早 7 個小時。 如果省略位移從時間的字串表示，剖析傳回<xref:System.DateTime>物件及其<xref:System.DateTime.Kind%2A>屬性設定為<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>。 如果指定的位移，則剖析傳回<xref:System.DateTime>物件及其<xref:System.DateTime.Kind%2A>屬性設定為<xref:System.DateTimeKind.Local>和其值調整為您電腦的當地時區。 您可以使用，以修改此行為<xref:System.Globalization.DateTimeStyles>常數，其剖析的方法。  
  
 格式提供者也可以用來解譯不明確的數值日期。 例如，在字串 "02/03/04" 中，不清楚那個日期元件表示月、日和年。 這種情況下，就會根據格式提供者中的相似日期格式順序來解譯元件。  
  
## <a name="parse"></a>Parse  
 下列程式碼範例說明使用**剖析**方法，將轉換成字串**DateTime**。 本例會使用與目前執行緒相關聯的文化特性執行剖析。 如果<xref:System.Globalization.CultureInfo>目前相關聯的文化特性無法剖析輸入的字串<xref:System.FormatException>就會擲回。  
  
 [!code-csharp[Parsing.DateAndTime#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example.cs#1)]
 [!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example.vb#1)]  
  
 您也可以指定**CultureInfo**設為其中一個物件，該物件所定義的文化特性，或您可以指定其中一個標準<xref:System.Globalization.DateTimeFormatInfo>所傳回的物件<xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>屬性。 下列程式碼範例會剖析成德文字串使用格式提供者**DateTime**。 A **CultureInfo**定義並通過，但以確保成功剖析這個特定字串的剖析的字串表示 DE-DE 文化特性。 如此即無需任何設定是在**CurrentCulture**的**CurrentThread**。  
  
 [!code-csharp[Parsing.DateAndTime#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example2.cs#2)]
 [!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example2.vb#2)]  
  
 不過，雖然您可以使用的多載<xref:System.DateTime.Parse%2A>方法，以指定自訂的格式提供者，此方法不支援非標準格式提供者的使用。 若要剖析的日期和時間以非標準格式表示，使用<xref:System.DateTime.ParseExact%2A>方法改為。  
  
 下列程式碼範例使用<xref:System.Globalization.DateTimeStyles>列舉來指定目前的日期和時間資訊不應該加入至**DateTime**字串未定義的欄位。  
  
 [!code-csharp[Parsing.DateAndTime#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example3.cs#3)]
 [!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example3.vb#3)]  
  
## <a name="parseexact"></a>ParseExact  
 <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>方法會將符合的字串轉換的指定的字串模式**DateTime**物件。 不是指定的格式字串傳遞至這個方法時<xref:System.FormatException>就會擲回。 您可以指定標準日期和時間格式指定名稱的其中之一，或自訂日期和時間格式指定名稱的有限組合。 使用自訂格式指定名稱，您有機會建構自訂的辨識字串。 如需指定名稱的說明，請參閱[標準日期和時間格式字串](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)以及[自訂日期和時間格式字串](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)主題。  
  
 每個多載<xref:System.DateTime.ParseExact%2A>方法也有<xref:System.IFormatProvider>通常提供特定文化特性資訊的格式字串的參數。 一般而言，這<xref:System.IFormatProvider>物件是<xref:System.Globalization.CultureInfo>物件，代表標準的文化特性或<xref:System.Globalization.DateTimeFormatInfo>所傳回的物件<xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>屬性。 不過，不同於其他日期和時間剖析函式，這個方法也支援<xref:System.IFormatProvider>定義非標準的日期和時間格式。  
  
 在下列程式碼範例中， **ParseExact**傳遞給方法的字串物件，來剖析、 後面接著格式規範，後面接著**CultureInfo**物件。 這**ParseExact**方法只可以剖析字串時，才會看到在 EN-US 文化特性的完整日期模式。  
  
 [!code-csharp[Parsing.DateAndTime#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example4.cs#4)]
 [!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example4.vb#4)]  
  
## <a name="see-also"></a>另請參閱  
 [剖析字串](../../../docs/standard/base-types/parsing-strings.md)  
 [格式化類型](../../../docs/standard/base-types/formatting-types.md)  
 [.NET 中的類型轉換](../../../docs/standard/base-types/type-conversion.md)
