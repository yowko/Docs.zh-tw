---
title: IHostTask::SetCLRTask 方法
ms.date: 03/30/2017
api_name:
- IHostTask.SetCLRTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetCLRTask
helpviewer_keywords:
- SetCLRTask method [.NET Framework hosting]
- IHostTask::SetCLRTask method [.NET Framework hosting]
ms.assetid: e9d39c80-41a1-49e7-bb5e-ea3433bfb5d7
topic_type:
- apiref
ms.openlocfilehash: b6eac134a4ffb1813cdc6957632ce5fb9b1a5fff
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842266"
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="a2e5e-102">IHostTask::SetCLRTask 方法</span><span class="sxs-lookup"><span data-stu-id="a2e5e-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="a2e5e-103">將 `ICLRTask` 實例與目前的[IHostTask](ihosttask-interface.md)實例產生關聯。</span><span class="sxs-lookup"><span data-stu-id="a2e5e-103">Associates an `ICLRTask` instance with the current [IHostTask](ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2e5e-104">語法</span><span class="sxs-lookup"><span data-stu-id="a2e5e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2e5e-105">參數</span><span class="sxs-lookup"><span data-stu-id="a2e5e-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="a2e5e-106">在要 `ICLRTask` 與目前實例相關聯之實例的介面指標 `IHostTask` 。</span><span class="sxs-lookup"><span data-stu-id="a2e5e-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2e5e-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="a2e5e-107">Return Value</span></span>  
  
|<span data-ttu-id="a2e5e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a2e5e-108">HRESULT</span></span>|<span data-ttu-id="a2e5e-109">描述</span><span class="sxs-lookup"><span data-stu-id="a2e5e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a2e5e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a2e5e-110">S_OK</span></span>|<span data-ttu-id="a2e5e-111">`SetCLRTask`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="a2e5e-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="a2e5e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a2e5e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a2e5e-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="a2e5e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a2e5e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a2e5e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a2e5e-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="a2e5e-115">The call timed out.</span></span>|  
|<span data-ttu-id="a2e5e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a2e5e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a2e5e-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="a2e5e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a2e5e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a2e5e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a2e5e-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="a2e5e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a2e5e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a2e5e-120">E_FAIL</span></span>|<span data-ttu-id="a2e5e-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="a2e5e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a2e5e-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="a2e5e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a2e5e-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a2e5e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2e5e-124">備註</span><span class="sxs-lookup"><span data-stu-id="a2e5e-124">Remarks</span></span>  
 <span data-ttu-id="a2e5e-125">CLR 會呼叫 `SetCLRTask` `ICLRTask` ，將實例與目前的 `IHostTask` 實例產生關聯，這是由呼叫[IHostTaskManager：： CreateTask](ihosttaskmanager-createtask-method.md)所建立。</span><span class="sxs-lookup"><span data-stu-id="a2e5e-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2e5e-126">規格需求</span><span class="sxs-lookup"><span data-stu-id="a2e5e-126">Requirements</span></span>  
 <span data-ttu-id="a2e5e-127">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a2e5e-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2e5e-128">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="a2e5e-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a2e5e-129">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a2e5e-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a2e5e-130">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2e5e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2e5e-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2e5e-131">See also</span></span>

- [<span data-ttu-id="a2e5e-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="a2e5e-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="a2e5e-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="a2e5e-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="a2e5e-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="a2e5e-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="a2e5e-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="a2e5e-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
