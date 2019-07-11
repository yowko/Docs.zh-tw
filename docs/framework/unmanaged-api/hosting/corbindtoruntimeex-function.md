---
title: CorBindToRuntimeEx 函式
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeEx
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeEx
helpviewer_keywords:
- CorBindToRuntimeEx function [.NET Framework hosting]
ms.assetid: aae9fb17-5d01-41da-9773-1b5b5b642d81
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84e4c70c973fb19be6800d2cbaf76ea137f58b28
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767950"
---
# <a name="corbindtoruntimeex-function"></a><span data-ttu-id="2955d-102">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="2955d-102">CorBindToRuntimeEx Function</span></span>
<span data-ttu-id="2955d-103">可讓 unmanaged 主應用程式將 common language runtime (CLR) 載入程序。</span><span class="sxs-lookup"><span data-stu-id="2955d-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span> <span data-ttu-id="2955d-104">[CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)並`CorBindToRuntimeEx`函式會執行相同的作業，但`CorBindToRuntimeEx`函式可讓您設定旗標指定 CLR 的行為。</span><span class="sxs-lookup"><span data-stu-id="2955d-104">The [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) and `CorBindToRuntimeEx` functions perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 <span data-ttu-id="2955d-105">此函式已被取代，在.NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="2955d-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="2955d-106">此函數會採用一組參數，可讓主應用程式執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="2955d-106">This function takes a set of parameters that allow a host to do the following:</span></span>  
  
- <span data-ttu-id="2955d-107">指定將載入的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="2955d-107">Specify the version of the runtime that will be loaded.</span></span>  
  
- <span data-ttu-id="2955d-108">指出是否應該載入的伺服器或工作站的組建。</span><span class="sxs-lookup"><span data-stu-id="2955d-108">Indicate whether the server or workstation build should be loaded.</span></span>  
  
- <span data-ttu-id="2955d-109">控制是否進行並行記憶體回收或非並行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="2955d-109">Control whether concurrent garbage collection or non-concurrent garbage collection is done.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2955d-110">執行 WOW64 的應用程式中不支援並行記憶體回收 x86 實作 Intel Itanium 架構 （先前稱為 IA-64） 的 64 位元系統上的模擬器。</span><span class="sxs-lookup"><span data-stu-id="2955d-110">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="2955d-111">如需在 64 位元 Windows 系統上使用 WOW64 的詳細資訊，請參閱[執行的 32 位元應用程式](/windows/desktop/WinProg64/running-32-bit-applications)。</span><span class="sxs-lookup"><span data-stu-id="2955d-111">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
- <span data-ttu-id="2955d-112">控制是否以定義域中性方式載入組件。</span><span class="sxs-lookup"><span data-stu-id="2955d-112">Control whether assemblies are loaded as domain-neutral.</span></span>  
  
- <span data-ttu-id="2955d-113">取得的介面指標[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ，可以用來設定其他選項來啟動之前設定的 CLR 執行個體。</span><span class="sxs-lookup"><span data-stu-id="2955d-113">Obtain an interface pointer to an [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) that can be used to set additional options for configuring an instance of the CLR before it is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2955d-114">語法</span><span class="sxs-lookup"><span data-stu-id="2955d-114">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntimeEx (  
    [in]  LPCWSTR      pwszVersion,   
    [in]  LPCWSTR      pwszBuildFlavor,   
    [in]  DWORD        startupFlags,   
    [in]  REFCLSID     rclsid,   
    [in]  REFIID       riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2955d-115">參數</span><span class="sxs-lookup"><span data-stu-id="2955d-115">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="2955d-116">[in]想要載入的字串，描述的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="2955d-116">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="2955d-117">在.NET Framework 的版本號碼是由以句點分隔的四個部分所組成： *major.minor.build.revision*。</span><span class="sxs-lookup"><span data-stu-id="2955d-117">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="2955d-118">將字串傳遞為`pwszVersion`不可使用字元"v"後面接著的版本號碼 (例如，"v1.0.1529 」) 的前三個部分。</span><span class="sxs-lookup"><span data-stu-id="2955d-118">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="2955d-119">某些版本的 CLR 會以指定與舊版的 clr 相容的原則陳述式安裝。</span><span class="sxs-lookup"><span data-stu-id="2955d-119">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="2955d-120">根據預設，啟動填充碼會評估`pwszVersion`針對原則陳述式並載入最新版本的執行階段，是與所要求的版本相容。</span><span class="sxs-lookup"><span data-stu-id="2955d-120">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="2955d-121">主機可以強制填充碼略過原則評估，並載入指定的確切版本`pwszVersion`傳遞的值，藉以`STARTUP_LOADER_SAFEMODE`如`startupFlags`參數，如下所述。</span><span class="sxs-lookup"><span data-stu-id="2955d-121">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `startupFlags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="2955d-122">如果呼叫端指定為 null `pwszVersion`，`CorBindToRuntimeEx`識別已安裝執行階段，其版本號碼低於.NET Framework 4 執行階段，並從該集合載入執行階段的最新版本的集合。</span><span class="sxs-lookup"><span data-stu-id="2955d-122">If the caller specifies null for `pwszVersion`, `CorBindToRuntimeEx` identifies the set of installed runtimes whose version numbers are lower than the .NET Framework 4 runtime, and loads the latest version of the runtime from that set.</span></span> <span data-ttu-id="2955d-123">如果安裝沒有較早的版本，它就不會載入.NET Framework 4 或更新版本，並會失敗。</span><span class="sxs-lookup"><span data-stu-id="2955d-123">It won't load the .NET Framework 4 or later, and fails if no earlier version is installed.</span></span> <span data-ttu-id="2955d-124">請注意，將 null 傳遞提供主機載入執行階段版本的任何控制項。</span><span class="sxs-lookup"><span data-stu-id="2955d-124">Note that passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="2955d-125">雖然這種方法可能適用於某些情況下，強烈建議主應用程式，提供要載入的特定版本。</span><span class="sxs-lookup"><span data-stu-id="2955d-125">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="2955d-126">[in]字串，指定是否要載入的伺服器或工作站組建的 clr。</span><span class="sxs-lookup"><span data-stu-id="2955d-126">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="2955d-127">有效值為 `svr` 和 `wks`。</span><span class="sxs-lookup"><span data-stu-id="2955d-127">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="2955d-128">伺服器組建已最佳化，可利用多個處理器的記憶體回收，以及工作站建置適用於單一處理器電腦上執行的用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="2955d-128">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="2955d-129">如果`pwszBuildFlavor`設為 null，工作站組建已載入。</span><span class="sxs-lookup"><span data-stu-id="2955d-129">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="2955d-130">單一處理器電腦上執行時，會一律載入工作站組建，即使`pwszBuildFlavor`設為`svr`。</span><span class="sxs-lookup"><span data-stu-id="2955d-130">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="2955d-131">不過，如果`pwszBuildFlavor`設為`svr`以及指定並行記憶體回收 (請參閱說明，`startupFlags`參數)，會載入伺服器組建。</span><span class="sxs-lookup"><span data-stu-id="2955d-131">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="2955d-132">[in]值的組合[STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="2955d-132">[in] A combination of values of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span> <span data-ttu-id="2955d-133">這些旗標控制並行記憶體回收、 定義域中性程式碼，以及行為`pwszVersion`參數。</span><span class="sxs-lookup"><span data-stu-id="2955d-133">These flags control concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="2955d-134">如果沒有旗標設定，則預設會為單一網域。</span><span class="sxs-lookup"><span data-stu-id="2955d-134">The default is single domain if no flag is set.</span></span> <span data-ttu-id="2955d-135">下列是有效值：</span><span class="sxs-lookup"><span data-stu-id="2955d-135">The following values are valid:</span></span>  
  
- `STARTUP_CONCURRENT_GC`  
  
- `STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`  
  
- `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`  
  
- `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`  
  
- `STARTUP_LOADER_SAFEMODE`  
  
- `STARTUP_LEGACY_IMPERSONATION`  
  
- `STARTUP_LOADER_SETPREFERENCE`  
  
- `STARTUP_SERVER_GC`  
  
- `STARTUP_HOARD_GC_VM`  
  
- `STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`  
  
- `STARTUP_LEGACY_IMPERSONATION`  
  
- `STARTUP_DISABLE_COMMITTHREADSTACK`  
  
- `STARTUP_ALWAYSFLOW_IMPERSONATION`  
  
 <span data-ttu-id="2955d-136">如需這些旗標的描述，請參閱 < [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="2955d-136">For descriptions of these flags, see the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="2955d-137">[in]`CLSID`的實作的 coclass [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)或[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="2955d-137">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="2955d-138">支援的值為 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="2955d-138">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="2955d-139">[in]`IID`的要求的介面，從`rclsid`。</span><span class="sxs-lookup"><span data-stu-id="2955d-139">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="2955d-140">支援的值為 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="2955d-140">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="2955d-141">[out]若要傳回的介面指標`riid`。</span><span class="sxs-lookup"><span data-stu-id="2955d-141">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2955d-142">備註</span><span class="sxs-lookup"><span data-stu-id="2955d-142">Remarks</span></span>  
 <span data-ttu-id="2955d-143">如果`pwszVersion`指定不存在，執行階段版本`CorBindToRuntimeEx`傳回 CLR_E_SHIM_RUNTIMELOAD HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="2955d-143">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="2955d-144">執行內容和流程的 Windows 身分識別</span><span class="sxs-lookup"><span data-stu-id="2955d-144">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="2955d-145">在第 1 版的 clr，<xref:System.Security.Principal.WindowsIdentity>物件不會流經非同步點，例如新的執行緒、 執行緒集區或計時器回呼。</span><span class="sxs-lookup"><span data-stu-id="2955d-145">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="2955d-146">在 2.0 版中的 clr，<xref:System.Threading.ExecutionContext>物件包裝目前執行中執行緒的一些資訊，並跨任何非同步點，但不是會在應用程式定義域界限之間流動它。</span><span class="sxs-lookup"><span data-stu-id="2955d-146">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="2955d-147">同樣地，<xref:System.Security.Principal.WindowsIdentity>物件也會流過任何非同步點。</span><span class="sxs-lookup"><span data-stu-id="2955d-147">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="2955d-148">因此，目前的模擬執行緒，如果有的話，會流動。</span><span class="sxs-lookup"><span data-stu-id="2955d-148">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="2955d-149">您可以變更流程有兩種：</span><span class="sxs-lookup"><span data-stu-id="2955d-149">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="2955d-150">藉由修改<xref:System.Threading.ExecutionContext>若要隱藏個別的執行緒上的流程的設定 (請參閱 < <xref:System.Threading.ExecutionContext.SuppressFlow%2A>， <xref:System.Security.SecurityContext.SuppressFlow%2A>，和<xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A>方法)。</span><span class="sxs-lookup"><span data-stu-id="2955d-150">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="2955d-151">藉由處理程序的預設模式變更為 「 第 1 版相容性模式中，其中<xref:System.Security.Principal.WindowsIdentity>物件不會流經任何非同步點，無論<xref:System.Threading.ExecutionContext>目前執行緒上的設定。</span><span class="sxs-lookup"><span data-stu-id="2955d-151">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="2955d-152">您要如何變更預設的模式取決於您是使用 managed 可執行檔或未受管理的裝載介面載入 CLR:</span><span class="sxs-lookup"><span data-stu-id="2955d-152">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="2955d-153">受管理的可執行檔，您必須設定`enabled`的屬性[ \<legacyImpersonationPolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)項目`true`。</span><span class="sxs-lookup"><span data-stu-id="2955d-153">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="2955d-154">Unmanaged 裝載介面，設定`STARTUP_LEGACY_IMPERSONATION`中的旗標`startupFlags`參數呼叫時`CorBindToRuntimeEx`函式。</span><span class="sxs-lookup"><span data-stu-id="2955d-154">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `startupFlags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="2955d-155">第 1 版相容性模式適用於整個程序和程序中的所有應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="2955d-155">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2955d-156">需求</span><span class="sxs-lookup"><span data-stu-id="2955d-156">Requirements</span></span>  
 <span data-ttu-id="2955d-157">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2955d-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2955d-158">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2955d-158">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2955d-159">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2955d-159">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2955d-160">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2955d-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2955d-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2955d-161">See also</span></span>

- [<span data-ttu-id="2955d-162">CorBindToCurrentRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="2955d-162">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="2955d-163">CorBindToRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="2955d-163">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="2955d-164">CorBindToRuntimeByCfg 函式</span><span class="sxs-lookup"><span data-stu-id="2955d-164">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="2955d-165">CorBindToRuntimeHost 函式</span><span class="sxs-lookup"><span data-stu-id="2955d-165">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="2955d-166">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="2955d-166">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="2955d-167">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="2955d-167">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
