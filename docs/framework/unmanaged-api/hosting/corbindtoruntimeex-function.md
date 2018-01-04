---
title: "CorBindToRuntimeEx 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToRuntimeEx
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CorBindToRuntimeEx
helpviewer_keywords: CorBindToRuntimeEx function [.NET Framework hosting]
ms.assetid: aae9fb17-5d01-41da-9773-1b5b5b642d81
topic_type: apiref
caps.latest.revision: "41"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c0080e5a01c8e856c2862182ba06096fdc9385c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="corbindtoruntimeex-function"></a><span data-ttu-id="b4667-102">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="b4667-102">CorBindToRuntimeEx Function</span></span>
<span data-ttu-id="b4667-103">可讓 unmanaged 的主機將 common language runtime (CLR) 載入處理序。</span><span class="sxs-lookup"><span data-stu-id="b4667-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span> <span data-ttu-id="b4667-104">[CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)和`CorBindToRuntimeEx`函式會執行相同的作業，但`CorBindToRuntimeEx`函式可讓您設定旗標來指定 CLR 的行為。</span><span class="sxs-lookup"><span data-stu-id="b4667-104">The [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) and `CorBindToRuntimeEx` functions perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 <span data-ttu-id="b4667-105">此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b4667-105">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
 <span data-ttu-id="b4667-106">此函數會採用一組參數，可讓主應用程式能夠執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="b4667-106">This function takes a set of parameters that allow a host to do the following:</span></span>  
  
-   <span data-ttu-id="b4667-107">指定將載入的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="b4667-107">Specify the version of the runtime that will be loaded.</span></span>  
  
-   <span data-ttu-id="b4667-108">指出是否應該載入的伺服器或工作站的組建。</span><span class="sxs-lookup"><span data-stu-id="b4667-108">Indicate whether the server or workstation build should be loaded.</span></span>  
  
-   <span data-ttu-id="b4667-109">控制是否進行並行記憶體回收或非並行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="b4667-109">Control whether concurrent garbage collection or non-concurrent garbage collection is done.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4667-110">執行 WOW64 應用程式中不支援並行記憶體回收 x86 實作 （之前稱為 ia-64） 的 Intel Itanium 架構的 64 位元系統上的模擬器。</span><span class="sxs-lookup"><span data-stu-id="b4667-110">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="b4667-111">如需使用 WOW64 在 64 位元 Windows 系統上的詳細資訊，請參閱[執行 32 位元應用程式](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx)。</span><span class="sxs-lookup"><span data-stu-id="b4667-111">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).</span></span>  
  
-   <span data-ttu-id="b4667-112">控制是否以定義域中性方式載入組件。</span><span class="sxs-lookup"><span data-stu-id="b4667-112">Control whether assemblies are loaded as domain-neutral.</span></span>  
  
-   <span data-ttu-id="b4667-113">取得的介面指標[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ，可以用來設定其他選項來啟動之前設定的 CLR 執行個體。</span><span class="sxs-lookup"><span data-stu-id="b4667-113">Obtain an interface pointer to an [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) that can be used to set additional options for configuring an instance of the CLR before it is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4667-114">語法</span><span class="sxs-lookup"><span data-stu-id="b4667-114">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntimeEx (  
    [in]  LPCWSTR      pwszVersion,   
    [in]  LPCWSTR      pwszBuildFlavor,   
    [in]  DWORD        startupFlags,   
    [in]  REFCLSID     rclsid,   
    [in]  REFIID       riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4667-115">參數</span><span class="sxs-lookup"><span data-stu-id="b4667-115">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="b4667-116">[in]您要載入描述的 CLR 版本字串。</span><span class="sxs-lookup"><span data-stu-id="b4667-116">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="b4667-117">在.NET Framework 的版本號碼是由以句號分隔的四個部分所組成： *major.minor.build.revision*。</span><span class="sxs-lookup"><span data-stu-id="b4667-117">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="b4667-118">當做字串傳遞給`pwszVersion`開頭必須是字元"v"後面接著的版本號碼 (例如，"v1.0.1529") 的前三個部分。</span><span class="sxs-lookup"><span data-stu-id="b4667-118">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="b4667-119">某些版本的 CLR 會以指定與舊版 CLR 相容的原則陳述式安裝。</span><span class="sxs-lookup"><span data-stu-id="b4667-119">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="b4667-120">根據預設，啟動填充碼會評估`pwszVersion`針對原則陳述式和載入執行階段的最新版本，是與所要求的版本相容。</span><span class="sxs-lookup"><span data-stu-id="b4667-120">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="b4667-121">主機可以強制略過原則評估並載入中指定的確切版本填充碼`pwszVersion`依值傳遞`STARTUP_LOADER_SAFEMODE`如`startupFlags`參數，如下所述。</span><span class="sxs-lookup"><span data-stu-id="b4667-121">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `startupFlags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="b4667-122">如果呼叫端指定為 null `pwszVersion`，`CorBindToRuntimeEx`識別其版本號碼低於.NET Framework 4 執行階段，並載入最新版執行階段的設定已安裝的執行階段中的集合。</span><span class="sxs-lookup"><span data-stu-id="b4667-122">If the caller specifies null for `pwszVersion`, `CorBindToRuntimeEx` identifies the set of installed runtimes whose version numbers are lower than the .NET Framework 4 runtime, and loads the latest version of the runtime from that set.</span></span> <span data-ttu-id="b4667-123">如果已不安裝任何舊版，它不會載入.NET Framework 4 或更新版本，而失敗時。</span><span class="sxs-lookup"><span data-stu-id="b4667-123">It won't load the .NET Framework 4 or later, and fails if no earlier version is installed.</span></span> <span data-ttu-id="b4667-124">請注意，傳遞 null 會給予主機載入的執行階段版本的任何控制項。</span><span class="sxs-lookup"><span data-stu-id="b4667-124">Note that passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="b4667-125">雖然在某些情況下可能適合使用這種方法，但強烈建議主應用程式，提供要載入的特定版本。</span><span class="sxs-lookup"><span data-stu-id="b4667-125">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="b4667-126">[in]字串，指定是否要在伺服器或工作站組建的 clr 載入。</span><span class="sxs-lookup"><span data-stu-id="b4667-126">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="b4667-127">有效值為 `svr` 和 `wks`。</span><span class="sxs-lookup"><span data-stu-id="b4667-127">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="b4667-128">伺服器組建已最佳化，可利用多個處理器的記憶體回收，並工作站組建最適合用於單一處理器電腦上執行的用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="b4667-128">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="b4667-129">如果`pwszBuildFlavor`設為 null，工作站組建已載入。</span><span class="sxs-lookup"><span data-stu-id="b4667-129">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="b4667-130">單一處理器電腦上執行時，會一律載入工作站組建，即使`pwszBuildFlavor`設`svr`。</span><span class="sxs-lookup"><span data-stu-id="b4667-130">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="b4667-131">不過，如果`pwszBuildFlavor`設為`svr`並行記憶體回收是指定 (請參閱描述`startupFlags`參數)，會載入伺服器組建。</span><span class="sxs-lookup"><span data-stu-id="b4667-131">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="b4667-132">[in]值的組合[STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="b4667-132">[in] A combination of values of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span> <span data-ttu-id="b4667-133">這些旗標控制並行記憶體回收、 定義域中性程式碼，以及行為`pwszVersion`參數。</span><span class="sxs-lookup"><span data-stu-id="b4667-133">These flags control concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="b4667-134">預設值是單一網域，如果沒有旗標設定。</span><span class="sxs-lookup"><span data-stu-id="b4667-134">The default is single domain if no flag is set.</span></span> <span data-ttu-id="b4667-135">下列是有效值：</span><span class="sxs-lookup"><span data-stu-id="b4667-135">The following values are valid:</span></span>  
  
-   `STARTUP_CONCURRENT_GC`  
  
-   `STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`  
  
-   `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`  
  
-   `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`  
  
-   `STARTUP_LOADER_SAFEMODE`  
  
-   `STARTUP_LEGACY_IMPERSONATION`  
  
-   `STARTUP_LOADER_SETPREFERENCE`  
  
-   `STARTUP_SERVER_GC`  
  
-   `STARTUP_HOARD_GC_VM`  
  
-   `STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`  
  
-   `STARTUP_LEGACY_IMPERSONATION`  
  
-   `STARTUP_DISABLE_COMMITTHREADSTACK`  
  
-   `STARTUP_ALWAYSFLOW_IMPERSONATION`  
  
 <span data-ttu-id="b4667-136">如需這些旗標的描述，請參閱[STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="b4667-136">For descriptions of these flags, see the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="b4667-137">[in]`CLSID`實作的 coclass 的[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)或[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="b4667-137">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="b4667-138">支援的值為 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="b4667-138">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="b4667-139">[in]`IID`所要求介面從`rclsid`。</span><span class="sxs-lookup"><span data-stu-id="b4667-139">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="b4667-140">支援的值為 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="b4667-140">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="b4667-141">[out]傳回的介面指標`riid`。</span><span class="sxs-lookup"><span data-stu-id="b4667-141">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4667-142">備註</span><span class="sxs-lookup"><span data-stu-id="b4667-142">Remarks</span></span>  
 <span data-ttu-id="b4667-143">如果`pwszVersion`指定不存在，執行階段版本`CorBindToRuntimeEx`傳回 CLR_E_SHIM_RUNTIMELOAD HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="b4667-143">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="b4667-144">執行內容和流程的 Windows 身分識別</span><span class="sxs-lookup"><span data-stu-id="b4667-144">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="b4667-145">在 CLR 的第 1 版中<xref:System.Security.Principal.WindowsIdentity>物件不會流動到非同步的點，例如新的執行緒、 執行緒集區或計時器回呼。</span><span class="sxs-lookup"><span data-stu-id="b4667-145">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="b4667-146">在 CLR 2.0 版<xref:System.Threading.ExecutionContext>物件包裝目前執行中執行緒的一些資訊及流向它，跨越任何非同步的點，但不是會跨應用程式定義域界限。</span><span class="sxs-lookup"><span data-stu-id="b4667-146">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="b4667-147">同樣地，<xref:System.Security.Principal.WindowsIdentity>物件也會透過非同步的任何時間點流動。</span><span class="sxs-lookup"><span data-stu-id="b4667-147">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="b4667-148">因此，目前的模擬執行緒，如果有的話，流動。</span><span class="sxs-lookup"><span data-stu-id="b4667-148">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="b4667-149">您可以修改流程有兩種：</span><span class="sxs-lookup"><span data-stu-id="b4667-149">You can alter the flow in two ways:</span></span>  
  
1.  <span data-ttu-id="b4667-150">藉由修改<xref:System.Threading.ExecutionContext>設定，以隱藏每個執行緒為基礎的流程 (請參閱<xref:System.Threading.ExecutionContext.SuppressFlow%2A>， <xref:System.Security.SecurityContext.SuppressFlow%2A>，和<xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A>方法)。</span><span class="sxs-lookup"><span data-stu-id="b4667-150">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2.  <span data-ttu-id="b4667-151">由處理程序的預設模式變更為 「 第 1 版的相容性模式，其中<xref:System.Security.Principal.WindowsIdentity>物件不會流動跨越任何非同步的點，不論<xref:System.Threading.ExecutionContext>目前執行緒上的設定。</span><span class="sxs-lookup"><span data-stu-id="b4667-151">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="b4667-152">如何變更預設的模式取決於是否載入 CLR 使用 managed 可執行檔或 unmanaged 裝載介面：</span><span class="sxs-lookup"><span data-stu-id="b4667-152">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1.  <span data-ttu-id="b4667-153">針對受管理的可執行檔，您必須設定`enabled`屬性[ \<legacyImpersonationPolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)元素`true`。</span><span class="sxs-lookup"><span data-stu-id="b4667-153">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2.  <span data-ttu-id="b4667-154">Unmanaged 裝載介面，設定`STARTUP_LEGACY_IMPERSONATION`加上旗標`startupFlags`參數呼叫時`CorBindToRuntimeEx`函式。</span><span class="sxs-lookup"><span data-stu-id="b4667-154">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `startupFlags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="b4667-155">第 1 版相容性模式適用於整個程序和程序中的所有應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="b4667-155">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4667-156">需求</span><span class="sxs-lookup"><span data-stu-id="b4667-156">Requirements</span></span>  
 <span data-ttu-id="b4667-157">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b4667-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4667-158">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b4667-158">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b4667-159">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b4667-159">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b4667-160">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4667-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4667-161">請參閱</span><span class="sxs-lookup"><span data-stu-id="b4667-161">See Also</span></span>  
 [<span data-ttu-id="b4667-162">CorBindToCurrentRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="b4667-162">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="b4667-163">CorBindToRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="b4667-163">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [<span data-ttu-id="b4667-164">CorBindToRuntimeByCfg 函式</span><span class="sxs-lookup"><span data-stu-id="b4667-164">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="b4667-165">CorBindToRuntimeHost 函式</span><span class="sxs-lookup"><span data-stu-id="b4667-165">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [<span data-ttu-id="b4667-166">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="b4667-166">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="b4667-167">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="b4667-167">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
