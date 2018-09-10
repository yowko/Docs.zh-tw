---
title: 記憶體回收告知
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- garbage collection, notifications
ms.assetid: e12d8e74-31e3-4035-a87d-f3e66f0a9b89
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10f947fc44e69368e30614e0b41eaf7c73fb6563
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084945"
---
# <a name="garbage-collection-notifications"></a>記憶體回收告知
在某些情況下，通用語言執行平台 (CLR) 所執行的完整記憶體回收 (也就是層代 2 回收) 可能會降低效能。 這是一個問題，特別會發生在處理大量要求的伺服器上；在此情況下，完整記憶體回收可能會導致要求逾時。若要避免在關鍵期間發生完整回收，您可以在接近完整記憶體回收時收到通知，然後採取行動將工作負載重新導向至另一個伺服器執行個體。 您也可以自行引發回收，前提是目前的伺服器執行個體不需要處理要求。  
  
 <xref:System.GC.RegisterForFullGCNotification%2A> 方法會註冊一個當執行階段偵測到接近完整記憶體回收時要引發的通知。 通知有兩個部分：當接近完整記憶體回收時，以及當完整記憶體回收完成時。  
  
> [!WARNING]
>  只有進行封鎖的記憶體回收會引發通知。 如果已啟用 [\<gcConcurrent>](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) 設定元素，背景記憶體回收將不會引發通知。  
  
 若要判斷引發通知的時機，請使用 <xref:System.GC.WaitForFullGCApproach%2A> 和 <xref:System.GC.WaitForFullGCComplete%2A> 方法。 一般來說，您會在 `while` 迴圈中使用這些方法，以持續取得可顯示通知狀態的 <xref:System.GCNotificationStatus> 列舉。 如果值為 <xref:System.GCNotificationStatus.Succeeded>，您可以執行以下動作：  
  
-   為了回應使用 <xref:System.GC.WaitForFullGCApproach%2A> 方法取得的通知，您可以重新導向工作負載，並有可能自行引發回收。  
  
-   為了回應使用 <xref:System.GC.WaitForFullGCComplete%2A> 方法取得的通知，您可以讓目前的伺服器執行個體可用以重新處理要求。 您也可以收集資訊。 例如，您可以使用 <xref:System.GC.CollectionCount%2A> 方法來記錄回收的數目。  
  
 <xref:System.GC.WaitForFullGCApproach%2A> 和 <xref:System.GC.WaitForFullGCComplete%2A> 方法是設計來搭配使用。 僅使用其中一個可能會產生不定的結果。  
  
## <a name="full-garbage-collection"></a>完整記憶體回收  
 當下列任何案例都成立時，執行階段會導致完整記憶體回收：  
  
-   足夠的記憶體已升階至層代 2，導致下一個層代 2 回收。  
  
-   足夠的記憶體已升階至大型物件堆積，導致下一個層代 2 回收。  
  
-   因為其他因素，層代 1 回收已擴大為層代 2 回收。  
  
 您在 <xref:System.GC.RegisterForFullGCNotification%2A> 方法中指定的閾值會套用到前兩個案例。 不過，在第一個案例中，您不一定會在指定的閾值成比例的時間收到通知，原因有兩個：  
  
-   執行階段不會檢查每個小型物件配置 (基於效能考量)。  
  
-   只有層代 1 回收會將記憶體升階為層代 2。  
  
 第三個案例也會造成您收到通知之時間的不確定性。 雖然這不是一種保證，但是透過在這段期間將要求重新導向或在更能容納的時候自行引發，確實已證明這是一種減輕不適當的完整記憶體回收之效果的有用方法。  
  
## <a name="notification-threshold-parameters"></a>通知閾值參數  
 <xref:System.GC.RegisterForFullGCNotification%2A> 方法有兩個參數來指定層代 2 物件和大型物件堆積的閾值。 當符合那些值時，應該會引發記憶體回收通知。 下列表格描述這些參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`maxGenerationThreshold`|範圍從 1 到 99 的數字，指定何時應根據層代 2 中所升階的物件來引發通知。|  
|`largeObjectHeapThreshold`|範圍從 1 到 99 的數字，指定何時應根據大型物件堆積中所配置的物件來引發通知。|  
  
 如果您指定的值太高，則有很高的機率會收到通知，但是在執行階段引發回收之前，可能會有一段很長的等待期間。 如果您自行引發回收，則可能會回收比原本回收 (如果執行階段導致回收的話) 還要多的物件。  
  
 如果您指定的值太低，執行階段可能會在您有足夠的時間收到通知之前導致回收。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 在下列範例中，一組伺服器會處理傳入的 Web 要求。 若要模擬處理要求的工作負載，請將位元組陣列加入至 <xref:System.Collections.Generic.List%601> 集合。 每部伺服器都會註冊記憶體回收通知，然後在 `WaitForFullGCProc` 使用者方法上啟動執行緒以持續監視 <xref:System.GC.WaitForFullGCApproach%2A> 和 <xref:System.GC.WaitForFullGCComplete%2A> 方法所傳回的 <xref:System.GCNotificationStatus> 列舉。  
  
 當引發通知時，<xref:System.GC.WaitForFullGCApproach%2A> 和 <xref:System.GC.WaitForFullGCComplete%2A> 方法會呼叫各自的事件處理使用者方法：  
  
-   `OnFullGCApproachNotify`  
  
     這個方法會呼叫 `RedirectRequests` 使用者方法，此使用者方法會指示要求佇列伺服器暫停將要求傳送至伺服器。 這會透過將類別層級變數 `bAllocate` 設定為 `false` 來進行模擬，如此便不會再配置任何物件。  
  
     接下來，會呼叫 `FinishExistingRequests` 使用者方法來完成處理擱置中伺服器要求。 這會透過清除 <xref:System.Collections.Generic.List%601> 集合來進行模擬。  
  
     最後，因為工作負載減輕，所以會引發記憶體回收。  
  
-   `OnFullGCCompleteNotify`  
  
     此方法會呼叫使用者方法 `AcceptRequests` 以繼續接受要求，因為伺服器不再容許完整記憶體回收。 此動作是透過將 `bAllocate` 變數設定為 `true` 來進行模擬，讓物件能夠繼續加入到 <xref:System.Collections.Generic.List%601> 集合。  
  
 下列程式碼包含範例的 `Main` 方法。  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 下列程式碼包含 `WaitForFullGCProc` 使用者方法，其中包含用來檢查記憶體回收通知的連續 while 迴圈。  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 下列程式碼包含從下列方法呼叫的 `OnFullGCApproachNotify` 方法：  
  
 `WaitForFullGCProc` 方法。  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 下列程式碼包含從下列方法呼叫的 `OnFullGCApproachComplete` 方法：  
  
 `WaitForFullGCProc` 方法。  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 下列程式碼包含從 `OnFullGCApproachNotify` 和 `OnFullGCCompleteNotify` 方法呼叫的使用者方法。 使用者方法會將要求重新導向，然後在完整記憶體回收之後繼續要求。  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 完整的程式碼範例如下所示：  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [記憶體回收](../../../docs/standard/garbage-collection/index.md)
