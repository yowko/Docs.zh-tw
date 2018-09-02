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
ms.openlocfilehash: 1952121a6c0c735926944c839c3c7e8a8db5fb53
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43396827"
---
# <a name="corbindtoruntimehost-function"></a><span data-ttu-id="26584-102">CorBindToRuntimeHost 函式</span><span class="sxs-lookup"><span data-stu-id="26584-102">CorBindToRuntimeHost Function</span></span>
<span data-ttu-id="26584-103">可讓主機以指定的 common language runtime (CLR) 版本載入處理序。</span><span class="sxs-lookup"><span data-stu-id="26584-103">Enables hosts to load a specified version of the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="26584-104">此函式中的過時[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="26584-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26584-105">語法</span><span class="sxs-lookup"><span data-stu-id="26584-105">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="26584-106">參數</span><span class="sxs-lookup"><span data-stu-id="26584-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="26584-107">[in]字串，描述您想要載入的 clr 版本。</span><span class="sxs-lookup"><span data-stu-id="26584-107">[in] A string that describes the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="26584-108">在.NET Framework 的版本號碼是由以句點分隔的四個部分所組成： *major.minor.build.revision*。</span><span class="sxs-lookup"><span data-stu-id="26584-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="26584-109">將字串傳遞為`pwszVersion`不可使用字元"v"後面接著的版本號碼 (例如，"v1.0.1529 」) 的前三個部分。</span><span class="sxs-lookup"><span data-stu-id="26584-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="26584-110">某些版本的 CLR 會以指定與舊版的 clr 相容的原則陳述式安裝。</span><span class="sxs-lookup"><span data-stu-id="26584-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="26584-111">根據預設，啟動填充碼會評估`pwszVersion`針對原則陳述式並載入最新版本的執行階段，是與所要求的版本相容。</span><span class="sxs-lookup"><span data-stu-id="26584-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="26584-112">主機可以強制填充碼略過原則評估，並載入指定的確切版本`pwszVersion`藉由傳遞值的 STARTUP_LOADER_SAFEMODE`startupFlags`參數。</span><span class="sxs-lookup"><span data-stu-id="26584-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of STARTUP_LOADER_SAFEMODE for the `startupFlags` parameter.</span></span>  
  
 <span data-ttu-id="26584-113">如果`pwszVersion`是`null,`方法不會載入任何版本的 CLR。</span><span class="sxs-lookup"><span data-stu-id="26584-113">If `pwszVersion` is `null,` the method does not load any version of the CLR.</span></span> <span data-ttu-id="26584-114">相反地，它會傳回 CLR_E_SHIM_RUNTIMELOAD，表示它無法載入執行階段。</span><span class="sxs-lookup"><span data-stu-id="26584-114">Instead, it returns CLR_E_SHIM_RUNTIMELOAD, which indicates that it failed to load the runtime.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="26584-115">[in]字串，指定是否要載入的伺服器或工作站組建的 clr。</span><span class="sxs-lookup"><span data-stu-id="26584-115">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="26584-116">有效值為 `svr` 和 `wks`。</span><span class="sxs-lookup"><span data-stu-id="26584-116">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="26584-117">伺服器組建已最佳化，可利用多個處理器的記憶體回收，以及工作站建置適用於單一處理器電腦上執行的用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="26584-117">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="26584-118">如果`pwszBuildFlavor`設為 null，工作站組建已載入。</span><span class="sxs-lookup"><span data-stu-id="26584-118">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="26584-119">單一處理器電腦上執行時，會一律載入工作站組建，即使`pwszBuildFlavor`設為`svr`。</span><span class="sxs-lookup"><span data-stu-id="26584-119">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="26584-120">不過，如果`pwszBuildFlavor`設為`svr`以及指定並行記憶體回收 (請參閱說明，`startupFlags`參數)，會載入伺服器組建。</span><span class="sxs-lookup"><span data-stu-id="26584-120">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26584-121">執行 WOW64 的應用程式中不支援並行記憶體回收 x86 實作 Intel Itanium 架構 （先前稱為 IA-64） 的 64 位元系統上的模擬器。</span><span class="sxs-lookup"><span data-stu-id="26584-121">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="26584-122">如需在 64 位元 Windows 系統上使用 WOW64 的詳細資訊，請參閱[執行的 32 位元應用程式](/windows/desktop/WinProg64/running-32-bit-applications)。</span><span class="sxs-lookup"><span data-stu-id="26584-122">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
 `pwszHostConfigFile`  
 <span data-ttu-id="26584-123">[in]指定要載入的 clr 版本的主機組態檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="26584-123">[in] The name of a host configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="26584-124">如果檔案名稱不包含完整的路徑，則會假設檔案是與正在進行呼叫之可執行檔相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="26584-124">If the file name does not include a fully qualified path, the file is assumed to be in the same directory as the executable that is making the call.</span></span>  
  
 `pReserved`  
 <span data-ttu-id="26584-125">[in]保留供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="26584-125">[in] Reserved for future extensibility.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="26584-126">[in]一組控制並行記憶體回收、 定義域中性程式碼和行為的旗標`pwszVersion`參數。</span><span class="sxs-lookup"><span data-stu-id="26584-126">[in] A set of flags that controls concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="26584-127">如果沒有旗標設定，則預設會為單一網域。</span><span class="sxs-lookup"><span data-stu-id="26584-127">The default is single domain if no flag is set.</span></span> <span data-ttu-id="26584-128">如需支援的值，請參閱[STARTUP_FLAGS 列舉](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="26584-128">For a list of supported values, see the [STARTUP_FLAGS enumeration](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>  
  
 `rclsid`  
 <span data-ttu-id="26584-129">[in]`CLSID`的實作的 coclass [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)或[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="26584-129">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="26584-130">支援的值為 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="26584-130">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="26584-131">[in]`IID`您所要求的介面。</span><span class="sxs-lookup"><span data-stu-id="26584-131">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="26584-132">支援的值為 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="26584-132">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="26584-133">[out]已載入的執行階段版本介面指標。</span><span class="sxs-lookup"><span data-stu-id="26584-133">[out] An interface pointer to the version of the runtime that was loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26584-134">需求</span><span class="sxs-lookup"><span data-stu-id="26584-134">Requirements</span></span>  
 <span data-ttu-id="26584-135">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="26584-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26584-136">**標頭：** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="26584-136">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="26584-137">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="26584-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26584-138">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26584-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26584-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26584-139">See Also</span></span>  
 [<span data-ttu-id="26584-140">CorBindToCurrentRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="26584-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="26584-141">CorBindToRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="26584-141">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [<span data-ttu-id="26584-142">CorBindToRuntimeByCfg 函式</span><span class="sxs-lookup"><span data-stu-id="26584-142">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="26584-143">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="26584-143">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="26584-144">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="26584-144">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="26584-145">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="26584-145">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
