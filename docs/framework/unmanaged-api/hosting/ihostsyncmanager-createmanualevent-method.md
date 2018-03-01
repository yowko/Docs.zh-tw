---
title: "IHostSyncManager::CreateManualEvent 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostSyncManager.CreateManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateManualEvent
helpviewer_keywords:
- CreateManualEvent method [.NET Framework hosting]
- IHostSyncManager::CreateManualEvent method [.NET Framework hosting]
ms.assetid: 68661fbd-09cf-46dc-890b-e694f8a3880a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 347eaa64b8a5e5b5c9494a779e3d583b10d80052
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanagercreatemanualevent-method"></a><span data-ttu-id="4bd2f-102">IHostSyncManager::CreateManualEvent 方法</span><span class="sxs-lookup"><span data-stu-id="4bd2f-102">IHostSyncManager::CreateManualEvent Method</span></span>
<span data-ttu-id="4bd2f-103">建立手動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="4bd2f-103">Creates a manual-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bd2f-104">語法</span><span class="sxs-lookup"><span data-stu-id="4bd2f-104">Syntax</span></span>  
  
```  
HRESULT CreateManualEvent (  
    [in]  BOOL bInitialState,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4bd2f-105">參數</span><span class="sxs-lookup"><span data-stu-id="4bd2f-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="4bd2f-106">[in]`true`，則物件為收到信號，否則`false`。</span><span class="sxs-lookup"><span data-stu-id="4bd2f-106">[in] `true`, if the object is signaled; otherwise, `false`.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="4bd2f-107">[out]位址指標[IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)執行個體，或如果無法建立事件，則為 null。</span><span class="sxs-lookup"><span data-stu-id="4bd2f-107">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4bd2f-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="4bd2f-108">Return Value</span></span>  
  
|<span data-ttu-id="4bd2f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4bd2f-109">HRESULT</span></span>|<span data-ttu-id="4bd2f-110">描述</span><span class="sxs-lookup"><span data-stu-id="4bd2f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4bd2f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4bd2f-111">S_OK</span></span>|<span data-ttu-id="4bd2f-112">`CreateManualEvent`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="4bd2f-112">`CreateManualEvent` returned successfully.</span></span>|  
|<span data-ttu-id="4bd2f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4bd2f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4bd2f-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="4bd2f-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4bd2f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4bd2f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4bd2f-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="4bd2f-116">The call timed out.</span></span>|  
|<span data-ttu-id="4bd2f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4bd2f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4bd2f-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="4bd2f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4bd2f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4bd2f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4bd2f-120">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="4bd2f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4bd2f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4bd2f-121">E_FAIL</span></span>|<span data-ttu-id="4bd2f-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="4bd2f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4bd2f-123">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="4bd2f-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4bd2f-124">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="4bd2f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4bd2f-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="4bd2f-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="4bd2f-126">沒有足夠的記憶體可用來建立要求的事件物件。</span><span class="sxs-lookup"><span data-stu-id="4bd2f-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bd2f-127">備註</span><span class="sxs-lookup"><span data-stu-id="4bd2f-127">Remarks</span></span>  
 <span data-ttu-id="4bd2f-128">`CreateManualEvent`建立`IHostManualEvent`，需要呼叫的手動重設事件物件[ihostmanualevent:: Reset](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)方法將它設定為未收到訊號的狀態。</span><span class="sxs-lookup"><span data-stu-id="4bd2f-128">`CreateManualEvent` creates an `IHostManualEvent`, a manual-reset event object that requires a call to the [IHostManualEvent::Reset](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md) method to set it to a non-signaled state.</span></span> <span data-ttu-id="4bd2f-129">`CreateManualEvent`鏡像處理 Win32`CreateEvent`函數中使用的值`true`指定`bManualReset`參數。</span><span class="sxs-lookup"><span data-stu-id="4bd2f-129">`CreateManualEvent` mirrors the Win32 `CreateEvent` function with a value of `true` specified for the `bManualReset` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bd2f-130">需求</span><span class="sxs-lookup"><span data-stu-id="4bd2f-130">Requirements</span></span>  
 <span data-ttu-id="4bd2f-131">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4bd2f-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bd2f-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4bd2f-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4bd2f-133">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4bd2f-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4bd2f-134">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bd2f-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bd2f-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="4bd2f-135">See Also</span></span>  
 [<span data-ttu-id="4bd2f-136">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="4bd2f-136">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="4bd2f-137">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="4bd2f-137">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="4bd2f-138">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="4bd2f-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
