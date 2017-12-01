---
title: "記憶體回收告知"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords: garbage collection, notifications
ms.assetid: e12d8e74-31e3-4035-a87d-f3e66f0a9b89
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 41a2ed9c5d239f1570955e87bb5b749e29830bc3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="garbage-collection-notifications"></a>記憶體回收告知
在某些情況下，通用語言執行平台 (CLR) 所執行的完整記憶體回收 (也就是層代 2 回收) 可能會降低效能。 這可以是特別處理大量要求，伺服器發生問題在此情況下，完整記憶體回收可能會導致要求逾時。若要避免在關鍵時間期間所發生的完整集合，可以通知您已接近完整記憶體回收，並採取行動，將工作負載重新導向至另一個伺服器執行個體。 您可以也自行引發回收，前提是目前的伺服器執行個體不需要處理要求。  
  
 <xref:System.GC.RegisterForFullGCNotification%2A>方法會註冊到執行階段偵測即將完整記憶體回收時，會引發通知。 有兩個部分，此通知： 何時即將進行完整記憶體回收時和完整記憶體回收完成。  
  
> [!WARNING]
>  只有進行封鎖的記憶體回收會引發通知。 當[ \<gcConcurrent >](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)組態項目已啟用，背景記憶體回收就不會引發通知。  
  
 若要判斷當已引發通知，請使用<xref:System.GC.WaitForFullGCApproach%2A>和<xref:System.GC.WaitForFullGCComplete%2A>方法。 一般而言，您可以使用這些方法進行`while`迴圈持續取得<xref:System.GCNotificationStatus>列舉型別，並顯示通知的狀態。 如果該值為<xref:System.GCNotificationStatus.Succeeded>，您可以執行下列：  
  
-   以回應通知，以取得<xref:System.GC.WaitForFullGCApproach%2A>方法，您可以將工作負載重新導向，並可能自行引發的集合。  
  
-   以回應通知，以取得<xref:System.GC.WaitForFullGCComplete%2A>方法，您可以讓目前的伺服器執行個體可用來一次處理要求。 您也可以收集資訊。 例如，您可以使用<xref:System.GC.CollectionCount%2A>方法來記錄的集合數目。  
  
 <xref:System.GC.WaitForFullGCApproach%2A>和<xref:System.GC.WaitForFullGCComplete%2A>方法用來搭配使用。 使用其中一個，而沒有其他可能產生未定的結果。  
  
## <a name="full-garbage-collection"></a>完整記憶體回收  
 當下列任何案例都成立時，執行階段會導致完整記憶體回收：  
  
-   已有記憶體不足，無法升級至層代 2，導致下一個層代 2 回收。  
  
-   已有記憶體不足，無法升級為大型物件堆積，導致下一個層代 2 回收。  
  
-   層代 1 的集合在擴大為第 2 代，因為其他因素的集合。  
  
 您在中指定的臨界值<xref:System.GC.RegisterForFullGCNotification%2A>方法套用到前兩個案例。 不過，在第一個案例中您會不一定會收到通知，原因有兩個您所指定的臨界值成比例的時間：  
  
-   執行階段不會檢查每個的小型物件配置 （基於效能考量）。  
  
-   只有層代 1 回收將記憶體升級為第 2 代。  
  
 第三種案例也都是計算時，您會收到通知的不確定性。 雖然不保證，但它未證明是有用的方式將要求重新導向在這段期間，或自行引發回收時就更能容納，來避免、 完整記憶體回收的效果。  
  
## <a name="notification-threshold-parameters"></a>通知閾值參數  
 <xref:System.GC.RegisterForFullGCNotification%2A>方法有兩個參數來指定層代 2 物件和大型物件堆積的臨界值。 當符合這些值時，應引發記憶體回收通知。 下表描述這些參數。  
  
|參數|說明|  
|---------------|-----------------|  
|`maxGenerationThreshold`|1 到 99 的數字，指定何時應該引發通知會根據層代 2 中升級的物件。|  
|`largeObjectHeapThreshold`|1 到 99 的數字，指定何時應該引發通知根據大型物件堆積中配置的物件。|  
  
 如果您指定的值太高，則高的機率，您會收到通知，但它可能太長的等待期間才執行階段引發的集合。 如果您自行引發集合，您可能會回收比如果執行階段會導致集合會回收的多個物件。  
  
 如果您指定的值太低，執行階段可能會導致集合之前，您有足夠的時間，會收到通知。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 在下列範例中，一組伺服器會處理傳入的 Web 要求。 若要模擬的處理要求的工作負載，位元組陣列加入至<xref:System.Collections.Generic.List%601>集合。 每個伺服器記憶體回收通知的註冊，並再啟動的執行緒上`WaitForFullGCProc`使用者的方法，以持續監視<xref:System.GCNotificationStatus>所傳回的列舉型別<xref:System.GC.WaitForFullGCApproach%2A>和<xref:System.GC.WaitForFullGCComplete%2A>方法。  
  
 <xref:System.GC.WaitForFullGCApproach%2A>和<xref:System.GC.WaitForFullGCComplete%2A>引發通知時，方法會呼叫其各自的事件處理使用者方法：  
  
-   `OnFullGCApproachNotify`  
  
     這個方法會呼叫`RedirectRequests`使用者方法，指示要求佇列伺服器，暫停傳送要求至的伺服器。 這藉由設定類別層級變數模擬`bAllocate`至`false`，如此會配置沒有任何物件。  
  
     下一步`FinishExistingRequests`呼叫使用者的方法來完成處理擱置的伺服器要求。 這藉由清除模擬<xref:System.Collections.Generic.List%601>集合。  
  
     最後，因為在工作負載很輕，被引發記憶體回收。  
  
-   `OnFullGCCompleteNotify`  
  
     這個方法會呼叫使用者方法`AcceptRequests`繼續接受要求，因為伺服器不會再受到完整記憶體回收。 此動作設定模擬時`bAllocate`變數設為`true`，讓物件可以繼續加入<xref:System.Collections.Generic.List%601>集合。  
  
 下列程式碼包含`Main`方法的範例。  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 下列程式碼包含`WaitForFullGCProc`包含連續的 while 迴圈，檢查記憶體回收通知的使用者方法。  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 下列程式碼包含`OnFullGCApproachNotify`從呼叫的方法  
  
 `WaitForFullGCProc` 方法。  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 下列程式碼包含`OnFullGCApproachComplete`從呼叫的方法  
  
 `WaitForFullGCProc` 方法。  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 下列程式碼包含了使用者方法的呼叫`OnFullGCApproachNotify`和`OnFullGCCompleteNotify`方法。 使用者方法會將要求重新導向、 完成現有的要求，並完整記憶體回收發生後再繼續要求。  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 整個程式碼範例如下所示：  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a>另請參閱  
 [記憶體回收](../../../docs/standard/garbage-collection/index.md)
