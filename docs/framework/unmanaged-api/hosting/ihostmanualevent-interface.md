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
ms.openlocfilehash: 7c46f00063cdf9281a5f1080594e8d6dbc6c101e
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804588"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="4eef1-102">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="4eef1-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="4eef1-103">提供主機的手動重設事件表示的執行方式。</span><span class="sxs-lookup"><span data-stu-id="4eef1-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4eef1-104">方法</span><span class="sxs-lookup"><span data-stu-id="4eef1-104">Methods</span></span>  
  
|<span data-ttu-id="4eef1-105">方法</span><span class="sxs-lookup"><span data-stu-id="4eef1-105">Method</span></span>|<span data-ttu-id="4eef1-106">描述</span><span class="sxs-lookup"><span data-stu-id="4eef1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4eef1-107">Reset 方法</span><span class="sxs-lookup"><span data-stu-id="4eef1-107">Reset Method</span></span>](ihostmanualevent-reset-method.md)|<span data-ttu-id="4eef1-108">將目前的 `IHostManualEvent` 實例重設為未收到信號的狀態。</span><span class="sxs-lookup"><span data-stu-id="4eef1-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="4eef1-109">Set 方法</span><span class="sxs-lookup"><span data-stu-id="4eef1-109">Set Method</span></span>](ihostmanualevent-set-method.md)|<span data-ttu-id="4eef1-110">將目前的 `IHostManualEvent` 實例設定為已發出信號的狀態。</span><span class="sxs-lookup"><span data-stu-id="4eef1-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="4eef1-111">Wait 方法</span><span class="sxs-lookup"><span data-stu-id="4eef1-111">Wait Method</span></span>](ihostmanualevent-wait-method.md)|<span data-ttu-id="4eef1-112">導致目前的 `IHostManualEvent` 實例等到其擁有，或經過指定的時間量為止。</span><span class="sxs-lookup"><span data-stu-id="4eef1-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4eef1-113">規格需求</span><span class="sxs-lookup"><span data-stu-id="4eef1-113">Requirements</span></span>  
 <span data-ttu-id="4eef1-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4eef1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4eef1-115">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="4eef1-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4eef1-116">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4eef1-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4eef1-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4eef1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eef1-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4eef1-118">See also</span></span>

- [<span data-ttu-id="4eef1-119">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="4eef1-119">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="4eef1-120">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="4eef1-120">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="4eef1-121">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="4eef1-121">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="4eef1-122">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="4eef1-122">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="4eef1-123">裝載介面</span><span class="sxs-lookup"><span data-stu-id="4eef1-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
