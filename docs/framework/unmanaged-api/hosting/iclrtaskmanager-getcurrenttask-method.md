---
title: ICLRTaskManager::GetCurrentTask 方法
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: c0b82a9f-edc6-4878-9c81-48de53c02142
topic_type:
- apiref
ms.openlocfilehash: af855e3ba47dc329a4fb722c3e13d5f1816beba4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723268"
---
# <a name="iclrtaskmanagergetcurrenttask-method"></a><span data-ttu-id="08189-102">ICLRTaskManager::GetCurrentTask 方法</span><span class="sxs-lookup"><span data-stu-id="08189-102">ICLRTaskManager::GetCurrentTask Method</span></span>

<span data-ttu-id="08189-103">取得目前在方法呼叫來源作業系統執行緒上執行的 [ICLRTask](iclrtask-interface.md) 實例。</span><span class="sxs-lookup"><span data-stu-id="08189-103">Gets the [ICLRTask](iclrtask-interface.md) instance that is currently running on the operating system thread from which the method call originated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08189-104">語法</span><span class="sxs-lookup"><span data-stu-id="08189-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTask (  
    [out] ICLRTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08189-105">參數</span><span class="sxs-lookup"><span data-stu-id="08189-105">Parameters</span></span>  

 `ppTask`  
 <span data-ttu-id="08189-106">擴展 `ICLRTask` 目前在呼叫來源的作業系統執行緒上執行之實例位址的指標，如果這個執行緒上目前未執行任何工作，則為 null。</span><span class="sxs-lookup"><span data-stu-id="08189-106">[out] A pointer to the address of an `ICLRTask` instance that is currently executing on the operating system thread from which the call originated, or null if no task is currently executing on this thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08189-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="08189-107">Return Value</span></span>  
  
|<span data-ttu-id="08189-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="08189-108">HRESULT</span></span>|<span data-ttu-id="08189-109">描述</span><span class="sxs-lookup"><span data-stu-id="08189-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="08189-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="08189-110">S_OK</span></span>|<span data-ttu-id="08189-111">此方法已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="08189-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="08189-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="08189-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="08189-113">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="08189-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="08189-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="08189-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="08189-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="08189-115">The call timed out.</span></span>|  
|<span data-ttu-id="08189-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="08189-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="08189-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="08189-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="08189-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="08189-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="08189-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="08189-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="08189-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="08189-120">E_FAIL</span></span>|<span data-ttu-id="08189-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="08189-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="08189-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="08189-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="08189-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="08189-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08189-124">備註</span><span class="sxs-lookup"><span data-stu-id="08189-124">Remarks</span></span>  

 <span data-ttu-id="08189-125">`ICLRTask`參數所指向的實例， `ppTask` 代表 CLR 目前正在執行的工作。</span><span class="sxs-lookup"><span data-stu-id="08189-125">The `ICLRTask` instance that the `ppTask` parameter points to represents the currently executing task for the CLR.</span></span> <span data-ttu-id="08189-126">`ICLRTask`實例與代表主機工作的對應[IHostTask](ihosttask-interface.md)實例相關聯。</span><span class="sxs-lookup"><span data-stu-id="08189-126">The `ICLRTask` instance is associated with a corresponding [IHostTask](ihosttask-interface.md) instance that represents the task for the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08189-127">需求</span><span class="sxs-lookup"><span data-stu-id="08189-127">Requirements</span></span>  

 <span data-ttu-id="08189-128">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="08189-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08189-129">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="08189-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="08189-130">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="08189-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08189-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08189-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08189-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08189-132">See also</span></span>

- [<span data-ttu-id="08189-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="08189-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="08189-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="08189-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="08189-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="08189-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="08189-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="08189-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
