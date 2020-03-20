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
ms.openlocfilehash: 645b64c8b536029663c350bdcde9a716a715aab3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178088"
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a><span data-ttu-id="f3183-102">ICLRGCManager::SetGCStartupLimits 方法</span><span class="sxs-lookup"><span data-stu-id="f3183-102">ICLRGCManager::SetGCStartupLimits Method</span></span>
<span data-ttu-id="f3183-103">設置垃圾回收段的大小和垃圾回收系統第 0 代的最大大小。</span><span class="sxs-lookup"><span data-stu-id="f3183-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f3183-104">從 .NET 框架 4.5 開始，可以將段大小和最大生成 0 大小設置為`DWORD`大於使用[ICLRGCManager2：：setGC 啟動極限Ex](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)方法的值。</span><span class="sxs-lookup"><span data-stu-id="f3183-104">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3183-105">語法</span><span class="sxs-lookup"><span data-stu-id="f3183-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3183-106">參數</span><span class="sxs-lookup"><span data-stu-id="f3183-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="f3183-107">[在]垃圾回收段的指定大小。</span><span class="sxs-lookup"><span data-stu-id="f3183-107">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="f3183-108">最小段大小為 4 MB。</span><span class="sxs-lookup"><span data-stu-id="f3183-108">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="f3183-109">段可以以 1 MB 或更大的增量增加。</span><span class="sxs-lookup"><span data-stu-id="f3183-109">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="f3183-110">[在]第 0 代的指定最大大小。</span><span class="sxs-lookup"><span data-stu-id="f3183-110">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="f3183-111">最小生成 0 大小為 64 KB。</span><span class="sxs-lookup"><span data-stu-id="f3183-111">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3183-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="f3183-112">Return Value</span></span>  
  
|<span data-ttu-id="f3183-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f3183-113">HRESULT</span></span>|<span data-ttu-id="f3183-114">描述</span><span class="sxs-lookup"><span data-stu-id="f3183-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f3183-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="f3183-115">S_OK</span></span>|<span data-ttu-id="f3183-116">`SetGCStartupLimits`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="f3183-116">`SetGCStartupLimits` returned successfully.</span></span>|  
|<span data-ttu-id="f3183-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f3183-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f3183-118">公共語言運行時 （CLR） 尚未載入到進程中，或者 CLR 處於無法運行託管代碼或成功處理調用的狀態。</span><span class="sxs-lookup"><span data-stu-id="f3183-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f3183-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f3183-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f3183-120">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="f3183-120">The call timed out.</span></span>|  
|<span data-ttu-id="f3183-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f3183-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f3183-122">調用方不擁有鎖。</span><span class="sxs-lookup"><span data-stu-id="f3183-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f3183-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f3183-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f3183-124">當阻塞的執行緒或光纖等待事件時，事件已被取消。</span><span class="sxs-lookup"><span data-stu-id="f3183-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f3183-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f3183-125">E_FAIL</span></span>|<span data-ttu-id="f3183-126">發生了未知的災難性故障。</span><span class="sxs-lookup"><span data-stu-id="f3183-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f3183-127">方法返回E_FAIL後，CLR 在進程中不再可用。</span><span class="sxs-lookup"><span data-stu-id="f3183-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f3183-128">對託管方法的後續調用返回HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="f3183-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3183-129">備註</span><span class="sxs-lookup"><span data-stu-id="f3183-129">Remarks</span></span>  
 <span data-ttu-id="f3183-130">只能指定一`SetGCStartupLimits`次設置的值。</span><span class="sxs-lookup"><span data-stu-id="f3183-130">The values that `SetGCStartupLimits` sets can be specified only once.</span></span> <span data-ttu-id="f3183-131">稍後將忽略對`SetGCStartupLimits`的調用。</span><span class="sxs-lookup"><span data-stu-id="f3183-131">Later calls to `SetGCStartupLimits` are ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3183-132">需求</span><span class="sxs-lookup"><span data-stu-id="f3183-132">Requirements</span></span>  
 <span data-ttu-id="f3183-133">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f3183-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3183-134">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f3183-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f3183-135">**庫：** 作為資源包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="f3183-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f3183-136">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3183-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3183-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3183-137">See also</span></span>

- [<span data-ttu-id="f3183-138">自動記憶體管理</span><span class="sxs-lookup"><span data-stu-id="f3183-138">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="f3183-139">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="f3183-139">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="f3183-140">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="f3183-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="f3183-141">ICLRGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="f3183-141">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
