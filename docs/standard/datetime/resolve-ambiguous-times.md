---
title: "如何：解決模稜兩可的時間 | Microsoft Docs"
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
  - "模稜兩可的時間 [.NET Framework]"
  - "時區 [.NET Framework], 模稜兩可的時間"
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：解決模稜兩可的時間
模稜兩可的時間就是可以對應至一個以上 Coordinated Universal Time \(UTC\) 的時間。  這會發生在時間及時調回時，例如從某個時區的日光節約時間轉換回標準時間時。  處理模稜兩可的時間時，您可以執行下列其中一項步驟：  
  
-   假設時間如何對應至 UTC。  例如，您可以假設模稜兩可的時間永遠都是以時區的標準時間表示。  
  
-   如果模稜兩可的時間是使用者所輸入的資料項目，您可以將這個情形留給使用者解決。  
  
 本主題說明如何假設模稜兩可的時間代表時區的標準時間，以解決模稜兩可的時間問題。  
  
### 將模稜兩可的時間對應至時區的標準時間  
  
1.  呼叫 <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> 方法以判斷時間是否模稜兩可。  
  
2.  如果時間是模稜兩可的，請從時區的 <xref:System.TimeZoneInfo.BaseUtcOffset%2A> 屬性所傳回的 <xref:System.TimeSpan> 物件中，將這個時間減去。  
  
3.  呼叫 `static` \(在 Visual Basic .NET 中為 `Shared`\) <xref:System.DateTime.SpecifyKind%2A> 方法，將 UTC 日期與時間值的 <xref:System.DateTime.Kind%2A> 屬性設定為 <xref:System.DateTimeKind?displayProperty=fullName>。  
  
## 範例  
 下列範例說明，如何透過假設模稜兩可的時間代表當地時區的標準時間，將模稜兩可的時間轉換成 UTC 的方式。  
  
 [!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
 [!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]  
  
 這個範例是由名稱為 `ResolveAmbiguousTime` 的方法所組成，會判斷傳送給方法的 <xref:System.DateTime> 值是否模稜兩可。  如果值模稜兩可，方法會傳回 <xref:System.DateTime> 值，代表對應的 UTC 時間。  這個方法是將當地時區的 <xref:System.TimeZoneInfo.BaseUtcOffset%2A> 屬性值，從當地時間中減去以進行轉換。  
  
 一般而言，呼叫 <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> 方法以擷取 <xref:System.TimeSpan> 物件的陣列 \(內含模稜兩可的時間可能的 UTC 位移\)，就可以解決模稜兩可的時間  但是，這個範例會自行假設，模稜兩可的時間應該要永遠對應至時區的標準時間。  <xref:System.TimeZoneInfo.BaseUtcOffset%2A> 屬性會傳回 UTC 與時區的標準時間之間的位移。  
  
 在本範例中，當地時區的所有參考都是透過 <xref:System.TimeZoneInfo.Local%2A?displayProperty=fullName> 屬性所建立的，當地時區並沒有被指派給物件變數。  建議採取這個方法，因為呼叫 <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=fullName> 方法會使被指派當地時區的任何物件失效。  
  
## 編譯程式碼  
 這個範例需要：  
  
-   將 System.Core.dll 的參考加入至專案中。  
  
-   以 `using` 陳述式 \(C\# 程式碼中的必要項\) 匯入 <xref:System> 命名空間。  
  
## 請參閱  
 [日期、時間和時區](../../../docs/standard/datetime/index.md)   
 [如何：讓使用者解決模稜兩可的時間](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)