---
title: IHostManualEvent::Set 方法
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Set
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Set
helpviewer_keywords:
- Set method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Set method [.NET Framework hosting]
ms.assetid: e930c174-f71d-4faa-bb59-f0fb3df4d77b
topic_type:
- apiref
ms.openlocfilehash: b5cd02f54a930942e1892f88fb3d8e926a6f3e1b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804562"
---
# <a name="ihostmanualeventset-method"></a><span data-ttu-id="2cfc2-102">IHostManualEvent::Set 方法</span><span class="sxs-lookup"><span data-stu-id="2cfc2-102">IHostManualEvent::Set Method</span></span>
<span data-ttu-id="2cfc2-103">將目前的[IHostManualEvent](ihostmanualevent-interface.md)實例設定為已發出信號的狀態。</span><span class="sxs-lookup"><span data-stu-id="2cfc2-103">Sets the current [IHostManualEvent](ihostmanualevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cfc2-104">語法</span><span class="sxs-lookup"><span data-stu-id="2cfc2-104">Syntax</span></span>  
  
```cpp  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2cfc2-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="2cfc2-105">Return Value</span></span>  
  
|<span data-ttu-id="2cfc2-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2cfc2-106">HRESULT</span></span>|<span data-ttu-id="2cfc2-107">描述</span><span class="sxs-lookup"><span data-stu-id="2cfc2-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2cfc2-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="2cfc2-108">S_OK</span></span>|<span data-ttu-id="2cfc2-109">`Set`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="2cfc2-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="2cfc2-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2cfc2-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2cfc2-111">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="2cfc2-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2cfc2-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2cfc2-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2cfc2-113">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="2cfc2-113">The call timed out.</span></span>|  
|<span data-ttu-id="2cfc2-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2cfc2-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2cfc2-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="2cfc2-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2cfc2-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2cfc2-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2cfc2-117">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="2cfc2-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2cfc2-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2cfc2-118">E_FAIL</span></span>|<span data-ttu-id="2cfc2-119">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="2cfc2-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2cfc2-120">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="2cfc2-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2cfc2-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="2cfc2-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2cfc2-122">規格需求</span><span class="sxs-lookup"><span data-stu-id="2cfc2-122">Requirements</span></span>  
 <span data-ttu-id="2cfc2-123">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2cfc2-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cfc2-124">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="2cfc2-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2cfc2-125">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2cfc2-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2cfc2-126">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cfc2-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cfc2-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2cfc2-127">See also</span></span>

- [<span data-ttu-id="2cfc2-128">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="2cfc2-128">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="2cfc2-129">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="2cfc2-129">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="2cfc2-130">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="2cfc2-130">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="2cfc2-131">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="2cfc2-131">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="2cfc2-132">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="2cfc2-132">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
