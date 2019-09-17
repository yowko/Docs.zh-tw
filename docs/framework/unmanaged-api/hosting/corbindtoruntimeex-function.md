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
ms.openlocfilehash: 88f31ae29efee9b353c2dcc679724db73da5444e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969418"
---
# <a name="corbindtoruntimeex-function"></a><span data-ttu-id="95c4f-102">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="95c4f-102">CorBindToRuntimeEx Function</span></span>
<span data-ttu-id="95c4f-103">讓非受控主機將 common language runtime （CLR）載入進程中。</span><span class="sxs-lookup"><span data-stu-id="95c4f-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span> <span data-ttu-id="95c4f-104">[CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)和`CorBindToRuntimeEx`函數會執行相同的作業，但`CorBindToRuntimeEx`函式可讓您設定旗標來指定 CLR 的行為。</span><span class="sxs-lookup"><span data-stu-id="95c4f-104">The [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) and `CorBindToRuntimeEx` functions perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 <span data-ttu-id="95c4f-105">此函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="95c4f-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="95c4f-106">此函式會接受一組參數，讓主機能夠執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="95c4f-106">This function takes a set of parameters that allow a host to do the following:</span></span>  
  
- <span data-ttu-id="95c4f-107">指定將要載入的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="95c4f-107">Specify the version of the runtime that will be loaded.</span></span>  
  
- <span data-ttu-id="95c4f-108">指出是否應載入伺服器或工作站組建。</span><span class="sxs-lookup"><span data-stu-id="95c4f-108">Indicate whether the server or workstation build should be loaded.</span></span>  
  
- <span data-ttu-id="95c4f-109">控制並行垃圾收集或非並行垃圾收集是否已完成。</span><span class="sxs-lookup"><span data-stu-id="95c4f-109">Control whether concurrent garbage collection or non-concurrent garbage collection is done.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95c4f-110">在執行 Intel Itanium 架構（先前稱為 IA-64）的64位系統上執行 WOW64 x86 模擬器的應用程式不支援並行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="95c4f-110">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="95c4f-111">如需在64位 Windows 系統上使用 WOW64 的詳細資訊，請參閱執行[32 位應用程式](/windows/desktop/WinProg64/running-32-bit-applications)。</span><span class="sxs-lookup"><span data-stu-id="95c4f-111">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
- <span data-ttu-id="95c4f-112">控制是否將元件載入為網域中性。</span><span class="sxs-lookup"><span data-stu-id="95c4f-112">Control whether assemblies are loaded as domain-neutral.</span></span>  
  
- <span data-ttu-id="95c4f-113">取得[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)的介面指標，其可以用來設定在啟動 CLR 實例之前，用來設定它的其他選項。</span><span class="sxs-lookup"><span data-stu-id="95c4f-113">Obtain an interface pointer to an [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) that can be used to set additional options for configuring an instance of the CLR before it is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95c4f-114">語法</span><span class="sxs-lookup"><span data-stu-id="95c4f-114">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="95c4f-115">參數</span><span class="sxs-lookup"><span data-stu-id="95c4f-115">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="95c4f-116">在描述您要載入之 CLR 版本的字串。</span><span class="sxs-lookup"><span data-stu-id="95c4f-116">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="95c4f-117">.NET Framework 中的版本號碼包含四個以句點分隔的部分： [主要]. [*次要. 組建. 修訂*]。</span><span class="sxs-lookup"><span data-stu-id="95c4f-117">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="95c4f-118">傳遞為`pwszVersion`的字串必須以字元 "v" 開頭，後面接著版本號碼的前三個部分（例如 "v 1.0.1529"）。</span><span class="sxs-lookup"><span data-stu-id="95c4f-118">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="95c4f-119">某些 CLR 版本會與原則語句一起安裝，以指定與舊版 CLR 的相容性。</span><span class="sxs-lookup"><span data-stu-id="95c4f-119">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="95c4f-120">根據預設，啟動填充碼會`pwszVersion`針對原則語句評估，並載入與所要求版本相容的最新執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="95c4f-120">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="95c4f-121">主機可以強制填充碼略過原則評估，並藉由傳遞`pwszVersion` `startupFlags`參數的`STARTUP_LOADER_SAFEMODE`值來載入中所指定的確切版本，如下所述。</span><span class="sxs-lookup"><span data-stu-id="95c4f-121">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `startupFlags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="95c4f-122">如果呼叫者為`pwszVersion`指定 null， `CorBindToRuntimeEx`則會識別版本號碼低於 .NET Framework 4 執行時間的已安裝執行時間，並從該集合載入最新版本的執行時間。</span><span class="sxs-lookup"><span data-stu-id="95c4f-122">If the caller specifies null for `pwszVersion`, `CorBindToRuntimeEx` identifies the set of installed runtimes whose version numbers are lower than the .NET Framework 4 runtime, and loads the latest version of the runtime from that set.</span></span> <span data-ttu-id="95c4f-123">它不會載入 .NET Framework 4 或更新版本，如果未安裝舊版，則會失敗。</span><span class="sxs-lookup"><span data-stu-id="95c4f-123">It won't load the .NET Framework 4 or later, and fails if no earlier version is installed.</span></span> <span data-ttu-id="95c4f-124">請注意，傳遞 null 可讓主機無法控制載入的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="95c4f-124">Note that passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="95c4f-125">雖然這種方法可能適用于某些情況，但強烈建議主機提供要載入的特定版本。</span><span class="sxs-lookup"><span data-stu-id="95c4f-125">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="95c4f-126">在字串，指定是否要載入伺服器或 CLR 的工作站組建。</span><span class="sxs-lookup"><span data-stu-id="95c4f-126">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="95c4f-127">有效值為 `svr` 和 `wks`。</span><span class="sxs-lookup"><span data-stu-id="95c4f-127">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="95c4f-128">伺服器組建已優化，可利用多個處理器進行垃圾收集，而且工作站組建已針對在單處理器機器上執行的用戶端應用程式優化。</span><span class="sxs-lookup"><span data-stu-id="95c4f-128">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="95c4f-129">如果`pwszBuildFlavor`設定為 null，則會載入工作站組建。</span><span class="sxs-lookup"><span data-stu-id="95c4f-129">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="95c4f-130">在單處理器機器上執行時，一律會載入工作站組建，即使設定為`pwszBuildFlavor` `svr`也一樣。</span><span class="sxs-lookup"><span data-stu-id="95c4f-130">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="95c4f-131">不過，如果`pwszBuildFlavor`設定為`svr` ，且指定了並行垃圾收集（ `startupFlags`請參閱參數的描述），則會載入伺服器組建。</span><span class="sxs-lookup"><span data-stu-id="95c4f-131">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="95c4f-132">在[STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)列舉的值組合。</span><span class="sxs-lookup"><span data-stu-id="95c4f-132">[in] A combination of values of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span> <span data-ttu-id="95c4f-133">這些旗標會控制並行垃圾收集、網域中性程式碼，以及`pwszVersion`參數的行為。</span><span class="sxs-lookup"><span data-stu-id="95c4f-133">These flags control concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="95c4f-134">如果未設定旗標，則預設值為單一網域。</span><span class="sxs-lookup"><span data-stu-id="95c4f-134">The default is single domain if no flag is set.</span></span> <span data-ttu-id="95c4f-135">下列是有效值：</span><span class="sxs-lookup"><span data-stu-id="95c4f-135">The following values are valid:</span></span>  
  
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
  
 <span data-ttu-id="95c4f-136">如需這些旗標的說明，請參閱[STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)列舉。</span><span class="sxs-lookup"><span data-stu-id="95c4f-136">For descriptions of these flags, see the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="95c4f-137">在Coclass 的，其會執行 [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) 或 [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) 介面。`CLSID`</span><span class="sxs-lookup"><span data-stu-id="95c4f-137">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="95c4f-138">支援的值為 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="95c4f-138">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="95c4f-139">在`IID` 從`rclsid`所要求之介面的。</span><span class="sxs-lookup"><span data-stu-id="95c4f-139">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="95c4f-140">支援的值為 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="95c4f-140">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="95c4f-141">脫銷傳回的介面指標`riid`。</span><span class="sxs-lookup"><span data-stu-id="95c4f-141">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95c4f-142">備註</span><span class="sxs-lookup"><span data-stu-id="95c4f-142">Remarks</span></span>  
 <span data-ttu-id="95c4f-143">如果`pwszVersion`指定不存在的執行階段版本， `CorBindToRuntimeEx`則會傳回 CLR_E_SHIM_RUNTIMELOAD 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="95c4f-143">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="95c4f-144">執行內容和 Windows 身分識別流程</span><span class="sxs-lookup"><span data-stu-id="95c4f-144">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="95c4f-145">在 CLR 的第1版中， <xref:System.Security.Principal.WindowsIdentity>物件不會流經非同步點，例如新執行緒、執行緒集區或計時器回呼。</span><span class="sxs-lookup"><span data-stu-id="95c4f-145">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="95c4f-146">在 CLR 的版本2.0 中， <xref:System.Threading.ExecutionContext>物件會包裝目前執行中線程的一些相關資訊，並將其流經任何非同步點，但不會跨越應用程式域界限。</span><span class="sxs-lookup"><span data-stu-id="95c4f-146">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="95c4f-147">同樣地， <xref:System.Security.Principal.WindowsIdentity>物件也會流經任何非同步點。</span><span class="sxs-lookup"><span data-stu-id="95c4f-147">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="95c4f-148">因此，執行緒上目前的模擬（如果有的話）也會流動。</span><span class="sxs-lookup"><span data-stu-id="95c4f-148">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="95c4f-149">您可以透過兩種方式來改變流程：</span><span class="sxs-lookup"><span data-stu-id="95c4f-149">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="95c4f-150">藉由修改<xref:System.Threading.ExecutionContext>設定來隱藏每個執行緒的流程（ <xref:System.Threading.ExecutionContext.SuppressFlow%2A>請參閱、 <xref:System.Security.SecurityContext.SuppressFlow%2A>和<xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A>方法）。</span><span class="sxs-lookup"><span data-stu-id="95c4f-150">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="95c4f-151">將進程預設模式變更為版本1相容性模式，其中<xref:System.Security.Principal.WindowsIdentity>物件不會流經任何非同步點，而不論<xref:System.Threading.ExecutionContext>目前線程上的設定為何。</span><span class="sxs-lookup"><span data-stu-id="95c4f-151">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="95c4f-152">您變更預設模式的方式，取決於您使用的是受控可執行檔或非受控裝載介面來載入 CLR：</span><span class="sxs-lookup"><span data-stu-id="95c4f-152">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="95c4f-153">對於受控可執行檔，您必須`enabled`將[ \<legacyImpersonationPolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)專案的屬性設定`true`為。</span><span class="sxs-lookup"><span data-stu-id="95c4f-153">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="95c4f-154">若為非受控裝載介面， `STARTUP_LEGACY_IMPERSONATION`請在呼叫`startupFlags` `CorBindToRuntimeEx`函式時，于參數中設定旗標。</span><span class="sxs-lookup"><span data-stu-id="95c4f-154">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `startupFlags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="95c4f-155">版本1相容性模式適用于整個進程和進程中的所有應用程式域。</span><span class="sxs-lookup"><span data-stu-id="95c4f-155">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95c4f-156">需求</span><span class="sxs-lookup"><span data-stu-id="95c4f-156">Requirements</span></span>  
 <span data-ttu-id="95c4f-157">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="95c4f-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95c4f-158">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="95c4f-158">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="95c4f-159">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="95c4f-159">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95c4f-160">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95c4f-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95c4f-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95c4f-161">See also</span></span>

- [<span data-ttu-id="95c4f-162">CorBindToCurrentRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="95c4f-162">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="95c4f-163">CorBindToRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="95c4f-163">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="95c4f-164">CorBindToRuntimeByCfg 函式</span><span class="sxs-lookup"><span data-stu-id="95c4f-164">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="95c4f-165">CorBindToRuntimeHost 函式</span><span class="sxs-lookup"><span data-stu-id="95c4f-165">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="95c4f-166">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="95c4f-166">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="95c4f-167">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="95c4f-167">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
