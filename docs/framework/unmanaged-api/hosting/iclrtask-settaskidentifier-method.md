---
title: ICLRTask::SetTaskIdentifier 方法
ms.date: 03/30/2017
api_name:
- ICLRTask.SetTaskIdentifier
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SetTaskIdentifier
helpviewer_keywords:
- SetTaskIdentifier method [.NET Framework hosting]
- ICLRTask::SetTaskIdentifier method [.NET Framework hosting]
ms.assetid: bdb7f047-1e90-40fc-9e3b-d44a16509073
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: abd8848ed54b26b66090e4865f9c3a0e5c4d20db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763499"
---
# <a name="iclrtasksettaskidentifier-method"></a><span data-ttu-id="b59b7-102">ICLRTask::SetTaskIdentifier 方法</span><span class="sxs-lookup"><span data-stu-id="b59b7-102">ICLRTask::SetTaskIdentifier Method</span></span>
<span data-ttu-id="b59b7-103">指示 common language runtime (CLR)，表示由目前的工作相關聯的指定之識別碼值[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)執行個體。</span><span class="sxs-lookup"><span data-stu-id="b59b7-103">Instructs the common language runtime (CLR) to associate the specified identifier value with the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b59b7-104">語法</span><span class="sxs-lookup"><span data-stu-id="b59b7-104">Syntax</span></span>  
  
```  
HRESULT SetTaskIdentifier (  
    [in] DWORD Asked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b59b7-105">參數</span><span class="sxs-lookup"><span data-stu-id="b59b7-105">Parameters</span></span>  
 `Asked`  
 <span data-ttu-id="b59b7-106">[in]通用語言執行平台，表示由目前的工作相關聯的唯一識別碼`ICLRTask`執行個體。</span><span class="sxs-lookup"><span data-stu-id="b59b7-106">[in] The unique identifier for the common language runtime to associate with the task represented by the current `ICLRTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b59b7-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="b59b7-107">Return Value</span></span>  
  
|<span data-ttu-id="b59b7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b59b7-108">HRESULT</span></span>|<span data-ttu-id="b59b7-109">描述</span><span class="sxs-lookup"><span data-stu-id="b59b7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b59b7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b59b7-110">S_OK</span></span>|<span data-ttu-id="b59b7-111">`SetTaskIdentifier` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="b59b7-111">`SetTaskIdentifier` returned successfully.</span></span>|  
|<span data-ttu-id="b59b7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b59b7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b59b7-113">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="b59b7-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b59b7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b59b7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b59b7-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="b59b7-115">The call timed out.</span></span>|  
|<span data-ttu-id="b59b7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b59b7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b59b7-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b59b7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b59b7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b59b7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b59b7-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="b59b7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b59b7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b59b7-120">E_FAIL</span></span>|<span data-ttu-id="b59b7-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="b59b7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b59b7-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="b59b7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b59b7-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b59b7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b59b7-124">備註</span><span class="sxs-lookup"><span data-stu-id="b59b7-124">Remarks</span></span>  
 <span data-ttu-id="b59b7-125">主應用程式可以將識別項關聯的工作，可協助整合 CLR 和偵錯環境中的主機。</span><span class="sxs-lookup"><span data-stu-id="b59b7-125">The host can associate an identifier with a task to help integrate the CLR and the host in a debugging environment.</span></span> <span data-ttu-id="b59b7-126">表示識別項具有對 CLR 而言沒有意義。</span><span class="sxs-lookup"><span data-stu-id="b59b7-126">The identifier has no meaning for the CLR.</span></span> <span data-ttu-id="b59b7-127">CLR 會將它傳遞給偵錯工具應用程式。</span><span class="sxs-lookup"><span data-stu-id="b59b7-127">The CLR passes it along to a debugger application.</span></span> <span data-ttu-id="b59b7-128">偵錯工具可以使用這個識別碼與主應用程式呼叫堆疊、 建立關聯 CLR 呼叫堆疊，並啟用其各自的追蹤資訊，以在偵錯工具的使用者介面中檢視時進行整合。</span><span class="sxs-lookup"><span data-stu-id="b59b7-128">The debugger can use this identifier to associate a CLR call stack with a host call stack, and enable their respective trace information to be unified when viewed in the debugger's user interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b59b7-129">需求</span><span class="sxs-lookup"><span data-stu-id="b59b7-129">Requirements</span></span>  
 <span data-ttu-id="b59b7-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b59b7-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b59b7-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b59b7-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b59b7-132">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b59b7-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b59b7-133">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b59b7-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b59b7-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b59b7-134">See also</span></span>

- [<span data-ttu-id="b59b7-135">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="b59b7-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="b59b7-136">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="b59b7-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="b59b7-137">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="b59b7-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="b59b7-138">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="b59b7-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
