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
ms.openlocfilehash: 103deb5ec46ba8c1d385c5339bc52a0c220c4c93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439764"
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="e623c-102">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="e623c-102">IHostSemaphore Interface</span></span>
<span data-ttu-id="e623c-103">表示執行緒的號誌的主機的實作。</span><span class="sxs-lookup"><span data-stu-id="e623c-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e623c-104">方法</span><span class="sxs-lookup"><span data-stu-id="e623c-104">Methods</span></span>  
  
|<span data-ttu-id="e623c-105">方法</span><span class="sxs-lookup"><span data-stu-id="e623c-105">Method</span></span>|<span data-ttu-id="e623c-106">描述</span><span class="sxs-lookup"><span data-stu-id="e623c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e623c-107">ReleaseSemaphore 方法</span><span class="sxs-lookup"><span data-stu-id="e623c-107">ReleaseSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="e623c-108">會在目前的計數增加`IHostSemaphore`執行個體，以指定的數量。</span><span class="sxs-lookup"><span data-stu-id="e623c-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="e623c-109">Wait 方法</span><span class="sxs-lookup"><span data-stu-id="e623c-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)|<span data-ttu-id="e623c-110">造成目前`IHostSemaphore`等候，直到它擁有的執行個體或指定的經過時間量。</span><span class="sxs-lookup"><span data-stu-id="e623c-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e623c-111">需求</span><span class="sxs-lookup"><span data-stu-id="e623c-111">Requirements</span></span>  
 <span data-ttu-id="e623c-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e623c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e623c-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e623c-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e623c-114">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e623c-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e623c-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e623c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e623c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e623c-116">See Also</span></span>  
 [<span data-ttu-id="e623c-117">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="e623c-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="e623c-118">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="e623c-118">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="e623c-119">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="e623c-119">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="e623c-120">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="e623c-120">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="e623c-121">裝載介面</span><span class="sxs-lookup"><span data-stu-id="e623c-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
