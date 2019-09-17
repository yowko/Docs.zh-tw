---
title: CorBindToRuntimeHost 函式
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeHost
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeHost
helpviewer_keywords:
- CorBindToRuntimeHost function [.NET Framework hosting]
ms.assetid: 5c826ba3-8258-49bc-a417-78807915fcaf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7e1965917e8a1c5ae07cf119df3664b969a979be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969243"
---
# <a name="corbindtoruntimehost-function"></a><span data-ttu-id="4c7be-102">CorBindToRuntimeHost 函式</span><span class="sxs-lookup"><span data-stu-id="4c7be-102">CorBindToRuntimeHost Function</span></span>
<span data-ttu-id="4c7be-103">讓主機將指定版本的 common language runtime （CLR）載入進程中。</span><span class="sxs-lookup"><span data-stu-id="4c7be-103">Enables hosts to load a specified version of the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="4c7be-104">此函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="4c7be-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c7be-105">語法</span><span class="sxs-lookup"><span data-stu-id="4c7be-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntimeHost (  
    [in] LPCWSTR       pwszVersion,   
    [in] LPCWSTR       pwszBuildFlavor,   
    [in] LPCWSTR       pwszHostConfigFile,   
    [in] VOID*         pReserved,   
    [in] DWORD         startupFlags,   
    [in] REFCLSID      rclsid,   
    [in] REFIID        riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c7be-106">參數</span><span class="sxs-lookup"><span data-stu-id="4c7be-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="4c7be-107">在描述您要載入之 CLR 版本的字串。</span><span class="sxs-lookup"><span data-stu-id="4c7be-107">[in] A string that describes the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="4c7be-108">.NET Framework 中的版本號碼包含四個以句點分隔的部分： [主要]. [*次要. 組建. 修訂*]。</span><span class="sxs-lookup"><span data-stu-id="4c7be-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="4c7be-109">傳遞為`pwszVersion`的字串必須以字元 "v" 開頭，後面接著版本號碼的前三個部分（例如 "v 1.0.1529"）。</span><span class="sxs-lookup"><span data-stu-id="4c7be-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="4c7be-110">某些 CLR 版本會與原則語句一起安裝，以指定與舊版 CLR 的相容性。</span><span class="sxs-lookup"><span data-stu-id="4c7be-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="4c7be-111">根據預設，啟動填充碼會`pwszVersion`針對原則語句評估，並載入與所要求版本相容的最新執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="4c7be-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="4c7be-112">主機可以強制填充碼略過原則評估，並藉`pwszVersion`由傳遞`startupFlags`參數的 STARTUP_LOADER_SAFEMODE 值來載入所指定的確切版本。</span><span class="sxs-lookup"><span data-stu-id="4c7be-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of STARTUP_LOADER_SAFEMODE for the `startupFlags` parameter.</span></span>  
  
 <span data-ttu-id="4c7be-113">如果`pwszVersion` 是`null,` ，則方法不會載入任何版本的 CLR。</span><span class="sxs-lookup"><span data-stu-id="4c7be-113">If `pwszVersion` is `null,` the method does not load any version of the CLR.</span></span> <span data-ttu-id="4c7be-114">相反地，它會傳回 CLR_E_SHIM_RUNTIMELOAD，這表示它無法載入執行時間。</span><span class="sxs-lookup"><span data-stu-id="4c7be-114">Instead, it returns CLR_E_SHIM_RUNTIMELOAD, which indicates that it failed to load the runtime.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="4c7be-115">在字串，指定是否要載入伺服器或 CLR 的工作站組建。</span><span class="sxs-lookup"><span data-stu-id="4c7be-115">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="4c7be-116">有效值為 `svr` 和 `wks`。</span><span class="sxs-lookup"><span data-stu-id="4c7be-116">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="4c7be-117">伺服器組建已優化，可利用多個處理器進行垃圾收集，而且工作站組建已針對在單處理器機器上執行的用戶端應用程式優化。</span><span class="sxs-lookup"><span data-stu-id="4c7be-117">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="4c7be-118">如果`pwszBuildFlavor`設定為 null，則會載入工作站組建。</span><span class="sxs-lookup"><span data-stu-id="4c7be-118">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="4c7be-119">在單處理器機器上執行時，一律會載入工作站組建，即使設定為`pwszBuildFlavor` `svr`也一樣。</span><span class="sxs-lookup"><span data-stu-id="4c7be-119">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="4c7be-120">不過，如果`pwszBuildFlavor`設定為`svr` ，且指定了並行垃圾收集（ `startupFlags`請參閱參數的描述），則會載入伺服器組建。</span><span class="sxs-lookup"><span data-stu-id="4c7be-120">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4c7be-121">在執行 Intel Itanium 架構（先前稱為 IA-64）的64位系統上執行 WOW64 x86 模擬器的應用程式不支援並行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="4c7be-121">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="4c7be-122">如需在64位 Windows 系統上使用 WOW64 的詳細資訊，請參閱執行[32 位應用程式](/windows/desktop/WinProg64/running-32-bit-applications)。</span><span class="sxs-lookup"><span data-stu-id="4c7be-122">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
 `pwszHostConfigFile`  
 <span data-ttu-id="4c7be-123">在主機設定檔的名稱，指定要載入的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="4c7be-123">[in] The name of a host configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="4c7be-124">如果檔案名不包含完整路徑，則會假設檔案與進行呼叫的可執行檔位於相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="4c7be-124">If the file name does not include a fully qualified path, the file is assumed to be in the same directory as the executable that is making the call.</span></span>  
  
 `pReserved`  
 <span data-ttu-id="4c7be-125">在保留以供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="4c7be-125">[in] Reserved for future extensibility.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="4c7be-126">在一組旗標，可控制並行垃圾收集、網域中性程式碼，以及`pwszVersion`參數的行為。</span><span class="sxs-lookup"><span data-stu-id="4c7be-126">[in] A set of flags that controls concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="4c7be-127">如果未設定旗標，則預設值為單一網域。</span><span class="sxs-lookup"><span data-stu-id="4c7be-127">The default is single domain if no flag is set.</span></span> <span data-ttu-id="4c7be-128">如需支援值的清單，請參閱[STARTUP_FLAGS 列舉](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="4c7be-128">For a list of supported values, see the [STARTUP_FLAGS enumeration](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>  
  
 `rclsid`  
 <span data-ttu-id="4c7be-129">在Coclass 的，其會執行 [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) 或 [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) 介面。`CLSID`</span><span class="sxs-lookup"><span data-stu-id="4c7be-129">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="4c7be-130">支援的值為 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="4c7be-130">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="4c7be-131">在您所要求之介面的。 `IID`</span><span class="sxs-lookup"><span data-stu-id="4c7be-131">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="4c7be-132">支援的值為 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="4c7be-132">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="4c7be-133">脫銷載入的執行階段版本的介面指標。</span><span class="sxs-lookup"><span data-stu-id="4c7be-133">[out] An interface pointer to the version of the runtime that was loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c7be-134">需求</span><span class="sxs-lookup"><span data-stu-id="4c7be-134">Requirements</span></span>  
 <span data-ttu-id="4c7be-135">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4c7be-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c7be-136">**標頭：** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="4c7be-136">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="4c7be-137">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4c7be-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4c7be-138">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c7be-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c7be-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c7be-139">See also</span></span>

- [<span data-ttu-id="4c7be-140">CorBindToCurrentRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="4c7be-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="4c7be-141">CorBindToRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="4c7be-141">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="4c7be-142">CorBindToRuntimeByCfg 函式</span><span class="sxs-lookup"><span data-stu-id="4c7be-142">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="4c7be-143">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="4c7be-143">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="4c7be-144">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="4c7be-144">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="4c7be-145">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="4c7be-145">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
