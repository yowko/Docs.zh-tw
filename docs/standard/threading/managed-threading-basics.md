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
# <a name="managed-threading-basics"></a><span data-ttu-id="b7754-103">受控執行緒處理的基本概念</span><span class="sxs-lookup"><span data-stu-id="b7754-103">Managed threading basics</span></span>

<span data-ttu-id="b7754-104">本節的前五個主題專門設計來協助您判斷何時使用受控執行緒處理，並說明一些基本功能。</span><span class="sxs-lookup"><span data-stu-id="b7754-104">The first five topics of this section are designed to help you determine when to use managed threading and to explain some basic features.</span></span> <span data-ttu-id="b7754-105">如需提供額外功能的類別相關資訊，請參閱[執行緒物件和功能](threading-objects-and-features.md)及[同步處理原始物件概觀](overview-of-synchronization-primitives.md)。</span><span class="sxs-lookup"><span data-stu-id="b7754-105">For information on classes that provide additional features, see [Threading Objects and Features](threading-objects-and-features.md) and [Overview of Synchronization Primitives](overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="b7754-106">本節的其餘主題將涵蓋進階主題，包括受控執行緒與 Windows 作業系統的互動。</span><span class="sxs-lookup"><span data-stu-id="b7754-106">The rest of the topics in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b7754-107">在 .NET Framework 4 中，工作平行程式庫和 PLINQ 提供適用於多執行緒程式中工作和資料平行處理原則的 API。</span><span class="sxs-lookup"><span data-stu-id="b7754-107">In the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="b7754-108">如需詳細資訊，請參閱[平行程式設計](../parallel-programming/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b7754-108">For more information, see [Parallel Programming](../parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b7754-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="b7754-109">In this section</span></span>

 [<span data-ttu-id="b7754-110">執行緒和執行緒處理</span><span class="sxs-lookup"><span data-stu-id="b7754-110">Threads and Threading</span></span>](threads-and-threading.md)  
 <span data-ttu-id="b7754-111">討論多個執行緒的優點和缺點，並概述您可能會建立執行緒或使用集區執行緒的案例。</span><span class="sxs-lookup"><span data-stu-id="b7754-111">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="b7754-112">Managed 執行緒中的例外狀況</span><span class="sxs-lookup"><span data-stu-id="b7754-112">Exceptions in Managed Threads</span></span>](exceptions-in-managed-threads.md)  
 <span data-ttu-id="b7754-113">描述適用於不同 .NET Framework 版本之未處理例外狀況的行為，特別是它們會導致應用程式終止的情況。</span><span class="sxs-lookup"><span data-stu-id="b7754-113">Describes the behavior of unhandled exceptions in threads for different versions of the .NET Framework, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="b7754-114">同步處理多執行緒的資料</span><span class="sxs-lookup"><span data-stu-id="b7754-114">Synchronizing Data for Multithreading</span></span>](synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="b7754-115">描述用來同步處理將與多個執行緒搭配使用之類別中的資料的策略。</span><span class="sxs-lookup"><span data-stu-id="b7754-115">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="b7754-116">前景和背景執行緒</span><span class="sxs-lookup"><span data-stu-id="b7754-116">Foreground and Background Threads</span></span>](foreground-and-background-threads.md)  
 <span data-ttu-id="b7754-117">說明前景和背景執行緒之間的差異。</span><span class="sxs-lookup"><span data-stu-id="b7754-117">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="b7754-118">Windows 中的 Managed 和 Unmanaged 執行緒處理</span><span class="sxs-lookup"><span data-stu-id="b7754-118">Managed and Unmanaged Threading in Windows</span></span>](managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="b7754-119">討論受控和非受控執行緒之間的關聯性、針對 Windows 執行緒 API 列出受控對等項目，並討論 COM Apartment 和受控執行緒的互動。</span><span class="sxs-lookup"><span data-stu-id="b7754-119">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="b7754-120">執行緒區域儲存區：執行緒相關的靜態欄位和資料位置</span><span class="sxs-lookup"><span data-stu-id="b7754-120">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="b7754-121">描述執行緒相關的儲存機制。</span><span class="sxs-lookup"><span data-stu-id="b7754-121">Describes thread-relative storage mechanisms.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b7754-122">參考</span><span class="sxs-lookup"><span data-stu-id="b7754-122">Reference</span></span>

 <xref:System.Threading.Thread>  
 <span data-ttu-id="b7754-123">提供 **Thread** 類別的參考文件，不論這個類別是來自 Unmanaged 程式碼或是在 Managed 應用程式中建立，都會代表 Managed 執行緒。</span><span class="sxs-lookup"><span data-stu-id="b7754-123">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="b7754-124">提供一個安全方式，搭配使用者介面物件來實作多執行緒。</span><span class="sxs-lookup"><span data-stu-id="b7754-124">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b7754-125">相關章節</span><span class="sxs-lookup"><span data-stu-id="b7754-125">Related sections</span></span>

 [<span data-ttu-id="b7754-126">同步處理基本專案的總覽</span><span class="sxs-lookup"><span data-stu-id="b7754-126">Overview of Synchronization Primitives</span></span>](overview-of-synchronization-primitives.md)  
 <span data-ttu-id="b7754-127">描述用來同步處理多個執行緒活動的受控類別。</span><span class="sxs-lookup"><span data-stu-id="b7754-127">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="b7754-128">受控執行緒最佳做法</span><span class="sxs-lookup"><span data-stu-id="b7754-128">Managed Threading Best Practices</span></span>](managed-threading-best-practices.md)  
 <span data-ttu-id="b7754-129">描述使用多執行緒的常見問題以及避免發生問題的策略。</span><span class="sxs-lookup"><span data-stu-id="b7754-129">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="b7754-130">平行程式設計</span><span class="sxs-lookup"><span data-stu-id="b7754-130">Parallel Programming</span></span>](../parallel-programming/index.md)  
 <span data-ttu-id="b7754-131">描述工作平行程式庫和 PLINQ，其可大幅簡化建立非同步和多執行緒 .NET Framework 應用程式的工作。</span><span class="sxs-lookup"><span data-stu-id="b7754-131">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET Framework applications.</span></span>
