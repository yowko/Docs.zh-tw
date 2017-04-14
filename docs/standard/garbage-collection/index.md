---
title: "Garbage Collection | Microsoft Docs"
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
  - "memory, garbage collection"
  - "garbage collection, automatic memory management"
  - "GC [.NET Framework]"
  - "memory, allocating"
  - "common language runtime, garbage collection"
  - "garbage collector"
  - "cleanup operations"
  - "garbage collection"
  - "memory, releasing"
  - "common language runtime, automatic memory management"
  - "automatic memory management"
  - "runtime, automatic memory management"
  - "runtime, garbage collection"
  - "garbage collection, about"
ms.assetid: 22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9
caps.latest.revision: 36
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 36
---
# Garbage Collection
.NET Framework 的記憶體回收行程會管理您應用程式記憶體的配置和釋放。  每當您建立物件時，Common Language Runtime 便會針對 Managed 堆積中的物件配置記憶體。  只要在 Managed 堆積中有位址空間可用，Runtime 就會繼續為新物件配置記憶體。  但是，記憶體畢竟不是無限的。  到最後，記憶體回收行程還是必須進行回收以釋放某些記憶體。  記憶體回收行程的最佳化引擎會依據所做的配置決定進行回收的最佳時機。  當記憶體回收行程進行回收時，它會檢查 Managed 堆積中應用程式已不再使用的物件，並且執行必要作業以回收它們的記憶體。  
  
<a name="related_topics"></a>   
## 相關主題  
  
|標題|描述|  
|--------|--------|  
|[Fundamentals of Garbage Collection](../../../docs/standard/garbage-collection/fundamentals.md)|描述記憶體回收如何運作、如何在 Managed 堆積上配置物件，以及其他核心概念。|  
|[Garbage Collection and Performance](../../../docs/standard/garbage-collection/performance.md)|描述您可以用來診斷記憶體回收和效能問題的效能檢查。|  
|[引發的集合](../../../docs/standard/garbage-collection/induced.md)|描述如何進行記憶體回收。|  
|[Latency Modes](../../../docs/standard/garbage-collection/latency.md)|描述判斷記憶體回收干擾程度的模式。|  
|[Optimization for Shared Web Hosting](../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md)|描述如何在多個小型網站共用的伺服器上最佳化記憶體回收。|  
|[Garbage Collection Notifications](../../../docs/standard/garbage-collection/notifications.md)|描述如何判斷何時即將進行完整記憶體回收以及何時完成。|  
|[Application Domain Resource Monitoring](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)|描述如何監視應用程式定義域的 CPU 和記憶體使用量。|  
|[Weak References](../../../docs/standard/garbage-collection/weak-references.md)|描述允許記憶體回收行程回收物件，同時允許應用程式存取物件的功能。|  
  
## 參考資料  
 <xref:System.GC?displayProperty=fullName>  
  
 <xref:System.GCCollectionMode?displayProperty=fullName>  
  
 <xref:System.GCNotificationStatus?displayProperty=fullName>  
  
 <xref:System.Runtime.GCLatencyMode?displayProperty=fullName>  
  
 <xref:System.Runtime.GCSettings?displayProperty=fullName>  
  
 <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=fullName>  
  
 <xref:System.Object.Finalize%2A?displayProperty=fullName>  
  
 <xref:System.IDisposable?displayProperty=fullName>  
  
## 請參閱  
 [Cleaning Up Unmanaged Resources](../../../docs/standard/garbage-collection/unmanaged.md)