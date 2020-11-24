---
title: IHostManualEvent 介面
ms.date: 03/30/2017
api_name:
- IHostManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent
helpviewer_keywords:
- IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 300c2661-b7d1-4c39-b080-9ebdef0fd523
topic_type:
- apiref
ms.openlocfilehash: 50e37b770e3ee6e0a5cdfca61fc5b09749e5735f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673191"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="945ee-102">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="945ee-102">IHostManualEvent Interface</span></span>

<span data-ttu-id="945ee-103">提供主機手動重設事件標記法的實作為。</span><span class="sxs-lookup"><span data-stu-id="945ee-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="945ee-104">方法</span><span class="sxs-lookup"><span data-stu-id="945ee-104">Methods</span></span>  
  
|<span data-ttu-id="945ee-105">方法</span><span class="sxs-lookup"><span data-stu-id="945ee-105">Method</span></span>|<span data-ttu-id="945ee-106">描述</span><span class="sxs-lookup"><span data-stu-id="945ee-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="945ee-107">Reset 方法</span><span class="sxs-lookup"><span data-stu-id="945ee-107">Reset Method</span></span>](ihostmanualevent-reset-method.md)|<span data-ttu-id="945ee-108">將目前的 `IHostManualEvent` 實例重設為未收到信號的狀態。</span><span class="sxs-lookup"><span data-stu-id="945ee-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="945ee-109">Set 方法</span><span class="sxs-lookup"><span data-stu-id="945ee-109">Set Method</span></span>](ihostmanualevent-set-method.md)|<span data-ttu-id="945ee-110">將目前的 `IHostManualEvent` 實例設定為已發出信號的狀態。</span><span class="sxs-lookup"><span data-stu-id="945ee-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="945ee-111">Wait 方法</span><span class="sxs-lookup"><span data-stu-id="945ee-111">Wait Method</span></span>](ihostmanualevent-wait-method.md)|<span data-ttu-id="945ee-112">導致目前的 `IHostManualEvent` 實例等到其擁有或經過指定的時間量為止。</span><span class="sxs-lookup"><span data-stu-id="945ee-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="945ee-113">需求</span><span class="sxs-lookup"><span data-stu-id="945ee-113">Requirements</span></span>  

 <span data-ttu-id="945ee-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="945ee-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="945ee-115">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="945ee-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="945ee-116">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="945ee-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="945ee-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="945ee-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="945ee-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="945ee-118">See also</span></span>

- [<span data-ttu-id="945ee-119">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="945ee-119">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="945ee-120">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="945ee-120">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="945ee-121">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="945ee-121">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="945ee-122">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="945ee-122">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="945ee-123">裝載介面</span><span class="sxs-lookup"><span data-stu-id="945ee-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
