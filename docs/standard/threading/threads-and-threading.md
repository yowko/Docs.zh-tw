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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 114fb704a622d92ab8e92fa866fa0fc9bebf4e58
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="threads-and-threading"></a>執行緒和執行緒處理
作業系統會使用處理序來分隔它們所執行的各種不同應用程式。 執行緒是作業系統配置處理器時間的基本單位，而在該處理序內可以有多個執行緒執行程式碼。 每個執行緒都保有例外處理常式、排程優先順序，以及系統用來儲存執行緒內容直到執行緒被排定為止的一組結構。 執行緒內容包括執行緒在執行緒主機處理序的位址空間中順暢繼續執行所需的所有資訊，包括執行緒的一組 CPU 暫存器和堆疊。  
  
 .NET Framework 將作業系統處理序進一步細分成輕量型受控子處理序 (稱為應用程式定義域)，由 <xref:System.AppDomain?displayProperty=nameWithType> 代表。 一或多個受控執行緒 (由 <xref:System.Threading.Thread?displayProperty=nameWithType> 代表) 可以在相同受控處理序內的一個或任何數量的應用程式定義域中執行。 雖然每個應用程式定義域都是從單一執行緒開始，但該應用程式定義域中的程式碼可以建立額外的應用程式定義域和額外的執行緒。 因此，受控執行緒可以在相同受控處理序內的應用程式定義域之間自由移動；您可以只使用一個執行緒在數個應用程式定義域之間移動。  
  
 作業系統如果支援先佔式多工作業，便可產生從多個處理序同時執行多個執行緒的效果。 做法是將可用的處理器時間分配給有需要的執行緒，將處理器時間配量依序配置給每個執行緒。 目前執行中的執行緒如果時間配量已過，就會暫停，而會由另一個執行緒繼續執行。 當系統從一個執行緒切換到另一個執行緒時，會儲存先佔執行緒的執行緒內容，然後重新載入執行緒佇列中下一個執行緒的已儲存執行緒內容。  
  
 時間配量的長短取決於作業系統和處理器。 由於每個時間配量都相當小，因此即使只有一個處理器，多個執行緒也會看似同時執行。 這實際上就是多處理器系統上的情況，其中會在可用的處理器之間分配可執行的執行緒。  
  
## <a name="when-to-use-multiple-threads"></a>使用多執行緒的時機  
 軟體如果需要使用者互動，就必須能夠儘快回應使用者的活動，才能提供豐富的使用者體驗。 不過，同時它也必須執行儘快向使用者顯示資料所需的計算。 如果您的應用程式只使用一個執行緒，您可以將[非同步程式設計](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)與 [.NET Framework 遠端處理](http://msdn.microsoft.com/library/eccb1d31-0a22-417a-97fd-f4f1f3aa4462)或使用 ASP.NET 建立的 [XML Web 服務](http://msdn.microsoft.com/library/1e64af78-d705-4384-b08d-591a45f4379c) 結合，以除了您自己電腦的處理時間之外，再利用其他電腦的處理時間，來加快對使用者的回應速度及縮短您應用程式的資料處理時間。 如果您要執行大量輸入/輸出的工作，您也可以使用 I/O 完成連接埠來加快應用程式的回應速度。  
  
### <a name="advantages-of-multiple-threads"></a>多執行緒的優點  
 無論如何，使用多個執行緒都是最強大的可用技術，不僅可加快對使用者的回應速度，還可處理讓作業幾乎同時完成所需的資料。 在有一個處理器的電腦上，多執行緒即可產生此效果，利用使用者事件之間的短暫時間在背景中處理資料。 例如，使用者可以編輯試算表，而同時另一個執行緒則在相同的應用程式內重新計算該試算表的其他部分。  
  
 相同的應用程式無須經過任何修改，在多處理器電腦上執行時，即可大幅提升客戶滿意度。 單一應用程式定義域可以使用多個執行緒來完成下列工作：  
  
-   透過網路與 Web 伺服器及資料庫進行通訊。  
  
-   執行耗費大量時間的作業。  
  
-   區分不同優先順序的工作。 例如，高優先順序執行緒會應付緊急工作，而低優先順序執行緒則執行其他工作。  
  
-   讓使用者介面保持回應，同時又配置時間給背景工作。  
  
### <a name="disadvantages-of-multiple-threads"></a>多執行緒的缺點  
 建議您儘可能只使用少量的執行緒，這樣可以將作業系統資源的使用量降到最低而提升效能。 設計您的應用程式時，執行緒也有資源需求和潛在的衝突需要考量。 資源需求如下：  
  
-   系統會耗用記憶體來處理處理序、**AppDomain** 物件及執行緒所需的內容資訊。 因此，可建立的處理序、**AppDomain** 物件及執行緒數量會受到可用記憶體的限制。  
  
-   追蹤大量執行緒會耗用大量的處理器時間。 如果執行緒太多，則大多數執行緒將不會有任何明顯的進展。 如果大多數目前的執行緒都在一個處理序中，其他處理序中的執行緒排程頻率就會較低。  
  
-   控制具有許多執行緒的程式碼執行相當複雜，且可能成為許多 Bug 的來源。  
  
-   若要終結執行緒，必須知道其可能的後果及如何處理這些問題。  
  
 提供對資源的共用存取權可能會造成衝突。 若要避免衝突，您必須同步處理共用資源，或控制對共用資源的存取。 如果無法正確地同步處理存取權 (在相同或不同的應用程式定義域中)，可能會導致發生問題，例如死結 (兩個執行緒互相等候對方完成而停止回應) 和競爭條件 (因非預期嚴重倚賴兩個事件的時間而發生異常結果時)。 系統會提供同步處理物件，可用來協調多個執行緒之間的資源共用。 減少執行緒數量可以讓資源的同步處理變得更容易。  
  
 需要同步處理的資源包括：  
  
-   系統資源 (例如通訊連接埠)。  
  
-   多個處理序所共用的資源 (例如檔案控制代碼)。  
  
-   多個執行緒所存取之單一應用程式定義域的資源 (例如全域、靜態及執行個體欄位)。  
  
### <a name="threading-and-application-design"></a>執行緒和應用程式設計  
 一般而言，針對不會阻礙其他執行緒的較簡短工作，以及當您不打算進行任何特定的工作排程時，使用 <xref:System.Threading.ThreadPool> 類別是處理多個執行緒的最簡單方法。 不過，有幾個您應該建立自己的執行緒的理由：  
  
-   如果您需要一個有特定優先順序的工作。  
  
-   如果您有一個可能需要執行很久的工作 (因而會阻礙其他工作)。  
  
-   如果您需要將執行緒放入單一執行緒 Apartment 中 (所有 **ThreadPool** 執行緒都會在多執行緒 Apartment 中)。  
  
-   如果您需要有一個與執行緒關聯的穩定身分識別。 例如，您應該使用專用執行緒來中止該執行緒、暫停它，或依名稱來探索它。  
  
-   如果您需要執行與使用者介面互動的背景執行緒，.NET Framework 2.0 版有提供一個使用事件來進行通訊的 <xref:System.ComponentModel.BackgroundWorker> 元件，可跨執行緒封送處理至使用者介面執行緒。  
  
### <a name="threading-and-exceptions"></a>執行緒和例外狀況  
 請務必處理執行緒中的例外狀況。 執行緒 (甚至是背景執行緒) 中未處理的例外狀況通常會終止處理序。 這項規則有三個例外狀況：  
  
-   因為呼叫了 <xref:System.Threading.Thread.Abort%2A>，而導致執行緒中擲回 <xref:System.Threading.ThreadAbortException>。  
  
-   因為將應用程式定義域卸載，而導致執行緒中擲回 <xref:System.AppDomainUnloadedException>。  
  
-   Common Language Runtime 或主應用程式處理序會結束這個執行緒。  
  
 如需詳細資訊，請參閱[受控執行緒中的例外狀況](../../../docs/standard/threading/exceptions-in-managed-threads.md)。  
  
> [!NOTE]
>  在 .NET Framework 1.0 和 1.1 版中，通用語言執行平台會以無訊息模式截獲一些例外狀況 (例如在執行緒集區執行緒中)。 這可能會破壞應用程式狀態，最終導致應用程式沒有回應，而可能讓偵錯工作變得相當困難。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Threading.ThreadPool>  
 <xref:System.ComponentModel.BackgroundWorker>  
 [同步處理多執行緒處理的資料](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 [Managed 執行緒集區](../../../docs/standard/threading/the-managed-thread-pool.md)
