---
title: "具現化 DateTimeOffset 物件 | Microsoft Docs"
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
  - "執行個體化時區物件"
  - "時區物件 [.NET Framework]，具現化"
  - "DateTimeOffset 結構，轉換為 DateTime"
  - "DateTimeOffset 結構，具現化"
ms.assetid: 9648375f-d368-4373-a976-3332ece00c0a
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 具現化 DateTimeOffset 物件
<xref:System.DateTimeOffset> 類別提供許多方法來建立新的 <xref:System.DateTimeOffset> 值。  其中有許多都是直接對應於具現化新 <xref:System.DateTime> 值的方法，經加強後，可讓您指定日期和時間值與 Coordinated Universal Time \(UTC\) 之間的位移。  特別是，您可以利用下列方式具現化 <xref:System.DateTimeOffset> 值：  
  
-   使用日期和時間常值。  
  
-   呼叫 <xref:System.DateTimeOffset> 建構函式。  
  
-   將值隱含轉換成 <xref:System.DateTimeOffset> 值。  
  
-   剖析日期和時間的字串表示。  
  
 本主題將提供更詳細的解說和程式碼範例，來說明這些具現化新 <xref:System.DateTimeOffset> 值的方法。  
  
## 日期和時間常值  
 對於支援的語言，要具現化 <xref:System.DateTime> 值，最常見的其中一種方式就是將日期和時間提供為固定的常值。  例如，下列 Visual Basic 程式碼會建立一個 <xref:System.DateTime> 物件，其值為 2008 年 1 月 1 日 10:00 AM。  
  
 [!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]  
  
 當您使用支援 <xref:System.DateTime> 常值的語言時，也可以使用日期和時間常值具現化 <xref:System.DateTimeOffset> 值。  例如，下列 Visual Basic 程式碼會建立一個 <xref:System.DateTimeOffset> 物件。  
  
 [!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]  
  
 如主控台輸出所示，以此方式建立的 <xref:System.DateTimeOffset> 值會指派成為本地時區的位移。  這表示如果程式碼在另一台電腦上執行，使用字元常值指派的 <xref:System.DateTimeOffset> 值不會識別單一時間點。  
  
## DateTimeOffset 建構函式  
 <xref:System.DateTimeOffset> 型別定義有六個建構函式。  其中四個直接對應於 <xref:System.DateTime> 建構函式，並有一個型別為 <xref:System.TimeSpan> 的額外參數，此參數會定義日期和時間與 UTC 之間的位移。  這些建構函式可讓您根據其個別日期和時間元件的值來定義 <xref:System.DateTimeOffset> 值。  例如，下列程式碼使用這四個建構函式具現化 <xref:System.DateTimeOffset> 物件，其值全部都是 7\/1\/2008 12:05 AM \+01:00。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
 [!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]  
  
 請注意，當 <xref:System.DateTimeOffset> 物件的值使用 <xref:System.Globalization.PersianCalendar> 物件做為其建構函式的其中一個引數具現化，並顯示在主控台上時，會以西曆表示日期，而不是使用波斯曆表示。  若要使用波斯曆輸出日期，請參閱 <xref:System.Globalization.PersianCalendar> 主題中的範例。  
  
 另外兩個建構函式則會從 <xref:System.DateTime> 值來建立 <xref:System.DateTimeOffset> 物件。  其中的第一個建構函式有單一參數，這個 <xref:System.DateTime> 值會轉換成 <xref:System.DateTimeOffset> 值。  所產生 <xref:System.DateTimeOffset> 值的位移會根據建構函式單一參數的 <xref:System.DateTime.Kind%2A> 屬性而定。  如果其值為 <xref:System.DateTimeKind?displayProperty=fullName>，位移會設成等於 <xref:System.TimeSpan.Zero?displayProperty=fullName>。  否則，其位移就會設成等於本地時區的位移。  下列範例說明如何使用這個建構函式具現化表示 UTC 和本地時區的 <xref:System.DateTimeOffset> 物件：  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
 [!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]  
  
> [!NOTE]
>  呼叫具有單一 <xref:System.DateTime> 參數之 <xref:System.DateTimeOffset> 建構函式的多載，就等於將 <xref:System.DateTime> 值隱含轉換成 <xref:System.DateTimeOffset> 值。  
  
 第二個建構函式會從 <xref:System.DateTime> 值建立 <xref:System.DateTimeOffset> 物件，它有兩個參數：一個是要轉換的 <xref:System.DateTime> 值，另一個是表示日期和時間與 UTC 之間位移的 <xref:System.TimeSpan> 值。  此位移值必須對應於建構函式第一個參數的 <xref:System.DateTime.Kind%2A> 屬性，否則會擲回 <xref:System.ArgumentException>。  如果第一個參數的 <xref:System.DateTime.Kind%2A> 屬性是 <xref:System.DateTimeKind?displayProperty=fullName>，則第二個參數的值必須是 <xref:System.TimeSpan.Zero?displayProperty=fullName>。  如果第一個參數的 <xref:System.DateTime.Kind%2A> 屬性是 <xref:System.DateTimeKind?displayProperty=fullName>，則第二個參數的值必須是本機系統時區的位移。  如果第一個參數的 <xref:System.DateTime.Kind%2A> 屬性是 <xref:System.DateTimeKind?displayProperty=fullName>，則位移可以是任何有效值。  下列程式碼顯示這個建構函式的呼叫，以將 <xref:System.DateTime> 轉換成 <xref:System.DateTimeOffset> 值。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
 [!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]  
  
## 隱含型別轉換  
 <xref:System.DateTimeOffset> 型別支援一種隱含型別轉換：從 <xref:System.DateTime> 值轉換成 <xref:System.DateTimeOffset> 值 \(隱含型別轉換是指從某個型別轉換成另一個型別，而無須明確轉換 \(C\# 為 Cast，Visual Basic 為 Conversion\) 且不會遺失資訊\)。  它可讓您撰寫下列的程式碼。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
 [!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]  
  
 所產生 <xref:System.DateTimeOffset> 值的位移會根據 <xref:System.DateTime.Kind%2A?displayProperty=fullName> 屬性值而定。  如果其值為 <xref:System.DateTimeKind?displayProperty=fullName>，位移會設成等於 <xref:System.TimeSpan.Zero?displayProperty=fullName>。  如果其值為 <xref:System.DateTimeKind?displayProperty=fullName> 或 <xref:System.DateTimeKind?displayProperty=fullName>，位移就會設成等於本地時區的位移。  
  
## 剖析日期和時間的字串表示  
 <xref:System.DateTimeOffset> 型別支援四種方法，可將日期和時間的字串表示轉換成 <xref:System.DateTimeOffset> 值：  
  
-   <xref:System.DateTimeOffset.Parse%2A>，此方法會嘗試將日期和時間的字串表示轉換成 <xref:System.DateTimeOffset> 值，如果轉換失敗，會擲出例外狀況。  
  
-   <xref:System.DateTimeOffset.TryParse%2A>，此方法會嘗試將日期和時間的字串表示轉換成 <xref:System.DateTimeOffset> 值，如果轉換失敗，會傳回 `false`。  
  
-   <xref:System.DateTimeOffset.ParseExact%2A>，此方法會嘗試將指定格式的日期和時間字串表示轉換成 <xref:System.DateTimeOffset> 值。  如果轉換失敗，此方法會擲回例外狀況。  
  
-   <xref:System.DateTimeOffset.TryParseExact%2A>，此方法會嘗試將指定格式的日期和時間字串表示轉換成 <xref:System.DateTimeOffset> 值。  如果轉換失敗，此方法會傳回 `false`。  
  
 下列範例顯示這四個字串轉換方法的呼叫，以具現化 <xref:System.DateTimeOffset> 值。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
 [!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]  
  
## 請參閱  
 [日期、時間和時區](../../../docs/standard/datetime/index.md)