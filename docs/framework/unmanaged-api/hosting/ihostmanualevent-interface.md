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
ms.openlocfilehash: eb09422872a0d9565be286c25ca1b28d1c45e08f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54501694"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="ea4b2-102">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="ea4b2-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="ea4b2-103">提供手動重設事件的表示主機的實作。</span><span class="sxs-lookup"><span data-stu-id="ea4b2-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ea4b2-104">方法</span><span class="sxs-lookup"><span data-stu-id="ea4b2-104">Methods</span></span>  
  
|<span data-ttu-id="ea4b2-105">方法</span><span class="sxs-lookup"><span data-stu-id="ea4b2-105">Method</span></span>|<span data-ttu-id="ea4b2-106">描述</span><span class="sxs-lookup"><span data-stu-id="ea4b2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ea4b2-107">Reset 方法</span><span class="sxs-lookup"><span data-stu-id="ea4b2-107">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|<span data-ttu-id="ea4b2-108">重設目前`IHostManualEvent`未收到信號狀態的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ea4b2-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="ea4b2-109">Set 方法</span><span class="sxs-lookup"><span data-stu-id="ea4b2-109">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|<span data-ttu-id="ea4b2-110">設定目前`IHostManualEvent`執行個體收到信號的狀態。</span><span class="sxs-lookup"><span data-stu-id="ea4b2-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="ea4b2-111">Wait 方法</span><span class="sxs-lookup"><span data-stu-id="ea4b2-111">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|<span data-ttu-id="ea4b2-112">造成目前`IHostManualEvent`等候，直到它所屬於的執行個體或指定的時間量。</span><span class="sxs-lookup"><span data-stu-id="ea4b2-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ea4b2-113">需求</span><span class="sxs-lookup"><span data-stu-id="ea4b2-113">Requirements</span></span>  
 <span data-ttu-id="ea4b2-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ea4b2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea4b2-115">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ea4b2-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ea4b2-116">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ea4b2-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ea4b2-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea4b2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea4b2-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea4b2-118">See also</span></span>
- [<span data-ttu-id="ea4b2-119">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="ea4b2-119">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="ea4b2-120">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="ea4b2-120">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="ea4b2-121">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="ea4b2-121">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="ea4b2-122">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="ea4b2-122">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="ea4b2-123">裝載介面</span><span class="sxs-lookup"><span data-stu-id="ea4b2-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
