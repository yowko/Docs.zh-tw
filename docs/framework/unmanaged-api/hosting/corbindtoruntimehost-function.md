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
ms.openlocfilehash: 6566adc442034763e0209869404b60b5afa63866
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176483"
---
# <a name="corbindtoruntimehost-function"></a><span data-ttu-id="2204c-102">CorBindToRuntimeHost 函式</span><span class="sxs-lookup"><span data-stu-id="2204c-102">CorBindToRuntimeHost Function</span></span>
<span data-ttu-id="2204c-103">使主機能夠將指定版本的通用語言運行時 （CLR） 載入到進程中。</span><span class="sxs-lookup"><span data-stu-id="2204c-103">Enables hosts to load a specified version of the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="2204c-104">此功能已在 .NET 框架 4 中棄用。</span><span class="sxs-lookup"><span data-stu-id="2204c-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2204c-105">語法</span><span class="sxs-lookup"><span data-stu-id="2204c-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="2204c-106">參數</span><span class="sxs-lookup"><span data-stu-id="2204c-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="2204c-107">[在]描述要載入的 CLR 版本的字串。</span><span class="sxs-lookup"><span data-stu-id="2204c-107">[in] A string that describes the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="2204c-108">.NET 框架中的版本號由四個部分組成，由句點分隔：*主要.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="2204c-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="2204c-109">傳遞的`pwszVersion`字串必須以字元"v"開頭，後跟版本號的前三個部分（例如，"v1.0.1529"）。</span><span class="sxs-lookup"><span data-stu-id="2204c-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="2204c-110">CLR 的某些版本都安裝了策略語句，該語句指定與 CLR 的早期版本的相容性。</span><span class="sxs-lookup"><span data-stu-id="2204c-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="2204c-111">預設情況下，啟動希姆`pwszVersion`根據策略語句進行評估，並載入與所請求版本相容的最新版本的運行時。</span><span class="sxs-lookup"><span data-stu-id="2204c-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="2204c-112">主機可以通過傳遞`startupFlags`參數的STARTUP_LOADER_SAFEMODE值來強制 him 跳過策略評估並載入指定`pwszVersion`的確切版本。</span><span class="sxs-lookup"><span data-stu-id="2204c-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of STARTUP_LOADER_SAFEMODE for the `startupFlags` parameter.</span></span>  
  
 <span data-ttu-id="2204c-113">如果`pwszVersion`是`null,`，該方法不會載入 CLR 的任何版本。</span><span class="sxs-lookup"><span data-stu-id="2204c-113">If `pwszVersion` is `null,` the method does not load any version of the CLR.</span></span> <span data-ttu-id="2204c-114">相反，它將返回CLR_E_SHIM_RUNTIMELOAD，這表明它無法載入運行時。</span><span class="sxs-lookup"><span data-stu-id="2204c-114">Instead, it returns CLR_E_SHIM_RUNTIMELOAD, which indicates that it failed to load the runtime.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="2204c-115">[在]指定是載入 CLR 的伺服器還是工作站構建的字串。</span><span class="sxs-lookup"><span data-stu-id="2204c-115">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="2204c-116">有效值為 `svr` 和 `wks`。</span><span class="sxs-lookup"><span data-stu-id="2204c-116">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="2204c-117">伺服器生成經過優化，以利用多個處理器進行垃圾回收，工作站生成針對在單處理器電腦上運行的用戶端應用程式進行了優化。</span><span class="sxs-lookup"><span data-stu-id="2204c-117">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="2204c-118">如果`pwszBuildFlavor`設置為 null，則載入工作站生成。</span><span class="sxs-lookup"><span data-stu-id="2204c-118">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="2204c-119">在單處理器電腦上運行時，工作站生成始終載入，即使`pwszBuildFlavor`設置為`svr`。</span><span class="sxs-lookup"><span data-stu-id="2204c-119">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="2204c-120">但是，如果`pwszBuildFlavor`設置為`svr`並指定了併發垃圾回收（請參閱`startupFlags`參數的說明），則載入伺服器生成。</span><span class="sxs-lookup"><span data-stu-id="2204c-120">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2204c-121">在 64 位系統上運行 WOW64 x86 模擬器的應用程式不支援併發垃圾回收，這些系統實現了英特爾 Itanium 架構（以前稱為 IA-64）。</span><span class="sxs-lookup"><span data-stu-id="2204c-121">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="2204c-122">有關在 64 位 Windows 系統上使用 WOW64 的詳細資訊，請參閱[運行 32 位應用程式](/windows/desktop/WinProg64/running-32-bit-applications)。</span><span class="sxs-lookup"><span data-stu-id="2204c-122">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
 `pwszHostConfigFile`  
 <span data-ttu-id="2204c-123">[在]指定要載入的 CLR 版本的主機設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="2204c-123">[in] The name of a host configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="2204c-124">如果檔案名不包含完全限定的路徑，則假定該檔與進行調用的可執行檔位於同一目錄中。</span><span class="sxs-lookup"><span data-stu-id="2204c-124">If the file name does not include a fully qualified path, the file is assumed to be in the same directory as the executable that is making the call.</span></span>  
  
 `pReserved`  
 <span data-ttu-id="2204c-125">[在]保留以供將來擴展。</span><span class="sxs-lookup"><span data-stu-id="2204c-125">[in] Reserved for future extensibility.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="2204c-126">[在]控制併發垃圾回收、域中立代碼和`pwszVersion`參數行為的標誌集。</span><span class="sxs-lookup"><span data-stu-id="2204c-126">[in] A set of flags that controls concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="2204c-127">如果未設置標誌，則預設值為單個域。</span><span class="sxs-lookup"><span data-stu-id="2204c-127">The default is single domain if no flag is set.</span></span> <span data-ttu-id="2204c-128">有關受支援值的清單，請參閱[STARTUP_FLAGS枚舉](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="2204c-128">For a list of supported values, see the [STARTUP_FLAGS enumeration](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>  
  
 `rclsid`  
 <span data-ttu-id="2204c-129">[在]`CLSID`實現[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)或[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)介面的共類。</span><span class="sxs-lookup"><span data-stu-id="2204c-129">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="2204c-130">支援的值CLSID_CorRuntimeHost或CLSID_CLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="2204c-130">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="2204c-131">[在]您`IID`請求的介面的。</span><span class="sxs-lookup"><span data-stu-id="2204c-131">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="2204c-132">支援的值IID_ICorRuntimeHost或IID_ICLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="2204c-132">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="2204c-133">[出]指向載入的執行階段版本的介面指標。</span><span class="sxs-lookup"><span data-stu-id="2204c-133">[out] An interface pointer to the version of the runtime that was loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2204c-134">需求</span><span class="sxs-lookup"><span data-stu-id="2204c-134">Requirements</span></span>  
 <span data-ttu-id="2204c-135">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2204c-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2204c-136">**標題：** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="2204c-136">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="2204c-137">**庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2204c-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2204c-138">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2204c-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2204c-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2204c-139">See also</span></span>

- [<span data-ttu-id="2204c-140">CorBindToCurrentRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="2204c-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="2204c-141">CorBindToRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="2204c-141">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="2204c-142">CorBindToRuntimeByCfg 函式</span><span class="sxs-lookup"><span data-stu-id="2204c-142">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="2204c-143">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="2204c-143">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="2204c-144">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="2204c-144">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="2204c-145">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="2204c-145">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
