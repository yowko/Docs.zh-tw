---
title: "如何：具現化 TimeZoneInfo 物件"
description: "如何具現化 TimeZoneInfo 物件"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bff137e5-d550-44c3-b460-b3f2dabd4035
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: 1c619cf6bd150e009367b43d1d83fa1713ec2690

---

# <a name="how-to-instantiate-a-timezoneinfo-object"></a>如何：具現化 TimeZoneInfo 物件

若要具現化 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件，最常見的方式是從作業系統擷取其相關資訊。 本主題討論如何從本機系統具現化 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件。

## <a name="to-instantiate-a-timezoneinfo-object"></a>將 TimeZoneInfo 物件具現化

1. 宣告 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件。

2. 呼叫 `static` (在 Visual Basic 中是 `Shared`) [TimeZoneInfo.FindSystemTimeZoneById](xref:System.TimeZoneInfo.FindSystemTimeZoneById(System.String)) 方法。

3. 處理方法所擲回的任何例外狀況。

## <a name="example"></a>範例

下列程式碼會擷取 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件，其代表美加東部標準時區，並顯示與當地時間對應的美加東部標準時間。

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

[TimeZoneInfo.FindSystemTimeZoneById](xref:System.TimeZoneInfo.FindSystemTimeZoneById(System.String)) 方法的單一參數是您想要擷取之時區的識別項，其對應至物件的 [TimeZoneInfo.Id](xref:System.TimeZoneInfo.Id) 屬性。 時區識別項是唯一識別時區的索引鍵欄位。 雖然大部分的索引鍵相對較短，但時區識別項相較之下就很長。 在大部分情況下，其值會對應到 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件的 [StandardName](xref:System.TimeZoneInfo.StandardName) 屬性，用來提供時區標準時間的名稱。 不過仍有例外狀況。 若要確定您提供了有效的識別項，最好的方法是列舉系統上可用的時區，並記下存在於其之上的時區識別項。 如需說明，請參閱[如何：列舉電腦上展示的時區](enumerate-time-zones.md)。 [尋找定義於本機系統的時區](finding-the-time-zones-on-local-system.md)主題同時包含所選取的時區識別碼的清單。

如果找到時區，此方法會傳回其 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件。 如果找到時區，但其資料已損毀或不完整，則方法會擲回 [InvalidTimeZoneException](xref:System.InvalidTimeZoneException)。 

## <a name="see-also"></a>另請參閱

[日期、時間及時區](index.md)

[尋找本機系統上定義的時區](finding-the-time-zones-on-local-system.md)


<!--HONumber=Nov16_HO3-->


