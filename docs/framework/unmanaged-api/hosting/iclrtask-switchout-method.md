---
title: "ICLRTask::SwitchOut 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8fc8fcc5550981b2b8f4a51877d9e6571954f48b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskswitchout-method"></a><span data-ttu-id="0a948-102">ICLRTask::SwitchOut 方法</span><span class="sxs-lookup"><span data-stu-id="0a948-102">ICLRTask::SwitchOut Method</span></span>
<span data-ttu-id="0a948-103">會告知 common language runtime (CLR)，代表目前的工作[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)執行個體已不再處於運作狀態。</span><span class="sxs-lookup"><span data-stu-id="0a948-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is no longer in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a948-104">語法</span><span class="sxs-lookup"><span data-stu-id="0a948-104">Syntax</span></span>  
  
```  
HRESULT SwitchOut ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0a948-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="0a948-105">Return Value</span></span>  
  
|<span data-ttu-id="0a948-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0a948-106">HRESULT</span></span>|<span data-ttu-id="0a948-107">描述</span><span class="sxs-lookup"><span data-stu-id="0a948-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0a948-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="0a948-108">S_OK</span></span>|<span data-ttu-id="0a948-109">`SwitchOut`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="0a948-109">`SwitchOut` returned successfully.</span></span>|  
|<span data-ttu-id="0a948-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0a948-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0a948-111">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="0a948-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0a948-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0a948-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0a948-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="0a948-113">The call timed out.</span></span>|  
|<span data-ttu-id="0a948-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0a948-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0a948-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="0a948-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0a948-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0a948-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0a948-117">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="0a948-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0a948-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0a948-118">E_FAIL</span></span>|<span data-ttu-id="0a948-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="0a948-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0a948-120">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="0a948-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0a948-121">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="0a948-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a948-122">備註</span><span class="sxs-lookup"><span data-stu-id="0a948-122">Remarks</span></span>  
 <span data-ttu-id="0a948-123">主機會呼叫`SwitchOut`通知 CLR 它已暫時停止執行工作的目前`ICLRTask`執行個體所表示，並將重新排程工作。</span><span class="sxs-lookup"><span data-stu-id="0a948-123">A host calls `SwitchOut` to inform the CLR that it has temporarily stopped executing the task that the current `ICLRTask` instance represents, and will reschedule the task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a948-124">需求</span><span class="sxs-lookup"><span data-stu-id="0a948-124">Requirements</span></span>  
 <span data-ttu-id="0a948-125">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0a948-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a948-126">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0a948-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0a948-127">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0a948-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a948-128">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a948-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a948-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="0a948-129">See Also</span></span>  
 [<span data-ttu-id="0a948-130">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="0a948-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="0a948-131">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="0a948-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="0a948-132">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="0a948-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="0a948-133">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="0a948-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
