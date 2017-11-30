---
title: Mutex
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wait handles
- threading [.NET Framework], Mutex class
- Mutex class, about Mutex class
- threading [.NET Framework], cross-process synchronization
ms.assetid: 9dd06e25-12c0-4a9e-855a-452dc83803e2
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a1d69c1b943d15b9ad8c80b4d7dbafebc54990ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="mutexes"></a><span data-ttu-id="927e6-102">Mutex</span><span class="sxs-lookup"><span data-stu-id="927e6-102">Mutexes</span></span>
<span data-ttu-id="927e6-103">您可以使用<xref:System.Threading.Mutex>來提供資源的獨佔存取的物件。</span><span class="sxs-lookup"><span data-stu-id="927e6-103">You can use a <xref:System.Threading.Mutex> object to provide exclusive access to a resource.</span></span> <span data-ttu-id="927e6-104"><xref:System.Threading.Mutex>類別會使用更多系統資源比<xref:System.Threading.Monitor>類別，但它可以封送處理跨應用程式定義域界限、 搭配多個等待，和它可以用於同步處理不同的處理序中執行緒。</span><span class="sxs-lookup"><span data-stu-id="927e6-104">The <xref:System.Threading.Mutex> class uses more system resources than the <xref:System.Threading.Monitor> class, but it can be marshaled across application domain boundaries, it can be used with multiple waits, and it can be used to synchronize threads in different processes.</span></span> <span data-ttu-id="927e6-105">如需受管理之同步處理機制的比較，請參閱[同步處理原始物件概觀](../../../docs/standard/threading/overview-of-synchronization-primitives.md)。</span><span class="sxs-lookup"><span data-stu-id="927e6-105">For a comparison of managed synchronization mechanisms, see [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="927e6-106">如需程式碼範例，請參閱參考文件<xref:System.Threading.Mutex.%23ctor%2A>建構函式。</span><span class="sxs-lookup"><span data-stu-id="927e6-106">For code examples, see the reference documentation for the <xref:System.Threading.Mutex.%23ctor%2A> constructors.</span></span>  
  
## <a name="using-mutexes"></a><span data-ttu-id="927e6-107">使用 Mutex</span><span class="sxs-lookup"><span data-stu-id="927e6-107">Using Mutexes</span></span>  
 <span data-ttu-id="927e6-108">執行緒呼叫<xref:System.Threading.WaitHandle.WaitOne%2A>要求擁有權的 mutex 的方法。</span><span class="sxs-lookup"><span data-stu-id="927e6-108">A thread calls the <xref:System.Threading.WaitHandle.WaitOne%2A> method of a mutex to request ownership.</span></span> <span data-ttu-id="927e6-109">該呼叫會封鎖起來，直到 Mutex 可供使用或直到選擇性的逾時間隔時間過去。</span><span class="sxs-lookup"><span data-stu-id="927e6-109">The call blocks until the mutex is available, or until the optional timeout interval elapses.</span></span> <span data-ttu-id="927e6-110">如果沒有任何執行緒擁有 Mutex，則 Mutex 的狀態為已發出訊號。</span><span class="sxs-lookup"><span data-stu-id="927e6-110">The state of a mutex is signaled if no thread owns it.</span></span>  
  
 <span data-ttu-id="927e6-111">執行緒釋放 mutex 藉由呼叫其<xref:System.Threading.Mutex.ReleaseMutex%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="927e6-111">A thread releases a mutex by calling its <xref:System.Threading.Mutex.ReleaseMutex%2A> method.</span></span> <span data-ttu-id="927e6-112">Mutex 具有執行緒相似性；也就是說，Mutex 的釋放只能由擁有該 Mutex 的執行緒來執行。</span><span class="sxs-lookup"><span data-stu-id="927e6-112">Mutexes have thread affinity; that is, the mutex can be released only by the thread that owns it.</span></span> <span data-ttu-id="927e6-113">如果執行緒釋放的 mutex 並未擁有，<xref:System.ApplicationException>執行緒擲回。</span><span class="sxs-lookup"><span data-stu-id="927e6-113">If a thread releases a mutex it does not own, an <xref:System.ApplicationException> is thrown in the thread.</span></span>  
  
 <span data-ttu-id="927e6-114">因為<xref:System.Threading.Mutex>類別衍生自<xref:System.Threading.WaitHandle>，您也可以呼叫靜態<xref:System.Threading.WaitHandle.WaitAll%2A>或<xref:System.Threading.WaitHandle.WaitAny%2A>方法<xref:System.Threading.WaitHandle>要求擁有權<xref:System.Threading.Mutex>搭配其他等候控制代碼。</span><span class="sxs-lookup"><span data-stu-id="927e6-114">Because the <xref:System.Threading.Mutex> class derives from <xref:System.Threading.WaitHandle>, you can also call the static <xref:System.Threading.WaitHandle.WaitAll%2A> or <xref:System.Threading.WaitHandle.WaitAny%2A> methods of <xref:System.Threading.WaitHandle> to request ownership of a <xref:System.Threading.Mutex> in combination with other wait handles.</span></span>  
  
 <span data-ttu-id="927e6-115">如果執行緒擁有<xref:System.Threading.Mutex>，執行緒可以指定相同<xref:System.Threading.Mutex>中重複的等候要求呼叫，而不會封鎖其執行中; 不過，它必須釋放<xref:System.Threading.Mutex>次數釋出擁有權。</span><span class="sxs-lookup"><span data-stu-id="927e6-115">If a thread owns a <xref:System.Threading.Mutex>, that thread can specify the same <xref:System.Threading.Mutex> in repeated wait-request calls without blocking its execution; however, it must release the <xref:System.Threading.Mutex> as many times to release ownership.</span></span>  
  
## <a name="abandoned-mutexes"></a><span data-ttu-id="927e6-116">遭到放棄的 Mutex</span><span class="sxs-lookup"><span data-stu-id="927e6-116">Abandoned Mutexes</span></span>  
 <span data-ttu-id="927e6-117">如果執行緒終止而未釋放<xref:System.Threading.Mutex>，就會放棄 mutex。</span><span class="sxs-lookup"><span data-stu-id="927e6-117">If a thread terminates without releasing a <xref:System.Threading.Mutex>, the mutex is said to be abandoned.</span></span> <span data-ttu-id="927e6-118">這通常代表程式在設計上有嚴重錯誤，因為 Mutex 所保護的資源可能仍處於不一致的狀態。</span><span class="sxs-lookup"><span data-stu-id="927e6-118">This often indicates a serious programming error because the resource the mutex is protecting might be left in an inconsistent state.</span></span> <span data-ttu-id="927e6-119">在.NET Framework 2.0 版中，<xref:System.Threading.AbandonedMutexException>取得 mutex 的下一個執行緒中擲回。</span><span class="sxs-lookup"><span data-stu-id="927e6-119">In the .NET Framework version 2.0, an <xref:System.Threading.AbandonedMutexException> is thrown in the next thread that acquires the mutex.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="927e6-120">在.NET framework 1.0 和 1.1 中，已放棄的<xref:System.Threading.Mutex>正在等候執行緒取得擁有權設為收到信號的狀態和下一步。</span><span class="sxs-lookup"><span data-stu-id="927e6-120">In the .NET Framework versions 1.0 and 1.1, an abandoned <xref:System.Threading.Mutex> is set to the signaled state and the next waiting thread gets ownership.</span></span> <span data-ttu-id="927e6-121">如果有任何執行緒正在不等待，<xref:System.Threading.Mutex>會保留在收到信號的狀態。</span><span class="sxs-lookup"><span data-stu-id="927e6-121">If no thread is waiting, the <xref:System.Threading.Mutex> remains in a signaled state.</span></span> <span data-ttu-id="927e6-122">不會有例外狀況擲回。</span><span class="sxs-lookup"><span data-stu-id="927e6-122">No exception is thrown.</span></span>  
  
 <span data-ttu-id="927e6-123">如果是全系統 Mutex，遭到放棄的 Mutex 可能表示應用程式已意外終止 (例如，透過使用「Windows 工作管理員」)。</span><span class="sxs-lookup"><span data-stu-id="927e6-123">In the case of a system-wide mutex, an abandoned mutex might indicate that an application has been terminated abruptly (for example, by using Windows Task Manager).</span></span>  
  
## <a name="local-and-system-mutexes"></a><span data-ttu-id="927e6-124">本機和系統 Mutex</span><span class="sxs-lookup"><span data-stu-id="927e6-124">Local and System Mutexes</span></span>  
 <span data-ttu-id="927e6-125">Mutex 有兩種類型︰本機 Mutex 和具名的系統 Mutex。</span><span class="sxs-lookup"><span data-stu-id="927e6-125">Mutexes are of two types: local mutexes and named system mutexes.</span></span> <span data-ttu-id="927e6-126">如果您建立<xref:System.Threading.Mutex>物件使用的建構函式接受名稱，它是與作業系統物件，該名稱的關聯。</span><span class="sxs-lookup"><span data-stu-id="927e6-126">If you create a <xref:System.Threading.Mutex> object using a constructor that accepts a name, it is associated with an operating-system object of that name.</span></span> <span data-ttu-id="927e6-127">具名的系統 Mutex 能在整個作業系統中看到，而且可用來同步處理處理序的活動。</span><span class="sxs-lookup"><span data-stu-id="927e6-127">Named system mutexes are visible throughout the operating system and can be used to synchronize the activities of processes.</span></span> <span data-ttu-id="927e6-128">您可以建立多個<xref:System.Threading.Mutex>物件，代表相同的具名系統 mutex，而且您可以使用<xref:System.Threading.Mutex.OpenExisting%2A>方法來開啟現有的具名系統 mutex。</span><span class="sxs-lookup"><span data-stu-id="927e6-128">You can create multiple <xref:System.Threading.Mutex> objects that represent the same named system mutex, and you can use the <xref:System.Threading.Mutex.OpenExisting%2A> method to open an existing named system mutex.</span></span>  
  
 <span data-ttu-id="927e6-129">本機 Mutex只存在於您的處理序內。</span><span class="sxs-lookup"><span data-stu-id="927e6-129">A local mutex exists only within your process.</span></span> <span data-ttu-id="927e6-130">可供您參考到本機的程序中的任何執行緒<xref:System.Threading.Mutex>物件。</span><span class="sxs-lookup"><span data-stu-id="927e6-130">It can be used by any thread in your process that has a reference to the local <xref:System.Threading.Mutex> object.</span></span> <span data-ttu-id="927e6-131">每個<xref:System.Threading.Mutex>物件是另一個本機 mutex。</span><span class="sxs-lookup"><span data-stu-id="927e6-131">Each <xref:System.Threading.Mutex> object is a separate local mutex.</span></span>  
  
### <a name="access-control-security-for-system-mutexes"></a><span data-ttu-id="927e6-132">系統 Mutex 的存取控制安全性</span><span class="sxs-lookup"><span data-stu-id="927e6-132">Access Control Security for System Mutexes</span></span>  
 <span data-ttu-id="927e6-133">.NET Framework 2.0 版可讓您查詢及設定具名系統物件的 Windows 存取控制安全性。</span><span class="sxs-lookup"><span data-stu-id="927e6-133">The .NET Framework version 2.0 provides the ability to query and set Windows access control security for named system objects.</span></span> <span data-ttu-id="927e6-134">我們會建議您在建立系統 Mutex 後就為其提供保護，因為系統物件為全域所有，因此非您所擁有的程式碼也可將其鎖定。</span><span class="sxs-lookup"><span data-stu-id="927e6-134">Protecting system mutexes from the moment of creation is recommended because system objects are global and therefore can be locked by code other than your own.</span></span>  
  
 <span data-ttu-id="927e6-135">Mutex 的存取控制安全性的相關資訊，請參閱<xref:System.Security.AccessControl.MutexSecurity>和<xref:System.Security.AccessControl.MutexAccessRule>類別，<xref:System.Security.AccessControl.MutexRights>列舉型別， <xref:System.Threading.Mutex.GetAccessControl%2A>， <xref:System.Threading.Mutex.SetAccessControl%2A>，和<xref:System.Threading.Mutex.OpenExisting%2A>方法<xref:System.Threading.Mutex>類別和<xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29>建構函式。</span><span class="sxs-lookup"><span data-stu-id="927e6-135">For information on access control security for mutexes, see the <xref:System.Security.AccessControl.MutexSecurity> and <xref:System.Security.AccessControl.MutexAccessRule> classes, the <xref:System.Security.AccessControl.MutexRights> enumeration, the <xref:System.Threading.Mutex.GetAccessControl%2A>, <xref:System.Threading.Mutex.SetAccessControl%2A>, and <xref:System.Threading.Mutex.OpenExisting%2A> methods of the <xref:System.Threading.Mutex> class, and the <xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29> constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="927e6-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="927e6-136">See Also</span></span>  
 <xref:System.Threading.Mutex>  
 <xref:System.Threading.Mutex.%23ctor%2A>  
 <xref:System.Security.AccessControl.MutexSecurity>  
 <xref:System.Security.AccessControl.MutexAccessRule>  
 [<span data-ttu-id="927e6-137">執行緒處理</span><span class="sxs-lookup"><span data-stu-id="927e6-137">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="927e6-138">執行緒物件和功能</span><span class="sxs-lookup"><span data-stu-id="927e6-138">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="927e6-139">監視</span><span class="sxs-lookup"><span data-stu-id="927e6-139">Monitors</span></span>](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 [<span data-ttu-id="927e6-140">執行緒和執行緒處理</span><span class="sxs-lookup"><span data-stu-id="927e6-140">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)
