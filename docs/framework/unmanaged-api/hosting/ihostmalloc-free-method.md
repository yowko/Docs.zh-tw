---
title: IHostMAlloc::Free 方法
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Free
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Free
helpviewer_keywords:
- IHostMAlloc::Free method [.NET Framework hosting]
- Free method, IHostMAlloc interface [.NET Framework hosting]
ms.assetid: c89abf5b-1120-4437-8b57-4a99fb3ae7f9
topic_type:
- apiref
ms.openlocfilehash: f7ae4e4cbb757edea242c57720baeb70ced5c428
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192060"
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="3e3d0-102">IHostMAlloc::Free 方法</span><span class="sxs-lookup"><span data-stu-id="3e3d0-102">IHostMAlloc::Free Method</span></span>
<span data-ttu-id="3e3d0-103">釋放使用配置函[式所配置](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)的記憶體。</span><span class="sxs-lookup"><span data-stu-id="3e3d0-103">Frees memory that was allocated by using the [Alloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e3d0-104">語法</span><span class="sxs-lookup"><span data-stu-id="3e3d0-104">Syntax</span></span>  
  
```cpp  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e3d0-105">參數</span><span class="sxs-lookup"><span data-stu-id="3e3d0-105">Parameters</span></span>  
 `pMem`  
 <span data-ttu-id="3e3d0-106">在要釋放之記憶體的指標。</span><span class="sxs-lookup"><span data-stu-id="3e3d0-106">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e3d0-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="3e3d0-107">Return Value</span></span>  
  
|<span data-ttu-id="3e3d0-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3e3d0-108">HRESULT</span></span>|<span data-ttu-id="3e3d0-109">描述</span><span class="sxs-lookup"><span data-stu-id="3e3d0-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3e3d0-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3e3d0-110">S_OK</span></span>|<span data-ttu-id="3e3d0-111">已成功傳回 `Free`。</span><span class="sxs-lookup"><span data-stu-id="3e3d0-111">`Free` returned successfully.</span></span>|  
|<span data-ttu-id="3e3d0-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3e3d0-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3e3d0-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="3e3d0-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3e3d0-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3e3d0-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3e3d0-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="3e3d0-115">The call timed out.</span></span>|  
|<span data-ttu-id="3e3d0-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3e3d0-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3e3d0-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="3e3d0-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3e3d0-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3e3d0-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3e3d0-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="3e3d0-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3e3d0-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3e3d0-120">E_FAIL</span></span>|<span data-ttu-id="3e3d0-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="3e3d0-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3e3d0-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="3e3d0-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3e3d0-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="3e3d0-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3e3d0-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="3e3d0-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="3e3d0-125">嘗試釋放未透過主機所配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="3e3d0-125">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e3d0-126">備註</span><span class="sxs-lookup"><span data-stu-id="3e3d0-126">Remarks</span></span>  
 <span data-ttu-id="3e3d0-127">如果 `pMem` 參數指的是未使用呼叫 `Alloc`所配置的記憶體區域，則主機應該會傳回 HOST_E_INVALIDOPERATION。</span><span class="sxs-lookup"><span data-stu-id="3e3d0-127">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e3d0-128">需求</span><span class="sxs-lookup"><span data-stu-id="3e3d0-128">Requirements</span></span>  
 <span data-ttu-id="3e3d0-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3e3d0-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e3d0-130">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="3e3d0-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3e3d0-131">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3e3d0-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e3d0-132">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e3d0-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e3d0-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="3e3d0-133">See also</span></span>

- [<span data-ttu-id="3e3d0-134">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="3e3d0-134">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="3e3d0-135">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="3e3d0-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
