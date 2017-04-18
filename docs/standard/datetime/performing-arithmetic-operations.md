---
title: "使用日期和時間執行算術運算 | Microsoft Docs"
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
  - "日期 [.NET Framework], 數學運算"
  - "日期 [.NET Framework], 比較"
  - "DateTime 結構, 數學運算"
  - "DateTimeOffset 結構, 數學運算"
  - "時區 [.NET Framework], 數學運算"
  - "時間 [.NET Framework], 數學運算"
ms.assetid: 87c7ddf2-f15e-48af-8602-b3642237e6d0
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 使用日期和時間執行算術運算
雖然 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 結構都提供成員來對其值執行算術運算，但算術運算得到的結果極為不同。  本主題將說明這些差異、這些差異與日期和時間資料的時區感知程度有何關係，並討論如何使用日期和時間資料執行完整的時區感知運算。  
  
## 對 DateTime 值進行比較和算術運算  
 從 .NET Framework 2.0 版開始，<xref:System.DateTime> 值加入了有限的時區感知程度。  <xref:System.DateTime.Kind%2A?displayProperty=fullName> 屬性可讓 <xref:System.DateTimeKind> 值指派給日期和時間，指出其表示的是本地時間、Coordinated Universal Time \(UTC\) 或未指定時區的時間。  不過，若對 <xref:System.DateTime> 值進行比較或執行日期和時間算術，此有限的時區資訊就會被忽略。  下列範例將以比較目前本地時間和目前 UTC 時間來說明此點。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
 [!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]  
  
 <xref:System.DateTime.CompareTo%28System.DateTime%29> 方法會報告本地時間早於 \(或晚於\) UTC 時間，接著減法運算會指出 UTC 與本地時間之間的差異，以美國太平洋標準時區系統來說相差七個小時。  但由於這兩個值提供不同的單一時間點表示，因此，從此例可以清楚得知，這段時間間隔完全是本地時間與 UTC 之間的位移。  
  
 簡單地說，就是 <xref:System.DateTime.Kind%2A?displayProperty=fullName> 屬性並不會影響 <xref:System.DateTime> 比較和計算後傳回的結果 \(就如同兩個完全相同的時間點比較的結果\)，雖然這可能會影響結果的解讀。  例如：  
  
-   對兩個 <xref:System.DateTime.Kind%2A?displayProperty=fullName> 屬性都等於 <xref:System.DateTimeKind> 的日期和時間值執行的任何算術運算所得到的結果，才會反映出兩個值之間的實際時間間隔。  同樣地，比較這兩個日期和時間值，才能準確反映出兩個時間之間的關係。  
  
-   對兩個 <xref:System.DateTime.Kind%2A?displayProperty=fullName> 屬性都等於 <xref:System.DateTimeKind> 的日期和時間值，或對兩個有不同 <xref:System.DateTime.Kind%2A?displayProperty=fullName> 屬性值的日期和時間值，執行的任何算術或比較運算所得結果反映的是兩個值之間的時鐘時間。  
  
-   對本地日期和時間值所做的算術或比較運算，不會考慮到特定值是否為模稜兩可或無效，也不會將本地時區與日光節約時間的來回轉換調整規則的影響列入考量。  
  
-   任何比較或計算 UTC 與本地時間之時差的運算所得的時間間隔，就等於是本地時區與 UTC 之間的位移。  
  
-   任何比較或計算未指定時間與 UTC 或本地時間之時差的運算，反映的是簡單的時鐘時間。  時區差異不會列入考量，而結果也不會反映出套用時區調整規則。  
  
-   任何比較或計算兩個未指定時間之時差的運算，可能會加入一段未知的時間間隔，以反映兩個不同時區的時間之間的差異。  
  
 在很多情節中，時區差異並不會影響日期和時間計算 \(如需部分案例討論，請參閱[在 DateTime、DateTimeOffset、 TimeSpan 和  TimeZoneInfo 之間選擇](../../../docs/standard/datetime/choosing-between-datetime.md)\)，或是日期和時間資料的內容會定義比較或算術運算的意義。  
  
## 對 DateTimeOffset 值進行比較和算術運算  
 <xref:System.DateTimeOffset> 值不僅包含日期和時間，也包含位移，它會明確定義相對於 UTC 的日期和時間。  因此，相等的定義與 <xref:System.DateTime> 值稍有不同。  對於 <xref:System.DateTime> 值，如果兩個值有相同的日期和時間值，就表示相等，但對於 <xref:System.DateTimeOffset> 值，則要兩個值都是指相同的時間點，才算相等。  這可讓 <xref:System.DateTimeOffset> 值在進行比較或大多數算術運算，以判斷兩個日期和時間值之間的時間間隔時，結果更為準確，也不需要太多的解讀。  下列範例是前面比較本地和 UTC <xref:System.DateTime> 值的範例，但將值改為了 <xref:System.DateTimeOffset>，以說明此行為差異。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
 [!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]  
  
 在這個範例中，<xref:System.DateTimeOffset.CompareTo%2A> 方法指出目前本地時間與目前 UTC 時間相等，而 <xref:System.DateTimeOffset> 值相減的結果顯示兩個時間的時差為 <xref:System.TimeSpan.Zero?displayProperty=fullName>。  
  
 在日期和時間的計算中使用 <xref:System.DateTimeOffset> 值的主要限制在於，雖然 <xref:System.DateTimeOffset> 值具有某些程度的時區感知，但卻不是完全的時區感知。  雖然在一開始指派值給 <xref:System.DateTimeOffset> 變數時，能夠讓 <xref:System.DateTimeOffset> 值的位移反映出時區與 UTC 之間的位移，但稍後就會與時區切斷關聯。  由於不再與可識別的時間直接相關聯，日期和時間間隔的加減就不會將時區的調整規則列入考量。  
  
 舉例而言，與日光節約時間轉換成在美國中央標準時區於 2008 年 3 月 9 日的 2:00 AM 。  這表示中央標準時間 2008 年 3 月 9 日 1:30 AM 加上兩個半小時，產生的日期應該為 2008 年 3 月 9 日 5:00 AM。  不過，如下列範例所示，加上兩個半小時後為 2008 年 3 月 9 日 4:00 A.M.。  請注意，這個運算結果並不代表正確的時間點，不過這也不是我們所要時區的時間 \(也就是說，沒有得到預期的時區位移\)。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
 [!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]  
  
## 對時區時間進行算術運算  
 <xref:System.TimeZoneInfo> 類別包含數個轉換方法，將時間從某個時區轉換成另一個時區時，會自動套用調整。  這些需求包括下列各項：  
  
-   <xref:System.TimeZoneInfo.ConvertTime%2A> 和 <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A> 方法，這兩個方法會在任何兩個時區之間轉換時間。  
  
-   <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> 和 <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> 方法，這兩個方法會將特定時區的時間轉換成 UTC，或將 UTC 轉換成特定時區的時間。  
  
 如需詳細資訊，請參閱 [在各時區間轉換時間](../../../docs/standard/datetime/converting-between-time-zones.md)。  
  
 <xref:System.TimeZoneInfo> 類別並沒有提供任何自動套用調整規則的方法，可供執行日期和時間算術使用。  不過，您可以這麼做：將時區的時間轉換成 UTC、執行算術運算，然後再將 UTC 轉換回該時區的時間。  如需詳細資訊，請參閱 [如何：在日期和時間運算中使用時區](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)。  
  
 例如，下列程式碼如同前面的程式碼，也是將 2008 年 3 月 9 日 2:00 A.M.加上兩個半小時。  不過，由於它是先將中部標準時間轉換成 UTC，然後才執行日期和時間算術，接著再將結果從 UTC 轉換回中部標準時間，因此所得時間就會反映轉換成日光節約時間之後的中部標準時區。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
 [!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]  
  
## 請參閱  
 [日期、時間和時區](../../../docs/standard/datetime/index.md)   
 [如何：在日期和時間運算中使用時區](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)