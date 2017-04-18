---
title: "如何：在非西曆中顯示日期 | Microsoft Docs"
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
  - "日期 [.NET Framework]，格式化"
  - "行事曆 [.NET Framework]，顯示日期"
  - "顯示日期和時間資料"
ms.assetid: ed324eff-4aff-4a76-b6c0-04e6c0d8f5a9
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：在非西曆中顯示日期
<xref:System.DateTime> 和 <xref:System.DateTimeOffset> 型別會使用西曆做為預設月曆。  這表示即使該日期和時間是使用其他月曆所建立，呼叫日期和時間值的 `ToString` 方法仍會使用西曆顯示該日期和時間的字串表示。  以下範例中將說明這種情況，其中會使用兩種不同的方式建立波斯曆的日期和時間值，但是在呼叫 <xref:System.DateTime.ToString%2A> 方法時，仍會以西曆顯示這些日期和時間值。  這個範例會反映兩種常用來顯示特殊月曆之日期，但不正確的技術。  
  
 [!code-csharp[Formatting.HowTo.Calendar#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#1)]
 [!code-vb[Formatting.HowTo.Calendar#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#1)]  
  
 兩種不同的技術可用來顯示特殊月曆的日期。  第一種需要將該月曆設為特殊文化特性的預設月曆。  第二種則可以使用任何月曆。  
  
### 顯示文化特性預設月曆的日期  
  
1.  具現化衍生自 <xref:System.Globalization.Calendar> 類別的月曆物件，該物件代表要使用的月曆。  
  
2.  具現化 <xref:System.Globalization.CultureInfo> 物件，該物件代表的文化特性將用來顯示日期。  
  
3.  呼叫 <xref:System.Array.Exists%2A?displayProperty=fullName> 方法，判斷月曆物件是否為 <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=fullName> 屬性所傳回陣列的成員。  這表示該月曆可以做為 <xref:System.Globalization.CultureInfo> 物件的預設月曆。  如果不是陣列成員，請依照＜顯示任何月曆中的日期＞一節中的指示進行。  
  
4.  將月曆物件指派給 <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=fullName> 屬性所傳回 <xref:System.Globalization.DateTimeFormatInfo> 物件的 <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A> 屬性。  
  
    > [!NOTE]
    >  <xref:System.Globalization.CultureInfo> 類別也有 <xref:System.Globalization.CultureInfo.Calendar%2A> 屬性。  不過該屬性是唯讀的常數，不會變更以反映指派給 <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=fullName> 屬性的新預設月曆。  
  
5.  呼叫 <xref:System.DateTime.ToString%2A> 或 <xref:System.DateTime.ToString%2A> 方法，並將上一個步驟中修改其預設月曆的 <xref:System.Globalization.CultureInfo> 物件傳遞給該方法。  
  
### 顯示任何月曆中的日期  
  
1.  具現化衍生自 <xref:System.Globalization.Calendar> 類別的月曆物件，該物件代表要使用的月曆。  
  
2.  決定應出現在日期和時間值的字串表示中的日期和時間項目。  
  
3.  針對您要顯示的每一個日期和時間項目，呼叫月曆物件的 `Get`… 方法。  下列為可用的方法：  
  
    -   <xref:System.Globalization.Calendar.GetYear%2A>，用來顯示適當月曆中的年份。  
  
    -   <xref:System.Globalization.Calendar.GetMonth%2A>，用來顯示適當月曆中的月份。  
  
    -   <xref:System.Globalization.Calendar.GetDayOfMonth%2A>，用來顯示適當月曆中某個月份的日期數字。  
  
    -   <xref:System.Globalization.Calendar.GetHour%2A>，用來顯示適當月曆中某天的小時。  
  
    -   <xref:System.Globalization.Calendar.GetMinute%2A>，用來顯示適當月曆中某小時的分鐘。  
  
    -   <xref:System.Globalization.Calendar.GetSecond%2A>，用來顯示適當月曆中某分鐘的秒鐘。  
  
    -   <xref:System.Globalization.Calendar.GetMilliseconds%2A>，用來顯示適當月曆中某一秒的毫秒。  
  
## 範例  
 這個範例顯示使用兩種不同月曆的日期。  日期會在定義回曆做為 ar\-JO 文化特性的預設月曆之後顯示，並且會使用波斯曆顯示日期，而波斯曆並不是 fa\-IR 文化特性支援的選用月曆。  
  
 [!code-csharp[Formatting.HowTo.Calendar#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#2)]
 [!code-vb[Formatting.HowTo.Calendar#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#2)]  
  
 每個 <xref:System.Globalization.CultureInfo> 物件都可以支援一個或多個月曆，由 <xref:System.Globalization.CultureInfo.OptionalCalendars%2A> 屬性表示。  其中一個月曆會指定為文化特性的預設月曆，並且由唯讀 <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=fullName> 屬性傳回。  另一個選用的月曆可以藉由指派代表該月曆的 <xref:System.Globalization.Calendar> 物件給 <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=fullName> 屬性 \(由 <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=fullName> 屬性傳回\) 指定為預設值。  不過，有些月曆 \(例如 <xref:System.Globalization.PersianCalendar> 類別所代表的波斯曆\) 無法做為任何文化特性的選用月曆。  
  
 這個範例會定義可重複使用的月曆公用程式類別 `CalendarUtility`，用來處理使用特殊月曆產生日期的字串表示時的許多細節。  `CalendarUtility` 類別擁有下列成員：  
  
-   參數化的建構函式，其單一參數為用來表示日期的 <xref:System.Globalization.Calendar> 物件。  這個參數會指派給類別的私用欄位。  
  
-   `CalendarExists`，傳回布林值的私用方法，表示傳遞至方法做為參數的 <xref:System.Globalization.CultureInfo> 物件是否支援 `CalendarUtility` 物件代表的月曆。  這個方法會包裝 <xref:System.Array.Exists%2A?displayProperty=fullName> 方法的呼叫，並且傳遞 <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=fullName> 陣列給該方法。  
  
-   `HasSameName`，指派給 <xref:System.Predicate%601> 委派的私用方法，其會做為參數傳遞至 <xref:System.Array.Exists%2A?displayProperty=fullName> 方法。  每一個陣列成員都會傳遞至方法，直到方法傳回 `true` 為止。  這個方法會判斷選用月曆的名稱是否與 `CalendarUtility` 物件代表的月曆相同。  
  
-   `DisplayDate`，多載的公用方法，以下兩個參數會傳遞給這個方法：<xref:System.DateTime> 或是 <xref:System.DateTimeOffset> 值，用來在 `CalendarUtility` 物件代表的月曆中表達，以及要使用其格式化規則的文化特性。  在傳回日期的字串表示時，其行為會根據文化特性是否支援要使用其格式化規則的目標月曆而定。  
  
 無論月曆在本範例中用來建立 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 值，該值通常都會以西曆日期表達。  這是因為 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 型別不會保留任何月曆資訊。  這兩個值會在內部表示為自 0001 年 1 月 1 日開始經過的刻度數。  該數字的轉譯會根據月曆而定。  大部分文化特性的預設月曆是西曆。  
  
## 編譯程式碼  
 這個範例需要參考 System.Core.dll。  
  
 使用 csc.exe 或 vb.exe 在命令列編輯程式碼。  若要編譯 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中的程式碼，請將程式碼放在主控台應用程式專案範本中。  
  
## 請參閱  
 [執行格式化作業](../../../docs/standard/base-types/performing-formatting-operations.md)