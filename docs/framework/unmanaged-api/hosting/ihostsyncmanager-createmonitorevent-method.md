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
ms.openlocfilehash: f7426585045c7ae81377ec9bfca9d397d6f734cb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192023"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="b5aa7-102">IHostSyncManager::CreateMonitorEvent 方法</span><span class="sxs-lookup"><span data-stu-id="b5aa7-102">IHostSyncManager::CreateMonitorEvent Method</span></span>
<span data-ttu-id="b5aa7-103">建立受監視的自動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="b5aa7-103">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5aa7-104">語法</span><span class="sxs-lookup"><span data-stu-id="b5aa7-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5aa7-105">參數</span><span class="sxs-lookup"><span data-stu-id="b5aa7-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="b5aa7-106">在要與事件物件產生關聯的 cookie。</span><span class="sxs-lookup"><span data-stu-id="b5aa7-106">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="b5aa7-107">脫銷[IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)實例位址的指標，如果無法建立事件物件則為 null。</span><span class="sxs-lookup"><span data-stu-id="b5aa7-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5aa7-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="b5aa7-108">Return Value</span></span>  
  
|<span data-ttu-id="b5aa7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b5aa7-109">HRESULT</span></span>|<span data-ttu-id="b5aa7-110">描述</span><span class="sxs-lookup"><span data-stu-id="b5aa7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b5aa7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b5aa7-111">S_OK</span></span>|<span data-ttu-id="b5aa7-112">已成功傳回 `CreateMonitorEvent`。</span><span class="sxs-lookup"><span data-stu-id="b5aa7-112">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="b5aa7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b5aa7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b5aa7-114">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="b5aa7-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b5aa7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b5aa7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b5aa7-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="b5aa7-116">The call timed out.</span></span>|  
|<span data-ttu-id="b5aa7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b5aa7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b5aa7-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b5aa7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b5aa7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b5aa7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b5aa7-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="b5aa7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b5aa7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b5aa7-121">E_FAIL</span></span>|<span data-ttu-id="b5aa7-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="b5aa7-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b5aa7-123">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="b5aa7-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b5aa7-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b5aa7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b5aa7-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b5aa7-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="b5aa7-126">沒有足夠的記憶體可用來建立要求的事件物件。</span><span class="sxs-lookup"><span data-stu-id="b5aa7-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5aa7-127">備註</span><span class="sxs-lookup"><span data-stu-id="b5aa7-127">Remarks</span></span>  
 <span data-ttu-id="b5aa7-128">`CreateMonitorEvent` 會傳回 CLR 在其 managed <xref:System.Threading.Monitor?displayProperty=nameWithType> 類型的執行中所使用的 `IHostAutoEvent`。</span><span class="sxs-lookup"><span data-stu-id="b5aa7-128">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="b5aa7-129">這個方法會鏡像 Win32 `CreateEvent` 函式，並為 `bManualReset` 參數指定 `false` 的值。</span><span class="sxs-lookup"><span data-stu-id="b5aa7-129">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="b5aa7-130">主機可以使用 cookie，藉由呼叫[ICLRSyncManager：： GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md)方法來判斷哪一項工作正在等候監視器。</span><span class="sxs-lookup"><span data-stu-id="b5aa7-130">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5aa7-131">需求</span><span class="sxs-lookup"><span data-stu-id="b5aa7-131">Requirements</span></span>  
 <span data-ttu-id="b5aa7-132">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b5aa7-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5aa7-133">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="b5aa7-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b5aa7-134">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b5aa7-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b5aa7-135">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5aa7-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5aa7-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="b5aa7-136">See also</span></span>

- [<span data-ttu-id="b5aa7-137">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="b5aa7-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="b5aa7-138">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="b5aa7-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="b5aa7-139">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="b5aa7-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- <xref:System.Threading.Monitor>
