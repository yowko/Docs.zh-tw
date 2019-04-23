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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc8d936ac4fca704e7e3069209d8ff75d46b044d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113668"
---
# <a name="iclrtaskyieldtask-method"></a><span data-ttu-id="05065-102">ICLRTask::YieldTask 方法</span><span class="sxs-lookup"><span data-stu-id="05065-102">ICLRTask::YieldTask Method</span></span>
<span data-ttu-id="05065-103">要求 common language runtime (CLR) 擱置在一旁把工作的目前[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)執行個體表示，並提供其他工作的處理器時間。</span><span class="sxs-lookup"><span data-stu-id="05065-103">Requests that the common language runtime (CLR) put aside the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents, and make the processor time available to other tasks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05065-104">語法</span><span class="sxs-lookup"><span data-stu-id="05065-104">Syntax</span></span>  
  
```  
HRESULT YieldTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="05065-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="05065-105">Return Value</span></span>  
  
|<span data-ttu-id="05065-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="05065-106">HRESULT</span></span>|<span data-ttu-id="05065-107">描述</span><span class="sxs-lookup"><span data-stu-id="05065-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="05065-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="05065-108">S_OK</span></span>|<span data-ttu-id="05065-109">`YieldTask` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="05065-109">`YieldTask` returned successfully.</span></span>|  
|<span data-ttu-id="05065-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="05065-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="05065-111">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="05065-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="05065-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="05065-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="05065-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="05065-113">The call timed out.</span></span>|  
|<span data-ttu-id="05065-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="05065-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="05065-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="05065-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="05065-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="05065-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="05065-117">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="05065-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="05065-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="05065-118">E_FAIL</span></span>|<span data-ttu-id="05065-119">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="05065-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="05065-120">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="05065-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="05065-121">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="05065-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05065-122">備註</span><span class="sxs-lookup"><span data-stu-id="05065-122">Remarks</span></span>  
 <span data-ttu-id="05065-123">主機會呼叫`YieldTask`來要求其他工作或處理序的處理器資源。</span><span class="sxs-lookup"><span data-stu-id="05065-123">A host calls `YieldTask` to request processor resources for other tasks or processes.</span></span> <span data-ttu-id="05065-124">這個方法主要是讓長時間執行的程式碼，放棄 CPU 時間。</span><span class="sxs-lookup"><span data-stu-id="05065-124">This method is primarily intended to allow long-running code to give up CPU time.</span></span> <span data-ttu-id="05065-125">執行階段會嘗試將工作放，目前`ICLRTask`執行個體表示它可以產生的處理時間，但不一定成功的狀態。</span><span class="sxs-lookup"><span data-stu-id="05065-125">The runtime attempts to put the task that the current `ICLRTask` instance represents in a state where it can yield processing time, but makes no guarantee of success.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05065-126">需求</span><span class="sxs-lookup"><span data-stu-id="05065-126">Requirements</span></span>  
 <span data-ttu-id="05065-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="05065-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05065-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="05065-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="05065-129">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="05065-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05065-130">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05065-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05065-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05065-131">See also</span></span>

- [<span data-ttu-id="05065-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="05065-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="05065-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="05065-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="05065-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="05065-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="05065-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="05065-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
