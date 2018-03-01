---
title: "IHostMAlloc::Free 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4775b6ae00f34d7d046515f8700a35470b2f6650
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="43599-102">IHostMAlloc::Free 方法</span><span class="sxs-lookup"><span data-stu-id="43599-102">IHostMAlloc::Free Method</span></span>
<span data-ttu-id="43599-103">釋放記憶體取消配置使用[配置](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)函式。</span><span class="sxs-lookup"><span data-stu-id="43599-103">Frees memory that was allocated by using the [Alloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43599-104">語法</span><span class="sxs-lookup"><span data-stu-id="43599-104">Syntax</span></span>  
  
```  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="43599-105">參數</span><span class="sxs-lookup"><span data-stu-id="43599-105">Parameters</span></span>  
 `pMem`  
 <span data-ttu-id="43599-106">[in]要釋放的記憶體指標。</span><span class="sxs-lookup"><span data-stu-id="43599-106">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43599-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="43599-107">Return Value</span></span>  
  
|<span data-ttu-id="43599-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="43599-108">HRESULT</span></span>|<span data-ttu-id="43599-109">描述</span><span class="sxs-lookup"><span data-stu-id="43599-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="43599-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="43599-110">S_OK</span></span>|<span data-ttu-id="43599-111">`Free`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="43599-111">`Free` returned successfully.</span></span>|  
|<span data-ttu-id="43599-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="43599-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="43599-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="43599-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="43599-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="43599-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="43599-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="43599-115">The call timed out.</span></span>|  
|<span data-ttu-id="43599-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="43599-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="43599-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="43599-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="43599-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="43599-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="43599-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="43599-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="43599-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="43599-120">E_FAIL</span></span>|<span data-ttu-id="43599-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="43599-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="43599-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="43599-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="43599-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="43599-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="43599-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="43599-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="43599-125">您嘗試釋放未配置到主機的記憶體。</span><span class="sxs-lookup"><span data-stu-id="43599-125">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43599-126">備註</span><span class="sxs-lookup"><span data-stu-id="43599-126">Remarks</span></span>  
 <span data-ttu-id="43599-127">如果`pMem`參數是指使用的呼叫未配置的記憶體區域`Alloc`，主應用程式應該傳回 HOST_E_INVALIDOPERATION。</span><span class="sxs-lookup"><span data-stu-id="43599-127">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43599-128">需求</span><span class="sxs-lookup"><span data-stu-id="43599-128">Requirements</span></span>  
 <span data-ttu-id="43599-129">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="43599-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43599-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="43599-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="43599-131">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="43599-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="43599-132">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43599-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43599-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="43599-133">See Also</span></span>  
 [<span data-ttu-id="43599-134">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="43599-134">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="43599-135">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="43599-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
