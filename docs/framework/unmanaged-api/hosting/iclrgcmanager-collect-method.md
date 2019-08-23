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
ms.openlocfilehash: 3064a5793c6158ead85a9ff6d9b09f077d0bd603
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966245"
---
# <a name="iclrgcmanagercollect-method"></a><span data-ttu-id="807b4-102">ICLRGCManager::Collect 方法</span><span class="sxs-lookup"><span data-stu-id="807b4-102">ICLRGCManager::Collect Method</span></span>
<span data-ttu-id="807b4-103">強制執行指定之層代的垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="807b4-103">Forces a garbage collection for the specified generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="807b4-104">語法</span><span class="sxs-lookup"><span data-stu-id="807b4-104">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="807b4-105">參數</span><span class="sxs-lookup"><span data-stu-id="807b4-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="807b4-106">在要收集的世代。</span><span class="sxs-lookup"><span data-stu-id="807b4-106">[in] The generation to collect.</span></span> <span data-ttu-id="807b4-107">-1 值會強制所有層代的集合。</span><span class="sxs-lookup"><span data-stu-id="807b4-107">A value of -1 forces a collection of all generations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="807b4-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="807b4-108">Return Value</span></span>  
  
|<span data-ttu-id="807b4-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="807b4-109">HRESULT</span></span>|<span data-ttu-id="807b4-110">描述</span><span class="sxs-lookup"><span data-stu-id="807b4-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="807b4-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="807b4-111">S_OK</span></span>|<span data-ttu-id="807b4-112">`Collect`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="807b4-112">`Collect` returned successfully.</span></span>|  
|<span data-ttu-id="807b4-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="807b4-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="807b4-114">Common language runtime (CLR) 尚未載入進程中, 或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="807b4-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="807b4-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="807b4-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="807b4-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="807b4-116">The call timed out.</span></span>|  
|<span data-ttu-id="807b4-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="807b4-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="807b4-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="807b4-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="807b4-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="807b4-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="807b4-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="807b4-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="807b4-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="807b4-121">E_FAIL</span></span>|<span data-ttu-id="807b4-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="807b4-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="807b4-123">在方法傳回 E_FAIL 之後, CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="807b4-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="807b4-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="807b4-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="807b4-125">備註</span><span class="sxs-lookup"><span data-stu-id="807b4-125">Remarks</span></span>  
 <span data-ttu-id="807b4-126">`Collect`方法會強制 CLR 的垃圾收集行程執行集合, 而不論其目前的狀態為何。</span><span class="sxs-lookup"><span data-stu-id="807b4-126">The `Collect` method forces the CLR's garbage collector to perform a collection regardless of its current state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="807b4-127">需求</span><span class="sxs-lookup"><span data-stu-id="807b4-127">Requirements</span></span>  
 <span data-ttu-id="807b4-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="807b4-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="807b4-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="807b4-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="807b4-130">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="807b4-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="807b4-131">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="807b4-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="807b4-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="807b4-132">See also</span></span>

- [<span data-ttu-id="807b4-133">自動管理記憶體</span><span class="sxs-lookup"><span data-stu-id="807b4-133">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="807b4-134">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="807b4-134">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="807b4-135">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="807b4-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="807b4-136">ICLRGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="807b4-136">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="807b4-137">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="807b4-137">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="807b4-138">裝載介面</span><span class="sxs-lookup"><span data-stu-id="807b4-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="807b4-139">裝載</span><span class="sxs-lookup"><span data-stu-id="807b4-139">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
