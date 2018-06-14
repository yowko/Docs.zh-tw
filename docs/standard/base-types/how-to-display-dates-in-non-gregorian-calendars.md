---
title: 如何：在非西曆中顯示日期
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [.NET Framework], dates
- dates [.NET Framework], formatting
- calendars [.NET Framework], displaying dates
- displaying date and time data
ms.assetid: ed324eff-4aff-4a76-b6c0-04e6c0d8f5a9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3da8a524af872a724ee6cbe206912572d6338624
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574744"
---
# <a name="how-to-display-dates-in-non-gregorian-calendars"></a>如何：在非西曆中顯示日期
<xref:System.DateTime> 和 <xref:System.DateTimeOffset> 類型使用西曆作為其預設月曆。 這表示即使該日期和時間是使用其他月曆所建立，呼叫日期和時間值的 `ToString` 方法仍會使用西曆顯示該日期和時間的字串表示。 以下範例將說明這種情況，其中使用兩種不同方式來建立波斯曆的日期和時間值，但在呼叫 <xref:System.DateTime.ToString%2A> 方法時，仍以西曆顯示這些日期和時間值。 此範例反映兩種常用來顯示特殊月曆之日期，但不正確的技術。  
  
 [!code-csharp[Formatting.HowTo.Calendar#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#1)]
 [!code-vb[Formatting.HowTo.Calendar#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#1)]  
  
 這兩種不同的技術可用來顯示特殊月曆的日期。 第一種技術要求該月曆必須是某個文化特性的預設月曆。 第二種技術可搭配任何月曆使用。  
  
### <a name="to-display-the-date-for-a-cultures-default-calendar"></a>顯示文化特性預設月曆的日期  
  
1.  將衍生自 <xref:System.Globalization.Calendar> 類別的月曆物件具現化，該物件代表要使用的月曆。  
  
2.  將 <xref:System.Globalization.CultureInfo> 物件具現化，該物件代表將使用其格式來顯示日期的文化特性。  
  
3.  呼叫 <xref:System.Array.Exists%2A?displayProperty=nameWithType> 方法，以判斷月曆物件是否為 <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> 屬性所傳回陣列的成員。 這表示該月曆可作為 <xref:System.Globalization.CultureInfo> 物件的預設月曆。 如果不是陣列成員，請依照＜顯示任何月曆中的日期＞一節中的指示進行。  
  
4.  將月曆物件指派給 <xref:System.Globalization.DateTimeFormatInfo> 物件的 <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A> 屬性，該物件是由 <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> 屬性所傳回的。  
  
    > [!NOTE]
    >  <xref:System.Globalization.CultureInfo> 類別也會有 <xref:System.Globalization.CultureInfo.Calendar%2A> 屬性。 不過，該屬性是唯讀且固定的，不會變更以反映指派給 <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> 屬性的新預設月曆。  
  
5.  呼叫 <xref:System.DateTime.ToString%2A> 或 <xref:System.DateTime.ToString%2A> 方法，並將 <xref:System.Globalization.CultureInfo> 物件傳遞給它，該物件的預設月曆已在上一個步驟中加以修改。  
  
### <a name="to-display-the-date-in-any-calendar"></a>顯示任何月曆中的日期  
  
1.  將衍生自 <xref:System.Globalization.Calendar> 類別的月曆物件具現化，該物件代表要使用的月曆。  
  
2.  決定應出現在日期和時間值的字串表示中的日期和時間項目。  
  
3.  針對您要顯示的每一個日期和時間元素，呼叫月曆物件的 `Get` 方法。 下列為可用的方法：  
  
    -   <xref:System.Globalization.Calendar.GetYear%2A>，用來顯示適當月曆中的年份。  
  
    -   <xref:System.Globalization.Calendar.GetMonth%2A>，用來顯示適當月曆中的月份。  
  
    -   <xref:System.Globalization.Calendar.GetDayOfMonth%2A>，用來顯示適當月曆中某個月份的日期數字。  
  
    -   <xref:System.Globalization.Calendar.GetHour%2A>，用來顯示適當月曆中某天的小時。  
  
    -   <xref:System.Globalization.Calendar.GetMinute%2A>，用來顯示適當月曆中某小時的分鐘。  
  
    -   <xref:System.Globalization.Calendar.GetSecond%2A>，用來顯示適當月曆中某分鐘的秒鐘。  
  
    -   <xref:System.Globalization.Calendar.GetMilliseconds%2A>，用來顯示適當月曆中某一秒的毫秒。  
  
## <a name="example"></a>範例  
 這個範例顯示使用兩種不同月曆的日期。 日期會在定義回曆作為 ar-JO 文化特性的預設月曆之後顯示，並且會使用波斯曆顯示日期，而波斯曆並不是 fa-IR 文化特性支援的選用月曆。  
  
 [!code-csharp[Formatting.HowTo.Calendar#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#2)]
 [!code-vb[Formatting.HowTo.Calendar#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#2)]  
  
 每個 <xref:System.Globalization.CultureInfo> 物件均可支援一或多個月曆，並以 <xref:System.Globalization.CultureInfo.OptionalCalendars%2A> 屬性表示。 這其中一個月曆會指定為文化特性的預設月曆，並由唯讀的 <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> 屬性傳回。 另一個選用月曆可藉由將代表該月曆的 <xref:System.Globalization.Calendar> 物件指派給由 <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> 屬性傳回的 <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> 屬性來指定為預設值。 不過，有些月曆 (例如 <xref:System.Globalization.PersianCalendar> 類別所代表的波斯曆) 無法作為任何文化特性的選用月曆。  
  
 這個範例會定義可重複使用的月曆公用程式類別 `CalendarUtility`，用來處理使用特殊月曆產生日期的字串表示時的許多細節。 `CalendarUtility` 類別具有下列成員：  
  
-   參數化的建構函式，其單一參數為用來表示日期的 <xref:System.Globalization.Calendar> 物件。 這個參數會指派給類別的私用欄位。  
  
-   `CalendarExists` 是傳回布林值的私用方法，指出以參數形式傳遞給方法的 <xref:System.Globalization.CultureInfo> 物件是否支援 `CalendarUtility` 物件所代表的月曆。 此方法會包裝對 <xref:System.Array.Exists%2A?displayProperty=nameWithType> 方法的呼叫，並將 <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> 陣列傳遞至其中。  
  
-   `HasSameName` 是指派給 <xref:System.Predicate%601> 委派的私用方法，會以參數形式傳遞給 <xref:System.Array.Exists%2A?displayProperty=nameWithType> 方法。 每一個陣列成員都會傳遞至方法，直到方法傳回 `true` 為止。 這個方法會判斷選用月曆的名稱是否與 `CalendarUtility` 物件代表的月曆相同。  
  
-   `DisplayDate` 是要傳入兩個參數的多載公用方法：要在 `CalendarUtility` 物件所代表之月曆中表示的 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 值，以及要使用之格式化規則所屬的文化特性。 在傳回日期的字串表示時，其行為會根據文化特性是否支援要使用其格式化規則的目標月曆而定。  
  
 不論此範例中用來建立 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 值的月曆為何，該值通常會以西曆日期來表示。 這是因為 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 類型不會保留任何月曆資訊。 這兩個值會在內部表示為自 0001 年 1 月 1 日午夜開始經過的刻度數。 該數字的轉譯會根據月曆而定。 大部分文化特性的預設月曆是西曆。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 此範例需要 System.Core.dll 命名空間的參考。  
  
 在命令列中，使用 csc.exe 或 vbc.exe 來編譯程式碼。 若要在 Visual Studio 中編譯程式碼，請將它放入主控台應用程式專案範本。  
  
## <a name="see-also"></a>請參閱  
 [執行格式化作業](../../../docs/standard/base-types/performing-formatting-operations.md)
