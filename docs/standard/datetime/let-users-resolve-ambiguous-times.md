---
title: "如何：讓使用者解決模稜兩可的時間 | Microsoft Docs"
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
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：讓使用者解決模稜兩可的時間
模稜兩可的時間就是可以對應至一個以上 Coordinated Universal Time \(UTC\) 的時間。  這會發生在時間及時調回時，例如從某個時區的日光節約時間轉換回標準時間時。  處理模稜兩可的時間時，您可以執行下列其中一項步驟：  
  
-   如果模稜兩可的時間是使用者所輸入的資料項目，您可以將這個情形留給使用者解決。  
  
-   假設時間如何對應至 UTC。  例如，您可以假設模稜兩可的時間永遠都是以時區的標準時間表示。  
  
 本主題說明如何讓使用者解決模稜兩可的時間。  
  
### 讓使用者解決模稜兩可的時間  
  
1.  取得使用者輸入的日期與時間。  
  
2.  呼叫 <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> 方法以判斷時間是否模稜兩可。  
  
3.  如果時間模稜兩可，請呼叫 <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> 方法，以擷取 <xref:System.TimeSpan> 物件的陣列。  陣列中的每一個項目內含模稜兩可的時間可對應的 UTC 位移。  
  
4.  讓使用者選擇想要的位移。  
  
5.  將當地時間減去使用者選擇的位移，以獲得 UTC 日期與時間。  
  
6.  呼叫 `static` \(在 Visual Basic .NET 中為 `Shared`\) <xref:System.DateTime.SpecifyKind%2A> 方法，將 UTC 日期與時間值的 <xref:System.DateTime.Kind%2A> 屬性設定為 <xref:System.DateTimeKind?displayProperty=fullName>。  
  
## 範例  
 下列範例會提示使用者輸入日期與時間，如果時間模稜兩可，會讓使用者選擇模稜兩可的時間對應至的 UTC 時間。  
  
 [!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
 [!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]  
  
 範例程式碼的核心使用 <xref:System.TimeSpan> 物件的陣列，指示模稜兩可的時間可能的 UTC 位移。  但是，這些位移對使用者來說可能沒有意義。  為了釐清位移的意義，程式碼中也註記了位移代表的是當地時區的標準時間，或日光節約時間。  程式碼會比較位移和 <xref:System.TimeZoneInfo.BaseUtcOffset%2A> 屬性的值，以判斷哪個時間是標準時間，哪個時間是日光節約時間。  這個屬性指示 UTC 及時區的標準時間之間的時差。  
  
 在本範例中，當地時區的所有參考都是透過 <xref:System.TimeZoneInfo.Local%2A?displayProperty=fullName> 屬性所建立的，當地時區並沒有被指派給物件變數。  建議採取這個方法，因為呼叫 <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=fullName> 方法會使被指派當地時區的任何物件失效。  
  
## 編譯程式碼  
 這個範例需要：  
  
-   將 System.Core.dll 的參考加入至專案中。  
  
-   以 `using` 陳述式 \(C\# 程式碼中的必要項\) 匯入 <xref:System> 命名空間。  
  
## 請參閱  
 [日期、時間和時區](../../../docs/standard/datetime/index.md)   
 [如何：解決模稜兩可的時間](../../../docs/standard/datetime/resolve-ambiguous-times.md)