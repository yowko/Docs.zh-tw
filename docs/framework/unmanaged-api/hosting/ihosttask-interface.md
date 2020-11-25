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
ms.openlocfilehash: 10efe853c9a7ad7676058bc01b07063c557623d8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699218"
---
# <a name="ihosttask-interface"></a><span data-ttu-id="46430-102">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="46430-102">IHostTask Interface</span></span>

<span data-ttu-id="46430-103">提供的方法，可讓 common language runtime (CLR) 與主機通訊，以管理工作。</span><span class="sxs-lookup"><span data-stu-id="46430-103">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="46430-104">方法</span><span class="sxs-lookup"><span data-stu-id="46430-104">Methods</span></span>  
  
|<span data-ttu-id="46430-105">方法</span><span class="sxs-lookup"><span data-stu-id="46430-105">Method</span></span>|<span data-ttu-id="46430-106">描述</span><span class="sxs-lookup"><span data-stu-id="46430-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="46430-107">Alert 方法</span><span class="sxs-lookup"><span data-stu-id="46430-107">Alert Method</span></span>](ihosttask-alert-method.md)|<span data-ttu-id="46430-108">要求主機喚醒目前實例所代表的工作 `IHostTask` ，讓工作可以中止。</span><span class="sxs-lookup"><span data-stu-id="46430-108">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="46430-109">GetPriority 方法</span><span class="sxs-lookup"><span data-stu-id="46430-109">GetPriority Method</span></span>](ihosttask-getpriority-method.md)|<span data-ttu-id="46430-110">取得目前實例所代表之工作的執行緒優先權層級 `IHostTask` 。</span><span class="sxs-lookup"><span data-stu-id="46430-110">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="46430-111">Join 方法</span><span class="sxs-lookup"><span data-stu-id="46430-111">Join Method</span></span>](ihosttask-join-method.md)|<span data-ttu-id="46430-112">封鎖呼叫工作，直到目前實例所代表的工作 `IHostTask` 完成、已超過指定的時間間隔，或呼叫 [IHostTask：： Alert](ihosttask-alert-method.md) 為止。</span><span class="sxs-lookup"><span data-stu-id="46430-112">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="46430-113">SetCLRTask 方法</span><span class="sxs-lookup"><span data-stu-id="46430-113">SetCLRTask Method</span></span>](ihosttask-setclrtask-method.md)|<span data-ttu-id="46430-114">將 [ICLRTask 介面](iclrtask-interface.md) 實例與目前的實例產生關聯 `IHostTask` 。</span><span class="sxs-lookup"><span data-stu-id="46430-114">Associates an [ICLRTask Interface](iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="46430-115">SetPriority 方法</span><span class="sxs-lookup"><span data-stu-id="46430-115">SetPriority Method</span></span>](ihosttask-setpriority-method.md)|<span data-ttu-id="46430-116">要求主機調整目前實例所代表之工作的執行緒優先權層級 `IHostTask` 。</span><span class="sxs-lookup"><span data-stu-id="46430-116">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="46430-117">Start 方法</span><span class="sxs-lookup"><span data-stu-id="46430-117">Start Method</span></span>](ihosttask-start-method.md)|<span data-ttu-id="46430-118">要求主機將目前實例所代表的工作 `IHostTask` 從暫停狀態移至即時狀態，其中可以執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="46430-118">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46430-119">備註</span><span class="sxs-lookup"><span data-stu-id="46430-119">Remarks</span></span>  

 <span data-ttu-id="46430-120">CLR 會呼叫所定義的方法 `IHostTask` 來啟動工作、設定其執行緒優先權層級等等。</span><span class="sxs-lookup"><span data-stu-id="46430-120">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46430-121">需求</span><span class="sxs-lookup"><span data-stu-id="46430-121">Requirements</span></span>  

 <span data-ttu-id="46430-122">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="46430-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46430-123">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="46430-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="46430-124">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="46430-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="46430-125">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46430-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46430-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46430-126">See also</span></span>

- [<span data-ttu-id="46430-127">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="46430-127">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="46430-128">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="46430-128">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="46430-129">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="46430-129">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="46430-130">裝載介面</span><span class="sxs-lookup"><span data-stu-id="46430-130">Hosting Interfaces</span></span>](hosting-interfaces.md)
