---
title: "Garbage Collection Notifications | Microsoft Docs"
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
  - "garbage collection, notifications"
ms.assetid: e12d8e74-31e3-4035-a87d-f3e66f0a9b89
caps.latest.revision: 23
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 23
---
# Garbage Collection Notifications
在某些情況下，由通用語言執行階段所執行的完整記憶體回收\(也就是第二代集合\)可能會降低效能。  特別是處理大量要求的伺服器，這可能會造成問題，因為在這種情況下，長時間的記憶體回收可能會導致要求逾時。  為避免完整回收在重要期間發生，您可由系統通知完整記憶體回收即將進行，然後採取動作將工作負載重新導向至另一個伺服器執行個體。  您也可以自行引發回收，只要目前伺服器執行個體不需要處理要求即可。  
  
 <xref:System.GC.RegisterForFullGCNotification%2A> 方法會註冊通知，當執行階段偵測到完整記憶體回收即將進行時，即發出通知。  此通知分為兩部分：何時即將進行完整記憶體回收，以及完整記憶體回收何時完成。  
  
> [!WARNING]
>  只有封鎖中的記憶體回收會引發告知。  當 [\<gcConcurrent\>](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) 組態項目已啟用，背景記憶體回收就不會引發告知。  
  
 若要判斷何時發出通知，請使用 <xref:System.GC.WaitForFullGCApproach%2A> 和 <xref:System.GC.WaitForFullGCComplete%2A> 方法。  一般來說，您可以在 `while` 迴圈 \(Loop\) 中使用這些方法，以持續取得顯示通知狀態的 <xref:System.GCNotificationStatus> 列舉型別 \(Enumeration\)。  如果該值為 <xref:System.GCNotificationStatus>，您可以執行下列動作：  
  
-   為回應 <xref:System.GC.WaitForFullGCApproach%2A> 方法所取得的通知，您可以重新導向工作負載並自行引發回收。  
  
-   為回應 <xref:System.GC.WaitForFullGCComplete%2A> 方法所取得的通知，您可以讓目前伺服器執行個體能夠再次處理要求。  您也可以收集資訊。  例如，您可以使用 <xref:System.GC.CollectionCount%2A> 方法記錄回收次數。  
  
 <xref:System.GC.WaitForFullGCApproach%2A> 和 <xref:System.GC.WaitForFullGCComplete%2A> 方法是設計一起運作。  若兩個方法未一起使用，可能產生不確定的結果。  
  
## 完整記憶體回收  
 當發生下列任何情況時，執行階段會引發完整記憶體回收：  
  
-   已有足夠的記憶體升級為層代 2，導致下一次的層代 2 回收。  
  
-   已有足夠的記憶體升級為大型物件堆積，導致下一次的層代 2 回收。  
  
-   其他因素導致層代 1 回收提升為層代 2 回收。  
  
 您在 <xref:System.GC.RegisterForFullGCNotification%2A> 方法中指定的臨界值會套用到前兩種情況。  不過，在第一種情況下，您不一定會在設定的臨界值達到時收到通知，原因有兩個：  
  
-   執行階段不會檢查每次的小型物件配置 \(基於效能考量\)。  
  
-   只有層代 1 回收會將記憶體升級為層代 2。  
  
 第三種情況也會使得收到通知的時間變得不確定。  雖然這不是絕對有用的方法，但若能在這段期間重新導向要求或自行引發回收，有助於減少不當完整記憶體回收所帶來的影響。  
  
## 通知臨界值參數  
 <xref:System.GC.RegisterForFullGCNotification%2A> 方法有兩個參數，分別指定層代 2 物件和大型物件堆積的臨界值。  當達到這些值時，就應發出記憶體回收通知。  下表描述這些參數。  
  
|參數|說明|  
|--------|--------|  
|`maxGenerationThreshold`|範圍從 1 到 99 的數字，根據層代 2 中升級的物件，指定何時應引發通知。|  
|`largeObjectHeapThreshold`|範圍從 1 到 99 的數字，根據大型物件堆積中所配置的物件，指定何時應引發通知。|  
  
 如果您指定的值太高，您很可能會收到通知，但有可能會等一段很長的時間，執行階段才會引發回收。  如果您自行引發回收，您所回收的物件可能比執行階段引發的回收還多。  
  
 如果您指定的值太低，執行階段引發回收時可能沒有足夠的時間通知您。  
  
## 範例  
  
### 說明  
 在下列範例中，有一組伺服器處理收到的 Web 要求。  為模擬處理要求的工作負載，會將位元組陣列加入到 <xref:System.Collections.Generic.List%601> 集合。  每台伺服器都會註冊記憶體回收通知，並在 `WaitForFullGCProc` 使用者方法上啟動執行緒，以持續監視 <xref:System.GC.WaitForFullGCApproach%2A> 和 <xref:System.GC.WaitForFullGCComplete%2A> 方法傳回的 <xref:System.GCNotificationStatus> 列舉。  
  
 當系統引發通知時，<xref:System.GC.WaitForFullGCApproach%2A> 和 <xref:System.GC.WaitForFullGCComplete%2A> 方法會呼叫各自的事件處理使用者方法：  
  
-   `OnFullGCApproachNotify`  
  
     此方法會呼叫 `RedirectRequests` 使用者方法，指示要求佇列伺服器暫停傳送要求至該伺服器。  模擬的方式是將類別層級變數 `bAllocate` 設為 `false`，這樣就不會再配置物件。  
  
     接著會呼叫 `FinishExistingRequests` 使用者方法，以完成處理暫止的伺服器要求。  模擬的方式是清除 <xref:System.Collections.Generic.List%601> 集合。  
  
     最後再引發記憶體回收，因為工作負載變輕。  
  
-   `OnFullGCCompleteNotify`  
  
     此方法會呼叫使用者方法 `AcceptRequests` 以繼續接受要求，因為伺服器不再容易受到完整記憶體回收的影響。  模擬此動作的方式是將 `bAllocate` 變數設為 `true`，這樣物件就會繼續加入到 <xref:System.Collections.Generic.List%601> 集合。  
  
 下列程式碼包含範例的 `Main` 方法。  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 下列程式碼包含 `WaitForFullGCProc` 使用者方法，此方法包含持續進行的 while 迴圈，檢查是否有記憶體回收通知。  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 下列程式碼包含 `OnFullGCApproachNotify` 方法，此方法是從  
  
 `WaitForFullGCProc` 方法呼叫的。  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 下列程式碼包含 `OnFullGCApproachComplete` 方法，此方法是從  
  
 `WaitForFullGCProc` 方法呼叫的。  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 下列程式碼包含從 `OnFullGCApproachNotify` 和 `OnFullGCCompleteNotify` 方法呼叫的使用者方法。  這些使用者方法會重新導向要求、完成現有的要求，然後在完整記憶體回收執行之後繼續要求。  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 完整的程式碼範例如下：  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## 請參閱  
 [Garbage Collection](../../../docs/standard/garbage-collection/index.md)