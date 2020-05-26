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
ms.openlocfilehash: 8345d85502087568cb05dd262cccf181e3ca07ac
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803697"
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="f8d89-102">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="f8d89-102">IHostSemaphore Interface</span></span>
<span data-ttu-id="f8d89-103">表示執行緒之信號的主機執行。</span><span class="sxs-lookup"><span data-stu-id="f8d89-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f8d89-104">方法</span><span class="sxs-lookup"><span data-stu-id="f8d89-104">Methods</span></span>  
  
|<span data-ttu-id="f8d89-105">方法</span><span class="sxs-lookup"><span data-stu-id="f8d89-105">Method</span></span>|<span data-ttu-id="f8d89-106">描述</span><span class="sxs-lookup"><span data-stu-id="f8d89-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f8d89-107">ReleaseSemaphore 方法</span><span class="sxs-lookup"><span data-stu-id="f8d89-107">ReleaseSemaphore Method</span></span>](ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="f8d89-108">`IHostSemaphore`依指定的數量增加目前實例的計數。</span><span class="sxs-lookup"><span data-stu-id="f8d89-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="f8d89-109">Wait 方法</span><span class="sxs-lookup"><span data-stu-id="f8d89-109">Wait Method</span></span>](ihostsemaphore-wait-method.md)|<span data-ttu-id="f8d89-110">使目前的 `IHostSemaphore` 實例等到其擁有或指定的時間量經過之後，才等候。</span><span class="sxs-lookup"><span data-stu-id="f8d89-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f8d89-111">規格需求</span><span class="sxs-lookup"><span data-stu-id="f8d89-111">Requirements</span></span>  
 <span data-ttu-id="f8d89-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f8d89-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8d89-113">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="f8d89-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f8d89-114">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f8d89-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f8d89-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8d89-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8d89-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8d89-116">See also</span></span>

- [<span data-ttu-id="f8d89-117">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="f8d89-117">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="f8d89-118">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="f8d89-118">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="f8d89-119">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="f8d89-119">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="f8d89-120">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="f8d89-120">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="f8d89-121">裝載介面</span><span class="sxs-lookup"><span data-stu-id="f8d89-121">Hosting Interfaces</span></span>](hosting-interfaces.md)
