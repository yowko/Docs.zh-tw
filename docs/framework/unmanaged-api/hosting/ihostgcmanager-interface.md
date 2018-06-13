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
ms.openlocfilehash: c4eac8abede82915386abc19c4c8389932451df4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440372"
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="9ebb2-102">IHostGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="9ebb2-102">IHostGCManager Interface</span></span>
<span data-ttu-id="9ebb2-103">提供方法，以通知主機在藉由 common language runtime (CLR) 記憶體回收機制中的事件。</span><span class="sxs-lookup"><span data-stu-id="9ebb2-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="9ebb2-104">成員</span><span class="sxs-lookup"><span data-stu-id="9ebb2-104">Members</span></span>  
  
|<span data-ttu-id="9ebb2-105">成員</span><span class="sxs-lookup"><span data-stu-id="9ebb2-105">Member</span></span>|<span data-ttu-id="9ebb2-106">描述</span><span class="sxs-lookup"><span data-stu-id="9ebb2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9ebb2-107">SuspensionEnding 方法</span><span class="sxs-lookup"><span data-stu-id="9ebb2-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="9ebb2-108">通知主機在 CLR 正在繼續執行的工作已暫止記憶體回收的執行緒上執行。</span><span class="sxs-lookup"><span data-stu-id="9ebb2-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="9ebb2-109">SuspensionStarting 方法</span><span class="sxs-lookup"><span data-stu-id="9ebb2-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="9ebb2-110">通知主機 CLR 暫停執行的工作，以執行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="9ebb2-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="9ebb2-111">ThreadIsBlockingForSuspension 方法</span><span class="sxs-lookup"><span data-stu-id="9ebb2-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="9ebb2-112">通知主機，從中進行方法呼叫的執行緒即將封鎖記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="9ebb2-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9ebb2-113">需求</span><span class="sxs-lookup"><span data-stu-id="9ebb2-113">Requirements</span></span>  
 <span data-ttu-id="9ebb2-114">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9ebb2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ebb2-115">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9ebb2-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9ebb2-116">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9ebb2-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ebb2-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ebb2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ebb2-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ebb2-118">See Also</span></span>  
 [<span data-ttu-id="9ebb2-119">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="9ebb2-119">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="9ebb2-120">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="9ebb2-120">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="9ebb2-121">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="9ebb2-121">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="9ebb2-122">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="9ebb2-122">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="9ebb2-123">裝載介面</span><span class="sxs-lookup"><span data-stu-id="9ebb2-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
