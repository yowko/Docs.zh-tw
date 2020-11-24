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
ms.openlocfilehash: cccbf9a28b16ffee14b3fd3ec43c376109d6ccec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683052"
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="fd370-102">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="fd370-102">IHostSemaphore Interface</span></span>

<span data-ttu-id="fd370-103">代表主機針對執行緒所執行的信號。</span><span class="sxs-lookup"><span data-stu-id="fd370-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fd370-104">方法</span><span class="sxs-lookup"><span data-stu-id="fd370-104">Methods</span></span>  
  
|<span data-ttu-id="fd370-105">方法</span><span class="sxs-lookup"><span data-stu-id="fd370-105">Method</span></span>|<span data-ttu-id="fd370-106">描述</span><span class="sxs-lookup"><span data-stu-id="fd370-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fd370-107">ReleaseSemaphore 方法</span><span class="sxs-lookup"><span data-stu-id="fd370-107">ReleaseSemaphore Method</span></span>](ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="fd370-108">依指定的數量增加目前 `IHostSemaphore` 實例的計數。</span><span class="sxs-lookup"><span data-stu-id="fd370-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="fd370-109">Wait 方法</span><span class="sxs-lookup"><span data-stu-id="fd370-109">Wait Method</span></span>](ihostsemaphore-wait-method.md)|<span data-ttu-id="fd370-110">導致目前的 `IHostSemaphore` 實例等到其擁有或經過指定的時間量為止。</span><span class="sxs-lookup"><span data-stu-id="fd370-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fd370-111">需求</span><span class="sxs-lookup"><span data-stu-id="fd370-111">Requirements</span></span>  

 <span data-ttu-id="fd370-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fd370-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd370-113">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="fd370-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fd370-114">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="fd370-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fd370-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd370-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd370-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd370-116">See also</span></span>

- [<span data-ttu-id="fd370-117">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="fd370-117">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="fd370-118">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="fd370-118">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="fd370-119">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="fd370-119">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="fd370-120">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="fd370-120">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="fd370-121">裝載介面</span><span class="sxs-lookup"><span data-stu-id="fd370-121">Hosting Interfaces</span></span>](hosting-interfaces.md)
