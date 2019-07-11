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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37ba54665dbd8d10c7e7aac9a0692c8882fb5209
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767296"
---
# <a name="ihostmanualeventreset-method"></a><span data-ttu-id="f71f1-102">IHostManualEvent::Reset 方法</span><span class="sxs-lookup"><span data-stu-id="f71f1-102">IHostManualEvent::Reset Method</span></span>
<span data-ttu-id="f71f1-103">重設目前[IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)未收到信號狀態的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f71f1-103">Resets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a non-signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f71f1-104">語法</span><span class="sxs-lookup"><span data-stu-id="f71f1-104">Syntax</span></span>  
  
```cpp  
HRESULT Reset ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f71f1-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="f71f1-105">Return Value</span></span>  
  
|<span data-ttu-id="f71f1-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f71f1-106">HRESULT</span></span>|<span data-ttu-id="f71f1-107">描述</span><span class="sxs-lookup"><span data-stu-id="f71f1-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f71f1-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="f71f1-108">S_OK</span></span>|<span data-ttu-id="f71f1-109">`Reset` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="f71f1-109">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="f71f1-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f71f1-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f71f1-111">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="f71f1-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f71f1-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f71f1-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f71f1-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="f71f1-113">The call timed out.</span></span>|  
|<span data-ttu-id="f71f1-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f71f1-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f71f1-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="f71f1-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f71f1-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f71f1-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f71f1-117">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="f71f1-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f71f1-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f71f1-118">E_FAIL</span></span>|<span data-ttu-id="f71f1-119">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="f71f1-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f71f1-120">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="f71f1-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f71f1-121">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="f71f1-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f71f1-122">需求</span><span class="sxs-lookup"><span data-stu-id="f71f1-122">Requirements</span></span>  
 <span data-ttu-id="f71f1-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f71f1-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f71f1-124">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f71f1-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f71f1-125">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f71f1-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f71f1-126">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f71f1-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f71f1-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f71f1-127">See also</span></span>

- [<span data-ttu-id="f71f1-128">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="f71f1-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="f71f1-129">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="f71f1-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="f71f1-130">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="f71f1-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="f71f1-131">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="f71f1-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="f71f1-132">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="f71f1-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
