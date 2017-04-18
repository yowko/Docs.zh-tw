---
title: "如何：列舉電腦上展示的時區 | Microsoft Docs"
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
  - "列舉時區 [.NET Framework]"
  - "時區 [.NET Framework], 列舉"
ms.assetid: bb7a42ab-6bd9-4c5c-b734-5546d51f8669
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：列舉電腦上展示的時區
系統上必須有時區的相關資訊，才能順利使用指派的時區。  Windows XP 及 Windows Vista 作業系統會將這項資訊儲存在登錄中。  然而，雖然全世界的時區總數很多，但是登錄中只有其中一部分的資訊而已。  此外，登錄本身是個動態結構，會受到刻意或意外變更而改變。  因此，應用程式不一定會一直假設系統上定義了或可以使用特定時區。  對於許多使用時區資訊應用程式的應用程式而言，第一步要作的就是判斷本機系統上是否有所需的時區，或是提供使用者時區清單以供選取。  應用程式必須列舉本機系統上所定義的時區才能這麼做。  
  
> [!NOTE]
>  如果應用程式必須藉助特定時區，而本機系統上可能沒有定義這個時區，應用程式就可以利用序列化和還原序列化時區資訊的方式，確保時區存在系統中。  接著時區就可以新增至清單控制項，供應用程式使用者選取。  如需詳細資訊，請參閱 [如何：將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)及 [如何：從內嵌資源還原時區](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)。  
  
### 列舉本機系統上存在的時區  
  
1.  呼叫 <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=fullName> 方法。  這個方法會傳回一個 <xref:System.TimeZoneInfo> 物件的泛型 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 集合。  集合中的項目會根據 <xref:System.TimeZoneInfo.DisplayName%2A> 屬性排序。  例如：  
  
     [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
     [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]  
  
2.  使用 `foreach` 迴圈 \(C\#\) 或 `For Each`…`Next` 迴圈 \(Visual Basic\)，列舉集合中的個別 <xref:System.TimeZoneInfo> 物件，並在每一個物件上執行必要的處理程序。  例如，下列程式碼會列舉步驟 1 中所傳回 <xref:System.TimeZoneInfo> 物件的 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 集合，並列出主控台中每一個時區的顯示名稱。  
  
     [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
     [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]  
  
### 向使用者呈現本機系統上的時區清單  
  
1.  呼叫 <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=fullName> 方法。  這個方法會傳回一個 <xref:System.TimeZoneInfo> 物件的泛型 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 集合。  
  
2.  將步驟 1 中所傳回的集合指派給 Windows Form 或 ASP.NET 清單控制項的 `DataSource` 屬性。  
  
3.  擷取使用者選擇的 <xref:System.TimeZoneInfo> 物件。  
  
 本範例提供 Windows 應用程式的圖例。  
  
## 範例  
 本範例會啟動一個 Windows 應用程式，在清單方塊中顯示系統上所定義的時區。  然後範例會顯示一個對話方塊，內含使用者所選取時區物件的 <xref:System.TimeZoneInfo.DisplayName%2A> 屬性值。  
  
 [!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
 [!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]  
  
 大部分的清單控制項 \(例如 <xref:System.Windows.Forms.ListBox?displayProperty=fullName> 或 <xref:System.Web.UI.WebControls.BulletedList?displayProperty=fullName> 控制項\) 可讓您將物件變數的集合，指派給 `DataSource` 屬性，只要該集合實作 <xref:System.Collections.IEnumerable> 介面就可以 \(由泛型 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 類別執行這個動作\)。如果要顯示集合中的個別物件，控制項會呼叫此物件的 `ToString` 方法以擷取用來代表物件的字串。  如果是 <xref:System.TimeZoneInfo> 物件，`ToString` 方法會傳回 <xref:System.TimeZoneInfo> 物件的顯示名稱 \(<xref:System.TimeZoneInfo.DisplayName%2A> 屬性的值\)。  
  
> [!NOTE]
>  因為清單控制項會呼叫物件的 `ToString` 方法，所以您可以將 <xref:System.TimeZoneInfo> 物件的集合指派給控制項、讓控制項顯示每一個物件有意義的名稱，以及擷取使用者所選擇的 <xref:System.TimeZoneInfo> 物件。  這麼做就可以不必擷取集合中每一個物件的字串、將這個字串指派給集合 \(集合會被指派給控制項的 `DataSource` 屬性\)、擷取使用者所選取的字串，以及使用這個字串來擷取所描述的物件。  
  
## 編譯程式碼  
 這個範例需要：  
  
-   將 System.Core.dll 的參考加入至專案中。  
  
-   匯入下列命名空間：  
  
     <xref:System> \(C\# 程式碼中\)  
  
     <xref:System.Collections.ObjectModel>  
  
## 請參閱  
 [日期、時間和時區](../../../docs/standard/datetime/index.md)   
 [如何：將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)   
 [如何：從內嵌資源還原時區](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)