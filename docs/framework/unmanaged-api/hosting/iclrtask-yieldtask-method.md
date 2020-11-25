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
ms.openlocfilehash: 7b9b47daa96ffcb1f66b462ff8e227250c5a81ca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720272"
---
# <a name="iclrtaskyieldtask-method"></a><span data-ttu-id="67b1b-102">ICLRTask::YieldTask 方法</span><span class="sxs-lookup"><span data-stu-id="67b1b-102">ICLRTask::YieldTask Method</span></span>

<span data-ttu-id="67b1b-103">要求 common language runtime (CLR) 將目前 [ICLRTask](iclrtask-interface.md) 實例所代表的工作放在旁邊，並讓處理器時間可供其他工作使用。</span><span class="sxs-lookup"><span data-stu-id="67b1b-103">Requests that the common language runtime (CLR) put aside the task that the current [ICLRTask](iclrtask-interface.md) instance represents, and make the processor time available to other tasks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67b1b-104">語法</span><span class="sxs-lookup"><span data-stu-id="67b1b-104">Syntax</span></span>  
  
```cpp  
HRESULT YieldTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="67b1b-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="67b1b-105">Return Value</span></span>  
  
|<span data-ttu-id="67b1b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="67b1b-106">HRESULT</span></span>|<span data-ttu-id="67b1b-107">描述</span><span class="sxs-lookup"><span data-stu-id="67b1b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="67b1b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="67b1b-108">S_OK</span></span>|<span data-ttu-id="67b1b-109">`YieldTask` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="67b1b-109">`YieldTask` returned successfully.</span></span>|  
|<span data-ttu-id="67b1b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="67b1b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="67b1b-111">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="67b1b-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="67b1b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="67b1b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="67b1b-113">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="67b1b-113">The call timed out.</span></span>|  
|<span data-ttu-id="67b1b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="67b1b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="67b1b-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="67b1b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="67b1b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="67b1b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="67b1b-117">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="67b1b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="67b1b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="67b1b-118">E_FAIL</span></span>|<span data-ttu-id="67b1b-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="67b1b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="67b1b-120">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="67b1b-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="67b1b-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="67b1b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67b1b-122">備註</span><span class="sxs-lookup"><span data-stu-id="67b1b-122">Remarks</span></span>  

 <span data-ttu-id="67b1b-123">主機呼叫 `YieldTask` ，以針對其他工作或進程要求處理器資源。</span><span class="sxs-lookup"><span data-stu-id="67b1b-123">A host calls `YieldTask` to request processor resources for other tasks or processes.</span></span> <span data-ttu-id="67b1b-124">這個方法主要是用來允許長時間執行的程式碼，以提供 CPU 時間。</span><span class="sxs-lookup"><span data-stu-id="67b1b-124">This method is primarily intended to allow long-running code to give up CPU time.</span></span> <span data-ttu-id="67b1b-125">執行時間會嘗試將目前實例所代表的工作放 `ICLRTask` 在可產生處理時間的狀態中，但不保證成功。</span><span class="sxs-lookup"><span data-stu-id="67b1b-125">The runtime attempts to put the task that the current `ICLRTask` instance represents in a state where it can yield processing time, but makes no guarantee of success.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67b1b-126">需求</span><span class="sxs-lookup"><span data-stu-id="67b1b-126">Requirements</span></span>  

 <span data-ttu-id="67b1b-127">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="67b1b-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67b1b-128">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="67b1b-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="67b1b-129">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="67b1b-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="67b1b-130">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67b1b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67b1b-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67b1b-131">See also</span></span>

- [<span data-ttu-id="67b1b-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="67b1b-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="67b1b-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="67b1b-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="67b1b-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="67b1b-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="67b1b-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="67b1b-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
