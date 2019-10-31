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
ms.openlocfilehash: 18dfee606f3d41229aa58a5b4bb9380b87c4efa5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121386"
---
# <a name="ihosttask-interface"></a><span data-ttu-id="fb02a-102">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="fb02a-102">IHostTask Interface</span></span>
<span data-ttu-id="fb02a-103">提供可讓 common language runtime （CLR）與主機通訊的方法，以管理工作。</span><span class="sxs-lookup"><span data-stu-id="fb02a-103">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fb02a-104">方法</span><span class="sxs-lookup"><span data-stu-id="fb02a-104">Methods</span></span>  
  
|<span data-ttu-id="fb02a-105">方法</span><span class="sxs-lookup"><span data-stu-id="fb02a-105">Method</span></span>|<span data-ttu-id="fb02a-106">描述</span><span class="sxs-lookup"><span data-stu-id="fb02a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fb02a-107">Alert 方法</span><span class="sxs-lookup"><span data-stu-id="fb02a-107">Alert Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|<span data-ttu-id="fb02a-108">要求主機喚醒目前 `IHostTask` 實例所代表的工作，讓工作可以中止。</span><span class="sxs-lookup"><span data-stu-id="fb02a-108">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="fb02a-109">GetPriority 方法</span><span class="sxs-lookup"><span data-stu-id="fb02a-109">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|<span data-ttu-id="fb02a-110">取得目前 `IHostTask` 實例所表示之工作的執行緒優先權層級。</span><span class="sxs-lookup"><span data-stu-id="fb02a-110">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="fb02a-111">Join 方法</span><span class="sxs-lookup"><span data-stu-id="fb02a-111">Join Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|<span data-ttu-id="fb02a-112">封鎖呼叫工作，直到目前的 `IHostTask` 實例所表示的工作完成、已超過指定的時間間隔，或呼叫[IHostTask：： Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)為止。</span><span class="sxs-lookup"><span data-stu-id="fb02a-112">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="fb02a-113">SetCLRTask 方法</span><span class="sxs-lookup"><span data-stu-id="fb02a-113">SetCLRTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|<span data-ttu-id="fb02a-114">將[ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)實例與目前的 `IHostTask` 實例產生關聯。</span><span class="sxs-lookup"><span data-stu-id="fb02a-114">Associates an [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="fb02a-115">SetPriority 方法</span><span class="sxs-lookup"><span data-stu-id="fb02a-115">SetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|<span data-ttu-id="fb02a-116">要求主機針對目前 `IHostTask` 實例所表示的工作，調整執行緒優先順序層級。</span><span class="sxs-lookup"><span data-stu-id="fb02a-116">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="fb02a-117">Start 方法</span><span class="sxs-lookup"><span data-stu-id="fb02a-117">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|<span data-ttu-id="fb02a-118">要求主機將目前 `IHostTask` 實例所代表的工作從暫停狀態移至即時狀態，在其中可執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="fb02a-118">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb02a-119">備註</span><span class="sxs-lookup"><span data-stu-id="fb02a-119">Remarks</span></span>  
 <span data-ttu-id="fb02a-120">CLR 會呼叫 `IHostTask` 所定義的方法來啟動工作、設定其執行緒優先順序層級等等。</span><span class="sxs-lookup"><span data-stu-id="fb02a-120">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb02a-121">需求</span><span class="sxs-lookup"><span data-stu-id="fb02a-121">Requirements</span></span>  
 <span data-ttu-id="fb02a-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fb02a-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb02a-123">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="fb02a-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fb02a-124">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fb02a-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fb02a-125">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb02a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb02a-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="fb02a-126">See also</span></span>

- [<span data-ttu-id="fb02a-127">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="fb02a-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="fb02a-128">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="fb02a-128">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="fb02a-129">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="fb02a-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="fb02a-130">裝載介面</span><span class="sxs-lookup"><span data-stu-id="fb02a-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
