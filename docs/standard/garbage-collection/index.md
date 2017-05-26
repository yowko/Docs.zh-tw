---
title: "記憶體回收 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- memory, garbage collection
- garbage collection, automatic memory management
- GC [.NET Framework]
- memory, allocating
- common language runtime, garbage collection
- garbage collector
- cleanup operations
- garbage collection
- memory, releasing
- common language runtime, automatic memory management
- automatic memory management
- runtime, automatic memory management
- runtime, garbage collection
- garbage collection, about
ms.assetid: 22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9
caps.latest.revision: 36
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 11ea4186a77a600d1645fe334ba9fd704fe728b4
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---
# <a name="garbage-collection"></a>記憶體回收
.NET 的記憶體回收行程可管理應用程式的記憶體配置及釋放。 每次當您建立新的物件時，通用語言執行平台會從 Managed 堆積配置物件的記憶體。 只要 Managed 堆積中有可供使用的位址空間，平台就會繼續為新的物件配置空間。 不過，記憶體不是無限的。 因此記憶體回收行程最後就必須執行回收以釋放一些記憶體。 記憶體回收行程的最佳化引擎會根據所做的配置，決定執行回收的最佳時機。 當記憶體回收行程執行回收時，會檢查 Managed 堆積中是否有應用程式不再使用的物件，並執行必要的作業以回收其記憶體。  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[記憶體回收的基本概念](../../../docs/standard/garbage-collection/fundamentals.md)|描述記憶體回收運作方式、如何在 Managed 堆積上配置物件，以及其他核心概念。|  
|[記憶體回收和效能](../../../docs/standard/garbage-collection/performance.md)|描述可用來診斷記憶體回收和效能問題的效能檢查。|  
|[引發的收集](../../../docs/standard/garbage-collection/induced.md)|描述如何進行記憶體回收。|  
|[延遲模式](../../../docs/standard/garbage-collection/latency.md)|描述判斷記憶體回收干擾程度的模式。|  
|[共用 Web 裝載的最佳化](../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md)|描述如何最佳化伺服器上由數個小型網站所共用的記憶體回收。|  
|[記憶體回收通知](../../../docs/standard/garbage-collection/notifications.md)|描述如何判斷何時接近完整的記憶體回收，以及何時已完成。|  
|[應用程式定義域資源監視](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)|描述如何監視應用程式定義域的 CPU 和記憶體使用量。|  
|[弱式參考](../../../docs/standard/garbage-collection/weak-references.md)|描述下列功能：允許記憶體回收行程回收物件，同時仍然允許應用程式存取該物件。|  
  
## <a name="reference"></a>參考資料  
 <xref:System.GC?displayProperty=fullName>  
  
 <xref:System.GCCollectionMode?displayProperty=fullName>  
  
 <xref:System.GCNotificationStatus?displayProperty=fullName>  
  
 <xref:System.Runtime.GCLatencyMode?displayProperty=fullName>  
  
 <xref:System.Runtime.GCSettings?displayProperty=fullName>  
  
 <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=fullName>  
  
 <xref:System.Object.Finalize%2A?displayProperty=fullName>  
  
 <xref:System.IDisposable?displayProperty=fullName>  
  
## <a name="see-also"></a>另請參閱  
 [清除 Unmanaged 資源](../../../docs/standard/garbage-collection/unmanaged.md)
