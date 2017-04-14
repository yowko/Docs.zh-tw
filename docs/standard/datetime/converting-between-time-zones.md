---
title: "在各時區間轉換時間 | Microsoft Docs"
ms.custom: ""
ms.date: "04/10/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "轉換時間"
  - "本地時間轉換"
  - "時區 [.NET Framework], 轉換"
  - "時間 [.NET Framework], 轉換"
  - "UTC 時間, 轉換"
ms.assetid: a51e1a3b-c983-4320-b31a-1f9fa3cf824a
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# 在各時區間轉換時間
對於任何具有日期與時間功能的應用程式而言，處理不同時區的功能變得越來越重要。  應用程式已不能再假設，所有時間都可以顯示成 <xref:System.DateTime> 結構所提供的當地時間。  例如，網頁如果顯示美國的東部時間，對東亞地區的客戶而言就不具有公信力。  本主題說明如何將時間從一個時區轉換成另一個時區，以及如何轉換有限制時區感知的 <xref:System.DateTimeOffset> 值。  
  
## 轉換成 Coordinated Universal Time  
 Coordinated Universal Time \(UTC\) 是高度精確的原子時間標準。  全世界的時區都是以 UTC 的正\/負位移所表示的。  因此 UTC 是一種無時區，或中立時區的時間。  如果不同電腦中的日期與時間的可攜性十分重要，建議使用 UTC \(如需使用日期與時間的詳細資訊及最佳作法，請參閱[使用 .NET Framework 中的 DateTime 的編碼最佳作法](http://go.microsoft.com/fwlink/?LinkId=92342)\)。將個別時區轉換成 UTC，可以使時間的比較變得更簡單。  
  
> [!NOTE]
>  您也可以將 <xref:System.DateTimeOffset> 結構序列化，以明確的表示單一時間點。  因為 <xref:System.DateTimeOffset> 物件會將日期與時間值及其 UTC 的位移值一起儲存，所以永遠都是表示相對於 UTC 的特定時間點。  
  
 將時間轉換成 UTC 最簡單的方式，就是呼叫 `static` \(Visual Basic 中為 `Shared`\) <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=fullName> 方法。  這個方法實際執行的轉換，會視 `dateTime` 參數的 <xref:System.DateTime.Kind%2A> 屬性值而定，如下表的說明。  
  
|DateTime.Kind 屬性|轉換|  
|----------------------|--------|  
|<xref:System.DateTimeKind?displayProperty=fullName>|將當地時間轉換成 UTC。|  
|<xref:System.DateTimeKind?displayProperty=fullName>|假設 `dateTime` 參數為當地時間，並將當地時間轉換成 UTC。|  
|<xref:System.DateTimeKind?displayProperty=fullName>|傳回未變更的 `dateTime` 參數。|  
  
 下列程式碼會將當地時間轉換成 UTC，並將結果顯示在主控台。  
  
 [!code-csharp[System.TimeZone2.Concepts#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#6)]
 [!code-vb[System.TimeZone2.Concepts#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#6)]  
  
> [!NOTE]
>  <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=fullName> 方法所產生的結果不一定會與 <xref:System.TimeZone.ToUniversalTime%2A?displayProperty=fullName> 和 <xref:System.DateTime.ToUniversalTime%2A?displayProperty=fullName> 方法相同。  如果主機系統的本地時區包含多個調整規則，<xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=fullName> 就會將適當的規則套用到特定的日期和時間。  另外兩個方法則一律套用最新的調整規則。  
  
 如果日期與時間值無法表示當地時間或 UTC，則 <xref:System.DateTime.ToUniversalTime%2A> 方法可能會傳回錯誤的結果。  但是，您可以使用 <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=fullName> 方法，轉換指定的時區之日期與時間 \(如需擷取代表目的地時區的 <xref:System.TimeZoneInfo> 物件的詳細資訊，請參閱[尋找定義於本機系統的時區](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)\)。下列程式碼使用 <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=fullName> 方法，將「東部標準時間」轉換成 UTC。  
  
 [!code-csharp[System.TimeZone2.Concepts#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#7)]
 [!code-vb[System.TimeZone2.Concepts#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#7)]  
  
 請注意如果 <xref:System.DateTime> 物件的 <xref:System.DateTime.Kind%2A> 屬性和時區不相符，這個方法會擲出 <xref:System.ArgumentException>。  如果 <xref:System.DateTime.Kind%2A> 屬性為 <xref:System.DateTimeKind?displayProperty=fullName> 但 <xref:System.TimeZoneInfo> 物件卻不代表當地時區，或如果 <xref:System.DateTime.Kind%2A> 屬性為 <xref:System.DateTimeKind?displayProperty=fullName> 但 <xref:System.TimeZoneInfo> 物件並不等於 <xref:System.DateTimeKind?displayProperty=fullName> 時，就會發生不相符的情形。  
  
 這些方法全部都使用 <xref:System.DateTime> 值為參數，並傳回一個 <xref:System.DateTime> 值。  如果是 <xref:System.DateTimeOffset> 值，<xref:System.DateTimeOffset> 結構有一個 <xref:System.DateTimeOffset.ToUniversalTime%2A> 執行個體方法，會將目前執行個體的日期與時間轉換成 UTC。下列範例會呼叫 <xref:System.DateTimeOffset.ToUniversalTime%2A> 方法，將當地時間及幾個其他時間轉換成 Coordinated Universal Time \(UTC\)。  
  
 [!code-csharp[System.DateTimeOffset.Methods#16](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/cs/Methods.cs#16)]
 [!code-vb[System.DateTimeOffset.Methods#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/vb/Methods.vb#16)]  
  
## 將 UTC 轉換成指定的時區  
 如果要將 UTC 轉換成當地時間，請參閱下一節的「將 UTC 轉換成當地時間」。  如果要將 UTC 轉換成您所指定的任何時區，請呼叫 <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> 方法。  這個方法會使用兩個參數：  
  
-   要轉換的 UTC。  必須是 <xref:System.DateTime> 值，且它的 <xref:System.DateTime.Kind%2A> 屬性設定為 <xref:System.DateTimeKind?displayProperty=fullName> 或 <xref:System.DateTimeKind?displayProperty=fullName>。  
  
-   要轉換 UTC 的目標時區。  
  
 下列程式碼會將 UTC 轉換成「中央標準時間」。  
  
 [!code-csharp[System.TimeZone2.Concepts#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#8)]
 [!code-vb[System.TimeZone2.Concepts#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#8)]  
  
## 將 UTC 轉換成當地時間  
 如果要將 UTC 轉換成當地時間，請呼叫您要轉換時間之 <xref:System.DateTime> 物件的 <xref:System.DateTime.ToLocalTime%2A> 方法。  方法的實際行為，會視物件的 <xref:System.DateTime.Kind%2A> 屬性值而定，如下表的說明。  
  
|`DateTime.Kind` 屬性|轉換|  
|------------------------|--------|  
|`DateTimeKind.Local`|傳回未變更的 <xref:System.DateTime> 值。|  
|`DateTimeKind.Unspecified`|假設 <xref:System.DateTime> 值是 UTC，並將 UTC 轉換為當地時間。|  
|`DateTimeKind.Utc`|將 <xref:System.DateTime> 值轉換成當地時間。|  
  
 **注意**：<xref:System.TimeZone.ToLocalTime%2A?displayProperty=fullName> 方法的行為和 `DateTime.ToLocalTime` 方法完全相同。這個方法會使用一個參數，也就是要轉換的日期與時間。  
  
 您也可以使用 `static` \(在 Visual Basic 中為 `Shared`\) <xref:System.TimeZoneInfo.ConvertTime%2A?displayProperty=fullName> 方法，將任何指定的時區時間轉換成當地時間。  使用的方法在下一節中將詳細說明。  
  
## 在任兩個時區之間轉換  
 您可以使用 <xref:System.TimeZoneInfo> 類別的下列兩個 `static` \(在 Visual Basic 中為 `Shared`\) 方法中的任何一個，在任兩個時區之間轉換。  
  
-   <xref:System.TimeZoneInfo.ConvertTime%2A>  
  
     這個方法的參數分別是要轉換的日期與時間值、`TimeZoneInfo` 物件代表日期與時間值的時區，以及 `TimeZoneInfo` 物件代表日期與時間值的轉換目標時區。  
  
-   <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>  
  
     這個方法的參數是要轉換的日期與時間值、日期與時間值的時區之識別項，以及日期與時間值的轉換目標時區之識別項。  
  
 這兩個方法都需要待轉換的日期與時間值的 <xref:System.DateTime.Kind%2A> 屬性，以及 <xref:System.TimeZoneInfo> 物件或代表彼此對應的時區識別項。  否則會擲回 <xref:System.ArgumentException>。  例如，如果日期與時間值的 `Kind` 屬性是 `DateTimeKind.Local`，而當做參數傳送給方法的 `TimeZoneInfo` 物件不等於 `TimeZoneInfo.Local` 時，就會擲回例外狀況。  如果當做參數傳送給方法的識別項不等於 `TimeZoneInfo.Local.Id`，也會擲回例外狀況。  
  
 下列範例使用 <xref:System.TimeZoneInfo.ConvertTime%2A> 方法，將夏威夷標準時間轉換為當地時間。  
  
 [!code-csharp[System.TimeZone2.Concepts#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#9)]
 [!code-vb[System.TimeZone2.Concepts#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#9)]  
  
## 轉換 DateTimeOffset 值  
 <xref:System.DateTimeOffset> 物件所代表的日期與時間值並不完全是時區感知的，因為在個體化時物件和所在的時區失去關聯。  但是，很多情況下，應用程式只需要根據兩個不同的 UTC 位移，而不需要特定的時區時間，就能夠轉換日期與時間。  如果要執行這項轉換，可以呼叫目前執行個體的 <xref:System.DateTimeOffset.ToOffset%2A> 方法。  這個方法的參數，就是方法將傳回之新日期與時間值的位移。  
  
 例如，如果已知使用者要求的網頁之日期與時間，且已序列化成 MM\/dd\/yyyy hh:mm:ss zzzz 格式的字串，則下列 `ReturnTimeOnServer` 方法會將這個日期與時間值轉換成網頁伺服器上的日期與時間。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/TimeConversions.cs#1)]
 [!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions.vb#1)]  
  
 如果該方法傳送字串 "9\/1\/2007 5:32:07 \-05:00"，代表比 UTC 早五個小時的時區之US時間，就會傳回 9\/1\/2007 3:32:07 AM \-07:00，代表位於美國。  
  
 <xref:System.TimeZoneInfo> 類別也包含 <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=fullName> 方法的多載，以 <xref:System.DateTimeOffset> 值執行時區轉換。  這個方法的參數是一個 <xref:System.DateTimeOffset> 值，以及一個待轉換時區的參考。  這個方法呼叫會傳回 <xref:System.DateTimeOffset> 值。  可以將上一個範例中的 `ReturnTimeOnServer` 方法重新撰寫如下以呼叫 <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29> 方法。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/timeconversions2.cs#2)]
 [!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions2.vb#2)]  
  
## 請參閱  
 <xref:System.TimeZoneInfo>   
 [日期、時間和時區](../../../docs/standard/datetime/index.md)   
 [尋找定義於本機系統的時區](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)