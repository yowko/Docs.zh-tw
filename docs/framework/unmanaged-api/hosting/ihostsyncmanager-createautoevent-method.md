---
title: IHostSyncManager::CreateAutoEvent 方法
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateAutoEvent
helpviewer_keywords:
- IHostSyncManager::CreateAutoEvent method [.NET Framework hosting]
- CreateAutoEvent method [.NET Framework hosting]
ms.assetid: 3153643e-cf5c-4b44-8e0e-c2b22cb08208
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9c91a982a5f3d28b43a301f961601485639bb91
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180624"
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="af83e-102">IHostSyncManager::CreateAutoEvent 方法</span><span class="sxs-lookup"><span data-stu-id="af83e-102">IHostSyncManager::CreateAutoEvent Method</span></span>
<span data-ttu-id="af83e-103">建立自動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="af83e-103">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af83e-104">語法</span><span class="sxs-lookup"><span data-stu-id="af83e-104">Syntax</span></span>  
  
```  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af83e-105">參數</span><span class="sxs-lookup"><span data-stu-id="af83e-105">Parameters</span></span>  
 `ppEvent`  
 <span data-ttu-id="af83e-106">[out]位址指標[IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)實作由主應用程式，則為 null，如果無法建立事件物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="af83e-106">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af83e-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="af83e-107">Return Value</span></span>  
  
|<span data-ttu-id="af83e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="af83e-108">HRESULT</span></span>|<span data-ttu-id="af83e-109">描述</span><span class="sxs-lookup"><span data-stu-id="af83e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="af83e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="af83e-110">S_OK</span></span>|`CreateAutoEvent` <span data-ttu-id="af83e-111">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="af83e-111">returned successfully.</span></span>|  
|<span data-ttu-id="af83e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="af83e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="af83e-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="af83e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="af83e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="af83e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="af83e-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="af83e-115">The call timed out.</span></span>|  
|<span data-ttu-id="af83e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="af83e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="af83e-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="af83e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="af83e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="af83e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="af83e-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="af83e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="af83e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="af83e-120">E_FAIL</span></span>|<span data-ttu-id="af83e-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="af83e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="af83e-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="af83e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="af83e-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="af83e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="af83e-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="af83e-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="af83e-125">記憶體不足，無法建立要求的事件物件。</span><span class="sxs-lookup"><span data-stu-id="af83e-125">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af83e-126">備註</span><span class="sxs-lookup"><span data-stu-id="af83e-126">Remarks</span></span>  
 `CreateAutoEvent` <span data-ttu-id="af83e-127">建立自動事件物件，其狀態會自動變更為未收到信號等候執行緒釋出之後。</span><span class="sxs-lookup"><span data-stu-id="af83e-127">creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="af83e-128">這個方法反映 Win32`CreateEvent`函數中使用的值`false`指定`bManualReset`參數</span><span class="sxs-lookup"><span data-stu-id="af83e-128">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af83e-129">需求</span><span class="sxs-lookup"><span data-stu-id="af83e-129">Requirements</span></span>  
 <span data-ttu-id="af83e-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="af83e-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af83e-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="af83e-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="af83e-132">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="af83e-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="af83e-133">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="af83e-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="af83e-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af83e-134">See also</span></span>

- [<span data-ttu-id="af83e-135">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="af83e-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="af83e-136">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="af83e-136">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="af83e-137">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="af83e-137">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="af83e-138">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="af83e-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
