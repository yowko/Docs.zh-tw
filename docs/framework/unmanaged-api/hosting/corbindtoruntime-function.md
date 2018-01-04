---
title: "CorBindToRuntime 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CorBindToRuntime
helpviewer_keywords: CorBindToRuntime function [.NET Framework hosting]
ms.assetid: 799740aa-46ec-4532-95da-6444565b4971
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e6ce976961eedaa58ad265a133c15b2f27a8985
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="ca1d5-102">CorBindToRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="ca1d5-102">CorBindToRuntime Function</span></span>
<span data-ttu-id="ca1d5-103">可讓 unmanaged 的主機將 common language runtime (CLR) 載入處理序。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="ca1d5-104">此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca1d5-105">語法</span><span class="sxs-lookup"><span data-stu-id="ca1d5-105">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,   
    [in]  LPCWSTR     pwszBuildFlavor,   
    [in]  REFCLSID    rclsid,   
    [in]  REFIID      riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ca1d5-106">參數</span><span class="sxs-lookup"><span data-stu-id="ca1d5-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="ca1d5-107">[in]您要載入描述的 CLR 版本字串。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="ca1d5-108">在.NET Framework 的版本號碼是由以句號分隔的四個部分所組成： *major.minor.build.revision*。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="ca1d5-109">當做字串傳遞給`pwszVersion`開頭必須是字元"v"後面接著的版本號碼 (例如，"v1.0.1529") 的前三個部分。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="ca1d5-110">某些版本的 CLR 會以指定與舊版 CLR 相容的原則陳述式安裝。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="ca1d5-111">根據預設，啟動填充碼會評估`pwszVersion`針對原則陳述式和載入執行階段的最新版本，是與所要求的版本相容。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="ca1d5-112">主機可以強制略過原則評估並載入中指定的確切版本填充碼`pwszVersion`依值傳遞`STARTUP_LOADER_SAFEMODE`如`flags`參數，如下所述。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="ca1d5-113">如果呼叫端指定為 null `pwszVersion`，載入執行階段的最新版本。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="ca1d5-114">將 null 傳遞不提供主應用程式載入的執行階段版本的任何控制項。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="ca1d5-115">雖然在某些情況下可能適合使用這種方法，但強烈建議主應用程式，提供要載入的特定版本。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="ca1d5-116">[in]字串，指定是否要在伺服器或工作站組建的 clr 載入。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="ca1d5-117">有效值為 `svr` 和 `wks`。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="ca1d5-118">伺服器組建已最佳化，可利用多個處理器的記憶體回收，並工作站組建最適合用於單一處理器電腦上執行的用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="ca1d5-119">如果`pwszBuildFlavor`設為 null，工作站組建已載入。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="ca1d5-120">單一處理器電腦上執行時，會一律載入工作站組建，即使`pwszBuildFlavor`設`svr`。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="ca1d5-121">不過，如果`pwszBuildFlavor`設為`svr`並行記憶體回收是指定 (請參閱描述`flags`參數)，會載入伺服器組建。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="ca1d5-122">[in]`CLSID`實作的 coclass 的[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)或[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="ca1d5-123">支援的值為 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="ca1d5-124">[in]`IID`所要求介面從`rclsid`。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="ca1d5-125">支援的值為 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="ca1d5-126">[out]傳回的介面指標`riid`。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca1d5-127">備註</span><span class="sxs-lookup"><span data-stu-id="ca1d5-127">Remarks</span></span>  
 <span data-ttu-id="ca1d5-128">如果`pwszVersion`指定不存在，執行階段版本`CorBindToRuntimeEx`傳回 CLR_E_SHIM_RUNTIMELOAD HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="ca1d5-129">執行內容和流程的 Windows 身分識別</span><span class="sxs-lookup"><span data-stu-id="ca1d5-129">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="ca1d5-130">在 CLR 的第 1 版中<xref:System.Security.Principal.WindowsIdentity>物件不會流動到非同步的點，例如新的執行緒、 執行緒集區或計時器回呼。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="ca1d5-131">在 CLR 2.0 版<xref:System.Threading.ExecutionContext>物件包裝目前執行中執行緒的一些資訊及流向它，跨越任何非同步的點，但不是會跨應用程式定義域界限。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="ca1d5-132">同樣地，<xref:System.Security.Principal.WindowsIdentity>物件也會透過非同步的任何時間點流動。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="ca1d5-133">因此，目前的模擬執行緒，如果有的話，流動。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="ca1d5-134">您可以修改流程有兩種：</span><span class="sxs-lookup"><span data-stu-id="ca1d5-134">You can alter the flow in two ways:</span></span>  
  
1.  <span data-ttu-id="ca1d5-135">藉由修改<xref:System.Threading.ExecutionContext>設定，以隱藏每個執行緒為基礎的流程 (請參閱<xref:System.Threading.ExecutionContext.SuppressFlow%2A>， <xref:System.Security.SecurityContext.SuppressFlow%2A>，和<xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A>方法)。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2.  <span data-ttu-id="ca1d5-136">由處理程序的預設模式變更為 「 第 1 版的相容性模式，其中<xref:System.Security.Principal.WindowsIdentity>物件不會流動跨越任何非同步的點，不論<xref:System.Threading.ExecutionContext>目前執行緒上的設定。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="ca1d5-137">如何變更預設的模式取決於是否載入 CLR 使用 managed 可執行檔或 unmanaged 裝載介面：</span><span class="sxs-lookup"><span data-stu-id="ca1d5-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1.  <span data-ttu-id="ca1d5-138">針對受管理的可執行檔，您必須設定`enabled`屬性[ \<legacyImpersonationPolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)元素`true`。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2.  <span data-ttu-id="ca1d5-139">Unmanaged 裝載介面，設定`STARTUP_LEGACY_IMPERSONATION`加上旗標`flags`參數呼叫時`CorBindToRuntimeEx`函式。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="ca1d5-140">第 1 版相容性模式適用於整個程序和程序中的所有應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca1d5-141">備註</span><span class="sxs-lookup"><span data-stu-id="ca1d5-141">Remarks</span></span>  
 <span data-ttu-id="ca1d5-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)和`CorBindToRuntime`執行相同的作業，但`CorBindToRuntimeEx`函式可讓您設定旗標來指定 CLR 的行為。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca1d5-143">需求</span><span class="sxs-lookup"><span data-stu-id="ca1d5-143">Requirements</span></span>  
 <span data-ttu-id="ca1d5-144">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ca1d5-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca1d5-145">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ca1d5-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ca1d5-146">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ca1d5-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca1d5-147">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca1d5-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca1d5-148">請參閱</span><span class="sxs-lookup"><span data-stu-id="ca1d5-148">See Also</span></span>  
 [<span data-ttu-id="ca1d5-149">CorBindToCurrentRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="ca1d5-149">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="ca1d5-150">CorBindToRuntimeByCfg 函式</span><span class="sxs-lookup"><span data-stu-id="ca1d5-150">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="ca1d5-151">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="ca1d5-151">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="ca1d5-152">CorBindToRuntimeHost 函式</span><span class="sxs-lookup"><span data-stu-id="ca1d5-152">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [<span data-ttu-id="ca1d5-153">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="ca1d5-153">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="ca1d5-154">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="ca1d5-154">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
