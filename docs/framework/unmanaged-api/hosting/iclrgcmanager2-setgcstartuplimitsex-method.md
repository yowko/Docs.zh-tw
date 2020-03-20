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
ms.openlocfilehash: 9885149a71147db6eef13958b8ef825caa1d6ec6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176379"
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="b04ea-102">ICLRGCManager2::SetGCStartupLimitsEx 方法</span><span class="sxs-lookup"><span data-stu-id="b04ea-102">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="b04ea-103">設置垃圾回收段的大小和垃圾回收系統第 0 代的最大大小。</span><span class="sxs-lookup"><span data-stu-id="b04ea-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b04ea-104">語法</span><span class="sxs-lookup"><span data-stu-id="b04ea-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b04ea-105">參數</span><span class="sxs-lookup"><span data-stu-id="b04ea-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="b04ea-106">[在]垃圾回收段的指定大小。</span><span class="sxs-lookup"><span data-stu-id="b04ea-106">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="b04ea-107">最小段大小為 4 MB。</span><span class="sxs-lookup"><span data-stu-id="b04ea-107">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="b04ea-108">段可以以 1 MB 或更大的增量增加。</span><span class="sxs-lookup"><span data-stu-id="b04ea-108">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="b04ea-109">[在]第 0 代的指定最大大小。</span><span class="sxs-lookup"><span data-stu-id="b04ea-109">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="b04ea-110">最小生成 0 大小為 64 KB。</span><span class="sxs-lookup"><span data-stu-id="b04ea-110">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b04ea-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="b04ea-111">Return Value</span></span>  
  
|<span data-ttu-id="b04ea-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b04ea-112">HRESULT</span></span>|<span data-ttu-id="b04ea-113">描述</span><span class="sxs-lookup"><span data-stu-id="b04ea-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b04ea-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="b04ea-114">S_OK</span></span>|<span data-ttu-id="b04ea-115">`SetGCStartupLimitsEx`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="b04ea-115">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="b04ea-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b04ea-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b04ea-117">公共語言運行時 （CLR） 尚未載入到進程中，或者 CLR 處於無法運行託管代碼或成功處理調用的狀態。</span><span class="sxs-lookup"><span data-stu-id="b04ea-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b04ea-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b04ea-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b04ea-119">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="b04ea-119">The call timed out.</span></span>|  
|<span data-ttu-id="b04ea-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b04ea-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b04ea-121">調用方不擁有鎖。</span><span class="sxs-lookup"><span data-stu-id="b04ea-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b04ea-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b04ea-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b04ea-123">當阻塞的執行緒或光纖等待事件時，事件已被取消。</span><span class="sxs-lookup"><span data-stu-id="b04ea-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b04ea-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b04ea-124">E_FAIL</span></span>|<span data-ttu-id="b04ea-125">發生了未知的災難性故障。</span><span class="sxs-lookup"><span data-stu-id="b04ea-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b04ea-126">方法返回E_FAIL後，CLR 在進程中不再可用。</span><span class="sxs-lookup"><span data-stu-id="b04ea-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b04ea-127">對託管方法的後續調用返回HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b04ea-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b04ea-128">備註</span><span class="sxs-lookup"><span data-stu-id="b04ea-128">Remarks</span></span>  
 <span data-ttu-id="b04ea-129">只能在啟動主機`SetGCStartupLimitsEx`之前指定設置的值。</span><span class="sxs-lookup"><span data-stu-id="b04ea-129">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="b04ea-130">稍後將忽略對`SetGCStartupLimitsEx`的調用。</span><span class="sxs-lookup"><span data-stu-id="b04ea-130">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="b04ea-131">要設置任一參數而不影響另一個參數，請為不想更改的參數指定 0（零）。</span><span class="sxs-lookup"><span data-stu-id="b04ea-131">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b04ea-132">需求</span><span class="sxs-lookup"><span data-stu-id="b04ea-132">Requirements</span></span>  
 <span data-ttu-id="b04ea-133">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b04ea-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b04ea-134">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b04ea-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b04ea-135">**庫：** 作為資源包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="b04ea-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b04ea-136">**.NET 框架版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b04ea-136">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b04ea-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b04ea-137">See also</span></span>

- [<span data-ttu-id="b04ea-138">自動記憶體管理</span><span class="sxs-lookup"><span data-stu-id="b04ea-138">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="b04ea-139">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="b04ea-139">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="b04ea-140">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="b04ea-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="b04ea-141">ICLRGCManager2 介面</span><span class="sxs-lookup"><span data-stu-id="b04ea-141">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)
