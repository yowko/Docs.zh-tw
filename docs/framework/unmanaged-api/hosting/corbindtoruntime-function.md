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
ms.openlocfilehash: 426e95281b648217642ca06f04dfbd9ec991221e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733772"
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="3f8a3-102">CorBindToRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="3f8a3-102">CorBindToRuntime Function</span></span>

<span data-ttu-id="3f8a3-103">讓非受控主機將 common language runtime (CLR) 載入至進程。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="3f8a3-104">此函式已在 .NET Framework 4 中被取代。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f8a3-105">語法</span><span class="sxs-lookup"><span data-stu-id="3f8a3-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,
    [in]  LPCWSTR     pwszBuildFlavor,
    [in]  REFCLSID    rclsid,
    [in]  REFIID      riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f8a3-106">參數</span><span class="sxs-lookup"><span data-stu-id="3f8a3-106">Parameters</span></span>  

 `pwszVersion`  
 <span data-ttu-id="3f8a3-107">在字串，描述您想要載入的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="3f8a3-108">.NET Framework 中的版本號碼包含四個以句號分隔的部分： *主要.*...............。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="3f8a3-109">傳遞的字串 `pwszVersion` 必須以字元 "v" 開頭，後面接著第三個版本號碼部分 (例如 "v 1.0.1529" ) 。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="3f8a3-110">某些版本的 CLR 會與指定 CLR 舊版相容性的原則語句一起安裝。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="3f8a3-111">根據預設，啟動填充碼 `pwszVersion` 會針對原則語句進行評估，並載入與所要求版本相容的最新執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="3f8a3-112">主機可以強制填充碼略過原則評估，並藉由傳遞參數的值來載入指定的確切版本 `pwszVersion`  `STARTUP_LOADER_SAFEMODE` `flags` ，如下所述。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="3f8a3-113">如果呼叫端對指定 null `pwszVersion` ，則會載入執行時間的最新版本。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="3f8a3-114">傳遞 null 可讓主機無法控制載入的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="3f8a3-115">雖然此方法可能適用于某些情況，但強烈建議主機提供要載入的特定版本。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="3f8a3-116">在字串，指定是否要載入伺服器或 CLR 的工作站組建。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="3f8a3-117">有效值為 `svr` 和 `wks`。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="3f8a3-118">伺服器組建經過優化，可利用多個處理器進行垃圾收集，而且工作站組建已針對在單處理器電腦上執行的用戶端應用程式優化。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="3f8a3-119">如果 `pwszBuildFlavor` 設定為 null，就會載入工作站組建。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="3f8a3-120">在單處理器電腦上執行時，一律會載入工作站組建，即使 `pwszBuildFlavor` 設定為 `svr` 。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="3f8a3-121">但是，如果 `pwszBuildFlavor` 設定為 `svr` ，而且指定了並行垃圾收集 (請參閱 `flags`) 的參數描述，就會載入伺服器組建。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="3f8a3-122">在Coclass 的， `CLSID` 可執行 [ICorRuntimeHost](icorruntimehost-interface.md) 或 [ICLRRuntimeHost](iclrruntimehost-interface.md) 介面。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="3f8a3-123">支援的值為 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="3f8a3-124">在所 `IID` 要求介面的 `rclsid` 。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="3f8a3-125">支援的值為 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="3f8a3-126">擴展傳回的介面指標 `riid` 。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f8a3-127">備註</span><span class="sxs-lookup"><span data-stu-id="3f8a3-127">Remarks</span></span>  

 <span data-ttu-id="3f8a3-128">如果 `pwszVersion` 指定不存在的執行階段版本，則會傳回 `CorBindToRuntimeEx` CLR_E_SHIM_RUNTIMELOAD 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="3f8a3-129">執行內容和 Windows 身分識別的流程</span><span class="sxs-lookup"><span data-stu-id="3f8a3-129">Execution Context and Flow of Windows Identity</span></span>  

 <span data-ttu-id="3f8a3-130">在 CLR 的第1版中， <xref:System.Security.Principal.WindowsIdentity> 物件不會在非同步點（例如新執行緒、執行緒集區或計時器回呼）之間流動。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="3f8a3-131">在 CLR 的2.0 版中， <xref:System.Threading.ExecutionContext> 物件會包裝有關目前執行中線程的一些資訊，並將其流經任何非同步點，而不是跨應用程式域界限。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="3f8a3-132">同樣地，此 <xref:System.Security.Principal.WindowsIdentity> 物件也會在任何非同步點之間流動。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="3f8a3-133">因此，執行緒上目前的模擬（如果有的話）也會流程。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="3f8a3-134">您可以透過兩種方式來變更流程：</span><span class="sxs-lookup"><span data-stu-id="3f8a3-134">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="3f8a3-135">藉由修改 <xref:System.Threading.ExecutionContext> 設定以針對每個執行緒隱藏流程 (查看 <xref:System.Threading.ExecutionContext.SuppressFlow%2A> 、 <xref:System.Security.SecurityContext.SuppressFlow%2A> 和 <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> 方法) 。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="3f8a3-136">藉由將進程預設模式變更為第1版的相容性模式，其中 <xref:System.Security.Principal.WindowsIdentity> 物件不會流經任何非同步點，而不論 <xref:System.Threading.ExecutionContext> 目前線程上的設定為何。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="3f8a3-137">變更預設模式的方式取決於您是使用 managed 可執行檔或非受控裝載介面載入 CLR：</span><span class="sxs-lookup"><span data-stu-id="3f8a3-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="3f8a3-138">針對 managed 可執行檔，您必須將 `enabled` 元素的屬性設定 [\<legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) 為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="3f8a3-139">若為非受控裝載介面，請在呼叫函式時，于 `STARTUP_LEGACY_IMPERSONATION` 參數中設定旗標 `flags` `CorBindToRuntimeEx` 。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="3f8a3-140">第1版的相容性模式會套用至整個進程，以及處理常式中的所有應用程式域。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f8a3-141">備註</span><span class="sxs-lookup"><span data-stu-id="3f8a3-141">Remarks</span></span>  

 <span data-ttu-id="3f8a3-142">[CorBindToRuntimeEx](corbindtoruntimeex-function.md) 和 `CorBindToRuntime` 執行相同的作業，但 `CorBindToRuntimeEx` 函數可讓您設定旗標來指定 CLR 的行為。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-142">[CorBindToRuntimeEx](corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f8a3-143">需求</span><span class="sxs-lookup"><span data-stu-id="3f8a3-143">Requirements</span></span>  

 <span data-ttu-id="3f8a3-144">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3f8a3-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f8a3-145">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="3f8a3-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3f8a3-146">連結 **庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3f8a3-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3f8a3-147">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f8a3-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f8a3-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f8a3-148">See also</span></span>

- [<span data-ttu-id="3f8a3-149">CorBindToCurrentRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="3f8a3-149">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="3f8a3-150">CorBindToRuntimeByCfg 函式</span><span class="sxs-lookup"><span data-stu-id="3f8a3-150">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="3f8a3-151">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="3f8a3-151">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="3f8a3-152">CorBindToRuntimeHost 函式</span><span class="sxs-lookup"><span data-stu-id="3f8a3-152">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="3f8a3-153">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="3f8a3-153">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="3f8a3-154">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="3f8a3-154">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
