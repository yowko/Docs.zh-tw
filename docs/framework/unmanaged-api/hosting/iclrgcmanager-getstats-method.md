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
ms.openlocfilehash: 1e881b4a55a99bac3f9ca0e8db1556807b888f13
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616958"
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="16cf6-102">ICLRGCManager::GetStats 方法</span><span class="sxs-lookup"><span data-stu-id="16cf6-102">ICLRGCManager::GetStats Method</span></span>
<span data-ttu-id="16cf6-103">取得有關 common language runtime 之垃圾收集系統的一組目前統計資料。</span><span class="sxs-lookup"><span data-stu-id="16cf6-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16cf6-104">語法</span><span class="sxs-lookup"><span data-stu-id="16cf6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16cf6-105">參數</span><span class="sxs-lookup"><span data-stu-id="16cf6-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="16cf6-106">[in、out]包含所要求統計資料的[COR_GC_STATS](cor-gc-stats-structure.md)實例。</span><span class="sxs-lookup"><span data-stu-id="16cf6-106">[in, out] A [COR_GC_STATS](cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="16cf6-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="16cf6-107">Return Value</span></span>  
  
|<span data-ttu-id="16cf6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="16cf6-108">HRESULT</span></span>|<span data-ttu-id="16cf6-109">說明</span><span class="sxs-lookup"><span data-stu-id="16cf6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="16cf6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="16cf6-110">S_OK</span></span>|<span data-ttu-id="16cf6-111">`GetStats`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="16cf6-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="16cf6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="16cf6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="16cf6-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="16cf6-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="16cf6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="16cf6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="16cf6-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="16cf6-115">The call timed out.</span></span>|  
|<span data-ttu-id="16cf6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="16cf6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="16cf6-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="16cf6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="16cf6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="16cf6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="16cf6-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="16cf6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="16cf6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="16cf6-120">E_FAIL</span></span>|<span data-ttu-id="16cf6-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="16cf6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="16cf6-122">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="16cf6-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="16cf6-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="16cf6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16cf6-124">備註</span><span class="sxs-lookup"><span data-stu-id="16cf6-124">Remarks</span></span>  
 <span data-ttu-id="16cf6-125">CLR 會計算並只傳回欄位所指定的統計資料 `Flags` `pStats` 。</span><span class="sxs-lookup"><span data-stu-id="16cf6-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="16cf6-126">將 `Flags` 欄位設定為[COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)列舉的一個或多個值，以指定要設定[COR_GC_STATS](cor-gc-stats-structure.md)結構中的哪些統計資料。</span><span class="sxs-lookup"><span data-stu-id="16cf6-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="16cf6-127">使用方式的範例如下：</span><span class="sxs-lookup"><span data-stu-id="16cf6-127">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="16cf6-128">需求</span><span class="sxs-lookup"><span data-stu-id="16cf6-128">Requirements</span></span>  
 <span data-ttu-id="16cf6-129">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="16cf6-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16cf6-130">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="16cf6-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="16cf6-131">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="16cf6-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="16cf6-132">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16cf6-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16cf6-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16cf6-133">See also</span></span>

- [<span data-ttu-id="16cf6-134">自動記憶體管理</span><span class="sxs-lookup"><span data-stu-id="16cf6-134">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="16cf6-135">COR_GC_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="16cf6-135">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="16cf6-136">COR_GC_STAT_TYPES 列舉</span><span class="sxs-lookup"><span data-stu-id="16cf6-136">COR_GC_STAT_TYPES Enumeration</span></span>](cor-gc-stat-types-enumeration.md)
- [<span data-ttu-id="16cf6-137">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="16cf6-137">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="16cf6-138">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="16cf6-138">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="16cf6-139">ICLRGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="16cf6-139">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="16cf6-140">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="16cf6-140">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="16cf6-141">裝載介面</span><span class="sxs-lookup"><span data-stu-id="16cf6-141">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="16cf6-142">裝載</span><span class="sxs-lookup"><span data-stu-id="16cf6-142">Hosting</span></span>](index.md)
