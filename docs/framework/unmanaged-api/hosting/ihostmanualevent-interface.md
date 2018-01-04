---
title: "IHostManualEvent 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostManualEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostManualEvent
helpviewer_keywords: IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 300c2661-b7d1-4c39-b080-9ebdef0fd523
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0d55500efbe808b2fce16e869422e727b8ed0b93
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="a3426-102">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="a3426-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="a3426-103">提供的手動重設事件表示主機的實作。</span><span class="sxs-lookup"><span data-stu-id="a3426-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a3426-104">方法</span><span class="sxs-lookup"><span data-stu-id="a3426-104">Methods</span></span>  
  
|<span data-ttu-id="a3426-105">方法</span><span class="sxs-lookup"><span data-stu-id="a3426-105">Method</span></span>|<span data-ttu-id="a3426-106">描述</span><span class="sxs-lookup"><span data-stu-id="a3426-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a3426-107">Reset 方法</span><span class="sxs-lookup"><span data-stu-id="a3426-107">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|<span data-ttu-id="a3426-108">重設目前`IHostManualEvent`未收到信號狀態的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a3426-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="a3426-109">Set 方法</span><span class="sxs-lookup"><span data-stu-id="a3426-109">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|<span data-ttu-id="a3426-110">設定目前`IHostManualEvent`收到信號狀態的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a3426-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="a3426-111">Wait 方法</span><span class="sxs-lookup"><span data-stu-id="a3426-111">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|<span data-ttu-id="a3426-112">造成目前`IHostManualEvent`等候，直到它擁有，執行個體或指定的經過時間量。</span><span class="sxs-lookup"><span data-stu-id="a3426-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a3426-113">需求</span><span class="sxs-lookup"><span data-stu-id="a3426-113">Requirements</span></span>  
 <span data-ttu-id="a3426-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a3426-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3426-115">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a3426-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a3426-116">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a3426-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3426-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3426-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3426-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="a3426-118">See Also</span></span>  
 [<span data-ttu-id="a3426-119">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="a3426-119">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="a3426-120">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="a3426-120">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="a3426-121">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="a3426-121">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="a3426-122">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="a3426-122">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="a3426-123">裝載介面</span><span class="sxs-lookup"><span data-stu-id="a3426-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
