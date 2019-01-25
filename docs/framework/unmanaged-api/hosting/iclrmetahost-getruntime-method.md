---
title: ICLRMetaHost::GetRuntime 方法
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetRuntime
helpviewer_keywords:
- GetRuntime method [.NET Framework hosting]
- ICLRMetaHost::GetRuntime method [.NET Framework hosting]
ms.assetid: a10749f1-ab91-47cf-982f-d8ccd2e81bd2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 273891b0814d9383d9640c79f5df959f2b9398b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707894"
---
# <a name="iclrmetahostgetruntime-method"></a><span data-ttu-id="6a949-102">ICLRMetaHost::GetRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="6a949-102">ICLRMetaHost::GetRuntime Method</span></span>
<span data-ttu-id="6a949-103">取得[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)對應至特定版本的 common language runtime (CLR) 的介面。</span><span class="sxs-lookup"><span data-stu-id="6a949-103">Gets the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to a particular version of the common language runtime (CLR).</span></span> <span data-ttu-id="6a949-104">這個方法會取代[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)搭配使用函式[STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)旗標。</span><span class="sxs-lookup"><span data-stu-id="6a949-104">This method supersedes the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flag.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a949-105">語法</span><span class="sxs-lookup"><span data-stu-id="6a949-105">Syntax</span></span>  
  
```  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in, REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6a949-106">參數</span><span class="sxs-lookup"><span data-stu-id="6a949-106">Parameters</span></span>  
 `pwzVersion`  
 <span data-ttu-id="6a949-107">[in].NET Framework 編譯版本儲存在中繼資料，格式為"v*A*。*B*[。*X*]"。</span><span class="sxs-lookup"><span data-stu-id="6a949-107">[in] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="6a949-108">*A*， *B*，以及*X*是對應至主要版本、 次要版本和組建編號的十進位數字。</span><span class="sxs-lookup"><span data-stu-id="6a949-108">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6a949-109">C:\Windows\Microsoft.NET\Framework 或 C:\Windows\Microsoft.NET\Framework64 下所顯示的樣子，這個參數必須符合.NET Framework 版本中，目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="6a949-109">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework or C:\Windows\Microsoft.NET\Framework64.</span></span>  
  
 <span data-ttu-id="6a949-110">範例值為"v1.0.3705"、"v1.1.4322"、"v2.0.50727"和"v4.0。*X*"，其中*X*取決於已安裝的組建編號。</span><span class="sxs-lookup"><span data-stu-id="6a949-110">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="6a949-111">需要"v"前置詞。</span><span class="sxs-lookup"><span data-stu-id="6a949-111">The "v" prefix is required.</span></span>  
  
 `riid`  
 <span data-ttu-id="6a949-112">[in]所需的介面識別項。</span><span class="sxs-lookup"><span data-stu-id="6a949-112">[in] The identifier for the desired interface.</span></span> <span data-ttu-id="6a949-113">目前，唯一有效的值，這個參數是 IID_ICLRRuntimeInfo。</span><span class="sxs-lookup"><span data-stu-id="6a949-113">Currently, the only valid value for this parameter is IID_ICLRRuntimeInfo.</span></span>  
  
 `ppRuntime`  
 <span data-ttu-id="6a949-114">[out]指標[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面會對應到要求的執行階段。</span><span class="sxs-lookup"><span data-stu-id="6a949-114">[out] A pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to the requested runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a949-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="6a949-115">Return Value</span></span>  
 <span data-ttu-id="6a949-116">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="6a949-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6a949-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6a949-117">HRESULT</span></span>|<span data-ttu-id="6a949-118">描述</span><span class="sxs-lookup"><span data-stu-id="6a949-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6a949-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="6a949-119">S_OK</span></span>|<span data-ttu-id="6a949-120">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="6a949-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="6a949-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="6a949-121">E_POINTER</span></span>|<span data-ttu-id="6a949-122">`pwzVersion` 或 `ppRuntime` 為 null。</span><span class="sxs-lookup"><span data-stu-id="6a949-122">`pwzVersion` or `ppRuntime` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a949-123">備註</span><span class="sxs-lookup"><span data-stu-id="6a949-123">Remarks</span></span>  
 <span data-ttu-id="6a949-124">這個方法互動以一致的方式與舊版的介面這類[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)介面以及與舊版的功能，例如已被取代`CorBindTo*`函式 (請參閱[取代 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)裝載 API 的.NET Framework 2.0 中)。</span><span class="sxs-lookup"><span data-stu-id="6a949-124">This method interacts consistently with legacy interfaces such as the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface and legacy functions such as the deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span> <span data-ttu-id="6a949-125">也就是執行階段會載入與舊版的 API，都可以看到新的 API，並執行階段會載入新的 api，都可以看到舊版的 API。</span><span class="sxs-lookup"><span data-stu-id="6a949-125">That is, runtimes that are loaded with the legacy API are visible to the new API, and runtimes that are loaded with the new API are visible to the legacy API.</span></span> <span data-ttu-id="6a949-126">。</span><span class="sxs-lookup"><span data-stu-id="6a949-126">.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a949-127">需求</span><span class="sxs-lookup"><span data-stu-id="6a949-127">Requirements</span></span>  
 <span data-ttu-id="6a949-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6a949-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a949-129">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="6a949-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6a949-130">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6a949-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6a949-131">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a949-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a949-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a949-132">See also</span></span>
- [<span data-ttu-id="6a949-133">ICLRMetaHost 介面</span><span class="sxs-lookup"><span data-stu-id="6a949-133">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="6a949-134">已被取代的 CLR 裝載介面和 Coclass</span><span class="sxs-lookup"><span data-stu-id="6a949-134">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)
- [<span data-ttu-id="6a949-135">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="6a949-135">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="6a949-136">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="6a949-136">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="6a949-137">裝載</span><span class="sxs-lookup"><span data-stu-id="6a949-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
