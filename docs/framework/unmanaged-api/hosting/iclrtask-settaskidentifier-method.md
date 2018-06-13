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
ms.openlocfilehash: 05a561c54f2d004d073fdfffffdb59cb2b5189e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435676"
---
# <a name="iclrtasksettaskidentifier-method"></a><span data-ttu-id="8d6a3-102">ICLRTask::SetTaskIdentifier 方法</span><span class="sxs-lookup"><span data-stu-id="8d6a3-102">ICLRTask::SetTaskIdentifier Method</span></span>
<span data-ttu-id="8d6a3-103">指示 common language runtime (CLR) 所指定的識別碼的值與表示由目前的工作[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)執行個體。</span><span class="sxs-lookup"><span data-stu-id="8d6a3-103">Instructs the common language runtime (CLR) to associate the specified identifier value with the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d6a3-104">語法</span><span class="sxs-lookup"><span data-stu-id="8d6a3-104">Syntax</span></span>  
  
```  
HRESULT SetTaskIdentifier (  
    [in] DWORD Asked  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8d6a3-105">參數</span><span class="sxs-lookup"><span data-stu-id="8d6a3-105">Parameters</span></span>  
 `Asked`  
 <span data-ttu-id="8d6a3-106">[in]Common language runtime 與表示由目前的工作產生關聯的唯一識別碼`ICLRTask`執行個體。</span><span class="sxs-lookup"><span data-stu-id="8d6a3-106">[in] The unique identifier for the common language runtime to associate with the task represented by the current `ICLRTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d6a3-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="8d6a3-107">Return Value</span></span>  
  
|<span data-ttu-id="8d6a3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8d6a3-108">HRESULT</span></span>|<span data-ttu-id="8d6a3-109">描述</span><span class="sxs-lookup"><span data-stu-id="8d6a3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8d6a3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8d6a3-110">S_OK</span></span>|<span data-ttu-id="8d6a3-111">`SetTaskIdentifier` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="8d6a3-111">`SetTaskIdentifier` returned successfully.</span></span>|  
|<span data-ttu-id="8d6a3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8d6a3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8d6a3-113">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="8d6a3-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8d6a3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8d6a3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8d6a3-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="8d6a3-115">The call timed out.</span></span>|  
|<span data-ttu-id="8d6a3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8d6a3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8d6a3-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="8d6a3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8d6a3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8d6a3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8d6a3-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="8d6a3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8d6a3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8d6a3-120">E_FAIL</span></span>|<span data-ttu-id="8d6a3-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="8d6a3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8d6a3-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="8d6a3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8d6a3-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="8d6a3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d6a3-124">備註</span><span class="sxs-lookup"><span data-stu-id="8d6a3-124">Remarks</span></span>  
 <span data-ttu-id="8d6a3-125">主機可以識別項關聯的工作，可協助整合 CLR 和偵錯環境中的主機。</span><span class="sxs-lookup"><span data-stu-id="8d6a3-125">The host can associate an identifier with a task to help integrate the CLR and the host in a debugging environment.</span></span> <span data-ttu-id="8d6a3-126">識別項具有 CLR 無意義。</span><span class="sxs-lookup"><span data-stu-id="8d6a3-126">The identifier has no meaning for the CLR.</span></span> <span data-ttu-id="8d6a3-127">CLR 會將它沿著傳遞至偵錯工具應用程式。</span><span class="sxs-lookup"><span data-stu-id="8d6a3-127">The CLR passes it along to a debugger application.</span></span> <span data-ttu-id="8d6a3-128">偵錯工具可以利用這個識別碼與主機呼叫堆疊中的 CLR 呼叫堆疊，並啟用在偵錯工具的使用者介面中檢視時統一其各自的追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="8d6a3-128">The debugger can use this identifier to associate a CLR call stack with a host call stack, and enable their respective trace information to be unified when viewed in the debugger's user interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d6a3-129">需求</span><span class="sxs-lookup"><span data-stu-id="8d6a3-129">Requirements</span></span>  
 <span data-ttu-id="8d6a3-130">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8d6a3-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d6a3-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8d6a3-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8d6a3-132">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8d6a3-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d6a3-133">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d6a3-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d6a3-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d6a3-134">See Also</span></span>  
 [<span data-ttu-id="8d6a3-135">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="8d6a3-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="8d6a3-136">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="8d6a3-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="8d6a3-137">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="8d6a3-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="8d6a3-138">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="8d6a3-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
