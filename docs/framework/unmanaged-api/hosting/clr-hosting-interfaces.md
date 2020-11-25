---
title: CLR 裝載介面
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
ms.openlocfilehash: 77f2ba64d9bdbe9793d56e88dae46fd506119ab8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719043"
---
# <a name="clr-hosting-interfaces"></a><span data-ttu-id="6af90-102">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="6af90-102">CLR Hosting Interfaces</span></span>

<span data-ttu-id="6af90-103">本節說明非受控主機可用來將 common language runtime (CLR) 整合至其應用程式的介面。</span><span class="sxs-lookup"><span data-stu-id="6af90-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span> <span data-ttu-id="6af90-104">.NET Framework 版本2.0 和更新版本的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="6af90-104">The information pertains to the .NET Framework version 2.0 and later versions.</span></span> <span data-ttu-id="6af90-105">這些介面可讓主控制項控制執行時間的許多層面，而不是1.0 和1.1 版本中可能的版本，並在 CLR 與主機的執行模型之間提供更緊密的整合。</span><span class="sxs-lookup"><span data-stu-id="6af90-105">These interfaces enable the host to control many more aspects of the runtime than was possible in versions 1.0 and 1.1, and provide much tighter integration between the CLR and the host's execution model.</span></span>  
  
 <span data-ttu-id="6af90-106">在 .NET Framework 1.0 和1.1 版中，裝載模型已啟用非受控主機，以將 CLR 載入至進程、設定特定設定，以及接收事件通知。</span><span class="sxs-lookup"><span data-stu-id="6af90-106">In the .NET Framework version 1.0 and 1.1, the hosting model enabled an unmanaged host to load the CLR into a process, to configure certain settings, and to receive event notifications.</span></span> <span data-ttu-id="6af90-107">不過，一般而言，主機和 CLR 會在該進程中獨立執行。</span><span class="sxs-lookup"><span data-stu-id="6af90-107">However, in general, the host and the CLR ran independently in that process.</span></span> <span data-ttu-id="6af90-108">在 .NET Framework 2.0 版和更新版本中，新的抽象層可讓主機提供 Win32 元件中類型目前提供的許多資源，並擴充主機可以設定的一組功能。</span><span class="sxs-lookup"><span data-stu-id="6af90-108">In the .NET Framework version 2.0 and later versions, new layers of abstraction let the host provide many of the resources currently provided by the types in the Win32 assembly, and extend the set of capabilities that the host can configure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6af90-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="6af90-109">In This Section</span></span>  

 [<span data-ttu-id="6af90-110">IActionOnCLREvent 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-110">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)  
 <span data-ttu-id="6af90-111">提供方法，此方法會針對已註冊的事件執行回呼。</span><span class="sxs-lookup"><span data-stu-id="6af90-111">Provides a method that performs a callback for a registered event.</span></span>  
  
 [<span data-ttu-id="6af90-112">IApartmentCallback 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-112">IApartmentCallback Interface</span></span>](iapartmentcallback-interface.md)  
 <span data-ttu-id="6af90-113">提供在一個單元內進行回呼的方法。</span><span class="sxs-lookup"><span data-stu-id="6af90-113">Provides methods for making callbacks within an apartment.</span></span>  
  
 [<span data-ttu-id="6af90-114">IAppDomainBinding 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-114">IAppDomainBinding Interface</span></span>](iappdomainbinding-interface.md)  
 <span data-ttu-id="6af90-115">提供用來設定執行時間設定的方法。</span><span class="sxs-lookup"><span data-stu-id="6af90-115">Provides methods for setting run-time configuration.</span></span>  
  
 [<span data-ttu-id="6af90-116">ICatalogServices 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-116">ICatalogServices Interface</span></span>](icatalogservices-interface.md)  
 <span data-ttu-id="6af90-117">提供編目服務的方法。</span><span class="sxs-lookup"><span data-stu-id="6af90-117">Provides methods for cataloging services.</span></span> <span data-ttu-id="6af90-118"> (此介面支援 .NET Framework 基礎結構，而且不適合直接從程式碼使用。 ) </span><span class="sxs-lookup"><span data-stu-id="6af90-118">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="6af90-119">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-119">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)  
 <span data-ttu-id="6af90-120">提供的方法可支援主機和 CLR 與元件之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="6af90-120">Provides methods that support communication between the host and the CLR about assemblies.</span></span>  
  
 [<span data-ttu-id="6af90-121">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-121">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)  
 <span data-ttu-id="6af90-122">管理由 CLR 載入的元件清單，而不是由主機載入的元件清單。</span><span class="sxs-lookup"><span data-stu-id="6af90-122">Manages a list of assemblies that are loaded by the CLR and not by the host.</span></span>  
  
 [<span data-ttu-id="6af90-123">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-123">ICLRControl Interface</span></span>](iclrcontrol-interface.md)  
 <span data-ttu-id="6af90-124">提供方法讓主機取得和設定 CLR 的各個層面。</span><span class="sxs-lookup"><span data-stu-id="6af90-124">Provides methods for the host to gain access to, and configure various aspects of, the CLR.</span></span>  
  
 [<span data-ttu-id="6af90-125">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-125">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)  
 <span data-ttu-id="6af90-126">提供可讓主控制項將一組工作與識別碼和易記名稱產生關聯的方法。</span><span class="sxs-lookup"><span data-stu-id="6af90-126">Provides methods that enable a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
 [<span data-ttu-id="6af90-127">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-127">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)  
 <span data-ttu-id="6af90-128">提供可讓主機針對錯誤報表設定自訂堆積傾印的方法。</span><span class="sxs-lookup"><span data-stu-id="6af90-128">Provides methods that enable the host to configure custom heap dumps for error reporting.</span></span>  
  
 [<span data-ttu-id="6af90-129">ICLRGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-129">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)  
 <span data-ttu-id="6af90-130">提供可讓主控制項與 CLR 的垃圾收集系統互動的方法。</span><span class="sxs-lookup"><span data-stu-id="6af90-130">Provides methods that enable a host to interact with the CLR's garbage collection system.</span></span>  
  
 [<span data-ttu-id="6af90-131">ICLRHostBindingPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-131">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)  
 <span data-ttu-id="6af90-132">提供方法，讓主機評估及傳達元件的原則資訊變更。</span><span class="sxs-lookup"><span data-stu-id="6af90-132">Provides methods for the host to evaluate and communicate changes in policy information for assemblies.</span></span>  
  
 [<span data-ttu-id="6af90-133">ICLRHostProtectionManager 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-133">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)  
 <span data-ttu-id="6af90-134">讓主機封鎖特定的 managed 類別、方法、屬性和欄位，使其無法在部分信任的程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="6af90-134">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
 [<span data-ttu-id="6af90-135">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-135">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)  
 <span data-ttu-id="6af90-136">執行回呼方法，這個方法可讓主機通知 CLR 所指定 i/o 要求的狀態。</span><span class="sxs-lookup"><span data-stu-id="6af90-136">Implements a callback method that enables the host to notify the CLR of the status of specified I/O requests.</span></span>  
  
 [<span data-ttu-id="6af90-137">ICLRMemoryNotificationCallback 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-137">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)  
 <span data-ttu-id="6af90-138">使用與 Win32 函數類似的方法，讓主機能夠報告記憶體壓力條件 `CreateMemoryResourceNotification` 。</span><span class="sxs-lookup"><span data-stu-id="6af90-138">Enables the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
 [<span data-ttu-id="6af90-139">ICLROnEventManager 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-139">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)  
 <span data-ttu-id="6af90-140">提供可讓主機針對 CLR 事件註冊和取消註冊回呼的方法。</span><span class="sxs-lookup"><span data-stu-id="6af90-140">Provides methods that enable the host to register and unregister callbacks for CLR events.</span></span>  
  
 [<span data-ttu-id="6af90-141">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-141">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)  
 <span data-ttu-id="6af90-142">提供的方法，可讓主機指定發生失敗和超時時所要採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="6af90-142">Provides methods that enable the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
 [<span data-ttu-id="6af90-143">ICLRProbingAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-143">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)  
 <span data-ttu-id="6af90-144">提供的方法可讓主機使用 CLR 內部的元件身分識別資訊來取得元件的探查識別，而不需要建立或瞭解該身分識別。</span><span class="sxs-lookup"><span data-stu-id="6af90-144">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the CLR, without needing to create or understand that identity.</span></span>  
  
 [<span data-ttu-id="6af90-145">ICLRReferenceAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-145">ICLRReferenceAssemblyEnum Interface</span></span>](iclrreferenceassemblyenum-interface.md)  
 <span data-ttu-id="6af90-146">提供的方法可讓主機使用 CLR 內部的元件身分識別資料，來操作檔案或資料流程所參考的元件集合，而不需要建立或瞭解這些身分識別。</span><span class="sxs-lookup"><span data-stu-id="6af90-146">Provides methods that enable the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the CLR, without needing to create or understand those identities.</span></span>  
  
 [<span data-ttu-id="6af90-147">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-147">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)  
 <span data-ttu-id="6af90-148">提供與 [ICorRuntimeHost](icorruntimehost-interface.md)類似的功能，並提供可設定主控制項介面的額外方法。</span><span class="sxs-lookup"><span data-stu-id="6af90-148">Provides capabilities similar to [ICorRuntimeHost](icorruntimehost-interface.md), with an additional method to set the host control interface.</span></span>  
  
 [<span data-ttu-id="6af90-149">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-149">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)  
 <span data-ttu-id="6af90-150">提供方法，讓主機取得所要求之工作的相關資訊，並偵測其同步處理執行中的鎖死。</span><span class="sxs-lookup"><span data-stu-id="6af90-150">Provides methods for the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
 [<span data-ttu-id="6af90-151">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-151">ICLRTask Interface</span></span>](iclrtask-interface.md)  
 <span data-ttu-id="6af90-152">提供可讓主機提出 CLR 要求的方法，或提供有關相關聯工作之 CLR 的通知。</span><span class="sxs-lookup"><span data-stu-id="6af90-152">Provides methods that enable the host to make requests of the CLR, or to provide notification to the CLR about the associated task.</span></span>  
  
 [<span data-ttu-id="6af90-153">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-153">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)  
 <span data-ttu-id="6af90-154">提供的方法可讓主機明確要求 CLR 建立新的工作、取得目前正在執行的工作，以及設定工作的地理語言和文化特性。</span><span class="sxs-lookup"><span data-stu-id="6af90-154">Provides methods that enable the host to request explicitly that the CLR create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
 [<span data-ttu-id="6af90-155">ICLRValidator 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-155">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)  
 <span data-ttu-id="6af90-156">提供驗證可攜式可執行檔 (PE) 映射和報告驗證錯誤的方法。</span><span class="sxs-lookup"><span data-stu-id="6af90-156">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
 [<span data-ttu-id="6af90-157">ICorConfiguration 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-157">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)  
 <span data-ttu-id="6af90-158">提供設定 CLR 的方法。</span><span class="sxs-lookup"><span data-stu-id="6af90-158">Provides methods for configuring the CLR.</span></span>  
  
 [<span data-ttu-id="6af90-159">ICorThreadpool 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-159">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)  
 <span data-ttu-id="6af90-160">提供存取執行緒集區的方法。</span><span class="sxs-lookup"><span data-stu-id="6af90-160">Provides methods for accessing the thread pool.</span></span>  
  
 [<span data-ttu-id="6af90-161">IDebuggerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-161">IDebuggerInfo Interface</span></span>](idebuggerinfo-interface.md)  
 <span data-ttu-id="6af90-162">提供方法，以取得有關偵錯工具狀態的資訊。</span><span class="sxs-lookup"><span data-stu-id="6af90-162">Provides methods for obtaining information about the state of the debugging services.</span></span>  
  
 [<span data-ttu-id="6af90-163">IDebuggerThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-163">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)  
 <span data-ttu-id="6af90-164">提供方法，通知主機有關偵錯工具的執行緒封鎖和解除封鎖。</span><span class="sxs-lookup"><span data-stu-id="6af90-164">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
 [<span data-ttu-id="6af90-165">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-165">IGCHost Interface</span></span>](igchost-interface.md)  
 <span data-ttu-id="6af90-166">提供方法來取得垃圾收集系統的相關資訊，以及控制垃圾收集的某些層面。</span><span class="sxs-lookup"><span data-stu-id="6af90-166">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
 [<span data-ttu-id="6af90-167">IGCHost2 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-167">IGCHost2 Interface</span></span>](igchost2-interface.md)  
 <span data-ttu-id="6af90-168">提供 [SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) 方法，可讓主控制項將垃圾收集區段的大小以及垃圾收集系統層代零的大小上限設定為大於 `DWORD` 的值。</span><span class="sxs-lookup"><span data-stu-id="6af90-168">Provides the [SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) method that enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation zero to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="6af90-169">IGCHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-169">IGCHostControl Interface</span></span>](igchostcontrol-interface.md)  
 <span data-ttu-id="6af90-170">提供一種方法，可讓垃圾收集行程要求主控制項變更虛擬記憶體的限制。</span><span class="sxs-lookup"><span data-stu-id="6af90-170">Provides a method that enables the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
 [<span data-ttu-id="6af90-171">IGCThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-171">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)  
 <span data-ttu-id="6af90-172">提供方法來參與執行緒的排程，而這些執行緒會被封鎖以進行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="6af90-172">Provides methods for participating in the scheduling of threads that would otherwise be blocked for garbage collection.</span></span>  
  
 [<span data-ttu-id="6af90-173">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-173">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)  
 <span data-ttu-id="6af90-174">提供的方法，可讓主機指定要由 CLR 或主機載入的元件集。</span><span class="sxs-lookup"><span data-stu-id="6af90-174">Provides methods that enable a host to specify sets of assemblies that should be loaded by the CLR or by the host.</span></span>  
  
 [<span data-ttu-id="6af90-175">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-175">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)  
 <span data-ttu-id="6af90-176">提供可讓主機獨立于 CLR 之外載入元件和模組的方法。</span><span class="sxs-lookup"><span data-stu-id="6af90-176">Provides methods that enable a host to load assemblies and modules independently of the CLR.</span></span>  
  
 [<span data-ttu-id="6af90-177">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-177">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)  
 <span data-ttu-id="6af90-178">提供主機所執行之自動重設事件的標記法。</span><span class="sxs-lookup"><span data-stu-id="6af90-178">Provides a representation of an auto-reset event implemented by the host.</span></span>  
  
 [<span data-ttu-id="6af90-179">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-179">IHostControl Interface</span></span>](ihostcontrol-interface.md)  
 <span data-ttu-id="6af90-180">提供方法來設定元件的載入，以及判斷主機所支援的裝載介面。</span><span class="sxs-lookup"><span data-stu-id="6af90-180">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
 [<span data-ttu-id="6af90-181">IHostCrst 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-181">IHostCrst Interface</span></span>](ihostcrst-interface.md)  
 <span data-ttu-id="6af90-182">作為執行緒的重要區段的主機標記法。</span><span class="sxs-lookup"><span data-stu-id="6af90-182">Serves as the host's representation of a critical section for threading.</span></span>  
  
 [<span data-ttu-id="6af90-183">IHostGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-183">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)  
 <span data-ttu-id="6af90-184">提供方法，以在 CLR 所執行的垃圾收集機制中通知主機事件。</span><span class="sxs-lookup"><span data-stu-id="6af90-184">Provides methods that notify the host of events in the garbage collection mechanism implemented by the CLR.</span></span>  
  
 [<span data-ttu-id="6af90-185">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-185">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)  
 <span data-ttu-id="6af90-186">提供可讓 CLR 與主機所提供的 i/o 完成通訊埠互動的方法。</span><span class="sxs-lookup"><span data-stu-id="6af90-186">Provides methods that enable the CLR to interact with I/O completion ports provided by the host.</span></span>  
  
 [<span data-ttu-id="6af90-187">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-187">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)  
 <span data-ttu-id="6af90-188">提供方法，讓 CLR 透過主控制項向堆積要求更精細的配置。</span><span class="sxs-lookup"><span data-stu-id="6af90-188">Provides methods for the CLR to request fine-grained allocations from the heap through the host.</span></span>  
  
 [<span data-ttu-id="6af90-189">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-189">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)  
 <span data-ttu-id="6af90-190">提供主機手動重設事件標記法的實作為。</span><span class="sxs-lookup"><span data-stu-id="6af90-190">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
 [<span data-ttu-id="6af90-191">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-191">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)  
 <span data-ttu-id="6af90-192">提供方法讓 CLR 透過主機提出虛擬記憶體要求，而不是使用標準 Win32 虛擬記憶體函式。</span><span class="sxs-lookup"><span data-stu-id="6af90-192">Provides methods for the CLR to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
 [<span data-ttu-id="6af90-193">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-193">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)  
 <span data-ttu-id="6af90-194">提供方法，以通知主機 CLR 在中止、超時或失敗時所執行的動作。</span><span class="sxs-lookup"><span data-stu-id="6af90-194">Provides methods that notify the host of the actions the CLR performs in case of aborts, timeouts, or failures.</span></span>  
  
 [<span data-ttu-id="6af90-195">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-195">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)  
 <span data-ttu-id="6af90-196">讓 CLR 維護主機所執行的安全性內容資訊。</span><span class="sxs-lookup"><span data-stu-id="6af90-196">Enables the CLR to maintain security context information implemented by the host.</span></span>  
  
 [<span data-ttu-id="6af90-197">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-197">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)  
 <span data-ttu-id="6af90-198">提供方法，可讓您存取和控制目前執行中線程的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="6af90-198">Provides methods that enable access to, and control over, the security context of the currently executing thread.</span></span>  
  
 [<span data-ttu-id="6af90-199">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-199">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)  
 <span data-ttu-id="6af90-200">提供主機所執行之信號的標記法。</span><span class="sxs-lookup"><span data-stu-id="6af90-200">Provides a representation of a semaphore implemented by the host.</span></span>  
  
 [<span data-ttu-id="6af90-201">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-201">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)  
 <span data-ttu-id="6af90-202">提供方法，讓 CLR 藉由呼叫主機來建立同步處理原始物件，而不是使用 Win32 同步處理函數。</span><span class="sxs-lookup"><span data-stu-id="6af90-202">Provides methods for the CLR to create synchronization primitives by calling the host, instead of using the Win32 synchronization functions.</span></span>  
  
 [<span data-ttu-id="6af90-203">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-203">IHostTask Interface</span></span>](ihosttask-interface.md)  
 <span data-ttu-id="6af90-204">提供可讓 CLR 與主機通訊以管理工作的方法。</span><span class="sxs-lookup"><span data-stu-id="6af90-204">Provides methods that enable the CLR to communicate with the host to manage tasks.</span></span>  
  
 [<span data-ttu-id="6af90-205">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-205">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)  
 <span data-ttu-id="6af90-206">提供可讓 CLR 透過主機處理工作的方法，而不是使用標準作業系統執行緒或光纖函數。</span><span class="sxs-lookup"><span data-stu-id="6af90-206">Provides methods that enable the CLR to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
 [<span data-ttu-id="6af90-207">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-207">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)  
 <span data-ttu-id="6af90-208">提供方法讓 CLR 設定執行緒集區，並將工作專案加入執行緒集區。</span><span class="sxs-lookup"><span data-stu-id="6af90-208">Provides methods for the CLR to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
 [<span data-ttu-id="6af90-209">IManagedObject 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-209">IManagedObject Interface</span></span>](imanagedobject-interface.md)  
 <span data-ttu-id="6af90-210">提供控制 managed 物件的方法。</span><span class="sxs-lookup"><span data-stu-id="6af90-210">Provides methods for controlling a managed object.</span></span>  
  
 <span data-ttu-id="6af90-211">IObjectHandle</span><span class="sxs-lookup"><span data-stu-id="6af90-211">"IObjectHandle"</span></span>  
 <span data-ttu-id="6af90-212">提供方法來解除包裝從間接取值的封送處理物件。</span><span class="sxs-lookup"><span data-stu-id="6af90-212">Provides a method for unwrapping marshal-by-value objects from indirection.</span></span>  
  
 [<span data-ttu-id="6af90-213">ITypeName 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-213">ITypeName Interface</span></span>](itypename-interface.md)  
 <span data-ttu-id="6af90-214">提供取得型別名稱資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="6af90-214">Provides methods for obtaining type name information.</span></span> <span data-ttu-id="6af90-215"> (此介面支援 .NET Framework 基礎結構，而且不適合直接從程式碼使用。 ) </span><span class="sxs-lookup"><span data-stu-id="6af90-215">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="6af90-216">ITypeNameBuilder 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-216">ITypeNameBuilder Interface</span></span>](itypenamebuilder-interface.md)  
 <span data-ttu-id="6af90-217">提供建立型別名稱的方法。</span><span class="sxs-lookup"><span data-stu-id="6af90-217">Provides methods for building a type name.</span></span> <span data-ttu-id="6af90-218"> (此介面支援 .NET Framework 基礎結構，而且不適合直接從程式碼使用。 ) </span><span class="sxs-lookup"><span data-stu-id="6af90-218">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="6af90-219">ITypeNameFactory 介面</span><span class="sxs-lookup"><span data-stu-id="6af90-219">ITypeNameFactory Interface</span></span>](itypenamefactory-interface.md)  
 <span data-ttu-id="6af90-220">提供解構型別名稱的方法。</span><span class="sxs-lookup"><span data-stu-id="6af90-220">Provides methods for deconstructing a type name.</span></span> <span data-ttu-id="6af90-221"> (此介面支援 .NET Framework 基礎結構，而且不適合直接從程式碼使用。 ) </span><span class="sxs-lookup"><span data-stu-id="6af90-221">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 <span data-ttu-id="6af90-222">IValidator</span><span class="sxs-lookup"><span data-stu-id="6af90-222">"IValidator"</span></span>  
 <span data-ttu-id="6af90-223">提供驗證可攜式可執行檔 (PE) 映射和報告驗證錯誤的方法。</span><span class="sxs-lookup"><span data-stu-id="6af90-223">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6af90-224">相關章節</span><span class="sxs-lookup"><span data-stu-id="6af90-224">Related Sections</span></span>  

 [<span data-ttu-id="6af90-225">已被取代的 CLR 裝載介面和 Coclass</span><span class="sxs-lookup"><span data-stu-id="6af90-225">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="6af90-226">包含描述 .NET Framework 版本1.0 和1.1 中所提供之裝載介面的主題。</span><span class="sxs-lookup"><span data-stu-id="6af90-226">Contains topics that describe the hosting interfaces provided in the .NET Framework version 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="6af90-227">.NET Framework 4 和 4.5 中新增的 CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="6af90-227">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="6af90-228">包含描述 .NET Framework 4 中所提供之裝載介面的主題。</span><span class="sxs-lookup"><span data-stu-id="6af90-228">Contains topics that describe the hosting interfaces provided in the .NET Framework 4.</span></span>
