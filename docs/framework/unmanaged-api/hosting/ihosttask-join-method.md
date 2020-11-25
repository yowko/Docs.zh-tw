---
title: IHostTask::Join 方法
ms.date: 03/30/2017
api_name:
- IHostTask.Join
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Join
helpviewer_keywords:
- IHostTask::Join method [.NET Framework hosting]
- Join method, IHostTask interface [.NET Framework hosting]
ms.assetid: 2cffcc52-19e0-4ced-a440-fc7375078ac9
topic_type:
- apiref
ms.openlocfilehash: 37156b03b184d06e0c7b03d7d7a9a018793bbb98
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721630"
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="f5f3f-102">IHostTask::Join 方法</span><span class="sxs-lookup"><span data-stu-id="f5f3f-102">IHostTask::Join Method</span></span>

<span data-ttu-id="f5f3f-103">封鎖呼叫工作，直到目前 [IHostTask](ihosttask-interface.md) 實例所代表的工作完成、已超過指定的時間間隔，或呼叫 [IHostTask：： Alert](ihosttask-alert-method.md) 為止。</span><span class="sxs-lookup"><span data-stu-id="f5f3f-103">Blocks the calling task until the task represented by the current [IHostTask](ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5f3f-104">語法</span><span class="sxs-lookup"><span data-stu-id="f5f3f-104">Syntax</span></span>  
  
```cpp  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5f3f-105">參數</span><span class="sxs-lookup"><span data-stu-id="f5f3f-105">Parameters</span></span>  

 `milliseconds`  
 <span data-ttu-id="f5f3f-106">在等候工作終止的時間間隔（以毫秒為單位）。</span><span class="sxs-lookup"><span data-stu-id="f5f3f-106">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="f5f3f-107">如果此間隔在工作終止之前結束，則呼叫的工作會解除封鎖。</span><span class="sxs-lookup"><span data-stu-id="f5f3f-107">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="f5f3f-108">在其中一個 [WAIT_OPTION](wait-option-enumeration.md) 值。</span><span class="sxs-lookup"><span data-stu-id="f5f3f-108">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values.</span></span> <span data-ttu-id="f5f3f-109">如果在 `Alert` 經過之前呼叫，WAIT_ALERTABLE 的值會指示主機喚醒工作 `milliseconds` 。</span><span class="sxs-lookup"><span data-stu-id="f5f3f-109">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5f3f-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="f5f3f-110">Return Value</span></span>  
  
|<span data-ttu-id="f5f3f-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f5f3f-111">HRESULT</span></span>|<span data-ttu-id="f5f3f-112">描述</span><span class="sxs-lookup"><span data-stu-id="f5f3f-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f5f3f-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="f5f3f-113">S_OK</span></span>|<span data-ttu-id="f5f3f-114">`Join` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="f5f3f-114">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="f5f3f-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f5f3f-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f5f3f-116">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="f5f3f-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f5f3f-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f5f3f-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f5f3f-118">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="f5f3f-118">The call timed out.</span></span>|  
|<span data-ttu-id="f5f3f-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f5f3f-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f5f3f-120">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="f5f3f-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f5f3f-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f5f3f-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f5f3f-122">當封鎖的執行緒或光纖正在等候時，或目前的 `IHostTask` 實例未與工作相關聯時，就會取消事件。</span><span class="sxs-lookup"><span data-stu-id="f5f3f-122">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="f5f3f-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f5f3f-123">E_FAIL</span></span>|<span data-ttu-id="f5f3f-124">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="f5f3f-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f5f3f-125">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="f5f3f-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f5f3f-126">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="f5f3f-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f5f3f-127">需求</span><span class="sxs-lookup"><span data-stu-id="f5f3f-127">Requirements</span></span>  

 <span data-ttu-id="f5f3f-128">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f5f3f-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5f3f-129">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f5f3f-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5f3f-130">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="f5f3f-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5f3f-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5f3f-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5f3f-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5f3f-132">See also</span></span>

- [<span data-ttu-id="f5f3f-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="f5f3f-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="f5f3f-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="f5f3f-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="f5f3f-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="f5f3f-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="f5f3f-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="f5f3f-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="f5f3f-137">WAIT_OPTION 列舉</span><span class="sxs-lookup"><span data-stu-id="f5f3f-137">WAIT_OPTION Enumeration</span></span>](wait-option-enumeration.md)
