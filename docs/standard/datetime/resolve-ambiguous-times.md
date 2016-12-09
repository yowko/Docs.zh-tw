---
title: "如何：解決不明確的時間"
description: "如何解決不明確的時間"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: e86050c6-d16d-405e-8bba-7205945c9a81
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: b31ea18cd7a7e32863f384cb279dc715fd62b3df

---

# <a name="how-to-resolve-ambiguous-times"></a>如何：解決不明確的時間

不明確的時間是指對應到多個國際標準時間 (UTC) 的時間。 發生時機是往回調整時鐘時間，例如從時區的日光節約時間轉換到其標準時間期間。 處理不明確的時間時，您可以執行下列其中一項：

* 假設如何將時間對應至 UTC。 例如，您可以假設不明確的時間一律是以時區的標準時間表示。

* 如果不明確的時間是使用者所輸入的資料項目，可交由使用者自行解決此不明確狀況。

本文示範如何在假設它代表時區標準時間的情況下解決不明確的時間。

## <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>將不明確的時間對應至時區標準時間

1. 呼叫 [System.TimeZoneInfo.IsAmbiguousTime(DateTime)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTime)) 或 [System.TimeZoneInfo.IsAmbiguousTime(DateTimeOffset)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTimeOffset)) 方法，以判斷時間是否不明確。

2. 如果是不明確的時間，請減去時區之 [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) 屬性所傳回 [TimeSpan](xref:System.TimeSpan) 物件的時間。

3. 呼叫 `static` (在 Visual Basic 中為 `Shared`) [SpecifyKind](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) 方法，以將 UTC 日期和時間值的 [Kind](xref:System.DateTime.Kind) 屬性設定為 [DateTimeKind.Utc](xref:System.DateTimeKind.Utc)。

## <a name="example"></a>範例

下列範例說明如何在假設不明確的 [DateTime](xref:System.DateTime) 代表當地時區標準時間的 UTC 的情況下，將其轉換為 UTC。 

```csharp
private DateTime ResolveAmbiguousTime(DateTime ambiguousTime)
{
   // Time is not ambiguous
   if (! TimeZoneInfo.Local.IsAmbiguousTime(ambiguousTime))
   { 
      return ambiguousTime; 
   }
   // Time is ambiguous
   else
   {
      DateTime utcTime = DateTime.SpecifyKind(ambiguousTime - TimeZoneInfo.Local.BaseUtcOffset, 
                                              DateTimeKind.Utc);      
      Console.WriteLine("{0} local time corresponds to {1} {2}.", 
                        ambiguousTime, utcTime, utcTime.Kind.ToString());
      return utcTime;            
   }   
}
```

```vb
Private Function ResolveAmbiguousTime(ambiguousTime As Date) As Date
   ' Time is not ambiguous
   If Not TimeZoneInfo.Local.IsAmbiguousTime(ambiguousTime) Then 
      Return TimeZoneInfo.ConvertTimeToUtc(ambiguousTime) 
   ' Time is ambiguous
   Else
      Dim utcTime As Date = DateTime.SpecifyKind(ambiguousTime - TimeZoneInfo.Local.BaseUtcOffset, DateTimeKind.Utc)      
      Console.WriteLine("{0} local time corresponds to {1} {2}.", ambiguousTime, utcTime, utcTime.Kind.ToString())
      Return utcTime            
   End If   
End Function
```

此範例包含名為 `ResolveAmbiguousTime` 的方法，可決定傳遞給它的 [DateTime](xref:System.DateTime) 值是否不明確。 如果值不明確，則方法會傳回代表對應 UTC 時間的 [DateTime](xref:System.DateTime) 值。 此方法會將當地時間減去當地時區的 [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) 屬性值，來處理這項轉換。 

一般而言，不明確時間的處理方式是呼叫 [GetAmbiguousTimeOffsets](xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets(System.DateTime)) 方法來擷取 [TimeSpan](xref:System.TimeSpan) 物件陣列，其中包含不明確時間的可能 UTC 位移。 不過，此範例會進行任意假設，即不明確的時間應該一律對應至時區標準時間。 [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) 屬性會傳回 UTC 與時區標準時間之間的位移。

## <a name="see-also"></a>另請參閱

[日期、時間及時區](index.md)

[如何：讓使用者解決不明確的時間](let-users-resolve-ambiguous-times.md)




<!--HONumber=Nov16_HO3-->


