---
title: ICLRGCManager::Collect 方法
ms.date: 03/30/2017
api_name:
- ICLRGCManager.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::Collect
helpviewer_keywords:
- ICLRGCManager::Collect method [.NET Framework hosting]
- Collect method, ICLRGCManager interface [.NET Framework hosting]
ms.assetid: 0c6cbbea-c27c-4695-bda3-17c1910d8ddb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1746527a2667676dfeab89e72874204460bcd33c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984720"
---
# <a name="iclrgcmanagercollect-method"></a><span data-ttu-id="7e90e-102">ICLRGCManager::Collect 方法</span><span class="sxs-lookup"><span data-stu-id="7e90e-102">ICLRGCManager::Collect Method</span></span>
<span data-ttu-id="7e90e-103">強制執行指定層代的回收。</span><span class="sxs-lookup"><span data-stu-id="7e90e-103">Forces a garbage collection for the specified generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e90e-104">語法</span><span class="sxs-lookup"><span data-stu-id="7e90e-104">Syntax</span></span>  
  
```  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e90e-105">參數</span><span class="sxs-lookup"><span data-stu-id="7e90e-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="7e90e-106">[in]要收集的層代。</span><span class="sxs-lookup"><span data-stu-id="7e90e-106">[in] The generation to collect.</span></span> <span data-ttu-id="7e90e-107">-1 值會強制回收所有層代。</span><span class="sxs-lookup"><span data-stu-id="7e90e-107">A value of -1 forces a collection of all generations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e90e-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="7e90e-108">Return Value</span></span>  
  
|<span data-ttu-id="7e90e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7e90e-109">HRESULT</span></span>|<span data-ttu-id="7e90e-110">描述</span><span class="sxs-lookup"><span data-stu-id="7e90e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7e90e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7e90e-111">S_OK</span></span>|<span data-ttu-id="7e90e-112">`Collect` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="7e90e-112">`Collect` returned successfully.</span></span>|  
|<span data-ttu-id="7e90e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7e90e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7e90e-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="7e90e-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7e90e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7e90e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7e90e-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="7e90e-116">The call timed out.</span></span>|  
|<span data-ttu-id="7e90e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7e90e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7e90e-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="7e90e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7e90e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7e90e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7e90e-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="7e90e-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7e90e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7e90e-121">E_FAIL</span></span>|<span data-ttu-id="7e90e-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="7e90e-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7e90e-123">方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="7e90e-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7e90e-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="7e90e-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e90e-125">備註</span><span class="sxs-lookup"><span data-stu-id="7e90e-125">Remarks</span></span>  
 <span data-ttu-id="7e90e-126">`Collect`方法會強制 CLR 的記憶體回收行程執行回收，不論目前的狀態。</span><span class="sxs-lookup"><span data-stu-id="7e90e-126">The `Collect` method forces the CLR's garbage collector to perform a collection regardless of its current state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e90e-127">需求</span><span class="sxs-lookup"><span data-stu-id="7e90e-127">Requirements</span></span>  
 <span data-ttu-id="7e90e-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7e90e-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e90e-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7e90e-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7e90e-130">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7e90e-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7e90e-131">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e90e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e90e-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e90e-132">See also</span></span>

- [<span data-ttu-id="7e90e-133">自動管理記憶體</span><span class="sxs-lookup"><span data-stu-id="7e90e-133">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="7e90e-134">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="7e90e-134">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
- [<span data-ttu-id="7e90e-135">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="7e90e-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="7e90e-136">ICLRGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="7e90e-136">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="7e90e-137">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="7e90e-137">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="7e90e-138">裝載介面</span><span class="sxs-lookup"><span data-stu-id="7e90e-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="7e90e-139">裝載</span><span class="sxs-lookup"><span data-stu-id="7e90e-139">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
