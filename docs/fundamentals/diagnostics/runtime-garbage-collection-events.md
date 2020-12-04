---
title: 垃圾收集運行時間事件
description: 請參閱收集 .NET 垃圾收集行程特定診斷資訊的 .NET 運行時間事件。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- GC events
- garbage collection events (CoreCLR)
- ETW, EventPipe, LTTng garbage collection events (CoreCLR)
ms.openlocfilehash: 2799a93f351baf23ec7a359b0b4b2be5c216dc4d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "96586639"
---
# <a name="net-runtime-garbage-collection-events"></a>.NET 執行時間垃圾收集事件

這些事件收集到記憶體回收的相關資訊。 它們有助於診斷和偵測，包括決定執行垃圾收集的次數、在垃圾收集期間釋放多少記憶體等等。如需如何基於診斷目的使用這些事件的詳細資訊，請參閱[記錄和追蹤 .net 應用程式](../../core/diagnostics/logging-tracing.md)。

## <a name="gcstart_v2-event"></a>GCStart_V2 事件

下表說明關鍵字和層級：

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|告知性 (4)|

下表說明事件資訊：

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`GCStart_V1`|1|已開始進行記憶體回收。|

下表說明事件資料：

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|第 *n* 個記憶體回收。|
|`Depth`|`win:UInt32`|所收集的產生。|
|`Reason`|`win:UInt32`|觸發記憶體回收的原因：<br /><br /> `0x0` -小型物件堆積配置。<br /><br /> `0x1` 引入.<br /><br /> `0x2` -記憶體不足。<br /><br /> `0x3` 空字元.<br /><br /> `0x4` -大型物件堆積配置。<br /><br /> `0x5` -用於小型物件堆積) 的空間 (。<br /><br /> `0x6` -) 大型物件堆積的空間 (。<br /><br /> `0x7` -已引發但未強制為封鎖。|
|`Type`|`win:UInt32`|`0x0` -在背景垃圾收集之外發生封鎖垃圾收集。<br /><br /> `0x1` -背景垃圾收集。<br /><br /> `0x2` -在背景垃圾收集期間發生封鎖垃圾收集。|
|`ClrInstanceID`|win:UInt16|CoreCLR 實例的唯一識別碼。|

## <a name="gcend_v1-event"></a>GCEnd_V1 事件

下表說明關鍵字和層級：

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|告知性 (4)|

下表說明事件資訊：

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`GCEnd_V1`|2|記憶體回收已經結束。|

下表說明事件資料：

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|第 *n* 個記憶體回收。|
|`Depth`|`win:UInt32`|所收集的產生。|
|`ClrInstanceID`|win:UInt16|CoreCLR 實例的唯一識別碼。|

## <a name="gcheapstats_v2-event"></a>GCHeapStats_V2 事件

下表說明關鍵字和層級：

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|告知性 (4)|

下表說明事件資訊：

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`GCHeapStats_V2`|4|每次記憶體回收結束時顯示堆積統計資料。|

下表說明事件資料：

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`GenerationSize0`|`win:UInt64`|以位元組為單位顯示的層代 0 記憶體大小。|
|`TotalPromotedSize0`|`win:UInt64`|從層代 0 升級至層代 1 的位元組數目。|
|`GenerationSize1`|`win:UInt64`|以位元組為單位顯示的層代 1 記憶體大小。|
|`TotalPromotedSize1`|`win:UInt64`|從層代 1 升級到層代 2 的位元組數目。|
|`GenerationSize2`|`win:UInt64`|以位元組為單位顯示的層代 2 記憶體大小。|
|`TotalPromotedSize2`|`win:UInt64`|在回收之後存留於層代 2 中的位元組數目。|
|`GenerationSize3`|`win:UInt64`|以位元組為單位顯示的目前大型物件堆積的大小。|
|`TotalPromotedSize3`|`win:UInt64`|在回收之後存留於大型物件堆積中的位元組數目。|
|`FinalizationPromotedSize`|`win:UInt64`|以位元組為單位顯示的準備最終處理的物件總大小。|
|`FinalizationPromotedCount`|`win:UInt64`|準備好進行最終處理的物件數目。|
|`PinnedObjectCount`|`win:UInt32`|固定 (不可移動) 的物件數目。|
|`SinkBlockCount`|`win:UInt32`|目前使用中的同步區塊數目。|
|`GCHandleCount`|`win:UInt32`|目前使用中的記憶體回收控制代碼數目。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|
|`GenerationSize4`|`win:UInt64`|釘選的物件堆積大小（以位元組為單位）。|
|`TotalPromotedSize4`|`win:UInt64`|在最後一個集合之後，在釘選的物件堆積中存活的位元組數目。|

## <a name="gccreatesegment_v1-event"></a>GCCreateSegment_V1 事件

下表說明關鍵字和層級：

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|告知性 (4)|

下表說明事件資訊：

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|5|已建立新的記憶體回收集合區段。 此外，當已經啟用追蹤正在執行的處理序時，每個已存在的區段都會引發本事件。|

下表說明事件資料：

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`Address`|`win:UInt64`|區段的位址。|
|`Size`|`win:UInt64`|區段的大小。|
|`Type`|`win:UInt32`|0x0 - 小型物件堆積。<br /><br /> 0x1 - 大型物件堆積。<br /><br /> 0x2 - 唯讀堆積。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

請注意記憶體回收行程所配置的區段大小是依實作而定，有可能在任何時間，包括在定期更新時做變更。 您的應用程式永遠都不應該對相關或根據特定區段的大小做出假設，也不應嘗試設定區段配置的可用記憶體數量。

## <a name="gcfreesegment_v1-event"></a>GCFreeSegment_V1 事件

下表說明關鍵字和層級：

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|告知性 (4)|

下表說明事件資訊：

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|6|已釋放記憶體回收區段。|

下表說明事件資料：

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`Address`|`win:UInt64`|區段的位址。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="gcrestarteebegin_v1-event"></a>GCRestartEEBegin_V1 事件

下表說明關鍵字和層級：

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|告知性 (4)|

下表說明事件資訊：

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|7|已開始從通用語言執行階段的擱置中恢復。|

此事件沒有任何事件資料。

## <a name="gcrestarteeend_v1-event"></a>GCRestartEEEnd_V1 事件

下表說明關鍵字和層級：

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|告知性 (4)|

下表說明事件資訊：

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|3|從通用語言執行階段擱置恢復已結束。|

此事件沒有任何事件資料。

## <a name="gcsuspendeeend_v1-event"></a>GCSuspendEEEnd_V1 事件

下表說明關鍵字和層級：

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|告知性 (4)|

下表說明事件資訊：

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|8|記憶體回收執行引擎擱置的終點。|

此事件沒有任何事件資料。

## <a name="gcsuspendeebegin_v1-event"></a>GCSuspendEEBegin_V1 事件

下表說明關鍵字和層級：

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|告知性 (4)|

下表說明事件資訊：

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`GCSuspendEEBegin_V1`|8|記憶體回收執行引擎擱置的起點。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|第 *n* 個記憶體回收。|
|`Reason`|`win:UInt32`|EE 暫停的原因。<br/><br/>`0x0`：暫停其他<br/><br/>`0x1`：暫止 GC。<br/><br/>`0x2`：暫止 AppDomain 關閉。<br/><br/>`0x3`：暫停程式碼推銷。<br/><br/>`0x4`：暫停關機。<br/><br/>`0x5`：暫停偵錯工具。<br/><br/>`0x6`：暫停 GC 準備。<br/><br/>`0x7`：暫止偵錯工具清理|

## <a name="gcallocationtick_v3-event"></a>GCAllocationTick_V3 事件

下表說明關鍵字和層級：

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|詳細資訊 (4) |

下表說明事件資訊：

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`GCAllocationTick_V3`|10|每次配置大約 100 KB。|

下表說明事件資料：

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`AllocationAmount`|`win:UInt32`|配置大小 (位元組)。 正確的配置長度值小於 ULONG (4,294,967,295 位元組)。 如果配置較大，則此欄位會包含已截斷的值。 使用 `AllocationAmount64` 以進行非常大的配置。|
|`AllocationKind`|`win:UInt32`|`0x0` -小型物件配置 (配置是在小型物件堆積) 中。<br /><br /> `0x1` -大型物件配置 (配置位於大型物件堆積) 。|
|`AllocationAmount64`|`win:UInt64`|配置大小 (位元組)。 對於非常大的配置來說這個值是正確的。|
|`TypeId`|`win:Pointer`|MethodTable 的位址。 當有多個在此事件期間所配置的物件類型時，這是對應至上次的物件配置 (該物件造成超過 100 KB 的臨界值) 的 MethodTable 位址。|
|`TypeName`|`win:UnicodeString`|已配置的類型名稱。 當有多個在此事件期間所配置的物件類型時，這是對應至上次的物件配置 (該物件造成超過 100 KB 的臨界值) 的類型。|
|`HeapIndex`|`win:UInt32`|物件所配置的堆積位置。 當與工作站記憶體回收一起執行時，這個值是 0 (零)。|
|`Address`|`win:Pointer`|最後設定物件的位址。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="gccreateconcurrentthread_v1-event"></a>GCCreateConcurrentThread_V1 事件

下表說明關鍵字和層級：

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|告知性 (4)|
|`ThreadingKeyword` (0x10000)|告知性 (4)|

下表說明事件資訊：

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|11|並行記憶體回收執行緒已建立。|

此事件沒有任何事件資料。

## <a name="gcterminateconcurrentthread_v1-event"></a>GCTerminateConcurrentThread_V1 事件

下表說明關鍵字和層級：

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|告知性 (4)|
|`ThreadingKeyword` (0x10000)|告知性 (4)|

下表說明事件資訊：

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|12|並行記憶體回收執行緒已終止。|

此事件沒有任何事件資料。

## <a name="gcfinalizersbegin_v1-event"></a>GCFinalizersBegin_V1 事件

下表說明關鍵字和層級：

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|告知性 (4)|

下表說明事件資訊：

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|14|開始執行完成項。|

此事件沒有任何事件資料。

## <a name="gcfinalizersend_v1-event"></a>GCFinalizersEnd_V1 事件

下表說明關鍵字和層級：

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|告知性 (4)|

下表說明事件資訊：

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|13|結束執行完成項。|

下表說明事件資料：

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|所執行的完成項數目。|
|`ClrInstanceID`|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|

## <a name="setgchandle-event"></a>SetGCHandle 事件

下表說明關鍵字和層級：

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`GCHandleKeyword` (0x2) |告知性 (4)|

下表說明事件資訊：

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`SetGCHandle`|30|已設定 GC 控制碼。|

下表說明事件資料：

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|配置的控制碼位址。|
|`ObjectID`|`win:Pointer`|建立控制碼之物件的位址。|
|`Kind`|`win:UInt32`|已設定的 GC 控制碼類型。 <br /><br />`0x0`: WeakShort <br/><br/>`0x1`: WeakLong <br /><br />`0x2`：強式 <br /><br />`0x3`：已釘選 <br /><br />`0x4`：變數<br /><br />`0x5`: RefCounted <br /><br />`0x6`：相依<br /><br />`0x7`: AsyncPinned<br /><br />`0x8`： SizedRef|
|`Generation`|`win:UInt32`|建立控制碼的物件產生。|
|`AppDomainID`|`win:UInt64`|AppDomain 識別碼。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="destroygchandle-event"></a>DestroyGCHandle 事件

下表說明關鍵字和層級：

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`GCHandleKeyword` (0x2) |告知性 (4)|

下表說明事件資訊：

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`DestroyGCHandle`|31|GC 控制碼已損毀。|

下表說明事件資料：

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|終結的控制碼位址。|
|`ClrInstanceID`|win:UInt16|CoreCLR 實例的唯一識別碼。|

## <a name="pinobjectatgctime-event"></a>PinObjectAtGCTime 事件

下表說明關鍵字和層級：

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|詳細資訊 (5)|

下表說明事件資訊：

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`PinObjectAtGCTime`|33|在 GC 期間釘選物件。|

下表說明事件資料：

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|控制碼的位址。|
|`ObjectID`|`win:Pointer`|釘選物件的位址。|
|`ObjectSize`|`win:UInt64`|釘選物件的大小。|
|`TypeName`|`win:UnicodeString`|釘選物件的型別名稱。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="gctriggered-event"></a>GCTriggered 事件

下表說明關鍵字和層級：

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|詳細資訊 (5)|

下表說明事件資訊：

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`GCTriggered`|33|已觸發 GC。|

下表說明事件資料：

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`Reason`|`win:UInt32`|觸發 GC 的原因。<br/><br/>`0x0`: AllocSmall<br/><br/>`0x1`：已引發 <br/><br/>`0x2`: LowMemory <br/><br/>`0x3`：空白 <br/><br/>`0x4`: AllocLarge <br/><br/>`0x5`: OutOfSpaceSmallObjectHeap <br/><br/>`0x6`: OutOfSpaceLargeObjectHeap <br/><br/>`0x7`:InducedNoForce <br/><br/>`0x8`：壓力 <br/><br/>`0x9`: InducedLowMemory|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="increasememorypressure-event"></a>IncreaseMemoryPressure 事件

下表說明關鍵字和層級：

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|資訊 (4) |

下表說明事件資訊：

|事件|事件識別碼|引發的時機|
|----------------|---------------|-----------------|
|`IncreaseMemoryPressure`|200|記憶體壓力已增加。|

下表說明事件資料：

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`ClrInstanceID`|win:UInt16|CoreCLR 實例的唯一識別碼。|

## <a name="decreasememorypressure-event"></a>DecreaseMemoryPressure 事件

下表說明關鍵字和層級：

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|資訊 (4) |

下表說明事件資訊：

|事件|事件識別碼|引發的時機|
|----------------|---------------|-----------------|
|`DecreaseMemoryPressure`|201|記憶體壓力已減少。|

下表說明事件資料：

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`BytesFreed`|`win:UInt32`|釋放的位元組。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="gcmarkwithtype-event"></a>GCMarkWithType 事件

下表說明關鍵字和層級：

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|資訊 (4) |

下表說明事件資訊：

|事件|事件識別碼|引發的時機|
|----------------|---------------|-----------------|
|`GCMarkWithType`|202|Gc 標記階段中已標示 GC 根。|

下表說明事件資料：

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`HeapNum`|`win:UInt32`|堆積數目。|
|`ClrInstanceID`|win:UInt16|CoreCLR 實例的唯一識別碼。|
|`Type`|`win:UInt32`|GC 根型別。<br/><br/>`0x0`： Stack<br/><br/>`0x1`： Finalizer<br/><br/>`0x2`：控制碼<br/><br/>`0x3`：舊版<br/><br/>`0x4`： SizedRef<br/><br/>`0x5`：溢位<br/><br/>|
|`Bytes`|`win:UInt64`|標示的位元組數目。|

## <a name="gcjoin_v2-event"></a>GCJoin_V2 事件

下表說明關鍵字和層級：

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|詳細資訊 (5)|

下表說明事件資訊：

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`GCJoin_V2`|203|已加入 GC 執行緒。|

下表說明事件資料：

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`Heap`|`win:UInt32`|堆積數目|
|`JoinTime`|`win:UInt32`|指出此事件是否會在聯結開始的聯結 (開頭或結束時引發 `0x0` ， `0x1` 以進行聯結結束) |
|`JoinType`|`win:UInt32`|聯結類型。 <br/><br/>`0x0`：上次聯結<br/><br/>`0x1`：聯結 <br/><br/>`0x2`：重新開機 <br/><br/>`0x3`：第一個反向聯結<br/><br/>`0x4`：反向聯結<br/><br/>|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|
