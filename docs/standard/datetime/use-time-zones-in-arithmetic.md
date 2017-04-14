---
title: "如何：在日期和時間運算中使用時區 | Microsoft Docs"
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
  - "數學運算 [.NET Framework], 日期和時間"
  - "日期 [.NET Framework], 加入和減去"
  - "時區 [.NET Framework], 數學運算"
ms.assetid: 83dd898d-1338-415d-8cd6-445377ab7871
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：在日期和時間運算中使用時區
通常，當您使用 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 值執行日期與時間算術時，結果並不會反映任何時區調整規則。  即使日期與時間值的時區明顯可識別也一樣 \(例如，當 <xref:System.DateTime.Kind%2A> 屬性設定為 <xref:System.DateTimeKind> 時\)。  本主題說明如何對特定時區所屬的日期與時間值，執行算術運算。  算術運算的結果會反映時區的調整規則。  
  
### 將調整規則套用至日期與時間算術  
  
1.  實作某個將日期與時間值和其所屬的時區緊密結合的方法。  例如，宣告一個內含日期與時間值以及所屬時區的結構。  下列範例使用這個方法，將 <xref:System.DateTime> 值連結至所屬的時區。  
  
     [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
     [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]  
  
2.  呼叫 <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> 或 <xref:System.TimeZoneInfo.ConvertTime%2A> 方法，將時間轉換成 Coordinated Universal Time \(UTC\)。  
  
3.  對 UTC 時間執行算術運算。  
  
4.  呼叫 <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=fullName> 方法，將時間從 UTC 轉換成原始時間相關的時區。  
  
## 範例  
 下列範例會增加兩小時又三十分鐘至「中央標準時間」2008 年 3 月 9 日 1:30 A.M.。  在三十分鐘後，2008年3月9日上午2點會執行時區轉換為日光節約時間。  因為本範例遵照上一節所列的四個步驟，所以會正確地回報結果為 5:00 A.M. on March 9, 2008。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
 [!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]  
  
 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 值都和所屬的時區失去關聯。  如果要執行自動套用時區調整規則的日期與時間算術，則日期與時間所屬的時區必須立即可識別。  也就是說，日期與時間和相關的時區必須緊密的結合。  有幾個方法可以這麼做，包括：  
  
-   假設應用程式使用的所有時間都屬於特定時區。  雖然這個方法有時適用，但是彈性有限而且可能也有可攜性的限制。  
  
-   定義一個型別，將日期與時間和其關聯的時區納入成為型別的欄位，以緊密的結合日期與時間和其時區。  程式碼範例就是使用這個方法，定義一個結構將日期與時間和時區儲存在兩個成員欄位中。  
  
 本範例說明如何對 <xref:System.DateTime> 值執行算數運算，將時區調整規則套用至結果。  但是，<xref:System.DateTimeOffset> 值的使用也可以很簡單。  下列範例說明如何改寫原始範例中的程式碼，以使用 <xref:System.DateTimeOffset> 而不使用 <xref:System.DateTime> 值。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
 [!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]  
  
 請注意，如果沒有先將 <xref:System.DateTimeOffset> 值轉換成 UTC 就執行這個動作，產生的結果會反映正確的時間點，但位移並不會反映指定給這個時間的時區。  
  
## 編譯程式碼  
 這個範例需要：  
  
-   將 System.Core.dll 的參考加入至專案中。  
  
-   以 `using` 陳述式 \(C\# 程式碼中的必要項\) 匯入 <xref:System> 命名空間。  
  
## 請參閱  
 [日期、時間和時區](../../../docs/standard/datetime/index.md)   
 [使用日期和時間執行算術運算](../../../docs/standard/datetime/performing-arithmetic-operations.md)