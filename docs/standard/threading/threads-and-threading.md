---
title: "Threads and Threading | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "multiple threads"
  - "threading [.NET Framework]"
  - "threading [.NET Framework], multiple threads"
ms.assetid: 5baac3aa-e603-4fa6-9f89-0f2c1084e6b1
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# Threads and Threading
作業系統使用處理序來分隔它們正在執行的不同應用程式。  執行緒是作業系統分配處理器時間的基本單元，而一個處理序中可有多個執行緒執行程式碼。  每個執行緒都維護例外狀況處理常式 \(Exception Handler\)、排程優先權，以及系統用來在執行緒排程之前儲存其內容的一組結構。  執行緒內容包含執行緒在執行緒之主處理序的位址空間中順利繼續執行所需的所有資訊，其中包括執行緒的一組 CPU 暫存器和堆疊。  
  
 .NET Framework 會進一步將作業系統處理序細分為輕量型 Managed 子處理序 \(稱為應用程式定義域\)，由 <xref:System.AppDomain?displayProperty=fullName> 表示。  一個或多個 Managed 執行緒 \(由 <xref:System.Threading.Thread?displayProperty=fullName> 表示\) 可在相同 Managed 處理序內的一個或數個應用程式定義域中執行。  雖然每個應用程式定義域是由單一執行緒所啟動，但應用程式定義域中的程式碼可建立其他應用程式定義域和其他執行緒。  結果是，Managed 執行緒可在同樣 Managed 處理序中的各個應用程式定義域之間自由移動；而您只能有一個執行緒在數個應用程式定義域之間移動。  
  
 支援先佔式多工的作業系統能夠從多個處理序產生同時執行多個執行緒的效果。  方法是將可用的處理器時間分給需要它的執行緒，依序將處理序時間量分配給每個執行緒。  目前執行的執行緒會在分配給它的時間量超過時暫止，同時另一個執行緒則繼續執行。  當系統從一執行緒切換至另一執行緒時，它會儲存先佔執行緒的執行緒內容，然後重新載入執行緒佇列中下一個執行緒的已存執行緒內容。  
  
 時間量的長度則要視作業系統和處理器而定。  由於每段時間極短，因此即使只有一個處理器，多個執行緒看起來還是像同時執行一樣。  這就是多處理器系統上的實際狀況，其中可執行的執行緒會在可用的處理器中散發。  
  
## 何時使用多個執行緒  
 需要使用者互動的軟體必須儘快回應使用者的活動，以便提供豐富的使用者經驗。  不過，同時它也必須執行需要的計算以儘快提供使用者資料。  如果您的應用程式只使用一個執行緒，您可將[非同步程式設計](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)和 [.NET 遠端處理](http://msdn.microsoft.com/zh-tw/eccb1d31-0a22-417a-97fd-f4f1f3aa4462)或使用 ASP.NET 建立的 [XML Web Service](http://msdn.microsoft.com/zh-tw/1e64af78-d705-4384-b08d-591a45f4379c) 結合一起，如此在使用本身的處理時間之外還可加上其他電腦的處理時間，藉此增加對使用者的回應性，並減少您的應用程式處理資料的時間。  如果您是執行耗用大量的輸出入 \(I\/O\) 工作，您也可使用 I\/O 完成通訊埠來增加應用程式的回應速度。  
  
### 多執行緒的優點  
 不過，使用多個執行緒是現行最能夠增加對使用者的回應速度，而且又能幾乎同時處理完成工作所需的資料。  在具有一個處理器的電腦上，多個執行緒利用使用者事件之間的短暫時間來在背景 \(Background\) 處理資料就可達到這種效果。  例如，使用者可在另一個執行緒重新計算試算表其他部分時，在同一應用程式內編輯試算表。  
  
 在相同的條件下，當在具有多個處理器的電腦上執行時，相同的應用程式會大幅提升使用者的滿意度。  您的單一應用程式定義域可使用多個執行緒來完成下列工作：  
  
-   在網路上與 Web 伺服器和資料庫通訊。  
  
-   執行需耗用大量時間的作業。  
  
-   區分不同優先權的工作。  例如，高優先權執行緒處理時間緊急的工作，而低優先權執行緒執行其他工作。  
  
-   允許使用者介面保持回應性，同時將時間分配給背景工作。  
  
### 多執行緒的缺點  
 建議您盡量少用執行緒，這樣可使作業系統資源的使用量降到最低並增進效能。  當您設計應用程式時，也應將執行緒處理的資源需求和可能發生的衝突列入考量。  資源需求如下：  
  
-   系統會為處理序、**AppDomain** 物件和執行緒所需的內容資訊耗用記憶體。  因此，可以建立的處理序、**AppDomain** 物件和執行緒數量就會受到可用記憶體的限制。  
  
-   記錄大量執行緒會耗用相當多的處理器時間。  如果同時有太多執行緒，則其中多數的進度會相當緩慢。  如果目前的執行緒大都在同一處理序中，則排到其他處理序中執行緒的機會就會減少。  
  
-   控制其中使用許多執行緒的程式碼執行是相當複雜的一件事，而且可能會產生許多錯誤。  
  
-   您需要知道終結執行緒時可能發生何種情況，並知道如何處理。  
  
 提供資源的共用存取可能會產生衝突。  若要避免衝突發生，您必須同步或控制共用資源的存取。  無法適當同步存取 \(無論是在相同或不同的應用程式定義域中\) 可能會引發死結 \(兩個執行緒停止回應來等候對方完成工作\) 和競爭情形 \(因未預期且嚴重依賴兩事件執行時間而發生的異常結果\)。  系統提供可用來協調多個執行緒之間資源共用的同步物件 \(Synchronization Object\)。  減少執行緒的數量會使同步處理資源更為容易。  
  
 需要同步的資源包括：  
  
-   系統資源 \(例如通訊連接埠\)。  
  
-   多個處理序共用的資源 \(例如檔案控制代碼，File Handle\)。  
  
-   多個執行緒存取的單一應用程式定義域的資源 \(例如全域、靜態和執行個體欄位\)。  
  
### 執行緒處理和應用程式設計  
 一般來說，針對不會阻礙其他執行緒的較短時間工作，以及當您的工作沒有特定排程時，使用 <xref:System.Threading.ThreadPool> 類別是處理多個執行緒最簡單的方法。  不過，要建立您自己的執行緒的原因如下：  
  
-   如果您要使一項工作具有特定的優先權。  
  
-   如果您要使一項工作可長期執行 \(並因此而封鎖其他工作\)。  
  
-   如果您必須將執行緒置入單一執行緒 Apartment 中 \(所有的 **ThreadPool** 執行緒均置於多執行緒 Apartment 中\)。  
  
-   如果您需要與執行緒關聯的穩定識別。  例如，您應使用專用執行緒來中止、暫止或以名稱尋找它。  
  
-   如果您需要執行與使用者介面互動的背景執行緒，.NET Framework 2.0 版提供了 <xref:System.ComponentModel.BackgroundWorker> 元件，可使用事件來進行溝通，並以跨執行緒方式封送處理至使用者介面執行緒。  
  
### 執行緒處理和例外狀況  
 一定要處理執行緒中的例外狀況。  執行緒 \(甚至是背景執行緒\) 中未處理的例外狀況，通常會結束處理序。  此項規則有三個例外情形：  
  
-   在執行緒中擲回 <xref:System.Threading.ThreadAbortException>，因為已呼叫 <xref:System.Threading.Thread.Abort%2A>。  
  
-   在執行緒中擲回 <xref:System.AppDomainUnloadedException>，因為正在卸載應用程式定義域。  
  
-   Common Language Runtime 或主應用程式處理序會結束此執行緒。  
  
 如需詳細資訊，請參閱 [Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md)。  
  
> [!NOTE]
>  在 .NET Framework 1.0 和 1.1 版中，Common Language Runtime 會以無訊息模式截獲某些例外狀況，例如，在執行緒集區執行緒中。  如此一來，可能會損壞應用程式狀態，而最後導致應用程式無回應，這樣可能會讓偵錯工作變得相當困難。  
  
## 請參閱  
 <xref:System.Threading.ThreadPool>   
 <xref:System.ComponentModel.BackgroundWorker>   
 [Synchronizing Data for Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)   
 [The Managed Thread Pool](../../../docs/standard/threading/the-managed-thread-pool.md)