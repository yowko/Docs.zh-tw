---
title: "執行緒和執行緒處理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multiple threads
- threading [.NET Framework]
- threading [.NET Framework], multiple threads
ms.assetid: 5baac3aa-e603-4fa6-9f89-0f2c1084e6b1
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b57cac34009e13c27c6d34a0ab402f9ecbe08305
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="threads-and-threading"></a>執行緒和執行緒處理
作業系統會使用處理程序，來分隔不同一起執行的應用程式。 執行緒會作業系統會配置處理器時間的基本單位，而且多個執行緒可執行該程序內的程式碼。 每個執行緒各維護例外狀況處理常式、 排程的優先權和一組系統用來儲存的執行緒內容，直到它已排程的結構。 執行緒內容會包含執行緒順利繼續執行，包括在執行緒的主控件程序的位址空間中 CPU 暫存器和堆疊、 執行緒的集所需的所有資訊。  
  
 .NET Framework 進一步細分為輕量級 managed 子處理序，呼叫應用程式定義域，由的作業系統處理序<xref:System.AppDomain?displayProperty=nameWithType>。 一或多個 managed 的執行緒 (由<xref:System.Threading.Thread?displayProperty=nameWithType>) 可以在一個或多個相同的受管理處理序中的應用程式定義域中執行。 雖然每個應用程式定義域與單一執行緒啟動時，應用程式定義域中的程式碼可以建立其他應用程式定義域和其他執行緒。 結果是在相同的 managed 處理序; 的應用程式網域之間移動 managed 的執行緒可以自由地您可能必須只有一個執行緒在多個應用程式網域的網域間移動。  
  
 支援先佔式多工作業的作業系統從多個處理序，建立多個執行緒同時執行的效果。 其做法是除以需要它的執行緒之間可用的處理器時間，依序配置給每個執行緒的處理器時間配量。 當它的時間配量已超過，而另一個執行緒則繼續執行時，將暫停目前執行中執行緒。 系統會從一個執行緒切換到另一個，它會將儲存的先佔執行緒的執行緒內容，並重新載入已儲存的執行緒內容的執行緒佇列中的下一個執行緒。  
  
 長度的時間配量取決於作業系統和處理器。 因為每個時間配量很小，即使只有一個處理器來執行相同的時間，會顯示多個執行緒。 這是多處理器的系統上的實際狀況可執行的執行緒在可用的處理器之間的發佈位置。  
  
## <a name="when-to-use-multiple-threads"></a>使用多個執行緒的時機  
 需要使用者互動的軟體必須儘可能提供豐富的使用者經驗快速回應使用者的活動。 不過，在相同的時間，它必須執行需要盡快對使用者顯示資料的計算。 如果您的應用程式只使用一個執行緒的執行，您可以結合[非同步程式設計](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)與[.NET Framework 遠端處理](http://msdn.microsoft.com/en-us/eccb1d31-0a22-417a-97fd-f4f1f3aa4462)或[XML Web service](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c)建立使用 ASP.NET 的處理時間，其他電腦的功能使用的使用者及減少您的應用程式的資料處理時間增加自己回應性。 如果您進行大量輸入/輸出工作，您也可以使用以提高應用程式的回應 I/O 完成通訊埠。  
  
### <a name="advantages-of-multiple-threads"></a>多執行緒的優點  
 不過，使用多個執行緒，是最強大的技術可用來加快對使用者和處理幾乎相同的時間完成工作所需的資料。 一個處理器的電腦上多個執行緒可以建立此效果，請利用短暫的時間來處理在背景中的資料的使用者事件之間。 例如，使用者可以編輯試算表，而另一個執行緒正在重新計算的試算表中同一個應用程式其他部分。  
  
 不需修改相同的應用程式，會大幅增加在具有一個以上處理器的電腦上執行時，使用者滿意度。 單一應用程式定義域可以使用多個執行緒來完成下列工作：  
  
-   在網路上的網頁伺服器，和資料庫通訊。  
  
-   執行需要大量時間的作業。  
  
-   區分不同優先權的工作。 例如，較高優先順序的執行緒管理時間緊急工作，並較低優先順序的執行緒會執行其他工作。  
  
-   允許在配置給背景工作的時間時保持回應性，使用者介面。  
  
### <a name="disadvantages-of-multiple-threads"></a>多執行緒的缺點  
 建議您盡量，藉此將作業系統資源的使用降至最低並增進效能，使用執行緒數目。 執行緒也有資源需求，並視為設計您的應用程式時可能發生的衝突。 資源需求如下所示：  
  
-   系統會耗用記憶體的處理程序所需的內容資訊**AppDomain**物件和執行緒。 因此，處理序的數目， **AppDomain**物件和可以建立的執行緒會受到可用記憶體。  
  
-   追蹤的大量執行緒會耗用大量的處理器時間。 如果有太多執行緒，大部分不是會使大量的進度。 如果目前執行緒的大部分一個處理序中，其他處理序中的執行緒排定較少。  
  
-   控制使用多執行緒程式碼執行相當複雜，而且可以很多 bug 的來源。  
  
-   終結執行緒需要了解可能發生什麼事，以及處理這些問題。  
  
 提供共用的資源的存取權可能會產生衝突。 若要避免衝突，您必須同步處理，或控制共用資源的存取。 以同步存取正確 （在相同或不同的應用程式網域中） 的失敗可能會造成問題，像是死結 （兩個執行緒停止回應每個等候另一個完成時） 和競爭情形 （由於發生的異常結果非預期且嚴重依賴兩個事件的計時）。 系統會提供可以用來協調多個執行緒之間共用資源的同步處理物件。 減少執行緒數目，可以更輕鬆地同步處理資源。  
  
 需要同步處理的資源包括：  
  
-   系統資源 （例如通訊連接埠）。  
  
-   資源 （例如檔案控制代碼） 的多個處理程序共用。  
  
-   單一應用程式網域的資源 (例如 全域、 靜態和執行個體欄位) 多個執行緒存取。  
  
### <a name="threading-and-application-design"></a>執行緒和應用程式的設計  
 一般情況下，使用<xref:System.Threading.ThreadPool>類別是最簡單的方式處理多個執行緒進行相對較短的工作，不會封鎖其他執行緒，以及當您不希望特定排程的工作。 不過，有多種原因，若要建立您自己的執行緒：  
  
-   如果您需要為特定優先順序的工作。  
  
-   如果您有可能會執行很長的時間 （並因此而封鎖其他工作） 的工作。  
  
-   如果您需要將執行緒放入單一執行緒 apartment (所有**ThreadPool**執行緒都會在多執行緒的 apartment)。  
  
-   如果您需要一個與執行緒相關聯的固定識別。 比方說，您應該使用專用的執行緒中止的執行緒、 暫止，或依名稱探索它。  
  
-   如果您需要執行與使用者介面互動的背景執行緒，.NET Framework 2.0 版提供<xref:System.ComponentModel.BackgroundWorker>通訊使用的事件，與跨執行緒封送處理，在使用者介面執行緒的元件。  
  
### <a name="threading-and-exceptions"></a>執行緒和例外狀況  
 處理執行緒中的例外狀況。 執行緒，甚至是背景執行緒中的未處理例外狀況通常會終止處理序。 這項規則有三個例外狀況：  
  
-   A<xref:System.Threading.ThreadAbortException>因為在執行緒中擲回<xref:System.Threading.Thread.Abort%2A>呼叫。  
  
-   <xref:System.AppDomainUnloadedException>正在卸載應用程式定義域，因為在執行緒中擲回。  
  
-   Common Language Runtime 或主應用程式處理序會結束這個執行緒。  
  
 如需詳細資訊，請參閱[Managed 執行緒中的例外狀況](../../../docs/standard/threading/exceptions-in-managed-threads.md)。  
  
> [!NOTE]
>  在.NET framework 1.0 和 1.1 版中，通用語言執行平台以無訊息模式設陷某些例外狀況，例如在執行緒集區。 這可能會破壞應用程式狀態，最終導致應用程式沒有回應，這可能很難偵錯。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.ThreadPool>  
 <xref:System.ComponentModel.BackgroundWorker>  
 [同步處理多執行緒處理的資料](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 [Managed 執行緒集區](../../../docs/standard/threading/the-managed-thread-pool.md)
