---
title: "ICLRMetaHost::GetRuntime 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.GetRuntime
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::GetRuntime
helpviewer_keywords:
- GetRuntime method [.NET Framework hosting]
- ICLRMetaHost::GetRuntime method [.NET Framework hosting]
ms.assetid: a10749f1-ab91-47cf-982f-d8ccd2e81bd2
topic_type: apiref
caps.latest.revision: "31"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6ebfa1af4b824f4fcd4247cd7d0a667488f3e3ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostgetruntime-method"></a><span data-ttu-id="51fb0-102">ICLRMetaHost::GetRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="51fb0-102">ICLRMetaHost::GetRuntime Method</span></span>
<span data-ttu-id="51fb0-103">取得[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)對應至特定版本的 common language runtime (CLR) 的介面。</span><span class="sxs-lookup"><span data-stu-id="51fb0-103">Gets the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to a particular version of the common language runtime (CLR).</span></span> <span data-ttu-id="51fb0-104">這個方法會取代[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)函式搭配[STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)旗標。</span><span class="sxs-lookup"><span data-stu-id="51fb0-104">This method supersedes the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flag.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51fb0-105">語法</span><span class="sxs-lookup"><span data-stu-id="51fb0-105">Syntax</span></span>  
  
```  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in, REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="51fb0-106">參數</span><span class="sxs-lookup"><span data-stu-id="51fb0-106">Parameters</span></span>  
 `pwzVersion`  
 <span data-ttu-id="51fb0-107">[in].NET Framework 編譯版本儲存在中繼資料，以格式"v*A*。*B*[。*X*]"。</span><span class="sxs-lookup"><span data-stu-id="51fb0-107">[in] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="51fb0-108">*A*， *B*，和*X*是對應至主要版本、 次要版本和組建編號的十進位數字。</span><span class="sxs-lookup"><span data-stu-id="51fb0-108">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51fb0-109">C:\Windows\Microsoft.NET\Framework 或 C:\Windows\Microsoft.NET\Framework64 底下所顯示的樣子，這個參數必須符合.NET Framework 版本的目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="51fb0-109">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework or C:\Windows\Microsoft.NET\Framework64.</span></span>  
  
 <span data-ttu-id="51fb0-110">範例值是"v1.0.3705"、"v1.1.4322"、"v2.0.50727，"和"v4.0。*X*"，其中*X*取決於已安裝的組建編號。</span><span class="sxs-lookup"><span data-stu-id="51fb0-110">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="51fb0-111">需要"v"前置詞。</span><span class="sxs-lookup"><span data-stu-id="51fb0-111">The "v" prefix is required.</span></span>  
  
 `riid`  
 <span data-ttu-id="51fb0-112">[in]所需的介面識別項。</span><span class="sxs-lookup"><span data-stu-id="51fb0-112">[in] The identifier for the desired interface.</span></span> <span data-ttu-id="51fb0-113">目前，唯一有效的值，這個參數是 IID_ICLRRuntimeInfo。</span><span class="sxs-lookup"><span data-stu-id="51fb0-113">Currently, the only valid value for this parameter is IID_ICLRRuntimeInfo.</span></span>  
  
 `ppRuntime`  
 <span data-ttu-id="51fb0-114">[out]指標[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)對應到要求的執行階段的介面。</span><span class="sxs-lookup"><span data-stu-id="51fb0-114">[out] A pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to the requested runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51fb0-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="51fb0-115">Return Value</span></span>  
 <span data-ttu-id="51fb0-116">這個方法會傳回下列特定的 HRESULT 以及 HRESULT 錯誤，以指出方法失敗。</span><span class="sxs-lookup"><span data-stu-id="51fb0-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="51fb0-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="51fb0-117">HRESULT</span></span>|<span data-ttu-id="51fb0-118">描述</span><span class="sxs-lookup"><span data-stu-id="51fb0-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="51fb0-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="51fb0-119">S_OK</span></span>|<span data-ttu-id="51fb0-120">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="51fb0-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="51fb0-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="51fb0-121">E_POINTER</span></span>|<span data-ttu-id="51fb0-122">`pwzVersion` 或 `ppRuntime` 為 null。</span><span class="sxs-lookup"><span data-stu-id="51fb0-122">`pwzVersion` or `ppRuntime` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51fb0-123">備註</span><span class="sxs-lookup"><span data-stu-id="51fb0-123">Remarks</span></span>  
 <span data-ttu-id="51fb0-124">這個方法以一致的方式會與互動傳統介面例如[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)介面和舊版的功能，例如已被取代`CorBindTo*`函式 (請參閱[取代 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)裝載 API 的.NET Framework 2.0 中)。</span><span class="sxs-lookup"><span data-stu-id="51fb0-124">This method interacts consistently with legacy interfaces such as the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface and legacy functions such as the deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span> <span data-ttu-id="51fb0-125">也就是執行階段會載入與舊版的 API，會顯示新的 api，而且載入新的 api 執行階段會顯示舊版的應用程式開發介面。</span><span class="sxs-lookup"><span data-stu-id="51fb0-125">That is, runtimes that are loaded with the legacy API are visible to the new API, and runtimes that are loaded with the new API are visible to the legacy API.</span></span> <span data-ttu-id="51fb0-126">。</span><span class="sxs-lookup"><span data-stu-id="51fb0-126">.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51fb0-127">需求</span><span class="sxs-lookup"><span data-stu-id="51fb0-127">Requirements</span></span>  
 <span data-ttu-id="51fb0-128">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="51fb0-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51fb0-129">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="51fb0-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="51fb0-130">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="51fb0-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="51fb0-131">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51fb0-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51fb0-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51fb0-132">See Also</span></span>  
 [<span data-ttu-id="51fb0-133">ICLRMetaHost 介面</span><span class="sxs-lookup"><span data-stu-id="51fb0-133">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="51fb0-134">已被取代的 CLR 裝載介面和 Coclass</span><span class="sxs-lookup"><span data-stu-id="51fb0-134">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 [<span data-ttu-id="51fb0-135">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="51fb0-135">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="51fb0-136">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="51fb0-136">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
 [<span data-ttu-id="51fb0-137">裝載</span><span class="sxs-lookup"><span data-stu-id="51fb0-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
