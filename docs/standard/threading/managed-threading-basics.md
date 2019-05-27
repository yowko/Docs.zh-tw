---
title: Managed 執行緒處理的基本概念
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7241dfb7e31ed2f83bf7af0ecc6bf0d97363b999
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960367"
---
# <a name="managed-threading-basics"></a>受控執行緒處理的基本概念

本節的前五個主題專門設計來協助您判斷何時使用受控執行緒處理，並說明一些基本功能。 如需提供額外功能的類別相關資訊，請參閱[執行緒物件和功能](../../../docs/standard/threading/threading-objects-and-features.md)及[同步處理原始物件概觀](../../../docs/standard/threading/overview-of-synchronization-primitives.md)。  
  
 本節的其餘主題將涵蓋進階主題，包括受控執行緒與 Windows 作業系統的互動。  
  
> [!NOTE]
>  在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 中，工作平行程式庫和 PLINQ 提供適用於多執行緒程式中工作和資料平行處理原則的 API。 如需詳細資訊，請參閱[平行程式設計](../../../docs/standard/parallel-programming/index.md)。  
  
## <a name="in-this-section"></a>本節內容

 [執行緒和執行緒處理](../../../docs/standard/threading/threads-and-threading.md)  
 討論多個執行緒的優點和缺點，並概述您可能會建立執行緒或使用集區執行緒的案例。  
  
 [Managed 執行緒中的例外狀況](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 描述適用於不同 .NET Framework 版本之未處理例外狀況的行為，特別是它們會導致應用程式終止的情況。  
  
 [同步處理多執行緒處理的資料](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 描述用來同步處理將與多個執行緒搭配使用之類別中的資料的策略。  
  
 [前景和背景執行緒](../../../docs/standard/threading/foreground-and-background-threads.md)  
 說明前景和背景執行緒之間的差異。  
  
 [Windows 中的 Managed 和 Unmanaged 執行緒處理](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 討論受控和非受控執行緒之間的關聯性、針對 Windows 執行緒 API 列出受控對等項目，並討論 COM Apartment 和受控執行緒的互動。  
  
 [執行緒本機儲存體：執行緒相關靜態欄位和資料插槽](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 描述執行緒相關的儲存機制。  
  
## <a name="reference"></a>參考資料

 <xref:System.Threading.Thread>  
 提供 **Thread** 類別的參考文件，不論這個類別是來自 Unmanaged 程式碼或是在 Managed 應用程式中建立，都會代表 Managed 執行緒。  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 提供一個安全方式，搭配使用者介面物件來實作多執行緒。  
  
## <a name="related-sections"></a>相關章節

 [同步處理原始物件概觀](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 描述用來同步處理多個執行緒活動的受控類別。  
  
 [Managed 執行緒處理的最佳實施方針](../../../docs/standard/threading/managed-threading-best-practices.md)  
 描述使用多執行緒的常見問題以及避免發生問題的策略。  
  
 [平行程式設計](../../../docs/standard/parallel-programming/index.md)  
 描述工作平行程式庫和 PLINQ，其可大幅簡化建立非同步和多執行緒 .NET Framework 應用程式的工作。
