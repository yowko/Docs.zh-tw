---
title: 引發的集合
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, forced
ms.assetid: 019008fe-4708-4e65-bebf-04fd9941e149
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69590b0efc924132d149621c135ef0816cac7d1e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44192544"
---
# <a name="induced-collections"></a>引發的集合
大部分情況下，記憶體回收行程會判斷執行回收的最佳時間，請讓記憶體回收行程獨立執行。 在罕見的情況下，強制回收可能會改善您應用程式的效能。 在這些情況下，您可以使用 <xref:System.GC.Collect%2A?displayProperty=nameWithType> 方法強制進行記憶體回收，來引發記憶體回收。  
  
 在應用程式碼特定位置所使用的記憶體數量大幅下降時，請使用 <xref:System.GC.Collect%2A?displayProperty=nameWithType> 方法。 例如，如果您的應用程式使用具有數個控制項的複雜對話方塊，則在關閉對話方塊時呼叫 <xref:System.GC.Collect%2A> 可透過立即回收對話方塊所使用的記憶體來改善效能。 請確定您的應用程式沒有太頻繁地進行記憶體回收，原因是如果記憶體回收行程嘗試在非最佳時間回收物件，則這樣可能會降低效能。 您可以將 <xref:System.GCCollectionMode.Optimized?displayProperty=nameWithType> 列舉值提供給 <xref:System.GC.Collect%2A> 方法，只在回收具備生產力時才進行回收 (如下節所討論)。  
  
## <a name="gc-collection-mode"></a>GC 收集模式  
 您可以使用其中一個 <xref:System.GC.Collect%2A?displayProperty=nameWithType> 方法多載，其包含 <xref:System.GCCollectionMode> 值來指定強制回收行為，如下所示。  
  
|`GCCollectionMode` 值|描述|  
|------------------------------|-----------------|  
|<xref:System.GCCollectionMode.Default>|使用 .NET 執行版本的預設記憶體回收設定。|  
|<xref:System.GCCollectionMode.Forced>|強制立即進行記憶體回收。 這等於呼叫 <xref:System.GC.Collect?displayProperty=nameWithType> 多載。 它會導致完整封鎖回收所有層代。<br /><br /> 您也可以在強制執行立即的完整區塊記憶體回收之前，透過將 <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> 屬性設定為 <xref:System.Runtime.GCLargeObjectHeapCompactionMode.CompactOnce?displayProperty=nameWithType> 來壓縮大型物件。|  
|<xref:System.GCCollectionMode.Optimized>|可讓記憶體回收行程判斷目前時間是否最適合回收物件。<br /><br /> 記憶體回收行程可能會判斷回收的生產力不足無法進行調整，在此情況下會返回，而不是回收物件。|  
  
## <a name="background-or-blocking-collections"></a>背景或封鎖回收  
 您可以呼叫 <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29?displayProperty=nameWithType> 方法多載，來指定是否封鎖引發的回收。 執行的回收類型取決於方法的 `mode` 與 `blocking` 參數組合。 `mode` 不是 <xref:System.GCCollectionMode> 列舉的成員，且 `blocking` 為 <xref:System.Boolean> 值。 下表摘要說明 `mode` 和 `blocking` 引數的互動。  
  
|`mode`|`blocking` = `true`|`blocking` = `false`|  
|------------|--------------------------|---------------------------|  
|<xref:System.GCCollectionMode.Forced> 或 <xref:System.GCCollectionMode.Default>|會盡快執行封鎖回收。 如果正在進行背景回收，而且層代是 0 或 1，則 <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> 方法會立即觸發封鎖回收，並在回收完成時返回。 如果正在進行背景回收，而且 `generation` 參數是 2，則方法會等到背景回收完成，並觸發封鎖層代 2 回收，然後返回。|會盡快執行回收。 <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> 方法會要求背景集合，但不保證可取得。視情況而定，可能仍會執行封鎖集合。 如果已在進行背景回收，則這個方法會立即返回。|  
|<xref:System.GCCollectionMode.Optimized>|可能會因記憶體回收行程和 `generation` 參數的狀態而執行封鎖集合。 記憶體回收行程會嘗試提供最佳效能。|根據記憶體回收行程的狀態，可能會執行回收。 <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> 方法會要求背景集合，但不保證可取得。視情況而定，可能仍會執行封鎖集合。 記憶體回收行程會嘗試提供最佳效能。 如果已在進行背景回收，則這個方法會立即返回。|  
  
## <a name="see-also"></a>另請參閱

- [延遲模式](../../../docs/standard/garbage-collection/latency.md)  
- [記憶體回收](../../../docs/standard/garbage-collection/index.md)
