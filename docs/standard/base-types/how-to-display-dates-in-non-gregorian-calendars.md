---
title: "如何：在非西曆中顯示日期"
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
- dates [.NET Framework], formatting
- calendars [.NET Framework], displaying dates
- displaying date and time data
ms.assetid: ed324eff-4aff-4a76-b6c0-04e6c0d8f5a9
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a79860091e549dcf4eaa7090947f9506eceb6119
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-display-dates-in-non-gregorian-calendars"></a>如何：在非西曆中顯示日期
<xref:System.DateTime>和<xref:System.DateTimeOffset>類型做為其預設行事曆使用西曆。 這表示即使該日期和時間是使用其他月曆所建立，呼叫日期和時間值的 `ToString` 方法仍會使用西曆顯示該日期和時間的字串表示。 以下是在下列範例中，這會使用兩種不同的方式來建立與波斯曆中的日期和時間值，但仍會顯示這些日期和時間值在西曆中呼叫時，如果<xref:System.DateTime.ToString%2A>方法。 此範例反映兩種常用來顯示特殊月曆之日期，但不正確的技術。  
  
 [!code-csharp[Formatting.HowTo.Calendar#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#1)]
 [!code-vb[Formatting.HowTo.Calendar#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#1)]  
  
 這兩種不同的技術可用來顯示特殊月曆的日期。 第一種技術要求該月曆必須是某個文化特性的預設月曆。 第二種技術可搭配任何月曆使用。  
  
### <a name="to-display-the-date-for-a-cultures-default-calendar"></a>顯示文化特性預設月曆的日期  
  
1.  具現化衍生自行事曆物件<xref:System.Globalization.Calendar>類別，表示要使用的行事曆。  
  
2.  具現化<xref:System.Globalization.CultureInfo>表示會用來顯示日期的格式化之文化特性的物件。  
  
3.  呼叫<xref:System.Array.Exists%2A?displayProperty=nameWithType>方法，以判斷行事曆物件是否為所傳回的陣列成員<xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType>屬性。 這表示行事曆可做為預設行事曆<xref:System.Globalization.CultureInfo>物件。 如果不是陣列成員，請依照＜顯示任何月曆中的日期＞一節中的指示進行。  
  
4.  若要將行事曆物件指派<xref:System.Globalization.DateTimeFormatInfo.Calendar%2A>屬性<xref:System.Globalization.DateTimeFormatInfo>所傳回物件<xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>屬性。  
  
    > [!NOTE]
    >  <xref:System.Globalization.CultureInfo>類別也有<xref:System.Globalization.CultureInfo.Calendar%2A>屬性。 但是，它是唯讀，常數;它不會變更以反映新的預設曆法指派給<xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType>屬性。  
  
5.  呼叫<xref:System.DateTime.ToString%2A>或<xref:System.DateTime.ToString%2A>方法，並將它傳遞<xref:System.Globalization.CultureInfo>其預設的行事曆已在上一個步驟中修改的物件。  
  
### <a name="to-display-the-date-in-any-calendar"></a>顯示任何月曆中的日期  
  
1.  具現化衍生自行事曆物件<xref:System.Globalization.Calendar>類別，表示要使用的行事曆。  
  
2.  決定應出現在日期和時間值的字串表示中的日期和時間項目。  
  
3.  針對每個您想要顯示的日期和時間元素，呼叫 行事曆物件的`Get`... 方法。 下列為可用的方法：  
  
    -   <xref:System.Globalization.Calendar.GetYear%2A>將年顯示適當的行事曆。  
  
    -   <xref:System.Globalization.Calendar.GetMonth%2A>顯示中適當的日曆月。  
  
    -   <xref:System.Globalization.Calendar.GetDayOfMonth%2A>若要顯示適當的日曆中的月份天數。  
  
    -   <xref:System.Globalization.Calendar.GetHour%2A>以在適當的行事曆顯示當天的小時。  
  
    -   <xref:System.Globalization.Calendar.GetMinute%2A>以顯示適當的行事曆小時數分鐘。  
  
    -   <xref:System.Globalization.Calendar.GetSecond%2A>在適當的行事曆分鐘內顯示秒數。  
  
    -   <xref:System.Globalization.Calendar.GetMilliseconds%2A>以顯示適當的日曆中的第二個毫秒數。  
  
## <a name="example"></a>範例  
 這個範例顯示使用兩種不同月曆的日期。 日期會在定義回曆作為 ar-JO 文化特性的預設月曆之後顯示，並且會使用波斯曆顯示日期，而波斯曆並不是 fa-IR 文化特性支援的選用月曆。  
  
 [!code-csharp[Formatting.HowTo.Calendar#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#2)]
 [!code-vb[Formatting.HowTo.Calendar#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#2)]  
  
 每個<xref:System.Globalization.CultureInfo>物件可以支援一或多個由指示的行事曆<xref:System.Globalization.CultureInfo.OptionalCalendars%2A>屬性。 下列其中一種會指定為文化特性的預設曆法，而且由唯讀<xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType>屬性。 其他選擇性曆法，即可指定為預設值指派<xref:System.Globalization.Calendar>物件，表示該曆法<xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType>屬性所傳回<xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>屬性。 不過，某些行事曆，例如由波斯曆<xref:System.Globalization.PersianCalendar>類別中，不做任何文化特性的選擇性曆法。  
  
 這個範例會定義可重複使用的月曆公用程式類別 `CalendarUtility`，用來處理使用特殊月曆產生日期的字串表示時的許多細節。 `CalendarUtility` 類別具有下列成員：  
  
-   參數化建構函式的參數，就是<xref:System.Globalization.Calendar>日期為表示的物件。 這個參數會指派給類別的私用欄位。  
  
-   `CalendarExists`會傳回布林值，指出是否行事曆所代表的私用方法`CalendarUtility`物件支援<xref:System.Globalization.CultureInfo>傳遞給方法的參數物件。 方法會包裝呼叫<xref:System.Array.Exists%2A?displayProperty=nameWithType>方法，會傳遞<xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType>陣列。  
  
-   `HasSameName`指派給私用方法<xref:System.Predicate%601>傳遞為參數，以委派<xref:System.Array.Exists%2A?displayProperty=nameWithType>方法。 每一個陣列成員都會傳遞至方法，直到方法傳回 `true` 為止。 這個方法會判斷選用月曆的名稱是否與 `CalendarUtility` 物件代表的月曆相同。  
  
-   `DisplayDate`會傳遞兩個參數的多載的公用方法： 請<xref:System.DateTime>或<xref:System.DateTimeOffset>值所代表的行事曆來表達`CalendarUtility`物件，以及其格式設定的規則所要使用的文化特性。 在傳回日期的字串表示時，其行為會根據文化特性是否支援要使用其格式化規則的目標月曆而定。  
  
 不論用來建立行事曆<xref:System.DateTime>或<xref:System.DateTimeOffset>在此範例中，通常以西曆日期表示值的值。 這是因為<xref:System.DateTime>和<xref:System.DateTimeOffset>類型不會保留任何行事曆資訊。 這兩個值會在內部表示為自 0001 年 1 月 1 日午夜開始經過的刻度數。 該數字的轉譯會根據月曆而定。 大部分文化特性的預設月曆是西曆。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要對 system.core.dll 的參考。  
  
 在命令列使用 csc.exe 或 vb.exe 程式碼編譯。 若要編譯中的程式碼[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]，將其放在主控台應用程式專案範本。  
  
## <a name="see-also"></a>另請參閱  
 [執行格式化作業](../../../docs/standard/base-types/performing-formatting-operations.md)
