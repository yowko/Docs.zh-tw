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
ms.openlocfilehash: 2cf490bcd167b7a498ae21f479f616694ccb5521
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139475"
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="62743-102">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="62743-102">IHostSemaphore Interface</span></span>
<span data-ttu-id="62743-103">表示執行緒之信號的主機執行。</span><span class="sxs-lookup"><span data-stu-id="62743-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="62743-104">方法</span><span class="sxs-lookup"><span data-stu-id="62743-104">Methods</span></span>  
  
|<span data-ttu-id="62743-105">方法</span><span class="sxs-lookup"><span data-stu-id="62743-105">Method</span></span>|<span data-ttu-id="62743-106">描述</span><span class="sxs-lookup"><span data-stu-id="62743-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="62743-107">ReleaseSemaphore 方法</span><span class="sxs-lookup"><span data-stu-id="62743-107">ReleaseSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="62743-108">依指定的數量增加目前 `IHostSemaphore` 實例的計數。</span><span class="sxs-lookup"><span data-stu-id="62743-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="62743-109">Wait 方法</span><span class="sxs-lookup"><span data-stu-id="62743-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)|<span data-ttu-id="62743-110">導致目前的 `IHostSemaphore` 實例等到其擁有或指定的時間量經過之後，才會等候。</span><span class="sxs-lookup"><span data-stu-id="62743-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="62743-111">需求</span><span class="sxs-lookup"><span data-stu-id="62743-111">Requirements</span></span>  
 <span data-ttu-id="62743-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="62743-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62743-113">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="62743-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="62743-114">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="62743-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="62743-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62743-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62743-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="62743-116">See also</span></span>

- [<span data-ttu-id="62743-117">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="62743-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="62743-118">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="62743-118">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="62743-119">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="62743-119">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="62743-120">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="62743-120">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="62743-121">裝載介面</span><span class="sxs-lookup"><span data-stu-id="62743-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
