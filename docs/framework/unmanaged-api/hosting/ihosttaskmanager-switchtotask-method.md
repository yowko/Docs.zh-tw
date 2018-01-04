---
title: "IHostTaskManager::SwitchToTask 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.SwitchToTask
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::SwitchToTask
helpviewer_keywords:
- IHostTaskManager::SwitchToTask method [.NET Framework hosting]
- SwitchToTask method [.NET Framework hosting]
ms.assetid: 35d0c27e-4b14-49ce-810d-7ab2120177e8
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 03578a6a9579a807323d54308347f16f24ae90dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="c5f2b-102">IHostTaskManager::SwitchToTask 方法</span><span class="sxs-lookup"><span data-stu-id="c5f2b-102">IHostTaskManager::SwitchToTask Method</span></span>
<span data-ttu-id="c5f2b-103">通知主機，它應該切換移出目前的工作。</span><span class="sxs-lookup"><span data-stu-id="c5f2b-103">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5f2b-104">語法</span><span class="sxs-lookup"><span data-stu-id="c5f2b-104">Syntax</span></span>  
  
```  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5f2b-105">參數</span><span class="sxs-lookup"><span data-stu-id="c5f2b-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="c5f2b-106">[in]其中一個[WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)列舉值，指出如果主應用程式應該採取的動作要求的作業區塊。</span><span class="sxs-lookup"><span data-stu-id="c5f2b-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c5f2b-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="c5f2b-107">Return Value</span></span>  
  
|<span data-ttu-id="c5f2b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c5f2b-108">HRESULT</span></span>|<span data-ttu-id="c5f2b-109">描述</span><span class="sxs-lookup"><span data-stu-id="c5f2b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c5f2b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c5f2b-110">S_OK</span></span>|<span data-ttu-id="c5f2b-111">`SwitchToTask`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="c5f2b-111">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="c5f2b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c5f2b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c5f2b-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="c5f2b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c5f2b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c5f2b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c5f2b-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="c5f2b-115">The call timed out.</span></span>|  
|<span data-ttu-id="c5f2b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c5f2b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c5f2b-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="c5f2b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c5f2b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c5f2b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c5f2b-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="c5f2b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c5f2b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c5f2b-120">E_FAIL</span></span>|<span data-ttu-id="c5f2b-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="c5f2b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c5f2b-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="c5f2b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c5f2b-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="c5f2b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5f2b-124">備註</span><span class="sxs-lookup"><span data-stu-id="c5f2b-124">Remarks</span></span>  
 <span data-ttu-id="c5f2b-125">主機可以在另一個工作所需或需要切換。</span><span class="sxs-lookup"><span data-stu-id="c5f2b-125">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5f2b-126">`SwitchToTask`未指定主機應改為; 的工作它會指定它應該從切換的工作。</span><span class="sxs-lookup"><span data-stu-id="c5f2b-126">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5f2b-127">需求</span><span class="sxs-lookup"><span data-stu-id="c5f2b-127">Requirements</span></span>  
 <span data-ttu-id="c5f2b-128">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c5f2b-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5f2b-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c5f2b-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c5f2b-130">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c5f2b-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5f2b-131">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5f2b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5f2b-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="c5f2b-132">See Also</span></span>  
 [<span data-ttu-id="c5f2b-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="c5f2b-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="c5f2b-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="c5f2b-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="c5f2b-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="c5f2b-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="c5f2b-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="c5f2b-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
