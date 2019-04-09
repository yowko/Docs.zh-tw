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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad580f7cab81323e09a24dc12db39f223be3aeb4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208627"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="eda34-102">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="eda34-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="eda34-103">提供手動重設事件的表示主機的實作。</span><span class="sxs-lookup"><span data-stu-id="eda34-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eda34-104">方法</span><span class="sxs-lookup"><span data-stu-id="eda34-104">Methods</span></span>  
  
|<span data-ttu-id="eda34-105">方法</span><span class="sxs-lookup"><span data-stu-id="eda34-105">Method</span></span>|<span data-ttu-id="eda34-106">描述</span><span class="sxs-lookup"><span data-stu-id="eda34-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eda34-107">Reset 方法</span><span class="sxs-lookup"><span data-stu-id="eda34-107">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|<span data-ttu-id="eda34-108">重設目前`IHostManualEvent`未收到信號狀態的執行個體。</span><span class="sxs-lookup"><span data-stu-id="eda34-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="eda34-109">Set 方法</span><span class="sxs-lookup"><span data-stu-id="eda34-109">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|<span data-ttu-id="eda34-110">設定目前`IHostManualEvent`執行個體收到信號的狀態。</span><span class="sxs-lookup"><span data-stu-id="eda34-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="eda34-111">Wait 方法</span><span class="sxs-lookup"><span data-stu-id="eda34-111">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|<span data-ttu-id="eda34-112">造成目前`IHostManualEvent`等候，直到它所屬於的執行個體或指定的時間量。</span><span class="sxs-lookup"><span data-stu-id="eda34-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eda34-113">需求</span><span class="sxs-lookup"><span data-stu-id="eda34-113">Requirements</span></span>  
 <span data-ttu-id="eda34-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eda34-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eda34-115">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="eda34-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eda34-116">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="eda34-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="eda34-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="eda34-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="eda34-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eda34-118">See also</span></span>

- [<span data-ttu-id="eda34-119">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="eda34-119">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="eda34-120">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="eda34-120">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="eda34-121">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="eda34-121">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="eda34-122">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="eda34-122">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="eda34-123">裝載介面</span><span class="sxs-lookup"><span data-stu-id="eda34-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
