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
ms.openlocfilehash: 77de550cd3fb614e03f8028707c3cbf914734910
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141097"
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="fe71e-102">ICLRGCManager2::SetGCStartupLimitsEx 方法</span><span class="sxs-lookup"><span data-stu-id="fe71e-102">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="fe71e-103">設定垃圾收集區段的大小，以及垃圾收集系統層代0的大小上限。</span><span class="sxs-lookup"><span data-stu-id="fe71e-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe71e-104">語法</span><span class="sxs-lookup"><span data-stu-id="fe71e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,   
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe71e-105">參數</span><span class="sxs-lookup"><span data-stu-id="fe71e-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="fe71e-106">在垃圾收集區段的指定大小。</span><span class="sxs-lookup"><span data-stu-id="fe71e-106">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="fe71e-107">最社區段大小為 4 MB。</span><span class="sxs-lookup"><span data-stu-id="fe71e-107">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="fe71e-108">區段可以增加 1 MB 或更大的增量。</span><span class="sxs-lookup"><span data-stu-id="fe71e-108">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="fe71e-109">在層代0的指定大小上限。</span><span class="sxs-lookup"><span data-stu-id="fe71e-109">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="fe71e-110">層代0的最小值為 64 KB。</span><span class="sxs-lookup"><span data-stu-id="fe71e-110">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe71e-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="fe71e-111">Return Value</span></span>  
  
|<span data-ttu-id="fe71e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fe71e-112">HRESULT</span></span>|<span data-ttu-id="fe71e-113">描述</span><span class="sxs-lookup"><span data-stu-id="fe71e-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fe71e-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="fe71e-114">S_OK</span></span>|<span data-ttu-id="fe71e-115">已成功傳回 `SetGCStartupLimitsEx`。</span><span class="sxs-lookup"><span data-stu-id="fe71e-115">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="fe71e-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fe71e-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fe71e-117">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="fe71e-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fe71e-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fe71e-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fe71e-119">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="fe71e-119">The call timed out.</span></span>|  
|<span data-ttu-id="fe71e-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fe71e-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fe71e-121">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="fe71e-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fe71e-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fe71e-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fe71e-123">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="fe71e-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fe71e-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fe71e-124">E_FAIL</span></span>|<span data-ttu-id="fe71e-125">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="fe71e-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fe71e-126">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="fe71e-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fe71e-127">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="fe71e-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe71e-128">備註</span><span class="sxs-lookup"><span data-stu-id="fe71e-128">Remarks</span></span>  
 <span data-ttu-id="fe71e-129">只有在啟動主機之前，才可以指定 `SetGCStartupLimitsEx` 設定的值。</span><span class="sxs-lookup"><span data-stu-id="fe71e-129">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="fe71e-130">稍後會忽略 `SetGCStartupLimitsEx` 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="fe71e-130">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="fe71e-131">若要設定其中一個參數而不影響另一個，請針對您不想要變更的參數指定0（零）。</span><span class="sxs-lookup"><span data-stu-id="fe71e-131">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe71e-132">需求</span><span class="sxs-lookup"><span data-stu-id="fe71e-132">Requirements</span></span>  
 <span data-ttu-id="fe71e-133">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fe71e-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe71e-134">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="fe71e-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fe71e-135">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fe71e-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fe71e-136">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe71e-136">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe71e-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="fe71e-137">See also</span></span>

- [<span data-ttu-id="fe71e-138">自動管理記憶體</span><span class="sxs-lookup"><span data-stu-id="fe71e-138">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="fe71e-139">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="fe71e-139">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="fe71e-140">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="fe71e-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="fe71e-141">ICLRGCManager2 介面</span><span class="sxs-lookup"><span data-stu-id="fe71e-141">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)
