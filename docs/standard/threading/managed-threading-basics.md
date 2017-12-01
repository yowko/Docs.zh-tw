---
title: "Managed 執行緒處理的基本概念"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 62c207f6074e33813887c6903f5285ee72d14e85
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="managed-threading-basics"></a>Managed 執行緒處理的基本概念
本章節的前五個主題專門設計來協助您判斷何時使用 managed 執行緒處理，並說明一些基本功能。 提供的額外功能的類別上的資訊，請參閱[執行緒處理物件和功能](../../../docs/standard/threading/threading-objects-and-features.md)和[同步處理原始物件概觀](../../../docs/standard/threading/overview-of-synchronization-primitives.md)。  
  
 此章節涵蓋的主題的其餘部分進階主題，包括 Windows 作業系統的 managed 執行緒的互動。  
  
> [!NOTE]
>  在[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]，工作平行程式庫和 PLINQ 提供應用程式開發介面在多執行緒程式中的工作和資料平行處理原則。 如需詳細資訊，請參閱[平行程式設計](../../../docs/standard/parallel-programming/index.md)。  
  
## <a name="in-this-section"></a>本章節內容  
 [執行緒和執行緒處理](../../../docs/standard/threading/threads-and-threading.md)  
 討論的優點和缺點的多個執行緒，並簡述的案例，您可能會建立執行緒，或使用執行緒集區。  
  
 [Managed 執行緒中的例外狀況](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 描述特別的情況下針對不同版本的.NET Framework 中，執行緒中的未處理例外狀況的行為在它們會在應用程式終止。  
  
 [同步處理多執行緒處理的資料](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 描述在將用於多個執行緒的類別中的資料同步處理的策略。  
  
 [Managed 執行緒狀態](../../../docs/standard/threading/managed-thread-states.md)  
 描述基本的執行緒狀態，並說明如何偵測是否正在執行一個執行緒。  
  
 [前景和背景執行緒](../../../docs/standard/threading/foreground-and-background-threads.md)  
 說明前景和背景執行緒之間的差異。  
  
 [Windows 中的 Managed 和 Unmanaged 執行緒處理](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 討論 managed 和 unmanaged 執行緒之間的關聯性、 列出受管理的對等項目適用於 Windows 執行緒應用程式開發介面，並討論的 COM apartment 和 managed 的執行緒的互動。  
  
 [Thread.Suspend、記憶體回收和安全點](../../../docs/standard/threading/thread-suspend-garbage-collection-and-safe-points.md)  
 描述執行緒暫止和記憶體回收集合。  
  
 [執行緒區域儲存區：執行緒相關的靜態欄位和資料位置](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 描述執行緒相關的儲存機制。  
  
 [Managed 執行緒中的取消作業](../../../docs/standard/threading/cancellation-in-managed-threads.md)  
 描述如何非同步或長時間執行的同步作業可以使用取消語彙基元已取消。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Threading.Thread>  
 提供 **Thread** 類別的參考文件，不論這個類別是來自 Unmanaged 程式碼或是在 Managed 應用程式中建立，都會代表 Managed 執行緒。  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 提供安全的方式來實作多執行緒處理與使用者介面物件一起使用。  
  
## <a name="related-sections"></a>相關章節  
 [同步處理原始物件概觀](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 描述 managed 的類別，用來同步處理多個執行緒的活動。  
  
 [Managed 執行緒處理的最佳實施方針](../../../docs/standard/threading/managed-threading-best-practices.md)  
 描述常見的問題，使用多執行緒及避免發生問題的策略。  
  
 [平行程式設計](../../../docs/standard/parallel-programming/index.md)  
 描述工作平行程式庫和 PLINQ，可大幅簡化建立非同步處理和多執行緒的.NET Framework 應用程式的工作。
