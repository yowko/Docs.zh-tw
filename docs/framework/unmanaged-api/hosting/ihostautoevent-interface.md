---
title: "IHostAutoEvent 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAutoEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAutoEvent
helpviewer_keywords: IHostAutoEvent interface [.NET Framework hosting]
ms.assetid: 6c1d15c1-a80a-4ee9-b1e4-6e859db6575a
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8c99bde7641ee640df06be71fc43a7f8774f7ff3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihostautoevent-interface"></a><span data-ttu-id="58912-102">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="58912-102">IHostAutoEvent Interface</span></span>
<span data-ttu-id="58912-103">提供主機的自動重設事件實作的表示法。</span><span class="sxs-lookup"><span data-stu-id="58912-103">Provides a representation of the host's implementation of an auto-reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="58912-104">方法</span><span class="sxs-lookup"><span data-stu-id="58912-104">Methods</span></span>  
  
|<span data-ttu-id="58912-105">方法</span><span class="sxs-lookup"><span data-stu-id="58912-105">Method</span></span>|<span data-ttu-id="58912-106">說明</span><span class="sxs-lookup"><span data-stu-id="58912-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="58912-107">Set 方法</span><span class="sxs-lookup"><span data-stu-id="58912-107">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-set-method.md)|<span data-ttu-id="58912-108">設定目前`IHostAutoEvent`收到信號狀態的執行個體。</span><span class="sxs-lookup"><span data-stu-id="58912-108">Sets the current `IHostAutoEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="58912-109">Wait 方法</span><span class="sxs-lookup"><span data-stu-id="58912-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-wait-method.md)|<span data-ttu-id="58912-110">造成目前`IHostAutoEvent`等候，直到擁有事件的執行個體或指定的經過時間量。</span><span class="sxs-lookup"><span data-stu-id="58912-110">Causes the current `IHostAutoEvent` instance to wait until the event is owned or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="58912-111">需求</span><span class="sxs-lookup"><span data-stu-id="58912-111">Requirements</span></span>  
 <span data-ttu-id="58912-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="58912-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58912-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="58912-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="58912-114">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="58912-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="58912-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58912-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58912-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58912-116">See Also</span></span>  
 [<span data-ttu-id="58912-117">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="58912-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="58912-118">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="58912-118">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="58912-119">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="58912-119">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="58912-120">裝載介面</span><span class="sxs-lookup"><span data-stu-id="58912-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
