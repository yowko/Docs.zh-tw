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
ms.openlocfilehash: 8622920a81f4b469361ffa879f7a4eeda697cab9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504221"
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="14d30-102">ICLRGCManager::GetStats 方法</span><span class="sxs-lookup"><span data-stu-id="14d30-102">ICLRGCManager::GetStats Method</span></span>
<span data-ttu-id="14d30-103">取得有關 common language runtime 之垃圾收集系統的一組目前統計資料。</span><span class="sxs-lookup"><span data-stu-id="14d30-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14d30-104">語法</span><span class="sxs-lookup"><span data-stu-id="14d30-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14d30-105">參數</span><span class="sxs-lookup"><span data-stu-id="14d30-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="14d30-106">[in、out]包含所要求統計資料的[COR_GC_STATS](cor-gc-stats-structure.md)實例。</span><span class="sxs-lookup"><span data-stu-id="14d30-106">[in, out] A [COR_GC_STATS](cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="14d30-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="14d30-107">Return Value</span></span>  
  
|<span data-ttu-id="14d30-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="14d30-108">HRESULT</span></span>|<span data-ttu-id="14d30-109">說明</span><span class="sxs-lookup"><span data-stu-id="14d30-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="14d30-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="14d30-110">S_OK</span></span>|<span data-ttu-id="14d30-111">`GetStats`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="14d30-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="14d30-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="14d30-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="14d30-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="14d30-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="14d30-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="14d30-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="14d30-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="14d30-115">The call timed out.</span></span>|  
|<span data-ttu-id="14d30-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="14d30-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="14d30-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="14d30-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="14d30-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="14d30-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="14d30-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="14d30-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="14d30-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="14d30-120">E_FAIL</span></span>|<span data-ttu-id="14d30-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="14d30-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="14d30-122">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="14d30-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="14d30-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="14d30-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14d30-124">備註</span><span class="sxs-lookup"><span data-stu-id="14d30-124">Remarks</span></span>  
 <span data-ttu-id="14d30-125">CLR 會計算並只傳回欄位所指定的統計資料 `Flags` `pStats` 。</span><span class="sxs-lookup"><span data-stu-id="14d30-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="14d30-126">將 `Flags` 欄位設定為[COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md)列舉的一個或多個值，以指定要設定[COR_GC_STATS](cor-gc-stats-structure.md)結構中的哪些統計資料。</span><span class="sxs-lookup"><span data-stu-id="14d30-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="14d30-127">使用方式的範例如下：</span><span class="sxs-lookup"><span data-stu-id="14d30-127">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="14d30-128">規格需求</span><span class="sxs-lookup"><span data-stu-id="14d30-128">Requirements</span></span>  
 <span data-ttu-id="14d30-129">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="14d30-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14d30-130">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="14d30-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="14d30-131">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="14d30-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="14d30-132">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14d30-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14d30-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14d30-133">See also</span></span>

- [<span data-ttu-id="14d30-134">自動記憶體管理</span><span class="sxs-lookup"><span data-stu-id="14d30-134">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="14d30-135">COR_GC_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="14d30-135">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="14d30-136">COR_GC_STAT_TYPES 列舉</span><span class="sxs-lookup"><span data-stu-id="14d30-136">COR_GC_STAT_TYPES Enumeration</span></span>](cor-gc-stat-types-enumeration.md)
- [<span data-ttu-id="14d30-137">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="14d30-137">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="14d30-138">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="14d30-138">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="14d30-139">ICLRGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="14d30-139">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="14d30-140">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="14d30-140">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="14d30-141">裝載介面</span><span class="sxs-lookup"><span data-stu-id="14d30-141">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="14d30-142">Hosting</span><span class="sxs-lookup"><span data-stu-id="14d30-142">Hosting</span></span>](index.md)
