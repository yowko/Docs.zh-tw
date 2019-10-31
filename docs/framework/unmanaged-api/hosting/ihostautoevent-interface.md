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
ms.openlocfilehash: 2b191243ea03adcfecaadbd3a5871e1773b28bb1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124456"
---
# <a name="ihostautoevent-interface"></a><span data-ttu-id="4e277-102">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="4e277-102">IHostAutoEvent Interface</span></span>
<span data-ttu-id="4e277-103">提供主控制項的自動重設事件的執行表示。</span><span class="sxs-lookup"><span data-stu-id="4e277-103">Provides a representation of the host's implementation of an auto-reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4e277-104">方法</span><span class="sxs-lookup"><span data-stu-id="4e277-104">Methods</span></span>  
  
|<span data-ttu-id="4e277-105">方法</span><span class="sxs-lookup"><span data-stu-id="4e277-105">Method</span></span>|<span data-ttu-id="4e277-106">描述</span><span class="sxs-lookup"><span data-stu-id="4e277-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4e277-107">Set 方法</span><span class="sxs-lookup"><span data-stu-id="4e277-107">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-set-method.md)|<span data-ttu-id="4e277-108">將目前的 `IHostAutoEvent` 實例設定為已發出信號的狀態。</span><span class="sxs-lookup"><span data-stu-id="4e277-108">Sets the current `IHostAutoEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="4e277-109">Wait 方法</span><span class="sxs-lookup"><span data-stu-id="4e277-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-wait-method.md)|<span data-ttu-id="4e277-110">導致目前的 `IHostAutoEvent` 實例等到事件擁有或經過指定的時間量之後，才會等候。</span><span class="sxs-lookup"><span data-stu-id="4e277-110">Causes the current `IHostAutoEvent` instance to wait until the event is owned or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4e277-111">需求</span><span class="sxs-lookup"><span data-stu-id="4e277-111">Requirements</span></span>  
 <span data-ttu-id="4e277-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4e277-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e277-113">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="4e277-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4e277-114">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4e277-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4e277-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e277-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e277-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="4e277-116">See also</span></span>

- [<span data-ttu-id="4e277-117">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="4e277-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="4e277-118">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="4e277-118">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="4e277-119">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="4e277-119">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="4e277-120">裝載介面</span><span class="sxs-lookup"><span data-stu-id="4e277-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
