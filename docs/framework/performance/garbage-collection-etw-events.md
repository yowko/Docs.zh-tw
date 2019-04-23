---
title: 記憶體回收 ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7f9bf0e309ec8c77d4b1d6afbf111e7eeae629ac
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149730"
---
# <a name="garbage-collection-etw-events"></a>記憶體回收 ETW 事件
<a name="top"></a> 這些事件收集到記憶體回收的相關資訊。 它們協助診斷和偵錯，包括判斷執行多少次記憶體回收、在記憶體回收期間釋放了多少記憶體，以及其他事項。  
  
 這個類別包含下列事件：  
  
-   [GCStart_V1 事件](#gcstart_v1_event)  
  
-   [GCEnd_V1 事件](#gcend_v1_event)  
  
-   [GCHeapStats_V1 事件](#gcheapstats_v1_event)  
  
-   [GCCreateSegment_V1 事件](#gccreatesegment_v1_event)  
  
-   [GCCreateSegment_V1 事件](#gcfreesegment_v1_event)  
  
-   [GCRestartEEBegin_V1 事件](#gcrestarteebegin_v1_event)  
  
-   [GCRestartEEEnd_V1 事件](#gcrestarteeend_v1_event)  
  
-   [GCSuspendEE_V1 事件](#gcsuspendee_v1_event)  
  
-   [GCSuspendEEEnd_V1 事件](#gcsuspendeeend_v1_event)  
  
-   [GCAllocationTick_V2 事件](#gcallocationtick_v2_event)  
  
-   [GCFinalizersBegin_V1 事件](#gcfinalizersbegin_v1_event)  
  
-   [GCFinalizersEnd_V1 事件](#gcfinalizersend_v1_event)  
  
-   [GCCreateConcurrentThread_V1 事件](#gccreateconcurrentthread_v1_event)  
  
-   [GCTerminateConcurrentThread_V1 事件](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a>GCStart_V1 事件  
 下表說明關鍵字和層級。 (如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|告知性 (4)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|1|已開始進行記憶體回收。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|計數|win:UInt32|第 *n*個記憶體回收。|  
|深度|win:UInt32|所收集的產生。|  
|原因|win:UInt32|觸發記憶體回收的原因：<br /><br /> 0x0 - 小型物件堆積配置。<br /><br /> 0x1 - 已引起。<br /><br /> 0x2 - 記憶體不足。<br /><br /> 0x3 - 空白。<br /><br /> 0x4 - 大型物件堆積配置。<br /><br /> 0x5 - 空間不足 (針對小型物件堆積)。<br /><br /> 0x6 - 空間不足 (針對大型物件堆積)。<br /><br /> 0x7 - 已引起，但不強制為封鎖。|  
|類型|win:UInt32|0x0 - 封鎖發生在背景記憶體回收之外的記憶體回收。<br /><br /> 0x1 - 背景記憶體回收。<br /><br /> 0x2 - 封鎖發生在背景記憶體回收期間的記憶體回收。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
 [回到頁首](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a>GCEnd_V1 事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|告知性 (4)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|2|記憶體回收已經結束。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|計數|win:UInt32|第 *n*個記憶體回收。|  
|深度|win:UInt32|所收集的產生。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
 [回到頁首](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a>GCHeapStats_V1 事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|告知性 (4)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|描述|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|4|每次記憶體回收結束時顯示堆積統計資料。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|GenerationSize0|win:UInt64|以位元組為單位顯示的層代 0 記憶體大小。|  
|TotalPromotedSize0|win:UInt64|從層代 0 升級至層代 1 的位元組數目。|  
|GenerationSize1|win:UInt64|以位元組為單位顯示的層代 1 記憶體大小。|  
|TotalPromotedSize1|win:UInt64|從層代 1 升級到層代 2 的位元組數目。|  
|GenerationSize2|win:UInt64|以位元組為單位顯示的層代 2 記憶體大小。|  
|TotalPromotedSize2|win:UInt64|在回收之後存留於層代 2 中的位元組數目。|  
|GenerationSize3|win:UInt64|以位元組為單位顯示的目前大型物件堆積的大小。|  
|TotalPromotedSize3|win:UInt64|在回收之後存留於大型物件堆積中的位元組數目。|  
|FinalizationPromotedSize|win:UInt64|以位元組為單位顯示的準備最終處理的物件總大小。|  
|FinalizationPromotedCount|win:UInt64|準備好進行最終處理的物件數目。|  
|PinnedObjectCount|win:UInt32|固定 (不可移動) 的物件數目。|  
|SinkBlockCount|win:UInt32|目前使用中的同步區塊數目。|  
|GCHandleCount|win:UInt32|目前使用中的記憶體回收控制代碼數目。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
 [回到頁首](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a>GCCreateSegment_V1 事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|告知性 (4)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|5|已建立新的記憶體回收集合區段。 此外，當已經啟用追蹤正在執行的處理序時，每個已存在的區段都會引發本事件。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|地址|win:UInt64|區段的位址。|  
|大小|win:UInt64|區段的大小。|  
|類型|win:UInt32|0x0 - 小型物件堆積。<br /><br /> 0x1 - 大型物件堆積。<br /><br /> 0x2 - 唯讀堆積。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
 請注意記憶體回收行程所配置的區段大小是依實作而定，有可能在任何時間，包括在定期更新時做變更。 您的應用程式永遠都不應該對相關或根據特定區段的大小做出假設，也不應嘗試設定區段配置的可用記憶體數量。  
  
 [回到頁首](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a>GCCreateSegment_V1 事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|告知性 (4)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|6|已釋放記憶體回收區段。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|地址|win:UInt64|區段的位址。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
 [回到頁首](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a>GCRestartEEBegin_V1 事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|告知性 (4)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|7|已開始從通用語言執行階段的擱置中恢復。|  
  
 沒有事件資料。  
  
 [回到頁首](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a>GCRestartEEEnd_V1 事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|告知性 (4)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|3|從通用語言執行階段擱置恢復已結束。|  
  
 沒有事件資料。  
  
 [回到頁首](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a>GCSuspendEE_V1 事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|告知性 (4)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|9|記憶體回收執行引擎擱置的起點。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|原因|win:UInt16|0x0 - 其他。<br /><br /> 0x1 - 記憶體回收。<br /><br /> 0x2 - 應用程式定義域關閉。<br /><br /> 0x3 - 推銷程式碼。<br /><br /> 0x4 - 關機。<br /><br /> 0x5 - 偵錯工具。<br /><br /> 0x6 - 準備進行記憶體回收。|  
|計數|win:UInt32|該時間的 GC 計數。 通常，您會在這之後看到後續「GC 啟動」事件，而且其計數會是這個計數 + 1，因為我們增加記憶體回收期間的 GC 索引。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
 [回到頁首](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a>GCSuspendEEEnd_V1 事件  
 下表說明關鍵字和層級：  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|告知性 (4)|  
  
 下表說明事件資訊：  
  
|Event - 事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|8|記憶體回收執行引擎擱置的終點。|  
  
 沒有事件資料。  
  
 [回到頁首](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a>GCAllocationTick_V2 事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|告知性 (4)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|10|每次配置大約 100 KB。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|AllocationAmount|win:UInt32|配置大小 (位元組)。 正確的配置長度值小於 ULONG (4,294,967,295 位元組)。 如果配置較大，則此欄位會包含已截斷的值。 使用 `AllocationAmount64` 以進行非常大的配置。|  
|AllocationKind|win:UInt32|0x0 - 小型物件配置 (配置於小型物件堆積中)。<br /><br /> 0x1 - 大型物件配置 (配置於大型物件堆積中)。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
|AllocationAmount64|win:UInt64|配置大小 (位元組)。 對於非常大的配置來說這個值是正確的。|  
|TypeId|win:Pointer|MethodTable 的位址。 當有多個在此事件期間所配置的物件類型時，這是對應至上次的物件配置 (該物件造成超過 100 KB 的臨界值) 的 MethodTable 位址。|  
|TypeName|win:UnicodeString|已配置的類型名稱。 當有多個在此事件期間所配置的物件類型時，這是對應至上次的物件配置 (該物件造成超過 100 KB 的臨界值) 的類型。|  
|HeapIndex|win:UInt32|物件所配置的堆積位置。 當與工作站記憶體回收一起執行時，這個值是 0 (零)。|  
  
 [回到頁首](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a>GCFinalizersBegin_V1 事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|告知性 (4)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|14|開始執行完成項。|  
  
 沒有事件資料。  
  
 [回到頁首](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a>GCFinalizersEnd_V1 事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|告知性 (4)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|13|結束執行完成項。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|計數|win:UInt32|所執行的完成項數目。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
 [回到頁首](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a>GCCreateConcurrentThread_V1 事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|告知性 (4)|  
|`ThreadingKeyword` (0x10000)|告知性 (4)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|11|並行記憶體回收執行緒已建立。|  
  
 沒有事件資料。  
  
 [回到頁首](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a>GCTerminateConcurrentThread_V1 事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|告知性 (4)|  
|`ThreadingKeyword` (0x10000)|告知性 (4)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|12|並行記憶體回收執行緒已終止。|  
  
 沒有事件資料。  
  
## <a name="see-also"></a>另請參閱

- [CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)
