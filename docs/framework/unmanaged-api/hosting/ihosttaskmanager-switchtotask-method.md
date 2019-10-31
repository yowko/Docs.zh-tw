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
ms.openlocfilehash: a55b43f3629cebb0ba1d3a7ac1802126874418d8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122122"
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="892f3-102">IHostTaskManager::SwitchToTask 方法</span><span class="sxs-lookup"><span data-stu-id="892f3-102">IHostTaskManager::SwitchToTask Method</span></span>
<span data-ttu-id="892f3-103">通知主機應該切換出目前的工作。</span><span class="sxs-lookup"><span data-stu-id="892f3-103">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="892f3-104">語法</span><span class="sxs-lookup"><span data-stu-id="892f3-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="892f3-105">參數</span><span class="sxs-lookup"><span data-stu-id="892f3-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="892f3-106">在其中一個[WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)列舉值，指出當要求的作業封鎖時，主機應採取的動作。</span><span class="sxs-lookup"><span data-stu-id="892f3-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="892f3-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="892f3-107">Return Value</span></span>  
  
|<span data-ttu-id="892f3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="892f3-108">HRESULT</span></span>|<span data-ttu-id="892f3-109">描述</span><span class="sxs-lookup"><span data-stu-id="892f3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="892f3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="892f3-110">S_OK</span></span>|<span data-ttu-id="892f3-111">已成功傳回 `SwitchToTask`。</span><span class="sxs-lookup"><span data-stu-id="892f3-111">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="892f3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="892f3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="892f3-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="892f3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="892f3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="892f3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="892f3-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="892f3-115">The call timed out.</span></span>|  
|<span data-ttu-id="892f3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="892f3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="892f3-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="892f3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="892f3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="892f3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="892f3-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="892f3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="892f3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="892f3-120">E_FAIL</span></span>|<span data-ttu-id="892f3-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="892f3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="892f3-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="892f3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="892f3-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="892f3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="892f3-124">備註</span><span class="sxs-lookup"><span data-stu-id="892f3-124">Remarks</span></span>  
 <span data-ttu-id="892f3-125">主機可以視需要或需要切換至另一個工作。</span><span class="sxs-lookup"><span data-stu-id="892f3-125">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="892f3-126">`SwitchToTask` 不會指定主機應切換至哪一項工作;它只會指定應該切換的工作。</span><span class="sxs-lookup"><span data-stu-id="892f3-126">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="892f3-127">需求</span><span class="sxs-lookup"><span data-stu-id="892f3-127">Requirements</span></span>  
 <span data-ttu-id="892f3-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="892f3-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="892f3-129">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="892f3-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="892f3-130">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="892f3-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="892f3-131">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="892f3-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="892f3-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="892f3-132">See also</span></span>

- [<span data-ttu-id="892f3-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="892f3-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="892f3-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="892f3-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="892f3-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="892f3-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="892f3-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="892f3-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
