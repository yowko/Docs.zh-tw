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
ms.openlocfilehash: a8bd7b16f06433970d1222dbeaa843e187715faa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438993"
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="3c0d8-102">IHostMAlloc::Free 方法</span><span class="sxs-lookup"><span data-stu-id="3c0d8-102">IHostMAlloc::Free Method</span></span>
<span data-ttu-id="3c0d8-103">釋放記憶體取消配置使用[配置](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)函式。</span><span class="sxs-lookup"><span data-stu-id="3c0d8-103">Frees memory that was allocated by using the [Alloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c0d8-104">語法</span><span class="sxs-lookup"><span data-stu-id="3c0d8-104">Syntax</span></span>  
  
```  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3c0d8-105">參數</span><span class="sxs-lookup"><span data-stu-id="3c0d8-105">Parameters</span></span>  
 `pMem`  
 <span data-ttu-id="3c0d8-106">[in]要釋放的記憶體指標。</span><span class="sxs-lookup"><span data-stu-id="3c0d8-106">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c0d8-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="3c0d8-107">Return Value</span></span>  
  
|<span data-ttu-id="3c0d8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3c0d8-108">HRESULT</span></span>|<span data-ttu-id="3c0d8-109">描述</span><span class="sxs-lookup"><span data-stu-id="3c0d8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3c0d8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3c0d8-110">S_OK</span></span>|<span data-ttu-id="3c0d8-111">`Free` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="3c0d8-111">`Free` returned successfully.</span></span>|  
|<span data-ttu-id="3c0d8-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3c0d8-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3c0d8-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="3c0d8-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3c0d8-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3c0d8-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3c0d8-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="3c0d8-115">The call timed out.</span></span>|  
|<span data-ttu-id="3c0d8-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3c0d8-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3c0d8-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="3c0d8-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3c0d8-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3c0d8-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3c0d8-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="3c0d8-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3c0d8-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3c0d8-120">E_FAIL</span></span>|<span data-ttu-id="3c0d8-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="3c0d8-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3c0d8-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="3c0d8-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3c0d8-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="3c0d8-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3c0d8-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="3c0d8-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="3c0d8-125">您嘗試釋放未配置到主機的記憶體。</span><span class="sxs-lookup"><span data-stu-id="3c0d8-125">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c0d8-126">備註</span><span class="sxs-lookup"><span data-stu-id="3c0d8-126">Remarks</span></span>  
 <span data-ttu-id="3c0d8-127">如果`pMem`參數是指使用的呼叫未配置的記憶體區域`Alloc`，主應用程式應該傳回 HOST_E_INVALIDOPERATION。</span><span class="sxs-lookup"><span data-stu-id="3c0d8-127">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c0d8-128">需求</span><span class="sxs-lookup"><span data-stu-id="3c0d8-128">Requirements</span></span>  
 <span data-ttu-id="3c0d8-129">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3c0d8-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c0d8-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3c0d8-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3c0d8-131">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3c0d8-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3c0d8-132">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c0d8-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c0d8-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c0d8-133">See Also</span></span>  
 [<span data-ttu-id="3c0d8-134">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="3c0d8-134">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="3c0d8-135">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="3c0d8-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
