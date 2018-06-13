---
title: ICLRGCManager2::SetGCStartupLimitsEx 方法
ms.date: 03/30/2017
api_name:
- ICLRGCManager2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2::SetCLRGCStartupLimitsEx
helpviewer_keywords:
- ICLRGCManager2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 6c3a08a9-5d65-48d4-8bbf-2a86ed7d356a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65fbf0bf42f7312ad80b61bf452b62a4d0ff93c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436120"
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="643dd-102">ICLRGCManager2::SetGCStartupLimitsEx 方法</span><span class="sxs-lookup"><span data-stu-id="643dd-102">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="643dd-103">設定記憶體回收集合區段的大小和記憶體回收系統的層代 0 的最大大小。</span><span class="sxs-lookup"><span data-stu-id="643dd-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="643dd-104">語法</span><span class="sxs-lookup"><span data-stu-id="643dd-104">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,   
    [in] SIZE_T MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="643dd-105">參數</span><span class="sxs-lookup"><span data-stu-id="643dd-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="643dd-106">[in]記憶體回收集合區段指定的大小。</span><span class="sxs-lookup"><span data-stu-id="643dd-106">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="643dd-107">最小的區段大小是 4 MB。</span><span class="sxs-lookup"><span data-stu-id="643dd-107">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="643dd-108">區段可以增加增量為 1 MB 或更大。</span><span class="sxs-lookup"><span data-stu-id="643dd-108">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="643dd-109">[in]指定的大小上限的層代 0。</span><span class="sxs-lookup"><span data-stu-id="643dd-109">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="643dd-110">最小層代 0 大小是 64 KB。</span><span class="sxs-lookup"><span data-stu-id="643dd-110">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="643dd-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="643dd-111">Return Value</span></span>  
  
|<span data-ttu-id="643dd-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="643dd-112">HRESULT</span></span>|<span data-ttu-id="643dd-113">描述</span><span class="sxs-lookup"><span data-stu-id="643dd-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="643dd-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="643dd-114">S_OK</span></span>|<span data-ttu-id="643dd-115">`SetGCStartupLimitsEx` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="643dd-115">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="643dd-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="643dd-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="643dd-117">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="643dd-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="643dd-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="643dd-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="643dd-119">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="643dd-119">The call timed out.</span></span>|  
|<span data-ttu-id="643dd-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="643dd-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="643dd-121">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="643dd-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="643dd-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="643dd-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="643dd-123">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="643dd-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="643dd-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="643dd-124">E_FAIL</span></span>|<span data-ttu-id="643dd-125">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="643dd-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="643dd-126">方法會傳回 E_FAIL 之後，CLR 就不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="643dd-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="643dd-127">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="643dd-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="643dd-128">備註</span><span class="sxs-lookup"><span data-stu-id="643dd-128">Remarks</span></span>  
 <span data-ttu-id="643dd-129">值，`SetGCStartupLimitsEx`可以指定只在主應用程式啟動之前。</span><span class="sxs-lookup"><span data-stu-id="643dd-129">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="643dd-130">稍後呼叫`SetGCStartupLimitsEx`都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="643dd-130">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="643dd-131">若要設定其中一個參數，而不會影響其他，您不想要變更為的參數指定 0 （零）。</span><span class="sxs-lookup"><span data-stu-id="643dd-131">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="643dd-132">需求</span><span class="sxs-lookup"><span data-stu-id="643dd-132">Requirements</span></span>  
 <span data-ttu-id="643dd-133">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="643dd-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="643dd-134">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="643dd-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="643dd-135">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="643dd-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="643dd-136">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="643dd-136">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="643dd-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="643dd-137">See Also</span></span>  
 [<span data-ttu-id="643dd-138">自動管理記憶體</span><span class="sxs-lookup"><span data-stu-id="643dd-138">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="643dd-139">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="643dd-139">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)  
 [<span data-ttu-id="643dd-140">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="643dd-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="643dd-141">ICLRGCManager2 介面</span><span class="sxs-lookup"><span data-stu-id="643dd-141">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)
