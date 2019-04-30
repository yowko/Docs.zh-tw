---
title: IHostTask 介面
ms.date: 03/30/2017
api_name:
- IHostTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask
helpviewer_keywords:
- IHostTask interface [.NET Framework hosting]
ms.assetid: a71dbbd5-64b8-47eb-9f03-8e8c85fbe2bc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb15da31d91565d49df83099045f742866eebcaa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992832"
---
# <a name="ihosttask-interface"></a><span data-ttu-id="e1c70-102">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="e1c70-102">IHostTask Interface</span></span>
<span data-ttu-id="e1c70-103">提供方法，可讓 common language runtime (CLR) 與主應用程式管理工作進行通訊。</span><span class="sxs-lookup"><span data-stu-id="e1c70-103">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e1c70-104">方法</span><span class="sxs-lookup"><span data-stu-id="e1c70-104">Methods</span></span>  
  
|<span data-ttu-id="e1c70-105">方法</span><span class="sxs-lookup"><span data-stu-id="e1c70-105">Method</span></span>|<span data-ttu-id="e1c70-106">描述</span><span class="sxs-lookup"><span data-stu-id="e1c70-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e1c70-107">Alert 方法</span><span class="sxs-lookup"><span data-stu-id="e1c70-107">Alert Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|<span data-ttu-id="e1c70-108">要求主機喚醒表示由目前的工作`IHostTask`執行個體，因此可以中止的工作。</span><span class="sxs-lookup"><span data-stu-id="e1c70-108">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="e1c70-109">GetPriority 方法</span><span class="sxs-lookup"><span data-stu-id="e1c70-109">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|<span data-ttu-id="e1c70-110">取得表示目前的工作的執行緒優先權層級`IHostTask`執行個體。</span><span class="sxs-lookup"><span data-stu-id="e1c70-110">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="e1c70-111">Join 方法</span><span class="sxs-lookup"><span data-stu-id="e1c70-111">Join Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|<span data-ttu-id="e1c70-112">表示由目前的工作之前會封鎖呼叫的工作`IHostTask`執行個體完成後，將指定的時間間隔過去後，或是[ihosttask:: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)呼叫。</span><span class="sxs-lookup"><span data-stu-id="e1c70-112">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="e1c70-113">SetCLRTask 方法</span><span class="sxs-lookup"><span data-stu-id="e1c70-113">SetCLRTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|<span data-ttu-id="e1c70-114">將產生關聯[ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)與目前的執行個體`IHostTask`執行個體。</span><span class="sxs-lookup"><span data-stu-id="e1c70-114">Associates an [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="e1c70-115">SetPriority 方法</span><span class="sxs-lookup"><span data-stu-id="e1c70-115">SetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|<span data-ttu-id="e1c70-116">表示由目前的工作要求主應用程式調整的執行緒優先權層級`IHostTask`執行個體。</span><span class="sxs-lookup"><span data-stu-id="e1c70-116">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="e1c70-117">Start 方法</span><span class="sxs-lookup"><span data-stu-id="e1c70-117">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|<span data-ttu-id="e1c70-118">要求主機移到表示由目前的工作`IHostTask`從暫停狀態的即時狀態，可以在其中執行程式碼的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e1c70-118">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1c70-119">備註</span><span class="sxs-lookup"><span data-stu-id="e1c70-119">Remarks</span></span>  
 <span data-ttu-id="e1c70-120">CLR 會呼叫所定義的方法`IHostTask`啟動工作，設定它的執行緒優先權層級，依此類推。</span><span class="sxs-lookup"><span data-stu-id="e1c70-120">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1c70-121">需求</span><span class="sxs-lookup"><span data-stu-id="e1c70-121">Requirements</span></span>  
 <span data-ttu-id="e1c70-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e1c70-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1c70-123">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e1c70-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e1c70-124">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e1c70-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e1c70-125">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1c70-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1c70-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1c70-126">See also</span></span>

- [<span data-ttu-id="e1c70-127">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="e1c70-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="e1c70-128">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="e1c70-128">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="e1c70-129">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="e1c70-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="e1c70-130">裝載介面</span><span class="sxs-lookup"><span data-stu-id="e1c70-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
