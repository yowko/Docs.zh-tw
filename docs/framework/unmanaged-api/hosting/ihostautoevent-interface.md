---
title: IHostAutoEvent 介面
ms.date: 03/30/2017
api_name:
- IHostAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent
helpviewer_keywords:
- IHostAutoEvent interface [.NET Framework hosting]
ms.assetid: 6c1d15c1-a80a-4ee9-b1e4-6e859db6575a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb5fea403f8210ea93d240aa3aabd4325524b987
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599451"
---
# <a name="ihostautoevent-interface"></a><span data-ttu-id="d3703-102">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="d3703-102">IHostAutoEvent Interface</span></span>
<span data-ttu-id="d3703-103">提供主機的自動重設事件實作的表示法。</span><span class="sxs-lookup"><span data-stu-id="d3703-103">Provides a representation of the host's implementation of an auto-reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d3703-104">方法</span><span class="sxs-lookup"><span data-stu-id="d3703-104">Methods</span></span>  
  
|<span data-ttu-id="d3703-105">方法</span><span class="sxs-lookup"><span data-stu-id="d3703-105">Method</span></span>|<span data-ttu-id="d3703-106">描述</span><span class="sxs-lookup"><span data-stu-id="d3703-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d3703-107">Set 方法</span><span class="sxs-lookup"><span data-stu-id="d3703-107">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-set-method.md)|<span data-ttu-id="d3703-108">設定目前`IHostAutoEvent`執行個體收到信號的狀態。</span><span class="sxs-lookup"><span data-stu-id="d3703-108">Sets the current `IHostAutoEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="d3703-109">Wait 方法</span><span class="sxs-lookup"><span data-stu-id="d3703-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-wait-method.md)|<span data-ttu-id="d3703-110">造成目前`IHostAutoEvent`等候，直到擁有事件的執行個體或指定的時間量。</span><span class="sxs-lookup"><span data-stu-id="d3703-110">Causes the current `IHostAutoEvent` instance to wait until the event is owned or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d3703-111">需求</span><span class="sxs-lookup"><span data-stu-id="d3703-111">Requirements</span></span>  
 <span data-ttu-id="d3703-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d3703-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3703-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d3703-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3703-114">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d3703-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3703-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3703-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3703-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3703-116">See also</span></span>

- [<span data-ttu-id="d3703-117">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="d3703-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="d3703-118">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="d3703-118">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="d3703-119">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="d3703-119">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="d3703-120">裝載介面</span><span class="sxs-lookup"><span data-stu-id="d3703-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
