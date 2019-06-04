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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3af11b3d2170e13bf216aec64f2bff88cc015f41
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490598"
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="83526-102">CorBindToRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="83526-102">CorBindToRuntime Function</span></span>
<span data-ttu-id="83526-103">可讓 unmanaged 主應用程式將 common language runtime (CLR) 載入程序。</span><span class="sxs-lookup"><span data-stu-id="83526-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="83526-104">此函式已被取代，在.NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="83526-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83526-105">語法</span><span class="sxs-lookup"><span data-stu-id="83526-105">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,   
    [in]  LPCWSTR     pwszBuildFlavor,   
    [in]  REFCLSID    rclsid,   
    [in]  REFIID      riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83526-106">參數</span><span class="sxs-lookup"><span data-stu-id="83526-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="83526-107">[in]想要載入的字串，描述的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="83526-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="83526-108">在.NET Framework 的版本號碼是由以句點分隔的四個部分所組成： *major.minor.build.revision*。</span><span class="sxs-lookup"><span data-stu-id="83526-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="83526-109">將字串傳遞為`pwszVersion`不可使用字元"v"後面接著的版本號碼 (例如，"v1.0.1529 」) 的前三個部分。</span><span class="sxs-lookup"><span data-stu-id="83526-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="83526-110">某些版本的 CLR 會以指定與舊版的 clr 相容的原則陳述式安裝。</span><span class="sxs-lookup"><span data-stu-id="83526-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="83526-111">根據預設，啟動填充碼會評估`pwszVersion`針對原則陳述式並載入最新版本的執行階段，是與所要求的版本相容。</span><span class="sxs-lookup"><span data-stu-id="83526-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="83526-112">主機可以強制填充碼略過原則評估，並載入指定的確切版本`pwszVersion`傳遞的值，藉以`STARTUP_LOADER_SAFEMODE`如`flags`參數，如下所述。</span><span class="sxs-lookup"><span data-stu-id="83526-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="83526-113">如果呼叫端指定為 null `pwszVersion`，載入執行階段的最新的版本。</span><span class="sxs-lookup"><span data-stu-id="83526-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="83526-114">將 null 傳遞不提供主機載入執行階段版本的任何控制項。</span><span class="sxs-lookup"><span data-stu-id="83526-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="83526-115">雖然這種方法可能適用於某些情況下，強烈建議主應用程式，提供要載入的特定版本。</span><span class="sxs-lookup"><span data-stu-id="83526-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="83526-116">[in]字串，指定是否要載入的伺服器或工作站組建的 clr。</span><span class="sxs-lookup"><span data-stu-id="83526-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="83526-117">有效值為 `svr` 和 `wks`。</span><span class="sxs-lookup"><span data-stu-id="83526-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="83526-118">伺服器組建已最佳化，可利用多個處理器的記憶體回收，以及工作站建置適用於單一處理器電腦上執行的用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="83526-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="83526-119">如果`pwszBuildFlavor`設為 null，工作站組建已載入。</span><span class="sxs-lookup"><span data-stu-id="83526-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="83526-120">單一處理器電腦上執行時，會一律載入工作站組建，即使`pwszBuildFlavor`設為`svr`。</span><span class="sxs-lookup"><span data-stu-id="83526-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="83526-121">不過，如果`pwszBuildFlavor`設為`svr`以及指定並行記憶體回收 (請參閱說明，`flags`參數)，會載入伺服器組建。</span><span class="sxs-lookup"><span data-stu-id="83526-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="83526-122">[in]`CLSID`的實作的 coclass [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)或[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="83526-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="83526-123">支援的值為 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="83526-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="83526-124">[in]`IID`的要求的介面，從`rclsid`。</span><span class="sxs-lookup"><span data-stu-id="83526-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="83526-125">支援的值為 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="83526-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="83526-126">[out]若要傳回的介面指標`riid`。</span><span class="sxs-lookup"><span data-stu-id="83526-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83526-127">備註</span><span class="sxs-lookup"><span data-stu-id="83526-127">Remarks</span></span>  
 <span data-ttu-id="83526-128">如果`pwszVersion`指定不存在，執行階段版本`CorBindToRuntimeEx`傳回 CLR_E_SHIM_RUNTIMELOAD HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="83526-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="83526-129">執行內容和流程的 Windows 身分識別</span><span class="sxs-lookup"><span data-stu-id="83526-129">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="83526-130">在第 1 版的 clr，<xref:System.Security.Principal.WindowsIdentity>物件不會流經非同步點，例如新的執行緒、 執行緒集區或計時器回呼。</span><span class="sxs-lookup"><span data-stu-id="83526-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="83526-131">在 2.0 版中的 clr，<xref:System.Threading.ExecutionContext>物件包裝目前執行中執行緒的一些資訊，並跨任何非同步點，但不是會在應用程式定義域界限之間流動它。</span><span class="sxs-lookup"><span data-stu-id="83526-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="83526-132">同樣地，<xref:System.Security.Principal.WindowsIdentity>物件也會流過任何非同步點。</span><span class="sxs-lookup"><span data-stu-id="83526-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="83526-133">因此，目前的模擬執行緒，如果有的話，會流動。</span><span class="sxs-lookup"><span data-stu-id="83526-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="83526-134">您可以變更流程有兩種：</span><span class="sxs-lookup"><span data-stu-id="83526-134">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="83526-135">藉由修改<xref:System.Threading.ExecutionContext>若要隱藏個別的執行緒上的流程的設定 (請參閱 < <xref:System.Threading.ExecutionContext.SuppressFlow%2A>， <xref:System.Security.SecurityContext.SuppressFlow%2A>，和<xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A>方法)。</span><span class="sxs-lookup"><span data-stu-id="83526-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="83526-136">藉由處理程序的預設模式變更為 「 第 1 版相容性模式中，其中<xref:System.Security.Principal.WindowsIdentity>物件不會流經任何非同步點，無論<xref:System.Threading.ExecutionContext>目前執行緒上的設定。</span><span class="sxs-lookup"><span data-stu-id="83526-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="83526-137">您要如何變更預設的模式取決於您是使用 managed 可執行檔或未受管理的裝載介面載入 CLR:</span><span class="sxs-lookup"><span data-stu-id="83526-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="83526-138">受管理的可執行檔，您必須設定`enabled`的屬性[ \<legacyImpersonationPolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)項目`true`。</span><span class="sxs-lookup"><span data-stu-id="83526-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="83526-139">Unmanaged 裝載介面，設定`STARTUP_LEGACY_IMPERSONATION`中的旗標`flags`參數呼叫時`CorBindToRuntimeEx`函式。</span><span class="sxs-lookup"><span data-stu-id="83526-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="83526-140">第 1 版相容性模式適用於整個程序和程序中的所有應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="83526-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83526-141">備註</span><span class="sxs-lookup"><span data-stu-id="83526-141">Remarks</span></span>  
 <span data-ttu-id="83526-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)並`CorBindToRuntime`執行相同的作業，但`CorBindToRuntimeEx`函式可讓您設定旗標指定 CLR 的行為。</span><span class="sxs-lookup"><span data-stu-id="83526-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83526-143">需求</span><span class="sxs-lookup"><span data-stu-id="83526-143">Requirements</span></span>  
 <span data-ttu-id="83526-144">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="83526-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83526-145">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="83526-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="83526-146">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="83526-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83526-147">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83526-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83526-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83526-148">See also</span></span>

- [<span data-ttu-id="83526-149">CorBindToCurrentRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="83526-149">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="83526-150">CorBindToRuntimeByCfg 函式</span><span class="sxs-lookup"><span data-stu-id="83526-150">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="83526-151">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="83526-151">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="83526-152">CorBindToRuntimeHost 函式</span><span class="sxs-lookup"><span data-stu-id="83526-152">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="83526-153">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="83526-153">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="83526-154">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="83526-154">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
