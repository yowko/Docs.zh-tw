---
title: "IHostSemaphore 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSemaphore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSemaphore
helpviewer_keywords: IHostSemaphore interface [.NET Framework hosting]
ms.assetid: c0765321-656c-441e-bab5-58176292be1e
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 67b3225186f74fceadfb3104145743823ef82fc2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="7925d-102">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="7925d-102">IHostSemaphore Interface</span></span>
<span data-ttu-id="7925d-103">表示執行緒的號誌的主機的實作。</span><span class="sxs-lookup"><span data-stu-id="7925d-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7925d-104">方法</span><span class="sxs-lookup"><span data-stu-id="7925d-104">Methods</span></span>  
  
|<span data-ttu-id="7925d-105">方法</span><span class="sxs-lookup"><span data-stu-id="7925d-105">Method</span></span>|<span data-ttu-id="7925d-106">說明</span><span class="sxs-lookup"><span data-stu-id="7925d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7925d-107">ReleaseSemaphore 方法</span><span class="sxs-lookup"><span data-stu-id="7925d-107">ReleaseSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="7925d-108">會在目前的計數增加`IHostSemaphore`執行個體，以指定的數量。</span><span class="sxs-lookup"><span data-stu-id="7925d-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="7925d-109">Wait 方法</span><span class="sxs-lookup"><span data-stu-id="7925d-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)|<span data-ttu-id="7925d-110">造成目前`IHostSemaphore`等候，直到它擁有的執行個體或指定的經過時間量。</span><span class="sxs-lookup"><span data-stu-id="7925d-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7925d-111">需求</span><span class="sxs-lookup"><span data-stu-id="7925d-111">Requirements</span></span>  
 <span data-ttu-id="7925d-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7925d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7925d-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7925d-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7925d-114">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7925d-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7925d-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7925d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7925d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7925d-116">See Also</span></span>  
 [<span data-ttu-id="7925d-117">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="7925d-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="7925d-118">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="7925d-118">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="7925d-119">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="7925d-119">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="7925d-120">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="7925d-120">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="7925d-121">裝載介面</span><span class="sxs-lookup"><span data-stu-id="7925d-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
