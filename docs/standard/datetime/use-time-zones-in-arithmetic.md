---
title: "如何：在日期和時間運算中使用時區"
description: "如何在日期和時間運算中使用時區"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 26870cdc-1709-4978-831b-ff2a2f24856f
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: a86471972d42adcbc412cc8eeb300410ca8a9c42
ms.contentlocale: zh-tw
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a><span data-ttu-id="44902-104">如何：在日期和時間運算中使用時區</span><span class="sxs-lookup"><span data-stu-id="44902-104">How to: use time zones in date and time arithmetic</span></span>

<span data-ttu-id="44902-105">一般來說，當您使用 [System.DateTimeOffset](xref:System.DateTimeOffset) 值執行日期和時間算術時，結果不會反映任何時區調整規則。</span><span class="sxs-lookup"><span data-stu-id="44902-105">Ordinarily, when you perform date and time arithmetic using [System.DateTimeOffset](xref:System.DateTimeOffset) values, the result does not reflect any time zone adjustment rules.</span></span> <span data-ttu-id="44902-106">即使可清楚識別日期和時間值的時區，也是這樣。</span><span class="sxs-lookup"><span data-stu-id="44902-106">This is true even when the time zone of the date and time value is clearly identifiable.</span></span> <span data-ttu-id="44902-107">本文示範如何對屬於特定時區的日期和時間值執行算術運算。</span><span class="sxs-lookup"><span data-stu-id="44902-107">This article shows how to perform arithmetic operations on date and time values that belong to a particular time zone.</span></span> <span data-ttu-id="44902-108">算術運算的結果將反映時區調整規則。</span><span class="sxs-lookup"><span data-stu-id="44902-108">The results of the arithmetic operations will reflect the time zone's adjustment rules.</span></span>

## <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a><span data-ttu-id="44902-109">將調整規則套用至日期和時間運算</span><span class="sxs-lookup"><span data-stu-id="44902-109">To apply adjustment rules to date and time arithmetic</span></span>

1. <span data-ttu-id="44902-110">實作某種方法，以將日期和時間值與所屬時區緊密結合。</span><span class="sxs-lookup"><span data-stu-id="44902-110">Implement some method of closely coupling a date and time value with the time zone to which it belongs.</span></span> <span data-ttu-id="44902-111">例如，宣告包含日期和時間值及其時區的結構。</span><span class="sxs-lookup"><span data-stu-id="44902-111">For example, declare a structure that includes both the date and time value and its time zone.</span></span> <span data-ttu-id="44902-112">下列範例使用這種方式來連結 [DateTimeOffset](xref:System.DateTimeOffset) 值與其時區。</span><span class="sxs-lookup"><span data-stu-id="44902-112">The following example uses this approach to link a [DateTimeOffset](xref:System.DateTimeOffset) value with its time zone.</span></span>

    ```csharp
    // Define a structure for DateTime values for internal use only
    internal struct TimeWithTimeZone
    {
    TimeZoneInfo TimeZone;
    DateTimeOffset Time;
    }
    ```

    ```vb
    ' Define a structure for DateTime values for internal use only
    Friend Structure TimeWithTimeZone
       Dim TimeZone As TimeZoneInfo
       Dim Time As Date
    End Structure
    ```
    
2. <span data-ttu-id="44902-113">呼叫 [TimeZoneInfo.ConvertTime(DateTime, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)) 方法，以將時間轉換為國際標準時間 (UTC)。</span><span class="sxs-lookup"><span data-stu-id="44902-113">Convert a time to Coordinated Universal Time (UTC) by calling the [TimeZoneInfo.ConvertTime(DateTime, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)) method.</span></span>

3. <span data-ttu-id="44902-114">對 UTC 時間執行算術運算。</span><span class="sxs-lookup"><span data-stu-id="44902-114">Perform the arithmetic operation on the UTC time.</span></span>

4. <span data-ttu-id="44902-115">呼叫 [TimeZoneInfo.ConvertTime(DateTime, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)) 方法，以將時間從 UTC 轉換為原始時間的相關聯時區。</span><span class="sxs-lookup"><span data-stu-id="44902-115">Convert the time from UTC to the original time's associated time zone by calling the [TimeZoneInfo.ConvertTime(DateTime, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)) method.</span></span> 

## <a name="example"></a><span data-ttu-id="44902-116">範例</span><span class="sxs-lookup"><span data-stu-id="44902-116">Example</span></span>

<span data-ttu-id="44902-117">下列範例將兩個小時三十分鐘新增至 2008 年 3 月 9 日凌晨 1:30</span><span class="sxs-lookup"><span data-stu-id="44902-117">The following example adds two hours and thirty minutes to March 9, 2008, at 1:30 A.M.</span></span> <span data-ttu-id="44902-118">中央標準時區。</span><span class="sxs-lookup"><span data-stu-id="44902-118">Central Standard Time.</span></span> <span data-ttu-id="44902-119">時區轉換為日光節約時間會在三十分鐘後，也就是 2008 年 3 月 9 日</span><span class="sxs-lookup"><span data-stu-id="44902-119">The time zone's transition to daylight saving time occurs thirty minutes later, at 2:00 A.M.</span></span> <span data-ttu-id="44902-120">凌晨 2:00 發生。</span><span class="sxs-lookup"><span data-stu-id="44902-120">on March 9, 2008.</span></span> <span data-ttu-id="44902-121">由於本範例依照上一節所列的四個步驟進行，因此會正確回報產生的時間 2008 年 3 月 9 日</span><span class="sxs-lookup"><span data-stu-id="44902-121">Because the example follows the four steps listed in the previous section, it correctly reports the resulting time as 5:00 A.M.</span></span> <span data-ttu-id="44902-122">凌晨 5:00。</span><span class="sxs-lookup"><span data-stu-id="44902-122">on March 9, 2008.</span></span> 

```csharp
using System;

public struct TimeZoneTime
{
   public TimeZoneInfo TimeZone;
   public DateTimeOffset Time;

   public TimeZoneTime(TimeZoneInfo tz, DateTimeOffset time)
   {
      if (tz == null) 
         throw new ArgumentNullException("The time zone cannot be a null reference.");

      this.TimeZone = tz;
      this.Time = time;   
   }

   public TimeZoneTime AddTime(TimeSpan interval)
   {
      // Convert time to UTC
      DateTimeOffset utcTime = TimeZoneInfo.ConvertTime(this.Time, TimeZoneInfo.Utc);      
      // Add time interval to time
      utcTime = utcTime.Add(interval);
      // Convert time back to time in time zone
      return new TimeZoneTime(this.TimeZone, TimeZoneInfo.ConvertTime(utcTime, this.TimeZone));
   }
}

public class TimeArithmetic
{
   public const string tzName = "Central Standard Time";

   public static void Main()
   {
      try
      {
         TimeZoneTime cstTime1, cstTime2;

         TimeZoneInfo cst = TimeZoneInfo.FindSystemTimeZoneById(tzName);
         DateTime time1 = new DateTime(2008, 3, 9, 1, 30, 0);          
         TimeSpan twoAndAHalfHours = new TimeSpan(2, 30, 0);

         cstTime1 = new TimeZoneTime(cst, 
                        new DateTimeOffset(time1, cst.GetUtcOffset(time1)));
         cstTime2 = cstTime1.AddTime(twoAndAHalfHours);
         Console.WriteLine("{0} + {1} hours = {2}", cstTime1.Time, 
                                                    twoAndAHalfHours.ToString(),  
                                                    cstTime2.Time);
      }
      catch
      {
         Console.WriteLine("Unable to find {0}.", tzName);
      }
   }
}
```

```vb
Public Structure TimeZoneTime
   Public TimeZone As TimeZoneInfo
   Public Time As Date

   Public Sub New(tz As TimeZoneInfo, time As Date)
      If tz Is Nothing Then _
         Throw New ArgumentNullException("The time zone cannot be a null reference.")

      Me.TimeZone = tz
      Me.Time = time
   End Sub

   Public Function AddTime(interval As TimeSpan) As TimeZoneTime
      ' Convert time to UTC
      Dim utcTime As DateTime = TimeZoneInfo.ConvertTimeToUtc(Me.Time, _
                                                              Me.TimeZone)      
      ' Add time interval to time
      utcTime = utcTime.Add(interval)
      ' Convert time back to time in time zone
      Return New TimeZoneTime(Me.TimeZone, TimeZoneInfo.ConvertTime(utcTime, _
                              TimeZoneInfo.Utc, Me.TimeZone))
   End Function
End Structure

Module TimeArithmetic
   Public Const tzName As String = "Central Standard Time"

   Public Sub Main()
      Try
         Dim cstTime1, cstTime2 As TimeZoneTime

         Dim cst As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById(tzName)
         Dim time1 As Date = #03/09/2008 1:30AM#
         Dim twoAndAHalfHours As New TimeSpan(2, 30, 0)

         cstTime1 = New TimeZoneTime(cst, time1)
         cstTime2 = cstTime1.AddTime(twoAndAHalfHours)

         Console.WriteLine("{0} + {1} hours = {2}", cstTime1.Time, _
                                                    twoAndAHalfHours.ToString(), _ 
                                                    cstTime2.Time)  
      Catch
         Console.WriteLine("Unable to find {0}.", tzName)
      End Try   
   End Sub   
End Module
```

<span data-ttu-id="44902-123">請注意，如果這個加法只會對 [DateTimeOffset](xref:System.DateTimeOffset) 值執行，而不需要先將它轉換為 UTC，則結果會反映正確時間點，但其位移不會反映該時間之指定時區的位移。</span><span class="sxs-lookup"><span data-stu-id="44902-123">Note that if this addition is simply performed on the [DateTimeOffset](xref:System.DateTimeOffset) value without first converting it to UTC, the result reflects the correct point in time but its offset does not reflect that of the designated time zone for that time.</span></span> 

<span data-ttu-id="44902-124">[DateTimeOffset](xref:System.DateTimeOffset) 值會與任何其可能所屬的時區解除關聯。</span><span class="sxs-lookup"><span data-stu-id="44902-124">[DateTimeOffset](xref:System.DateTimeOffset) values are disassociated from any time zone to which they might belong.</span></span> <span data-ttu-id="44902-125">若要透過自動套用時區調整規則來執行日期和時間運算，則必須立即識別任何日期和時間值所屬的時區。</span><span class="sxs-lookup"><span data-stu-id="44902-125">To perform date and time arithmetic in a way that automatically applies a time zone's adjustment rules, the time zone to which any date and time value belongs must be immediately identifiable.</span></span> <span data-ttu-id="44902-126">這表示日期和時間及其相關聯時區必須緊密結合。</span><span class="sxs-lookup"><span data-stu-id="44902-126">This means that a date and time and its associated time zone must be tightly coupled.</span></span> <span data-ttu-id="44902-127">有幾個方式可做到這點，包括下列各項︰</span><span class="sxs-lookup"><span data-stu-id="44902-127">There are several ways to do this, which include the following:</span></span>

* <span data-ttu-id="44902-128">假設應用程式中使用的所有時間都是屬於特定時區。</span><span class="sxs-lookup"><span data-stu-id="44902-128">Assume that all times used in an application belong to a particular time zone.</span></span> <span data-ttu-id="44902-129">雖然適用於某些情況，但是這種方式提供的彈性有限，可攜性也可能有限。</span><span class="sxs-lookup"><span data-stu-id="44902-129">Although appropriate in some cases, this approach offers limited flexibility and possibly limited portability.</span></span>

* <span data-ttu-id="44902-130">定義一種類型，而這個類型透過將日期和時間與其相關聯時區都包含為類型的欄位來緊密結合兩者。</span><span class="sxs-lookup"><span data-stu-id="44902-130">Define a type that tightly couples a date and time with its associated time zone by including both as fields of the type.</span></span> <span data-ttu-id="44902-131">程式碼範例中使用這種方式，以定義將日期和時間以及時區儲存在兩個成員欄位中的結構。</span><span class="sxs-lookup"><span data-stu-id="44902-131">This approach is used in the code example, which defines a structure to store the date and time and the time zone in two member fields.</span></span>

## <a name="see-also"></a><span data-ttu-id="44902-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44902-132">See Also</span></span>

[<span data-ttu-id="44902-133">日期、時間及時區</span><span class="sxs-lookup"><span data-stu-id="44902-133">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="44902-134">使用日期與時間執行算術運算</span><span class="sxs-lookup"><span data-stu-id="44902-134">Performing arithmetic operations with dates and times</span></span>](performing-arithmetic-operations.md)

