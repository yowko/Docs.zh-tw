---
title: ICLRTask::SwitchOut 方法
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchOut
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchOut
helpviewer_keywords:
- ICLRTask::SwitchOut method [.NET Framework hosting]
- SwitchOut method [.NET Framework hosting]
ms.assetid: b6fb168c-b24b-4ecf-a390-2b5ba3317ae6
topic_type:
- apiref
ms.openlocfilehash: 1b27983b3f10eba225442dcd2f5df02062e53ed4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720265"
---
# <a name="iclrtaskswitchout-method"></a><span data-ttu-id="d6921-102">ICLRTask::SwitchOut 方法</span><span class="sxs-lookup"><span data-stu-id="d6921-102">ICLRTask::SwitchOut Method</span></span>

<span data-ttu-id="d6921-103">通知 common language runtime (CLR) 目前 [ICLRTask](iclrtask-interface.md) 實例所代表的工作不再處於可操作的狀態。</span><span class="sxs-lookup"><span data-stu-id="d6921-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](iclrtask-interface.md) instance is no longer in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6921-104">語法</span><span class="sxs-lookup"><span data-stu-id="d6921-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchOut ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d6921-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="d6921-105">Return Value</span></span>  
  
|<span data-ttu-id="d6921-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d6921-106">HRESULT</span></span>|<span data-ttu-id="d6921-107">描述</span><span class="sxs-lookup"><span data-stu-id="d6921-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d6921-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="d6921-108">S_OK</span></span>|<span data-ttu-id="d6921-109">`SwitchOut` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="d6921-109">`SwitchOut` returned successfully.</span></span>|  
|<span data-ttu-id="d6921-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d6921-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d6921-111">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="d6921-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d6921-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d6921-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d6921-113">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="d6921-113">The call timed out.</span></span>|  
|<span data-ttu-id="d6921-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d6921-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d6921-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d6921-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d6921-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d6921-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d6921-117">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="d6921-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d6921-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d6921-118">E_FAIL</span></span>|<span data-ttu-id="d6921-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="d6921-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d6921-120">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="d6921-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d6921-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d6921-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6921-122">備註</span><span class="sxs-lookup"><span data-stu-id="d6921-122">Remarks</span></span>  

 <span data-ttu-id="d6921-123">主機呼叫 `SwitchOut` 來通知 CLR，它已暫時停止執行目前實例所代表的工作 `ICLRTask` ，而且會重新排程工作。</span><span class="sxs-lookup"><span data-stu-id="d6921-123">A host calls `SwitchOut` to inform the CLR that it has temporarily stopped executing the task that the current `ICLRTask` instance represents, and will reschedule the task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6921-124">需求</span><span class="sxs-lookup"><span data-stu-id="d6921-124">Requirements</span></span>  

 <span data-ttu-id="d6921-125">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d6921-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6921-126">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d6921-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d6921-127">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="d6921-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6921-128">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6921-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6921-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6921-129">See also</span></span>

- [<span data-ttu-id="d6921-130">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="d6921-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="d6921-131">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="d6921-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="d6921-132">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="d6921-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="d6921-133">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="d6921-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
