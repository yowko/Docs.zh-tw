---
title: "Managed Threading Basics | Microsoft Docs"
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
  - "multiple threads"
  - "threading [.NET Framework], multiple threads"
  - "threading [.NET Framework], about threading"
  - "managed threading"
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 16
---
# Managed Threading Basics
本章節的前五個主題可以幫助您決定何時使用 Managed 執行緒處理，並且說明一些基本功能。  如需可提供其他功能之類別的相關資訊，請參閱[Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)和[Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md)。  
  
 這個章節還涵蓋其他進階主題，包括 Managed 執行緒處理與 Windows 作業系統之間的互動。  
  
> [!NOTE]
>  在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]中，工作平行程式庫與 PLINQ 提供 API，可用於多執行序程式中的工作與資料平行處理原則。  如需詳細資訊，請參閱[Parallel Programming](../../../docs/standard/parallel-programming/index.md)。  
  
## 在本節中  
 [Threads and Threading](../../../docs/standard/threading/threads-and-threading.md)  
 討論多執行緒的優缺點，並且簡述可能建立執行緒或使用執行緒集區執行緒的案例。  
  
 [Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 描述在不同版本的 .NET Framework 中，執行緒內未處理之例外狀況的行為，特別是當這些例外狀況會造成應用程式終止時。  
  
 [Synchronizing Data for Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 描述將會使用多執行緒的類別資料之同步處理策略。  
  
 [Managed 執行緒狀態](../../../docs/standard/threading/managed-thread-states.md)  
 描述基本的執行緒狀態，並說明如何偵測執行緒是否正在執行中。  
  
 [Foreground and Background Threads](../../../docs/standard/threading/foreground-and-background-threads.md)  
 說明前景和背景執行緒的差異。  
  
 [Managed and Unmanaged Threading in Windows](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 討論 Managed 和 Unmanaged 執行緒處理的關聯性、列出 Windows 執行緒處理 API 的 Managed 對等用法，並且討論 COM Apartment 和 Managed 執行緒的互動。  
  
 [Thread.Suspend, Garbage Collection, and Safe Points](../../../docs/standard/threading/thread-suspend-garbage-collection-and-safe-points.md)  
 描述執行緒暫止和記憶體回收。  
  
 [Thread Local Storage: Thread\-Relative Static Fields and Data Slots](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 描述與執行緒相關的儲存機制。  
  
 [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md)  
 描述如何使用取消語彙基元移除非同步或長時間同步作業。  
  
## 參考  
 <xref:System.Threading.Thread>  
 提供 **Thread** 類別的參考文件，此類別表示 Managed 執行緒，不論是否來自於 Unmanaged 程式碼，或是否在 Managed 應用程式中建立。  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 提供一個安全的方式將多執行緒處理結合使用者介面物件一起實作。  
  
## 相關章節  
 [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 描述用來同步處理多執行緒之活動的 Managed 類別。  
  
 [Managed Threading Best Practices](../../../docs/standard/threading/managed-threading-best-practices.md)  
 描述多執行緒處理的常見問題，以及避免這些問題的策略。  
  
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)  
 說明工作平行程式庫與 PLINQ，這兩者能夠大幅簡化建立非同步與多執行緒 .NET Framework 應用程式的工作。