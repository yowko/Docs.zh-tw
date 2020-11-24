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
ms.openlocfilehash: 70fe8b132f03925c41b6bc7aae8e60fea1b05202
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678268"
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="0309e-102">ICLRGCManager::GetStats 方法</span><span class="sxs-lookup"><span data-stu-id="0309e-102">ICLRGCManager::GetStats Method</span></span>

<span data-ttu-id="0309e-103">取得有關 common language runtime 的垃圾收集系統的一組目前統計資料。</span><span class="sxs-lookup"><span data-stu-id="0309e-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0309e-104">語法</span><span class="sxs-lookup"><span data-stu-id="0309e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0309e-105">參數</span><span class="sxs-lookup"><span data-stu-id="0309e-105">Parameters</span></span>  

 `pStats`  
 <span data-ttu-id="0309e-106">[in，out]包含所要求統計資料的 [COR_GC_STATS](cor-gc-stats-structure.md) 實例。</span><span class="sxs-lookup"><span data-stu-id="0309e-106">[in, out] A [COR_GC_STATS](cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0309e-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="0309e-107">Return Value</span></span>  
  
|<span data-ttu-id="0309e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0309e-108">HRESULT</span></span>|<span data-ttu-id="0309e-109">描述</span><span class="sxs-lookup"><span data-stu-id="0309e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0309e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0309e-110">S_OK</span></span>|<span data-ttu-id="0309e-111">`GetStats` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="0309e-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="0309e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0309e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0309e-113">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="0309e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0309e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0309e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0309e-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="0309e-115">The call timed out.</span></span>|  
|<span data-ttu-id="0309e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0309e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0309e-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="0309e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0309e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0309e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0309e-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="0309e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0309e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0309e-120">E_FAIL</span></span>|<span data-ttu-id="0309e-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="0309e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0309e-122">在方法傳回 E_FAIL 之後，就無法在進程中使用 CLR。</span><span class="sxs-lookup"><span data-stu-id="0309e-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0309e-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="0309e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0309e-124">備註</span><span class="sxs-lookup"><span data-stu-id="0309e-124">Remarks</span></span>  

 <span data-ttu-id="0309e-125">CLR 只會計算並傳回由的欄位所指定的統計資料 `Flags` `pStats` 。</span><span class="sxs-lookup"><span data-stu-id="0309e-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="0309e-126">將 `Flags` 欄位設定為 [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) 列舉的一或多個值，以指定要設定 [COR_GC_STATS](cor-gc-stats-structure.md) 結構中的統計資料。</span><span class="sxs-lookup"><span data-stu-id="0309e-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="0309e-127">使用方式的範例如下：</span><span class="sxs-lookup"><span data-stu-id="0309e-127">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="0309e-128">需求</span><span class="sxs-lookup"><span data-stu-id="0309e-128">Requirements</span></span>  

 <span data-ttu-id="0309e-129">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0309e-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0309e-130">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="0309e-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0309e-131">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="0309e-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0309e-132">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0309e-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0309e-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0309e-133">See also</span></span>

- [<span data-ttu-id="0309e-134">自動記憶體管理</span><span class="sxs-lookup"><span data-stu-id="0309e-134">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="0309e-135">COR_GC_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="0309e-135">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="0309e-136">COR_GC_STAT_TYPES 列舉</span><span class="sxs-lookup"><span data-stu-id="0309e-136">COR_GC_STAT_TYPES Enumeration</span></span>](cor-gc-stat-types-enumeration.md)
- [<span data-ttu-id="0309e-137">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="0309e-137">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="0309e-138">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="0309e-138">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="0309e-139">ICLRGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="0309e-139">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="0309e-140">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="0309e-140">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="0309e-141">裝載介面</span><span class="sxs-lookup"><span data-stu-id="0309e-141">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="0309e-142">裝載</span><span class="sxs-lookup"><span data-stu-id="0309e-142">Hosting</span></span>](index.md)
