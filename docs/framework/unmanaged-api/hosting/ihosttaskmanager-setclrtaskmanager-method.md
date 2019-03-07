---
title: IHostTaskManager::SetCLRTaskManager 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetCLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetCLRTaskManager
helpviewer_keywords:
- IHostTaskManager::SetCLRTaskManager method [.NET Framework hosting]
- SetCLRTaskManager method [.NET Framework hosting]
ms.assetid: ec90ee83-bd4b-408b-9274-62a923ab86a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a93efc0701248f8e4ef930261b31b3ce948647a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484923"
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="db540-102">IHostTaskManager::SetCLRTaskManager 方法</span><span class="sxs-lookup"><span data-stu-id="db540-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="db540-103">主應用程式提供的介面指標[ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) common language runtime (CLR) 所實作的執行個體。</span><span class="sxs-lookup"><span data-stu-id="db540-103">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db540-104">語法</span><span class="sxs-lookup"><span data-stu-id="db540-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db540-105">參數</span><span class="sxs-lookup"><span data-stu-id="db540-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="db540-106">[in]指標`ICLRTaskManager`藉由將 common language runtime 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="db540-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db540-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="db540-107">Return Value</span></span>  
  
|<span data-ttu-id="db540-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="db540-108">HRESULT</span></span>|<span data-ttu-id="db540-109">描述</span><span class="sxs-lookup"><span data-stu-id="db540-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="db540-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="db540-110">S_OK</span></span>|<span data-ttu-id="db540-111">`SetCLRTaskManager` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="db540-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="db540-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="db540-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="db540-113">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="db540-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="db540-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="db540-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="db540-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="db540-115">The call timed out.</span></span>|  
|<span data-ttu-id="db540-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="db540-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="db540-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="db540-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="db540-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="db540-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="db540-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="db540-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="db540-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="db540-120">E_FAIL</span></span>|<span data-ttu-id="db540-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="db540-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="db540-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="db540-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="db540-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="db540-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db540-124">備註</span><span class="sxs-lookup"><span data-stu-id="db540-124">Remarks</span></span>  
 <span data-ttu-id="db540-125">執行階段會呼叫`SetCLRTaskManager`為主機提供的介面指標`ICLRTaskManager`執行個體。</span><span class="sxs-lookup"><span data-stu-id="db540-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db540-126">需求</span><span class="sxs-lookup"><span data-stu-id="db540-126">Requirements</span></span>  
 <span data-ttu-id="db540-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="db540-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db540-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="db540-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="db540-129">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="db540-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db540-130">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db540-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db540-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db540-131">See also</span></span>
- [<span data-ttu-id="db540-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="db540-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="db540-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="db540-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="db540-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="db540-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="db540-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="db540-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
