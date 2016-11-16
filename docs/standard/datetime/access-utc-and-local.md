---
title: "如何：存取預先定義的 UTC 和當地時區物件"
description: "如何：存取預先定義的 UTC 和當地時區物件"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/11/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 13454d47-d957-421b-9ecd-940058b8835e
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: 865e41ca544e8931d0a7037310387e077d8a5547

---

# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>如何：存取預先定義的 UTC 和當地時區物件

[System.TimeZoneInfo](xref:System.TimeZoneInfo) 類別提供兩個屬性︰`Utc` 和 `Local`，以將預先定義的時區物件存取權授與您的程式碼。 本主題討論如何存取這些屬性所傳回的 `TimeZoneInfo` 物件。

## <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>存取國際標準時間 (UTC) TimeZoneInfo 物件

1. 使用**靜態** (在 Visual Basic 中為**共用**) [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) 屬性來存取國際標準時間。

2. 繼續透過 [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) 屬性存取國際標準時間，而不是指派屬性傳回給物件變數的 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件。


## <a name="to-access-the-local-time-zone"></a>存取當地時區

1. 使用**靜態** (在 Visual Basic 中為**共用**) [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) 屬性來存取當地系統時區。

2. 繼續透過 [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) 屬性存取當地時區，而不是指派屬性傳回給物件變數的 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件。

## <a name="example"></a>範例

下列程式碼會使用 [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) 和 [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) 屬性轉換美國及加拿大東部標準時區的時間，以及對主控台顯示時區名稱。

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

您應該一律透過 [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) 屬性存取當地時區，而不是將當地時區指派給 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件變數。 同樣地，您應該一律透過 [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) 屬性存取國際標準時間，而不是將 UTC 時區指派給 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件變數。 這防止透過外部方法讓 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件變數失效。


## <a name="see-also"></a>另請參閱

[日期、時間及時區](index.md)

[尋找本機系統上定義的時區](finding-the-time-zones-on-local-system.md)



<!--HONumber=Nov16_HO1-->


