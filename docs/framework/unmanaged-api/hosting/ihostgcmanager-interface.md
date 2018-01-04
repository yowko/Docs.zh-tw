---
title: "IHostGCManager 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostGCManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostGCManager
helpviewer_keywords: IHostGCManager interface [.NET Framework hosting]
ms.assetid: 820330a4-244c-4f67-ab5e-f24b0b3c2080
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7452f49df6970bf2ca49781f6a38874186bec64f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="f6180-102">IHostGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="f6180-102">IHostGCManager Interface</span></span>
<span data-ttu-id="f6180-103">提供方法，以通知主機在藉由 common language runtime (CLR) 記憶體回收機制中的事件。</span><span class="sxs-lookup"><span data-stu-id="f6180-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="f6180-104">成員</span><span class="sxs-lookup"><span data-stu-id="f6180-104">Members</span></span>  
  
|<span data-ttu-id="f6180-105">成員</span><span class="sxs-lookup"><span data-stu-id="f6180-105">Member</span></span>|<span data-ttu-id="f6180-106">描述</span><span class="sxs-lookup"><span data-stu-id="f6180-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f6180-107">SuspensionEnding 方法</span><span class="sxs-lookup"><span data-stu-id="f6180-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="f6180-108">通知主機在 CLR 正在繼續執行的工作已暫止記憶體回收的執行緒上執行。</span><span class="sxs-lookup"><span data-stu-id="f6180-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="f6180-109">SuspensionStarting 方法</span><span class="sxs-lookup"><span data-stu-id="f6180-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="f6180-110">通知主機 CLR 暫停執行的工作，以執行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="f6180-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="f6180-111">ThreadIsBlockingForSuspension 方法</span><span class="sxs-lookup"><span data-stu-id="f6180-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="f6180-112">通知主機，從中進行方法呼叫的執行緒即將封鎖記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="f6180-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f6180-113">需求</span><span class="sxs-lookup"><span data-stu-id="f6180-113">Requirements</span></span>  
 <span data-ttu-id="f6180-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f6180-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6180-115">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f6180-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f6180-116">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f6180-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6180-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6180-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6180-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="f6180-118">See Also</span></span>  
 [<span data-ttu-id="f6180-119">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="f6180-119">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="f6180-120">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="f6180-120">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="f6180-121">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="f6180-121">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="f6180-122">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="f6180-122">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="f6180-123">裝載介面</span><span class="sxs-lookup"><span data-stu-id="f6180-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
