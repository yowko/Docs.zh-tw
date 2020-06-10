---
title: .NET 垃圾收集
description: 瞭解 .NET 中的垃圾收集。 .NET 垃圾收集行程會管理應用程式的記憶體配置和釋放。
ms.date: 04/21/2020
ms.technology: dotnet-standard
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
ms.openlocfilehash: dde0012ff7233eb7ee13efab1931f129b0eae276
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662481"
---
# <a name="garbage-collection"></a>記憶體回收

.NET 的記憶體回收行程可管理應用程式的記憶體配置及釋放。 每次當您建立新的物件時，通用語言執行平台會從 Managed 堆積配置物件的記憶體。 只要 Managed 堆積中有可供使用的位址空間，平台就會繼續為新的物件配置空間。 不過，記憶體不是無限的。 因此記憶體回收行程最後就必須執行回收以釋放一些記憶體。 記憶體回收行程的最佳化引擎會根據所做的配置，決定執行回收的最佳時機。 當記憶體回收行程執行回收時，會檢查 Managed 堆積中是否有應用程式不再使用的物件，並執行必要的作業以回收其記憶體。  
  
## <a name="in-this-section"></a>本節內容
  
|Title|描述|  
|-----------|-----------------|  
|[垃圾收集的基本概念](fundamentals.md)|描述記憶體回收運作方式、如何在 Managed 堆積上配置物件，以及其他核心概念。|  
|[工作站和伺服器記憶體回收](workstation-server-gc.md)|說明用戶端應用程式的工作站垃圾收集與伺服器應用程式的伺服器垃圾收集之間的差異。|
|[背景垃圾收集](background-gc.md)|描述背景垃圾收集，這是層代0和1物件的集合，而層代2回收正在進行中。|
|[大型物件堆積](large-object-heap.md)|描述大型物件堆積（LOH），以及如何將大型物件進行垃圾收集。|
|[記憶體回收和效能](performance.md)|描述可用來診斷記憶體回收和效能問題的效能檢查。|  
|[引發的回收](induced.md)|描述如何進行記憶體回收。|  
|[延遲模式](latency.md)|描述判斷記憶體回收干擾程度的模式。|  
|[共用 Web 裝載的最佳化](optimization-for-shared-web-hosting.md)|描述如何最佳化伺服器上由數個小型網站所共用的記憶體回收。|  
|[記憶體回收通知](notifications.md)|描述如何判斷何時接近完整的記憶體回收，以及何時已完成。|  
|[應用程式定義域資源監視](app-domain-resource-monitoring.md)|描述如何監視應用程式定義域的 CPU 和記憶體使用量。|  
|[弱式參考](weak-references.md)|描述下列功能：允許記憶體回收行程回收物件，同時仍然允許應用程式存取該物件。|  
  
## <a name="reference"></a>參考

- <xref:System.GC?displayProperty=nameWithType>  
- <xref:System.GCCollectionMode?displayProperty=nameWithType>  
- <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
- <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a>另請參閱

- [清除非受控資源](unmanaged.md)
