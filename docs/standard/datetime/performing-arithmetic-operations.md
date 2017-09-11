---
title: "使用日期和時間執行算術運算"
description: "使用日期和時間執行算術運算"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 589ac5ec-8365-4a0d-bc38-72183718110c
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: b872cc4c2b799ddafc9df263795d860754d1ec17
ms.contentlocale: zh-tw
ms.lasthandoff: 03/02/2017

---

# <a name="performing-arithmetic-operations-with-dates-and-times"></a><span data-ttu-id="ece9e-104">使用日期和時間執行算術運算</span><span class="sxs-lookup"><span data-stu-id="ece9e-104">Performing arithmetic operations with dates and times</span></span>

<span data-ttu-id="ece9e-105">雖然 [System.DateTime](xref:System.DateTime) 和 [System.DateTimeOffset](xref:System.DateTimeOffset) 結構提供對其值執行算術運算的成員，但是算術運算的結果非常不同。</span><span class="sxs-lookup"><span data-stu-id="ece9e-105">Although both the [System.DateTime](xref:System.DateTime) and the [System.DateTimeOffset](xref:System.DateTimeOffset) structures provide members that perform arithmetic operations on their values, the results of arithmetic operations are very different.</span></span> <span data-ttu-id="ece9e-106">本文會檢查這些差異、將它們與日期和時間資料的時區感知程度產生關聯，以及討論如何使用日期和時間資料來執行完全時區感知運算。</span><span class="sxs-lookup"><span data-stu-id="ece9e-106">This article examines those differences, relates them to degrees of time zone awareness in date and time data, and discusses how to perform fully time zone aware operations using date and time data.</span></span>

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a><span data-ttu-id="ece9e-107">使用 DateTime 值的比較和算術運算</span><span class="sxs-lookup"><span data-stu-id="ece9e-107">Comparisons and Arithmetic Operations with DateTime Values</span></span>

<span data-ttu-id="ece9e-108">[System.DateTime](xref:System.DateTime) 值具有有限時區感知程度。</span><span class="sxs-lookup"><span data-stu-id="ece9e-108">[System.DateTime](xref:System.DateTime) values possess a limited degree of time zone awareness.</span></span> <span data-ttu-id="ece9e-109">[DateTime.Kind](xref:System.DateTime.Kind) 屬性允許將 [System.DateTimeKind](xref:System.DateTimeKind) 值指派給日期和時間，指出它是否代表當地時間、國際標準時間 (UTC) 或未指定時區的時間。</span><span class="sxs-lookup"><span data-stu-id="ece9e-109">The [DateTime.Kind](xref:System.DateTime.Kind) property allows a [System.DateTimeKind](xref:System.DateTimeKind) value to be assigned to the date and time to indicate whether it represents local time, Coordinated Universal Time (UTC), or the time in an unspecified time zone.</span></span> <span data-ttu-id="ece9e-110">不過，對 [DateTime](xref:System.DateTime) 值比較或執行日期和時間運算時，會忽略這個有限時區資訊。</span><span class="sxs-lookup"><span data-stu-id="ece9e-110">However, this limited time zone information is ignored when comparing or performing date and time arithmetic on [DateTime](xref:System.DateTime) values.</span></span> <span data-ttu-id="ece9e-111">下列範例會比較目前當地時間與目前 UTC 時間，以說明這點。</span><span class="sxs-lookup"><span data-stu-id="ece9e-111">The following example, which compares the current local time with the current UTC time, illustrates this.</span></span>

```csharp
using System;

public enum TimeComparison
{
   EarlierThan = -1,
   TheSameAs = 0,
   LaterThan = 1
}

public class DateManipulation
{
   public static void Main()
   {
      DateTime localTime = DateTime.Now;
      DateTime utcTime = DateTime.UtcNow;

      Console.WriteLine("Difference between {0} and {1} time: {2}:{3} hours", 
                        localTime.Kind.ToString(), 
                        utcTime.Kind.ToString(), 
                        (localTime - utcTime).Hours, 
                        (localTime - utcTime).Minutes);
      Console.WriteLine("The {0} time is {1} the {2} time.", 
                        localTime.Kind.ToString(), 
                        Enum.GetName(typeof(TimeComparison), localTime.CompareTo(utcTime)), 
                        utcTime.Kind.ToString());  
   }
}
// If run in the U.S. Pacific Standard Time zone, the example displays 
// the following output to the console:
//    Difference between Local and Utc time: -7:0 hours
//    The Local time is EarlierThan the Utc time.
```

```vb
Public Enum TimeComparison As Integer
   EarlierThan = -1
   TheSameAs = 0
   LaterThan = 1
End Enum

Module DateManipulation
   Public Sub Main()
      Dim localTime As Date = Date.Now
      Dim utcTime As Date = Date.UtcNow

      Console.WriteLine("Difference between {0} and {1} time: {2}:{3} hours", _
                        localTime.Kind.ToString(), _
                        utcTime.Kind.ToString(), _
                        (localTime - utcTime).Hours, _
                        (localTime - utcTime).Minutes)
      Console.WriteLine("The {0} time is {1} the {2} time.", _
                        localTime.Kind.ToString(), _ 
                        [Enum].GetName(GetType(TimeComparison), localTime.CompareTo(utcTime)), _
                        utcTime.Kind.ToString())  
      ' If run in the U.S. Pacific Standard Time zone, the example displays 
      ' the following output to the console:
      '    Difference between Local and Utc time: -7:0 hours
      '    The Local time is EarlierThan the Utc time.                                                    
   End Sub
End Module
```

<span data-ttu-id="ece9e-112">[DateTime.CompareTo(DateTime, DateTime)](xref:System.DateTime.Compare(System.DateTime,System.DateTime)) 方法會報告當地時間早於 (或晚於) UTC 時間，接著減法運算會指出 UTC 與當地時間之間的時差，以美國太平洋標準時間時區系統來說相差七個小時。</span><span class="sxs-lookup"><span data-stu-id="ece9e-112">The [DateTime.CompareTo(DateTime, DateTime)](xref:System.DateTime.Compare(System.DateTime,System.DateTime)) method reports that the local time is earlier than (or less than) the UTC time, and the subtraction operation indicates that the difference between UTC and the local time for a system in the U.S. Pacific Standard Time zone is seven hours.</span></span> <span data-ttu-id="ece9e-113">但因為這兩個值提供單一時間點的不同表示，所以在此情況下，此時間間隔很明顯地完全歸因於當地時區與 UTC 的位移。</span><span class="sxs-lookup"><span data-stu-id="ece9e-113">But because these two values provide different representations of a single point in time, it is clear in this case that this time interval is completely attributable to the local time zone's offset from UTC.</span></span> 

<span data-ttu-id="ece9e-114">一般來說，[DateTimeKind](xref:System.DateTimeKind) 屬性不會影響 [DateTime](xref:System.DateTime) 比較和算術方法所傳回的結果 (如兩個相同時間點的比較所指出)，但是可能會影響這些結果的解譯。</span><span class="sxs-lookup"><span data-stu-id="ece9e-114">More generally, the [DateTimeKind](xref:System.DateTimeKind) property does not affect the results returned by [DateTime](xref:System.DateTime) comparison and arithmetic methods (as the comparison of two identical points in time indicates), although it can affect the interpretation of those results.</span></span> <span data-ttu-id="ece9e-115">例如: </span><span class="sxs-lookup"><span data-stu-id="ece9e-115">For example:</span></span>

* <span data-ttu-id="ece9e-116">針對 [DateTimeKind](xref:System.DateTimeKind) 屬性等於 [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) 的兩個日期和時間值所執行的任何算術運算結果，會反映兩個值的實際時間間隔。</span><span class="sxs-lookup"><span data-stu-id="ece9e-116">The result of any arithmetic operation performed on two date and time values whose [DateTimeKind](xref:System.DateTimeKind) properties both equal [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) reflects the actual time interval between the two values.</span></span> <span data-ttu-id="ece9e-117">同樣地，兩個這類日期和時間值的比較會精確地反映時間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="ece9e-117">Similarly, the comparison of two such date and time values accurately reflects the relationship between times.</span></span>

* <span data-ttu-id="ece9e-118">針對 [DateTimeKind](xref:System.DateTimeKind) 屬性等於 [DateTimeKind.Local](xref:System.DateTimeKind.Local) 的兩個日期和時間值或具有不同 [DateTimeKind](xref:System.DateTimeKind) 屬性值的兩個日期和時間值所執行的任何算術或比較運算結果，會反映兩個值的時鐘時間差異。</span><span class="sxs-lookup"><span data-stu-id="ece9e-118">The result of any arithmetic or comparison operation performed on two date and time values whose [DateTimeKind](xref:System.DateTimeKind) properties both equal [DateTimeKind.Local](xref:System.DateTimeKind.Local) or on two date and time values with different [DateTimeKind](xref:System.DateTimeKind) property values reflects the difference in clock time between the two values.</span></span> 

* <span data-ttu-id="ece9e-119">當地日期和時間值的算術或比較作業不會考慮特定值是不明確或無效，也不會考慮當地時區與日光節約時間之轉換所產生的任何調整規則的影響。</span><span class="sxs-lookup"><span data-stu-id="ece9e-119">Arithmetic or comparison operations on local date and time values do not consider whether a particular value is ambiguous or invalid, nor do they take account of the effect of any adjustment rules that result from the local time zone's transition to or from daylight saving time.</span></span>

* <span data-ttu-id="ece9e-120">任何比較或計算 UTC 與當地時間之差異的作業，都會在結果中包含等於當地時區與 UTC 之位移的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="ece9e-120">Any operation that compares or calculates the difference between UTC and a local time includes a time interval equal to the local time zone's offset from UTC in the result.</span></span> 

* <span data-ttu-id="ece9e-121">任何比較或計算未指定時間與 UTC 或當地時間之差異的作業，都會反映簡單時鐘時間。</span><span class="sxs-lookup"><span data-stu-id="ece9e-121">Any operation that compares or calculates the difference between an unspecified time and either UTC or the local time reflects simple clock time.</span></span> <span data-ttu-id="ece9e-122">不考慮時區差異，而且結果不會反映如何套用時區調整規則。</span><span class="sxs-lookup"><span data-stu-id="ece9e-122">Time zone differences are not considered, and the result does not reflect the application of time zone adjustment rules.</span></span> 

* <span data-ttu-id="ece9e-123">任何比較或計算兩個未指定時間之差異的作業都可能包含未知間隔，而未知間隔反映兩個不同時區的時間差異。</span><span class="sxs-lookup"><span data-stu-id="ece9e-123">Any operation that compares or calculates the difference between two unspecified times may include an unknown interval that reflects the difference between the time in two different time zones.</span></span>

<span data-ttu-id="ece9e-124">有許多情況是時區差異不會影響日期和時間計算，或日期和時間資料的內容會定義比較或算術運算的意義。</span><span class="sxs-lookup"><span data-stu-id="ece9e-124">There are many scenarios in which time zone differences do not affect date and time calculations or in which the context of the date and time data defines the meaning of comparison or arithmetic operations.</span></span> <span data-ttu-id="ece9e-125">如需其中部分項目的討論，請參閱[在 DateTime、DateTimeOffset、TimeSpan 與 TimeZoneInfo 之間選擇](choosing-between-datetime.md)。</span><span class="sxs-lookup"><span data-stu-id="ece9e-125">For a discussion of some of these, see [Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo](choosing-between-datetime.md).</span></span>

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a><span data-ttu-id="ece9e-126">使用 DateTimeOffset 值的比較和算術運算</span><span class="sxs-lookup"><span data-stu-id="ece9e-126">Comparisons and Arithmetic Operations with DateTimeOffset Values</span></span>

<span data-ttu-id="ece9e-127">[System.DateTimeOffset](xref:System.DateTimeOffset) 值不只包含日期和時間，也會包含明確定義該日期和時間相對於 UTC 的位移。</span><span class="sxs-lookup"><span data-stu-id="ece9e-127">A [System.DateTimeOffset](xref:System.DateTimeOffset) value includes not only a date and time, but also an offset that unambiguously defines that date and time relative to UTC.</span></span> <span data-ttu-id="ece9e-128">這樣可能會針對 [System.DateTime](xref:System.DateTime) 值定義略有不同的相等性。</span><span class="sxs-lookup"><span data-stu-id="ece9e-128">This makes it possible to define equality somewhat differently than for [System.DateTime](xref:System.DateTime) values.</span></span> <span data-ttu-id="ece9e-129">而 [DateTime](xref:System.DateTime) 值若具有相同日期和時間值則相等，[DateTimeOffset](xref:System.DateTimeOffset) 值若參照相同時間點則相等。</span><span class="sxs-lookup"><span data-stu-id="ece9e-129">Whereas [DateTime](xref:System.DateTime) values are equal if they have the same date and time value, [DateTimeOffset](xref:System.DateTimeOffset) values are equal if they both refer to the same point in time.</span></span> <span data-ttu-id="ece9e-130">如果用於判斷兩個日期和時間之間隔的比較和大部分算術運算，則這採用更精確且較不需要解譯的 [DateTimeOffset](xref:System.DateTimeOffset) 值。</span><span class="sxs-lookup"><span data-stu-id="ece9e-130">This makes a [DateTimeOffset](xref:System.DateTimeOffset) value more accurate and less in need of interpretation when used in comparisons and in most arithmetic operations that determine the interval between two dates and times.</span></span> <span data-ttu-id="ece9e-131">下列範例 (即 [DateTimeOffset](xref:System.DateTimeOffset) 等於比較當地和 UTC DateTime 值的前一個範例) 說明這項行為差異。</span><span class="sxs-lookup"><span data-stu-id="ece9e-131">The following example, which is the [DateTimeOffset](xref:System.DateTimeOffset) equivalent to the previous example that compared local and UTC DateTime values, illustrates this difference in behavior.</span></span>

```csharp
using System;

public enum TimeComparison
{
   EarlierThan = -1,
   TheSameAs = 0,
   LaterThan = 1
}

public class DateTimeOffsetManipulation
{
   public static void Main()
   {
      DateTimeOffset localTime = DateTimeOffset.Now;
      DateTimeOffset utcTime = DateTimeOffset.UtcNow;

      Console.WriteLine("Difference between local time and UTC: {0}:{1:D2} hours", 
                        (localTime - utcTime).Hours, 
                        (localTime - utcTime).Minutes);
      Console.WriteLine("The local time is {0} UTC.", 
                        Enum.GetName(typeof(TimeComparison), localTime.CompareTo(utcTime)));  
   }
}
// Regardless of the local time zone, the example displays 
// the following output to the console:
//    Difference between local time and UTC: 0:00 hours.
//    The local time is TheSameAs UTC.
```

```vb
Public Enum TimeComparison As Integer
   EarlierThan = -1
   TheSameAs = 0
   LaterThan = 1
End Enum

Module DateTimeOffsetManipulation
   Public Sub Main()
      Dim localTime As DateTimeOffset = DateTimeOffset.Now
      Dim utcTime As DateTimeOffset = DateTimeOffset.UtcNow

      Console.WriteLine("Difference between local time and UTC: {0}:{1:D2} hours.", _
                        (localTime - utcTime).Hours, _
                        (localTime - utcTime).Minutes)
      Console.WriteLine("The local time is {0} UTC.", _
                        [Enum].GetName(GetType(TimeComparison), localTime.CompareTo(utcTime)))  
   End Sub
End Module
' Regardless of the local time zone, the example displays 
' the following output to the console:
'    Difference between local time and UTC: 0:00 hours.
'    The local time is TheSameAs UTC.
'          Console.WriteLine(e.GetType().Name)
```

<span data-ttu-id="ece9e-132">在此範例中，[DateTimeOffset.CompareTo](xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)) 方法表示目前當地時間和目前 UTC 時間相等，而且減去 [DateTimeOffset](xref:System.DateTimeOffset) 值表示兩個時間的差異是 [TimeSpan.Zero](xref:System.TimeSpan.Zero)。</span><span class="sxs-lookup"><span data-stu-id="ece9e-132">In this example, the [DateTimeOffset.CompareTo](xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)) method indicates that the current local time and the current UTC time are equal, and subtraction of [DateTimeOffset](xref:System.DateTimeOffset) values indicates that the difference between the two times is [TimeSpan.Zero](xref:System.TimeSpan.Zero).</span></span> 

<span data-ttu-id="ece9e-133">在日期和時間運算中使用 [DateTimeOffset](xref:System.DateTimeOffset) 值的主要限制，在於雖然 [DateTimeOffset](xref:System.DateTimeOffset) 值具有一些時區感知，但並不是完全時區感知的。</span><span class="sxs-lookup"><span data-stu-id="ece9e-133">The chief limitation of using [DateTimeOffset](xref:System.DateTimeOffset) values in date and time arithmetic is that although [DateTimeOffset](xref:System.DateTimeOffset) values have some time zone awareness, they are not fully time zone aware.</span></span> <span data-ttu-id="ece9e-134">雖然 [DateTimeOffset](xref:System.DateTimeOffset) 值的位移會在第一次指派 [DateTimeOffset](xref:System.DateTimeOffset) 變數的值時反映時區與 UTC 的位移，但是之後會與時區解除關聯。</span><span class="sxs-lookup"><span data-stu-id="ece9e-134">Although the [DateTimeOffset](xref:System.DateTimeOffset) value's offset reflects a time zone's offset from UTC when a [DateTimeOffset](xref:System.DateTimeOffset) variable is first assigned a value, it becomes disassociated from the time zone thereafter.</span></span> <span data-ttu-id="ece9e-135">因為它不再與可識別時間直接關聯，所以加上和減去日期和時間間隔不會視為時區的調整規則。</span><span class="sxs-lookup"><span data-stu-id="ece9e-135">Because it is no longer directly associated with an identifiable time, the addition and subtraction of date and time intervals does not consider a time zone's adjustment rules.</span></span> 

<span data-ttu-id="ece9e-136">舉例而言，美國中央標準時間時區轉換成日光節約時間是在 2008 年 3 月 9 日的</span><span class="sxs-lookup"><span data-stu-id="ece9e-136">To illustrate, the transition to daylight saving time in the U.S. Central Standard Time zone occurs at 2:00 A.M.</span></span> <span data-ttu-id="ece9e-137">凌晨 2:00 發生。</span><span class="sxs-lookup"><span data-stu-id="ece9e-137">on March 9, 2008.</span></span> <span data-ttu-id="ece9e-138">這表示，中央標準時間 2008 年 3 月 9 日上午 1:30 加上兩個半小時的間隔，</span><span class="sxs-lookup"><span data-stu-id="ece9e-138">This means that adding a two and a half hour interval to a Central Standard time of 1:30 A.M.</span></span> <span data-ttu-id="ece9e-139">就會產生 2008 年 3 月 9 日凌晨 5:00 的</span><span class="sxs-lookup"><span data-stu-id="ece9e-139">on March 9, 2008, should produce a date and time of 5:00 A.M.</span></span> <span data-ttu-id="ece9e-140">日期和時間。</span><span class="sxs-lookup"><span data-stu-id="ece9e-140">on March 9, 2008.</span></span> <span data-ttu-id="ece9e-141">不過，如下列範例所示，加上兩個半小時後為 2008 年 3 月 9 日</span><span class="sxs-lookup"><span data-stu-id="ece9e-141">However, as the following example shows, the result of the addition is 4:00 A.M.</span></span> <span data-ttu-id="ece9e-142">凌晨 4:00。</span><span class="sxs-lookup"><span data-stu-id="ece9e-142">on March 9, 2008.</span></span> <span data-ttu-id="ece9e-143">請注意，雖然這並非我們感興趣的時區時間 (亦即，它沒有預期的時區位移)，但是這項作業的結果確實代表正確時間點。</span><span class="sxs-lookup"><span data-stu-id="ece9e-143">Note that this result of this operation does represent the correct point in time, although it is not the time in the time zone in which we are interested (that is, it does not have the expected time zone offset).</span></span>

```csharp
using System;

public class IntervalArithmetic
{
   public static void Main()
   {
      DateTime generalTime = new DateTime(2008, 3, 9, 1, 30, 0);
      const string tzName = "Central Standard Time";
      TimeSpan twoAndAHalfHours = new TimeSpan(2, 30, 0);

      // Instantiate DateTimeOffset value to have correct CST offset
      try
      {
         DateTimeOffset centralTime1 = new DateTimeOffset(generalTime, 
                    TimeZoneInfo.FindSystemTimeZoneById(tzName).GetUtcOffset(generalTime));

         // Add two and a half hours      
         DateTimeOffset centralTime2 = centralTime1.Add(twoAndAHalfHours);
         // Display result
         Console.WriteLine("{0} + {1} hours = {2}", centralTime1, 
                                                    twoAndAHalfHours.ToString(), 
                                                    centralTime2);  
      }
      catch (TimeZoneNotFoundException)
      {
         Console.WriteLine("Unable to retrieve Central Standard Time zone information.");
      }
   }
}
// The example displays the following output to the console:
//    3/9/2008 1:30:00 AM -06:00 + 02:30:00 hours = 3/9/2008 4:00:00 AM -06:00
```

```vb
Module IntervalArithmetic
   Public Sub Main()
      Dim generalTime As Date = #03/09/2008 1:30AM#
      Const tzName As String = "Central Standard Time"
      Dim twoAndAHalfHours As New TimeSpan(2, 30, 0)

      ' Instantiate DateTimeOffset value to have correct CST offset
      Try
         Dim centralTime1 As New DateTimeOffset(generalTime, _
                    TimeZoneInfo.FindSystemTimeZoneById(tzName).GetUtcOffset(generalTime))

         ' Add two and a half hours      
         Dim centralTime2 As DateTimeOffset = centralTime1.Add(twoAndAHalfHours)
         ' Display result
         Console.WriteLine("{0} + {1} hours = {2}", centralTime1, _
                                                    twoAndAHalfHours.ToString(), _
                                                    centralTime2)   
      Catch e As TimeZoneNotFoundException
         Console.WriteLine("Unable to retrieve Central Standard Time zone information.")
      End Try
   End Sub
End Module
' The example displays the following output to the console:
'    3/9/2008 1:30:00 AM -06:00 + 02:30:00 hours = 3/9/2008 4:00:00 AM -06:00
```

## <a name="arithmetic-operations-with-times-in-time-zones"></a><span data-ttu-id="ece9e-144">使用時區時間的算術運算</span><span class="sxs-lookup"><span data-stu-id="ece9e-144">Arithmetic Operations with Times in Time Zones</span></span>

<span data-ttu-id="ece9e-145">[System.TimeZoneInfo](xref:System.TimeZoneInfo) 類別未提供任何方法，可在您執行日期和時間運算時自動套用調整規則。</span><span class="sxs-lookup"><span data-stu-id="ece9e-145">The [System.TimeZoneInfo](xref:System.TimeZoneInfo) class does not provide any methods that automatically apply adjustment rules when you perform date and time arithmetic.</span></span> <span data-ttu-id="ece9e-146">不過，作法是將時區時間轉換為 UTC，並執行算術運算，然後從 UTC 轉換回時區時間。</span><span class="sxs-lookup"><span data-stu-id="ece9e-146">However, you can do this by converting the time in a time zone to UTC, performing the arithmetic operation, and then converting from UTC back to the time in the time zone.</span></span> <span data-ttu-id="ece9e-147">如需詳細資訊，請參閱[如何：在日期和時間運算中使用時區](use-time-zones-in-arithmetic.md)。</span><span class="sxs-lookup"><span data-stu-id="ece9e-147">For details, see [How to: Use Time Zones in Date and Time Arithmetic](use-time-zones-in-arithmetic.md).</span></span>

<span data-ttu-id="ece9e-148">例如，下列程式碼與前面的程式碼類似，也是將 2008 年 3 月 9 日</span><span class="sxs-lookup"><span data-stu-id="ece9e-148">For example, the following code is similar to the previous code that added two-and-a-half hours to 2:00 A.M.</span></span> <span data-ttu-id="ece9e-149">凌晨 2:00 加上兩個半小時。</span><span class="sxs-lookup"><span data-stu-id="ece9e-149">on March 9, 2008.</span></span> <span data-ttu-id="ece9e-150">不過，因為它會先將美加中部標準時間轉換為 UTC，再執行日期和時間運算，然後將 UTC 的結果轉換回美加中部標準時間，所以產生的時間會反映美加中部標準時區到日光節約時間的轉換。</span><span class="sxs-lookup"><span data-stu-id="ece9e-150">However, because it converts a Central Standard time to UTC before it performs date and time arithmetic, and then converts the result from UTC back to Central Standard time, the resulting time reflects the Central Standard Time Zone's transition to daylight saving time.</span></span>

```csharp
using System;

public class TimeZoneAwareArithmetic
{
   public static void Main()
   {
      const string tzName = "Central Standard Time";

      DateTime generalTime = new DateTime(2008, 3, 9, 1, 30, 0);
      TimeZoneInfo cst = TimeZoneInfo.FindSystemTimeZoneById(tzName);
      TimeSpan twoAndAHalfHours = new TimeSpan(2, 30, 0);

      // Instantiate DateTimeOffset value to have correct CST offset
      try
      {
         DateTimeOffset centralTime1 = new DateTimeOffset(generalTime, 
                                       cst.GetUtcOffset(generalTime));

         // Add two and a half hours
         DateTimeOffset utcTime = centralTime1.ToUniversalTime();
         utcTime += twoAndAHalfHours;

         DateTimeOffset centralTime2 = TimeZoneInfo.ConvertTime(utcTime, cst);
         // Display result
         Console.WriteLine("{0} + {1} hours = {2}", centralTime1, 
                                                    twoAndAHalfHours.ToString(), 
                                                    centralTime2);  
      }
      catch (TimeZoneNotFoundException)
      {
         Console.WriteLine("Unable to retrieve Central Standard Time zone information.");
      }
   }
}
// The example displays the following output to the console:
//    3/9/2008 1:30:00 AM -06:00 + 02:30:00 hours = 3/9/2008 5:00:00 AM -05:00
```

```vb
Module TimeZoneAwareArithmetic
   Public Sub Main()
      Const tzName As String = "Central Standard Time"

      Dim generalTime As Date = #03/09/2008 1:30AM#
      Dim cst As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById(tzName) 
      Dim twoAndAHalfHours As New TimeSpan(2, 30, 0)

      ' Instantiate DateTimeOffset value to have correct CST offset
      Try
         Dim centralTime1 As New DateTimeOffset(generalTime, _
                    cst.GetUtcOffset(generalTime))

         ' Add two and a half hours 
         Dim utcTime As DateTimeOffset = centralTime1.ToUniversalTime()
         utcTime += twoAndAHalfHours

         Dim centralTime2 As DateTimeOffset = TimeZoneInfo.ConvertTime(utcTime, cst)
         ' Display result
         Console.WriteLine("{0} + {1} hours = {2}", centralTime1, _
                                                    twoAndAHalfHours.ToString(), _
                                                    centralTime2)   
      Catch e As TimeZoneNotFoundException
         Console.WriteLine("Unable to retrieve Central Standard Time zone information.")
      End Try
   End Sub
End Module
' The example displays the following output to the console:
'    3/9/2008 1:30:00 AM -06:00 + 02:30:00 hours = 3/9/2008 5:00:00 AM -05:00
```

## <a name="see-also"></a><span data-ttu-id="ece9e-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ece9e-151">See Also</span></span>

[<span data-ttu-id="ece9e-152">日期、時間及時區</span><span class="sxs-lookup"><span data-stu-id="ece9e-152">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="ece9e-153">如何：在日期與時間運算中使用時區</span><span class="sxs-lookup"><span data-stu-id="ece9e-153">How to: use time zones in date and time arithmetic</span></span>](use-time-zones-in-arithmetic.md)



