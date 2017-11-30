---
title: "引發的集合"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: garbage collection, forced
ms.assetid: 019008fe-4708-4e65-bebf-04fd9941e149
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 92918e347b10dfcf3a0d6e2c08cec8c7a6963f5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="induced-collections"></a>引發的集合
大部分情況下，記憶體回收行程會判斷執行回收的最佳時間，請讓記憶體回收行程獨立執行。 在罕見的情況下，強制回收可能會改善您應用程式的效能。 在這些情況下，您可以藉由引發記憶體回收<xref:System.GC.Collect%2A?displayProperty=nameWithType>方法，以強制執行記憶體回收。  
  
 使用<xref:System.GC.Collect%2A?displayProperty=nameWithType>大幅降低記憶體正在使用您的應用程式程式碼中的特定點時的方法。 例如，如果您的應用程式會使用複雜的對話方塊中，有幾個控制項，呼叫<xref:System.GC.Collect%2A>關閉對話方塊時無法改善效能立即回收對話方塊中所使用的記憶體。 請確定您的應用程式沒有太頻繁地進行記憶體回收，原因是如果記憶體回收行程嘗試在非最佳時間回收物件，則這樣可能會降低效能。 您可以提供<xref:System.GCCollectionMode.Optimized?displayProperty=nameWithType>列舉值，以<xref:System.GC.Collect%2A>只能在下一節中所述，集合會是高生產力、 時要收集的方法。  
  
## <a name="gc-collection-mode"></a>GC 收集模式  
 您可以使用其中一個<xref:System.GC.Collect%2A?displayProperty=nameWithType>方法多載，包括<xref:System.GCCollectionMode>指定強制集合的行為，如下所示的值。  
  
|`GCCollectionMode` 值|說明|  
|------------------------------|-----------------|  
|<xref:System.GCCollectionMode.Default>|執行版本的.NET 中使用的預設記憶體回收集合設定。|  
|<xref:System.GCCollectionMode.Forced>|強制立即進行記憶體回收。 這就相當於呼叫<xref:System.GC.Collect?displayProperty=nameWithType>多載。 它會導致完整封鎖回收所有層代。<br /><br /> 您也可以藉由設定壓縮大型物件堆積<xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>屬性<xref:System.Runtime.GCLargeObjectHeapCompactionMode.CompactOnce?displayProperty=nameWithType>之前強制執行立即完全封鎖記憶體回收。|  
|<xref:System.GCCollectionMode.Optimized>|可讓記憶體回收行程判斷目前時間是否最適合回收物件。<br /><br /> 記憶體回收行程可能會判斷回收的生產力不足無法進行調整，在此情況下會返回，而不是回收物件。|  
  
## <a name="background-or-blocking-collections"></a>背景或封鎖回收  
 您可以呼叫<xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29?displayProperty=nameWithType>方法多載來指定是否封鎖或不引發的集合。 執行集合的型別取決於方法的組合`mode`和`blocking`參數。 `mode`成員的<xref:System.GCCollectionMode>列舉型別和`blocking`是<xref:System.Boolean>值。 下表摘要說明之間的互動`mode`和`blocking`引數。  
  
|`mode`|`blocking` = `true`|`blocking` = `false`|  
|------------|--------------------------|---------------------------|  
|<xref:System.GCCollectionMode.Forced> 或 <xref:System.GCCollectionMode.Default>|會盡快執行封鎖回收。 如果背景回收正在進行且層代 0 或 1，<xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29>方法立即觸發封鎖的集合，並在完成集合後傳回。 如果正在進行中的背景集合和`generation`參數為 2，則方法會等候直到背景回收完成時，封鎖的層代 2 回收，觸發程序，然後傳回。|會盡快執行回收。 <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29>方法要求背景集合，但這不保證; 根據情況，封鎖的集合可能仍會執行。 如果已在進行背景回收，則這個方法會立即返回。|  
|<xref:System.GCCollectionMode.Optimized>|封鎖的集合可能會執行，根據記憶體回收行程的狀態和`generation`參數。 記憶體回收行程會嘗試提供最佳效能。|根據記憶體回收行程的狀態，可能會執行回收。 <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29>方法要求背景集合，但這不保證; 根據情況，封鎖的集合可能仍會執行。 記憶體回收行程會嘗試提供最佳效能。 如果已在進行背景回收，則這個方法會立即返回。|  
  
## <a name="see-also"></a>另請參閱  
 [延遲模式](../../../docs/standard/garbage-collection/latency.md)  
 [記憶體回收](../../../docs/standard/garbage-collection/index.md)
