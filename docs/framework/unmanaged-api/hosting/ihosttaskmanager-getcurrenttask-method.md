---
title: IHostTaskManager::GetCurrentTask 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: f17bca49-90bd-4dee-a5e1-b9a57ea46f85
topic_type:
- apiref
ms.openlocfilehash: 72b7f6e3a5a09bd06e8a7fbb94680ed3ea89b225
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727298"
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="f104d-102">IHostTaskManager::GetCurrentTask 方法</span><span class="sxs-lookup"><span data-stu-id="f104d-102">IHostTaskManager::GetCurrentTask Method</span></span>

<span data-ttu-id="f104d-103">取得執行此呼叫之作業系統執行緒上目前正在執行之工作的介面指標。</span><span class="sxs-lookup"><span data-stu-id="f104d-103">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f104d-104">語法</span><span class="sxs-lookup"><span data-stu-id="f104d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f104d-105">參數</span><span class="sxs-lookup"><span data-stu-id="f104d-105">Parameters</span></span>  

 `pTask`  
 <span data-ttu-id="f104d-106">擴展 [IHostTask](ihosttask-interface.md) 實例位址的指標，代表目前正在執行的工作，如果目前沒有任何工作正在執行，則為 null。</span><span class="sxs-lookup"><span data-stu-id="f104d-106">[out] A pointer to the address of an [IHostTask](ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f104d-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="f104d-107">Return Value</span></span>  
  
|<span data-ttu-id="f104d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f104d-108">HRESULT</span></span>|<span data-ttu-id="f104d-109">描述</span><span class="sxs-lookup"><span data-stu-id="f104d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f104d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f104d-110">S_OK</span></span>|<span data-ttu-id="f104d-111">`GetCurrentTask` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="f104d-111">`GetCurrentTask` returned successfully.</span></span>|  
|<span data-ttu-id="f104d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f104d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f104d-113">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="f104d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f104d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f104d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f104d-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="f104d-115">The call timed out.</span></span>|  
|<span data-ttu-id="f104d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f104d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f104d-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="f104d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f104d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f104d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f104d-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="f104d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f104d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f104d-120">E_FAIL</span></span>|<span data-ttu-id="f104d-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="f104d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f104d-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="f104d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f104d-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="f104d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f104d-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="f104d-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="f104d-125">`GetCurrentTask` 在主機的控制外部的作業系統執行緒上呼叫。</span><span class="sxs-lookup"><span data-stu-id="f104d-125">`GetCurrentTask` was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f104d-126">備註</span><span class="sxs-lookup"><span data-stu-id="f104d-126">Remarks</span></span>  

 <span data-ttu-id="f104d-127">主機也可以將參數設定 `pTask` 為 null，以防止它不是從輸入 CLR 開始的工作。</span><span class="sxs-lookup"><span data-stu-id="f104d-127">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f104d-128">需求</span><span class="sxs-lookup"><span data-stu-id="f104d-128">Requirements</span></span>  

 <span data-ttu-id="f104d-129">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f104d-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f104d-130">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f104d-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f104d-131">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="f104d-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f104d-132">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f104d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f104d-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f104d-133">See also</span></span>

- [<span data-ttu-id="f104d-134">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="f104d-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="f104d-135">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="f104d-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="f104d-136">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="f104d-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="f104d-137">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="f104d-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
