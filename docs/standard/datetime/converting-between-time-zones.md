---
title: "在各時區間轉換時間"
description: "在各時區間轉換時間"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bf8f74e6-e7f2-4c2a-a04c-57db0e28dd36
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: c2baa48c3b79dfbc5d39652cc57fe015a2313d6e

---

# <a name="converting-times-between-time-zones"></a>在各時區間轉換時間

對於使用日期和時間來處理時區差異的任何應用程式，它會變得越來越重要。 應用程式無法再假設所有時間都是以當地時間表示，這是可從 [System.DateTime](xref:System.DateTime) 結構取得的時間。 例如，顯示美國東部目前時間的網頁對東亞地區的客戶不具公信力。 本主題說明如何將時間從某個時區轉換為另一個時區，以及如何轉換具有有限時區感知的 [System.DateTimeOffset](xref:System.DateTimeOffset) 值。

## <a name="converting-to-coordinated-universal-time"></a>轉換為國際標準時間

國際標準時間 (UTC) 是高精確度且不可部分完成的時間標準。 全世界的時區都會表示為與 UTC 的正或負位移。 因此，UTC 提供一種無時區或時區中性時間。 跨電腦的日期和時間可攜性十分重要時，建議使用 UTC 時間。 將個別時區轉換為 UTC 可輕鬆地比較時間。

> [!NOTE]
> 您也可以序列化 [DateTimeOffset](xref:System.DateTimeOffset) 結構來明確代表單一時間點。 因為 [DateTimeOffset](xref:System.DateTimeOffset) 物件會儲存日期和時間值以及其與 UTC 的位移，所以它們一律代表與 UTC 之關聯性中的特定時間點。

將時間轉換為 UTC 的最簡單方式是呼叫 `static` (在 Visual Basic 中為 `Shared`) [TimeZoneInfo.ConvertTimeToUtc(DateTime)](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) 方法。 

> [!IMPORTANT]
> .NET Core 目前未提供 `TimeZoneInfo.ConvertTimeToUtc(DateTime)` 方法。 

方法所執行的確切轉換取決於 `DateTime` 參數的 [Kind](xref:System.DateTime.Kind) 屬性值 (如下表所示)。

[DateTime.Kind](xref:System.DateTimeKind) 屬性 | 轉換
---------------------------------------------------------------------------------------------- | ----------
[DateTimeKind.Local](xref:System.DateTimeKind.Local) | 將當地時間轉換為 UTC。
[DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) | 假設 `DateTime` 參數是當地時間，並將當地時間轉換為 UTC。
[DateTimeKind.Utc](xref:System.DateTimeKind.Utc) | 傳回未變更的 `DateTime` 參數。

下列程式碼會將目前當地時間轉換為 UTC，並將結果顯示到主控台。

```csharp
DateTime dateNow = DateTime.Now;
Console.WriteLine("The date and time are {0} UTC.", 
                   TimeZoneInfo.ConvertTimeToUtc(dateNow));
```

```vb
Dim dateNow As Date = Date.Now      
Console.WriteLine("The date and time are {0} UTC.", _
                  TimeZoneInfo.ConvertTimeToUtc(dateNow))
```

> [!NOTE]
>[TimeZoneInfo.ConvertTimeToUtc(DateTime)](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) 方法不一定會產生與 [TimeZone.ToUniversalTime](https://msdn.microsoft.com/en-us/library/System.TimeZone.ToUniversalTime(v=vs.110).aspx) 和 [DateTime.ToUniversalTime](xref:System.DateTime.ToUniversalTime) 方法相同的結果。 如果主機系統的當地時區包含多個調整規則，則 [TimeZoneInfo.ConvertTimeToUtc(DateTime)](https://msdn.microsoft.com/en-us/library/System.TimeZone.ConvertTimeToUtc(v=vs.110).aspx) 會將適當的規則套用至特定日期和時間。 另兩種方法一律會套用最新的調整規則。

如果日期和時間值不代表當地時間或 UTC，則 [ToUniversalTime](https://msdn.microsoft.com/en-us/library/System.TimeZone.ToUniversalTime(v=vs.110).aspx) 方法可能會傳回錯誤結果。 不過，您可以使用 [TimeZoneInfo.ConvertTimeToUtc](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) 方法轉換所指定時區的日期和時間。 如需擷取代表目的地時區之 TimeZoneInfo 物件的詳細資訊，請參閱[尋找本機系統上所定義的時區](finding-the-time-zones-on-local-system.md)。 下列程式碼使用 [TimeZoneInfo.ConvertTimeToUtc](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) 方法將美加東部標準時間轉換為 UTC。

```csharp
DateTime easternTime = new DateTime(2007, 01, 02, 12, 16, 00);
string easternZoneId = "Eastern Standard Time";
try
{
   TimeZoneInfo easternZone = TimeZoneInfo.FindSystemTimeZoneById(easternZoneId);
   Console.WriteLine("The date and time are {0} UTC.", 
                     TimeZoneInfo.ConvertTimeToUtc(easternTime, easternZone));
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("Unable to find the {0} zone in the registry.", 
                     easternZoneId);
}                           
catch (InvalidTimeZoneException)
{
   Console.WriteLine("Registry data on the {0} zone has been corrupted.", 
                     easternZoneId);
}
```

```vb
Dim easternTime As New Date(2007, 01, 02, 12, 16, 00)
Dim easternZoneId As String = "Eastern Standard Time"
Try
   Dim easternZone As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById(easternZoneId)
   Console.WriteLine("The date and time are {0} UTC.", _ 
                     TimeZoneInfo.ConvertTimeToUtc(easternTime, easternZone))
Catch e As TimeZoneNotFoundException
   Console.WriteLine("Unable to find the {0} zone in the registry.", _
                     easternZoneId)
Catch e As InvalidTimeZoneException
   Console.WriteLine("Registry data on the {0} zone has been corrupted.", _ 
                     easternZoneId)
End Try    
```

請注意，如果 [DateTime](xref:System.DateTime) 物件的 [Kind](xref:System.DateTimeKind) 屬性和時區不相符，則這個方法會擲回 [ArgumentException](xref:System.ArgumentException)。 如果 Kind 屬性為 [DateTimeKind.Local](xref:System.DateTimeKind.Local) 但 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件不代表當地時區，或 Kind 屬性為 [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) 但 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件不等於 [DateTimeKind.Utc](xref:System.DateTimeKind.Utc)，則會不相符。

所有這些方法都會採用 [DateTime](xref:System.DateTime) 值作為參數，並傳回 [DateTime](xref:System.DateTime) 值。 對於 [DateTimeOffset](xref:System.DateTimeOffset) 值，[DateTimeOffset](xref:System.DateTimeOffset) 結構具有 [ToUniversalTime](xref:System.DateTimeOffset.ToUniversalTime) 執行個體方法，以將目前執行個體的日期和時間轉換為 UTC。 下列範例呼叫 [ToUniversalTime](xref:System.DateTimeOffset.ToUniversalTime) 方法，以將當地時間和數個其他時間轉換為國際標準時間 (UTC)。

```csharp
DateTimeOffset localTime, otherTime, universalTime;

// Define local time in local time zone
localTime = new DateTimeOffset(new DateTime(2007, 6, 15, 12, 0, 0));
Console.WriteLine("Local time: {0}", localTime);
Console.WriteLine();

// Convert local time to offset 0 and assign to otherTime
otherTime = localTime.ToOffset(TimeSpan.Zero);
Console.WriteLine("Other time: {0}", otherTime);
Console.WriteLine("{0} = {1}: {2}", 
                  localTime, otherTime, 
                  localTime.Equals(otherTime));
Console.WriteLine("{0} exactly equals {1}: {2}", 
                  localTime, otherTime, 
                  localTime.EqualsExact(otherTime));
Console.WriteLine();

// Convert other time to UTC
universalTime = localTime.ToUniversalTime(); 
Console.WriteLine("Universal time: {0}", universalTime);
Console.WriteLine("{0} = {1}: {2}", 
                  otherTime, universalTime, 
                  universalTime.Equals(otherTime));
Console.WriteLine("{0} exactly equals {1}: {2}", 
                  otherTime, universalTime, 
                  universalTime.EqualsExact(otherTime));
Console.WriteLine();
// The example produces the following output to the console:
//    Local time: 6/15/2007 12:00:00 PM -07:00
//    
//    Other time: 6/15/2007 7:00:00 PM +00:00
//    6/15/2007 12:00:00 PM -07:00 = 6/15/2007 7:00:00 PM +00:00: True
//    6/15/2007 12:00:00 PM -07:00 exactly equals 6/15/2007 7:00:00 PM +00:00: False
//    
//    Universal time: 6/15/2007 7:00:00 PM +00:00
//    6/15/2007 7:00:00 PM +00:00 = 6/15/2007 7:00:00 PM +00:00: True
//    6/15/2007 7:00:00 PM +00:00 exactly equals 6/15/2007 7:00:00 PM +00:00: True 
```

```vb
Dim localTime, otherTime, universalTime As DateTimeOffset

' Define local time in local time zone
localTime = New DateTimeOffset(#6/15/2007 12:00:00PM#)
Console.WriteLine("Local time: {0}", localTime)
Console.WriteLine()

' Convert local time to offset 0 and assign to otherTime
otherTime = localTime.ToOffset(TimeSpan.Zero)
Console.WriteLine("Other time: {0}", otherTime)
Console.WriteLine("{0} = {1}: {2}", _
                  localTime, otherTime, _
                  localTime.Equals(otherTime))
Console.WriteLine("{0} exactly equals {1}: {2}", _ 
                  localTime, otherTime, _
                  localTime.EqualsExact(otherTime))
Console.WriteLine()

' Convert other time to UTC
universalTime = localTime.ToUniversalTime() 
Console.WriteLine("Universal time: {0}", universalTime)
Console.WriteLine("{0} = {1}: {2}", _
                  otherTime, universalTime, _ 
                  universalTime.Equals(otherTime))
Console.WriteLine("{0} exactly equals {1}: {2}", _ 
                  otherTime, universalTime, _
                  universalTime.EqualsExact(otherTime))
Console.WriteLine()
' The example produces the following output to the console:
'    Local time: 6/15/2007 12:00:00 PM -07:00
'    
'    Other time: 6/15/2007 7:00:00 PM +00:00
'    6/15/2007 12:00:00 PM -07:00 = 6/15/2007 7:00:00 PM +00:00: True
'    6/15/2007 12:00:00 PM -07:00 exactly equals 6/15/2007 7:00:00 PM +00:00: False
'    
'    Universal time: 6/15/2007 7:00:00 PM +00:00
'    6/15/2007 7:00:00 PM +00:00 = 6/15/2007 7:00:00 PM +00:00: True
'    6/15/2007 7:00:00 PM +00:00 exactly equals 6/15/2007 7:00:00 PM +00:00: True 
```

## <a name="converting-utc-to-a-designated-time-zone"></a>將 UTC 轉換為指定的時區

若要將 UTC 轉換為當地時間，請參閱後續的[將 UTC 轉換為當地時間](#converting-utc-to-local-time)一節。 

若要將 UTC 轉換為任何您所指定時區的時間，請呼叫 [ConvertTimeFromUtc](https://msdn.microsoft.com/en-us/library/System.TimeZoneInfo.converttimefromutc(v=vs.110).aspx) 方法。 

> [!IMPORTANT]
> .NET Core 目前未提供 `TimeZoneInfo.ConvertTimeFromUtc' 方法。 

這個方法採用兩個參數：

* 要轉換的 UTC。 這必須是 [Kind](xref:System.DateTime.Kind) 屬性設定為 [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) 或 [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) 的 [DateTime](xref:System.DateTime) 值。 

* 要將 UTC 轉換為的時區。 

下列程式碼會將 UTC 轉換為美加中部標準時間。

```csharp
DateTime timeUtc = DateTime.UtcNow;
try
{
   TimeZoneInfo cstZone = TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time");
   DateTime cstTime = TimeZoneInfo.ConvertTimeFromUtc(timeUtc, cstZone);
   Console.WriteLine("The date and time are {0} {1}.", 
                     cstTime, 
                     cstZone.IsDaylightSavingTime(cstTime) ?
                             cstZone.DaylightName : cstZone.StandardName);
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("The registry does not define the Central Standard Time zone.");
}                           
catch (InvalidTimeZoneException)
{
   Console.WriteLine("Registry data on the Central Standard Time zone has been corrupted.");
}
```

```vb
Dim timeUtc As Date = Date.UtcNow
Try
   Dim cstZone As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time")
   Dim cstTime As Date = TimeZoneInfo.ConvertTimeFromUtc(timeUtc, cstZone)
   Console.WriteLine("The date and time are {0} {1}.", _
                     cstTime, _
                     IIf(cstZone.IsDaylightSavingTime(cstTime), _
                         cstZone.DaylightName, cstZone.StandardName))
Catch e As TimeZoneNotFoundException
   Console.WriteLine("The registry does not define the Central Standard Time zone.")
Catch e As InvalidTimeZoneException
   Console.WriteLine("Registry data on the Central Standard Time zone has been corrupted.")
End Try
``` 

## <a name="converting-utc-to-local-time"></a>將 UTC 轉換為當地時間

若要將 UTC 轉換為當地時間，請呼叫所想要轉換時間之 [DateTime](xref:System.DateTime) 物件的 [DateTime.ToLocalTime](xref:System.DateTime) 方法。 方法的確切行為取決於物件的 [Kind](xref:System.DateTime.Kind) 屬性值 (如下表所示)。

[DateTime.Kind](xref:System.DateTimeKind) 屬性 | 轉換
---------------------------------------------------------------------------------------------- | ----------
[DateTimeKind.Local](xref:System.DateTimeKind.Local) | 傳回未變更的 [DateTime](xref:System.DateTime) 值。
[DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) | 假設 [DateTime](xref:System.DateTime) 值為 UTC，並將 UTC 轉換為當地時間。
[DateTimeKind.Utc](xref:System.DateTimeKind.Utc) | 將 [DateTime](xref:System.DateTime) 值轉換為當地時間。

## <a name="converting-between-any-two-time-zones"></a>在兩個時區之間轉換

您可以使用靜態 [TimeZoneInfo.ConvertTime](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)) 方法在任兩個時區之間進行轉換。 此方法的參數是要轉換的 [DateTime](xref:System.DateTime) 值、代表日期和時間值時區的 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件，以及代表將日期和時間值轉換成之時區的 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件。

此方法需要下列兩者彼此對應：要轉換之日期和時間值的 [Kind](xref:System.DateTime.Kind) 屬性，以及代表其時區的 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件或時區識別碼。 否則，會擲回 [ArgumentException](xref:System.ArgumentException)。 例如，如果日期和時間值的 [Kind](xref:System.DateTime.Kind) 屬性是 [DateTimeKind.Local](xref:System.DateTimeKind.Local)，則會在以參數形式傳遞給方法的 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件不等於 [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) 時擲回例外狀況。 如果以參數形式傳遞給方法的識別碼不等於 [TimeZoneInfo.Id](xref:System.TimeZoneInfo.Id)，也會擲回例外狀況。

下列範例使用 [ConvertTime](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)) 方法，將夏威夷標準時間轉換為當地時間。

```csharp
DateTime hwTime = new DateTime(2007, 02, 01, 08, 00, 00);
try
{
   TimeZoneInfo hwZone = TimeZoneInfo.FindSystemTimeZoneById("Hawaiian Standard Time");
   Console.WriteLine("{0} {1} is {2} local time.", 
           hwTime, 
           hwZone.IsDaylightSavingTime(hwTime) ? hwZone.DaylightName : hwZone.StandardName, 
           TimeZoneInfo.ConvertTime(hwTime, hwZone, TimeZoneInfo.Local));
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("The registry does not define the Hawaiian Standard Time zone.");
}                           
catch (InvalidTimeZoneException)
{
   Console.WriteLine("Registry data on the Hawaiian STandard Time zone has been corrupted.");
}
```

```vb
Dim hwTime As Date = #2/01/2007 8:00:00 AM#
Try
   Dim hwZone As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById("Hawaiian Standard Time")
   Console.WriteLine("{0} {1} is {2} local time.", _
                     hwTime, _
                     IIf(hwZone.IsDaylightSavingTime(hwTime), hwZone.DaylightName, hwZone.StandardName), _
                     TimeZoneInfo.ConvertTime(hwTime, hwZone, TimeZoneInfo.Local))
Catch e As TimeZoneNotFoundException
   Console.WriteLine("The registry does not define the Hawaiian Standard Time zone.")
Catch e As InvalidTimeZoneException
   Console.WriteLine("Registry data on the Hawaiian Standard Time zone has been corrupted.")
End Try
```

## <a name="converting-datetimeoffset-values"></a>轉換 DateTimeOffset 值

[System.DateTimeOffset](xref:System.DateTimeOffset) 物件所代表的日期和時間值不是完全時區感知的，原因是該物件在具現化時與其時區解除關聯。 不過，在許多情況下，應用程式只需要根據與 UTC 的兩個不同位移來轉換日期和時間，而不是根據特定時區的時間。 若要執行這項轉換，您可以呼叫目前執行個體的 [ToOffset](xref:System.DateTimeOffset.ToOffset(System.TimeSpan)) 方法。 方法的單一參數是 [TimeSpan](xref:System.TimeSpan)，其代表方法要傳回之新日期和時間值的位移。  

例如，如果網頁使用者要求的日期和時間已知且序列化為字串 (格式為 MM/dd/yyyy hh:mm:ss zzzz)，則下列 `ReturnTimeOnServer` 方法會將這個日期和時間值轉換為 Web 伺服器上的時間和日期。

```csharp
public DateTimeOffset ReturnTimeOnServer(string clientString)
{
   string format = @"M/d/yyyy H:m:s zzz";
   TimeSpan serverOffset = TimeZoneInfo.Local.GetUtcOffset(DateTimeOffset.Now);

   try
   {      
      DateTimeOffset clientTime = DateTimeOffset.ParseExact(clientString, format, CultureInfo.InvariantCulture);
      DateTimeOffset serverTime = clientTime.ToOffset(serverOffset);
      return serverTime;
   }
   catch (FormatException)
   {
      return DateTimeOffset.MinValue;
   }
}
```

```vb
Public Function ReturnTimeOnServer(clientString As String) As DateTimeOffset
   Dim format As String = "M/d/yyyy H:m:s zzz"
   Dim serverOffset As TimeSpan = TimeZoneInfo.Local.GetUtcOffset(DateTimeOffset.Now)

   Try      
      Dim clientTime As DateTimeOffset = DateTimeOffset.ParseExact(clientString, format, CultureInfo.InvariantCulture)
      Dim serverTime As DateTimeOffset = clientTime.ToOffset(serverOffset)
      Return serverTime
   Catch e As FormatException
      Return DateTimeOffset.MinValue
   End Try    
End Function
```

如果將字串 "9/1/2007 5:32:07 -05:00" 傳遞給這個方法，代表時區中的日期和時間比 UTC 早五個小時，就會傳回 9/1/2007 3:32:07 AM -07:00，代表伺服器位於美國太平洋標準時區。

[TimeZoneInfo](xref:System.TimeZoneInfo) 類別也包含多載的 [TimeZoneInfo.ConvertTime(DateTimeOffset, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTimeOffset,System.TimeZoneInfo)) 方法，以執行與 [System.DateTimeOffset](xref:System.DateTimeOffset) 值的時區轉換。 方法的參數是 [System.DateTimeOffset](xref:System.DateTimeOffset) 值以及時間要轉換成之時區的參考。 方法呼叫會傳回 [System.DateTimeOffset](xref:System.DateTimeOffset) 值。 例如，可以如下重新撰寫前一個範例中的 `ReturnTimeOnServer` 方法，以呼叫 [ConvertTime(DateTimeOffset, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTimeOffset,System.TimeZoneInfo)) 方法。

```csharp
public DateTimeOffset ReturnTimeOnServer(string clientString)
{
   string format = @"M/d/yyyy H:m:s zzz";

   try
   {      
      DateTimeOffset clientTime = DateTimeOffset.ParseExact(clientString, format, 
                                  CultureInfo.InvariantCulture);
      DateTimeOffset serverTime = TimeZoneInfo.ConvertTime(clientTime, 
                                  TimeZoneInfo.Local);
      return serverTime;
   }
   catch (FormatException)
   {
      return DateTimeOffset.MinValue;
   }
}
```

```vb
Public Function ReturnTimeOnServer(clientString As String) As DateTimeOffset
   Dim format As String = "M/d/yyyy H:m:s zzz"

   Try      
      Dim clientTime As DateTimeOffset = DateTimeOffset.ParseExact(clientString, format, CultureInfo.InvariantCulture)
      Dim serverTime As DateTimeOffset = TimeZoneInfo.ConvertTime(clientTime, TimeZoneInfo.Local)
      Return serverTime
   Catch e As FormatException
      Return DateTimeOffset.MinValue
   End Try    
End Function
```

## <a name="see-also"></a>請參閱

[TimeZoneInfo](xref:System.TimeZoneInfo)

[日期、時間及時區](index.md)

[尋找本機系統上定義的時區](finding-the-time-zones-on-local-system.md)





<!--HONumber=Nov16_HO3-->


