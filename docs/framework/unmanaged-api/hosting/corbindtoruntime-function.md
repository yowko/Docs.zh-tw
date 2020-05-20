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
ms.openlocfilehash: 0bcfe42a70d64c091851a1eec81d03e49dbde52b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616657"
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="5b3a5-102">CorBindToRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="5b3a5-102">CorBindToRuntime Function</span></span>
<span data-ttu-id="5b3a5-103">讓非受控主機將 common language runtime （CLR）載入進程中。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="5b3a5-104">此函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b3a5-105">語法</span><span class="sxs-lookup"><span data-stu-id="5b3a5-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,
    [in]  LPCWSTR     pwszBuildFlavor,
    [in]  REFCLSID    rclsid,
    [in]  REFIID      riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b3a5-106">參數</span><span class="sxs-lookup"><span data-stu-id="5b3a5-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="5b3a5-107">在描述您要載入之 CLR 版本的字串。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="5b3a5-108">.NET Framework 中的版本號碼包含四個以句點分隔的部分： [主要]. [*次要. 組建. 修訂*]。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="5b3a5-109">傳遞為的字串 `pwszVersion` 必須以字元 "v" 開頭，後面接著版本號碼的前三個部分（例如 "v 1.0.1529"）。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="5b3a5-110">某些 CLR 版本會與原則語句一起安裝，以指定與舊版 CLR 的相容性。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="5b3a5-111">根據預設，啟動填充碼 `pwszVersion` 會針對原則語句評估，並載入與所要求版本相容的最新執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="5b3a5-112">主機可以強制填充碼略過原則評估，並藉由傳遞參數的值來載入中所指定的確切版本 `pwszVersion` `STARTUP_LOADER_SAFEMODE` `flags` ，如下所述。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="5b3a5-113">如果呼叫端針對指定 null `pwszVersion` ，則會載入最新版本的執行時間。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="5b3a5-114">傳遞 null 可讓主機無法控制載入的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="5b3a5-115">雖然這種方法可能適用于某些情況，但強烈建議主機提供要載入的特定版本。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="5b3a5-116">在字串，指定是否要載入伺服器或 CLR 的工作站組建。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="5b3a5-117">有效值為 `svr` 和 `wks`。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="5b3a5-118">伺服器組建已優化，可利用多個處理器進行垃圾收集，而且工作站組建已針對在單處理器機器上執行的用戶端應用程式優化。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="5b3a5-119">如果 `pwszBuildFlavor` 設定為 null，則會載入工作站組建。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="5b3a5-120">在單處理器機器上執行時，一律會載入工作站組建，即使 `pwszBuildFlavor` 設定為也一樣 `svr` 。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="5b3a5-121">不過，如果 `pwszBuildFlavor` 設定為 `svr` ，且指定了並行垃圾收集（請參閱參數的描述 `flags` ），則會載入伺服器組建。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="5b3a5-122">在Coclass 的，其 `CLSID` 會執行[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)或[ICLRRuntimeHost](iclrruntimehost-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="5b3a5-123">支援的值為 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="5b3a5-124">在`IID`從所要求之介面的 `rclsid` 。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="5b3a5-125">支援的值為 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="5b3a5-126">脫銷傳回的介面指標 `riid` 。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b3a5-127">備註</span><span class="sxs-lookup"><span data-stu-id="5b3a5-127">Remarks</span></span>  
 <span data-ttu-id="5b3a5-128">如果 `pwszVersion` 指定不存在的執行階段版本，則會傳回 `CorBindToRuntimeEx` CLR_E_SHIM_RUNTIMELOAD 的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="5b3a5-129">執行內容和 Windows 身分識別流程</span><span class="sxs-lookup"><span data-stu-id="5b3a5-129">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="5b3a5-130">在 CLR 的第1版中， <xref:System.Security.Principal.WindowsIdentity> 物件不會流經非同步點，例如新執行緒、執行緒集區或計時器回呼。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="5b3a5-131">在 CLR 的版本2.0 中， <xref:System.Threading.ExecutionContext> 物件會包裝目前執行中線程的一些相關資訊，並將其流經任何非同步點，但不會跨越應用程式域界限。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="5b3a5-132">同樣地， <xref:System.Security.Principal.WindowsIdentity> 物件也會流經任何非同步點。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="5b3a5-133">因此，執行緒上目前的模擬（如果有的話）也會流動。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="5b3a5-134">您可以透過兩種方式來改變流程：</span><span class="sxs-lookup"><span data-stu-id="5b3a5-134">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="5b3a5-135">藉由修改 <xref:System.Threading.ExecutionContext> 設定來隱藏每個執行緒的流程（請參閱 <xref:System.Threading.ExecutionContext.SuppressFlow%2A> 、 <xref:System.Security.SecurityContext.SuppressFlow%2A> 和 <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> 方法）。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="5b3a5-136">將進程預設模式變更為版本1相容性模式，其中物件不 <xref:System.Security.Principal.WindowsIdentity> 會流經任何非同步點，而不論 <xref:System.Threading.ExecutionContext> 目前線程上的設定為何。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="5b3a5-137">您變更預設模式的方式，取決於您使用的是受控可執行檔或非受控裝載介面來載入 CLR：</span><span class="sxs-lookup"><span data-stu-id="5b3a5-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="5b3a5-138">對於受控可執行檔，您必須將 `enabled` [ \< legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)專案的屬性設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="5b3a5-139">若為非受控裝載介面，請在呼叫函式時，于 `STARTUP_LEGACY_IMPERSONATION` 參數中設定旗標 `flags` `CorBindToRuntimeEx` 。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="5b3a5-140">版本1相容性模式適用于整個進程和進程中的所有應用程式域。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b3a5-141">備註</span><span class="sxs-lookup"><span data-stu-id="5b3a5-141">Remarks</span></span>  
 <span data-ttu-id="5b3a5-142">[CorBindToRuntimeEx](corbindtoruntimeex-function.md)並 `CorBindToRuntime` 執行相同的作業，但函式可 `CorBindToRuntimeEx` 讓您設定旗標來指定 CLR 的行為。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-142">[CorBindToRuntimeEx](corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b3a5-143">需求</span><span class="sxs-lookup"><span data-stu-id="5b3a5-143">Requirements</span></span>  
 <span data-ttu-id="5b3a5-144">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5b3a5-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b3a5-145">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="5b3a5-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5b3a5-146">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="5b3a5-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5b3a5-147">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b3a5-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b3a5-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b3a5-148">See also</span></span>

- [<span data-ttu-id="5b3a5-149">CorBindToCurrentRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="5b3a5-149">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="5b3a5-150">CorBindToRuntimeByCfg 函式</span><span class="sxs-lookup"><span data-stu-id="5b3a5-150">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="5b3a5-151">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="5b3a5-151">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="5b3a5-152">CorBindToRuntimeHost 函式</span><span class="sxs-lookup"><span data-stu-id="5b3a5-152">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="5b3a5-153">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="5b3a5-153">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="5b3a5-154">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="5b3a5-154">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
