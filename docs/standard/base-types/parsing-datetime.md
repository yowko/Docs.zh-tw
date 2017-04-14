---
title: "在 .NET Framework 中剖析日期和時間字串 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "基底類型, 剖析字串"
  - "日期和時間字串"
  - "DateTime 物件"
  - "列舉類型 [.NET Framework], 剖析字串"
  - "ParseExact 方法"
  - "剖析字串, 日期和時間字串"
  - "時間字串"
ms.assetid: 43bae51e-9b1d-41a6-a187-772c0d096d90
caps.latest.revision: 24
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 24
---
# 在 .NET Framework 中剖析日期和時間字串
剖析方法會將代表日期和時間的字串轉換為相等的 <xref:System.DateTime> 物件。  <xref:System.DateTime.Parse%2A> 和 <xref:System.DateTime.TryParse%2A> 方法會轉換日期和時間的幾個常見表示法。  <xref:System.DateTime.ParseExact%2A> 和 <xref:System.DateTime.TryParseExact%2A> 方法會轉換符合日期與時間格式字串所指定模式的字串表示 \(請參閱[標準日期和時間格式字串](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)和[自訂日期和時間格式字串](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)主題\)。  
  
 剖析會受到格式提供者之屬性的影響 \(格式提供者會提供類似用於日期和時間分隔符號的字串以及月份、日期和年代名稱等資訊\)。  格式提供者是目前的 <xref:System.Globalization.DateTimeFormatInfo> 物件，該物件是由目前執行緒的文化特性以隱含方式提供，或是由剖析方法的 <xref:System.IFormatProvider> 參數明確提供。  請針對 <xref:System.IFormatProvider> 參數指定 <xref:System.Globalization.CultureInfo> 物件，該物件表示文化特性或 <xref:System.Globalization.DateTimeFormatInfo> 物件。  
  
 將進行剖析之日期的字串表示必須包含月份，而且至少要包含日期或年份。  時間的字串表示必須包含小時，而且至少要包含分鐘或 AM\/PM 指示項。  不過，剖析可為省略的元件提供預設值 \(可能的話\)。  遺漏的日期預設為目前的日期、遺漏的年份預設為目前的年份、遺漏的月份日期預設為該月份的第一天，而遺漏的時間則預設為午夜時間。  
  
 如果字串表示只有指定時間，則剖析作業會傳回 <xref:System.DateTime> 物件，而且該物件的 <xref:System.DateTime.Year%2A>、<xref:System.DateTime.Month%2A> 和 <xref:System.DateTime.Day%2A> 屬性會設定為 <xref:System.DateTime.Today%2A> 屬性的對應值。  不過，如果 <xref:System.Globalization.DateTimeStyles> 常數是在剖析方法內指定，則產生的年份、月份和日期屬性會設定為 `1` 的值。  
  
 除了日期與時間元件外，日期與時間的字串表示包含一個位移，指示和 Coordinated Universal Time \(UTC\) 的時差有多久。  例如，字串 "2\/14\/2007 5:32:00 \-7:00" 所定義的時間，比 UTC 早七個小時。  如時間的字串表示中省略了位移，剖析會傳回一個 <xref:System.DateTime> 物件，且物件的 <xref:System.DateTime.Kind%2A> 屬性會設定為 <xref:System.DateTimeKind?displayProperty=fullName>。  如果指定了位移，則剖析會傳回 <xref:System.DateTime> 物件，<xref:System.DateTime.Kind%2A> 屬性則是設定為 <xref:System.DateTimeKind>，而且值會調整成您的電腦的當地時區。  您可以使用具有剖析方法的 <xref:System.Globalization.DateTimeStyles> 常數來修改這項行為。  
  
 格式提供者也可用於解譯模稜兩可的數值日期，  例如，由字串 "02\/03\/04" 表示的日期元件很難區分哪一個是月份、日期和年份。  在此情況下，會根據格式提供者內類似日期格式的順序來解譯元件。  
  
## Parse  
 下列程式碼範例說明如何使用 **Parse** 方法，將字串轉換成 **DateTime**。  這個範例會使用和目前執行緒關聯的文化特性來執行剖析。  如果和目前文化特性關聯的 <xref:System.Globalization.CultureInfo> 無法剖析輸入字串，便會擲回 <xref:System.FormatException>。  
  
 [!code-csharp[Parsing.DateAndTime#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example.cs#1)]
 [!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example.vb#1)]  
  
 您也可以指定 **CultureInfo** 並設定為該物件所定義的其中一個文化特性，或者，您可以指定 <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=fullName> 屬性所傳回的其中一個標準 <xref:System.Globalization.DateTimeFormatInfo> 物件。  下列程式碼範例會使用格式提供者，將德文字串剖析為 **DateTime**。  它會定義代表 de\-DE 文化特性的 **CultureInfo** 物件並傳遞正在剖析的字串，確保能成功剖析這個特定的字串。  這將會排除 **CurrentThread** 中 **CurrentCulture** 的任何設定。  
  
 [!code-csharp[Parsing.DateAndTime#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example2.cs#2)]
 [!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example2.vb#2)]  
  
 但是，雖然您可以使用 <xref:System.DateTime.Parse%2A> 方法的多載以指定自訂格式提供者，這個方法並不支援使用非標準的格式提供者。  如果要剖析以非標準格式表示的日期與時間，請使用 <xref:System.DateTime.ParseExact%2A> 方法。  
  
 下列程式碼範例會使用 <xref:System.Globalization.DateTimeStyles> 列舉型別，指定不應該將目前的日期和時間資訊，新增至字串未定義的欄位之 **DateTime**。  
  
 [!code-csharp[Parsing.DateAndTime#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example3.cs#3)]
 [!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example3.vb#3)]  
  
## ParseExact  
 <xref:System.DateTime.ParseExact%2A?displayProperty=fullName> 方法會將符合指定的字串模式之字串，轉換成 **DateTime** 物件。  將非指定格式的字串傳遞至這個方法時，會擲回 <xref:System.FormatException>。  您可以指定其中一個標準的日期和時間格式規範或自訂日期和時間格式規範的有限組合。  如果使用自訂格式規範，您便可以建構自訂辨識字串。  如需規範的說明，請參閱[標準日期和時間格式字串](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)和[自訂日期和時間格式字串](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)主題。  
  
 <xref:System.DateTime.ParseExact%2A> 方法的每一個多載也都有一個 <xref:System.IFormatProvider> 參數，會提供與字串的格式相關的文化特性特定資訊。  通常，這個 <xref:System.IFormatProvider> 物件是一個代表標準文化特性的 <xref:System.Globalization.CultureInfo> 物件，或是由 <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=fullName> 屬性所傳回的 <xref:System.Globalization.DateTimeFormatInfo> 物件。  但是，不同於其他日期與時間剖析函式之處在於，這個方法也支援定義非標準日期與時間格式的 <xref:System.IFormatProvider>。  
  
 在下列程式碼範例中，會將要剖析的字串物件傳遞至 **ParseExact** 方法，接著依序傳遞的是格式規範和 **CultureInfo** 物件。  這個 **ParseExact** 方法只能剖析具有 EN\-US 文化特性中長日期模式的字串。  
  
 [!code-csharp[Parsing.DateAndTime#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example4.cs#4)]
 [!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example4.vb#4)]  
  
## 請參閱  
 [剖析字串](../../../docs/standard/base-types/parsing-strings.md)   
 [格式化類型](../../../docs/standard/base-types/formatting-types.md)   
 [.NET Framework 中的類型轉換](../../../docs/standard/base-types/type-conversion.md)