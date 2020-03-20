---
title: CorBindToRuntime 函式
ms.date: 03/30/2017
api_name:
- CorBindToRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntime
helpviewer_keywords:
- CorBindToRuntime function [.NET Framework hosting]
ms.assetid: 799740aa-46ec-4532-95da-6444565b4971
topic_type:
- apiref
ms.openlocfilehash: 2db9d26ef2dec150977c468b16334a7cb4b3d49c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176509"
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="29f56-102">CorBindToRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="29f56-102">CorBindToRuntime Function</span></span>
<span data-ttu-id="29f56-103">使非託管主機能夠將通用語言運行時 （CLR） 載入到進程中。</span><span class="sxs-lookup"><span data-stu-id="29f56-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="29f56-104">此功能已在 .NET 框架 4 中棄用。</span><span class="sxs-lookup"><span data-stu-id="29f56-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29f56-105">語法</span><span class="sxs-lookup"><span data-stu-id="29f56-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,
    [in]  LPCWSTR     pwszBuildFlavor,
    [in]  REFCLSID    rclsid,
    [in]  REFIID      riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29f56-106">參數</span><span class="sxs-lookup"><span data-stu-id="29f56-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="29f56-107">[在]描述要載入的 CLR 版本的字串。</span><span class="sxs-lookup"><span data-stu-id="29f56-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="29f56-108">.NET 框架中的版本號由四個部分組成，由句點分隔：*主要.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="29f56-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="29f56-109">傳遞的`pwszVersion`字串必須以字元"v"開頭，後跟版本號的前三個部分（例如，"v1.0.1529"）。</span><span class="sxs-lookup"><span data-stu-id="29f56-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="29f56-110">CLR 的某些版本都安裝了策略語句，該語句指定與 CLR 的早期版本的相容性。</span><span class="sxs-lookup"><span data-stu-id="29f56-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="29f56-111">預設情況下，啟動希姆`pwszVersion`根據策略語句進行評估，並載入與所請求版本相容的最新版本的運行時。</span><span class="sxs-lookup"><span data-stu-id="29f56-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="29f56-112">主機可以強制 him 跳過策略評估，並通過傳遞`pwszVersion``STARTUP_LOADER_SAFEMODE``flags`參數的值來載入指定的確切版本，如下所述。</span><span class="sxs-lookup"><span data-stu-id="29f56-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="29f56-113">如果調用方為`pwszVersion`指定 null，則載入運行時的最新版本。</span><span class="sxs-lookup"><span data-stu-id="29f56-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="29f56-114">傳遞 null 使主機無法控制載入的哪個版本的運行時。</span><span class="sxs-lookup"><span data-stu-id="29f56-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="29f56-115">儘管此方法在某些情況下可能適用，但強烈建議主機提供要載入的特定版本。</span><span class="sxs-lookup"><span data-stu-id="29f56-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="29f56-116">[在]指定是載入 CLR 的伺服器還是工作站構建的字串。</span><span class="sxs-lookup"><span data-stu-id="29f56-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="29f56-117">有效值為 `svr` 和 `wks`。</span><span class="sxs-lookup"><span data-stu-id="29f56-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="29f56-118">伺服器生成經過優化，以利用多個處理器進行垃圾回收，工作站生成針對在單處理器電腦上運行的用戶端應用程式進行了優化。</span><span class="sxs-lookup"><span data-stu-id="29f56-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="29f56-119">如果`pwszBuildFlavor`設置為 null，則載入工作站生成。</span><span class="sxs-lookup"><span data-stu-id="29f56-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="29f56-120">在單處理器電腦上運行時，工作站生成始終載入，即使`pwszBuildFlavor`設置為`svr`。</span><span class="sxs-lookup"><span data-stu-id="29f56-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="29f56-121">但是，如果`pwszBuildFlavor`設置為`svr`並指定了併發垃圾回收（請參閱`flags`參數的說明），則載入伺服器生成。</span><span class="sxs-lookup"><span data-stu-id="29f56-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="29f56-122">[在]`CLSID`實現[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)或[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)介面的共類。</span><span class="sxs-lookup"><span data-stu-id="29f56-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="29f56-123">支援的值CLSID_CorRuntimeHost或CLSID_CLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="29f56-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="29f56-124">[在]從`IID`的請求介面的`rclsid`的</span><span class="sxs-lookup"><span data-stu-id="29f56-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="29f56-125">支援的值IID_ICorRuntimeHost或IID_ICLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="29f56-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="29f56-126">[出]返回的介面指標到`riid`。</span><span class="sxs-lookup"><span data-stu-id="29f56-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29f56-127">備註</span><span class="sxs-lookup"><span data-stu-id="29f56-127">Remarks</span></span>  
 <span data-ttu-id="29f56-128">如果`pwszVersion`指定不存在的執行階段版本，`CorBindToRuntimeEx`則返回 hRESULT 值CLR_E_SHIM_RUNTIMELOAD。</span><span class="sxs-lookup"><span data-stu-id="29f56-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="29f56-129">執行上下文和 Windows 標識的流</span><span class="sxs-lookup"><span data-stu-id="29f56-129">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="29f56-130">在 CLR 的版本 1<xref:System.Security.Principal.WindowsIdentity>中，物件不會跨非同步點（如新執行緒、執行緒池或計時器回檔）流動。</span><span class="sxs-lookup"><span data-stu-id="29f56-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="29f56-131">在 CLR 的版本 2.0<xref:System.Threading.ExecutionContext>中，物件會包裝有關當前正在執行的執行緒的一些資訊，並將其流過任何非同步點，但不跨應用程式域邊界。</span><span class="sxs-lookup"><span data-stu-id="29f56-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="29f56-132">同樣，<xref:System.Security.Principal.WindowsIdentity>物件也流過任何非同步點。</span><span class="sxs-lookup"><span data-stu-id="29f56-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="29f56-133">因此，執行緒上的當前類比（如果有）也會流動。</span><span class="sxs-lookup"><span data-stu-id="29f56-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="29f56-134">您可以通過兩種方式更改流：</span><span class="sxs-lookup"><span data-stu-id="29f56-134">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="29f56-135">通過修改<xref:System.Threading.ExecutionContext>設置以按執行緒禁止流（請參閱 、<xref:System.Threading.ExecutionContext.SuppressFlow%2A><xref:System.Security.SecurityContext.SuppressFlow%2A>和方法）。 <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A></span><span class="sxs-lookup"><span data-stu-id="29f56-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="29f56-136">通過將進程預設模式更改為版本 1 相容性模式，其中<xref:System.Security.Principal.WindowsIdentity>物件不會流過任何非同步點，而不考慮當前執行緒上的<xref:System.Threading.ExecutionContext>設置。</span><span class="sxs-lookup"><span data-stu-id="29f56-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="29f56-137">更改預設模式的方式取決於您是使用託管可執行檔還是非託管託管介面來載入 CLR：</span><span class="sxs-lookup"><span data-stu-id="29f56-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="29f56-138">對於託管可執行檔，必須將`enabled`[\<舊類比策略>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)元素的屬性設置為`true`。</span><span class="sxs-lookup"><span data-stu-id="29f56-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="29f56-139">對於非託管託管介面，在`STARTUP_LEGACY_IMPERSONATION`調用`flags``CorBindToRuntimeEx`函數時在參數中設置標誌。</span><span class="sxs-lookup"><span data-stu-id="29f56-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="29f56-140">版本 1 相容性模式適用于整個過程和流程中的所有應用程式域。</span><span class="sxs-lookup"><span data-stu-id="29f56-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29f56-141">備註</span><span class="sxs-lookup"><span data-stu-id="29f56-141">Remarks</span></span>  
 <span data-ttu-id="29f56-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) `CorBindToRuntime`並執行相同的操作，`CorBindToRuntimeEx`但該函數允許您設置標誌以指定 CLR 的行為。</span><span class="sxs-lookup"><span data-stu-id="29f56-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29f56-143">需求</span><span class="sxs-lookup"><span data-stu-id="29f56-143">Requirements</span></span>  
 <span data-ttu-id="29f56-144">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="29f56-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29f56-145">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="29f56-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="29f56-146">**庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="29f56-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="29f56-147">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29f56-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29f56-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29f56-148">See also</span></span>

- [<span data-ttu-id="29f56-149">CorBindToCurrentRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="29f56-149">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="29f56-150">CorBindToRuntimeByCfg 函式</span><span class="sxs-lookup"><span data-stu-id="29f56-150">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="29f56-151">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="29f56-151">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="29f56-152">CorBindToRuntimeHost 函式</span><span class="sxs-lookup"><span data-stu-id="29f56-152">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="29f56-153">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="29f56-153">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="29f56-154">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="29f56-154">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
