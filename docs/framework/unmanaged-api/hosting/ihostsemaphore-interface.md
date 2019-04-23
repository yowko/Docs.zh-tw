---
title: IHostSemaphore 介面
ms.date: 03/30/2017
api_name:
- IHostSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore
helpviewer_keywords:
- IHostSemaphore interface [.NET Framework hosting]
ms.assetid: c0765321-656c-441e-bab5-58176292be1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d7d4a295832a958fb6a8fe2e6c43a09135500d3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182282"
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="9678e-102">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="9678e-102">IHostSemaphore Interface</span></span>
<span data-ttu-id="9678e-103">代表號誌，執行緒的主應用程式的實作。</span><span class="sxs-lookup"><span data-stu-id="9678e-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9678e-104">方法</span><span class="sxs-lookup"><span data-stu-id="9678e-104">Methods</span></span>  
  
|<span data-ttu-id="9678e-105">方法</span><span class="sxs-lookup"><span data-stu-id="9678e-105">Method</span></span>|<span data-ttu-id="9678e-106">描述</span><span class="sxs-lookup"><span data-stu-id="9678e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9678e-107">ReleaseSemaphore 方法</span><span class="sxs-lookup"><span data-stu-id="9678e-107">ReleaseSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="9678e-108">增加的目前計數`IHostSemaphore`指定數量的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9678e-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="9678e-109">Wait 方法</span><span class="sxs-lookup"><span data-stu-id="9678e-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)|<span data-ttu-id="9678e-110">造成目前`IHostSemaphore`等候，直到它擁有的執行個體或指定的時間量。</span><span class="sxs-lookup"><span data-stu-id="9678e-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9678e-111">需求</span><span class="sxs-lookup"><span data-stu-id="9678e-111">Requirements</span></span>  
 <span data-ttu-id="9678e-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9678e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9678e-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9678e-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9678e-114">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9678e-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9678e-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9678e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9678e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9678e-116">See also</span></span>

- [<span data-ttu-id="9678e-117">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="9678e-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="9678e-118">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="9678e-118">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="9678e-119">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="9678e-119">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="9678e-120">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="9678e-120">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="9678e-121">裝載介面</span><span class="sxs-lookup"><span data-stu-id="9678e-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
