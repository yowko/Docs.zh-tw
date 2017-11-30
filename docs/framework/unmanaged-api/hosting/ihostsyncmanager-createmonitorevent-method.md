---
title: "IHostSyncManager::CreateMonitorEvent 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateMonitorEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateMonitorEvent
helpviewer_keywords:
- CreateMonitorEvent method [.NET Framework hosting]
- IHostSyncManager::CreateMonitorEvent method [.NET Framework hosting]
ms.assetid: 524c7fd3-9b5c-46e7-99ba-555fd2fe33f0
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c16c1376237916d09fb4156b023f4f1cc51a7d54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="c455f-102">IHostSyncManager::CreateMonitorEvent 方法</span><span class="sxs-lookup"><span data-stu-id="c455f-102">IHostSyncManager::CreateMonitorEvent Method</span></span>
<span data-ttu-id="c455f-103">建立受監視的自動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="c455f-103">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c455f-104">語法</span><span class="sxs-lookup"><span data-stu-id="c455f-104">Syntax</span></span>  
  
```  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c455f-105">參數</span><span class="sxs-lookup"><span data-stu-id="c455f-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="c455f-106">[in]此 cookie 會與事件物件產生關聯。</span><span class="sxs-lookup"><span data-stu-id="c455f-106">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="c455f-107">[out]位址指標[IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)執行個體，或如果無法建立事件物件則為 null。</span><span class="sxs-lookup"><span data-stu-id="c455f-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c455f-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="c455f-108">Return Value</span></span>  
  
|<span data-ttu-id="c455f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c455f-109">HRESULT</span></span>|<span data-ttu-id="c455f-110">描述</span><span class="sxs-lookup"><span data-stu-id="c455f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c455f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c455f-111">S_OK</span></span>|<span data-ttu-id="c455f-112">`CreateMonitorEvent`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="c455f-112">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="c455f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c455f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c455f-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="c455f-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c455f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c455f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c455f-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="c455f-116">The call timed out.</span></span>|  
|<span data-ttu-id="c455f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c455f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c455f-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="c455f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c455f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c455f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c455f-120">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="c455f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c455f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c455f-121">E_FAIL</span></span>|<span data-ttu-id="c455f-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="c455f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c455f-123">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="c455f-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c455f-124">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="c455f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c455f-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="c455f-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="c455f-126">沒有足夠的記憶體可用來建立要求的事件物件。</span><span class="sxs-lookup"><span data-stu-id="c455f-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c455f-127">備註</span><span class="sxs-lookup"><span data-stu-id="c455f-127">Remarks</span></span>  
 <span data-ttu-id="c455f-128">`CreateMonitorEvent`傳回`IHostAutoEvent`，供 CLR 用於在實作 managed<xref:System.Threading.Monitor?displayProperty=nameWithType>型別。</span><span class="sxs-lookup"><span data-stu-id="c455f-128">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="c455f-129">這個方法會反映 Win32`CreateEvent`函式，其值為`false`指定`bManualReset`參數。</span><span class="sxs-lookup"><span data-stu-id="c455f-129">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="c455f-130">主機可以使用 cookie 來判斷哪一項工作在等候監視器上，藉由呼叫[iclrsyncmanager:: Getmonitorowner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="c455f-130">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c455f-131">需求</span><span class="sxs-lookup"><span data-stu-id="c455f-131">Requirements</span></span>  
 <span data-ttu-id="c455f-132">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c455f-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c455f-133">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c455f-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c455f-134">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c455f-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c455f-135">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c455f-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c455f-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c455f-136">See Also</span></span>  
 [<span data-ttu-id="c455f-137">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="c455f-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="c455f-138">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="c455f-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="c455f-139">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="c455f-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="c455f-140">監視</span><span class="sxs-lookup"><span data-stu-id="c455f-140">Monitors</span></span>](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)
