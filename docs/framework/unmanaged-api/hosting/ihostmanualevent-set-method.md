---
title: "IHostManualEvent::Set 方法"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 30dcb7232d6e0f7d42de48fefd2fbb9433a50405
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmanualeventset-method"></a><span data-ttu-id="1092c-102">IHostManualEvent::Set 方法</span><span class="sxs-lookup"><span data-stu-id="1092c-102">IHostManualEvent::Set Method</span></span>
<span data-ttu-id="1092c-103">設定目前[IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)收到信號狀態的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1092c-103">Sets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1092c-104">語法</span><span class="sxs-lookup"><span data-stu-id="1092c-104">Syntax</span></span>  
  
```  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1092c-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="1092c-105">Return Value</span></span>  
  
|<span data-ttu-id="1092c-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1092c-106">HRESULT</span></span>|<span data-ttu-id="1092c-107">描述</span><span class="sxs-lookup"><span data-stu-id="1092c-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1092c-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="1092c-108">S_OK</span></span>|<span data-ttu-id="1092c-109">`Set`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="1092c-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="1092c-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1092c-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1092c-111">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="1092c-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1092c-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1092c-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1092c-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="1092c-113">The call timed out.</span></span>|  
|<span data-ttu-id="1092c-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1092c-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1092c-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="1092c-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1092c-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1092c-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1092c-117">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="1092c-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1092c-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1092c-118">E_FAIL</span></span>|<span data-ttu-id="1092c-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="1092c-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1092c-120">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="1092c-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1092c-121">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="1092c-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1092c-122">需求</span><span class="sxs-lookup"><span data-stu-id="1092c-122">Requirements</span></span>  
 <span data-ttu-id="1092c-123">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1092c-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1092c-124">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1092c-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1092c-125">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1092c-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1092c-126">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1092c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1092c-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="1092c-127">See Also</span></span>  
 [<span data-ttu-id="1092c-128">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="1092c-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="1092c-129">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="1092c-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="1092c-130">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="1092c-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="1092c-131">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="1092c-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="1092c-132">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="1092c-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
