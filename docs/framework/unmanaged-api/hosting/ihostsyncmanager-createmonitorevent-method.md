---
title: IHostSyncManager::CreateMonitorEvent 方法
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateMonitorEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateMonitorEvent
helpviewer_keywords:
- CreateMonitorEvent method [.NET Framework hosting]
- IHostSyncManager::CreateMonitorEvent method [.NET Framework hosting]
ms.assetid: 524c7fd3-9b5c-46e7-99ba-555fd2fe33f0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d06f1c93275cb6adf4f1da02ccd5d889cb06c5d0
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45520846"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="58000-102">IHostSyncManager::CreateMonitorEvent 方法</span><span class="sxs-lookup"><span data-stu-id="58000-102">IHostSyncManager::CreateMonitorEvent Method</span></span>
<span data-ttu-id="58000-103">建立受監視的自動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="58000-103">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58000-104">語法</span><span class="sxs-lookup"><span data-stu-id="58000-104">Syntax</span></span>  
  
```  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="58000-105">參數</span><span class="sxs-lookup"><span data-stu-id="58000-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="58000-106">[in]事件物件相關聯的 cookie。</span><span class="sxs-lookup"><span data-stu-id="58000-106">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="58000-107">[out]位址指標[IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)執行個體，或如果無法建立事件物件，則為 null。</span><span class="sxs-lookup"><span data-stu-id="58000-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="58000-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="58000-108">Return Value</span></span>  
  
|<span data-ttu-id="58000-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="58000-109">HRESULT</span></span>|<span data-ttu-id="58000-110">描述</span><span class="sxs-lookup"><span data-stu-id="58000-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="58000-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="58000-111">S_OK</span></span>|<span data-ttu-id="58000-112">`CreateMonitorEvent` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="58000-112">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="58000-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="58000-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="58000-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="58000-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="58000-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="58000-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="58000-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="58000-116">The call timed out.</span></span>|  
|<span data-ttu-id="58000-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="58000-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="58000-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="58000-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="58000-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="58000-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="58000-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="58000-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="58000-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="58000-121">E_FAIL</span></span>|<span data-ttu-id="58000-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="58000-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="58000-123">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="58000-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="58000-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="58000-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="58000-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="58000-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="58000-126">記憶體不足，無法建立要求的事件物件。</span><span class="sxs-lookup"><span data-stu-id="58000-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58000-127">備註</span><span class="sxs-lookup"><span data-stu-id="58000-127">Remarks</span></span>  
 <span data-ttu-id="58000-128">`CreateMonitorEvent` 會傳回`IHostAutoEvent`CLR 中，使用它的 managed 實作<xref:System.Threading.Monitor?displayProperty=nameWithType>型別。</span><span class="sxs-lookup"><span data-stu-id="58000-128">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="58000-129">這個方法反映 Win32`CreateEvent`函式，其值為`false`指定`bManualReset`參數。</span><span class="sxs-lookup"><span data-stu-id="58000-129">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="58000-130">主機可以使用 cookie 來判斷哪一項工作正在等候的監視器上，藉由呼叫[iclrsyncmanager:: Getmonitorowner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="58000-130">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58000-131">需求</span><span class="sxs-lookup"><span data-stu-id="58000-131">Requirements</span></span>  
 <span data-ttu-id="58000-132">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="58000-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58000-133">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="58000-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="58000-134">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="58000-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="58000-135">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58000-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58000-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58000-136">See Also</span></span>  
 [<span data-ttu-id="58000-137">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="58000-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="58000-138">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="58000-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="58000-139">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="58000-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="58000-140">監視</span><span class="sxs-lookup"><span data-stu-id="58000-140">Monitors</span></span>](https://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)
