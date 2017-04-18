---
title: "引發的集合 | Microsoft Docs"
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
  - "記憶體回收，強制"
ms.assetid: 019008fe-4708-4e65-bebf-04fd9941e149
caps.latest.revision: 20
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 20
---
# 引發的集合
大部分的情況下，記憶體回收行程會判斷執行回收的最佳時間，請讓記憶體回收行程獨立執行。  在極少數的情況下，強制回收可能會增進應用程式的效能。  此時，您可以使用 <xref:System.GC.Collect%2A?displayProperty=fullName> 方法以強制執行記憶體回收。  
  
 當應用程式的程式碼中特定點上的記憶體使用量明顯減少時，請使用 <xref:System.GC.Collect%2A?displayProperty=fullName> 方法。  例如，如果您的應用程式使用內含多個控制項的複雜對話方塊，則當對話方塊關閉時，呼叫 <xref:System.GC.Collect%2A> 立即回收對話方塊使用的記憶體，可以提高效能。  請確定應用程式不會太過頻繁的引發記憶體回收，因為如果記憶體回收行程嘗試回收物件的次數並非最佳，就會降低效能。  您可以提供 <xref:System.GCCollectionMode?displayProperty=fullName> 列舉值給 <xref:System.GC.Collect%2A> 方法，只有在收集具有生產力時進行收集，如下一節所述。  
  
## GC 回收模式  
 您可以使用其中一個包含 <xref:System.GCCollectionMode> 值的 <xref:System.GC.Collect%2A?displayProperty=fullName> 方法多載，指定強制回收的行為，如下所述。  
  
|`GCCollectionMode` 值|描述|  
|--------------------------|--------|  
|<xref:System.GCCollectionMode>|使用執行中 .NET Framework 版本的預設記憶體回收之設定。|  
|<xref:System.GCCollectionMode>|強制立即執行記憶體回收。  這相當於呼叫 <xref:System.GC.Collect?displayProperty=fullName> 多載。  這會產生所有層代的完整封鎖集合。<br /><br /> 您也可以在強制立即完整的封鎖記憶體回收之前，藉由將 <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=fullName> 屬性設為 <xref:System.Runtime.GCLargeObjectHeapCompactionMode?displayProperty=fullName> 壓縮大型物件堆積。|  
|<xref:System.GCCollectionMode>|啟用記憶體回收以判斷現在是否是回收物件的最佳時間。<br /><br /> 記憶體回收行程會判斷，執行回收是否能有效提高生產力，如果不能就會返回而不回收物件。|  
  
## 背景或封鎖集合  
 您可以呼叫 <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29?displayProperty=fullName> 方法多載，指定引發的集合是否封鎖。  所執行的集合類型需視方法的 `mode` 和 `blocking` 參數組合而定。  `mode` 是 <xref:System.GCCollectionMode> 列舉類型的成員，`blocking` 則是 <xref:System.Boolean> 的值。  下表摘要說明 `mode` 和 `blocking` 引數的互動。  
  
|`mode`|`blocking` \= `true`|`blocking` \= `false`|  
|------------|--------------------------|---------------------------|  
|<xref:System.GCCollectionMode> 或 <xref:System.GCCollectionMode>|封鎖集合儘快執行。  如果背景集合正在進行且層代為 0 或 1，則 <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> 方法會立即觸發封鎖集合，並且在集合完成時傳回。  如果背景集合正在進行且 `generation` 參數為 2，則此方法會等候直到背景集合完成，觸發封鎖層代 2 集合，然後傳回。|集合儘快執行。  <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> 方法會要求背景集合，但不保證可取得。視情況而定，可能仍會執行封鎖集合。  如果背景集合已在進行中，方法會立即傳回。|  
|<xref:System.GCCollectionMode>|可能會因記憶體回收行程和 `generation` 參數的狀態而執行封鎖集合。  記憶體回收行程會嘗試提供最佳效能。|可能會因記憶體回收行程的狀態而執行集合。  <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> 方法會要求背景集合，但不保證可取得。視情況而定，可能仍會執行封鎖集合。  記憶體回收行程會嘗試提供最佳效能。  如果背景集合已在進行中，方法會立即傳回。|  
  
## 請參閱  
 [Latency Modes](../../../docs/standard/garbage-collection/latency.md)   
 [Garbage Collection](../../../docs/standard/garbage-collection/index.md)