---
title: "如何：存取預先定義的 UTC 和當地時區物件"
description: "如何：存取預先定義的 UTC 和當地時區物件"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/11/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 13454d47-d957-421b-9ecd-940058b8835e
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: fcc48e40cdad25c6142dbc3a86513b816378fa4b
ms.contentlocale: zh-tw
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="d797a-104">如何：存取預先定義的 UTC 和當地時區物件</span><span class="sxs-lookup"><span data-stu-id="d797a-104">How to: access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="d797a-105">[System.TimeZoneInfo](xref:System.TimeZoneInfo) 類別提供兩個屬性︰`Utc` 和 `Local`，以將預先定義的時區物件存取權授與您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d797a-105">The [System.TimeZoneInfo](xref:System.TimeZoneInfo) class provides two properties, `Utc` and `Local`, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="d797a-106">本主題討論如何存取這些屬性所傳回的 `TimeZoneInfo` 物件。</span><span class="sxs-lookup"><span data-stu-id="d797a-106">This topic discusses how to access the `TimeZoneInfo` objects returned by those properties.</span></span>

## <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="d797a-107">存取國際標準時間 (UTC) TimeZoneInfo 物件</span><span class="sxs-lookup"><span data-stu-id="d797a-107">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="d797a-108">使用**靜態** (在 Visual Basic 中為**共用**) [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) 屬性來存取國際標準時間。</span><span class="sxs-lookup"><span data-stu-id="d797a-108">Use the **static** (**Shared** in Visual Basic) [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="d797a-109">繼續透過 [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) 屬性存取國際標準時間，而不是指派屬性傳回給物件變數的 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件。</span><span class="sxs-lookup"><span data-stu-id="d797a-109">Rather than assigning the [TimeZoneInfo](xref:System.TimeZoneInfo) object returned by the property to an object variable, continue to access Coordinated Universal Time through the [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) property.</span></span>


## <a name="to-access-the-local-time-zone"></a><span data-ttu-id="d797a-110">存取當地時區</span><span class="sxs-lookup"><span data-stu-id="d797a-110">To access the local time zone</span></span>

1. <span data-ttu-id="d797a-111">使用**靜態** (在 Visual Basic 中為**共用**) [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) 屬性來存取當地系統時區。</span><span class="sxs-lookup"><span data-stu-id="d797a-111">Use the **static** (**Shared** in Visual Basic) [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) property to access the local system time zone.</span></span>

2. <span data-ttu-id="d797a-112">繼續透過 [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) 屬性存取當地時區，而不是指派屬性傳回給物件變數的 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件。</span><span class="sxs-lookup"><span data-stu-id="d797a-112">Rather than assigning the [TimeZoneInfo](xref:System.TimeZoneInfo) object returned by the property to an object variable, continue to access the local time zone through the [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) property.</span></span>

## <a name="example"></a><span data-ttu-id="d797a-113">範例</span><span class="sxs-lookup"><span data-stu-id="d797a-113">Example</span></span>

<span data-ttu-id="d797a-114">下列程式碼會使用 [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) 和 [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) 屬性轉換美國及加拿大東部標準時區的時間，以及對主控台顯示時區名稱。</span><span class="sxs-lookup"><span data-stu-id="d797a-114">The following code uses the [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) and [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

```csharp
// Create Eastern Standard Time value and TimeZoneInfo object      
DateTime estTime = new DateTime(2007, 1, 1, 00, 00, 00);
string timeZoneName = "Eastern Standard Time";
try
{
   TimeZoneInfo est = TimeZoneInfo.FindSystemTimeZoneById(timeZoneName);

   // Convert EST to local time
   DateTime localTime = TimeZoneInfo.ConvertTime(estTime, est, TimeZoneInfo.Local);
   Console.WriteLine("At {0} {1}, the local time is {2} {3}.", 
           estTime, 
           est, 
           localTime, 
           TimeZoneInfo.Local.IsDaylightSavingTime(localTime) ?
                     TimeZoneInfo.Local.DaylightName : 
                     TimeZoneInfo.Local.StandardName);

   // Convert EST to UTC
   DateTime utcTime = TimeZoneInfo.ConvertTime(estTime, est, TimeZoneInfo.Utc);
   Console.WriteLine("At {0} {1}, the time is {2} {3}.", 
           estTime, 
           est, 
           utcTime, 
           TimeZoneInfo.Utc.StandardName);
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("The {0} zone cannot be found in the registry.", 
                     timeZoneName);
}
catch (InvalidTimeZoneException)
{
   Console.WriteLine("The registry contains invalid data for the {0} zone.", 
                     timeZoneName);
}
```

```vb
' Create Eastern Standard Time value and TimeZoneInfo object      
Dim estTime As Date = #01/01/2007 00:00:00#
Dim timeZoneName As String = "Eastern Standard Time"
Try
   Dim est As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById(timeZoneName)

   ' Convert EST to local time
   Dim localTime As Date = TimeZoneInfo.ConvertTime(estTime, est, TimeZoneInfo.Local)
   Console.WriteLine("At {0} {1}, the local time is {2} {3}.", _
           estTime, _
           est, _
           localTime, _
           IIf(TimeZoneInfo.Local.IsDaylightSavingTime(localTime), _
               TimeZoneInfo.Local.DaylightName, _
               TimeZoneInfo.Local.StandardName))

   ' Convert EST to UTC
   Dim utcTime As Date = TimeZoneInfo.ConvertTime(estTime, est, TimeZoneInfo.Utc)
   Console.WriteLine("At {0} {1}, the time is {2} {3}.", _
           estTime, _
           est, _
           utcTime, _
           TimeZoneInfo.Utc.StandardName)
Catch e As TimeZoneNotFoundException
   Console.WriteLine("The {0} zone cannot be found in the registry.", _
                     timeZoneName)
Catch e As InvalidTimeZoneException
   Console.WriteLine("The registry contains invalid data for the {0} zone.", _
                     timeZoneName)
End Try
```

<span data-ttu-id="d797a-115">您應該一律透過 [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) 屬性存取當地時區，而不是將當地時區指派給 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件變數。</span><span class="sxs-lookup"><span data-stu-id="d797a-115">You should always access the local time zone through the [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) property rather than assigning the local time zone to a [TimeZoneInfo](xref:System.TimeZoneInfo) object variable.</span></span> <span data-ttu-id="d797a-116">同樣地，您應該一律透過 [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) 屬性存取國際標準時間，而不是將 UTC 時區指派給 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件變數。</span><span class="sxs-lookup"><span data-stu-id="d797a-116">Similarly, you should always access Coordinated Universal Time through the [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) property rather than assigning the UTC zone to a [TimeZoneInfo](xref:System.TimeZoneInfo) object variable.</span></span> <span data-ttu-id="d797a-117">這防止透過外部方法讓 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件變數失效。</span><span class="sxs-lookup"><span data-stu-id="d797a-117">This prevents the [TimeZoneInfo](xref:System.TimeZoneInfo) object variable from being invalidated by an external method.</span></span>


## <a name="see-also"></a><span data-ttu-id="d797a-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d797a-118">See Also</span></span>

[<span data-ttu-id="d797a-119">日期、時間及時區</span><span class="sxs-lookup"><span data-stu-id="d797a-119">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="d797a-120">尋找本機系統上定義的時區</span><span class="sxs-lookup"><span data-stu-id="d797a-120">Finding the time zones defined on a local system</span></span>](finding-the-time-zones-on-local-system.md)

