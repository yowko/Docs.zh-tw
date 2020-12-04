---
title: ThreadPool 運行時間事件
description: 請參閱 .net 運行時間表程集區事件，以收集 .NET Core 中線程集區的相關診斷資訊。 執行緒集區事件是背景工作執行緒集區事件或 i/o 執行緒集區事件。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- ThreadPool events (CoreCLR)
- ETW, thread pool events (CoreCLR)
ms.openlocfilehash: cdd6041c5842d4922c60e33daf6db366f7d35327
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96586661"
---
# <a name="net-runtime-thread-pool-events"></a>.NET 運行時間表程集區事件

這些事件會收集 threadpool 中工作者和 i/o 執行緒的相關資訊。 如需如何基於診斷目的使用這些事件的詳細資訊，請參閱[記錄和追蹤 .net 應用程式](../../core/diagnostics/logging-tracing.md)。

## <a name="iothreadcreate_v1-event"></a>IOThreadCreate_V1 事件

 下表說明關鍵字和層級。

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|告知性 (4)|

 下表說明事件資訊。

|事件|事件識別碼|引發的時機|
|-----------------------------------|-----------|
|`IOThreadCreate_V1`|44|在執行緒集區中建立 I/O 執行緒時。|

 下表說明事件資料。

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|I/O 執行緒的數目，其包含新建立的執行緒。|
|`NumRetired`|`win:UInt64`|已淘汰之背景工作執行緒的數目。|
|`ClrInstanceID`|`win:UInt16`|CLR 或 CoreCLR 執行個體的唯一 ID。|

## <a name="iothreadterminate_v1-event"></a>IOThreadTerminate_V1 事件

 下表說明關鍵字和層級

|引發事件的關鍵字|層級
|-----------------------------------|-----------
|`ThreadingKeyword` (0x10000)|告知性 (4)

 下表說明事件資訊。

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`IOThreadTerminate`|45|執行緒集區中的 i/o 執行緒終止。|

 下表說明事件資料。

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|執行緒集區中剩餘的 I/O 執行緒數目。|
|`NumRetired`|`win:UInt64`|已淘汰的 I/O 執行緒數目。|
|`ClrInstanceID`|`win:UInt16`|CLR 或 CoreCLR 執行個體的唯一 ID。|

## <a name="iothreadretire_v1-event"></a>IOThreadRetire_V1 事件

 下表說明關鍵字和層級。

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|告知性 (4)|

 下表說明事件資訊。

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`IOThreadRetire_V1`|46|當 I/O 執行緒變成淘汰候選時。|

 下表說明事件資料。

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|執行緒集區中剩餘的 I/O 執行緒數目。|
|`NumRetired`|`win:UInt64`|已淘汰的 I/O 執行緒數目。|
|`ClrInstanceID`|`win:UInt16`|CLR 或 CoreCLR 執行個體的唯一 ID。|

## <a name="iothreadunretire_v1-event"></a>IOThreadUnretire_V1 事件

 下表說明關鍵字和層級。

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|告知性 (4)|

 下表說明事件資訊。

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`IOThreadUnretire_V1`|47|因為在執行緒變成淘汰候選之後，I/O 在等候期間內到達，而導致 I/O 執行緒取消淘汰時。|

 下表說明事件資料。

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|執行緒集區中的 I/O 執行緒數目，包含此執行緒。|
|`NumRetired`|`win:UInt64`|已淘汰的 I/O 執行緒數目。|
|`ClrInstanceID`|`Win:UInt16`|CLR 或 CoreCLR 執行個體的唯一 ID。|

## <a name="threadpoolworkerthreadstart-event"></a>ThreadPoolWorkerThreadStart 事件

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|-----------|
|`ThreadingKeyword` (0x10000)|告知性 (4)|

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadStart`|50|建立背景工作執行緒時。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|可用以處理工作的背景工作執行緒數目，其包含正在處理工作的執行緒。|
|`RetiredWorkerThreadCount`|`win:UInt32`|無法用以處理工作的背景工作執行緒數目，但其正處於保留狀態以免之後需要更多執行緒。|
|`ClrInstanceID`|`win:UInt16`|CLR 或 CoreCLR 執行個體的唯一 ID。|

## <a name="threadpoolworkerthreadstop-event"></a>ThreadPoolWorkerThreadStop 事件

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|-----------|
|`ThreadingKeyword` (0x10000)|告知性 (4)|

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadStop`|51|停止背景工作執行緒時。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|可用以處理工作的背景工作執行緒數目，其包含正在處理工作的執行緒。|
|`RetiredWorkerThreadCount`|`win:UInt32`|無法用以處理工作的背景工作執行緒數目，但其正處於保留狀態以免之後需要更多執行緒。|
|`ClrInstanceID`|`win:UInt16`|CLR 或 CoreCLR 執行個體的唯一 ID。|

## <a name="threadpoolworkerthreadwait-event"></a>ThreadPoolWorkerThreadWait 事件

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|-----------|
|`ThreadingKeyword` (0x10000)|告知性 (4)|

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadWait`|57|工作者執行緒開始等候工作。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|可用以處理工作的背景工作執行緒數目，其包含正在處理工作的執行緒。|
|`RetiredWorkerThreadCount`|`win:UInt32`|無法用以處理工作的背景工作執行緒數目，但其正處於保留狀態以免之後需要更多執行緒。|
|`ClrInstanceID`|`win:UInt16`|CLR 或 CoreCLR 執行個體的唯一 ID。|

## <a name="threadpoolworkerthreadretirementstart-event"></a>ThreadPoolWorkerThreadRetirementStart 事件

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|-----------|
|`ThreadingKeyword` (0x10000)|告知性 (4)|

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadRetirementStart`|52|淘汰背景工作執行緒時。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|可用以處理工作的背景工作執行緒數目，其包含正在處理工作的執行緒。|
|`RetiredWorkerThreadCount`|`win:UInt32`|無法用以處理工作的背景工作執行緒數目，但其正處於保留狀態以免之後需要更多執行緒。|
|`ClrInstanceID`|`win:UInt16`|CLR 或 CoreCLR 執行個體的唯一 ID。|

## <a name="threadpoolworkerthreadretirementstop-event"></a>ThreadPoolWorkerThreadRetirementStop 事件

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|-----------|
|`ThreadingKeyword` (0x10000)|告知性 (4)|

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadRetirementStop`|53|淘汰的背景工作執行緒再次作用時。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|可用以處理工作的背景工作執行緒數目，其包含正在處理工作的執行緒。|
|`RetiredWorkerThreadCount`|`win:UInt32`|無法用以處理工作的背景工作執行緒數目，但其正處於保留狀態以免之後需要更多執行緒。|
|`ClrInstanceID`|`win:UInt16`|CLR 或 CoreCLR 執行個體的唯一 ID。|

## <a name="threadpoolworkerthreadadjustmentsample-event"></a>ThreadPoolWorkerThreadAdjustmentSample 事件

 下表說明關鍵字和層級。

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|告知性 (4)|

 下表說明事件資訊。

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentSample`|54|表示單一範例的資訊集合。亦即，具有特定並行層級之輸送量的瞬間量。|

 下表說明事件資料。

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`Throughput`|`win:Double`|每個時間單位完成的數目。|
|`ClrInstanceID`|`win:UInt16`|CLR 或 CoreCLR 執行個體的唯一 ID。|

## <a name="threadpoolworkerthreadadjustmentadjustment-event"></a>ThreadPoolWorkerThreadAdjustmentAdjustment 事件

 下表說明關鍵字和層級。

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|告知性 (4)|

 下表說明事件資訊。

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|55|當執行緒插入 (攀登) 演算法判斷具有並行層級時，記錄控制中的變更。|

 下表說明事件資料。

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`AverageThroughput`|`win:Double`|度量範例的平均輸送量。|
|`NewWorkerThreadCount`|`win:UInt32`|作用中背景工作執行緒的新數目。|
|`Reason`|`win:UInt32`|調整的原因。<br /><br /> `0x0` 預熱.<br /><br /> `0x1` 初始化.<br /><br /> `0x2` -隨機移動。<br /><br /> `0x3` -上升移動。<br /><br /> `0x4` -變更點。<br /><br /> `0x5` 穩定化.<br /><br /> `0x6` 不足.<br /><br /> `0x7` -執行緒超時。|
|`ClrInstanceID`|`win:UInt16`|CLR 或 CoreCLR 執行個體的唯一 ID。|

## <a name="threadpoolworkerthreadadjustmentstats-event"></a>ThreadPoolWorkerThreadAdjustmentStats 事件

 下表說明關鍵字和層級。

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|詳細資訊 (5)

 下表說明事件資訊。

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentStats`|56|收集執行緒集區的資料。|

 下表顯示事件資料

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`Duration`|`win:Double`|收集這些統計資料期間的時間量 (以秒為單位)。|
|`Throughput`|`win:Double`|在這段間隔期間，每秒完成的平均數目。|
|`ThreadWave`|`win:Double`|保留供內部使用。|
|`ThroughputWave`|`win:Double`|保留供內部使用。|
|`ThroughputErrorEstimate`|`win:Double`|保留供內部使用。|
|`AverageThroughputErrorEstimate`|`win:Double`|保留供內部使用。|
|`ThroughputRatio`|`win:Double`|在這段間隔期間，正在作用中的背景工作執行緒計數變更所造成的輸送量相對改善。|
|`Confidence`|`win:Double`|ThroughputRatio 欄位有效性的度量。|
|`NewcontrolSetting`|`win:Double`|作用中背景工作執行緒數目，其將做為作用中執行緒計數未來變化的基準。|
|`NewThreadWaveMagnitude`|`win:UInt16`|作用中執行緒計數未來變化的範圍。|
|`ClrInstanceID`|`win:UInt16`|CLR 或 CoreCLR 執行個體的唯一 ID。|

## <a name="threadpoolenqueue-event"></a>ThreadPoolEnqueue 事件

 下表說明關鍵字和層級。

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|詳細資訊 (5)

 下表說明事件資訊。

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`ThreadPoolEnqueue`|61|工作專案已排入執行緒集區佇列中。|

 下表顯示事件資料

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`WorkID`|`win:Pointer`|工作要求的指標。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="threadpooldequeue-event"></a>ThreadPoolDequeue 事件

 下表說明關鍵字和層級。

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|詳細資訊 (5)

 下表說明事件資訊。

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`ThreadPoolDequeue`|62|工作專案已從執行緒集區佇列中清除。|

 下表顯示事件資料

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`WorkID`|`win:Pointer`|工作要求的指標。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="threadpoolioenqueue-event"></a>ThreadPoolIOEnqueue 事件

 下表說明關鍵字和層級。

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|詳細資訊 (5)

 下表說明事件資訊。

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`ThreadPoolIOEnqueue`|63|在非同步 IO 完成之後，執行緒會將 IO 完成通知。|

 下表顯示事件資料

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|保留供內部使用。|
|`Overlapped`|`win:Pointer`|保留供內部使用。|
|`MultiDequeues`|`win:Boolean`|保留供內部使用。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="threadpooliodequeue-event"></a>ThreadPoolIODequeue 事件

 下表說明關鍵字和層級。

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|詳細資訊 (5)

 下表說明事件資訊。

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`ThreadPoolIODequeue`|64|清除 IO 完成通知的執行緒。|

 下表顯示事件資料

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|保留供內部使用。|
|`Overlapped`|`win:Pointer`|保留供內部使用。|
|`MultiDequeues`|`win:Boolean`|保留供內部使用。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="threadpooliopack-event"></a>ThreadPoolIOPack 事件

 下表說明關鍵字和層級。

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|詳細資訊 (5)|

 下表說明事件資訊。

|事件|事件識別碼|描述|
|-----------|--------------|-----------------|
|`ThreadPoolIOPack`|65|呼叫 ThreadPool 重迭 IO 套件。|

 下表顯示事件資料

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|保留供內部使用。|
|`Overlapped`|`win:Pointer`|保留供內部使用。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="threadcreating-event"></a>ThreadCreating 事件

 下表說明關鍵字和層級。

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|告知性 (4)|

 下表說明事件資訊。

|事件|事件識別碼|描述|
|----------------|---------------|-----------------|
|`ThreadCreating`|70|已建立執行緒。|

 下表說明事件資料。

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`ID`|`win:Pointer`|執行緒識別碼|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="threadrunning-event"></a>ThreadRunning 事件

 下表說明關鍵字和層級。

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`ThreadingKeyword` (0x10000)|告知性 (4)|

 下表說明事件資訊。

|事件|事件識別碼|描述|
|----------------|---------------|-----------------|
|`ThreadRunning`|71|執行緒已開始執行。|

 下表說明事件資料。

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`ID`|`win:Pointer`|執行緒識別碼|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|
