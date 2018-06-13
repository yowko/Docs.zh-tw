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
ms.openlocfilehash: fe1b685f50f793f7451187f17adc848ec9d4422f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440199"
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="0ebe3-102">IHostSyncManager::CreateAutoEvent 方法</span><span class="sxs-lookup"><span data-stu-id="0ebe3-102">IHostSyncManager::CreateAutoEvent Method</span></span>
<span data-ttu-id="0ebe3-103">建立的自動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="0ebe3-103">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ebe3-104">語法</span><span class="sxs-lookup"><span data-stu-id="0ebe3-104">Syntax</span></span>  
  
```  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0ebe3-105">參數</span><span class="sxs-lookup"><span data-stu-id="0ebe3-105">Parameters</span></span>  
 `ppEvent`  
 <span data-ttu-id="0ebe3-106">[out]位址指標[IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)實作由主應用程式，則為 null，如果無法建立事件物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0ebe3-106">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ebe3-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="0ebe3-107">Return Value</span></span>  
  
|<span data-ttu-id="0ebe3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0ebe3-108">HRESULT</span></span>|<span data-ttu-id="0ebe3-109">描述</span><span class="sxs-lookup"><span data-stu-id="0ebe3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0ebe3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0ebe3-110">S_OK</span></span>|<span data-ttu-id="0ebe3-111">`CreateAutoEvent` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="0ebe3-111">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="0ebe3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0ebe3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0ebe3-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="0ebe3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0ebe3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0ebe3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0ebe3-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="0ebe3-115">The call timed out.</span></span>|  
|<span data-ttu-id="0ebe3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0ebe3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0ebe3-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="0ebe3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0ebe3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0ebe3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0ebe3-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="0ebe3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0ebe3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0ebe3-120">E_FAIL</span></span>|<span data-ttu-id="0ebe3-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="0ebe3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0ebe3-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="0ebe3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0ebe3-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="0ebe3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0ebe3-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0ebe3-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0ebe3-125">沒有足夠的記憶體可用來建立要求的事件物件。</span><span class="sxs-lookup"><span data-stu-id="0ebe3-125">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ebe3-126">備註</span><span class="sxs-lookup"><span data-stu-id="0ebe3-126">Remarks</span></span>  
 <span data-ttu-id="0ebe3-127">`CreateAutoEvent` 建立其狀態會自動變更為未收到訊號等候的執行緒釋放之後的自動事件物件。</span><span class="sxs-lookup"><span data-stu-id="0ebe3-127">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="0ebe3-128">這個方法會反映 Win32`CreateEvent`函數中使用的值`false`指定`bManualReset`參數</span><span class="sxs-lookup"><span data-stu-id="0ebe3-128">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ebe3-129">需求</span><span class="sxs-lookup"><span data-stu-id="0ebe3-129">Requirements</span></span>  
 <span data-ttu-id="0ebe3-130">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0ebe3-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ebe3-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0ebe3-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ebe3-132">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0ebe3-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ebe3-133">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ebe3-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ebe3-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ebe3-134">See Also</span></span>  
 [<span data-ttu-id="0ebe3-135">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="0ebe3-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="0ebe3-136">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="0ebe3-136">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="0ebe3-137">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="0ebe3-137">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="0ebe3-138">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="0ebe3-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
