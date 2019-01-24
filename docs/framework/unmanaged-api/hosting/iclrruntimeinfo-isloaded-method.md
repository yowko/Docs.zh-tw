---
title: ICLRRuntimeInfo::IsLoaded 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoaded
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoaded
helpviewer_keywords:
- IsLoaded method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoaded method [.NET Framework hosting]
ms.assetid: fdc5a3a7-71ff-4025-99a1-59e4ee0bfe1b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69a3b0921528ed09ee4ab3a1ede6b9efe565e02a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619214"
---
# <a name="iclrruntimeinfoisloaded-method"></a><span data-ttu-id="dcb10-102">ICLRRuntimeInfo::IsLoaded 方法</span><span class="sxs-lookup"><span data-stu-id="dcb10-102">ICLRRuntimeInfo::IsLoaded Method</span></span>
<span data-ttu-id="dcb10-103">表示 common language runtime (CLR) 要與相關聯[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面會載入處理序。</span><span class="sxs-lookup"><span data-stu-id="dcb10-103">Indicates whether the common language runtime (CLR) associated with the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span> <span data-ttu-id="dcb10-104">但還沒有開始，就可以載入執行階段。</span><span class="sxs-lookup"><span data-stu-id="dcb10-104">A runtime can be loaded without also being started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcb10-105">語法</span><span class="sxs-lookup"><span data-stu-id="dcb10-105">Syntax</span></span>  
  
```  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dcb10-106">參數</span><span class="sxs-lookup"><span data-stu-id="dcb10-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="dcb10-107">[in]處理序控制代碼。</span><span class="sxs-lookup"><span data-stu-id="dcb10-107">[in] A handle to the process.</span></span>  
  
 `pbLoaded`  
 <span data-ttu-id="dcb10-108">[out]`true` CLR 載入處理序，否則如果`false`。</span><span class="sxs-lookup"><span data-stu-id="dcb10-108">[out] `true` if the CLR is loaded into the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dcb10-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="dcb10-109">Return Value</span></span>  
 <span data-ttu-id="dcb10-110">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="dcb10-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="dcb10-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dcb10-111">HRESULT</span></span>|<span data-ttu-id="dcb10-112">描述</span><span class="sxs-lookup"><span data-stu-id="dcb10-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dcb10-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="dcb10-113">S_OK</span></span>|<span data-ttu-id="dcb10-114">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="dcb10-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="dcb10-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="dcb10-115">E_POINTER</span></span>|<span data-ttu-id="dcb10-116">`pbLoaded` 為 null。</span><span class="sxs-lookup"><span data-stu-id="dcb10-116">`pbLoaded` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dcb10-117">備註</span><span class="sxs-lookup"><span data-stu-id="dcb10-117">Remarks</span></span>  
 <span data-ttu-id="dcb10-118">這個方法是具有回溯相容性與下列函式和介面：</span><span class="sxs-lookup"><span data-stu-id="dcb10-118">This method is backward-compatible with the following functions and interfaces:</span></span>  
  
-   <span data-ttu-id="dcb10-119">[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)介面 （在.NET Framework 第 1 版裝載 API)。</span><span class="sxs-lookup"><span data-stu-id="dcb10-119">[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface (in the .NET Framework version 1 hosting API).</span></span>  
  
-   <span data-ttu-id="dcb10-120">[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) （在.NET Framework 2.0 中裝載 API) 的介面。</span><span class="sxs-lookup"><span data-stu-id="dcb10-120">[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface (in the .NET Framework 2.0 hosting API).</span></span>  
  
-   <span data-ttu-id="dcb10-121">已被取代`CorBindTo*`函式 (請參閱 <<c2> [ 已被取代 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)裝載 API 的.NET Framework 2.0 中)。</span><span class="sxs-lookup"><span data-stu-id="dcb10-121">Deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span>  
  
 <span data-ttu-id="dcb10-122">主機可能呼叫其中一個已被取代`CorBindTo*`函式，例如[CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)函式，來具現化特定的 clr 版本。</span><span class="sxs-lookup"><span data-stu-id="dcb10-122">A host may call one of the deprecated `CorBindTo*` functions, such as the [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) function, to instantiate a specific version of the CLR.</span></span> <span data-ttu-id="dcb10-123">主應用程式然後再呼叫[iclrmetahost:: Getruntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)方法並指定相同的版本號碼，才能取得[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="dcb10-123">The host could then call the [ICLRMetaHost::GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) method and specify the same version number to obtain a [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="dcb10-124">如果主應用程式接著會呼叫`IsLoaded`方法傳回[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面`pbLoaded`傳回`true`; 否則它會傳回`false`。</span><span class="sxs-lookup"><span data-stu-id="dcb10-124">If the host then calls the `IsLoaded` method on the returned [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, `pbLoaded` returns `true`; otherwise, it returns `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcb10-125">需求</span><span class="sxs-lookup"><span data-stu-id="dcb10-125">Requirements</span></span>  
 <span data-ttu-id="dcb10-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dcb10-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcb10-127">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="dcb10-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="dcb10-128">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="dcb10-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dcb10-129">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcb10-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcb10-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dcb10-130">See also</span></span>
- [<span data-ttu-id="dcb10-131">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="dcb10-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="dcb10-132">裝載介面</span><span class="sxs-lookup"><span data-stu-id="dcb10-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="dcb10-133">裝載</span><span class="sxs-lookup"><span data-stu-id="dcb10-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
