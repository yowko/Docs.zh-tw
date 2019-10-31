---
title: IHostManualEvent::Reset 方法
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Reset
helpviewer_keywords:
- Reset method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Reset method [.NET Framework hosting]
ms.assetid: 0d101168-b5e3-49ce-90c7-85cf2db83c4c
topic_type:
- apiref
ms.openlocfilehash: 464093291648d7c5c1f2001fbaef85fcd5d592de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136795"
---
# <a name="ihostmanualeventreset-method"></a><span data-ttu-id="4cbc4-102">IHostManualEvent::Reset 方法</span><span class="sxs-lookup"><span data-stu-id="4cbc4-102">IHostManualEvent::Reset Method</span></span>
<span data-ttu-id="4cbc4-103">將目前的[IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)實例重設為未收到信號的狀態。</span><span class="sxs-lookup"><span data-stu-id="4cbc4-103">Resets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a non-signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cbc4-104">語法</span><span class="sxs-lookup"><span data-stu-id="4cbc4-104">Syntax</span></span>  
  
```cpp  
HRESULT Reset ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4cbc4-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="4cbc4-105">Return Value</span></span>  
  
|<span data-ttu-id="4cbc4-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4cbc4-106">HRESULT</span></span>|<span data-ttu-id="4cbc4-107">描述</span><span class="sxs-lookup"><span data-stu-id="4cbc4-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4cbc4-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="4cbc4-108">S_OK</span></span>|<span data-ttu-id="4cbc4-109">已成功傳回 `Reset`。</span><span class="sxs-lookup"><span data-stu-id="4cbc4-109">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="4cbc4-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4cbc4-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4cbc4-111">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="4cbc4-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4cbc4-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4cbc4-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4cbc4-113">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="4cbc4-113">The call timed out.</span></span>|  
|<span data-ttu-id="4cbc4-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4cbc4-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4cbc4-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="4cbc4-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4cbc4-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4cbc4-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4cbc4-117">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="4cbc4-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4cbc4-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4cbc4-118">E_FAIL</span></span>|<span data-ttu-id="4cbc4-119">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="4cbc4-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4cbc4-120">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="4cbc4-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4cbc4-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="4cbc4-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4cbc4-122">需求</span><span class="sxs-lookup"><span data-stu-id="4cbc4-122">Requirements</span></span>  
 <span data-ttu-id="4cbc4-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4cbc4-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cbc4-124">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="4cbc4-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4cbc4-125">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4cbc4-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4cbc4-126">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cbc4-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cbc4-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="4cbc4-127">See also</span></span>

- [<span data-ttu-id="4cbc4-128">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="4cbc4-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="4cbc4-129">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="4cbc4-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="4cbc4-130">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="4cbc4-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="4cbc4-131">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="4cbc4-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="4cbc4-132">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="4cbc4-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
