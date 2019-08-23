---
title: IHostTaskManager::SwitchToTask 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SwitchToTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SwitchToTask
helpviewer_keywords:
- IHostTaskManager::SwitchToTask method [.NET Framework hosting]
- SwitchToTask method [.NET Framework hosting]
ms.assetid: 35d0c27e-4b14-49ce-810d-7ab2120177e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4af3d73a4c45654d1d40ef2fbf44a0e2b3e1bf32
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913706"
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="946fe-102">IHostTaskManager::SwitchToTask 方法</span><span class="sxs-lookup"><span data-stu-id="946fe-102">IHostTaskManager::SwitchToTask Method</span></span>
<span data-ttu-id="946fe-103">通知主機應該切換出目前的工作。</span><span class="sxs-lookup"><span data-stu-id="946fe-103">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="946fe-104">語法</span><span class="sxs-lookup"><span data-stu-id="946fe-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="946fe-105">參數</span><span class="sxs-lookup"><span data-stu-id="946fe-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="946fe-106">在其中一個[WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)列舉值, 指出當要求的作業封鎖時, 主機應採取的動作。</span><span class="sxs-lookup"><span data-stu-id="946fe-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="946fe-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="946fe-107">Return Value</span></span>  
  
|<span data-ttu-id="946fe-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="946fe-108">HRESULT</span></span>|<span data-ttu-id="946fe-109">說明</span><span class="sxs-lookup"><span data-stu-id="946fe-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="946fe-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="946fe-110">S_OK</span></span>|<span data-ttu-id="946fe-111">`SwitchToTask`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="946fe-111">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="946fe-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="946fe-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="946fe-113">Common language runtime (CLR) 尚未載入進程中, 或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="946fe-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="946fe-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="946fe-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="946fe-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="946fe-115">The call timed out.</span></span>|  
|<span data-ttu-id="946fe-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="946fe-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="946fe-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="946fe-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="946fe-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="946fe-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="946fe-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="946fe-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="946fe-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="946fe-120">E_FAIL</span></span>|<span data-ttu-id="946fe-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="946fe-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="946fe-122">當方法傳回 E_FAIL 時, CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="946fe-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="946fe-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="946fe-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="946fe-124">備註</span><span class="sxs-lookup"><span data-stu-id="946fe-124">Remarks</span></span>  
 <span data-ttu-id="946fe-125">主機可以視需要或需要切換至另一個工作。</span><span class="sxs-lookup"><span data-stu-id="946fe-125">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="946fe-126">`SwitchToTask`不會指定主機應切換至哪一項工作;它只會指定應該切換的工作。</span><span class="sxs-lookup"><span data-stu-id="946fe-126">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="946fe-127">需求</span><span class="sxs-lookup"><span data-stu-id="946fe-127">Requirements</span></span>  
 <span data-ttu-id="946fe-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="946fe-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="946fe-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="946fe-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="946fe-130">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="946fe-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="946fe-131">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="946fe-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="946fe-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="946fe-132">See also</span></span>

- [<span data-ttu-id="946fe-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="946fe-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="946fe-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="946fe-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="946fe-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="946fe-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="946fe-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="946fe-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
