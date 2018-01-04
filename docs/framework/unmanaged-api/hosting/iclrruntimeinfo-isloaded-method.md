---
title: "ICLRRuntimeInfo::IsLoaded 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.IsLoaded
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::IsLoaded
helpviewer_keywords:
- IsLoaded method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoaded method [.NET Framework hosting]
ms.assetid: fdc5a3a7-71ff-4025-99a1-59e4ee0bfe1b
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f1a83db3a5fc7b5f8b4ad763208fa31ab8f840e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfoisloaded-method"></a><span data-ttu-id="af779-102">ICLRRuntimeInfo::IsLoaded 方法</span><span class="sxs-lookup"><span data-stu-id="af779-102">ICLRRuntimeInfo::IsLoaded Method</span></span>
<span data-ttu-id="af779-103">指出是否與 common language runtime (CLR) 相關聯[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面載入處理序。</span><span class="sxs-lookup"><span data-stu-id="af779-103">Indicates whether the common language runtime (CLR) associated with the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span> <span data-ttu-id="af779-104">可以載入執行階段，但也沒有開始。</span><span class="sxs-lookup"><span data-stu-id="af779-104">A runtime can be loaded without also being started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af779-105">語法</span><span class="sxs-lookup"><span data-stu-id="af779-105">Syntax</span></span>  
  
```  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="af779-106">參數</span><span class="sxs-lookup"><span data-stu-id="af779-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="af779-107">[in]處理序控制代碼。</span><span class="sxs-lookup"><span data-stu-id="af779-107">[in] A handle to the process.</span></span>  
  
 `pbLoaded`  
 <span data-ttu-id="af779-108">[out]`true` CLR 載入處理序; 否則如果`false`。</span><span class="sxs-lookup"><span data-stu-id="af779-108">[out] `true` if the CLR is loaded into the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af779-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="af779-109">Return Value</span></span>  
 <span data-ttu-id="af779-110">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="af779-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="af779-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="af779-111">HRESULT</span></span>|<span data-ttu-id="af779-112">描述</span><span class="sxs-lookup"><span data-stu-id="af779-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="af779-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="af779-113">S_OK</span></span>|<span data-ttu-id="af779-114">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="af779-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="af779-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="af779-115">E_POINTER</span></span>|<span data-ttu-id="af779-116">`pbLoaded` 為 null。</span><span class="sxs-lookup"><span data-stu-id="af779-116">`pbLoaded` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af779-117">備註</span><span class="sxs-lookup"><span data-stu-id="af779-117">Remarks</span></span>  
 <span data-ttu-id="af779-118">這個方法是與舊版相容的下列功能和介面：</span><span class="sxs-lookup"><span data-stu-id="af779-118">This method is backward-compatible with the following functions and interfaces:</span></span>  
  
-   <span data-ttu-id="af779-119">[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)介面 （在.NET Framework 第 1 版裝載 API)。</span><span class="sxs-lookup"><span data-stu-id="af779-119">[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface (in the .NET Framework version 1 hosting API).</span></span>  
  
-   <span data-ttu-id="af779-120">[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)介面 （在.NET Framework 2.0 裝載應用程式開發介面)。</span><span class="sxs-lookup"><span data-stu-id="af779-120">[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface (in the .NET Framework 2.0 hosting API).</span></span>  
  
-   <span data-ttu-id="af779-121">Deprecated`CorBindTo*`函式 (請參閱[已被取代的 CLR 裝載函數](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)裝載 API 的.NET Framework 2.0 中)。</span><span class="sxs-lookup"><span data-stu-id="af779-121">Deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span>  
  
 <span data-ttu-id="af779-122">主機可能呼叫其中一個已被取代`CorBindTo*`函式，例如[CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)函式，來具現化特定的 clr 版本。</span><span class="sxs-lookup"><span data-stu-id="af779-122">A host may call one of the deprecated `CorBindTo*` functions, such as the [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) function, to instantiate a specific version of the CLR.</span></span> <span data-ttu-id="af779-123">然後再呼叫主機[iclrmetahost:: Getruntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)方法並指定相同的版本號碼，才能取得[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="af779-123">The host could then call the [ICLRMetaHost::GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) method and specify the same version number to obtain a [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="af779-124">如果主機然後呼叫`IsLoaded`方法在傳回[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面，`pbLoaded`傳回`true`; 否則它會傳回`false`。</span><span class="sxs-lookup"><span data-stu-id="af779-124">If the host then calls the `IsLoaded` method on the returned [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, `pbLoaded` returns `true`; otherwise, it returns `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af779-125">需求</span><span class="sxs-lookup"><span data-stu-id="af779-125">Requirements</span></span>  
 <span data-ttu-id="af779-126">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="af779-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af779-127">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="af779-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="af779-128">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="af779-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="af779-129">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af779-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af779-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="af779-130">See Also</span></span>  
 [<span data-ttu-id="af779-131">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="af779-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="af779-132">裝載介面</span><span class="sxs-lookup"><span data-stu-id="af779-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="af779-133">裝載</span><span class="sxs-lookup"><span data-stu-id="af779-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
