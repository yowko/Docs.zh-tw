---
title: IHostGCManager 介面
ms.date: 03/30/2017
api_name:
- IHostGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager
helpviewer_keywords:
- IHostGCManager interface [.NET Framework hosting]
ms.assetid: 820330a4-244c-4f67-ab5e-f24b0b3c2080
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 238b054d240437df64a83a9c4daad34d4bd5d36a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228872"
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="9e736-102">IHostGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="9e736-102">IHostGCManager Interface</span></span>
<span data-ttu-id="9e736-103">提供方法，以通知主機藉由將 common language runtime (CLR) 記憶體回收機制中的事件。</span><span class="sxs-lookup"><span data-stu-id="9e736-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="9e736-104">成員</span><span class="sxs-lookup"><span data-stu-id="9e736-104">Members</span></span>  
  
|<span data-ttu-id="9e736-105">成員</span><span class="sxs-lookup"><span data-stu-id="9e736-105">Member</span></span>|<span data-ttu-id="9e736-106">描述</span><span class="sxs-lookup"><span data-stu-id="9e736-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9e736-107">SuspensionEnding 方法</span><span class="sxs-lookup"><span data-stu-id="9e736-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="9e736-108">主應用程式，CLR 會繼續已暫止記憶體回收的執行緒上的工作執行。</span><span class="sxs-lookup"><span data-stu-id="9e736-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="9e736-109">SuspensionStarting 方法</span><span class="sxs-lookup"><span data-stu-id="9e736-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="9e736-110">CLR 會暫停執行的工作，以執行記憶體回收通知主機。</span><span class="sxs-lookup"><span data-stu-id="9e736-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="9e736-111">ThreadIsBlockingForSuspension 方法</span><span class="sxs-lookup"><span data-stu-id="9e736-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="9e736-112">主應用程式在進行方法呼叫的執行緒即將封鎖記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="9e736-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9e736-113">需求</span><span class="sxs-lookup"><span data-stu-id="9e736-113">Requirements</span></span>  
 <span data-ttu-id="9e736-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9e736-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e736-115">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9e736-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e736-116">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9e736-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="9e736-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="9e736-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9e736-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e736-118">See also</span></span>

- [<span data-ttu-id="9e736-119">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="9e736-119">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="9e736-120">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="9e736-120">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="9e736-121">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="9e736-121">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="9e736-122">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="9e736-122">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="9e736-123">裝載介面</span><span class="sxs-lookup"><span data-stu-id="9e736-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
