---
title: Managed 執行緒處理
description: 請參閱 .NET 中 managed 執行緒的連結，其中涵蓋了基本概念、最佳作法、執行緒物件 & 功能、參考頁面 & 更多專案。
ms.date: 03/30/2017
helpviewer_keywords:
- threading [.NET], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
ms.openlocfilehash: 28ba05c345d22b14512d280f3855934d727b3142
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728442"
---
# <a name="managed-threading"></a><span data-ttu-id="e21e3-103">受控執行緒</span><span class="sxs-lookup"><span data-stu-id="e21e3-103">Managed threading</span></span>

<span data-ttu-id="e21e3-104">無論您是針對具有一個或多個處理器的電腦進行開發，您都想要讓應用程式能夠提供與使用者的最快速回應，即使應用程式目前正在執行其他工作也是一樣。</span><span class="sxs-lookup"><span data-stu-id="e21e3-104">Whether you're developing for computers with one processor or several, you want your application to provide the most responsive interaction with the user, even if the application is currently doing other work.</span></span> <span data-ttu-id="e21e3-105">使用多執行緒的執行是一種讓應用程式能迅速回應使用者，同時能夠在使用者事件之間或甚至在使用者事件當中善用處理器的強大方法。</span><span class="sxs-lookup"><span data-stu-id="e21e3-105">Using multiple threads of execution is one of the most powerful ways to keep your application responsive to the user and at the same time make use of the processor in between or even during user events.</span></span> <span data-ttu-id="e21e3-106">雖然本節將介紹執行緒處理的基本概念，但是重點會放在 Managed 執行緒處理概念和如何使用 Managed 執行緒處理。</span><span class="sxs-lookup"><span data-stu-id="e21e3-106">While this section introduces the basic concepts of threading, it focuses on managed threading concepts and using managed threading.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e21e3-107">從 .NET Framework 4 開始，多執行緒程式設計已透過 <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> 和類別大幅簡化 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 、 [平行 LINQ (PLINQ) ](../parallel-programming/introduction-to-plinq.md)、命名空間中的並行集合類別 <xref:System.Collections.Concurrent?displayProperty=nameWithType> ，以及以工作（而非執行緒）概念為基礎的程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="e21e3-107">Starting with .NET Framework 4, multithreaded programming is greatly simplified with the <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> classes, [Parallel LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md), concurrent collection classes in the <xref:System.Collections.Concurrent?displayProperty=nameWithType> namespace, and a programming model that is based on the concept of tasks rather than threads.</span></span> <span data-ttu-id="e21e3-108">如需詳細資訊，請參閱 [平行程式設計](../parallel-programming/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e21e3-108">For more information, see [Parallel Programming](../parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e21e3-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="e21e3-109">In This Section</span></span>  

 [<span data-ttu-id="e21e3-110">Managed 執行緒處理的基本概念</span><span class="sxs-lookup"><span data-stu-id="e21e3-110">Managed Threading Basics</span></span>](managed-threading-basics.md)  
 <span data-ttu-id="e21e3-111">提供 Managed 執行緒處理的概觀，並討論何時使用多個執行緒。</span><span class="sxs-lookup"><span data-stu-id="e21e3-111">Provides an overview of managed threading and discusses when to use multiple threads.</span></span>  
  
 [<span data-ttu-id="e21e3-112">使用執行緒和執行緒</span><span class="sxs-lookup"><span data-stu-id="e21e3-112">Using Threads and Threading</span></span>](using-threads-and-threading.md)  
 <span data-ttu-id="e21e3-113">說明如何建立、啟動、暫停、繼續和中止執行緒。</span><span class="sxs-lookup"><span data-stu-id="e21e3-113">Explains how to create, start, pause, resume, and abort threads.</span></span>  
  
 [<span data-ttu-id="e21e3-114">Managed 執行緒處理的最佳實施方針</span><span class="sxs-lookup"><span data-stu-id="e21e3-114">Managed Threading Best Practices</span></span>](managed-threading-best-practices.md)  
 <span data-ttu-id="e21e3-115">討論同步處理的層級、如何避免死結和競爭條件，以及其他執行緒處理問題。</span><span class="sxs-lookup"><span data-stu-id="e21e3-115">Discusses levels of synchronization, how to avoid deadlocks and race conditions, and other threading issues.</span></span>  
  
 [<span data-ttu-id="e21e3-116">執行緒物件和功能</span><span class="sxs-lookup"><span data-stu-id="e21e3-116">Threading Objects and Features</span></span>](threading-objects-and-features.md)  
 <span data-ttu-id="e21e3-117">描述可用來同步執行緒活動的 Managed 類別，以及在不同執行緒上存取的物件資料，並提供執行緒集區執行緒的概觀。</span><span class="sxs-lookup"><span data-stu-id="e21e3-117">Describes the managed classes you can use to synchronize the activities of threads and the data of objects accessed on different threads, and provides an overview of thread pool threads.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e21e3-118">參考</span><span class="sxs-lookup"><span data-stu-id="e21e3-118">Reference</span></span>  

 <xref:System.Threading>  
 <span data-ttu-id="e21e3-119">包含使用和同步 Managed 執行緒的類別。</span><span class="sxs-lookup"><span data-stu-id="e21e3-119">Contains classes for using and synchronizing managed threads.</span></span>  
  
 <xref:System.Collections.Concurrent>  
 <span data-ttu-id="e21e3-120">包含可安全用於多個執行緒的集合類別。</span><span class="sxs-lookup"><span data-stu-id="e21e3-120">Contains collection classes that are safe for use with multiple threads.</span></span>  
  
 <xref:System.Threading.Tasks>  
 <span data-ttu-id="e21e3-121">包含建立和排程並行處理工作的類別。</span><span class="sxs-lookup"><span data-stu-id="e21e3-121">Contains classes for creating and scheduling concurrent processing tasks.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e21e3-122">相關章節</span><span class="sxs-lookup"><span data-stu-id="e21e3-122">Related Sections</span></span>  

 [<span data-ttu-id="e21e3-123">應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="e21e3-123">Application Domains</span></span>](../../framework/app-domains/application-domains.md)  
 <span data-ttu-id="e21e3-124">提供應用程式定義域的概觀及通用語言基礎結構如何使用它們。</span><span class="sxs-lookup"><span data-stu-id="e21e3-124">Provides an overview of application domains and their use by the Common Language Infrastructure.</span></span>  
  
 [<span data-ttu-id="e21e3-125">非同步檔案 i/o</span><span class="sxs-lookup"><span data-stu-id="e21e3-125">Asynchronous File I/O</span></span>](../io/asynchronous-file-i-o.md)  
 <span data-ttu-id="e21e3-126">描述非同步 I/O 的效能利益和基本作業。</span><span class="sxs-lookup"><span data-stu-id="e21e3-126">Describes the performance advantages and basic operation of asynchronous I/O.</span></span>  
  
 [<span data-ttu-id="e21e3-127">以工作為基礎的非同步模式 (TAP)</span><span class="sxs-lookup"><span data-stu-id="e21e3-127">Task-based Asynchronous Pattern (TAP)</span></span>](../asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 <span data-ttu-id="e21e3-128">提供 .NET 中非同步程式設計建議模式的概觀。</span><span class="sxs-lookup"><span data-stu-id="e21e3-128">Provides an overview of the recommended pattern for asynchronous programming in .NET.</span></span>  
  
 [<span data-ttu-id="e21e3-129">以非同步的方式呼叫同步方法</span><span class="sxs-lookup"><span data-stu-id="e21e3-129">Calling Synchronous Methods Asynchronously</span></span>](../asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="e21e3-130">說明如何使用內建的委派功能在執行緒集區執行緒上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="e21e3-130">Explains how to call methods on thread pool threads using built-in features of delegates.</span></span>  
  
 [<span data-ttu-id="e21e3-131">平行程式設計</span><span class="sxs-lookup"><span data-stu-id="e21e3-131">Parallel Programming</span></span>](../parallel-programming/index.md)  
 <span data-ttu-id="e21e3-132">描述平行程式設計程式庫，簡化應用程式中多個執行緒的用法。</span><span class="sxs-lookup"><span data-stu-id="e21e3-132">Describes the parallel programming libraries, which simplify the use of multiple threads in applications.</span></span>  
  
 [<span data-ttu-id="e21e3-133">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="e21e3-133">Parallel LINQ (PLINQ)</span></span>](../parallel-programming/introduction-to-plinq.md)  
 <span data-ttu-id="e21e3-134">描述以平行方式執行查詢的系統，以善用多個處理器。</span><span class="sxs-lookup"><span data-stu-id="e21e3-134">Describes a system for running queries in parallel, to take advantage of multiple processors.</span></span>
