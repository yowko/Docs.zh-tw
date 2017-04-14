---
title: "時區概觀 | Microsoft Docs"
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
  - "模稜兩可的時間 [.NET Framework]"
  - "日光節約時期 [.NET Framework]"
  - "固定規則 [.NET Framework]"
  - "浮動規則 [.NET Framework]"
  - "無效的時間 [.NET Framework]"
  - "時區 [.NET Framework], 關於時區"
  - "時區 [.NET Framework], 建立"
  - "時區 [.NET Framework], 用語"
  - "TimeZoneInfo 類別, 關於 TimeZoneInfo 類別"
  - "轉換時間 [.NET Framework]"
ms.assetid: c4b7ed01-5e38-4959-a3b6-ef9765d6ccf1
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 時區概觀
<xref:System.TimeZoneInfo> 類別會簡化時區感知應用程式的建立過程。  <xref:System.TimeZone> 類別支援使用當地時區及 Coordinated Universal Time \(UTC\)。  <xref:System.TimeZoneInfo> 類別支援這兩種時區，以及任何相關資訊已預先定義於登錄中的時區。  您也可以使用 <xref:System.TimeZoneInfo> 定義系統中沒有相關資訊的自訂時區。  
  
## 時區基本功能  
 時區是一個地理區域，在此區域中的時間都相同。  通常，但不是絕對，相鄰的時區相差一個小時。  全球任何時區的時間，都可以表示成 Coordinated Universal Time \(UTC\) 的位移。  
  
 全世界有許多時區都支援日光節約時間。  在春季或夏季初期將時間往前撥一小時，並在夏末或秋季調整回一般 \(即標準\) 時間，以延長白晝的時間，稱為日光節約時間。  標準時間的來回變動就是調整規則。  
  
 特定時區的日光節約時間來回轉換，可以使用固定或浮動調整規則加以定義。  固定調整規則就是設定一個特定日期，並在每年此時來回轉換日光節約時間。  例如，日光節約時間轉換回標準時間，是在每年的 10 月 25 日，所遵循的就是固定調整規則。  較為常見的是浮動調整規則，這些規則會設定在特定月份的特定星期的特定日期來回轉換日光節約時間。  例如，從標準時間轉換成日光節約時間設定在三月的第三個星期日，就會遵循浮動調整規則。  
  
 對於支援調整規則的時區，來回轉換日光節約時間會產生兩種異常時間：無效時間及模稜兩可的時間。  無效的時間就是來回轉換標準時間和日光節約時間而造成的不存在的時間。  例如，如果轉換發生在某一日的 2:00 A.M. 而造成時間變成 3:00 A.M.，每次在 2:00 A.M. 到2:59:99 A.M. 之間的間隔無效。  模稜兩可的時間就是單一時區內，時間可以對應至兩個不同的時間。  這是從日光節約時間轉換成標準時間所造成的。  例如，如果轉換發生在某一日的 2:00 A.M. 而造成時間變成 1:00 A.M.，每次在 1:00 A.M. 1:59:99 A.M. 之間的間隔可以解譯為標準時間或日光節約時間。  
  
## 時區用語  
 下表定義使用時區及開發時區感知應用程式時，常見的詞彙。  
  
|詞彙|定義|  
|--------|--------|  
|調整規則|定義何時從標準時間轉換成日光節約時間，以及從日光節約時間轉換回標準時間的規則。  每一個調整規則都有開始及結束時間，定義規則生效的時間 \(例如，調整規則從 1986 年 1 月開始到 2006 年 12 月 31 日\)、時間差異 \(套用調整規則使標準時間變更的時間長度\)，以及在調整期間發生轉換的特定日期與時間之相關資訊。  轉換可以採用固定規則或浮動規則。|  
|模稜兩可的時間|單一時區內，時間可以對應至兩個不同的時間。  這會發生在時間及時調回時，例如從某個時區的日光節約時間轉換回標準時間時。  例如，如果轉換發生在某一日的 2:00 A.M. 而造成時間變成 1:00 A.M.，每次在 1:00 A.M. 1:59:99 A.M. 之間的間隔可以解譯為標準時間或日光節約時間。|  
|固定規則|設定特定日期以來回轉換日光節約時間的調整規則。  例如，日光節約時間轉換回標準時間，是在每年的 10 月 25 日，所遵循的就是固定調整規則。|  
|浮動規則|設定月份的特定週的特定日，來回轉換日光節約時間的調整規則。  例如，從標準時間轉換成日光節約時間設定在三月的第三個星期日，就會遵循浮動調整規則。|  
|無效的時間|因來回轉換標準時間和日光節約時間而造成的不存在的時間。  當時間及時向前調整，例如，從某個時區的標準時間轉換成日光節約時間，就會發生這種情形。  例如，如果轉換發生在某一日的 2:00 A.M. 而造成時間變成 3:00 A.M.，每次在 2:00 A.M. 到2:59:99 A.M. 之間的間隔無效。|  
|轉換時間|有關特定時區中特定時間變更 \(例如從日光節約時間變為標準時間，反之亦然\) 的資訊。|  
  
## 時區與 TimeZoneInfo 類別  
 在 .NET Framework 中，<xref:System.TimeZoneInfo> 物件代表時區。  <xref:System.TimeZoneInfo> 類別包含 <xref:System.TimeZoneInfo.GetAdjustmentRules%2A> 方法，會傳回 <xref:System.TimeZoneInfo.AdjustmentRule> 物件陣列。  陣列的每一個項目都會提供有關特定時段的日光節約時間來回轉換資訊 \(如果是不支援日光節約時間的時區，這個方法會傳回空的陣列\)。每一個 <xref:System.TimeZoneInfo.AdjustmentRule> 物件都有一個 <xref:System.TimeZoneInfo.AdjustmentRule.DaylightTransitionStart%2A> 和 <xref:System.TimeZoneInfo.AdjustmentRule.DaylightTransitionEnd%2A> 屬性，定義來回轉換日光節約時間的特定日期與時間。  <xref:System.TimeZoneInfo.TransitionTime.IsFixedDateRule%2A> 屬性指定採用固定或浮動轉換。  
  
 .NET Framework 需要由 Windows 作業系統所提供，並儲存在登錄中的時區資訊。  由於全球的時區數量眾多，登錄中並沒有所有現有時區。  此外，因為登錄是一種動態結構，所以結構中可以新增或刪除預先定義的時區。  最後，登錄並不一定內含歷史時區資料。  例如，在 Windows XP 中，登錄內只有一組時區調整的資料。  Windows Vista 支援動態時區資料，表示單一時區可以有多個調整規則，套用至特定的年度間隔。  但是，Windows Vista 登錄中所定義及支援日光節約時間的大部分時區，都只有一或兩個預先定義的調整規則。  
  
 登錄中的 <xref:System.TimeZoneInfo> 類別的相依性，表示時區感知應用程式無法確定特定時區是否已定義於登錄中。  因此，嘗試將特定時區 \(除了當地時區或代表 UTC 的時區\) 具現化就必須使用例外狀況處理。  也必須提供方法，當必要的 <xref:System.TimeZoneInfo> 物件無法從登錄中具現化時，仍能讓應用程式繼續執行。  
  
 為了處理缺少的必要時區，<xref:System.TimeZoneInfo> 類別包含一個 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 方法，您可以用這個方法建立登錄中沒有的自訂時區。  如需建立自訂時區的詳細資訊，請參閱 [如何：建立沒有調整規則的時區](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)及 [如何：建立有調整規則的時區](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)。  此外，您可以使用 <xref:System.TimeZoneInfo.ToSerializedString%2A> 方法，將新建立的時區轉換成字串並儲存在資料存放區中 \(例如資料庫、文字檔、登錄或應用程式資源\)。  然後您就可以使用 <xref:System.TimeZoneInfo.FromSerializedString%2A> 方法，將這個字串轉換回 <xref:System.TimeZoneInfo> 物件。  如需詳細資訊，請參閱 [如何：將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)及 [如何：從內嵌資源還原時區](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)。  
  
 因為每一個時區都可以由 UTC 基本位移表示，以及反映任何現有調整規則的 UTC 位移來表示，時區的時間可以很容易就轉換成其他時區的時間。  因此，<xref:System.TimeZoneInfo> 物件內含幾個轉換方法，包括：  
  
-   <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>，將 UTC 轉換成指定時區的時間。  
  
-   <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A>，將指定時區的時間轉換成 UTC。  
  
-   <xref:System.TimeZoneInfo.ConvertTime%2A>，將指定時區的時間轉換成另一個指定時區的時間。  
  
-   <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>，使用時區識別項 \(而非 <xref:System.TimeZoneInfo> 物件\) 做為參數，將指定時區的時間轉換成另一個指定時區的時間。  
  
 如需時區的時間轉換詳細資訊，請參閱[在各時區間轉換時間](../../../docs/standard/datetime/converting-between-time-zones.md)。  
  
## 請參閱  
 [日期、時間和時區](../../../docs/standard/datetime/index.md)