---
title: CLR 裝載介面
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
ms.openlocfilehash: 66fdd97d101f5ea53a96b996a2a60e5ed65a2701
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131960"
---
# <a name="clr-hosting-interfaces"></a><span data-ttu-id="72bf8-102">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-102">CLR Hosting Interfaces</span></span>
<span data-ttu-id="72bf8-103">本節說明非受控主機可用來將 common language runtime （CLR）整合到其應用程式的介面。</span><span class="sxs-lookup"><span data-stu-id="72bf8-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span> <span data-ttu-id="72bf8-104">.NET Framework 版本2.0 和更新版本的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="72bf8-104">The information pertains to the .NET Framework version 2.0 and later versions.</span></span> <span data-ttu-id="72bf8-105">這些介面可讓主機控制執行時間的許多層面，而不是1.0 和1.1 版中可能的，並且在 CLR 與主機的執行模型之間提供更緊密的整合。</span><span class="sxs-lookup"><span data-stu-id="72bf8-105">These interfaces enable the host to control many more aspects of the runtime than was possible in versions 1.0 and 1.1, and provide much tighter integration between the CLR and the host's execution model.</span></span>  
  
 <span data-ttu-id="72bf8-106">在 .NET Framework 版本1.0 和1.1 中，裝載模型已啟用非受控主機，以將 CLR 載入至進程、設定特定設定，以及接收事件通知。</span><span class="sxs-lookup"><span data-stu-id="72bf8-106">In the .NET Framework version 1.0 and 1.1, the hosting model enabled an unmanaged host to load the CLR into a process, to configure certain settings, and to receive event notifications.</span></span> <span data-ttu-id="72bf8-107">不過，一般而言，主機和 CLR 會在該進程中獨立執行。</span><span class="sxs-lookup"><span data-stu-id="72bf8-107">However, in general, the host and the CLR ran independently in that process.</span></span> <span data-ttu-id="72bf8-108">在 .NET Framework 版本2.0 和更新版本中，新的抽象層可讓主機提供 Win32 元件中的類型目前提供的許多資源，並擴充主機可設定的一組功能。</span><span class="sxs-lookup"><span data-stu-id="72bf8-108">In the .NET Framework version 2.0 and later versions, new layers of abstraction let the host provide many of the resources currently provided by the types in the Win32 assembly, and extend the set of capabilities that the host can configure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="72bf8-109">本章節內容</span><span class="sxs-lookup"><span data-stu-id="72bf8-109">In This Section</span></span>  
 [<span data-ttu-id="72bf8-110">IActionOnCLREvent 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-110">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 <span data-ttu-id="72bf8-111">提供方法來執行已註冊事件的回呼。</span><span class="sxs-lookup"><span data-stu-id="72bf8-111">Provides a method that performs a callback for a registered event.</span></span>  
  
 [<span data-ttu-id="72bf8-112">IApartmentCallback 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-112">IApartmentCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)  
 <span data-ttu-id="72bf8-113">提供在單元內進行回呼的方法。</span><span class="sxs-lookup"><span data-stu-id="72bf8-113">Provides methods for making callbacks within an apartment.</span></span>  
  
 [<span data-ttu-id="72bf8-114">IAppDomainBinding 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-114">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)  
 <span data-ttu-id="72bf8-115">提供設定執行時間設定的方法。</span><span class="sxs-lookup"><span data-stu-id="72bf8-115">Provides methods for setting run-time configuration.</span></span>  
  
 [<span data-ttu-id="72bf8-116">ICatalogServices 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-116">ICatalogServices Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icatalogservices-interface.md)  
 <span data-ttu-id="72bf8-117">提供編目服務的方法。</span><span class="sxs-lookup"><span data-stu-id="72bf8-117">Provides methods for cataloging services.</span></span> <span data-ttu-id="72bf8-118">（此介面支援 .NET Framework 的基礎結構，但不適合直接從您的程式碼使用）。</span><span class="sxs-lookup"><span data-stu-id="72bf8-118">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="72bf8-119">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-119">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 <span data-ttu-id="72bf8-120">提供的方法可支援主機和 CLR 之間有關元件的通訊。</span><span class="sxs-lookup"><span data-stu-id="72bf8-120">Provides methods that support communication between the host and the CLR about assemblies.</span></span>  
  
 [<span data-ttu-id="72bf8-121">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 <span data-ttu-id="72bf8-122">管理由 CLR 載入的元件清單，而不是由主機載入。</span><span class="sxs-lookup"><span data-stu-id="72bf8-122">Manages a list of assemblies that are loaded by the CLR and not by the host.</span></span>  
  
 [<span data-ttu-id="72bf8-123">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-123">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 <span data-ttu-id="72bf8-124">提供方法讓主機取得 CLR 的存取權，以及設定各個層面。</span><span class="sxs-lookup"><span data-stu-id="72bf8-124">Provides methods for the host to gain access to, and configure various aspects of, the CLR.</span></span>  
  
 [<span data-ttu-id="72bf8-125">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 <span data-ttu-id="72bf8-126">提供可讓主機將一組工作與識別碼和易記名稱建立關聯的方法。</span><span class="sxs-lookup"><span data-stu-id="72bf8-126">Provides methods that enable a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
 [<span data-ttu-id="72bf8-127">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-127">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 <span data-ttu-id="72bf8-128">提供的方法可讓主機設定錯誤報表的自訂堆積傾印。</span><span class="sxs-lookup"><span data-stu-id="72bf8-128">Provides methods that enable the host to configure custom heap dumps for error reporting.</span></span>  
  
 [<span data-ttu-id="72bf8-129">ICLRGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-129">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 <span data-ttu-id="72bf8-130">提供可讓主機與 CLR 的垃圾收集系統互動的方法。</span><span class="sxs-lookup"><span data-stu-id="72bf8-130">Provides methods that enable a host to interact with the CLR's garbage collection system.</span></span>  
  
 [<span data-ttu-id="72bf8-131">ICLRHostBindingPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-131">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 <span data-ttu-id="72bf8-132">提供方法，讓主機評估和傳達元件原則資訊中的變更。</span><span class="sxs-lookup"><span data-stu-id="72bf8-132">Provides methods for the host to evaluate and communicate changes in policy information for assemblies.</span></span>  
  
 [<span data-ttu-id="72bf8-133">ICLRHostProtectionManager 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-133">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 <span data-ttu-id="72bf8-134">可讓主機封鎖特定的 managed 類別、方法、屬性和欄位，使其無法在部分信任的程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="72bf8-134">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
 [<span data-ttu-id="72bf8-135">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-135">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 <span data-ttu-id="72bf8-136">會執行回呼方法，讓主機通知 CLR 所指定 i/o 要求的狀態。</span><span class="sxs-lookup"><span data-stu-id="72bf8-136">Implements a callback method that enables the host to notify the CLR of the status of specified I/O requests.</span></span>  
  
 [<span data-ttu-id="72bf8-137">ICLRMemoryNotificationCallback 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 <span data-ttu-id="72bf8-138">使用類似 Win32 `CreateMemoryResourceNotification` 函式的方法，讓主機能夠報告記憶體壓力狀況。</span><span class="sxs-lookup"><span data-stu-id="72bf8-138">Enables the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
 [<span data-ttu-id="72bf8-139">ICLROnEventManager 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-139">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 <span data-ttu-id="72bf8-140">提供的方法可讓主機註冊和取消註冊 CLR 事件的回呼。</span><span class="sxs-lookup"><span data-stu-id="72bf8-140">Provides methods that enable the host to register and unregister callbacks for CLR events.</span></span>  
  
 [<span data-ttu-id="72bf8-141">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 <span data-ttu-id="72bf8-142">提供的方法可讓主機指定發生失敗和超時事件時所要採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="72bf8-142">Provides methods that enable the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
 [<span data-ttu-id="72bf8-143">ICLRProbingAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-143">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 <span data-ttu-id="72bf8-144">提供的方法可讓主機使用 CLR 內部的元件身分識別資訊來取得元件的探查識別，而不需要建立或瞭解該身分識別。</span><span class="sxs-lookup"><span data-stu-id="72bf8-144">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the CLR, without needing to create or understand that identity.</span></span>  
  
 [<span data-ttu-id="72bf8-145">ICLRReferenceAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-145">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)  
 <span data-ttu-id="72bf8-146">提供的方法可讓主機使用 CLR 內部的元件識別資料來操作檔案或資料流程所參考的元件集，而不需要建立或瞭解這些身分識別。</span><span class="sxs-lookup"><span data-stu-id="72bf8-146">Provides methods that enable the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the CLR, without needing to create or understand those identities.</span></span>  
  
 [<span data-ttu-id="72bf8-147">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-147">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 <span data-ttu-id="72bf8-148">提供與[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)類似的功能，以及設定主控制項介面的額外方法。</span><span class="sxs-lookup"><span data-stu-id="72bf8-148">Provides capabilities similar to [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md), with an additional method to set the host control interface.</span></span>  
  
 [<span data-ttu-id="72bf8-149">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-149">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 <span data-ttu-id="72bf8-150">提供方法，讓主機取得所要求之工作的相關資訊，以及偵測其同步處理執行中的鎖死。</span><span class="sxs-lookup"><span data-stu-id="72bf8-150">Provides methods for the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
 [<span data-ttu-id="72bf8-151">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-151">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 <span data-ttu-id="72bf8-152">提供的方法可讓主機提出 CLR 的要求，或提供相關聯工作的通知給 CLR。</span><span class="sxs-lookup"><span data-stu-id="72bf8-152">Provides methods that enable the host to make requests of the CLR, or to provide notification to the CLR about the associated task.</span></span>  
  
 [<span data-ttu-id="72bf8-153">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-153">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 <span data-ttu-id="72bf8-154">提供的方法可讓主機明確地要求 CLR 建立新工作、取得目前正在執行的工作，以及設定工作的地理語言和文化特性。</span><span class="sxs-lookup"><span data-stu-id="72bf8-154">Provides methods that enable the host to request explicitly that the CLR create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
 [<span data-ttu-id="72bf8-155">ICLRValidator 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-155">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)  
 <span data-ttu-id="72bf8-156">提供驗證可移植執行檔（PE）映射和報告驗證錯誤的方法。</span><span class="sxs-lookup"><span data-stu-id="72bf8-156">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
 [<span data-ttu-id="72bf8-157">ICorConfiguration 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-157">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)  
 <span data-ttu-id="72bf8-158">提供設定 CLR 的方法。</span><span class="sxs-lookup"><span data-stu-id="72bf8-158">Provides methods for configuring the CLR.</span></span>  
  
 [<span data-ttu-id="72bf8-159">ICorThreadpool 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-159">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)  
 <span data-ttu-id="72bf8-160">提供存取執行緒集區的方法。</span><span class="sxs-lookup"><span data-stu-id="72bf8-160">Provides methods for accessing the thread pool.</span></span>  
  
 [<span data-ttu-id="72bf8-161">IDebuggerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-161">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)  
 <span data-ttu-id="72bf8-162">提供方法來取得有關偵錯工具狀態的資訊。</span><span class="sxs-lookup"><span data-stu-id="72bf8-162">Provides methods for obtaining information about the state of the debugging services.</span></span>  
  
 [<span data-ttu-id="72bf8-163">IDebuggerThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-163">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)  
 <span data-ttu-id="72bf8-164">提供方法，以通知主機有關偵錯工具的執行緒封鎖和解除封鎖。</span><span class="sxs-lookup"><span data-stu-id="72bf8-164">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
 [<span data-ttu-id="72bf8-165">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-165">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)  
 <span data-ttu-id="72bf8-166">提供方法來取得垃圾收集系統的相關資訊，以及控制垃圾收集的某些層面。</span><span class="sxs-lookup"><span data-stu-id="72bf8-166">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
 [<span data-ttu-id="72bf8-167">IGCHost2 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-167">IGCHost2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)  
 <span data-ttu-id="72bf8-168">提供[SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)方法，可讓主機將垃圾收集區段的大小，以及垃圾收集系統層代零的大小上限設定為大於 `DWORD`的值。</span><span class="sxs-lookup"><span data-stu-id="72bf8-168">Provides the [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method that enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation zero to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="72bf8-169">IGCHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-169">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)  
 <span data-ttu-id="72bf8-170">提供一種方法，可讓垃圾收集行程要求主控制項變更虛擬記憶體的限制。</span><span class="sxs-lookup"><span data-stu-id="72bf8-170">Provides a method that enables the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
 [<span data-ttu-id="72bf8-171">IGCThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-171">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)  
 <span data-ttu-id="72bf8-172">提供方法來參與執行緒的排程，否則會封鎖進行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="72bf8-172">Provides methods for participating in the scheduling of threads that would otherwise be blocked for garbage collection.</span></span>  
  
 [<span data-ttu-id="72bf8-173">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-173">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 <span data-ttu-id="72bf8-174">提供的方法可讓主機指定要由 CLR 或主機載入的元件集。</span><span class="sxs-lookup"><span data-stu-id="72bf8-174">Provides methods that enable a host to specify sets of assemblies that should be loaded by the CLR or by the host.</span></span>  
  
 [<span data-ttu-id="72bf8-175">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-175">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 <span data-ttu-id="72bf8-176">提供的方法可讓主機獨立載入元件和模組，而不受 CLR 影響。</span><span class="sxs-lookup"><span data-stu-id="72bf8-176">Provides methods that enable a host to load assemblies and modules independently of the CLR.</span></span>  
  
 [<span data-ttu-id="72bf8-177">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-177">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 <span data-ttu-id="72bf8-178">提供主機所執行之自動重設事件的標記法。</span><span class="sxs-lookup"><span data-stu-id="72bf8-178">Provides a representation of an auto-reset event implemented by the host.</span></span>  
  
 [<span data-ttu-id="72bf8-179">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-179">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 <span data-ttu-id="72bf8-180">提供設定元件載入的方法，以及判斷主機支援的主控介面。</span><span class="sxs-lookup"><span data-stu-id="72bf8-180">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
 [<span data-ttu-id="72bf8-181">IHostCrst 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-181">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 <span data-ttu-id="72bf8-182">作為執行緒之重要區段的主機標記法。</span><span class="sxs-lookup"><span data-stu-id="72bf8-182">Serves as the host's representation of a critical section for threading.</span></span>  
  
 [<span data-ttu-id="72bf8-183">IHostGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-183">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
 <span data-ttu-id="72bf8-184">提供方法，在 CLR 所執行的垃圾收集機制中通知事件的主機。</span><span class="sxs-lookup"><span data-stu-id="72bf8-184">Provides methods that notify the host of events in the garbage collection mechanism implemented by the CLR.</span></span>  
  
 [<span data-ttu-id="72bf8-185">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-185">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 <span data-ttu-id="72bf8-186">提供的方法可讓 CLR 與主機所提供的 i/o 完成通訊埠互動。</span><span class="sxs-lookup"><span data-stu-id="72bf8-186">Provides methods that enable the CLR to interact with I/O completion ports provided by the host.</span></span>  
  
 [<span data-ttu-id="72bf8-187">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-187">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 <span data-ttu-id="72bf8-188">提供方法，讓 CLR 透過主機要求堆積中的精細配置。</span><span class="sxs-lookup"><span data-stu-id="72bf8-188">Provides methods for the CLR to request fine-grained allocations from the heap through the host.</span></span>  
  
 [<span data-ttu-id="72bf8-189">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-189">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 <span data-ttu-id="72bf8-190">提供主機的手動重設事件表示的執行方式。</span><span class="sxs-lookup"><span data-stu-id="72bf8-190">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
 [<span data-ttu-id="72bf8-191">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-191">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 <span data-ttu-id="72bf8-192">提供 CLR 透過主機提出虛擬記憶體要求的方法，而不是使用標準的 Win32 虛擬記憶體函數。</span><span class="sxs-lookup"><span data-stu-id="72bf8-192">Provides methods for the CLR to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
 [<span data-ttu-id="72bf8-193">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-193">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 <span data-ttu-id="72bf8-194">提供方法，以通知主機 CLR 在中止、超時或失敗時所執行的動作。</span><span class="sxs-lookup"><span data-stu-id="72bf8-194">Provides methods that notify the host of the actions the CLR performs in case of aborts, timeouts, or failures.</span></span>  
  
 [<span data-ttu-id="72bf8-195">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-195">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 <span data-ttu-id="72bf8-196">可讓 CLR 維護主機所執行的安全性內容資訊。</span><span class="sxs-lookup"><span data-stu-id="72bf8-196">Enables the CLR to maintain security context information implemented by the host.</span></span>  
  
 [<span data-ttu-id="72bf8-197">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-197">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 <span data-ttu-id="72bf8-198">提供的方法可讓您存取目前執行中線程的安全性內容，以及對其進行控制。</span><span class="sxs-lookup"><span data-stu-id="72bf8-198">Provides methods that enable access to, and control over, the security context of the currently executing thread.</span></span>  
  
 [<span data-ttu-id="72bf8-199">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-199">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 <span data-ttu-id="72bf8-200">提供主機所實作為信號的標記法。</span><span class="sxs-lookup"><span data-stu-id="72bf8-200">Provides a representation of a semaphore implemented by the host.</span></span>  
  
 [<span data-ttu-id="72bf8-201">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-201">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 <span data-ttu-id="72bf8-202">為 CLR 提供方法，藉由呼叫主機來建立同步處理原始物件，而不是使用 Win32 同步處理函式。</span><span class="sxs-lookup"><span data-stu-id="72bf8-202">Provides methods for the CLR to create synchronization primitives by calling the host, instead of using the Win32 synchronization functions.</span></span>  
  
 [<span data-ttu-id="72bf8-203">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-203">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 <span data-ttu-id="72bf8-204">提供的方法可讓 CLR 與主控制項進行通訊，以管理工作。</span><span class="sxs-lookup"><span data-stu-id="72bf8-204">Provides methods that enable the CLR to communicate with the host to manage tasks.</span></span>  
  
 [<span data-ttu-id="72bf8-205">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-205">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 <span data-ttu-id="72bf8-206">提供的方法可讓 CLR 透過主機來處理工作，而不是使用標準作業系統執行緒或光纖函數。</span><span class="sxs-lookup"><span data-stu-id="72bf8-206">Provides methods that enable the CLR to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
 [<span data-ttu-id="72bf8-207">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-207">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 <span data-ttu-id="72bf8-208">提供方法，讓 CLR 設定執行緒集區，並將工作專案排入執行緒集區佇列。</span><span class="sxs-lookup"><span data-stu-id="72bf8-208">Provides methods for the CLR to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
 [<span data-ttu-id="72bf8-209">IManagedObject 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-209">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)  
 <span data-ttu-id="72bf8-210">提供控制 managed 物件的方法。</span><span class="sxs-lookup"><span data-stu-id="72bf8-210">Provides methods for controlling a managed object.</span></span>  
  
 <span data-ttu-id="72bf8-211">IObjectHandle</span><span class="sxs-lookup"><span data-stu-id="72bf8-211">"IObjectHandle"</span></span>  
 <span data-ttu-id="72bf8-212">提供方法來解除包裝從間接取值的封送處理物件。</span><span class="sxs-lookup"><span data-stu-id="72bf8-212">Provides a method for unwrapping marshal-by-value objects from indirection.</span></span>  
  
 [<span data-ttu-id="72bf8-213">ITypeName 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-213">ITypeName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/itypename-interface.md)  
 <span data-ttu-id="72bf8-214">提供取得型別名稱資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="72bf8-214">Provides methods for obtaining type name information.</span></span> <span data-ttu-id="72bf8-215">（此介面支援 .NET Framework 的基礎結構，但不適合直接從您的程式碼使用）。</span><span class="sxs-lookup"><span data-stu-id="72bf8-215">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="72bf8-216">ITypeNameBuilder 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-216">ITypeNameBuilder Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/itypenamebuilder-interface.md)  
 <span data-ttu-id="72bf8-217">提供用來建立型別名稱的方法。</span><span class="sxs-lookup"><span data-stu-id="72bf8-217">Provides methods for building a type name.</span></span> <span data-ttu-id="72bf8-218">（此介面支援 .NET Framework 的基礎結構，但不適合直接從您的程式碼使用）。</span><span class="sxs-lookup"><span data-stu-id="72bf8-218">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="72bf8-219">ITypeNameFactory 介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-219">ITypeNameFactory Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/itypenamefactory-interface.md)  
 <span data-ttu-id="72bf8-220">提供解構類型名稱的方法。</span><span class="sxs-lookup"><span data-stu-id="72bf8-220">Provides methods for deconstructing a type name.</span></span> <span data-ttu-id="72bf8-221">（此介面支援 .NET Framework 的基礎結構，但不適合直接從您的程式碼使用）。</span><span class="sxs-lookup"><span data-stu-id="72bf8-221">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 <span data-ttu-id="72bf8-222">IValidator</span><span class="sxs-lookup"><span data-stu-id="72bf8-222">"IValidator"</span></span>  
 <span data-ttu-id="72bf8-223">提供驗證可移植執行檔（PE）映射和報告驗證錯誤的方法。</span><span class="sxs-lookup"><span data-stu-id="72bf8-223">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="72bf8-224">相關章節</span><span class="sxs-lookup"><span data-stu-id="72bf8-224">Related Sections</span></span>  
 [<span data-ttu-id="72bf8-225">已被取代的 CLR 裝載介面和 Coclass</span><span class="sxs-lookup"><span data-stu-id="72bf8-225">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="72bf8-226">包含主題，說明 .NET Framework 版本1.0 和1.1 中提供的主控介面。</span><span class="sxs-lookup"><span data-stu-id="72bf8-226">Contains topics that describe the hosting interfaces provided in the .NET Framework version 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="72bf8-227">.NET Framework 4 和 4.5 中新增的 CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="72bf8-227">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="72bf8-228">包含描述 .NET Framework 4 中所提供之主控介面的主題。</span><span class="sxs-lookup"><span data-stu-id="72bf8-228">Contains topics that describe the hosting interfaces provided in the .NET Framework 4.</span></span>
