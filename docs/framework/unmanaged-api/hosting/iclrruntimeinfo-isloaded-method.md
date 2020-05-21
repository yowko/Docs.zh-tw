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
ms.openlocfilehash: 3275a69683a312340f35841815685066def10b23
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762522"
---
# <a name="iclrruntimeinfoisloaded-method"></a><span data-ttu-id="6a0d8-102">ICLRRuntimeInfo::IsLoaded 方法</span><span class="sxs-lookup"><span data-stu-id="6a0d8-102">ICLRRuntimeInfo::IsLoaded Method</span></span>
<span data-ttu-id="6a0d8-103">指出與[ICLRRuntimeInfo](iclrruntimeinfo-interface.md)介面相關聯的 common language RUNTIME （CLR）是否已載入進程中。</span><span class="sxs-lookup"><span data-stu-id="6a0d8-103">Indicates whether the common language runtime (CLR) associated with the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span> <span data-ttu-id="6a0d8-104">您也可以載入執行時間，而不需要啟動。</span><span class="sxs-lookup"><span data-stu-id="6a0d8-104">A runtime can be loaded without also being started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a0d8-105">語法</span><span class="sxs-lookup"><span data-stu-id="6a0d8-105">Syntax</span></span>  
  
```cpp  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a0d8-106">參數</span><span class="sxs-lookup"><span data-stu-id="6a0d8-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="6a0d8-107">在進程的控制碼。</span><span class="sxs-lookup"><span data-stu-id="6a0d8-107">[in] A handle to the process.</span></span>  
  
 `pbLoaded`  
 <span data-ttu-id="6a0d8-108">[out] `true`如果 CLR 已載入進程中，則為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="6a0d8-108">[out] `true` if the CLR is loaded into the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a0d8-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="6a0d8-109">Return Value</span></span>  
 <span data-ttu-id="6a0d8-110">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="6a0d8-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6a0d8-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6a0d8-111">HRESULT</span></span>|<span data-ttu-id="6a0d8-112">Description</span><span class="sxs-lookup"><span data-stu-id="6a0d8-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6a0d8-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="6a0d8-113">S_OK</span></span>|<span data-ttu-id="6a0d8-114">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="6a0d8-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="6a0d8-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="6a0d8-115">E_POINTER</span></span>|<span data-ttu-id="6a0d8-116">`pbLoaded` 為 null。</span><span class="sxs-lookup"><span data-stu-id="6a0d8-116">`pbLoaded` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a0d8-117">備註</span><span class="sxs-lookup"><span data-stu-id="6a0d8-117">Remarks</span></span>  
 <span data-ttu-id="6a0d8-118">這個方法與下列函數和介面具有回溯相容性：</span><span class="sxs-lookup"><span data-stu-id="6a0d8-118">This method is backward-compatible with the following functions and interfaces:</span></span>  
  
- <span data-ttu-id="6a0d8-119">[ICorRuntimeHost](icorruntimehost-interface.md)介面（在 .NET Framework 版本1裝載 API 中）。</span><span class="sxs-lookup"><span data-stu-id="6a0d8-119">[ICorRuntimeHost](icorruntimehost-interface.md) interface (in the .NET Framework version 1 hosting API).</span></span>  
  
- <span data-ttu-id="6a0d8-120">[ICLRRuntimeHost](iclrruntimehost-interface.md)介面（在 .NET Framework 2.0 裝載 API 中）。</span><span class="sxs-lookup"><span data-stu-id="6a0d8-120">[ICLRRuntimeHost](iclrruntimehost-interface.md) interface (in the .NET Framework 2.0 hosting API).</span></span>  
  
- <span data-ttu-id="6a0d8-121">已淘汰的函式 `CorBindTo*` （請參閱 .NET Framework 2.0 裝載 API 中已[淘汰的 CLR 裝載](deprecated-clr-hosting-functions.md)函式）。</span><span class="sxs-lookup"><span data-stu-id="6a0d8-121">Deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span>  
  
 <span data-ttu-id="6a0d8-122">主機可以呼叫其中一個已被取代的函式（ `CorBindTo*` 例如[CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)函數），以具現化 CLR 的特定版本。</span><span class="sxs-lookup"><span data-stu-id="6a0d8-122">A host may call one of the deprecated `CorBindTo*` functions, such as the [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) function, to instantiate a specific version of the CLR.</span></span> <span data-ttu-id="6a0d8-123">然後主機可以呼叫[ICLRMetaHost：： GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)方法，並指定相同的版本號碼來取得[ICLRRuntimeInfo](iclrruntimeinfo-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="6a0d8-123">The host could then call the [ICLRMetaHost::GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) method and specify the same version number to obtain a [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="6a0d8-124">如果主機接著在 `IsLoaded` 傳回的[ICLRRuntimeInfo](iclrruntimeinfo-interface.md)介面上呼叫方法，則 `pbLoaded` `true` 會傳回; 否則，它會傳回 `false` 。</span><span class="sxs-lookup"><span data-stu-id="6a0d8-124">If the host then calls the `IsLoaded` method on the returned [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface, `pbLoaded` returns `true`; otherwise, it returns `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a0d8-125">規格需求</span><span class="sxs-lookup"><span data-stu-id="6a0d8-125">Requirements</span></span>  
 <span data-ttu-id="6a0d8-126">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6a0d8-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a0d8-127">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="6a0d8-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6a0d8-128">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6a0d8-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6a0d8-129">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a0d8-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a0d8-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a0d8-130">See also</span></span>

- [<span data-ttu-id="6a0d8-131">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="6a0d8-131">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="6a0d8-132">裝載介面</span><span class="sxs-lookup"><span data-stu-id="6a0d8-132">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="6a0d8-133">裝載</span><span class="sxs-lookup"><span data-stu-id="6a0d8-133">Hosting</span></span>](index.md)
