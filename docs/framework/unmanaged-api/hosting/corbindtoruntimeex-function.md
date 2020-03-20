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
ms.openlocfilehash: 3520af5f55f43183920dce7fbd24b70359c023a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176496"
---
# <a name="corbindtoruntimeex-function"></a><span data-ttu-id="f6e26-102">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="f6e26-102">CorBindToRuntimeEx Function</span></span>
<span data-ttu-id="f6e26-103">使非託管主機能夠將通用語言運行時 （CLR） 載入到進程中。</span><span class="sxs-lookup"><span data-stu-id="f6e26-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span> <span data-ttu-id="f6e26-104">[CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)和`CorBindToRuntimeEx`函數執行相同的操作，`CorBindToRuntimeEx`但該函數允許您設置標誌以指定 CLR 的行為。</span><span class="sxs-lookup"><span data-stu-id="f6e26-104">The [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) and `CorBindToRuntimeEx` functions perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 <span data-ttu-id="f6e26-105">此功能已在 .NET 框架 4 中棄用。</span><span class="sxs-lookup"><span data-stu-id="f6e26-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="f6e26-106">此函數採用一組允許主機執行以下操作的參數：</span><span class="sxs-lookup"><span data-stu-id="f6e26-106">This function takes a set of parameters that allow a host to do the following:</span></span>  
  
- <span data-ttu-id="f6e26-107">指定將載入的運行時的版本。</span><span class="sxs-lookup"><span data-stu-id="f6e26-107">Specify the version of the runtime that will be loaded.</span></span>  
  
- <span data-ttu-id="f6e26-108">指示是否應載入伺服器或工作站生成。</span><span class="sxs-lookup"><span data-stu-id="f6e26-108">Indicate whether the server or workstation build should be loaded.</span></span>  
  
- <span data-ttu-id="f6e26-109">控制是否完成了併發垃圾回收或非併發垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="f6e26-109">Control whether concurrent garbage collection or non-concurrent garbage collection is done.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6e26-110">在 64 位系統上運行 WOW64 x86 模擬器的應用程式不支援併發垃圾回收，這些系統實現了英特爾 Itanium 架構（以前稱為 IA-64）。</span><span class="sxs-lookup"><span data-stu-id="f6e26-110">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="f6e26-111">有關在 64 位 Windows 系統上使用 WOW64 的詳細資訊，請參閱[運行 32 位應用程式](/windows/desktop/WinProg64/running-32-bit-applications)。</span><span class="sxs-lookup"><span data-stu-id="f6e26-111">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
- <span data-ttu-id="f6e26-112">控制程式集是否載入為域中立。</span><span class="sxs-lookup"><span data-stu-id="f6e26-112">Control whether assemblies are loaded as domain-neutral.</span></span>  
  
- <span data-ttu-id="f6e26-113">獲取指向[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)的介面指標，該指標可用於在 CLR 啟動之前設置用於配置 CLR 實例的其他選項。</span><span class="sxs-lookup"><span data-stu-id="f6e26-113">Obtain an interface pointer to an [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) that can be used to set additional options for configuring an instance of the CLR before it is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6e26-114">語法</span><span class="sxs-lookup"><span data-stu-id="f6e26-114">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f6e26-115">參數</span><span class="sxs-lookup"><span data-stu-id="f6e26-115">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="f6e26-116">[在]描述要載入的 CLR 版本的字串。</span><span class="sxs-lookup"><span data-stu-id="f6e26-116">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="f6e26-117">.NET 框架中的版本號由四個部分組成，由句點分隔：*主要.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="f6e26-117">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="f6e26-118">傳遞的`pwszVersion`字串必須以字元"v"開頭，後跟版本號的前三個部分（例如，"v1.0.1529"）。</span><span class="sxs-lookup"><span data-stu-id="f6e26-118">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="f6e26-119">CLR 的某些版本都安裝了策略語句，該語句指定與 CLR 的早期版本的相容性。</span><span class="sxs-lookup"><span data-stu-id="f6e26-119">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="f6e26-120">預設情況下，啟動希姆`pwszVersion`根據策略語句進行評估，並載入與所請求版本相容的最新版本的運行時。</span><span class="sxs-lookup"><span data-stu-id="f6e26-120">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="f6e26-121">主機可以強制 him 跳過策略評估，並通過傳遞`pwszVersion``STARTUP_LOADER_SAFEMODE``startupFlags`參數的值來載入指定的確切版本，如下所述。</span><span class="sxs-lookup"><span data-stu-id="f6e26-121">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `startupFlags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="f6e26-122">如果調用方為`pwszVersion`指定`CorBindToRuntimeEx`null，則標識其版本號低於 .NET Framework 4 運行時的已安裝運行時集，並從該集載入最新版本的運行時。</span><span class="sxs-lookup"><span data-stu-id="f6e26-122">If the caller specifies null for `pwszVersion`, `CorBindToRuntimeEx` identifies the set of installed runtimes whose version numbers are lower than the .NET Framework 4 runtime, and loads the latest version of the runtime from that set.</span></span> <span data-ttu-id="f6e26-123">它不會載入 .NET 框架 4 或更高版本，如果沒有安裝早期版本，它將失敗。</span><span class="sxs-lookup"><span data-stu-id="f6e26-123">It won't load the .NET Framework 4 or later, and fails if no earlier version is installed.</span></span> <span data-ttu-id="f6e26-124">請注意，傳遞 null 使主機無法控制載入的哪個版本的運行時。</span><span class="sxs-lookup"><span data-stu-id="f6e26-124">Note that passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="f6e26-125">儘管此方法在某些情況下可能適用，但強烈建議主機提供要載入的特定版本。</span><span class="sxs-lookup"><span data-stu-id="f6e26-125">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="f6e26-126">[在]指定是載入 CLR 的伺服器還是工作站構建的字串。</span><span class="sxs-lookup"><span data-stu-id="f6e26-126">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="f6e26-127">有效值為 `svr` 和 `wks`。</span><span class="sxs-lookup"><span data-stu-id="f6e26-127">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="f6e26-128">伺服器生成經過優化，以利用多個處理器進行垃圾回收，工作站生成針對在單處理器電腦上運行的用戶端應用程式進行了優化。</span><span class="sxs-lookup"><span data-stu-id="f6e26-128">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="f6e26-129">如果`pwszBuildFlavor`設置為 null，則載入工作站生成。</span><span class="sxs-lookup"><span data-stu-id="f6e26-129">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="f6e26-130">在單處理器電腦上運行時，工作站生成始終載入，即使`pwszBuildFlavor`設置為`svr`。</span><span class="sxs-lookup"><span data-stu-id="f6e26-130">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="f6e26-131">但是，如果`pwszBuildFlavor`設置為`svr`並指定了併發垃圾回收（請參閱`startupFlags`參數的說明），則載入伺服器生成。</span><span class="sxs-lookup"><span data-stu-id="f6e26-131">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="f6e26-132">[在][STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)枚舉的值的組合。</span><span class="sxs-lookup"><span data-stu-id="f6e26-132">[in] A combination of values of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span> <span data-ttu-id="f6e26-133">這些標誌控制併發垃圾回收、域中立代碼和`pwszVersion`參數的行為。</span><span class="sxs-lookup"><span data-stu-id="f6e26-133">These flags control concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="f6e26-134">如果未設置標誌，則預設值為單個域。</span><span class="sxs-lookup"><span data-stu-id="f6e26-134">The default is single domain if no flag is set.</span></span> <span data-ttu-id="f6e26-135">下列是有效值：</span><span class="sxs-lookup"><span data-stu-id="f6e26-135">The following values are valid:</span></span>  
  
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
  
 <span data-ttu-id="f6e26-136">有關這些標誌的說明，請參閱[STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)枚舉。</span><span class="sxs-lookup"><span data-stu-id="f6e26-136">For descriptions of these flags, see the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="f6e26-137">[在]`CLSID`實現[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)或[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)介面的共類。</span><span class="sxs-lookup"><span data-stu-id="f6e26-137">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="f6e26-138">支援的值CLSID_CorRuntimeHost或CLSID_CLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="f6e26-138">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="f6e26-139">[在]從`IID`的請求介面的`rclsid`的</span><span class="sxs-lookup"><span data-stu-id="f6e26-139">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="f6e26-140">支援的值IID_ICorRuntimeHost或IID_ICLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="f6e26-140">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="f6e26-141">[出]返回的介面指標到`riid`。</span><span class="sxs-lookup"><span data-stu-id="f6e26-141">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6e26-142">備註</span><span class="sxs-lookup"><span data-stu-id="f6e26-142">Remarks</span></span>  
 <span data-ttu-id="f6e26-143">如果`pwszVersion`指定不存在的執行階段版本，`CorBindToRuntimeEx`則返回 hRESULT 值CLR_E_SHIM_RUNTIMELOAD。</span><span class="sxs-lookup"><span data-stu-id="f6e26-143">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="f6e26-144">執行上下文和 Windows 標識的流</span><span class="sxs-lookup"><span data-stu-id="f6e26-144">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="f6e26-145">在 CLR 的版本 1<xref:System.Security.Principal.WindowsIdentity>中，物件不會跨非同步點（如新執行緒、執行緒池或計時器回檔）流動。</span><span class="sxs-lookup"><span data-stu-id="f6e26-145">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="f6e26-146">在 CLR 的版本 2.0<xref:System.Threading.ExecutionContext>中，物件會包裝有關當前正在執行的執行緒的一些資訊，並將其流過任何非同步點，但不跨應用程式域邊界。</span><span class="sxs-lookup"><span data-stu-id="f6e26-146">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="f6e26-147">同樣，<xref:System.Security.Principal.WindowsIdentity>物件也流過任何非同步點。</span><span class="sxs-lookup"><span data-stu-id="f6e26-147">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="f6e26-148">因此，執行緒上的當前類比（如果有）也會流動。</span><span class="sxs-lookup"><span data-stu-id="f6e26-148">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="f6e26-149">您可以通過兩種方式更改流：</span><span class="sxs-lookup"><span data-stu-id="f6e26-149">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="f6e26-150">通過修改<xref:System.Threading.ExecutionContext>設置以按執行緒禁止流（請參閱 、<xref:System.Threading.ExecutionContext.SuppressFlow%2A><xref:System.Security.SecurityContext.SuppressFlow%2A>和方法）。 <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A></span><span class="sxs-lookup"><span data-stu-id="f6e26-150">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="f6e26-151">通過將進程預設模式更改為版本 1 相容性模式，其中<xref:System.Security.Principal.WindowsIdentity>物件不會流過任何非同步點，而不考慮當前執行緒上的<xref:System.Threading.ExecutionContext>設置。</span><span class="sxs-lookup"><span data-stu-id="f6e26-151">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="f6e26-152">更改預設模式的方式取決於您是使用託管可執行檔還是非託管託管介面來載入 CLR：</span><span class="sxs-lookup"><span data-stu-id="f6e26-152">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="f6e26-153">對於託管可執行檔，必須將`enabled`[\<舊類比策略>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)元素的屬性設置為`true`。</span><span class="sxs-lookup"><span data-stu-id="f6e26-153">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="f6e26-154">對於非託管託管介面，在`STARTUP_LEGACY_IMPERSONATION`調用`startupFlags``CorBindToRuntimeEx`函數時在參數中設置標誌。</span><span class="sxs-lookup"><span data-stu-id="f6e26-154">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `startupFlags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="f6e26-155">版本 1 相容性模式適用于整個過程和流程中的所有應用程式域。</span><span class="sxs-lookup"><span data-stu-id="f6e26-155">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6e26-156">需求</span><span class="sxs-lookup"><span data-stu-id="f6e26-156">Requirements</span></span>  
 <span data-ttu-id="f6e26-157">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f6e26-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6e26-158">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f6e26-158">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f6e26-159">**庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f6e26-159">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6e26-160">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6e26-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6e26-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6e26-161">See also</span></span>

- [<span data-ttu-id="f6e26-162">CorBindToCurrentRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="f6e26-162">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="f6e26-163">CorBindToRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="f6e26-163">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="f6e26-164">CorBindToRuntimeByCfg 函式</span><span class="sxs-lookup"><span data-stu-id="f6e26-164">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="f6e26-165">CorBindToRuntimeHost 函式</span><span class="sxs-lookup"><span data-stu-id="f6e26-165">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="f6e26-166">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="f6e26-166">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="f6e26-167">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="f6e26-167">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
