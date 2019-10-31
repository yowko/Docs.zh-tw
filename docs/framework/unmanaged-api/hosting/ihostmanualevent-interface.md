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
ms.openlocfilehash: 8eba189d6dfca3781c28631a72a9af3c037efeda
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136787"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="ed49d-102">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="ed49d-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="ed49d-103">提供主機的手動重設事件表示的執行方式。</span><span class="sxs-lookup"><span data-stu-id="ed49d-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ed49d-104">方法</span><span class="sxs-lookup"><span data-stu-id="ed49d-104">Methods</span></span>  
  
|<span data-ttu-id="ed49d-105">方法</span><span class="sxs-lookup"><span data-stu-id="ed49d-105">Method</span></span>|<span data-ttu-id="ed49d-106">描述</span><span class="sxs-lookup"><span data-stu-id="ed49d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ed49d-107">Reset 方法</span><span class="sxs-lookup"><span data-stu-id="ed49d-107">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|<span data-ttu-id="ed49d-108">將目前的 `IHostManualEvent` 實例重設為未收到信號的狀態。</span><span class="sxs-lookup"><span data-stu-id="ed49d-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="ed49d-109">Set 方法</span><span class="sxs-lookup"><span data-stu-id="ed49d-109">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|<span data-ttu-id="ed49d-110">將目前的 `IHostManualEvent` 實例設定為已發出信號的狀態。</span><span class="sxs-lookup"><span data-stu-id="ed49d-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="ed49d-111">Wait 方法</span><span class="sxs-lookup"><span data-stu-id="ed49d-111">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|<span data-ttu-id="ed49d-112">導致目前的 `IHostManualEvent` 實例等到其擁有，或經過指定的時間量之後，才等待。</span><span class="sxs-lookup"><span data-stu-id="ed49d-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ed49d-113">需求</span><span class="sxs-lookup"><span data-stu-id="ed49d-113">Requirements</span></span>  
 <span data-ttu-id="ed49d-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ed49d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed49d-115">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="ed49d-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ed49d-116">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ed49d-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ed49d-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed49d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed49d-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="ed49d-118">See also</span></span>

- [<span data-ttu-id="ed49d-119">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="ed49d-119">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="ed49d-120">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="ed49d-120">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="ed49d-121">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="ed49d-121">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="ed49d-122">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="ed49d-122">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="ed49d-123">裝載介面</span><span class="sxs-lookup"><span data-stu-id="ed49d-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
