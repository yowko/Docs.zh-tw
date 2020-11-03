---
title: Managed 執行緒處理的基本概念
description: 請參閱其他 managed 執行緒文章的連結，其中涵蓋例外狀況、同步處理資料、前景 & 背景執行緒、本機儲存空間等主題。
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET], multiple threads
- threading [.NET], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
ms.openlocfilehash: ca3073cca9887265b4bacb4f8dfeb01203f82621
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2020
ms.locfileid: "93189130"
---
# <a name="managed-threading-basics"></a><span data-ttu-id="e3d87-103">受控執行緒處理的基本概念</span><span class="sxs-lookup"><span data-stu-id="e3d87-103">Managed threading basics</span></span>

<span data-ttu-id="e3d87-104">本節的前五篇文章是設計來協助您判斷何時使用 managed 執行緒，並說明一些基本功能。</span><span class="sxs-lookup"><span data-stu-id="e3d87-104">The first five articles of this section are designed to help you determine when to use managed threading and to explain some basic features.</span></span> <span data-ttu-id="e3d87-105">如需提供額外功能的類別相關資訊，請參閱[執行緒物件和功能](threading-objects-and-features.md)及[同步處理原始物件概觀](overview-of-synchronization-primitives.md)。</span><span class="sxs-lookup"><span data-stu-id="e3d87-105">For information on classes that provide additional features, see [Threading Objects and Features](threading-objects-and-features.md) and [Overview of Synchronization Primitives](overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="e3d87-106">本節中的其餘文章涵蓋了 advanced 主題，包括 managed 執行緒與 Windows 作業系統的互動。</span><span class="sxs-lookup"><span data-stu-id="e3d87-106">The remaining articles in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e3d87-107">從 .NET Framework 4 開始，工作平行程式庫和 PLINQ 會在多執行緒程式中提供工作和資料平行處理原則的 Api。</span><span class="sxs-lookup"><span data-stu-id="e3d87-107">Starting with .NET Framework 4, the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="e3d87-108">如需詳細資訊，請參閱 [平行程式設計](../parallel-programming/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e3d87-108">For more information, see [Parallel Programming](../parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e3d87-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="e3d87-109">In this section</span></span>

 [<span data-ttu-id="e3d87-110">執行緒和執行緒處理</span><span class="sxs-lookup"><span data-stu-id="e3d87-110">Threads and Threading</span></span>](threads-and-threading.md)  
 <span data-ttu-id="e3d87-111">討論多個執行緒的優點和缺點，並概述您可能會建立執行緒或使用集區執行緒的案例。</span><span class="sxs-lookup"><span data-stu-id="e3d87-111">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="e3d87-112">Managed 執行緒中的例外狀況</span><span class="sxs-lookup"><span data-stu-id="e3d87-112">Exceptions in Managed Threads</span></span>](exceptions-in-managed-threads.md)  
 <span data-ttu-id="e3d87-113">描述不同 .NET 版本之執行緒中未處理例外狀況的行為，尤其是它們會導致應用程式終止的情況。</span><span class="sxs-lookup"><span data-stu-id="e3d87-113">Describes the behavior of unhandled exceptions in threads for different versions of .NET, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="e3d87-114">同步處理多執行緒處理的資料</span><span class="sxs-lookup"><span data-stu-id="e3d87-114">Synchronizing Data for Multithreading</span></span>](synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="e3d87-115">描述用來同步處理將與多個執行緒搭配使用之類別中的資料的策略。</span><span class="sxs-lookup"><span data-stu-id="e3d87-115">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="e3d87-116">前景和背景執行緒</span><span class="sxs-lookup"><span data-stu-id="e3d87-116">Foreground and Background Threads</span></span>](foreground-and-background-threads.md)  
 <span data-ttu-id="e3d87-117">說明前景和背景執行緒之間的差異。</span><span class="sxs-lookup"><span data-stu-id="e3d87-117">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="e3d87-118">Windows 中的 Managed 和 Unmanaged 執行緒處理</span><span class="sxs-lookup"><span data-stu-id="e3d87-118">Managed and Unmanaged Threading in Windows</span></span>](managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="e3d87-119">討論受控和非受控執行緒之間的關聯性、針對 Windows 執行緒 API 列出受控對等項目，並討論 COM Apartment 和受控執行緒的互動。</span><span class="sxs-lookup"><span data-stu-id="e3d87-119">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="e3d87-120">執行緒區域儲存區：執行緒相關的靜態欄位和資料位置</span><span class="sxs-lookup"><span data-stu-id="e3d87-120">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="e3d87-121">描述執行緒相關的儲存機制。</span><span class="sxs-lookup"><span data-stu-id="e3d87-121">Describes thread-relative storage mechanisms.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e3d87-122">參考</span><span class="sxs-lookup"><span data-stu-id="e3d87-122">Reference</span></span>

 <xref:System.Threading.Thread>  
 <span data-ttu-id="e3d87-123">提供 **Thread** 類別的參考文件，不論這個類別是來自 Unmanaged 程式碼或是在 Managed 應用程式中建立，都會代表 Managed 執行緒。</span><span class="sxs-lookup"><span data-stu-id="e3d87-123">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="e3d87-124">提供一個安全方式，搭配使用者介面物件來實作多執行緒。</span><span class="sxs-lookup"><span data-stu-id="e3d87-124">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e3d87-125">相關章節</span><span class="sxs-lookup"><span data-stu-id="e3d87-125">Related sections</span></span>

 [<span data-ttu-id="e3d87-126">同步處理原始物件總覽</span><span class="sxs-lookup"><span data-stu-id="e3d87-126">Overview of Synchronization Primitives</span></span>](overview-of-synchronization-primitives.md)  
 <span data-ttu-id="e3d87-127">描述用來同步處理多個執行緒活動的受控類別。</span><span class="sxs-lookup"><span data-stu-id="e3d87-127">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="e3d87-128">Managed 執行緒處理的最佳實施方針</span><span class="sxs-lookup"><span data-stu-id="e3d87-128">Managed Threading Best Practices</span></span>](managed-threading-best-practices.md)  
 <span data-ttu-id="e3d87-129">描述使用多執行緒的常見問題以及避免發生問題的策略。</span><span class="sxs-lookup"><span data-stu-id="e3d87-129">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="e3d87-130">平行程式設計</span><span class="sxs-lookup"><span data-stu-id="e3d87-130">Parallel Programming</span></span>](../parallel-programming/index.md)  
 <span data-ttu-id="e3d87-131">描述工作平行程式庫和 PLINQ，可大幅簡化建立異步和多執行緒 .NET 應用程式的工作。</span><span class="sxs-lookup"><span data-stu-id="e3d87-131">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET applications.</span></span>
