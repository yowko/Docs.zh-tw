---
title: Managed 執行緒處理的基本概念
description: 請參閱其他 managed 執行緒文章的連結，包括例外狀況、同步處理資料、前景 & 背景執行緒、本機儲存空間等主題。
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
ms.openlocfilehash: d4a4ceabf29bd0f6f537e59ba477f9da686b1ef5
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769089"
---
# <a name="managed-threading-basics"></a>受控執行緒處理的基本概念

本節的前五個主題專門設計來協助您判斷何時使用受控執行緒處理，並說明一些基本功能。 如需提供額外功能的類別相關資訊，請參閱[執行緒物件和功能](threading-objects-and-features.md)及[同步處理原始物件概觀](overview-of-synchronization-primitives.md)。  
  
 本節的其餘主題將涵蓋進階主題，包括受控執行緒與 Windows 作業系統的互動。  
  
> [!NOTE]
> 在 .NET Framework 4 中，工作平行程式庫和 PLINQ 提供適用於多執行緒程式中工作和資料平行處理原則的 API。 如需詳細資訊，請參閱[平行程式設計](../parallel-programming/index.md)。  
  
## <a name="in-this-section"></a>本節內容

 [執行緒和執行緒處理](threads-and-threading.md)  
 討論多個執行緒的優點和缺點，並概述您可能會建立執行緒或使用集區執行緒的案例。  
  
 [Managed 執行緒中的例外狀況](exceptions-in-managed-threads.md)  
 描述適用於不同 .NET Framework 版本之未處理例外狀況的行為，特別是它們會導致應用程式終止的情況。  
  
 [同步處理多執行緒的資料](synchronizing-data-for-multithreading.md)  
 描述用來同步處理將與多個執行緒搭配使用之類別中的資料的策略。  
  
 [前景和背景執行緒](foreground-and-background-threads.md)  
 說明前景和背景執行緒之間的差異。  
  
 [Windows 中的 Managed 和 Unmanaged 執行緒處理](managed-and-unmanaged-threading-in-windows.md)  
 討論受控和非受控執行緒之間的關聯性、針對 Windows 執行緒 API 列出受控對等項目，並討論 COM Apartment 和受控執行緒的互動。  
  
 [執行緒區域儲存區：執行緒相關的靜態欄位和資料位置](thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 描述執行緒相關的儲存機制。  
  
## <a name="reference"></a>參考

 <xref:System.Threading.Thread>  
 提供 **Thread** 類別的參考文件，不論這個類別是來自 Unmanaged 程式碼或是在 Managed 應用程式中建立，都會代表 Managed 執行緒。  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 提供一個安全方式，搭配使用者介面物件來實作多執行緒。  
  
## <a name="related-sections"></a>相關章節

 [同步處理基本專案的總覽](overview-of-synchronization-primitives.md)  
 描述用來同步處理多個執行緒活動的受控類別。  
  
 [受控執行緒最佳做法](managed-threading-best-practices.md)  
 描述使用多執行緒的常見問題以及避免發生問題的策略。  
  
 [平行程式設計](../parallel-programming/index.md)  
 描述工作平行程式庫和 PLINQ，其可大幅簡化建立非同步和多執行緒 .NET Framework 應用程式的工作。
