---
title: "如何：具現化 TimeZoneInfo 物件"
description: "如何具現化 TimeZoneInfo 物件"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: bff137e5-d550-44c3-b460-b3f2dabd4035
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: f2584d446c92d2df2f6d74533ef07fe96888d36a
ms.contentlocale: zh-tw
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-instantiate-a-timezoneinfo-object"></a><span data-ttu-id="61be5-104">如何：具現化 TimeZoneInfo 物件</span><span class="sxs-lookup"><span data-stu-id="61be5-104">How to: instantiate a TimeZoneInfo object</span></span>

<span data-ttu-id="61be5-105">若要具現化 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件，最常見的方式是從作業系統擷取其相關資訊。</span><span class="sxs-lookup"><span data-stu-id="61be5-105">The most common way to instantiate a [TimeZoneInfo](xref:System.TimeZoneInfo) object is to retrieve information about it from the operating system.</span></span> <span data-ttu-id="61be5-106">本主題討論如何從本機系統具現化 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件。</span><span class="sxs-lookup"><span data-stu-id="61be5-106">This topic discusses how to instantiate a [TimeZoneInfo](xref:System.TimeZoneInfo) object from the local system.</span></span>

## <a name="to-instantiate-a-timezoneinfo-object"></a><span data-ttu-id="61be5-107">將 TimeZoneInfo 物件具現化</span><span class="sxs-lookup"><span data-stu-id="61be5-107">To instantiate a TimeZoneInfo Object</span></span>

1. <span data-ttu-id="61be5-108">宣告 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件。</span><span class="sxs-lookup"><span data-stu-id="61be5-108">Declare a [TimeZoneInfo](xref:System.TimeZoneInfo) object.</span></span>

2. <span data-ttu-id="61be5-109">呼叫 `static` (在 Visual Basic 中是 `Shared`) [TimeZoneInfo.FindSystemTimeZoneById](xref:System.TimeZoneInfo.FindSystemTimeZoneById(System.String)) 方法。</span><span class="sxs-lookup"><span data-stu-id="61be5-109">Call the `static` (`Shared` in Visual Basic) [TimeZoneInfo.FindSystemTimeZoneById](xref:System.TimeZoneInfo.FindSystemTimeZoneById(System.String)) method.</span></span>

3. <span data-ttu-id="61be5-110">處理方法所擲回的任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="61be5-110">Handle any exceptions thrown by the method.</span></span>

## <a name="example"></a><span data-ttu-id="61be5-111">範例</span><span class="sxs-lookup"><span data-stu-id="61be5-111">Example</span></span>

<span data-ttu-id="61be5-112">下列程式碼會擷取 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件，其代表美加東部標準時區，並顯示與當地時間對應的美加東部標準時間。</span><span class="sxs-lookup"><span data-stu-id="61be5-112">The following code retrieves a [TimeZoneInfo](xref:System.TimeZoneInfo) object that represents the Eastern Standard Time zone and displays the Eastern Standard time that corresponds to the local time.</span></span>

```csharp
DateTime timeNow = DateTime.Now;
try
{
   TimeZoneInfo easternZone = TimeZoneInfo.FindSystemTimeZoneById("Eastern Standard Time");
   DateTime easternTimeNow = TimeZoneInfo.ConvertTime(timeNow, TimeZoneInfo.Local, 
                                                   easternZone);
   Console.WriteLine("{0} {1} corresponds to {2} {3}.",
                     timeNow, 
                     TimeZoneInfo.Local.IsDaylightSavingTime(timeNow) ?
                               TimeZoneInfo.Local.DaylightName : 
                               TimeZoneInfo.Local.StandardName,
                     easternTimeNow, 
                     easternZone.IsDaylightSavingTime(easternTimeNow) ?
                                 easternZone.DaylightName : 
                                 easternZone.StandardName);
}
// Handle exception
//
// As an alternative to simply displaying an error message, an alternate Eastern
// Standard Time TimeZoneInfo object could be instantiated here either by restoring
// it from a serialized string or by providing the necessary data to the
// CreateCustomTimeZone method.
catch (InvalidTimeZoneException)
{
   Console.WriteLine("The Eastern Standard Time Zone contains invalid or missing data.");
}
catch (SecurityException)
{
   Console.WriteLine("The application lacks permission to read time zone information from the registry.");
}
catch (OutOfMemoryException)
{
   Console.WriteLine("Not enough memory is available to load information on the Eastern Standard Time zone.");
}
// If we weren't passing FindSystemTimeZoneById a literal string, we also 
// would handle an ArgumentNullException.
```

```vb
Dim timeNow As Date = Date.Now
Try
   Dim easternZone As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById("Eastern Standard Time")
   Dim easternTimeNow As Date = TimeZoneInfo.ConvertTime(timeNow, TimeZoneInfo.Local, easternZone)
   Console.WriteLine("{0} {1} corresponds to {2} {3}.", _
                     timeNow, _
                     IIf(TimeZoneInfo.Local.IsDaylightSavingTime(timeNow), _
                         TimeZoneInfo.Local.DaylightName, TimeZoneInfo.Local.StandardName), _
                     easternTimeNow, _
                     IIf(easternZone.IsDaylightSavingTime(easternTimeNow), _
                         easternZone.DaylightName, easternZone.StandardName))
' Handle exception
'
' As an alternative to simply displaying an error message, an alternate Eastern
' Standard Time TimeZoneInfo object could be instantiated here either by restoring
' it from a serialized string or by providing the necessary data to the
' CreateCustomTimeZone method.
Catch e As InvalidTimeZoneException
   Console.WriteLine("The Eastern Standard Time Zone contains invalid or missing data.")   
Catch e As SecurityException
   Console.WriteLine("The application lacks permission to read time zone information from the registry.")
Catch e As OutOfMemoryException
   Console.WriteLine("Not enough memory is available to load information on the Eastern Standard Time zone.")
' If we weren't passing FindSystemTimeZoneById a literal string, we also 
' would handle an ArgumentNullException.
End
``` 

<span data-ttu-id="61be5-113">[TimeZoneInfo.FindSystemTimeZoneById](xref:System.TimeZoneInfo.FindSystemTimeZoneById(System.String)) 方法的單一參數是您想要擷取之時區的識別項，其對應至物件的 [TimeZoneInfo.Id](xref:System.TimeZoneInfo.Id) 屬性。</span><span class="sxs-lookup"><span data-stu-id="61be5-113">The [TimeZoneInfo.FindSystemTimeZoneById](xref:System.TimeZoneInfo.FindSystemTimeZoneById(System.String)) method's single parameter is the identifier of the time zone that you want to retrieve, which corresponds to the object's [TimeZoneInfo.Id](xref:System.TimeZoneInfo.Id) property.</span></span> <span data-ttu-id="61be5-114">時區識別項是唯一識別時區的索引鍵欄位。</span><span class="sxs-lookup"><span data-stu-id="61be5-114">The time zone identifier is a key field that uniquely identifies the time zone.</span></span> <span data-ttu-id="61be5-115">雖然大部分的索引鍵相對較短，但時區識別項相較之下就很長。</span><span class="sxs-lookup"><span data-stu-id="61be5-115">While most keys are relatively short, the time zone identifier is comparatively long.</span></span> <span data-ttu-id="61be5-116">在大部分情況下，其值會對應到 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件的 [StandardName](xref:System.TimeZoneInfo.StandardName) 屬性，用來提供時區標準時間的名稱。</span><span class="sxs-lookup"><span data-stu-id="61be5-116">In most cases, its value corresponds to the [StandardName](xref:System.TimeZoneInfo.StandardName) property of a [TimeZoneInfo](xref:System.TimeZoneInfo) object, which is used to provide the name of the time zone's standard time.</span></span> <span data-ttu-id="61be5-117">不過仍有例外狀況。</span><span class="sxs-lookup"><span data-stu-id="61be5-117">However, there are exceptions.</span></span> <span data-ttu-id="61be5-118">若要確定您提供了有效的識別項，最好的方法是列舉系統上可用的時區，並記下存在於其之上的時區識別項。</span><span class="sxs-lookup"><span data-stu-id="61be5-118">The best way to make sure that you supply a valid identifier is to enumerate the time zones available on your system and note the identifiers of the time zones present on them.</span></span> <span data-ttu-id="61be5-119">如需說明，請參閱[如何：列舉電腦上展示的時區](enumerate-time-zones.md)。</span><span class="sxs-lookup"><span data-stu-id="61be5-119">For an illustration, see [How to: enumerate time zones present on a computer](enumerate-time-zones.md).</span></span> <span data-ttu-id="61be5-120">[尋找定義於本機系統的時區](finding-the-time-zones-on-local-system.md)主題同時包含所選取的時區識別碼的清單。</span><span class="sxs-lookup"><span data-stu-id="61be5-120">The [Finding the time zones defined on a local system](finding-the-time-zones-on-local-system.md) topic also contains a list of selected time zone identifiers.</span></span>

<span data-ttu-id="61be5-121">如果找到時區，此方法會傳回其 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件。</span><span class="sxs-lookup"><span data-stu-id="61be5-121">If the time zone is found, the method returns its [TimeZoneInfo](xref:System.TimeZoneInfo) object.</span></span> <span data-ttu-id="61be5-122">如果找到時區，但其資料已損毀或不完整，則方法會擲回 [InvalidTimeZoneException](xref:System.InvalidTimeZoneException)。</span><span class="sxs-lookup"><span data-stu-id="61be5-122">If the time zone is found but its data is corrupted or incomplete, the method throws an [InvalidTimeZoneException](xref:System.InvalidTimeZoneException).</span></span> 

## <a name="see-also"></a><span data-ttu-id="61be5-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61be5-123">See Also</span></span>

[<span data-ttu-id="61be5-124">日期、時間及時區</span><span class="sxs-lookup"><span data-stu-id="61be5-124">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="61be5-125">尋找本機系統上定義的時區</span><span class="sxs-lookup"><span data-stu-id="61be5-125">Finding the time zones defined on a local system</span></span>](finding-the-time-zones-on-local-system.md)
