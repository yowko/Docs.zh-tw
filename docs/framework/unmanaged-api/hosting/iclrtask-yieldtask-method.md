---
title: ICLRTask::YieldTask 方法
ms.date: 03/30/2017
api_name:
- ICLRTask.YieldTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::YieldTask
helpviewer_keywords:
- ICLRTask::YieldTask method [.NET Framework hosting]
- YieldTask method [.NET Framework hosting]
ms.assetid: b8eb4095-3a8f-4be3-9446-63e9893dce7d
topic_type:
- apiref
ms.openlocfilehash: 43f2048c8ab85fa7e94f73aad430400ad4c8352f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124586"
---
# <a name="iclrtaskyieldtask-method"></a><span data-ttu-id="2a1d9-102">ICLRTask::YieldTask 方法</span><span class="sxs-lookup"><span data-stu-id="2a1d9-102">ICLRTask::YieldTask Method</span></span>
<span data-ttu-id="2a1d9-103">要求 common language runtime （CLR）放置目前[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)實例所代表的工作，並將處理器時間提供給其他工作使用。</span><span class="sxs-lookup"><span data-stu-id="2a1d9-103">Requests that the common language runtime (CLR) put aside the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents, and make the processor time available to other tasks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a1d9-104">語法</span><span class="sxs-lookup"><span data-stu-id="2a1d9-104">Syntax</span></span>  
  
```cpp  
HRESULT YieldTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2a1d9-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="2a1d9-105">Return Value</span></span>  
  
|<span data-ttu-id="2a1d9-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2a1d9-106">HRESULT</span></span>|<span data-ttu-id="2a1d9-107">描述</span><span class="sxs-lookup"><span data-stu-id="2a1d9-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2a1d9-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="2a1d9-108">S_OK</span></span>|<span data-ttu-id="2a1d9-109">已成功傳回 `YieldTask`。</span><span class="sxs-lookup"><span data-stu-id="2a1d9-109">`YieldTask` returned successfully.</span></span>|  
|<span data-ttu-id="2a1d9-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2a1d9-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2a1d9-111">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="2a1d9-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2a1d9-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2a1d9-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2a1d9-113">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="2a1d9-113">The call timed out.</span></span>|  
|<span data-ttu-id="2a1d9-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2a1d9-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2a1d9-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="2a1d9-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2a1d9-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2a1d9-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2a1d9-117">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="2a1d9-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2a1d9-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2a1d9-118">E_FAIL</span></span>|<span data-ttu-id="2a1d9-119">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="2a1d9-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2a1d9-120">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="2a1d9-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2a1d9-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="2a1d9-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a1d9-122">備註</span><span class="sxs-lookup"><span data-stu-id="2a1d9-122">Remarks</span></span>  
 <span data-ttu-id="2a1d9-123">主機會呼叫 `YieldTask` 來要求其他工作或處理常式的處理器資源。</span><span class="sxs-lookup"><span data-stu-id="2a1d9-123">A host calls `YieldTask` to request processor resources for other tasks or processes.</span></span> <span data-ttu-id="2a1d9-124">這個方法主要是為了讓長時間執行的程式碼放棄 CPU 時間。</span><span class="sxs-lookup"><span data-stu-id="2a1d9-124">This method is primarily intended to allow long-running code to give up CPU time.</span></span> <span data-ttu-id="2a1d9-125">執行時間會嘗試將目前 `ICLRTask` 實例所代表的工作，置於可產生處理時間的狀態中，但不會保證成功。</span><span class="sxs-lookup"><span data-stu-id="2a1d9-125">The runtime attempts to put the task that the current `ICLRTask` instance represents in a state where it can yield processing time, but makes no guarantee of success.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a1d9-126">需求</span><span class="sxs-lookup"><span data-stu-id="2a1d9-126">Requirements</span></span>  
 <span data-ttu-id="2a1d9-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2a1d9-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a1d9-128">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="2a1d9-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2a1d9-129">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2a1d9-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2a1d9-130">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a1d9-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a1d9-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="2a1d9-131">See also</span></span>

- [<span data-ttu-id="2a1d9-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="2a1d9-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="2a1d9-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="2a1d9-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="2a1d9-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="2a1d9-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="2a1d9-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="2a1d9-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
