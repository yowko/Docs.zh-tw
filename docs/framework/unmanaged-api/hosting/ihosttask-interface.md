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
ms.openlocfilehash: 1b7209a36f8e9d6f02bd4cc1882adeef8af30c3d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503914"
---
# <a name="ihosttask-interface"></a><span data-ttu-id="e1c1f-102">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="e1c1f-102">IHostTask Interface</span></span>
<span data-ttu-id="e1c1f-103">提供可讓 common language runtime （CLR）與主機通訊的方法，以管理工作。</span><span class="sxs-lookup"><span data-stu-id="e1c1f-103">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e1c1f-104">方法</span><span class="sxs-lookup"><span data-stu-id="e1c1f-104">Methods</span></span>  
  
|<span data-ttu-id="e1c1f-105">方法</span><span class="sxs-lookup"><span data-stu-id="e1c1f-105">Method</span></span>|<span data-ttu-id="e1c1f-106">描述</span><span class="sxs-lookup"><span data-stu-id="e1c1f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e1c1f-107">Alert 方法</span><span class="sxs-lookup"><span data-stu-id="e1c1f-107">Alert Method</span></span>](ihosttask-alert-method.md)|<span data-ttu-id="e1c1f-108">要求主機喚醒目前實例所代表的工作 `IHostTask` ，讓工作可以中止。</span><span class="sxs-lookup"><span data-stu-id="e1c1f-108">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="e1c1f-109">GetPriority 方法</span><span class="sxs-lookup"><span data-stu-id="e1c1f-109">GetPriority Method</span></span>](ihosttask-getpriority-method.md)|<span data-ttu-id="e1c1f-110">取得目前實例所代表之工作的執行緒優先權層級 `IHostTask` 。</span><span class="sxs-lookup"><span data-stu-id="e1c1f-110">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="e1c1f-111">Join 方法</span><span class="sxs-lookup"><span data-stu-id="e1c1f-111">Join Method</span></span>](ihosttask-join-method.md)|<span data-ttu-id="e1c1f-112">封鎖呼叫工作，直到目前實例所代表的工作 `IHostTask` 完成、已超過指定的時間間隔，或呼叫[IHostTask：： Alert](ihosttask-alert-method.md)為止。</span><span class="sxs-lookup"><span data-stu-id="e1c1f-112">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="e1c1f-113">SetCLRTask 方法</span><span class="sxs-lookup"><span data-stu-id="e1c1f-113">SetCLRTask Method</span></span>](ihosttask-setclrtask-method.md)|<span data-ttu-id="e1c1f-114">將[ICLRTask 介面](iclrtask-interface.md)實例與目前的實例產生關聯 `IHostTask` 。</span><span class="sxs-lookup"><span data-stu-id="e1c1f-114">Associates an [ICLRTask Interface](iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="e1c1f-115">SetPriority 方法</span><span class="sxs-lookup"><span data-stu-id="e1c1f-115">SetPriority Method</span></span>](ihosttask-setpriority-method.md)|<span data-ttu-id="e1c1f-116">要求主機調整目前實例所代表之工作的執行緒優先權層級 `IHostTask` 。</span><span class="sxs-lookup"><span data-stu-id="e1c1f-116">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="e1c1f-117">Start 方法</span><span class="sxs-lookup"><span data-stu-id="e1c1f-117">Start Method</span></span>](ihosttask-start-method.md)|<span data-ttu-id="e1c1f-118">要求主機將目前實例所代表的工作 `IHostTask` 從暫停狀態移動到即時狀態，在此情況下可以執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="e1c1f-118">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1c1f-119">備註</span><span class="sxs-lookup"><span data-stu-id="e1c1f-119">Remarks</span></span>  
 <span data-ttu-id="e1c1f-120">CLR 會呼叫所定義的方法 `IHostTask` 來啟動工作、設定其執行緒優先順序層級等等。</span><span class="sxs-lookup"><span data-stu-id="e1c1f-120">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1c1f-121">規格需求</span><span class="sxs-lookup"><span data-stu-id="e1c1f-121">Requirements</span></span>  
 <span data-ttu-id="e1c1f-122">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e1c1f-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1c1f-123">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="e1c1f-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e1c1f-124">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e1c1f-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e1c1f-125">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1c1f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1c1f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1c1f-126">See also</span></span>

- [<span data-ttu-id="e1c1f-127">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="e1c1f-127">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="e1c1f-128">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="e1c1f-128">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="e1c1f-129">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="e1c1f-129">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="e1c1f-130">裝載介面</span><span class="sxs-lookup"><span data-stu-id="e1c1f-130">Hosting Interfaces</span></span>](hosting-interfaces.md)
