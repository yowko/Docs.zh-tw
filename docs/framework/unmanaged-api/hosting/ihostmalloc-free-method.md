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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9cf60d4e711d0c88b5fb8b4c213b19bdea564324
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57477825"
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="18eb5-102">IHostMAlloc::Free 方法</span><span class="sxs-lookup"><span data-stu-id="18eb5-102">IHostMAlloc::Free Method</span></span>
<span data-ttu-id="18eb5-103">釋放已使用所配置的記憶體[Alloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)函式。</span><span class="sxs-lookup"><span data-stu-id="18eb5-103">Frees memory that was allocated by using the [Alloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18eb5-104">語法</span><span class="sxs-lookup"><span data-stu-id="18eb5-104">Syntax</span></span>  
  
```  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18eb5-105">參數</span><span class="sxs-lookup"><span data-stu-id="18eb5-105">Parameters</span></span>  
 `pMem`  
 <span data-ttu-id="18eb5-106">[in]要釋放的記憶體指標。</span><span class="sxs-lookup"><span data-stu-id="18eb5-106">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="18eb5-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="18eb5-107">Return Value</span></span>  
  
|<span data-ttu-id="18eb5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="18eb5-108">HRESULT</span></span>|<span data-ttu-id="18eb5-109">描述</span><span class="sxs-lookup"><span data-stu-id="18eb5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="18eb5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="18eb5-110">S_OK</span></span>|<span data-ttu-id="18eb5-111">`Free` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="18eb5-111">`Free` returned successfully.</span></span>|  
|<span data-ttu-id="18eb5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="18eb5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="18eb5-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="18eb5-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="18eb5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="18eb5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="18eb5-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="18eb5-115">The call timed out.</span></span>|  
|<span data-ttu-id="18eb5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="18eb5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="18eb5-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="18eb5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="18eb5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="18eb5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="18eb5-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="18eb5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="18eb5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="18eb5-120">E_FAIL</span></span>|<span data-ttu-id="18eb5-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="18eb5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="18eb5-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="18eb5-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="18eb5-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="18eb5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="18eb5-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="18eb5-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="18eb5-125">您嘗試釋出透過主機未配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="18eb5-125">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18eb5-126">備註</span><span class="sxs-lookup"><span data-stu-id="18eb5-126">Remarks</span></span>  
 <span data-ttu-id="18eb5-127">如果`pMem`參數會參考所使用的呼叫未配置的記憶體區域`Alloc`，主應用程式應該會傳回 HOST_E_INVALIDOPERATION。</span><span class="sxs-lookup"><span data-stu-id="18eb5-127">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18eb5-128">需求</span><span class="sxs-lookup"><span data-stu-id="18eb5-128">Requirements</span></span>  
 <span data-ttu-id="18eb5-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="18eb5-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18eb5-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="18eb5-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="18eb5-131">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="18eb5-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="18eb5-132">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18eb5-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18eb5-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18eb5-133">See also</span></span>
- [<span data-ttu-id="18eb5-134">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="18eb5-134">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="18eb5-135">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="18eb5-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
