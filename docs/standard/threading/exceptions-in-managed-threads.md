---
title: "Managed 執行緒中的例外狀況"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unhandled exceptions,in managed threads
- threading [.NET Framework],unhandled exceptions
- threading [.NET Framework],exceptions in managed threads
- managed threading
ms.assetid: 11294769-2e89-43cb-890e-ad4ad79cfbee
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4f68a7aebdb1625b149287d70fd91c2108a658b9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="exceptions-in-managed-threads"></a><span data-ttu-id="93135-102">Managed 執行緒中的例外狀況</span><span class="sxs-lookup"><span data-stu-id="93135-102">Exceptions in Managed Threads</span></span>
<span data-ttu-id="93135-103">從 .NET Framework version 2.0 開始，通用語言執行平台允許執行緒中大多數未處理的例外狀況自然地繼續。</span><span class="sxs-lookup"><span data-stu-id="93135-103">Starting with the .NET Framework version 2.0, the common language runtime allows most unhandled exceptions in threads to proceed naturally.</span></span> <span data-ttu-id="93135-104">在大多數情況下，這表示未處理的例外狀況導致應用程式終止。</span><span class="sxs-lookup"><span data-stu-id="93135-104">In most cases this means that the unhandled exception causes the application to terminate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93135-105">這是 .NET Framework 1.0 和 1.1 的重大變更，其針對許多未處理的例外狀況提供了防護網 — 例如，執行緒集區執行緒中的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="93135-105">This is a significant change from the .NET Framework versions 1.0 and 1.1, which provide a backstop for many unhandled exceptions — for example, unhandled exceptions in thread pool threads.</span></span> <span data-ttu-id="93135-106">請參閱本主題後面的[從舊版變更](#ChangeFromPreviousVersions)。</span><span class="sxs-lookup"><span data-stu-id="93135-106">See [Change from Previous Versions](#ChangeFromPreviousVersions) later in this topic.</span></span>  
  
 <span data-ttu-id="93135-107">通用語言執行平台針對用於控制程式流程的特定未處理例外狀況提供了防護網︰</span><span class="sxs-lookup"><span data-stu-id="93135-107">The common language runtime provides a backstop for certain unhandled exceptions that are used for controlling program flow:</span></span>  
  
-   <span data-ttu-id="93135-108">因為呼叫了 <xref:System.Threading.Thread.Abort%2A>，而導致執行緒中擲回 <xref:System.Threading.ThreadAbortException>。</span><span class="sxs-lookup"><span data-stu-id="93135-108">A <xref:System.Threading.ThreadAbortException> is thrown in a thread because <xref:System.Threading.Thread.Abort%2A> was called.</span></span>  
  
-   <span data-ttu-id="93135-109">因為正在卸載執行緒執行所在的應用程式定義域，而在執行緒中擲回 <xref:System.AppDomainUnloadedException>。</span><span class="sxs-lookup"><span data-stu-id="93135-109">An <xref:System.AppDomainUnloadedException> is thrown in a thread because the application domain in which the thread is executing is being unloaded.</span></span>  
  
-   <span data-ttu-id="93135-110">通用語言執行平台或主機處理序會藉由擲回內部例外狀況來終止執行緒。</span><span class="sxs-lookup"><span data-stu-id="93135-110">The common language runtime or a host process terminates the thread by throwing an internal exception.</span></span>  
  
 <span data-ttu-id="93135-111">如果在通用語言執行平台所建立的執行緒中有上述任何未處理的例外狀況，則此例外狀況會終止執行緒，但通用語言執行平台不允許例外狀況進一步繼續作業。</span><span class="sxs-lookup"><span data-stu-id="93135-111">If any of these exceptions are unhandled in threads created by the common language runtime, the exception terminates the thread, but the common language runtime does not allow the exception to proceed further.</span></span>  
  
 <span data-ttu-id="93135-112">如果未在主要執行緒中，或在從 Unmanaged 程式碼進入執行平台的執行緒中處理這些例外狀況，這些例外狀況會正常進行，而導致應用程式終止。</span><span class="sxs-lookup"><span data-stu-id="93135-112">If these exceptions are unhandled in the main thread, or in threads that entered the runtime from unmanaged code, they proceed normally, resulting in termination of the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93135-113">在任何 Managed 程式碼有機會安裝例外狀況處理常式之前，執行平台可能會擲回未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="93135-113">It is possible for the runtime to throw an unhandled exception before any managed code has had a chance to install an exception handler.</span></span> <span data-ttu-id="93135-114">即使 Managed 程式碼沒有機會處理這類例外狀況，但允許例外狀況自然地進行。</span><span class="sxs-lookup"><span data-stu-id="93135-114">Even though managed code had no chance to handle such an exception, the exception is allowed to proceed naturally.</span></span>  
  
## <a name="exposing-threading-problems-during-development"></a><span data-ttu-id="93135-115">公開開發期間的執行緒問題</span><span class="sxs-lookup"><span data-stu-id="93135-115">Exposing Threading Problems During Development</span></span>  
 <span data-ttu-id="93135-116">若允許執行緒以無訊息模式失敗，而不終止應用程式，則可能偵測不到嚴重的程式設計問題。</span><span class="sxs-lookup"><span data-stu-id="93135-116">When threads are allowed to fail silently, without terminating the application, serious programming problems can go undetected.</span></span> <span data-ttu-id="93135-117">這是長時間執行的服務和其他應用程式特有的問題。</span><span class="sxs-lookup"><span data-stu-id="93135-117">This is a particular problem for services and other applications which run for extended periods.</span></span> <span data-ttu-id="93135-118">因為執行緒失敗，所以程式狀態會逐漸變差。</span><span class="sxs-lookup"><span data-stu-id="93135-118">As threads fail, program state gradually becomes corrupted.</span></span> <span data-ttu-id="93135-119">應用程式效能可能會降低，或應用程式可能會停止回應。</span><span class="sxs-lookup"><span data-stu-id="93135-119">Application performance may degrade, or the application might hang.</span></span>  
  
 <span data-ttu-id="93135-120">允許執行緒中的未處理例外狀況自然地進行，直到作業系統終止程式，公開開發和測試期間的這類問題為止。</span><span class="sxs-lookup"><span data-stu-id="93135-120">Allowing unhandled exceptions in threads to proceed naturally, until the operating system terminates the program, exposes such problems during development and testing.</span></span> <span data-ttu-id="93135-121">程式終止的錯誤報告可支援偵錯。</span><span class="sxs-lookup"><span data-stu-id="93135-121">Error reports on program terminations support debugging.</span></span>  
  
<a name="ChangeFromPreviousVersions"></a>   
## <a name="change-from-previous-versions"></a><span data-ttu-id="93135-122">從舊版變更</span><span class="sxs-lookup"><span data-stu-id="93135-122">Change from Previous Versions</span></span>  
 <span data-ttu-id="93135-123">最重大的變更與 Managed 執行緒有關。</span><span class="sxs-lookup"><span data-stu-id="93135-123">The most significant change pertains to managed threads.</span></span> <span data-ttu-id="93135-124">在 .NET Framework 1.0 和 1.1 版中，通用語言執行平台會針對下列情況中未處理的例外狀況提供防護網：</span><span class="sxs-lookup"><span data-stu-id="93135-124">In the .NET Framework versions 1.0 and 1.1, the common language runtime provides a backstop for unhandled exceptions in the following situations:</span></span>  
  
-   <span data-ttu-id="93135-125">執行緒集區執行緒上不會有未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="93135-125">There is no such thing as an unhandled exception on a thread pool thread.</span></span> <span data-ttu-id="93135-126">當工作擲回未處理的例外狀況時，執行平台會將例外狀況堆疊追蹤列印到主控台，然後將執行緒傳回到執行緒集區。</span><span class="sxs-lookup"><span data-stu-id="93135-126">When a task throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then returns the thread to the thread pool.</span></span>  
  
-   <span data-ttu-id="93135-127">使用 <xref:System.Threading.Thread> 類別的 <xref:System.Threading.Thread.Start%2A> 方法建立的執行緒上不會有未處理例外狀況之類的項目。</span><span class="sxs-lookup"><span data-stu-id="93135-127">There is no such thing as an unhandled exception on a thread created with the <xref:System.Threading.Thread.Start%2A> method of the <xref:System.Threading.Thread> class.</span></span> <span data-ttu-id="93135-128">在此種執行緒上執行的程式碼擲回未處理的例外狀況時，執行平台會將例外狀況堆疊追蹤列印到主控台，然後正常終止執行緒。</span><span class="sxs-lookup"><span data-stu-id="93135-128">When code running on such a thread throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then gracefully terminates the thread.</span></span>  
  
-   <span data-ttu-id="93135-129">完成項執行緒上不會有未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="93135-129">There is no such thing as an unhandled exception on the finalizer thread.</span></span> <span data-ttu-id="93135-130">當完成項擲回未處理的例外狀況時，執行平台會將例外狀況堆疊追蹤列印到主控台，然後允許完成項執行緒繼續執行完成項。</span><span class="sxs-lookup"><span data-stu-id="93135-130">When a finalizer throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then allows the finalizer thread to resume running finalizers.</span></span>  
  
 <span data-ttu-id="93135-131">Managed 執行緒的前景或背景狀態不會影響此行為。</span><span class="sxs-lookup"><span data-stu-id="93135-131">The foreground or background status of a managed thread does not affect this behavior.</span></span>  
  
 <span data-ttu-id="93135-132">若為源自於 Unmanaged 程式碼的執行緒上未處理的例外狀況，差別更加細微。</span><span class="sxs-lookup"><span data-stu-id="93135-132">For unhandled exceptions on threads originating in unmanaged code, the difference is more subtle.</span></span> <span data-ttu-id="93135-133">對於已通過機器碼之執行緒上的 Managed 例外狀況或原生例外狀況而言，執行階段 JIT-attach 對話方塊的順序優先於作業系統對話方塊。</span><span class="sxs-lookup"><span data-stu-id="93135-133">The runtime JIT-attach dialog preempts the operating system dialog for managed exceptions or native exceptions on threads that have passed through native code.</span></span> <span data-ttu-id="93135-134">在所有情況下，此處理序會終止。</span><span class="sxs-lookup"><span data-stu-id="93135-134">The process terminates in all cases.</span></span>  
  
### <a name="migrating-code"></a><span data-ttu-id="93135-135">移轉程式碼</span><span class="sxs-lookup"><span data-stu-id="93135-135">Migrating Code</span></span>  
 <span data-ttu-id="93135-136">一般而言，變更會公開先前無法辨識的程式設計問題，以便修正這些問題。</span><span class="sxs-lookup"><span data-stu-id="93135-136">In general, the change will expose previously unrecognized programming problems so that they can be fixed.</span></span> <span data-ttu-id="93135-137">不過，在某些情況下，程式設計人員可能已利用執行階段防護網來終止執行緒。</span><span class="sxs-lookup"><span data-stu-id="93135-137">In some cases, however, programmers might have taken advantage of the runtime backstop, for example to terminate threads.</span></span> <span data-ttu-id="93135-138">視情況而定，它們應該考慮下列其中一個移轉策略︰</span><span class="sxs-lookup"><span data-stu-id="93135-138">Depending on the situation, they should consider one of the following migration strategies:</span></span>  
  
-   <span data-ttu-id="93135-139">重新建構程式碼，讓執行緒在收到訊號時依正常程序結束。</span><span class="sxs-lookup"><span data-stu-id="93135-139">Restructure the code so the thread exits gracefully when a signal is received.</span></span>  
  
-   <span data-ttu-id="93135-140">使用 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 方法來中止執行緒。</span><span class="sxs-lookup"><span data-stu-id="93135-140">Use the <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method to abort the thread.</span></span>  
  
-   <span data-ttu-id="93135-141">如果執行緒必須停止，處理序終止作業才能繼續，請讓執行緒成為背景執行緒，以便在處理序結束時自動終止。</span><span class="sxs-lookup"><span data-stu-id="93135-141">If a thread must be stopped so that process termination can proceed, make the thread a background thread so that it is automatically terminated on process exit.</span></span>  
  
 <span data-ttu-id="93135-142">在所有情況下，此策略應該遵循例外狀況的設計方針。</span><span class="sxs-lookup"><span data-stu-id="93135-142">In all cases, the strategy should follow the design guidelines for exceptions.</span></span> <span data-ttu-id="93135-143">請參閱[例外狀況的設計方針](../../../docs/standard/design-guidelines/exceptions.md)。</span><span class="sxs-lookup"><span data-stu-id="93135-143">See [Design Guidelines for Exceptions](../../../docs/standard/design-guidelines/exceptions.md).</span></span>  
  
### <a name="application-compatibility-flag"></a><span data-ttu-id="93135-144">應用程式相容性旗標</span><span class="sxs-lookup"><span data-stu-id="93135-144">Application Compatibility Flag</span></span>  
 <span data-ttu-id="93135-145">系統管理員可以在應用程式組態檔的 `<runtime>` 區段中放置相容性旗標，做為暫存的相容性度量。</span><span class="sxs-lookup"><span data-stu-id="93135-145">As a temporary compatibility measure, administrators can place a compatibility flag in the `<runtime>` section of the application configuration file.</span></span> <span data-ttu-id="93135-146">這會導致通用語言執行平台還原為 1.0 和 1.1 版的行為。</span><span class="sxs-lookup"><span data-stu-id="93135-146">This causes the common language runtime to revert to the behavior of versions 1.0 and 1.1.</span></span>  
  
```xml  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## <a name="host-override"></a><span data-ttu-id="93135-147">主機覆寫</span><span class="sxs-lookup"><span data-stu-id="93135-147">Host Override</span></span>  
 <span data-ttu-id="93135-148">在 .NET Framework 2.0 版中，Unmanaged 主機可以使用裝載 API 中的 [ICLRPolicyManager](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) 介面，覆寫通用語言執行平台的預設未處理例外狀況原則。</span><span class="sxs-lookup"><span data-stu-id="93135-148">In the .NET Framework version 2.0, an unmanaged host can use the [ICLRPolicyManager](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface in the Hosting API to override the default unhandled exception policy of the common language runtime.</span></span> <span data-ttu-id="93135-149">[Iclrpolicymanager:: Setunhandledexceptionpolicy](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) 函數用來設定未處理例外狀況的原則。</span><span class="sxs-lookup"><span data-stu-id="93135-149">The [ICLRPolicyManager::SetUnhandledExceptionPolicy](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) function is used to set the policy for unhandled exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93135-150">請參閱</span><span class="sxs-lookup"><span data-stu-id="93135-150">See Also</span></span>  
 [<span data-ttu-id="93135-151">Managed 執行緒處理的基本概念</span><span class="sxs-lookup"><span data-stu-id="93135-151">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)
