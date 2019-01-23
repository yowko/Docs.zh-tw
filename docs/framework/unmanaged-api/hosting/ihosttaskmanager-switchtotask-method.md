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
ms.openlocfilehash: 9c7bf550985b5177348541aaa148c88c7c205258
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54490713"
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="568e5-102">IHostTaskManager::SwitchToTask 方法</span><span class="sxs-lookup"><span data-stu-id="568e5-102">IHostTaskManager::SwitchToTask Method</span></span>
<span data-ttu-id="568e5-103">主應用程式，它應該切換移出目前的工作。</span><span class="sxs-lookup"><span data-stu-id="568e5-103">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="568e5-104">語法</span><span class="sxs-lookup"><span data-stu-id="568e5-104">Syntax</span></span>  
  
```  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="568e5-105">參數</span><span class="sxs-lookup"><span data-stu-id="568e5-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="568e5-106">[in]其中一個[WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)列舉值，指出如果，主應用程式應該採取的動作要求的作業區塊。</span><span class="sxs-lookup"><span data-stu-id="568e5-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="568e5-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="568e5-107">Return Value</span></span>  
  
|<span data-ttu-id="568e5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="568e5-108">HRESULT</span></span>|<span data-ttu-id="568e5-109">描述</span><span class="sxs-lookup"><span data-stu-id="568e5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="568e5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="568e5-110">S_OK</span></span>|<span data-ttu-id="568e5-111">`SwitchToTask` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="568e5-111">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="568e5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="568e5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="568e5-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="568e5-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="568e5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="568e5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="568e5-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="568e5-115">The call timed out.</span></span>|  
|<span data-ttu-id="568e5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="568e5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="568e5-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="568e5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="568e5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="568e5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="568e5-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="568e5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="568e5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="568e5-120">E_FAIL</span></span>|<span data-ttu-id="568e5-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="568e5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="568e5-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="568e5-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="568e5-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="568e5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="568e5-124">備註</span><span class="sxs-lookup"><span data-stu-id="568e5-124">Remarks</span></span>  
 <span data-ttu-id="568e5-125">主機可以切換為想要或需要另一項工作。</span><span class="sxs-lookup"><span data-stu-id="568e5-125">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="568e5-126">`SwitchToTask` 未指定主應用程式應該切換至; 的工作它會指定它應該從切換的工作。</span><span class="sxs-lookup"><span data-stu-id="568e5-126">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="568e5-127">需求</span><span class="sxs-lookup"><span data-stu-id="568e5-127">Requirements</span></span>  
 <span data-ttu-id="568e5-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="568e5-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="568e5-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="568e5-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="568e5-130">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="568e5-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="568e5-131">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="568e5-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="568e5-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="568e5-132">See also</span></span>
- [<span data-ttu-id="568e5-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="568e5-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="568e5-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="568e5-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="568e5-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="568e5-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="568e5-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="568e5-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
