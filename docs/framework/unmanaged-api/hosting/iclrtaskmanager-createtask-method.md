---
title: ICLRTaskManager::CreateTask 方法
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::CreateTask
helpviewer_keywords:
- ICLRTaskManager::CreateTask method [.NET Framework hosting]
- CreateTask method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: eea570d9-2e53-4320-9ea0-eb777bf9dcf3
topic_type:
- apiref
ms.openlocfilehash: c8d18b78cf0185271eae763892610d13f76e42ab
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733993"
---
# <a name="iclrtaskmanagercreatetask-method"></a><span data-ttu-id="28ae2-102">ICLRTaskManager::CreateTask 方法</span><span class="sxs-lookup"><span data-stu-id="28ae2-102">ICLRTaskManager::CreateTask Method</span></span>

<span data-ttu-id="28ae2-103">明確要求 common language runtime (CLR) 建立新的工作。</span><span class="sxs-lookup"><span data-stu-id="28ae2-103">Requests explicitly that the common language runtime (CLR) create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28ae2-104">語法</span><span class="sxs-lookup"><span data-stu-id="28ae2-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28ae2-105">參數</span><span class="sxs-lookup"><span data-stu-id="28ae2-105">Parameters</span></span>  

 `pTask`  
 <span data-ttu-id="28ae2-106">擴展新建立之 [ICLRTask](iclrtask-interface.md)的位址指標，如果無法建立工作，則為 null。</span><span class="sxs-lookup"><span data-stu-id="28ae2-106">[out] A pointer to the address of a newly created [ICLRTask](iclrtask-interface.md), or null, if the task could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28ae2-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="28ae2-107">Return Value</span></span>  
  
|<span data-ttu-id="28ae2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="28ae2-108">HRESULT</span></span>|<span data-ttu-id="28ae2-109">描述</span><span class="sxs-lookup"><span data-stu-id="28ae2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="28ae2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="28ae2-110">S_OK</span></span>|<span data-ttu-id="28ae2-111">此方法已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="28ae2-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="28ae2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="28ae2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="28ae2-113">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="28ae2-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="28ae2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="28ae2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="28ae2-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="28ae2-115">The call timed out.</span></span>|  
|<span data-ttu-id="28ae2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="28ae2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="28ae2-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="28ae2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="28ae2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="28ae2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="28ae2-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="28ae2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="28ae2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="28ae2-120">E_FAIL</span></span>|<span data-ttu-id="28ae2-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="28ae2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="28ae2-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="28ae2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="28ae2-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="28ae2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="28ae2-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="28ae2-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="28ae2-125">可用的記憶體不足，無法配置要求的資源。</span><span class="sxs-lookup"><span data-stu-id="28ae2-125">Not enough memory is available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28ae2-126">備註</span><span class="sxs-lookup"><span data-stu-id="28ae2-126">Remarks</span></span>  

 <span data-ttu-id="28ae2-127">當使用者程式碼在命名空間中使用類型建立執行緒 <xref:System.Threading> ，或增加執行緒集區的大小時，CLR 會在初始化時自動建立新的工作。</span><span class="sxs-lookup"><span data-stu-id="28ae2-127">The CLR creates a new task automatically upon initialization, when user code creates a thread by using types in the <xref:System.Threading> namespace, or when the size of the thread pool is increased.</span></span> <span data-ttu-id="28ae2-128">當非受控程式碼呼叫 managed 函式時，也會建立工作。</span><span class="sxs-lookup"><span data-stu-id="28ae2-128">It also creates tasks when unmanaged code makes a call to a managed function.</span></span>  
  
 <span data-ttu-id="28ae2-129">`CreateTask` 允許主機發出明確的要求，讓 CLR 建立新的工作。</span><span class="sxs-lookup"><span data-stu-id="28ae2-129">`CreateTask` allows the host to make an explicit request that the CLR create a new task.</span></span> <span data-ttu-id="28ae2-130">例如，主機可以叫用這個方法來將資料結構。</span><span class="sxs-lookup"><span data-stu-id="28ae2-130">For example, the host can invoke this method to preinitialize data structures.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="28ae2-131">新工作會以暫停狀態傳回並保持暫停狀態，直到主機明確呼叫 [IHostTask：： Start](ihosttask-start-method.md)為止。</span><span class="sxs-lookup"><span data-stu-id="28ae2-131">The new task is returned in a suspended state and remains suspended until the host explicitly calls [IHostTask::Start](ihosttask-start-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28ae2-132">需求</span><span class="sxs-lookup"><span data-stu-id="28ae2-132">Requirements</span></span>  

 <span data-ttu-id="28ae2-133">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="28ae2-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28ae2-134">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="28ae2-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="28ae2-135">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="28ae2-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="28ae2-136">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28ae2-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28ae2-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28ae2-137">See also</span></span>

- [<span data-ttu-id="28ae2-138">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="28ae2-138">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="28ae2-139">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="28ae2-139">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="28ae2-140">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="28ae2-140">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="28ae2-141">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="28ae2-141">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
