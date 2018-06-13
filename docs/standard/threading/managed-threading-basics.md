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
ms.openlocfilehash: 5fa91bb22de6492815f79bfd50e1fefc800c6047
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586509"
---
# <a name="managed-threading-basics"></a><span data-ttu-id="9b5c8-102">Managed 執行緒處理的基本概念</span><span class="sxs-lookup"><span data-stu-id="9b5c8-102">Managed Threading Basics</span></span>
<span data-ttu-id="9b5c8-103">本節的前五個主題專門設計來協助您判斷何時使用受控執行緒處理，並說明一些基本功能。</span><span class="sxs-lookup"><span data-stu-id="9b5c8-103">The first five topics of this section are designed to help you determine when to use managed threading, and to explain some basic features.</span></span> <span data-ttu-id="9b5c8-104">如需提供額外功能的類別相關資訊，請參閱[執行緒物件和功能](../../../docs/standard/threading/threading-objects-and-features.md)及[同步處理原始物件概觀](../../../docs/standard/threading/overview-of-synchronization-primitives.md)。</span><span class="sxs-lookup"><span data-stu-id="9b5c8-104">For information on classes that provide additional features, see [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md) and [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="9b5c8-105">本節的其餘主題將涵蓋進階主題，包括受控執行緒與 Windows 作業系統的互動。</span><span class="sxs-lookup"><span data-stu-id="9b5c8-105">The rest of the topics in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b5c8-106">在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 中，工作平行程式庫和 PLINQ 提供適用於多執行緒程式中工作和資料平行處理原則的 API。</span><span class="sxs-lookup"><span data-stu-id="9b5c8-106">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="9b5c8-107">如需詳細資訊，請參閱[平行程式設計](../../../docs/standard/parallel-programming/index.md)。</span><span class="sxs-lookup"><span data-stu-id="9b5c8-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9b5c8-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="9b5c8-108">In This Section</span></span>  
 [<span data-ttu-id="9b5c8-109">執行緒和執行緒處理</span><span class="sxs-lookup"><span data-stu-id="9b5c8-109">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 <span data-ttu-id="9b5c8-110">討論多個執行緒的優點和缺點，並概述您可能會建立執行緒或使用集區執行緒的案例。</span><span class="sxs-lookup"><span data-stu-id="9b5c8-110">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="9b5c8-111">Managed 執行緒中的例外狀況</span><span class="sxs-lookup"><span data-stu-id="9b5c8-111">Exceptions in Managed Threads</span></span>](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 <span data-ttu-id="9b5c8-112">描述適用於不同 .NET Framework 版本之未處理例外狀況的行為，特別是它們會導致應用程式終止的情況。</span><span class="sxs-lookup"><span data-stu-id="9b5c8-112">Describes the behavior of unhandled exceptions in threads for different versions of the .NET Framework, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="9b5c8-113">同步處理多執行緒處理的資料</span><span class="sxs-lookup"><span data-stu-id="9b5c8-113">Synchronizing Data for Multithreading</span></span>](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="9b5c8-114">描述用來同步處理將與多個執行緒搭配使用之類別中的資料的策略。</span><span class="sxs-lookup"><span data-stu-id="9b5c8-114">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="9b5c8-115">Managed 執行緒狀態</span><span class="sxs-lookup"><span data-stu-id="9b5c8-115">Managed Thread States</span></span>](../../../docs/standard/threading/managed-thread-states.md)  
 <span data-ttu-id="9b5c8-116">描述基本執行緒狀態，並說明如何偵測執行緒是否正在執行。</span><span class="sxs-lookup"><span data-stu-id="9b5c8-116">Describes the basic thread states, and explains how to detect whether a thread is running.</span></span>  
  
 [<span data-ttu-id="9b5c8-117">前景和背景執行緒</span><span class="sxs-lookup"><span data-stu-id="9b5c8-117">Foreground and Background Threads</span></span>](../../../docs/standard/threading/foreground-and-background-threads.md)  
 <span data-ttu-id="9b5c8-118">說明前景和背景執行緒之間的差異。</span><span class="sxs-lookup"><span data-stu-id="9b5c8-118">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="9b5c8-119">Windows 中的 Managed 和 Unmanaged 執行緒處理</span><span class="sxs-lookup"><span data-stu-id="9b5c8-119">Managed and Unmanaged Threading in Windows</span></span>](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="9b5c8-120">討論受控和非受控執行緒之間的關聯性、針對 Windows 執行緒 API 列出受控對等項目，並討論 COM Apartment 和受控執行緒的互動。</span><span class="sxs-lookup"><span data-stu-id="9b5c8-120">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="9b5c8-121">Thread.Suspend、記憶體回收和安全點</span><span class="sxs-lookup"><span data-stu-id="9b5c8-121">Thread.Suspend, Garbage Collection, and Safe Points</span></span>](../../../docs/standard/threading/thread-suspend-garbage-collection-and-safe-points.md)  
 <span data-ttu-id="9b5c8-122">描述執行緒暫止和記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="9b5c8-122">Describes thread suspension and garbage collection.</span></span>  
  
 [<span data-ttu-id="9b5c8-123">執行緒區域儲存區：執行緒相關的靜態欄位和資料位置</span><span class="sxs-lookup"><span data-stu-id="9b5c8-123">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="9b5c8-124">描述執行緒相關的儲存機制。</span><span class="sxs-lookup"><span data-stu-id="9b5c8-124">Describes thread-relative storage mechanisms.</span></span>  
  
 [<span data-ttu-id="9b5c8-125">Managed 執行緒中的取消作業</span><span class="sxs-lookup"><span data-stu-id="9b5c8-125">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)  
 <span data-ttu-id="9b5c8-126">描述如何使用取消語彙基元來取消非同步或長時間執行的同步作業。</span><span class="sxs-lookup"><span data-stu-id="9b5c8-126">Describes how asynchronous or long-running synchronous operations can be canceled by using a cancellation token.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9b5c8-127">參考資料</span><span class="sxs-lookup"><span data-stu-id="9b5c8-127">Reference</span></span>  
 <xref:System.Threading.Thread>  
 <span data-ttu-id="9b5c8-128">提供 **Thread** 類別的參考文件，不論這個類別是來自 Unmanaged 程式碼或是在 Managed 應用程式中建立，都會代表 Managed 執行緒。</span><span class="sxs-lookup"><span data-stu-id="9b5c8-128">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="9b5c8-129">提供一個安全方式，搭配使用者介面物件來實作多執行緒。</span><span class="sxs-lookup"><span data-stu-id="9b5c8-129">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9b5c8-130">相關章節</span><span class="sxs-lookup"><span data-stu-id="9b5c8-130">Related Sections</span></span>  
 [<span data-ttu-id="9b5c8-131">同步處理原始物件概觀</span><span class="sxs-lookup"><span data-stu-id="9b5c8-131">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 <span data-ttu-id="9b5c8-132">描述用來同步處理多個執行緒活動的受控類別。</span><span class="sxs-lookup"><span data-stu-id="9b5c8-132">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="9b5c8-133">Managed 執行緒處理的最佳實施方針</span><span class="sxs-lookup"><span data-stu-id="9b5c8-133">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="9b5c8-134">描述使用多執行緒的常見問題以及避免發生問題的策略。</span><span class="sxs-lookup"><span data-stu-id="9b5c8-134">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="9b5c8-135">平行程式設計</span><span class="sxs-lookup"><span data-stu-id="9b5c8-135">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="9b5c8-136">描述工作平行程式庫和 PLINQ，其可大幅簡化建立非同步和多執行緒 .NET Framework 應用程式的工作。</span><span class="sxs-lookup"><span data-stu-id="9b5c8-136">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET Framework applications.</span></span>
