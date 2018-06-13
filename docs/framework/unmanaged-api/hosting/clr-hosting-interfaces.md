---
title: CLR 裝載介面
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03839a2c6e52f9d2dcdd2e0941ff4fdbeb8a3a17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435637"
---
# <a name="clr-hosting-interfaces"></a><span data-ttu-id="71f0f-102">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-102">CLR Hosting Interfaces</span></span>
<span data-ttu-id="71f0f-103">本節描述 unmanaged 介面主機可用於將 common language runtime (CLR) 整合到他們的應用程式。</span><span class="sxs-lookup"><span data-stu-id="71f0f-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span> <span data-ttu-id="71f0f-104">資訊適用於.NET Framework 2.0 版和更新版本。</span><span class="sxs-lookup"><span data-stu-id="71f0f-104">The information pertains to the .NET Framework version 2.0 and later versions.</span></span> <span data-ttu-id="71f0f-105">這些介面來控制許多層面的執行階段，比起 1.0 和 1.1 版，請將主機啟用，並提供更緊密的整合，則 CLR 與主機的執行模式之間。</span><span class="sxs-lookup"><span data-stu-id="71f0f-105">These interfaces enable the host to control many more aspects of the runtime than was possible in versions 1.0 and 1.1, and provide much tighter integration between the CLR and the host's execution model.</span></span>  
  
 <span data-ttu-id="71f0f-106">在.NET Framework 1.0 和 1.1 版中，裝載模型啟用受管理的主機載入 CLR 程序，來設定特定的設定，以及接收事件通知。</span><span class="sxs-lookup"><span data-stu-id="71f0f-106">In the .NET Framework version 1.0 and 1.1, the hosting model enabled an unmanaged host to load the CLR into a process, to configure certain settings, and to receive event notifications.</span></span> <span data-ttu-id="71f0f-107">不過，在一般情況下，主應用程式和 CLR 執行獨立該處理程序。</span><span class="sxs-lookup"><span data-stu-id="71f0f-107">However, in general, the host and the CLR ran independently in that process.</span></span> <span data-ttu-id="71f0f-108">在.NET Framework 2.0 版和更新版本中，新的抽象層可讓主機提供多目前 Win32 組件中類型所提供的資源和擴充主應用程式可以設定的功能集。</span><span class="sxs-lookup"><span data-stu-id="71f0f-108">In the .NET Framework version 2.0 and later versions, new layers of abstraction let the host provide many of the resources currently provided by the types in the Win32 assembly, and extend the set of capabilities that the host can configure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="71f0f-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="71f0f-109">In This Section</span></span>  
 [<span data-ttu-id="71f0f-110">IActionOnCLREvent 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-110">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 <span data-ttu-id="71f0f-111">提供方法，以執行已註冊的事件回呼。</span><span class="sxs-lookup"><span data-stu-id="71f0f-111">Provides a method that performs a callback for a registered event.</span></span>  
  
 [<span data-ttu-id="71f0f-112">IApartmentCallback 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-112">IApartmentCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)  
 <span data-ttu-id="71f0f-113">提供讓 apartment 內的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="71f0f-113">Provides methods for making callbacks within an apartment.</span></span>  
  
 [<span data-ttu-id="71f0f-114">IAppDomainBinding 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-114">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)  
 <span data-ttu-id="71f0f-115">提供方法來設定執行階段組態。</span><span class="sxs-lookup"><span data-stu-id="71f0f-115">Provides methods for setting run-time configuration.</span></span>  
  
 [<span data-ttu-id="71f0f-116">ICatalogServices 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-116">ICatalogServices Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icatalogservices-interface.md)  
 <span data-ttu-id="71f0f-117">提供方法來分類的服務。</span><span class="sxs-lookup"><span data-stu-id="71f0f-117">Provides methods for cataloging services.</span></span> <span data-ttu-id="71f0f-118">（此介面支援.NET Framework 基礎結構的而且不是直接從您的程式碼使用）。</span><span class="sxs-lookup"><span data-stu-id="71f0f-118">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="71f0f-119">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-119">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 <span data-ttu-id="71f0f-120">提供方法，支援在主機與 CLR 有關組件之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="71f0f-120">Provides methods that support communication between the host and the CLR about assemblies.</span></span>  
  
 [<span data-ttu-id="71f0f-121">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 <span data-ttu-id="71f0f-122">管理 clr，而不是由主應用程式載入的組件清單。</span><span class="sxs-lookup"><span data-stu-id="71f0f-122">Manages a list of assemblies that are loaded by the CLR and not by the host.</span></span>  
  
 [<span data-ttu-id="71f0f-123">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-123">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 <span data-ttu-id="71f0f-124">提供方法讓主應用程式存取，並設定 CLR 的各個層面。</span><span class="sxs-lookup"><span data-stu-id="71f0f-124">Provides methods for the host to gain access to, and configure various aspects of, the CLR.</span></span>  
  
 [<span data-ttu-id="71f0f-125">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 <span data-ttu-id="71f0f-126">提供方法，讓主應用程式能夠與識別項和好記的名稱產生關聯的一組工作。</span><span class="sxs-lookup"><span data-stu-id="71f0f-126">Provides methods that enable a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
 [<span data-ttu-id="71f0f-127">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-127">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 <span data-ttu-id="71f0f-128">提供方法，讓主應用程式設定錯誤報告的自訂堆積傾印。</span><span class="sxs-lookup"><span data-stu-id="71f0f-128">Provides methods that enable the host to configure custom heap dumps for error reporting.</span></span>  
  
 [<span data-ttu-id="71f0f-129">ICLRGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-129">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 <span data-ttu-id="71f0f-130">提供方法，讓主應用程式能夠與 CLR 的記憶體回收系統互動。</span><span class="sxs-lookup"><span data-stu-id="71f0f-130">Provides methods that enable a host to interact with the CLR's garbage collection system.</span></span>  
  
 [<span data-ttu-id="71f0f-131">ICLRHostBindingPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-131">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 <span data-ttu-id="71f0f-132">提供方法讓主應用程式評估和溝通變更組件的原則資訊。</span><span class="sxs-lookup"><span data-stu-id="71f0f-132">Provides methods for the host to evaluate and communicate changes in policy information for assemblies.</span></span>  
  
 [<span data-ttu-id="71f0f-133">ICLRHostProtectionManager 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-133">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 <span data-ttu-id="71f0f-134">可讓主應用程式封鎖特定的 managed 的類別、 方法、 屬性和欄位，無法在部分信任程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="71f0f-134">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
 [<span data-ttu-id="71f0f-135">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-135">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 <span data-ttu-id="71f0f-136">實作回呼方法，可讓主應用程式通知指定的 I/O 要求之狀態的 CLR。</span><span class="sxs-lookup"><span data-stu-id="71f0f-136">Implements a callback method that enables the host to notify the CLR of the status of specified I/O requests.</span></span>  
  
 [<span data-ttu-id="71f0f-137">ICLRMemoryNotificationCallback 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 <span data-ttu-id="71f0f-138">可讓主機使用的方法類似的 Win32 報表記憶體壓力狀況`CreateMemoryResourceNotification`函式。</span><span class="sxs-lookup"><span data-stu-id="71f0f-138">Enables the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
 [<span data-ttu-id="71f0f-139">ICLROnEventManager 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-139">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 <span data-ttu-id="71f0f-140">提供方法，讓主應用程式註冊及取消註冊回呼的 CLR 事件。</span><span class="sxs-lookup"><span data-stu-id="71f0f-140">Provides methods that enable the host to register and unregister callbacks for CLR events.</span></span>  
  
 [<span data-ttu-id="71f0f-141">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 <span data-ttu-id="71f0f-142">提供方法，讓主應用程式指定原則發生失敗和逾時所要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="71f0f-142">Provides methods that enable the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
 [<span data-ttu-id="71f0f-143">ICLRProbingAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-143">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 <span data-ttu-id="71f0f-144">提供方法，讓主應用程式，以取得組件的探查識別使用的組件是 CLR 內部，不需要建立或了解該身分識別的身分識別資訊。</span><span class="sxs-lookup"><span data-stu-id="71f0f-144">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the CLR, without needing to create or understand that identity.</span></span>  
  
 [<span data-ttu-id="71f0f-145">ICLRReferenceAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-145">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)  
 <span data-ttu-id="71f0f-146">提供方法，讓主應用程式管理的檔案或使用組件識別資料，而不需要建立，或了解這些識別的 CLR，內部資料流所參考的組件集。</span><span class="sxs-lookup"><span data-stu-id="71f0f-146">Provides methods that enable the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the CLR, without needing to create or understand those identities.</span></span>  
  
 [<span data-ttu-id="71f0f-147">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-147">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 <span data-ttu-id="71f0f-148">提供功能類似於[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)，設定主控制項介面的其他方法。</span><span class="sxs-lookup"><span data-stu-id="71f0f-148">Provides capabilities similar to [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md), with an additional method to set the host control interface.</span></span>  
  
 [<span data-ttu-id="71f0f-149">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-149">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 <span data-ttu-id="71f0f-150">提供方法來取得要求的工作的相關資訊，並在同步處理實作偵測死結的主機。</span><span class="sxs-lookup"><span data-stu-id="71f0f-150">Provides methods for the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
 [<span data-ttu-id="71f0f-151">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-151">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 <span data-ttu-id="71f0f-152">提供方法，讓主應用程式提出要求的 clr，或提供相關聯的工作有關 clr 的通知。</span><span class="sxs-lookup"><span data-stu-id="71f0f-152">Provides methods that enable the host to make requests of the CLR, or to provide notification to the CLR about the associated task.</span></span>  
  
 [<span data-ttu-id="71f0f-153">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-153">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 <span data-ttu-id="71f0f-154">提供方法，讓主應用程式明確要求 CLR 建立新的工作、 取得目前執行的工作，以及設定地理語言和文化特性的工作。</span><span class="sxs-lookup"><span data-stu-id="71f0f-154">Provides methods that enable the host to request explicitly that the CLR create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
 [<span data-ttu-id="71f0f-155">ICLRValidator 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-155">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)  
 <span data-ttu-id="71f0f-156">提供方法來驗證的可攜式執行檔 (PE) 影像，以及回報驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="71f0f-156">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
 [<span data-ttu-id="71f0f-157">ICorConfiguration 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-157">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)  
 <span data-ttu-id="71f0f-158">提供方法來設定 CLR。</span><span class="sxs-lookup"><span data-stu-id="71f0f-158">Provides methods for configuring the CLR.</span></span>  
  
 [<span data-ttu-id="71f0f-159">ICorThreadpool 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-159">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)  
 <span data-ttu-id="71f0f-160">提供方法來存取在執行緒集區。</span><span class="sxs-lookup"><span data-stu-id="71f0f-160">Provides methods for accessing the thread pool.</span></span>  
  
 [<span data-ttu-id="71f0f-161">IDebuggerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-161">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)  
 <span data-ttu-id="71f0f-162">提供方法來取得有關偵錯服務的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="71f0f-162">Provides methods for obtaining information about the state of the debugging services.</span></span>  
  
 [<span data-ttu-id="71f0f-163">IDebuggerThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-163">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)  
 <span data-ttu-id="71f0f-164">提供方法來通知主機有關封鎖及解除封鎖的執行緒，偵錯服務。</span><span class="sxs-lookup"><span data-stu-id="71f0f-164">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
 [<span data-ttu-id="71f0f-165">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-165">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)  
 <span data-ttu-id="71f0f-166">提供方法來取得記憶體回收系統的相關資訊，以及控制記憶體回收的某些層面。</span><span class="sxs-lookup"><span data-stu-id="71f0f-166">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
 [<span data-ttu-id="71f0f-167">IGCHost2 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-167">IGCHost2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)  
 <span data-ttu-id="71f0f-168">提供[SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)方法可讓主應用程式設定記憶體回收集合區段的大小和記憶體回收系統的層代零的最大值大於`DWORD`。</span><span class="sxs-lookup"><span data-stu-id="71f0f-168">Provides the [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method that enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation zero to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="71f0f-169">IGCHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-169">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)  
 <span data-ttu-id="71f0f-170">提供方法，讓記憶體回收行程，以要求主機若要變更虛擬記憶體的限制。</span><span class="sxs-lookup"><span data-stu-id="71f0f-170">Provides a method that enables the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
 [<span data-ttu-id="71f0f-171">IGCThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-171">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)  
 <span data-ttu-id="71f0f-172">提供方法來參與，否則記憶體回收會封鎖執行緒的排程。</span><span class="sxs-lookup"><span data-stu-id="71f0f-172">Provides methods for participating in the scheduling of threads that would otherwise be blocked for garbage collection.</span></span>  
  
 [<span data-ttu-id="71f0f-173">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-173">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 <span data-ttu-id="71f0f-174">提供方法，讓主應用程式指定的 clr 或主應用程式應該載入的組件集合。</span><span class="sxs-lookup"><span data-stu-id="71f0f-174">Provides methods that enable a host to specify sets of assemblies that should be loaded by the CLR or by the host.</span></span>  
  
 [<span data-ttu-id="71f0f-175">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-175">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 <span data-ttu-id="71f0f-176">提供方法，讓主應用程式載入組件和模組與 CLR 無關。</span><span class="sxs-lookup"><span data-stu-id="71f0f-176">Provides methods that enable a host to load assemblies and modules independently of the CLR.</span></span>  
  
 [<span data-ttu-id="71f0f-177">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-177">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 <span data-ttu-id="71f0f-178">提供主機所實作的自動重設事件的表示法。</span><span class="sxs-lookup"><span data-stu-id="71f0f-178">Provides a representation of an auto-reset event implemented by the host.</span></span>  
  
 [<span data-ttu-id="71f0f-179">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-179">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 <span data-ttu-id="71f0f-180">提供設定載入的組件，以及判斷哪些裝載介面主應用程式支援的方法。</span><span class="sxs-lookup"><span data-stu-id="71f0f-180">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
 [<span data-ttu-id="71f0f-181">IHostCrst 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-181">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 <span data-ttu-id="71f0f-182">可做為主機的關鍵區段的執行緒的表示法。</span><span class="sxs-lookup"><span data-stu-id="71f0f-182">Serves as the host's representation of a critical section for threading.</span></span>  
  
 [<span data-ttu-id="71f0f-183">IHostGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-183">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
 <span data-ttu-id="71f0f-184">提供方法，以通知主機在實作 clr 記憶體回收機制中的事件。</span><span class="sxs-lookup"><span data-stu-id="71f0f-184">Provides methods that notify the host of events in the garbage collection mechanism implemented by the CLR.</span></span>  
  
 [<span data-ttu-id="71f0f-185">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-185">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 <span data-ttu-id="71f0f-186">提供讓 CLR 與 I/O 完成通訊埠提供主機互動的方法。</span><span class="sxs-lookup"><span data-stu-id="71f0f-186">Provides methods that enable the CLR to interact with I/O completion ports provided by the host.</span></span>  
  
 [<span data-ttu-id="71f0f-187">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-187">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 <span data-ttu-id="71f0f-188">提供從透過主機堆積要求更細緻的配置 CLR 的方法。</span><span class="sxs-lookup"><span data-stu-id="71f0f-188">Provides methods for the CLR to request fine-grained allocations from the heap through the host.</span></span>  
  
 [<span data-ttu-id="71f0f-189">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-189">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 <span data-ttu-id="71f0f-190">提供的手動重設事件表示主機的實作。</span><span class="sxs-lookup"><span data-stu-id="71f0f-190">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
 [<span data-ttu-id="71f0f-191">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-191">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 <span data-ttu-id="71f0f-192">提供 CLR 的虛擬記憶體透過建立要求的主機，而不是使用標準 Win32 虛擬記憶體函式的方法。</span><span class="sxs-lookup"><span data-stu-id="71f0f-192">Provides methods for the CLR to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
 [<span data-ttu-id="71f0f-193">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-193">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 <span data-ttu-id="71f0f-194">提供方法，以通知主機在 CLR 中的案例所執行的動作會中止，逾時或失敗。</span><span class="sxs-lookup"><span data-stu-id="71f0f-194">Provides methods that notify the host of the actions the CLR performs in case of aborts, timeouts, or failures.</span></span>  
  
 [<span data-ttu-id="71f0f-195">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-195">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 <span data-ttu-id="71f0f-196">啟用 CLR 的維護主機實作的安全性內容資訊。</span><span class="sxs-lookup"><span data-stu-id="71f0f-196">Enables the CLR to maintain security context information implemented by the host.</span></span>  
  
 [<span data-ttu-id="71f0f-197">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-197">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 <span data-ttu-id="71f0f-198">提供方法，以啟用存取權，以及控制目前執行中執行緒的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="71f0f-198">Provides methods that enable access to, and control over, the security context of the currently executing thread.</span></span>  
  
 [<span data-ttu-id="71f0f-199">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-199">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 <span data-ttu-id="71f0f-200">提供由主機實作的號誌的表示法。</span><span class="sxs-lookup"><span data-stu-id="71f0f-200">Provides a representation of a semaphore implemented by the host.</span></span>  
  
 [<span data-ttu-id="71f0f-201">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-201">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 <span data-ttu-id="71f0f-202">提供 CLR 呼叫主應用程式，而不是使用 Win32 同步處理函式來建立同步處理原始物件的方法。</span><span class="sxs-lookup"><span data-stu-id="71f0f-202">Provides methods for the CLR to create synchronization primitives by calling the host, instead of using the Win32 synchronization functions.</span></span>  
  
 [<span data-ttu-id="71f0f-203">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-203">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 <span data-ttu-id="71f0f-204">提供讓 CLR 與主應用程式管理工作進行通訊的方法。</span><span class="sxs-lookup"><span data-stu-id="71f0f-204">Provides methods that enable the CLR to communicate with the host to manage tasks.</span></span>  
  
 [<span data-ttu-id="71f0f-205">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-205">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 <span data-ttu-id="71f0f-206">提供讓 CLR 工作透過主應用程式，而不是使用標準的作業系統執行緒或 fiber 函式所使用的方法。</span><span class="sxs-lookup"><span data-stu-id="71f0f-206">Provides methods that enable the CLR to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
 [<span data-ttu-id="71f0f-207">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-207">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 <span data-ttu-id="71f0f-208">提供方法來設定執行緒集區和工作項目至執行緒集區佇列的 CLR。</span><span class="sxs-lookup"><span data-stu-id="71f0f-208">Provides methods for the CLR to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
 [<span data-ttu-id="71f0f-209">IManagedObject 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-209">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)  
 <span data-ttu-id="71f0f-210">提供方法來控制受管理的物件。</span><span class="sxs-lookup"><span data-stu-id="71f0f-210">Provides methods for controlling a managed object.</span></span>  
  
 <span data-ttu-id="71f0f-211">「 IObjectHandle"</span><span class="sxs-lookup"><span data-stu-id="71f0f-211">"IObjectHandle"</span></span>  
 <span data-ttu-id="71f0f-212">提供方法，以解除包裝的傳值方式封送處理物件，從間接取值。</span><span class="sxs-lookup"><span data-stu-id="71f0f-212">Provides a method for unwrapping marshal-by-value objects from indirection.</span></span>  
  
 [<span data-ttu-id="71f0f-213">ITypeName 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-213">ITypeName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/itypename-interface.md)  
 <span data-ttu-id="71f0f-214">提供方法來取得型別名稱資訊。</span><span class="sxs-lookup"><span data-stu-id="71f0f-214">Provides methods for obtaining type name information.</span></span> <span data-ttu-id="71f0f-215">（此介面支援.NET Framework 基礎結構的而且不是直接從您的程式碼使用）。</span><span class="sxs-lookup"><span data-stu-id="71f0f-215">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="71f0f-216">ITypeNameBuilder 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-216">ITypeNameBuilder Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/itypenamebuilder-interface.md)  
 <span data-ttu-id="71f0f-217">提供方法來建置型別名稱。</span><span class="sxs-lookup"><span data-stu-id="71f0f-217">Provides methods for building a type name.</span></span> <span data-ttu-id="71f0f-218">（此介面支援.NET Framework 基礎結構的而且不是直接從您的程式碼使用）。</span><span class="sxs-lookup"><span data-stu-id="71f0f-218">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="71f0f-219">ITypeNameFactory 介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-219">ITypeNameFactory Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/itypenamefactory-interface.md)  
 <span data-ttu-id="71f0f-220">提供方法來解構型別名稱。</span><span class="sxs-lookup"><span data-stu-id="71f0f-220">Provides methods for deconstructing a type name.</span></span> <span data-ttu-id="71f0f-221">（此介面支援.NET Framework 基礎結構的而且不是直接從您的程式碼使用）。</span><span class="sxs-lookup"><span data-stu-id="71f0f-221">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 <span data-ttu-id="71f0f-222">「 IValidator"</span><span class="sxs-lookup"><span data-stu-id="71f0f-222">"IValidator"</span></span>  
 <span data-ttu-id="71f0f-223">提供方法來驗證的可攜式執行檔 (PE) 影像，以及回報驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="71f0f-223">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="71f0f-224">相關章節</span><span class="sxs-lookup"><span data-stu-id="71f0f-224">Related Sections</span></span>  
 [<span data-ttu-id="71f0f-225">已被取代的 CLR 裝載介面和 Coclass</span><span class="sxs-lookup"><span data-stu-id="71f0f-225">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="71f0f-226">包含的主題將描述裝載.NET Framework 1.0 和 1.1 版中提供的介面。</span><span class="sxs-lookup"><span data-stu-id="71f0f-226">Contains topics that describe the hosting interfaces provided in the .NET Framework version 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="71f0f-227">.NET Framework 4 和 4.5 中新增的 CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="71f0f-227">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="71f0f-228">包含描述裝載介面中提供的主題[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="71f0f-228">Contains topics that describe the hosting interfaces provided in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>
