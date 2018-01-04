---
title: "IHostAutoEvent::Set 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAutoEvent.Set
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAutoEvent::Set
helpviewer_keywords:
- Set method, IHostAutoEvent interface [.NET Framework hosting]
- IHostAutoEvent::Set method [.NET Framework hosting]
ms.assetid: 46becf3e-bc0e-4338-85c0-9ab0df76a1d0
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e83da6d4e360291eca501b5af34541f9e44543f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostautoeventset-method"></a><span data-ttu-id="59432-102">IHostAutoEvent::Set 方法</span><span class="sxs-lookup"><span data-stu-id="59432-102">IHostAutoEvent::Set Method</span></span>
<span data-ttu-id="59432-103">設定目前[IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)收到信號狀態的執行個體。</span><span class="sxs-lookup"><span data-stu-id="59432-103">Sets the current [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59432-104">語法</span><span class="sxs-lookup"><span data-stu-id="59432-104">Syntax</span></span>  
  
```  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="59432-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="59432-105">Return Value</span></span>  
  
|<span data-ttu-id="59432-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="59432-106">HRESULT</span></span>|<span data-ttu-id="59432-107">描述</span><span class="sxs-lookup"><span data-stu-id="59432-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="59432-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="59432-108">S_OK</span></span>|<span data-ttu-id="59432-109">`Set`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="59432-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="59432-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="59432-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="59432-111">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="59432-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="59432-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="59432-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="59432-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="59432-113">The call timed out.</span></span>|  
|<span data-ttu-id="59432-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="59432-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="59432-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="59432-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="59432-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="59432-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="59432-117">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="59432-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="59432-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="59432-118">E_FAIL</span></span>|<span data-ttu-id="59432-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="59432-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="59432-120">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="59432-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="59432-121">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="59432-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="59432-122">需求</span><span class="sxs-lookup"><span data-stu-id="59432-122">Requirements</span></span>  
 <span data-ttu-id="59432-123">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="59432-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59432-124">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="59432-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="59432-125">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="59432-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="59432-126">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59432-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59432-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="59432-127">See Also</span></span>  
 [<span data-ttu-id="59432-128">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="59432-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="59432-129">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="59432-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="59432-130">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="59432-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="59432-131">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="59432-131">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
