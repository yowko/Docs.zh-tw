---
title: "評估使用 .NET Native 的啟動改善"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4d25b24-9c1a-4b3e-9705-97ba0d6c0289
caps.latest.revision: 7
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2486aa4daa5682f09b9cd5da8eac4b9071671a3c
ms.contentlocale: zh-tw
ms.lasthandoff: 08/21/2017

---
# <a name="measuring-startup-improvement-with-net-native"></a>評估使用 .NET Native 的啟動改善
[!INCLUDE[net_native](../../../includes/net-native-md.md)] 可大幅改善應用程式的啟動時間。 在可攜式、低電源的裝置上，以及用於複雜的應用程式時，這項改良功能尤其明顯。 本主題將協助您著手進行測量這項啟動改良功能所需的基本檢測。  
  
 為加速效能調查，.NET Framework 和 Windows 使用一個名為 Windows 事件追蹤 (ETW) 的事件架構，可讓您的應用程式在事件發生時通知工具。 然後您可以使用名為 PerfView 的工具，輕鬆檢視及分析 ETW 事件。 本主題將說明如何：  
  
-   使用 <xref:System.Diagnostics.Tracing.EventSource> 類別來發出事件。  
  
-   使用 PerfView 來收集這些事件。  
  
-   使用 PerfView 來顯示這些事件。  
  
## <a name="using-eventsource-to-emit-events"></a>使用 EventSource 來發出事件  
 <xref:System.Diagnostics.Tracing.EventSource> 提供可用來建立自訂事件提供者的基底類別。 一般而言，您會建立 <xref:System.Diagnostics.Tracing.EventSource> 的子類別，並以您自己的事件方法來包裝 `Write*` 方法。 通常會為每個 <xref:System.Diagnostics.Tracing.EventSource> 使用單一子句模式。  
  
 例如，下列範例中的類別可以用來測量兩項效能特性：  
  
-   到呼叫 `App` 類別建構函式之前的時間。  
  
-   到呼叫 `MainPage` 建構函式之前的時間。  
  
 [!code-csharp[ProjectN_ETW#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw1.cs#1)]  
  
 這裡有幾件事要特別注意。 首先，單一子句會建立在 `AppEventSource.Log` 中。 該執行個體將會用於所有記錄。 第二，每個事件方法都有 <xref:System.Diagnostics.Tracing.EventAttribute>。 這樣有助於工具將 <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> 方法的索引與在 `AppEventSource` 上呼叫的方法建立關聯。  
  
 請注意，這些事件僅為範例。 大部分應用程式程式碼會在這些事件之後執行。 您應該了解程式碼中的哪些事件對應至使用者互動、評量並改善這些基準測試。 此外，事件本身只會及時記錄單一執行個體。 如果每項作業都有成對的開始和停止事件，通常會很有用。 檢查應用程式啟動時，開始事件通常是作業系統發出的「處理/開始」事件。  
  
 例如，假設您正在建立 RSS 閱讀程式。 幾個記錄事件的有趣位置是：  
  
-   第一次呈現主頁面時。  
  
-   從本機儲存體將舊的 RSS 報導還原序列化時。  
  
-   您的應用程式開始同步處理新的報導時。  
  
-   您的應用程式已經完成同步處理新的報導時。  
  
 檢測應用程式很簡單：只要在衍生的類別上呼叫適當的方法即可。 使用先前範例中的 `AppEventSource`，您可以檢測應用程式，如下所示：  
  
 [!code-csharp[ProjectN_ETW#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw2.cs#2)]  
  
 檢測應用程式之後，您即可準備收集事件。  
  
## <a name="gathering-events-with-perfview"></a>使用 PerfView 收集事件  
 PerfView 會使用 ETW 事件來協助您在應用程式上進行各種效能調查。 它也有包含組態 GUI，可讓您針對不同類型的事件開啟或關閉記錄功能。 PerfView 是一種免費工具，可以從 [Microsoft 下載中心](http://www.microsoft.com/download/details.aspx?id=28567)下載。 如需詳細資訊，請觀看 [PerfView 教學課程影片](http://channel9.msdn.com/Series/PerfView-Tutorial)。  
  
> [!NOTE]
>  PerfView 不能用來在 ARM 系統上收集事件。 若要在 ARM 系統上收集事件，請使用 Windows 效能記錄程式 (WPR)。 如需詳細資訊，請參閱 [Vance Morrison 的部落格文章](http://blogs.msdn.com/b/vancem/archive/2012/12/19/collecting-etw-perfview-data-on-an-windows-rt-winrt-arm-surface-device.aspx)。  
  
 您也可以從命令列叫用 PerfView。 如果只要從您的提供者記錄事件，請開啟 [命令提示字元] 視窗，並輸入命令：  
  
```  
perfview -KernelEvents:Process -OnlyProviders:*MyCompany-MyApp collect outputFile   
```  
  
 其中：  
  
 `-KernelEvents:Process`  
 指出您想要知道處理程序何時開始和停止。 您需要應用程式的「處理/開始」事件，以將其從其他事件時間減去。  
  
 `-OnlyProviders:*MyCompany-MyApp`  
 請關閉 PerfView 預設開啟的其他提供者，並開啟 MyCompany-MyApp 提供者。  (星號表示其為 <xref:System.Diagnostics.Tracing.EventSource>。)  
  
 `collect outputFile`  
 指出您想要開始收集資料，並將資料儲存至 outputFile.etl.zip。  
  
 啟動 PerfView 之後，請執行您的應用程式。 執行您的應用程式時，要記得幾件事：  
  
-   使用發行組建，而不是偵錯組建。 偵錯組建通常會包含額外的錯誤檢查和錯誤處理程式碼，可能會使您的應用程式執行速度比預期慢。  
  
-   附加偵錯工具來執行您的應用程式會影響應用程式的效能。  
  
-   Windows 會使用多個快取策略來加速應用程式啟動時間。 如果您的應用程式目前快取在記憶體中，而且不必從磁碟載入，則啟動速度會較快。 若要確保一致性，請在開始測量之前，將您的應用程式開始並關閉數次。  
  
 如果您已經執行您的應用程式，而 PerfView 可以收集發出的事件，請選擇 [停止收集] 按鈕。 一般而言，您應該先停止收集，再關閉應用程式，這樣才不會收集到無關的事件。 不過，如果您要測量關機或暫停效能，您就會想要繼續收集。  
  
## <a name="displaying-the-events"></a>顯示事件  
 若要檢視已收集的事件，請使用 PerfView 來開啟您建立的 .etl 或 .etl.zip 檔案，然後選擇 [事件]。 ETW 將已經收集大量事件的相關資訊，包括來自其他處理序的事件。 若要專注您的調查，請在 [事件] 檢視中填寫下列文字方塊：  
  
-   在 [Process Filter] (處理序篩選) 方塊中，指定您的應用程式名稱 (不含 ".exe")。  
  
-   在 [Event Types Filter] (事件類型篩選) 方塊中，指定 `Process/Start | MyCompany-MyApp`。 這會從 MyCompany-MyApp 和 Windows 核心/處理/開始事件設定事件的篩選。  
  
 選取左窗格中列出的所有事件 (Ctrl-A)，然後選擇 **Enter** 鍵。 現在，您應該可以看到每個事件的時間戳記。 這些時間戳記相對於追蹤的開始，所以您必須處理序的開始時間減去每個事件的時間，以識別自啟動後所耗用的時間。 如果您使用 Ctrl+按一下的方式來選取兩個時間戳記，您會看到其之間的差異顯示在頁面底部的狀態列中。 這樣可以讓您很容易在顯示器中查看任何兩個事件之間的經歷時間 (包括處理開始)。 您可以開啟檢視的快顯功能表，並從一些有用的選項中選取，像是匯出至 CSV 檔案，或是開啟 Microsoft Excel 來儲存或處理資料。  
  
 針對您原始的應用程式以及使用 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 工具鏈來建置的版本重複此程序，就可以比較出效能的差異。   [!INCLUDE[net_native](../../../includes/net-native-md.md)] 應用程式的啟動速度通常會比非 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 應用程式快。 如果您有挖掘更深入的資料，PerfView 也可以識別出程式碼中最耗時間的部分。 如需詳細資訊，請觀看 [PerfView 教學課程](http://channel9.msdn.com/Series/PerfView-Tutorial)或閱讀 [Vance Morrison 的部落格文章](http://blogs.msdn.com/b/vancem/archive/2011/12/28/publication-of-the-perfview-performance-analysis-tool.aspx)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Diagnostics.Tracing.EventSource>

