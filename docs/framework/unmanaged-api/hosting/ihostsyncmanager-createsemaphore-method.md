---
title: "IHostSyncManager::CreateSemaphore 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateSemaphore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateSemaphore
helpviewer_keywords:
- CreateSemaphore method [.NET Framework hosting]
- IHostSyncManager::CreateSemaphore method [.NET Framework hosting]
ms.assetid: 37679e94-5ff9-4173-8fa5-457febeb89bf
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7c7e33e4f178a4fd51ae27912959d0e4edf30ecb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanagercreatesemaphore-method"></a><span data-ttu-id="f90b4-102">IHostSyncManager::CreateSemaphore 方法</span><span class="sxs-lookup"><span data-stu-id="f90b4-102">IHostSyncManager::CreateSemaphore Method</span></span>
<span data-ttu-id="f90b4-103">建立[IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)作為等候事件信號的 common language runtime (CLR) 物件。</span><span class="sxs-lookup"><span data-stu-id="f90b4-103">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the common language runtime (CLR) to use as a semaphore for wait events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f90b4-104">語法</span><span class="sxs-lookup"><span data-stu-id="f90b4-104">Syntax</span></span>  
  
```  
HRESULT CreateSemaphore (  
    [in]  DWORD dwInitial,  
    [in]  DWORD dwMax,  
    [out] IHostSemaphore **ppSemaphore  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f90b4-105">參數</span><span class="sxs-lookup"><span data-stu-id="f90b4-105">Parameters</span></span>  
 `dwInitial`  
 <span data-ttu-id="f90b4-106">[in]初始計數`ppSemaphore`。</span><span class="sxs-lookup"><span data-stu-id="f90b4-106">[in] The initial count for `ppSemaphore`.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="f90b4-107">[in]最大計數`ppSemaphore`。</span><span class="sxs-lookup"><span data-stu-id="f90b4-107">[in] The maximum count for `ppSemaphore`.</span></span>  
  
 `ppSemaphore`  
 <span data-ttu-id="f90b4-108">[out]位址指標`IHostSemaphore`執行個體，或如果無法建立號誌，則為 null。</span><span class="sxs-lookup"><span data-stu-id="f90b4-108">[out] A pointer to the address of an `IHostSemaphore` instance, or null if the semaphore could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f90b4-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="f90b4-109">Return Value</span></span>  
  
|<span data-ttu-id="f90b4-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f90b4-110">HRESULT</span></span>|<span data-ttu-id="f90b4-111">描述</span><span class="sxs-lookup"><span data-stu-id="f90b4-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f90b4-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f90b4-112">S_OK</span></span>|<span data-ttu-id="f90b4-113">`CreateSemaphore`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="f90b4-113">`CreateSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="f90b4-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f90b4-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f90b4-115">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="f90b4-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f90b4-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f90b4-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f90b4-117">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="f90b4-117">The call timed out.</span></span>|  
|<span data-ttu-id="f90b4-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f90b4-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f90b4-119">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="f90b4-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f90b4-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f90b4-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f90b4-121">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="f90b4-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f90b4-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f90b4-122">E_FAIL</span></span>|<span data-ttu-id="f90b4-123">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="f90b4-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f90b4-124">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="f90b4-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f90b4-125">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="f90b4-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f90b4-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f90b4-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="f90b4-127">沒有足夠的記憶體可用來建立要求的事件物件。</span><span class="sxs-lookup"><span data-stu-id="f90b4-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f90b4-128">備註</span><span class="sxs-lookup"><span data-stu-id="f90b4-128">Remarks</span></span>  
 <span data-ttu-id="f90b4-129">`CreateSemaphore`鏡像有相同名稱的 Win32 函式。</span><span class="sxs-lookup"><span data-stu-id="f90b4-129">`CreateSemaphore` mirrors the Win32 function that has the same name.</span></span> <span data-ttu-id="f90b4-130">`dwInitial`和`dwMax`參數為 Win32 號誌計數為使用相同的語意`lInitialCount`和`lMaximumCount`參數，分別。</span><span class="sxs-lookup"><span data-stu-id="f90b4-130">The `dwInitial` and `dwMax` parameters use the same semantics for the semaphore count as the Win32 `lInitialCount` and `lMaximumCount` parameters, respectively.</span></span> <span data-ttu-id="f90b4-131">`dwInitial`必須介於零和`dwMax`(含） 之間。</span><span class="sxs-lookup"><span data-stu-id="f90b4-131">`dwInitial` must be between zero and `dwMax`, inclusive.</span></span> <span data-ttu-id="f90b4-132">`dwMax`必須是大於零。</span><span class="sxs-lookup"><span data-stu-id="f90b4-132">`dwMax` must be greater than zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f90b4-133">需求</span><span class="sxs-lookup"><span data-stu-id="f90b4-133">Requirements</span></span>  
 <span data-ttu-id="f90b4-134">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f90b4-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f90b4-135">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f90b4-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f90b4-136">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f90b4-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f90b4-137">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f90b4-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f90b4-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f90b4-138">See Also</span></span>  
 [<span data-ttu-id="f90b4-139">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="f90b4-139">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="f90b4-140">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="f90b4-140">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="f90b4-141">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="f90b4-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
