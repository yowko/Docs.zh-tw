---
title: ICLRGCManager::GetStats 方法
ms.date: 03/30/2017
api_name:
- ICLRGCManager.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::GetStats
helpviewer_keywords:
- GetStats method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::GetStats method [.NET Framework hosting]
ms.assetid: ce259d1d-cd81-4490-a7a1-0d0ea0804872
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e92707e7b24709d64915e29823196bb0f827175
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485228"
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="2ca04-102">ICLRGCManager::GetStats 方法</span><span class="sxs-lookup"><span data-stu-id="2ca04-102">ICLRGCManager::GetStats Method</span></span>
<span data-ttu-id="2ca04-103">取得一組有關 common language runtime 的記憶體回收系統目前的統計資料。</span><span class="sxs-lookup"><span data-stu-id="2ca04-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ca04-104">語法</span><span class="sxs-lookup"><span data-stu-id="2ca04-104">Syntax</span></span>  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ca04-105">參數</span><span class="sxs-lookup"><span data-stu-id="2ca04-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="2ca04-106">[in、 out]A [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)包含要求的統計資料的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2ca04-106">[in, out] A [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ca04-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="2ca04-107">Return Value</span></span>  
  
|<span data-ttu-id="2ca04-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2ca04-108">HRESULT</span></span>|<span data-ttu-id="2ca04-109">描述</span><span class="sxs-lookup"><span data-stu-id="2ca04-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2ca04-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2ca04-110">S_OK</span></span>|<span data-ttu-id="2ca04-111">`GetStats` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="2ca04-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="2ca04-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2ca04-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2ca04-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="2ca04-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2ca04-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2ca04-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2ca04-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="2ca04-115">The call timed out.</span></span>|  
|<span data-ttu-id="2ca04-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2ca04-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2ca04-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="2ca04-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2ca04-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2ca04-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2ca04-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="2ca04-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2ca04-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2ca04-120">E_FAIL</span></span>|<span data-ttu-id="2ca04-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="2ca04-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2ca04-122">方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="2ca04-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2ca04-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="2ca04-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ca04-124">備註</span><span class="sxs-lookup"><span data-stu-id="2ca04-124">Remarks</span></span>  
 <span data-ttu-id="2ca04-125">CLR 會計算並傳回所指定這些統計資料`Flags`欄位`pStats`。</span><span class="sxs-lookup"><span data-stu-id="2ca04-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="2ca04-126">設定`Flags`欄位設為一或多個值[COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)列舉，來指定哪些統計資料，在[COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)結構所設定。</span><span class="sxs-lookup"><span data-stu-id="2ca04-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="2ca04-127">使用方式的範例如下所示：</span><span class="sxs-lookup"><span data-stu-id="2ca04-127">An example of the usage is as follows:</span></span>  
  
```  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="2ca04-128">需求</span><span class="sxs-lookup"><span data-stu-id="2ca04-128">Requirements</span></span>  
 <span data-ttu-id="2ca04-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2ca04-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ca04-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2ca04-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2ca04-131">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2ca04-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2ca04-132">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ca04-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ca04-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ca04-133">See also</span></span>
- [<span data-ttu-id="2ca04-134">自動管理記憶體</span><span class="sxs-lookup"><span data-stu-id="2ca04-134">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="2ca04-135">COR_GC_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="2ca04-135">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="2ca04-136">COR_GC_STAT_TYPES 列舉</span><span class="sxs-lookup"><span data-stu-id="2ca04-136">COR_GC_STAT_TYPES Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)
- [<span data-ttu-id="2ca04-137">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="2ca04-137">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
- [<span data-ttu-id="2ca04-138">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="2ca04-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="2ca04-139">ICLRGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="2ca04-139">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="2ca04-140">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="2ca04-140">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="2ca04-141">裝載介面</span><span class="sxs-lookup"><span data-stu-id="2ca04-141">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="2ca04-142">裝載</span><span class="sxs-lookup"><span data-stu-id="2ca04-142">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
