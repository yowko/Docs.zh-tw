---
title: 執行緒集區 ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- thread pool events [.NET Framework]
- ETW, thread pool events (CLR)
ms.assetid: f2a21e3a-3b6c-4433-97f3-47ff16855ecc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: caacee591c4df8389cea241916618f50da56b22b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119128"
---
# <a name="thread-pool-etw-events"></a>執行緒集區 ETW 事件
<a name="top"></a> 這些事件會收集背景工作和 I/O 執行緒的資訊。  
  
 執行緒集區事件可分兩組：  
  
-   [背景工作執行緒集區事件](#worker)，提供有關應用程式如何使用執行緒集區，以及工作負載對並行存取控制項之影響的資訊。  
  
-   [I/O 執行緒集區事件](#io)，提供有關執行緒集區中所建立、淘汰、取消淘汰或終止之 I/O 執行緒的資訊。  
  
<a name="worker"></a>   
## <a name="worker-thread-pool-events"></a>背景工作執行緒集區事件  
 這些事件與執行階段的背景工作執行緒集區有關，可提供執行緒事件 (例如建立或停止執行緒) 的通知。 背景工作執行緒集區會使用適應性演算法來進行並行存取控制項，其中執行緒的數目是根據測量的輸送量計算而得。 背景工作執行緒集區事件可用以了解應用程式如何使用執行緒集區，以及特定工作負載可能對並行存取控制項所造成的影響。  
  
### <a name="threadpoolworkerthreadstart-and-threadpoolworkerthreadstop"></a>ThreadPoolWorkerThreadStart 與 ThreadPoolWorkerThreadStop  
 下表顯示這些事件的關鍵字與層級。 (如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|告知性 (4)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|引發的時機|  
|-|-|-|  
|`ThreadPoolWorkerThreadStart`|50|建立背景工作執行緒時。|  
|`ThreadPoolWorkerThreadStop`|51|停止背景工作執行緒時。|  
|`ThreadPoolWorkerThreadRetirementStart`|52|淘汰背景工作執行緒時。|  
|`ThreadPoolWorkerThreadRetirementStop`|53|淘汰的背景工作執行緒再次作用時。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|ActiveWorkerThreadCount|win:UInt32|可用以處理工作的背景工作執行緒數目，其包含正在處理工作的執行緒。|  
|RetiredWorkerThreadCount|win:UInt32|無法用以處理工作的背景工作執行緒數目，但其正處於保留狀態以免之後需要更多執行緒。|  
|ClrInstanceID|Win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
### <a name="threadpoolworkerthreadadjustment"></a>ThreadPoolWorkerThreadAdjustment  
 這些執行緒集區事件會提供一些資訊，可讓您了解及偵錯執行緒插入 (並行存取控制項) 演算法的行為。 背景工作執行緒集區會於內部使用此資訊。  
  
#### <a name="threadpoolworkerthreadadjustmentsample"></a>ThreadPoolWorkerThreadAdjustmentSample  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|告知性 (4)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|描述|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentSample`|54|表示單一範例的資訊集合。亦即，具有特定並行層級之輸送量的瞬間量。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|輸送量|win:Double|每個時間單位完成的數目。|  
|ClrInstanceID|Win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
#### <a name="threadpoolworkerthreadadjustmentadjustment"></a>ThreadPoolWorkerThreadAdjustmentAdjustment  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|告知性 (4)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|描述|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|55|當執行緒插入 (攀登) 演算法判斷具有並行層級時，記錄控制中的變更。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|AverageThroughput|win:Double|度量範例的平均輸送量。|  
|NewWorkerThreadCount|win:UInt32|作用中背景工作執行緒的新數目。|  
|原因|win:UInt32|調整的原因。<br /><br /> 0x00 - 熱身。<br /><br /> 0x01 - 初始化。<br /><br /> 0x02 - 隨機移動。<br /><br /> 0x03 - 攀登移動。<br /><br /> 0x04 - 變更點。<br /><br /> 0x05 - 穩定。<br /><br /> 0x06 - 資源不足。<br /><br /> 0x07 - 執行緒逾時。|  
|ClrInstanceID|Win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
#### <a name="threadpoolworkerthreadadjustmentstats"></a>ThreadPoolWorkerThreadAdjustmentStats  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|告知性 (4)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|描述|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentStats`|56|收集執行緒集區的資料。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|持續期間|win:Double|收集這些統計資料期間的時間量 (以秒為單位)。|  
|輸送量|win:Double|在這段間隔期間，每秒完成的平均數目。|  
|ThreadWave|win:Double|保留供內部使用。|  
|ThroughputWave|win:Double|保留供內部使用。|  
|ThroughputErrorEstimate|win:Double|保留供內部使用。|  
|AverageThroughputErrorEstimate|win:Double|保留供內部使用。|  
|ThroughputRatio|win:Double|在這段間隔期間，正在作用中的背景工作執行緒計數變更所造成的輸送量相對改善。|  
|Confidence|win:Double|ThroughputRatio 欄位有效性的度量。|  
|NewcontrolSetting|win:Double|作用中背景工作執行緒數目，其將做為作用中執行緒計數未來變化的基準。|  
|NewThreadWaveMagnitude|Win:UInt16|作用中執行緒計數未來變化的範圍。|  
|ClrInstanceID|Win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
 [回到頁首](#top)  
  
<a name="io"></a>   
## <a name="io-thread-events"></a>I/O 執行緒事件  
 會針對非同步 I/O 執行緒集區 (完成連接埠) 中的執行緒發生這些執行緒集區事件。  
  
### <a name="iothreadcreatev1"></a>IOThreadCreate_V1  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|告知性 (4)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|引發的時機|  
|-|-|-|  
|`IOThreadCreate_V1`|44|在執行緒集區中建立 I/O 執行緒時。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|計數|win:UInt64|I/O 執行緒的數目，其包含新建立的執行緒。|  
|NumRetired|win:UInt64|已淘汰之背景工作執行緒的數目。|  
|ClrInstanceID|Win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
### <a name="iothreadretirev1"></a>IOThreadRetire_V1  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|告知性 (4)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`IOThreadRetire_V1`|46|當 I/O 執行緒變成淘汰候選時。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|計數|win:UInt64|執行緒集區中剩餘的 I/O 執行緒數目。|  
|NumRetired|win:UInt64|已淘汰的 I/O 執行緒數目。|  
|ClrInstanceID|Win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
### <a name="iothreadunretirev1"></a>IOThreadUnretire_V1  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|告知性 (4)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`IOThreadUnretire_V1`|47|因為在執行緒變成淘汰候選之後，I/O 在等候期間內到達，而導致 I/O 執行緒取消淘汰時。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|計數|win:UInt64|執行緒集區中的 I/O 執行緒數目，包含此執行緒。|  
|NumRetired|win:UInt64|已淘汰的 I/O 執行緒數目。|  
|ClrInstanceID|Win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
### <a name="iothreadterminate"></a>IOThreadTerminate  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|告知性 (4)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`IOThreadTerminate`|45|在執行緒集區中建立 I/O 執行緒時。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|計數|win:UInt64|執行緒集區中剩餘的 I/O 執行緒數目。|  
|NumRetired|win:UInt64|已淘汰的 I/O 執行緒數目。|  
|ClrInstanceID|Win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
## <a name="see-also"></a>另請參閱

- [CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)
