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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21e77b781c382cbcab79a93a0c58edd4f07690b2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770397"
---
# <a name="iclrtaskswitchout-method"></a><span data-ttu-id="45c5c-102">ICLRTask::SwitchOut 方法</span><span class="sxs-lookup"><span data-stu-id="45c5c-102">ICLRTask::SwitchOut Method</span></span>
<span data-ttu-id="45c5c-103">會告知 common language runtime (CLR)，代表目前的工作[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)執行個體已不再處於運作狀態。</span><span class="sxs-lookup"><span data-stu-id="45c5c-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is no longer in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45c5c-104">語法</span><span class="sxs-lookup"><span data-stu-id="45c5c-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchOut ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="45c5c-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="45c5c-105">Return Value</span></span>  
  
|<span data-ttu-id="45c5c-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="45c5c-106">HRESULT</span></span>|<span data-ttu-id="45c5c-107">說明</span><span class="sxs-lookup"><span data-stu-id="45c5c-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="45c5c-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="45c5c-108">S_OK</span></span>|<span data-ttu-id="45c5c-109">`SwitchOut` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="45c5c-109">`SwitchOut` returned successfully.</span></span>|  
|<span data-ttu-id="45c5c-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="45c5c-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="45c5c-111">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="45c5c-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="45c5c-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="45c5c-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="45c5c-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="45c5c-113">The call timed out.</span></span>|  
|<span data-ttu-id="45c5c-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="45c5c-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="45c5c-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="45c5c-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="45c5c-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="45c5c-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="45c5c-117">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="45c5c-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="45c5c-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="45c5c-118">E_FAIL</span></span>|<span data-ttu-id="45c5c-119">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="45c5c-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="45c5c-120">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="45c5c-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="45c5c-121">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="45c5c-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45c5c-122">備註</span><span class="sxs-lookup"><span data-stu-id="45c5c-122">Remarks</span></span>  
 <span data-ttu-id="45c5c-123">主機會呼叫`SwitchOut`來通知 CLR 暫時停止執行工作的目前`ICLRTask`執行個體表示，並將重新排定的工作。</span><span class="sxs-lookup"><span data-stu-id="45c5c-123">A host calls `SwitchOut` to inform the CLR that it has temporarily stopped executing the task that the current `ICLRTask` instance represents, and will reschedule the task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45c5c-124">需求</span><span class="sxs-lookup"><span data-stu-id="45c5c-124">Requirements</span></span>  
 <span data-ttu-id="45c5c-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="45c5c-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45c5c-126">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="45c5c-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="45c5c-127">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="45c5c-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="45c5c-128">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45c5c-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45c5c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45c5c-129">See also</span></span>

- [<span data-ttu-id="45c5c-130">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="45c5c-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="45c5c-131">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="45c5c-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="45c5c-132">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="45c5c-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="45c5c-133">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="45c5c-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
