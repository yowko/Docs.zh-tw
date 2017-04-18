---
title: "如何：存取預先定義的 UTC 和本機時區物件 | Microsoft Docs"
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
  - "當地時區存取"
  - "預先定義的時區"
  - "時區 [.NET Framework], 本機"
  - "時區 [.NET Framework], 擷取"
  - "時區 [.NET Framework], UTC"
  - "UTC 時間, 預先定義的"
ms.assetid: 961fb70b-83f0-4dab-a042-cb5fcd817cf5
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：存取預先定義的 UTC 和本機時區物件
<xref:System.TimeZoneInfo> 類別提供兩個屬性，<xref:System.TimeZoneInfo.Utc%2A> 和 <xref:System.TimeZoneInfo.Local%2A>，提供您預先定義的時區物件之程式碼存取權。  本主題討論如何存取這些屬性所傳回的 <xref:System.TimeZoneInfo> 物件。  
  
### 存取 Coordinated Universal Time \(UTC\) TimeZoneInfo 物件  
  
1.  使用 `static` \(在 Visual Basic 中為 `Shared`\) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=fullName> 屬性存取 Coordinated Universal Time。  
  
2.  您應該繼續透過 <xref:System.TimeZoneInfo.Utc%2A?displayProperty=fullName> 屬性存取 Coordinated Universal Time，而不是將屬性所傳回的 <xref:System.TimeZoneInfo> 物件指派給物件變數。  
  
### 存取當地時區  
  
1.  使用 `static` \(在 Visual Basic 中為 `Shared`\) <xref:System.TimeZoneInfo.Local%2A?displayProperty=fullName> 屬性存取當地系統時區。  
  
2.  您應該繼續透過 <xref:System.TimeZoneInfo.Local%2A?displayProperty=fullName> 屬性存取當地時區，而不是將屬性所傳回的 <xref:System.TimeZoneInfo> 物件指派給物件變數。  
  
## 範例  
 下列程式碼會使用 <xref:System.TimeZoneInfo.Local%2A?displayProperty=fullName> 和 <xref:System.TimeZoneInfo.Utc%2A?displayProperty=fullName> 屬性來轉換美國及加拿大東部標準時區的時間，以及顯示時區名稱寫入主控台。  
  
 [!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
 [!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]  
  
 您應該透過 <xref:System.TimeZoneInfo.Local%2A?displayProperty=fullName> 屬性存取當地時區，而不是將當地時區指派給 <xref:System.TimeZoneInfo> 物件變數。  同樣的，您應該透過 <xref:System.TimeZoneInfo.Utc%2A?displayProperty=fullName> 屬性存取 Coordinated Universal Time，而不是將 UTC 時區指派給 <xref:System.TimeZoneInfo> 物件變數。這麼做可以避免 <xref:System.TimeZoneInfo> 物件變數因呼叫 <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=fullName> 方法而失效。  
  
## 編譯程式碼  
 這個範例需要：  
  
-   將 System.Core.dll 的參考加入至專案中。  
  
-   以 `using` 陳述式 \(C\# 程式碼中的必要項\) 匯入 <xref:System> 命名空間。  
  
## 請參閱  
 [日期、時間和時區](../../../docs/standard/datetime/index.md)   
 [尋找定義於本機系統的時區](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)   
 [如何：具現化 TimeZoneInfo 物件](../../../docs/standard/datetime/instantiate-time-zone-info.md)