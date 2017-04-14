---
title: "在 DateTime 和 DateTimeOffset 之間轉換 | Microsoft Docs"
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
  - "轉換 DateTimeOffset 和 DateTime 值"
  - "轉換時間"
  - "Date 資料類型, 轉換"
  - "日期 [.NET Framework], 轉換"
  - "DateTime 結構, 轉換"
  - "DateTimeOffset 結構, 轉換"
  - "本地時間轉換"
  - "時區 [.NET Framework], 轉換"
  - "UTC 時間, 轉換"
ms.assetid: b605ff97-0c45-4c24-833f-4c6a3e8be64c
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# 在 DateTime 和 DateTimeOffset 之間轉換
雖然 <xref:System.DateTimeOffset> 結構對時區的感知程度要比 <xref:System.DateTime> 結構高，但在方法呼叫中較常使用的卻是 <xref:System.DateTime> 參數。  因此，知道如何將 <xref:System.DateTimeOffset> 值與 <xref:System.DateTime> 值相互轉換，就十分重要。  本主題說明如何執行這些轉換，同時盡可能保留時區資訊。  
  
> [!NOTE]
>  無論是使用 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 型別來表示時區中的時間，都會受到某些限制。  透過 <xref:System.DateTime> 的 <xref:System.DateTime.Kind%2A> 屬性，只能反映國際標準時間 \(UTC\) 和系統的本地時區。  <xref:System.DateTimeOffset> 雖然可以反映時間的 UTC 位移，但無法反映位移所屬的實際時區為何。  如需時間值和時區支援的詳細資訊，請參閱[在 DateTime、DateTimeOffset、 TimeSpan 和  TimeZoneInfo 之間選擇](../../../docs/standard/datetime/choosing-between-datetime.md)。  
  
## 從 DateTime 轉換為 DateTimeOffset  
 <xref:System.DateTimeOffset> 結構提供兩種對等的方法來執行 <xref:System.DateTime> 至 <xref:System.DateTimeOffset> 的轉換，這兩種方法可處理大部分的轉換：  
  
-   <xref:System.DateTimeOffset.%23ctor%2A> 建構函式，會根據 <xref:System.DateTime> 值來建立新的 <xref:System.DateTimeOffset> 物件。  
  
-   隱含轉換運算子，可以讓您將 <xref:System.DateTime> 值指派給 <xref:System.DateTimeOffset> 物件。  
  
 針對 UTC 和本地 <xref:System.DateTime> 值，所產生之 <xref:System.DateTimeOffset> 值的 <xref:System.DateTimeOffset.Offset%2A> 屬性會準確地反映出 UTC 或本地時區位移。  例如，下列程式碼會將 UTC 時間轉換成其對等的 <xref:System.DateTimeOffset> 值。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]  
  
 在此例中，`utcTime2` 變數的位移為 00:00。  同樣地，下列程式碼會將本地時間轉換成其對等的 <xref:System.DateTimeOffset> 值。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]  
  
 不過，對於 <xref:System.DateTime.Kind%2A> 屬性為 <xref:System.DateTimeKind?displayProperty=fullName> 的 <xref:System.DateTime> 值，這兩種轉換方法都會產生其位移為本地時區位移的 <xref:System.DateTimeOffset> 值。  這會在下列範例中示範，在美國太平洋標準時區執行。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]  
  
 如果 <xref:System.DateTime> 值反映的日期和時間不是本地時區或 UTC，您可以藉由呼叫多載 <xref:System.DateTimeOffset.%23ctor%2A> 建構函式，將它轉換成 <xref:System.DateTimeOffset> 值並保留其時區資訊。  例如，下列範例會將反映中央標準時間的 <xref:System.DateTimeOffset> 物件具現化。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]  
  
 此建構函式多載的第二個參數 \(即表示時間之 UTC 位移的 <xref:System.TimeSpan> 物件\) 應藉由呼叫時間相對應時區的 <xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=fullName> 方法來擷取。  這個方法的單一參數就是 <xref:System.DateTime> 值，此值表示要轉換的日期和時間。  如果時區支援日光節約時間，則此參數可讓方法判斷該特定日期和時間的適當位移。  
  
## 從 DateTimeOffset 轉換為 DateTime  
 <xref:System.DateTimeOffset.DateTime%2A> 屬性最常用來執行 <xref:System.DateTimeOffset> 至 <xref:System.DateTime> 的轉換。  不過，它會傳回 <xref:System.DateTime.Kind%2A> 屬性為 <xref:System.DateTimeKind> 的 <xref:System.DateTime> 值，如下列範例所示。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]  
  
 這表示當使用 <xref:System.DateTimeOffset.DateTime%2A> 屬性時，在轉換之後，關於 <xref:System.DateTimeOffset> 值與 UTC 之間關係的任何資訊都將會遺失。  這會影響對應至 UTC 時間或系統本地時間的 <xref:System.DateTimeOffset> 值，因為 <xref:System.DateTimeOffset.DateTime%2A> 結構的 <xref:System.DateTime.Kind%2A> 屬性中只會反映這兩種時區。  
  
 為了在轉換 <xref:System.DateTimeOffset> 為 <xref:System.DateTime> 值時盡可能保留時區資訊，您可以使用 <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=fullName> 和 <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=fullName> 屬性。  
  
### 轉換 UTC 時間  
 若要指示轉換的 <xref:System.DateTimeOffset.DateTime%2A> 值是 UTC 時間，您可以擷取 <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=fullName> 屬性的值。  它在下列兩方面與 <xref:System.DateTimeOffset.DateTime%2A> 屬性不同：  
  
-   它會傳回其 <xref:System.DateTime.Kind%2A> 屬性為 <xref:System.DateTimeKind> 的 <xref:System.DateTime> 值。  
  
-   如果 <xref:System.DateTimeOffset.Offset%2A> 屬性值不等於 <xref:System.TimeSpan.Zero?displayProperty=fullName>，它會將時間轉換為 UTC。  
  
> [!NOTE]
>  如果您的應用程式需要轉換的 <xref:System.DateTime> 值明確識別單一時間點，請考慮使用 <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=fullName> 屬性來處理所有 <xref:System.DateTimeOffset> 至 <xref:System.DateTime> 的轉換。  
  
 下列程式碼使用 <xref:System.DateTimeOffset.UtcDateTime%2A> 屬性來將位移等於 <xref:System.TimeSpan.Zero?displayProperty=fullName> 的 <xref:System.DateTimeOffset> 值轉換為 <xref:System.DateTime> 值。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]  
  
 下列程式碼使用 <xref:System.DateTimeOffset.UtcDateTime%2A> 屬性來對 <xref:System.DateTimeOffset> 值同時執行時區轉換和型別轉換。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]  
  
### 轉換本地時間  
 若要指示 <xref:System.DateTimeOffset> 值表示的是本地時間，您可以將 <xref:System.DateTimeOffset.DateTime%2A?displayProperty=fullName> 屬性傳回的 <xref:System.DateTime> 值傳遞至 `static` \(在 Visual Basic 中為`Shared` \) <xref:System.DateTime.SpecifyKind%2A> 方法。  這個方法會傳回第一個參數傳遞給它的日期和時間，但其 <xref:System.DateTime.Kind%2A> 屬性會被設為第二個參數所指定的值。  下列程式碼使用 <xref:System.DateTime.SpecifyKind%2A> 方法來轉換值相當於本地時區位移的 <xref:System.DateTimeOffset>。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]  
  
 您也可以使用 <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=fullName> 屬性來將 <xref:System.DateTimeOffset> 值轉換為本地 <xref:System.DateTime> 值。  傳回之 <xref:System.DateTime> 值的 <xref:System.DateTime.Kind%2A> 屬性為 <xref:System.DateTimeKind>。  下列程式碼會使用 <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=fullName> 屬性來轉換值相當於本地時區位移的 <xref:System.DateTimeOffset> 值。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]  
  
 當您使用 <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=fullName> 屬性擷取 <xref:System.DateTime> 值時，屬性的 `get` 存取子會先將 <xref:System.DateTimeOffset> 值轉換成 UTC，然後再藉由呼叫 <xref:System.DateTimeOffset.ToLocalTime%2A> 方法將它轉換成本地時間。  這表示您可以從 <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=fullName> 屬性擷取值來執行時區轉換，並且同時執行型別轉換。  這也表示會套用本地時區的調整規則來執行轉換。  下列程式碼說明如何使用 <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=fullName> 屬性來同時執行型別和時區轉換。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]  
  
### 通用轉換方法  
 在下列範例中，會定義名為 `ConvertFromDateTimeOffset` 的方法，用它來將 <xref:System.DateTimeOffset> 值轉換成 <xref:System.DateTime> 值。  根據其位移而定，它會判斷 <xref:System.DateTimeOffset> 值是 UTC 時間、本地時間或其他時間，然後依此定義所傳回日期和時間值的 <xref:System.DateTime.Kind%2A> 屬性。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]  
  
 下列範例會呼叫 `ConvertFromDateTimeOffset` 方法來轉換 <xref:System.DateTimeOffset> 値，這些値表示 UTC 時間、本地時間以及美國中央標準時區。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]  
  
 請注意，此程式碼做了兩項假設，但根據應用程式以及其日期和時間值的來源，這些假設不一定會成立：  
  
-   它假設位移為 <xref:System.TimeSpan.Zero?displayProperty=fullName> 的日期和時間值是代表 UTC。  事實上，UTC 並不是特定時區的時間，而是相對於全球時區中已標準化的時間。  時區也可以有 <xref:System.TimeSpan.Zero> 的位移。  
  
-   它假設位移等於本地時區位移的日期和時間是代表本地時區。  由於日期和時間值與其原始時區並不相關，因此假設不一定成立。日期和時間可能來自具有相同位移的另一個時區。  
  
## 請參閱  
 [日期、時間和時區](../../../docs/standard/datetime/index.md)