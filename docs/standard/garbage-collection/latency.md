---
title: "延遲模式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- garbage collection, intrusiveness
- garbage collection, latency modes
ms.assetid: 96278bb7-6eab-4612-8594-ceebfc887d81
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d0ac0db376ad7cd4aa139ed0eb065a5ba33836c8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="latency-modes"></a>延遲模式
為了回收物件，記憶體回收行程必須停止應用程式中所有正在執行的執行緒。 在某些情況下，例如當應用程式擷取資料或顯示內容時，完整記憶體回收會在關鍵時刻進行，而妨礙效能。 您可以藉由設定 <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> 屬性為 <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> 值的其中一個，來調整記憶體回收行程的干擾程度。  
  
 延遲指的是記憶體回收行程干擾應用程式的時間。 在低延遲期間，記憶體回收行程會更加保守，也較不干擾啟用物件。 <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> 列舉會提供兩個低延遲設定：  
  
-   <xref:System.Runtime.GCLatencyMode.LowLatency> 會隱藏層代 2 回收，並且只執行層代 0 和 1 回收。 它只適合短時間使用。 經過一段較長的時間後，如果系統記憶體吃緊，則記憶體回收行程將會觸發回收，該回收可能會短暫暫停應用程式，並且中斷時間關鍵的作業。 這項設定僅適用於工作站記憶體回收。  
  
-   <xref:System.Runtime.GCLatencyMode.SustainedLowLatency> 會隱藏前景層代 2 回收，並且只執行層代 0、1 和背景層代 2 回收。 它可以長時間使用，並且可用於工作站和伺服器記憶體回收。 如果已停用[並行記憶體回收](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)，則無法使用這個設定。  
  
 在低延遲期間，會隱藏層代 2 回收，除非發生下列情況：  
  
-   系統從作業系統接收到記憶體不足的通知。  
  
-   應用程式程式碼會呼叫 <xref:System.GC.Collect%2A?displayProperty=nameWithType> 方法並指定 `generation` 參數為 2 來進行回收。  
  
 下表列出使用 <xref:System.Runtime.GCLatencyMode> 值的應用程式案例。  
  
|延遲模式|應用程式案例|  
|------------------|---------------------------|  
|<xref:System.Runtime.GCLatencyMode.Batch>|對於沒有 UI 或伺服器端作業的應用程式。<br /><br /> 這是[並行記憶體回收](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)停用時的預設模式。|  
|<xref:System.Runtime.GCLatencyMode.Interactive>|對於大部分有使用者介面的應用程式，<br /><br /> 這是[並行記憶體回收](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)啟用時的預設模式。|  
|<xref:System.Runtime.GCLatencyMode.LowLatency>|對於具有短期、對時間敏感作業的應用程式，其執行期間可能受到記憶體回收行程中斷的干擾。 例如，應用程式使用動畫呈現或資料擷取的函式。|  
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|適合的應用程式具有對時間敏感的作業，這些作業可能長時間持續執行，且這段執行時間內可能經常受到記憶體回收行程中斷的干擾。 例如，因為交易時間內市場資料不斷變化，而需要迅速回應的應用程式。<br /><br /> 這個模式會所產生的 Managed 堆積大小會比其他模式更大。 由於它不會壓縮 Managed 堆積，因此磁碟可能會高度分割。 確定有足夠的記憶體可供使用。|  
  
## <a name="guidelines-for-using-low-latency"></a>使用低延遲的指導方針  
 當您使用 <xref:System.Runtime.GCLatencyMode.LowLatency> 模式時，請考慮下列指導方針：  
  
-   盡可能縮短這段低延遲的時間。  
  
-   請避免在低延遲期間配置大量記憶體。 因為記憶體回收較少物件時，會造成記憶體不足的通知。  
  
-   在低延遲模式時，盡量減少配置數目，特別是配置到大型物件堆積和 Pin 物件的數目。  
  
-   請注意無法配置的執行緒。 因為 <xref:System.Runtime.GCSettings.LatencyMode%2A> 屬性設定為整個處理序，或許會在可能配置的任何執行緒中產生 <xref:System.OutOfMemoryException>。  
  
-   將低度延遲的程式碼包裝在限制執行區域 (如需詳細資訊，請參閱[限制執行區域](../../../docs/framework/performance/constrained-execution-regions.md))。  
  
-   您也可以呼叫 <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType> 方法，在低延遲期間強制層代 2 回收。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.GC?displayProperty=nameWithType>  
 [引發的收集](../../../docs/standard/garbage-collection/induced.md)  
 [記憶體回收](../../../docs/standard/garbage-collection/index.md)
