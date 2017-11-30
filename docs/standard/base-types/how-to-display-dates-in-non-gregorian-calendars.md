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
# <a name="how-to-display-dates-in-non-gregorian-calendars"></a><span data-ttu-id="8c3d2-102">如何：在非西曆中顯示日期</span><span class="sxs-lookup"><span data-stu-id="8c3d2-102">How to: Display Dates in Non-Gregorian Calendars</span></span>
<span data-ttu-id="8c3d2-103"><xref:System.DateTime>和<xref:System.DateTimeOffset>類型做為其預設行事曆使用西曆。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-103">The <xref:System.DateTime> and <xref:System.DateTimeOffset> types use the Gregorian calendar as their default calendar.</span></span> <span data-ttu-id="8c3d2-104">這表示即使該日期和時間是使用其他月曆所建立，呼叫日期和時間值的 `ToString` 方法仍會使用西曆顯示該日期和時間的字串表示。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-104">This means that calling a date and time value's `ToString` method displays the string representation of that date and time in the Gregorian calendar, even if that date and time was created using another calendar.</span></span> <span data-ttu-id="8c3d2-105">以下是在下列範例中，這會使用兩種不同的方式來建立與波斯曆中的日期和時間值，但仍會顯示這些日期和時間值在西曆中呼叫時，如果<xref:System.DateTime.ToString%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-105">This is illustrated in the following example, which uses two different ways to create a date and time value with the Persian calendar, but still displays those date and time values in the Gregorian calendar when it calls the <xref:System.DateTime.ToString%2A> method.</span></span> <span data-ttu-id="8c3d2-106">此範例反映兩種常用來顯示特殊月曆之日期，但不正確的技術。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-106">This example reflects two commonly used but incorrect techniques for displaying the date in a particular calendar.</span></span>  
  
 [!code-csharp[Formatting.HowTo.Calendar#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#1)]
 [!code-vb[Formatting.HowTo.Calendar#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#1)]  
  
 <span data-ttu-id="8c3d2-107">這兩種不同的技術可用來顯示特殊月曆的日期。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-107">Two different techniques can be used to display the date in a particular calendar.</span></span> <span data-ttu-id="8c3d2-108">第一種技術要求該月曆必須是某個文化特性的預設月曆。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-108">The first requires that the calendar be the default calendar for a particular culture.</span></span> <span data-ttu-id="8c3d2-109">第二種技術可搭配任何月曆使用。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-109">The second can be used with any calendar.</span></span>  
  
### <a name="to-display-the-date-for-a-cultures-default-calendar"></a><span data-ttu-id="8c3d2-110">顯示文化特性預設月曆的日期</span><span class="sxs-lookup"><span data-stu-id="8c3d2-110">To display the date for a culture's default calendar</span></span>  
  
1.  <span data-ttu-id="8c3d2-111">具現化衍生自行事曆物件<xref:System.Globalization.Calendar>類別，表示要使用的行事曆。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-111">Instantiate a calendar object derived from the <xref:System.Globalization.Calendar> class that represents the calendar to be used.</span></span>  
  
2.  <span data-ttu-id="8c3d2-112">具現化<xref:System.Globalization.CultureInfo>表示會用來顯示日期的格式化之文化特性的物件。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-112">Instantiate a <xref:System.Globalization.CultureInfo> object representing the culture whose formatting will be used to display the date.</span></span>  
  
3.  <span data-ttu-id="8c3d2-113">呼叫<xref:System.Array.Exists%2A?displayProperty=nameWithType>方法，以判斷行事曆物件是否為所傳回的陣列成員<xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-113">Call the <xref:System.Array.Exists%2A?displayProperty=nameWithType> method to determine whether the calendar object is a member of the array returned by the <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="8c3d2-114">這表示行事曆可做為預設行事曆<xref:System.Globalization.CultureInfo>物件。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-114">This indicates that the calendar can serve as the default calendar for the <xref:System.Globalization.CultureInfo> object.</span></span> <span data-ttu-id="8c3d2-115">如果不是陣列成員，請依照＜顯示任何月曆中的日期＞一節中的指示進行。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-115">If it is not a member of the array, follow the instructions in the "To Display the Date in Any Calendar" section.</span></span>  
  
4.  <span data-ttu-id="8c3d2-116">若要將行事曆物件指派<xref:System.Globalization.DateTimeFormatInfo.Calendar%2A>屬性<xref:System.Globalization.DateTimeFormatInfo>所傳回物件<xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-116">Assign the calendar object to the <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A> property of the <xref:System.Globalization.DateTimeFormatInfo> object returned by the <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> property.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8c3d2-117"><xref:System.Globalization.CultureInfo>類別也有<xref:System.Globalization.CultureInfo.Calendar%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-117">The <xref:System.Globalization.CultureInfo> class also has a <xref:System.Globalization.CultureInfo.Calendar%2A> property.</span></span> <span data-ttu-id="8c3d2-118">但是，它是唯讀，常數;它不會變更以反映新的預設曆法指派給<xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-118">However, it is read-only and constant; it does not change to reflect the new default calendar assigned to the <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> property.</span></span>  
  
5.  <span data-ttu-id="8c3d2-119">呼叫<xref:System.DateTime.ToString%2A>或<xref:System.DateTime.ToString%2A>方法，並將它傳遞<xref:System.Globalization.CultureInfo>其預設的行事曆已在上一個步驟中修改的物件。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-119">Call either the <xref:System.DateTime.ToString%2A> or the <xref:System.DateTime.ToString%2A> method, and pass it the <xref:System.Globalization.CultureInfo> object whose default calendar was modified in the previous step.</span></span>  
  
### <a name="to-display-the-date-in-any-calendar"></a><span data-ttu-id="8c3d2-120">顯示任何月曆中的日期</span><span class="sxs-lookup"><span data-stu-id="8c3d2-120">To display the date in any calendar</span></span>  
  
1.  <span data-ttu-id="8c3d2-121">具現化衍生自行事曆物件<xref:System.Globalization.Calendar>類別，表示要使用的行事曆。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-121">Instantiate a calendar object derived from the <xref:System.Globalization.Calendar> class that represents the calendar to be used.</span></span>  
  
2.  <span data-ttu-id="8c3d2-122">決定應出現在日期和時間值的字串表示中的日期和時間項目。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-122">Determine which date and time elements should appear in the string representation of the date and time value.</span></span>  
  
3.  <span data-ttu-id="8c3d2-123">針對每個您想要顯示的日期和時間元素，呼叫 行事曆物件的`Get`...</span><span class="sxs-lookup"><span data-stu-id="8c3d2-123">For each date and time element that you want to display, call the calendar object's `Get`…</span></span> <span data-ttu-id="8c3d2-124">方法。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-124">method.</span></span> <span data-ttu-id="8c3d2-125">下列為可用的方法：</span><span class="sxs-lookup"><span data-stu-id="8c3d2-125">The following methods are available:</span></span>  
  
    -   <span data-ttu-id="8c3d2-126"><xref:System.Globalization.Calendar.GetYear%2A>將年顯示適當的行事曆。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-126"><xref:System.Globalization.Calendar.GetYear%2A>, to display the year in the appropriate calendar.</span></span>  
  
    -   <span data-ttu-id="8c3d2-127"><xref:System.Globalization.Calendar.GetMonth%2A>顯示中適當的日曆月。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-127"><xref:System.Globalization.Calendar.GetMonth%2A>, to display the month in the appropriate calendar.</span></span>  
  
    -   <span data-ttu-id="8c3d2-128"><xref:System.Globalization.Calendar.GetDayOfMonth%2A>若要顯示適當的日曆中的月份天數。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-128"><xref:System.Globalization.Calendar.GetDayOfMonth%2A>, to display the number of the day of the month in the appropriate calendar.</span></span>  
  
    -   <span data-ttu-id="8c3d2-129"><xref:System.Globalization.Calendar.GetHour%2A>以在適當的行事曆顯示當天的小時。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-129"><xref:System.Globalization.Calendar.GetHour%2A>, to display the hour of the day in the appropriate calendar.</span></span>  
  
    -   <span data-ttu-id="8c3d2-130"><xref:System.Globalization.Calendar.GetMinute%2A>以顯示適當的行事曆小時數分鐘。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-130"><xref:System.Globalization.Calendar.GetMinute%2A>, to display the minutes in the hour in the appropriate calendar.</span></span>  
  
    -   <span data-ttu-id="8c3d2-131"><xref:System.Globalization.Calendar.GetSecond%2A>在適當的行事曆分鐘內顯示秒數。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-131"><xref:System.Globalization.Calendar.GetSecond%2A>, to display the seconds in the minute in the appropriate calendar.</span></span>  
  
    -   <span data-ttu-id="8c3d2-132"><xref:System.Globalization.Calendar.GetMilliseconds%2A>以顯示適當的日曆中的第二個毫秒數。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-132"><xref:System.Globalization.Calendar.GetMilliseconds%2A> , to display the milliseconds in the second in the appropriate calendar.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c3d2-133">範例</span><span class="sxs-lookup"><span data-stu-id="8c3d2-133">Example</span></span>  
 <span data-ttu-id="8c3d2-134">這個範例顯示使用兩種不同月曆的日期。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-134">The example displays a date using two different calendars.</span></span> <span data-ttu-id="8c3d2-135">日期會在定義回曆作為 ar-JO 文化特性的預設月曆之後顯示，並且會使用波斯曆顯示日期，而波斯曆並不是 fa-IR 文化特性支援的選用月曆。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-135">It displays the date after defining the Hijri calendar as the default calendar for the ar-JO culture, and displays the date using the Persian calendar, which is not supported as an optional calendar by the fa-IR culture.</span></span>  
  
 [!code-csharp[Formatting.HowTo.Calendar#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#2)]
 [!code-vb[Formatting.HowTo.Calendar#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#2)]  
  
 <span data-ttu-id="8c3d2-136">每個<xref:System.Globalization.CultureInfo>物件可以支援一或多個由指示的行事曆<xref:System.Globalization.CultureInfo.OptionalCalendars%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-136">Each <xref:System.Globalization.CultureInfo> object can support one or more calendars, which are indicated by the <xref:System.Globalization.CultureInfo.OptionalCalendars%2A> property.</span></span> <span data-ttu-id="8c3d2-137">下列其中一種會指定為文化特性的預設曆法，而且由唯讀<xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-137">One of these is designated as the culture's default calendar and is returned by the read-only <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="8c3d2-138">其他選擇性曆法，即可指定為預設值指派<xref:System.Globalization.Calendar>物件，表示該曆法<xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType>屬性所傳回<xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-138">Another of the optional calendars can be designated as the default by assigning a <xref:System.Globalization.Calendar> object that represents that calendar to the <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> property returned by the <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="8c3d2-139">不過，某些行事曆，例如由波斯曆<xref:System.Globalization.PersianCalendar>類別中，不做任何文化特性的選擇性曆法。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-139">However, some calendars, such as the Persian calendar represented by the <xref:System.Globalization.PersianCalendar> class, do not serve as optional calendars for any culture.</span></span>  
  
 <span data-ttu-id="8c3d2-140">這個範例會定義可重複使用的月曆公用程式類別 `CalendarUtility`，用來處理使用特殊月曆產生日期的字串表示時的許多細節。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-140">The example defines a reusable calendar utility class, `CalendarUtility`, to handle many of the details of generating the string representation of a date using a particular calendar.</span></span> <span data-ttu-id="8c3d2-141">`CalendarUtility` 類別具有下列成員：</span><span class="sxs-lookup"><span data-stu-id="8c3d2-141">The `CalendarUtility` class has the following members:</span></span>  
  
-   <span data-ttu-id="8c3d2-142">參數化建構函式的參數，就是<xref:System.Globalization.Calendar>日期為表示的物件。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-142">A parameterized constructor whose single parameter is a <xref:System.Globalization.Calendar> object in which a date is to be represented.</span></span> <span data-ttu-id="8c3d2-143">這個參數會指派給類別的私用欄位。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-143">This is assigned to a private field of the class.</span></span>  
  
-   <span data-ttu-id="8c3d2-144">`CalendarExists`會傳回布林值，指出是否行事曆所代表的私用方法`CalendarUtility`物件支援<xref:System.Globalization.CultureInfo>傳遞給方法的參數物件。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-144">`CalendarExists`, a private method that returns a Boolean value indicating whether the calendar represented by the `CalendarUtility` object is supported by the <xref:System.Globalization.CultureInfo> object that is passed to the method as a parameter.</span></span> <span data-ttu-id="8c3d2-145">方法會包裝呼叫<xref:System.Array.Exists%2A?displayProperty=nameWithType>方法，會傳遞<xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType>陣列。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-145">The method wraps a call to the <xref:System.Array.Exists%2A?displayProperty=nameWithType> method, to which it passes the <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> array.</span></span>  
  
-   <span data-ttu-id="8c3d2-146">`HasSameName`指派給私用方法<xref:System.Predicate%601>傳遞為參數，以委派<xref:System.Array.Exists%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-146">`HasSameName`, a private method assigned to the <xref:System.Predicate%601> delegate that is passed as a parameter to the <xref:System.Array.Exists%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8c3d2-147">每一個陣列成員都會傳遞至方法，直到方法傳回 `true` 為止。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-147">Each member of the array is passed to the method until the method returns `true`.</span></span> <span data-ttu-id="8c3d2-148">這個方法會判斷選用月曆的名稱是否與 `CalendarUtility` 物件代表的月曆相同。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-148">The method determines whether the name of an optional calendar is the same as the calendar represented by the `CalendarUtility` object.</span></span>  
  
-   <span data-ttu-id="8c3d2-149">`DisplayDate`會傳遞兩個參數的多載的公用方法： 請<xref:System.DateTime>或<xref:System.DateTimeOffset>值所代表的行事曆來表達`CalendarUtility`物件，以及其格式設定的規則所要使用的文化特性。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-149">`DisplayDate`, an overloaded public method that is passed two parameters: either a <xref:System.DateTime> or <xref:System.DateTimeOffset> value to express in the calendar represented by the `CalendarUtility` object; and the culture whose formatting rules are to be used.</span></span> <span data-ttu-id="8c3d2-150">在傳回日期的字串表示時，其行為會根據文化特性是否支援要使用其格式化規則的目標月曆而定。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-150">Its behavior in returning the string representation of a date depends on whether the target calendar is supported by the culture whose formatting rules are to be used.</span></span>  
  
 <span data-ttu-id="8c3d2-151">不論用來建立行事曆<xref:System.DateTime>或<xref:System.DateTimeOffset>在此範例中，通常以西曆日期表示值的值。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-151">Regardless of the calendar used to create a <xref:System.DateTime> or <xref:System.DateTimeOffset> value in this example, that value is typically expressed as a Gregorian date.</span></span> <span data-ttu-id="8c3d2-152">這是因為<xref:System.DateTime>和<xref:System.DateTimeOffset>類型不會保留任何行事曆資訊。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-152">This is because the <xref:System.DateTime> and <xref:System.DateTimeOffset> types do not preserve any calendar information.</span></span> <span data-ttu-id="8c3d2-153">這兩個值會在內部表示為自 0001 年 1 月 1 日午夜開始經過的刻度數。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-153">Internally, they are represented as the number of ticks that have elapsed since midnight of January 1, 0001.</span></span> <span data-ttu-id="8c3d2-154">該數字的轉譯會根據月曆而定。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-154">The interpretation of that number depends on the calendar.</span></span> <span data-ttu-id="8c3d2-155">大部分文化特性的預設月曆是西曆。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-155">For most cultures, the default calendar is the Gregorian calendar.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8c3d2-156">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="8c3d2-156">Compiling the Code</span></span>  
 <span data-ttu-id="8c3d2-157">這個範例需要對 system.core.dll 的參考。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-157">This example requires a reference to System.Core.dll.</span></span>  
  
 <span data-ttu-id="8c3d2-158">在命令列使用 csc.exe 或 vb.exe 程式碼編譯。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-158">Compile the code at the command line using csc.exe or vb.exe.</span></span> <span data-ttu-id="8c3d2-159">若要編譯中的程式碼[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]，將其放在主控台應用程式專案範本。</span><span class="sxs-lookup"><span data-stu-id="8c3d2-159">To compile the code in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], put it in a console application project template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c3d2-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c3d2-160">See Also</span></span>  
 [<span data-ttu-id="8c3d2-161">執行格式化作業</span><span class="sxs-lookup"><span data-stu-id="8c3d2-161">Performing Formatting Operations</span></span>](../../../docs/standard/base-types/performing-formatting-operations.md)
