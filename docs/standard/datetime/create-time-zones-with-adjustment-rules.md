---
title: "如何：建立有調整規則的時區 | Microsoft Docs"
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
  - "調整規則 [.NET Framework]"
  - "時區 [.NET Framework], 以及調整規則"
  - "時區 [.NET Framework], 建立"
ms.assetid: c52ef192-13a9-435f-8015-3b12eae8c47c
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：建立有調整規則的時區
特定系統可能基於以下原因，而沒有應用程式所需的精確的時區資訊：  
  
-   本機系統登錄中從未定義這個時區。  
  
-   時區的資料已被修改或從登錄中移除。  
  
-   這個時區並沒有特定歷史期間的時區調整精確資訊。  
  
 在這種情況下，您可以呼叫 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 方法以定義應用程式所需的時區。  您可以使用這個方法的多載，以建立包含或不含調整規則的時區。  如果該時區支援日光節約時間，您可以使用固定或浮動調整規則來定義調整方式 \(如需這些用語的定義，請參閱[時區概觀](../../../docs/standard/datetime/time-zone-overview.md)的＜時區用語＞一節\)。  
  
> [!IMPORTANT]
>  呼叫 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 方法所建立的自訂時區不會新增至登錄中。  只能透過 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 方法呼叫所傳回的物件參考才能存取。  
  
 本主題說明如何建立時區和調整規則。  如果要建立不支援日光節約時間調整規則的時區，請參閱 [如何：建立沒有調整規則的時區](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)。  
  
### 建立採用浮動調整規則的時區  
  
1.  對每一個調整方法 \(就是，標準時間與特定時間間隔的來回轉換\) 執行下列步驟：  
  
    1.  定義時區調整開始轉換的時間。  
  
         您必須呼叫 <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=fullName> 方法，並將下列值傳送給方法：定義轉換時間的 <xref:System.DateTime> 值、定義轉換月份的整數值、定義轉換週的整數值，以及定義轉換日的 <xref:System.DayOfWeek> 值。  這個方法呼叫會將 <xref:System.TimeZoneInfo.TransitionTime> 物件個體化。  
  
    2.  定義時區調整結束轉換的時間。  這麼做必須要再次呼叫 <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=fullName> 方法。  這個方法呼叫會將第二個 <xref:System.TimeZoneInfo.TransitionTime> 物件個體化。  
  
    3.  呼叫 <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> 方法，並將下列值傳送給方法：調整的有效開始及結束日期、定義轉換時間長度的 <xref:System.TimeSpan> 物件，以及兩個定義來回轉換日光節約時間發生時間的 <xref:System.TimeZoneInfo.TransitionTime> 物件。  這個方法呼叫會將 <xref:System.TimeZoneInfo.AdjustmentRule> 物件個體化。  
  
    4.  將 <xref:System.TimeZoneInfo.AdjustmentRule> 物件指派給 <xref:System.TimeZoneInfo.AdjustmentRule> 物件的陣列。  
  
2.  定義時區的顯示名稱。  顯示名稱遵循相當程度的標準格式，其中時區的 Coordinated Universal Time \(UTC\) 位移會包含在括號中，後面接著識別時區的字串、該時區的一或多個城市，或是該時區的一或多個國家或地區。  
  
3.  定義時區的標準時間之名稱。  通常，這個字串也會當成時區的識別項使用。  
  
4.  定義時區的日光節約時間名稱。  
  
5.  如果您要使用和時區的標準名稱不同的識別項，請定義時區識別項。  
  
6.  將定義時區的 UTC 位移之 <xref:System.TimeSpan> 物件個體化。  時間較 UTC 晚的時區，位移值是正的。  時間較 UTC 早的時區，位移值是負的。  
  
7.  呼叫 [TimeZoneInfo.CreateCustomTimeZone\(String, TimeSpan, String, String, String, TimeZoneInfo.AdjustmentRule\<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=fullName> 方法，將新時區個體化。  
  
## 範例  
 下列範例會定義美國的「中央標準時間」區，內含自 1918 年至今的各種時間間隔的調整規則。  
  
 [!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
 [!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]  
  
 本範例中所建立的時區有多重調整規則。  請特別小心，以確保任何調整規則的有效開始及結束日期不會與其他調整規則的日期重疊。  如果重疊，就會擲回 <xref:System.InvalidTimeZoneException>。  
  
 如果是浮動調整規則，會將值 5 傳送給 <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> 方法的 `week` 參數，以指出轉換是在特定月份的最後一週發生的。  
  
 在建立 <xref:System.TimeZoneInfo.AdjustmentRule> 物件的陣列以使用於 [TimeZoneInfo.CreateCustomTimeZone\(String, TimeSpan, String, String, String, TimeZoneInfo.AdjustmentRule\<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=fullName> 方法呼叫時，程式碼可以將陣列個體化，使陣列的大小和時區要建立之調整數目所要求的大小一樣。  這個程式碼範例會呼叫 <xref:System.Collections.Generic.List%601.Add%2A> 方法，將每一個調整規則新增至 <xref:System.TimeZoneInfo.AdjustmentRule> 物件的泛型 <xref:System.Collections.Generic.List%601> 集合。  然後程式碼會呼叫 <xref:System.Collections.Generic.List%601.CopyTo%2A> 方法，將集合的成員複製至陣列。  
  
 這個範例也會使用 <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> 方法來定義固定日期的調整。  這麼做類似呼叫 <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> 方法，只不過它只需要轉換參數的時間、月份及日期。  
  
 本範例可以使用如下面的程式碼測試：  
  
 [!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
 [!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   將 System.Core.dll 的參考加入至專案中。  
  
-   匯入下列命名空間：  
  
     [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
     [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]  
  
## 請參閱  
 [日期、時間和時區](../../../docs/standard/datetime/index.md)   
 [時區概觀](../../../docs/standard/datetime/time-zone-overview.md)   
 [如何：建立沒有調整規則的時區](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)