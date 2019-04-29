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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789658"
---
# <a name="clr-hosting-interfaces"></a><span data-ttu-id="b0ca3-102">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-102">CLR Hosting Interfaces</span></span>
<span data-ttu-id="b0ca3-103">本節描述 unmanaged 介面主機可用來將 common language runtime (CLR) 整合到他們的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span> <span data-ttu-id="b0ca3-104">此資訊適用於.NET Framework 2.0 版和更新版本。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-104">The information pertains to the .NET Framework version 2.0 and later versions.</span></span> <span data-ttu-id="b0ca3-105">這些介面讓控制許多的更多方面，比在 1.0 和 1.1 版中的執行階段主應用程式，並提供 CLR 與主機的執行模式之間更緊密整合。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-105">These interfaces enable the host to control many more aspects of the runtime than was possible in versions 1.0 and 1.1, and provide much tighter integration between the CLR and the host's execution model.</span></span>  
  
 <span data-ttu-id="b0ca3-106">在.NET Framework 1.0 和 1.1 版中，主控模型會啟用受管理的主機將 CLR 載入處理序，來設定特定的設定，以及接收事件通知。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-106">In the .NET Framework version 1.0 and 1.1, the hosting model enabled an unmanaged host to load the CLR into a process, to configure certain settings, and to receive event notifications.</span></span> <span data-ttu-id="b0ca3-107">不過，在一般情況下，主應用程式和 CLR 獨立執行該程序中。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-107">However, in general, the host and the CLR ran independently in that process.</span></span> <span data-ttu-id="b0ca3-108">在.NET Framework 2.0 版和更新版本中，新的抽象層可讓主機提供許多 Win32 組件中的型別由目前提供的資源和擴充主應用程式可以設定的功能集。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-108">In the .NET Framework version 2.0 and later versions, new layers of abstraction let the host provide many of the resources currently provided by the types in the Win32 assembly, and extend the set of capabilities that the host can configure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b0ca3-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="b0ca3-109">In This Section</span></span>  
 [<span data-ttu-id="b0ca3-110">IActionOnCLREvent 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-110">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 <span data-ttu-id="b0ca3-111">提供針對已註冊的事件執行的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-111">Provides a method that performs a callback for a registered event.</span></span>  
  
 [<span data-ttu-id="b0ca3-112">IApartmentCallback 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-112">IApartmentCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)  
 <span data-ttu-id="b0ca3-113">提供方法來進行回呼的 apartment 中。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-113">Provides methods for making callbacks within an apartment.</span></span>  
  
 [<span data-ttu-id="b0ca3-114">IAppDomainBinding 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-114">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)  
 <span data-ttu-id="b0ca3-115">提供方法來設定執行階段組態。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-115">Provides methods for setting run-time configuration.</span></span>  
  
 [<span data-ttu-id="b0ca3-116">ICatalogServices 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-116">ICatalogServices Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icatalogservices-interface.md)  
 <span data-ttu-id="b0ca3-117">提供方法來編製目錄服務。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-117">Provides methods for cataloging services.</span></span> <span data-ttu-id="b0ca3-118">（此介面支援.NET Framework 基礎結構的而且不是直接從您的程式碼使用）。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-118">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="b0ca3-119">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-119">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 <span data-ttu-id="b0ca3-120">提供方法，支援在主機與 CLR 有關組件之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-120">Provides methods that support communication between the host and the CLR about assemblies.</span></span>  
  
 [<span data-ttu-id="b0ca3-121">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 <span data-ttu-id="b0ca3-122">管理組件載入 clr，而不是由主應用程式的清單。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-122">Manages a list of assemblies that are loaded by the CLR and not by the host.</span></span>  
  
 [<span data-ttu-id="b0ca3-123">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-123">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 <span data-ttu-id="b0ca3-124">提供方法讓主應用程式取得存取權，以及設定 CLR 的各個層面。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-124">Provides methods for the host to gain access to, and configure various aspects of, the CLR.</span></span>  
  
 [<span data-ttu-id="b0ca3-125">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 <span data-ttu-id="b0ca3-126">提供方法，讓主應用程式相關聯的一組工作識別碼和易記名稱。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-126">Provides methods that enable a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
 [<span data-ttu-id="b0ca3-127">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-127">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 <span data-ttu-id="b0ca3-128">提供方法，讓主應用程式設定錯誤報告的自訂堆積傾印。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-128">Provides methods that enable the host to configure custom heap dumps for error reporting.</span></span>  
  
 [<span data-ttu-id="b0ca3-129">ICLRGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-129">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 <span data-ttu-id="b0ca3-130">提供方法，讓主應用程式能夠與 CLR 的記憶體回收系統互動。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-130">Provides methods that enable a host to interact with the CLR's garbage collection system.</span></span>  
  
 [<span data-ttu-id="b0ca3-131">ICLRHostBindingPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-131">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 <span data-ttu-id="b0ca3-132">提供方法供主機用來評估，並傳達變更組件的原則資訊。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-132">Provides methods for the host to evaluate and communicate changes in policy information for assemblies.</span></span>  
  
 [<span data-ttu-id="b0ca3-133">ICLRHostProtectionManager 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-133">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 <span data-ttu-id="b0ca3-134">可讓主應用程式封鎖特定的 managed 的類別、 方法、 屬性和欄位，無法在部分信任程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-134">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
 [<span data-ttu-id="b0ca3-135">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-135">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 <span data-ttu-id="b0ca3-136">實作回呼方法，可讓主應用程式向 CLR 通知將指定的 I/O 要求的狀態。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-136">Implements a callback method that enables the host to notify the CLR of the status of specified I/O requests.</span></span>  
  
 [<span data-ttu-id="b0ca3-137">ICLRMemoryNotificationCallback 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 <span data-ttu-id="b0ca3-138">可讓主應用程式使用的 Win32 類似的方法報告記憶體壓力狀況`CreateMemoryResourceNotification`函式。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-138">Enables the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
 [<span data-ttu-id="b0ca3-139">ICLROnEventManager 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-139">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 <span data-ttu-id="b0ca3-140">提供可讓主應用程式註冊和取消註冊 CLR 事件的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-140">Provides methods that enable the host to register and unregister callbacks for CLR events.</span></span>  
  
 [<span data-ttu-id="b0ca3-141">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 <span data-ttu-id="b0ca3-142">提供方法，讓主應用程式指定原則發生失敗和逾時所要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-142">Provides methods that enable the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
 [<span data-ttu-id="b0ca3-143">ICLRProbingAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-143">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 <span data-ttu-id="b0ca3-144">提供方法，讓主應用程式，以取得組件探查的身分識別使用而不需要建立，或了解該身分識別是 CLR 中，內部的組件的身分識別資訊。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-144">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the CLR, without needing to create or understand that identity.</span></span>  
  
 [<span data-ttu-id="b0ca3-145">ICLRReferenceAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-145">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)  
 <span data-ttu-id="b0ca3-146">提供方法，讓主應用程式管理的檔案或組件的身分識別資料，而不需要建立，或了解這些身分識別是 CLR 中，內部的資料流所參考的組件集。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-146">Provides methods that enable the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the CLR, without needing to create or understand those identities.</span></span>  
  
 [<span data-ttu-id="b0ca3-147">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-147">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 <span data-ttu-id="b0ca3-148">提供功能類似於[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)，以其他方法設定的主控件控制介面。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-148">Provides capabilities similar to [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md), with an additional method to set the host control interface.</span></span>  
  
 [<span data-ttu-id="b0ca3-149">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-149">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 <span data-ttu-id="b0ca3-150">提供方法來取得要求的工作的相關資訊，及偵測死結的同步處理實作中的主機。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-150">Provides methods for the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
 [<span data-ttu-id="b0ca3-151">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-151">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 <span data-ttu-id="b0ca3-152">提供方法，讓主應用程式提出要求的 clr 中，或以用於 CLR 有關相關聯的工作提供通知。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-152">Provides methods that enable the host to make requests of the CLR, or to provide notification to the CLR about the associated task.</span></span>  
  
 [<span data-ttu-id="b0ca3-153">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-153">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 <span data-ttu-id="b0ca3-154">提供方法，讓主應用程式明確要求 CLR 建立新的工作、 取得目前執行的工作，以及設定地理的語言和文化特性的工作。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-154">Provides methods that enable the host to request explicitly that the CLR create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
 [<span data-ttu-id="b0ca3-155">ICLRValidator 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-155">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)  
 <span data-ttu-id="b0ca3-156">提供方法來驗證的可攜式執行檔 (PE) 映像和報告驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-156">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
 [<span data-ttu-id="b0ca3-157">ICorConfiguration 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-157">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)  
 <span data-ttu-id="b0ca3-158">提供用於設定 CLR 方法。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-158">Provides methods for configuring the CLR.</span></span>  
  
 [<span data-ttu-id="b0ca3-159">ICorThreadpool 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-159">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)  
 <span data-ttu-id="b0ca3-160">提供方法來存取執行緒集區。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-160">Provides methods for accessing the thread pool.</span></span>  
  
 [<span data-ttu-id="b0ca3-161">IDebuggerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-161">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)  
 <span data-ttu-id="b0ca3-162">提供方法來取得有關偵錯服務的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-162">Provides methods for obtaining information about the state of the debugging services.</span></span>  
  
 [<span data-ttu-id="b0ca3-163">IDebuggerThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-163">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)  
 <span data-ttu-id="b0ca3-164">提供方法來通知主機有關封鎖和解除封鎖執行緒的偵錯服務。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-164">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
 [<span data-ttu-id="b0ca3-165">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-165">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)  
 <span data-ttu-id="b0ca3-166">提供方法來取得記憶體回收系統的相關資訊，以及控制記憶體回收的某些層面。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-166">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
 [<span data-ttu-id="b0ca3-167">IGCHost2 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-167">IGCHost2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)  
 <span data-ttu-id="b0ca3-168">提供[SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)方法，讓主應用程式來設定記憶體回收集合區段的大小和記憶體回收系統的層代 0 的最大值大於`DWORD`。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-168">Provides the [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method that enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation zero to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="b0ca3-169">IGCHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-169">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)  
 <span data-ttu-id="b0ca3-170">提供方法，以允許要求的主機，若要變更的虛擬記憶體限制的記憶體回收行程。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-170">Provides a method that enables the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
 [<span data-ttu-id="b0ca3-171">IGCThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-171">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)  
 <span data-ttu-id="b0ca3-172">提供方法來參與，否則記憶體回收會封鎖執行緒的排程。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-172">Provides methods for participating in the scheduling of threads that would otherwise be blocked for garbage collection.</span></span>  
  
 [<span data-ttu-id="b0ca3-173">IHostAssemblyManager 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-173">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 <span data-ttu-id="b0ca3-174">提供方法，讓主應用程式指定的 CLR 或由主機載入的組件集合。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-174">Provides methods that enable a host to specify sets of assemblies that should be loaded by the CLR or by the host.</span></span>  
  
 [<span data-ttu-id="b0ca3-175">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-175">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 <span data-ttu-id="b0ca3-176">提供方法，讓主應用程式載入組件和模組與 CLR 無關。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-176">Provides methods that enable a host to load assemblies and modules independently of the CLR.</span></span>  
  
 [<span data-ttu-id="b0ca3-177">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-177">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 <span data-ttu-id="b0ca3-178">提供由主機實作的自動重設事件的表示法。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-178">Provides a representation of an auto-reset event implemented by the host.</span></span>  
  
 [<span data-ttu-id="b0ca3-179">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-179">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 <span data-ttu-id="b0ca3-180">提供對於設定載入的組件，以及判斷哪些裝載介面主應用程式支援的方法。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-180">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
 [<span data-ttu-id="b0ca3-181">IHostCrst 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-181">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 <span data-ttu-id="b0ca3-182">可做為執行緒的關鍵區段之主機的表示法。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-182">Serves as the host's representation of a critical section for threading.</span></span>  
  
 [<span data-ttu-id="b0ca3-183">IHostGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-183">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
 <span data-ttu-id="b0ca3-184">提供方法，以通知主機實作的 CLR 記憶體回收機制中的事件。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-184">Provides methods that notify the host of events in the garbage collection mechanism implemented by the CLR.</span></span>  
  
 [<span data-ttu-id="b0ca3-185">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-185">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 <span data-ttu-id="b0ca3-186">提供讓 CLR 主機所提供的 I/O 完成連接埠與互動的方法。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-186">Provides methods that enable the CLR to interact with I/O completion ports provided by the host.</span></span>  
  
 [<span data-ttu-id="b0ca3-187">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-187">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 <span data-ttu-id="b0ca3-188">提供 CLR 從透過主控件堆積要求更細緻的配置方法。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-188">Provides methods for the CLR to request fine-grained allocations from the heap through the host.</span></span>  
  
 [<span data-ttu-id="b0ca3-189">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-189">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 <span data-ttu-id="b0ca3-190">提供手動重設事件的表示主機的實作。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-190">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
 [<span data-ttu-id="b0ca3-191">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-191">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 <span data-ttu-id="b0ca3-192">提供 CLR 進行透過主應用程式，而不是使用標準的 Win32 虛擬記憶體函式的虛擬記憶體要求的方法。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-192">Provides methods for the CLR to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
 [<span data-ttu-id="b0ca3-193">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-193">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 <span data-ttu-id="b0ca3-194">提供方法，通知主應用程式中的案例中的 CLR 執行的動作會中止，逾時或失敗。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-194">Provides methods that notify the host of the actions the CLR performs in case of aborts, timeouts, or failures.</span></span>  
  
 [<span data-ttu-id="b0ca3-195">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-195">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 <span data-ttu-id="b0ca3-196">可讓 CLR 維護主機所實作的安全性內容資訊。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-196">Enables the CLR to maintain security context information implemented by the host.</span></span>  
  
 [<span data-ttu-id="b0ca3-197">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-197">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 <span data-ttu-id="b0ca3-198">提供方法，以啟用存取權，以及控制目前執行中執行緒的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-198">Provides methods that enable access to, and control over, the security context of the currently executing thread.</span></span>  
  
 [<span data-ttu-id="b0ca3-199">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-199">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 <span data-ttu-id="b0ca3-200">提供由主機實作的號誌的表示法。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-200">Provides a representation of a semaphore implemented by the host.</span></span>  
  
 [<span data-ttu-id="b0ca3-201">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-201">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 <span data-ttu-id="b0ca3-202">提供 CLR 呼叫主應用程式，而不是使用 Win32 同步處理函式來建立同步處理原始物件的方法。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-202">Provides methods for the CLR to create synchronization primitives by calling the host, instead of using the Win32 synchronization functions.</span></span>  
  
 [<span data-ttu-id="b0ca3-203">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-203">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 <span data-ttu-id="b0ca3-204">提供讓 CLR 與主應用程式管理工作進行通訊的方法。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-204">Provides methods that enable the CLR to communicate with the host to manage tasks.</span></span>  
  
 [<span data-ttu-id="b0ca3-205">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-205">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 <span data-ttu-id="b0ca3-206">提供啟用 CLR，才能透過主應用程式，而不是使用標準的作業系統執行緒或 fiber 函式的工作使用的方法。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-206">Provides methods that enable the CLR to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
 [<span data-ttu-id="b0ca3-207">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-207">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 <span data-ttu-id="b0ca3-208">提供 clr 來設定執行緒集區，以及執行緒集區的工作項目佇列的方法。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-208">Provides methods for the CLR to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
 [<span data-ttu-id="b0ca3-209">IManagedObject 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-209">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)  
 <span data-ttu-id="b0ca3-210">提供方法來控制受管理的物件。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-210">Provides methods for controlling a managed object.</span></span>  
  
 <span data-ttu-id="b0ca3-211">"IObjectHandle"</span><span class="sxs-lookup"><span data-stu-id="b0ca3-211">"IObjectHandle"</span></span>  
 <span data-ttu-id="b0ca3-212">提供從間接取值的解除包裝傳值方式封送處理物件的方法。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-212">Provides a method for unwrapping marshal-by-value objects from indirection.</span></span>  
  
 [<span data-ttu-id="b0ca3-213">ITypeName 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-213">ITypeName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/itypename-interface.md)  
 <span data-ttu-id="b0ca3-214">提供方法來取得型別名稱資訊。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-214">Provides methods for obtaining type name information.</span></span> <span data-ttu-id="b0ca3-215">（此介面支援.NET Framework 基礎結構的而且不是直接從您的程式碼使用）。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-215">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="b0ca3-216">ITypeNameBuilder 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-216">ITypeNameBuilder Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/itypenamebuilder-interface.md)  
 <span data-ttu-id="b0ca3-217">提供方法來建置型別名稱。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-217">Provides methods for building a type name.</span></span> <span data-ttu-id="b0ca3-218">（此介面支援.NET Framework 基礎結構的而且不是直接從您的程式碼使用）。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-218">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="b0ca3-219">ITypeNameFactory 介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-219">ITypeNameFactory Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/itypenamefactory-interface.md)  
 <span data-ttu-id="b0ca3-220">提供方法來解構類型名稱。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-220">Provides methods for deconstructing a type name.</span></span> <span data-ttu-id="b0ca3-221">（此介面支援.NET Framework 基礎結構的而且不是直接從您的程式碼使用）。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-221">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 <span data-ttu-id="b0ca3-222">「 IValidator"</span><span class="sxs-lookup"><span data-stu-id="b0ca3-222">"IValidator"</span></span>  
 <span data-ttu-id="b0ca3-223">提供方法來驗證的可攜式執行檔 (PE) 映像和報告驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-223">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b0ca3-224">相關章節</span><span class="sxs-lookup"><span data-stu-id="b0ca3-224">Related Sections</span></span>  
 [<span data-ttu-id="b0ca3-225">已被取代的 CLR 裝載介面和 Coclass</span><span class="sxs-lookup"><span data-stu-id="b0ca3-225">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="b0ca3-226">包含說明.NET Framework 1.0 和 1.1 版中提供裝載介面主題。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-226">Contains topics that describe the hosting interfaces provided in the .NET Framework version 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="b0ca3-227">.NET Framework 4 和 4.5 中新增的 CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="b0ca3-227">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="b0ca3-228">包含的主題將描述中所提供的裝載介面[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0ca3-228">Contains topics that describe the hosting interfaces provided in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>
