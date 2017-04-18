---
title: "如何：從特定日期擷取一星期的哪一日 | Microsoft Docs"
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
  - "格式化 [.NET Framework]，日期"
  - "DateTime.DayOfWeek 屬性"
  - "DateTime.ToString 方法"
  - "日期 [.NET Framework], 擷取週資訊"
  - "DateTimeOffset.DayOfWeek 屬性"
  - "日期 [.NET Framework], 週中的日"
  - "Weekday 函式"
  - "週中的日 [.NET Framework]"
  - "擷取週中的日"
  - "星期名稱"
  - "WeekdayName 函式"
  - "數字 [.NET Framework], 週中的日"
  - "格式 [.NET Framework], 時間"
  - "DateTimeOffset.ToString 方法"
  - "完整的星期名稱"
ms.assetid: 1c9bef76-5634-46cf-b91c-9b9eb72091d7
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：從特定日期擷取一星期的哪一日
.NET Framework 可方便判斷特定日期是一週的第幾天，並可顯示特定日期當地語系化的工作日名稱。 您可以從 <xref:System.DateTime.DayOfWeek%2A> 或 <xref:System.DateTimeOffset.DayOfWeek%2A> 屬性取得指出對應於特定日期是星期幾的列舉值。 相對地，擷取工作日名稱是一種格式化作業，可藉由呼叫格式化方法來執行，例如日期和時間值的 `ToString` 方法或 <xref:System.String.Format%2A?displayProperty=fullName> 方法。 本主題示範如何執行下列格式化作業：  
  
### 從特定日期擷取指出星期幾的數字  
  
1.  如果您要處理日期的字串表示法，請使用靜態 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 方法，將其轉換成 <xref:System.DateTime.Parse%2A?displayProperty=fullName> 或 <xref:System.DateTimeOffset.Parse%2A?displayProperty=fullName> 值。  
  
2.  使用 <xref:System.DateTime.DayOfWeek%2A?displayProperty=fullName> 或 <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=fullName> 屬性，以擷取指出星期幾的 <xref:System.DayOfWeek> 值。  
  
3.  若有需要，可將 <xref:System.DayOfWeek> 值轉型 \(在 C\# 中\) 或轉換 \(在 Visual Basic 中\) 成整數。  
  
 下列範例顯示代表特定日期是星期幾的整數。  
  
 [!code-csharp[Formatting.Howto.WeekdayName#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/weekdaynumber7.cs#7)]
 [!code-vb[Formatting.Howto.WeekdayName#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/weekdaynumber7.vb#7)]  
  
### 從特定日期擷取縮寫的工作日名稱。  
  
1.  如果您要處理日期的字串表示法，請使用靜態 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 方法，將其轉換成 <xref:System.DateTime.Parse%2A?displayProperty=fullName> 或 <xref:System.DateTimeOffset.Parse%2A?displayProperty=fullName> 值。  
  
2.  您可以擷取目前文化特性或特定文化特性的工作日名稱縮寫。  
  
    1.  若要擷取目前文化特性的工作日名稱縮寫，請呼叫日期和時間值的 <xref:System.DateTime.ToString%28System.String%29?displayProperty=fullName> 或 <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=fullName> 執行個體方法，並傳遞字串 "ddd" 做為 `format` 參數。 下列範例說明如何呼叫 <xref:System.DateTime.ToString%28System.String%29> 方法。  
  
         [!code-csharp[Formatting.Howto.WeekdayName#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname1.cs#1)]
         [!code-vb[Formatting.Howto.WeekdayName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname1.vb#1)]  
  
    2.  若要擷取特定文化特性的工作日名稱縮寫，請呼叫日期和時間值的 <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=fullName> 或 <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=fullName> 執行個體方法。 傳遞字串 "ddd" 做為 `format` 參數。 傳遞 <xref:System.Globalization.CultureInfo> 或 <xref:System.Globalization.DateTimeFormatInfo> 物件，其代表您想要將其工作日名稱當作 `provider` 參數來擷取的文化特性。 下列程式碼說明如何使用代表 fr\-FR 文化特性的 <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> 物件，來呼叫 <xref:System.Globalization.CultureInfo> 方法。  
  
         [!code-csharp[Formatting.Howto.WeekdayName#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname2.cs#2)]
         [!code-vb[Formatting.Howto.WeekdayName#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname2.vb#2)]  
  
### 從特定日期擷取完整的工作日名稱。  
  
1.  如果您要處理日期的字串表示法，請使用靜態 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 方法，將其轉換成 <xref:System.DateTime.Parse%2A?displayProperty=fullName> 或 <xref:System.DateTimeOffset.Parse%2A?displayProperty=fullName> 值。  
  
2.  您可以擷取目前文化特性或特定文化特性的完整工作日名稱。  
  
    1.  若要擷取目前文化特性的工作日名稱，請呼叫日期和時間值的 <xref:System.DateTime.ToString%28System.String%29?displayProperty=fullName> 或 <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=fullName> 執行個體方法，並傳遞字串 "dddd" 做為 `format` 參數。 下列範例說明如何呼叫 <xref:System.DateTime.ToString%28System.String%29> 方法。  
  
         [!code-csharp[Formatting.Howto.WeekdayName#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname4.cs#4)]
         [!code-vb[Formatting.Howto.WeekdayName#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname4.vb#4)]  
  
    2.  若要擷取特定文化特性的工作日名稱，請呼叫日期和時間值的 <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=fullName> 或 <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=fullName> 執行個體方法。 傳遞字串 "ddd" 做為 `format` 參數。 傳遞 <xref:System.Globalization.CultureInfo> 或 <xref:System.Globalization.DateTimeFormatInfo> 物件，其代表您想要將其工作日名稱當作 `provider` 參數來擷取的文化特性。 下列程式碼說明如何使用代表 es\-ES 文化特性的 <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> 物件，來呼叫 <xref:System.Globalization.CultureInfo> 方法。  
  
         [!code-csharp[Formatting.Howto.WeekdayName#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname5.cs#5)]
         [!code-vb[Formatting.Howto.WeekdayName#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname5.vb#5)]  
  
## 範例  
 此範例說明如何呼叫 <xref:System.DateTime.DayOfWeek%2A?displayProperty=fullName> 和 <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=fullName> 屬性以及 <xref:System.DateTime.ToString%2A?displayProperty=fullName> 和 <xref:System.DateTimeOffset.ToString%2A?displayProperty=fullName> 方法，以針對特定日期擷取代表星期幾的數字、縮寫的工作日名稱，以及完整的工作日名稱。  
  
 [!code-csharp[Formatting.Howto.WeekdayName#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/example6.cs#6)]
 [!code-vb[Formatting.Howto.WeekdayName#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example6.vb#6)]  
  
 個別語言可能會提供功能來複製或補充 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 提供的功能。 例如，Visual Basic 就有包含兩個這類函式：  
  
-   `Weekday` 會傳回指出特定日期是星期幾的數字。 它會將一週第一天的序數值視為一，而 <xref:System.DateTime.DayOfWeek%2A?displayProperty=fullName> 屬性會將其視為零。  
  
-   `WeekdayName` 會傳回目前文化特性中對應特定工作日編號的週間日名稱。  
  
 下列範例說明如何使用 Visual Basic `Weekday` 和 `WeekdayName` 函式。  
  
 [!code-vb[Formatting.HowTo.WeekdayName#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example9.vb#9)]  
  
 您也可以使用 <xref:System.DateTime.DayOfWeek%2A?displayProperty=fullName> 屬性傳回的值來擷取特定日期的工作日名稱。 這只需要在該屬性傳回的 <xref:System.Enum.ToString%2A> 值上呼叫 <xref:System.DayOfWeek> 方法。 不過，此技巧並不會產生目前文化特性的當地語系化工作日名稱，如下列範例所說明。  
  
 [!code-csharp[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/Howto1.cs#8)]
 [!code-vb[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/Howto1.vb#8)]  
  
## 請參閱  
 [執行格式化作業](../../../docs/standard/base-types/performing-formatting-operations.md)   
 [標準日期和時間格式字串](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)   
 [自訂日期和時間格式字串](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)