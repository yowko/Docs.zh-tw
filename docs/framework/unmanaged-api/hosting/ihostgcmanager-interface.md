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
ms.openlocfilehash: 428e4cf8997713b08e40d9376c34ae5eee8cfa32
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804847"
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="5b032-102">IHostGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="5b032-102">IHostGCManager Interface</span></span>
<span data-ttu-id="5b032-103">提供方法，以通知 common language runtime （CLR）所實作為垃圾收集機制的事件主機。</span><span class="sxs-lookup"><span data-stu-id="5b032-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="5b032-104">成員</span><span class="sxs-lookup"><span data-stu-id="5b032-104">Members</span></span>  
  
|<span data-ttu-id="5b032-105">成員</span><span class="sxs-lookup"><span data-stu-id="5b032-105">Member</span></span>|<span data-ttu-id="5b032-106">描述</span><span class="sxs-lookup"><span data-stu-id="5b032-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5b032-107">SuspensionEnding 方法</span><span class="sxs-lookup"><span data-stu-id="5b032-107">SuspensionEnding Method</span></span>](ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="5b032-108">通知主機 CLR 正在繼續執行已暫止垃圾收集的執行緒上的工作。</span><span class="sxs-lookup"><span data-stu-id="5b032-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="5b032-109">SuspensionStarting 方法</span><span class="sxs-lookup"><span data-stu-id="5b032-109">SuspensionStarting Method</span></span>](ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="5b032-110">通知主機 CLR 正在暫停執行工作，以執行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="5b032-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="5b032-111">ThreadIsBlockingForSuspension 方法</span><span class="sxs-lookup"><span data-stu-id="5b032-111">ThreadIsBlockingForSuspension Method</span></span>](ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="5b032-112">通知主機，方法呼叫的來源執行緒即將封鎖進行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="5b032-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5b032-113">規格需求</span><span class="sxs-lookup"><span data-stu-id="5b032-113">Requirements</span></span>  
 <span data-ttu-id="5b032-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5b032-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b032-115">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="5b032-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5b032-116">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5b032-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5b032-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b032-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b032-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b032-118">See also</span></span>

- [<span data-ttu-id="5b032-119">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="5b032-119">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="5b032-120">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="5b032-120">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="5b032-121">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="5b032-121">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="5b032-122">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="5b032-122">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="5b032-123">裝載介面</span><span class="sxs-lookup"><span data-stu-id="5b032-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
