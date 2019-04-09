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
ms.openlocfilehash: a50c9f7fc5921d3e5c21dd3566de81ac2249f3dd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110556"
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="6221a-102">IHostTaskManager::SwitchToTask 方法</span><span class="sxs-lookup"><span data-stu-id="6221a-102">IHostTaskManager::SwitchToTask Method</span></span>
<span data-ttu-id="6221a-103">主應用程式，它應該切換移出目前的工作。</span><span class="sxs-lookup"><span data-stu-id="6221a-103">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6221a-104">語法</span><span class="sxs-lookup"><span data-stu-id="6221a-104">Syntax</span></span>  
  
```  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6221a-105">參數</span><span class="sxs-lookup"><span data-stu-id="6221a-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="6221a-106">[in]其中一個[WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)列舉值，指出如果，主應用程式應該採取的動作要求的作業區塊。</span><span class="sxs-lookup"><span data-stu-id="6221a-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6221a-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="6221a-107">Return Value</span></span>  
  
|<span data-ttu-id="6221a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6221a-108">HRESULT</span></span>|<span data-ttu-id="6221a-109">描述</span><span class="sxs-lookup"><span data-stu-id="6221a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6221a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6221a-110">S_OK</span></span>|`SwitchToTask` <span data-ttu-id="6221a-111">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="6221a-111">returned successfully.</span></span>|  
|<span data-ttu-id="6221a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6221a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6221a-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="6221a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6221a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6221a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6221a-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="6221a-115">The call timed out.</span></span>|  
|<span data-ttu-id="6221a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6221a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6221a-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="6221a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6221a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6221a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6221a-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="6221a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6221a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6221a-120">E_FAIL</span></span>|<span data-ttu-id="6221a-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="6221a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6221a-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="6221a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6221a-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="6221a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6221a-124">備註</span><span class="sxs-lookup"><span data-stu-id="6221a-124">Remarks</span></span>  
 <span data-ttu-id="6221a-125">主機可以切換為想要或需要另一項工作。</span><span class="sxs-lookup"><span data-stu-id="6221a-125">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
>  `SwitchToTask` <span data-ttu-id="6221a-126">未指定主應用程式應該切換至; 的工作它會指定它應該從切換的工作。</span><span class="sxs-lookup"><span data-stu-id="6221a-126">does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6221a-127">需求</span><span class="sxs-lookup"><span data-stu-id="6221a-127">Requirements</span></span>  
 <span data-ttu-id="6221a-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6221a-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6221a-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6221a-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6221a-130">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6221a-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="6221a-131">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="6221a-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6221a-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6221a-132">See also</span></span>

- [<span data-ttu-id="6221a-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="6221a-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="6221a-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="6221a-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="6221a-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="6221a-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="6221a-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="6221a-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
