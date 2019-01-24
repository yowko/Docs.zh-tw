---
title: ICLRGCManager::SetGCStartupLimits 方法
ms.date: 03/30/2017
api_name:
- ICLRGCManager.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: 1c8d9959-95b5-4131-be4a-556d97774014
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf68d2284a6b2603ab97b5be27d6659857fd6c63
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656475"
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a><span data-ttu-id="c73f7-102">ICLRGCManager::SetGCStartupLimits 方法</span><span class="sxs-lookup"><span data-stu-id="c73f7-102">ICLRGCManager::SetGCStartupLimits Method</span></span>
<span data-ttu-id="c73f7-103">設定記憶體回收集合區段的大小和記憶體回收系統的層代 0 的最大大小。</span><span class="sxs-lookup"><span data-stu-id="c73f7-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c73f7-104">開頭[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]，您可以設定區段的大小和最大層代 0 大小值大於`DWORD`利用[ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="c73f7-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c73f7-105">語法</span><span class="sxs-lookup"><span data-stu-id="c73f7-105">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,   
    [in] DWORD MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c73f7-106">參數</span><span class="sxs-lookup"><span data-stu-id="c73f7-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="c73f7-107">[in]記憶體回收區段指定的大小。</span><span class="sxs-lookup"><span data-stu-id="c73f7-107">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="c73f7-108">最小的區段大小是 4 MB。</span><span class="sxs-lookup"><span data-stu-id="c73f7-108">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="c73f7-109">區段可以增加遞增量為 1 MB 或更大。</span><span class="sxs-lookup"><span data-stu-id="c73f7-109">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="c73f7-110">[in]層代 0 指定最大大小。</span><span class="sxs-lookup"><span data-stu-id="c73f7-110">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="c73f7-111">最小層代 0 大小為 64 KB。</span><span class="sxs-lookup"><span data-stu-id="c73f7-111">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c73f7-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="c73f7-112">Return Value</span></span>  
  
|<span data-ttu-id="c73f7-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c73f7-113">HRESULT</span></span>|<span data-ttu-id="c73f7-114">描述</span><span class="sxs-lookup"><span data-stu-id="c73f7-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c73f7-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="c73f7-115">S_OK</span></span>|<span data-ttu-id="c73f7-116">`SetGCStartupLimits` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="c73f7-116">`SetGCStartupLimits` returned successfully.</span></span>|  
|<span data-ttu-id="c73f7-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c73f7-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c73f7-118">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="c73f7-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c73f7-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c73f7-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c73f7-120">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="c73f7-120">The call timed out.</span></span>|  
|<span data-ttu-id="c73f7-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c73f7-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c73f7-122">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="c73f7-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c73f7-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c73f7-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c73f7-124">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="c73f7-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c73f7-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c73f7-125">E_FAIL</span></span>|<span data-ttu-id="c73f7-126">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="c73f7-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c73f7-127">方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="c73f7-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c73f7-128">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="c73f7-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c73f7-129">備註</span><span class="sxs-lookup"><span data-stu-id="c73f7-129">Remarks</span></span>  
 <span data-ttu-id="c73f7-130">值，`SetGCStartupLimits`集合可以指定一次。</span><span class="sxs-lookup"><span data-stu-id="c73f7-130">The values that `SetGCStartupLimits` sets can be specified only once.</span></span> <span data-ttu-id="c73f7-131">稍後呼叫`SetGCStartupLimits`都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="c73f7-131">Later calls to `SetGCStartupLimits` are ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c73f7-132">需求</span><span class="sxs-lookup"><span data-stu-id="c73f7-132">Requirements</span></span>  
 <span data-ttu-id="c73f7-133">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c73f7-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c73f7-134">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c73f7-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c73f7-135">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c73f7-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c73f7-136">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c73f7-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c73f7-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c73f7-137">See also</span></span>
- [<span data-ttu-id="c73f7-138">自動管理記憶體</span><span class="sxs-lookup"><span data-stu-id="c73f7-138">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="c73f7-139">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="c73f7-139">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
- [<span data-ttu-id="c73f7-140">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="c73f7-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="c73f7-141">ICLRGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="c73f7-141">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
