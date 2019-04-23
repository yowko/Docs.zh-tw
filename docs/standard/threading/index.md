---
title: Managed 執行緒處理
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6447cd37e4718093acfb3a0e2db053c13a027d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62015135"
---
# <a name="managed-threading"></a><span data-ttu-id="9a807-102">Managed 執行緒處理</span><span class="sxs-lookup"><span data-stu-id="9a807-102">Managed Threading</span></span>
<span data-ttu-id="9a807-103">不論您開發的是搭載一或多個處理器的電腦，即使應用程式目前正在執行其他工作，您還是希望應用程式能以最快速度與使用者互動。</span><span class="sxs-lookup"><span data-stu-id="9a807-103">Whether you are developing for computers with one processor or several, you want your application to provide the most responsive interaction with the user, even if the application is currently doing other work.</span></span> <span data-ttu-id="9a807-104">使用多執行緒的執行是一種讓應用程式能迅速回應使用者，同時能夠在使用者事件之間或甚至在使用者事件當中善用處理器的強大方法。</span><span class="sxs-lookup"><span data-stu-id="9a807-104">Using multiple threads of execution is one of the most powerful ways to keep your application responsive to the user and at the same time make use of the processor in between or even during user events.</span></span> <span data-ttu-id="9a807-105">雖然本節將介紹執行緒處理的基本概念，但是重點會放在 Managed 執行緒處理概念和如何使用 Managed 執行緒處理。</span><span class="sxs-lookup"><span data-stu-id="9a807-105">While this section introduces the basic concepts of threading, it focuses on managed threading concepts and using managed threading.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a807-106">從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 開始，多執行緒的程式設計已透過 <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 類型、[平行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)、<xref:System.Collections.Concurrent?displayProperty=nameWithType> 命名空間中的新並行集合類別，以及以工作 (而非執行緒) 概念為基礎的新程式設計模型，而做出簡化。</span><span class="sxs-lookup"><span data-stu-id="9a807-106">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], multithreaded programming is greatly simplified with the <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> classes, [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), new concurrent collection classes in the <xref:System.Collections.Concurrent?displayProperty=nameWithType> namespace, and a new programming model that is based on the concept of tasks rather than threads.</span></span> <span data-ttu-id="9a807-107">如需詳細資訊，請參閱[平行程式設計](../../../docs/standard/parallel-programming/index.md)。</span><span class="sxs-lookup"><span data-stu-id="9a807-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9a807-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="9a807-108">In This Section</span></span>  
 [<span data-ttu-id="9a807-109">Managed 執行緒處理的基本概念</span><span class="sxs-lookup"><span data-stu-id="9a807-109">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)  
 <span data-ttu-id="9a807-110">提供 Managed 執行緒處理的概觀，並討論何時使用多個執行緒。</span><span class="sxs-lookup"><span data-stu-id="9a807-110">Provides an overview of managed threading and discusses when to use multiple threads.</span></span>  
  
 [<span data-ttu-id="9a807-111">使用執行緒和執行緒處理</span><span class="sxs-lookup"><span data-stu-id="9a807-111">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 <span data-ttu-id="9a807-112">說明如何建立、啟動、暫停、繼續和中止執行緒。</span><span class="sxs-lookup"><span data-stu-id="9a807-112">Explains how to create, start, pause, resume, and abort threads.</span></span>  
  
 [<span data-ttu-id="9a807-113">Managed 執行緒處理的最佳實施方針</span><span class="sxs-lookup"><span data-stu-id="9a807-113">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="9a807-114">討論同步處理的層級、如何避免死結和競爭條件，以及其他執行緒處理問題。</span><span class="sxs-lookup"><span data-stu-id="9a807-114">Discusses levels of synchronization, how to avoid deadlocks and race conditions, and other threading issues.</span></span>  
  
 [<span data-ttu-id="9a807-115">執行緒物件和功能</span><span class="sxs-lookup"><span data-stu-id="9a807-115">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 <span data-ttu-id="9a807-116">描述可用來同步執行緒活動的 Managed 類別，以及在不同執行緒上存取的物件資料，並提供執行緒集區執行緒的概觀。</span><span class="sxs-lookup"><span data-stu-id="9a807-116">Describes the managed classes you can use to synchronize the activities of threads and the data of objects accessed on different threads, and provides an overview of thread pool threads.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9a807-117">參考資料</span><span class="sxs-lookup"><span data-stu-id="9a807-117">Reference</span></span>  
 <xref:System.Threading>  
 <span data-ttu-id="9a807-118">包含使用和同步 Managed 執行緒的類別。</span><span class="sxs-lookup"><span data-stu-id="9a807-118">Contains classes for using and synchronizing managed threads.</span></span>  
  
 <xref:System.Collections.Concurrent>  
 <span data-ttu-id="9a807-119">包含可安全用於多個執行緒的集合類別。</span><span class="sxs-lookup"><span data-stu-id="9a807-119">Contains collection classes that are safe for use with multiple threads.</span></span>  
  
 <xref:System.Threading.Tasks>  
 <span data-ttu-id="9a807-120">包含建立和排程並行處理工作的類別。</span><span class="sxs-lookup"><span data-stu-id="9a807-120">Contains classes for creating and scheduling concurrent processing tasks.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9a807-121">相關章節</span><span class="sxs-lookup"><span data-stu-id="9a807-121">Related Sections</span></span>  
 [<span data-ttu-id="9a807-122">應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="9a807-122">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="9a807-123">提供應用程式定義域的概觀及通用語言基礎結構如何使用它們。</span><span class="sxs-lookup"><span data-stu-id="9a807-123">Provides an overview of application domains and their use by the Common Language Infrastructure.</span></span>  
  
 [<span data-ttu-id="9a807-124">Asynchronous File I/O</span><span class="sxs-lookup"><span data-stu-id="9a807-124">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 <span data-ttu-id="9a807-125">描述非同步 I/O 的效能利益和基本作業。</span><span class="sxs-lookup"><span data-stu-id="9a807-125">Describes the performance advantages and basic operation of asynchronous I/O.</span></span>  
  
 [<span data-ttu-id="9a807-126">工作式非同步模式 (TAP)</span><span class="sxs-lookup"><span data-stu-id="9a807-126">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 <span data-ttu-id="9a807-127">提供 .NET 中非同步程式設計建議模式的概觀。</span><span class="sxs-lookup"><span data-stu-id="9a807-127">Provides an overview of the recommended pattern for asynchronous programming in .NET.</span></span>  
  
 [<span data-ttu-id="9a807-128">非同步呼叫同步方法</span><span class="sxs-lookup"><span data-stu-id="9a807-128">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="9a807-129">說明如何使用內建的委派功能在執行緒集區執行緒上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="9a807-129">Explains how to call methods on thread pool threads using built-in features of delegates.</span></span>  
  
 [<span data-ttu-id="9a807-130">平行程式設計</span><span class="sxs-lookup"><span data-stu-id="9a807-130">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="9a807-131">描述平行程式設計程式庫，簡化應用程式中多個執行緒的用法。</span><span class="sxs-lookup"><span data-stu-id="9a807-131">Describes the parallel programming libraries, which simplify the use of multiple threads in applications.</span></span>  
  
 [<span data-ttu-id="9a807-132">平行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="9a807-132">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 <span data-ttu-id="9a807-133">描述以平行方式執行查詢的系統，以善用多個處理器。</span><span class="sxs-lookup"><span data-stu-id="9a807-133">Describes a system for running queries in parallel, to take advantage of multiple processors.</span></span>
