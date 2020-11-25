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
ms.openlocfilehash: eb7e52b5237d4341c27b8c167249dc2614168679
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729515"
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="20056-102">IHostGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="20056-102">IHostGCManager Interface</span></span>

<span data-ttu-id="20056-103">提供方法，在 common language runtime (CLR) 所執行的垃圾收集機制中，通知主機事件。</span><span class="sxs-lookup"><span data-stu-id="20056-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="20056-104">成員</span><span class="sxs-lookup"><span data-stu-id="20056-104">Members</span></span>  
  
|<span data-ttu-id="20056-105">member</span><span class="sxs-lookup"><span data-stu-id="20056-105">Member</span></span>|<span data-ttu-id="20056-106">描述</span><span class="sxs-lookup"><span data-stu-id="20056-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="20056-107">SuspensionEnding 方法</span><span class="sxs-lookup"><span data-stu-id="20056-107">SuspensionEnding Method</span></span>](ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="20056-108">通知主機 CLR 正在暫停執行垃圾收集的執行緒上執行工作。</span><span class="sxs-lookup"><span data-stu-id="20056-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="20056-109">SuspensionStarting 方法</span><span class="sxs-lookup"><span data-stu-id="20056-109">SuspensionStarting Method</span></span>](ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="20056-110">通知主機 CLR 正在暫停執行工作，以執行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="20056-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="20056-111">ThreadIsBlockingForSuspension 方法</span><span class="sxs-lookup"><span data-stu-id="20056-111">ThreadIsBlockingForSuspension Method</span></span>](ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="20056-112">通知主機發出方法呼叫的執行緒，即將封鎖垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="20056-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="20056-113">需求</span><span class="sxs-lookup"><span data-stu-id="20056-113">Requirements</span></span>  

 <span data-ttu-id="20056-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="20056-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20056-115">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="20056-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="20056-116">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="20056-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20056-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20056-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20056-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20056-118">See also</span></span>

- [<span data-ttu-id="20056-119">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="20056-119">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="20056-120">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="20056-120">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="20056-121">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="20056-121">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="20056-122">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="20056-122">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="20056-123">裝載介面</span><span class="sxs-lookup"><span data-stu-id="20056-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
