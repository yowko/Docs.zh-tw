---
title: ICLRTask::LocksHeld 方法
ms.date: 03/30/2017
api_name:
- ICLRTask.LocksHeld
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::LocksHeld
helpviewer_keywords:
- LocksHeld method [.NET Framework hosting]
- ICLRTask::LocksHeld method [.NET Framework hosting]
ms.assetid: e88a4dc3-02cc-4703-a474-292b71c40657
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 931395a1bb5f516000097f964ce0372a69420d85
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679626"
---
# <a name="iclrtasklocksheld-method"></a><span data-ttu-id="a9eda-102">ICLRTask::LocksHeld 方法</span><span class="sxs-lookup"><span data-stu-id="a9eda-102">ICLRTask::LocksHeld Method</span></span>
<span data-ttu-id="a9eda-103">取得目前工作上保留的鎖定數目。</span><span class="sxs-lookup"><span data-stu-id="a9eda-103">Gets the number of locks currently held on the task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9eda-104">語法</span><span class="sxs-lookup"><span data-stu-id="a9eda-104">Syntax</span></span>  
  
```  
HRESULT LocksHeld (  
    [out] SIZE_T *pLockCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a9eda-105">參數</span><span class="sxs-lookup"><span data-stu-id="a9eda-105">Parameters</span></span>  
 `pLockCount`  
 <span data-ttu-id="a9eda-106">[out]在方法呼叫時，在工作上持有鎖定的數量。</span><span class="sxs-lookup"><span data-stu-id="a9eda-106">[out] The number of locks held on the task at the time of the method call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9eda-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="a9eda-107">Return Value</span></span>  
  
|<span data-ttu-id="a9eda-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a9eda-108">HRESULT</span></span>|<span data-ttu-id="a9eda-109">描述</span><span class="sxs-lookup"><span data-stu-id="a9eda-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a9eda-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a9eda-110">S_OK</span></span>|<span data-ttu-id="a9eda-111">`LocksHeld` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="a9eda-111">`LocksHeld` returned successfully.</span></span>|  
|<span data-ttu-id="a9eda-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a9eda-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a9eda-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="a9eda-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a9eda-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a9eda-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a9eda-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="a9eda-115">The call timed out.</span></span>|  
|<span data-ttu-id="a9eda-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a9eda-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a9eda-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="a9eda-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a9eda-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a9eda-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a9eda-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="a9eda-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a9eda-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a9eda-120">E_FAIL</span></span>|<span data-ttu-id="a9eda-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="a9eda-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a9eda-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="a9eda-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a9eda-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a9eda-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a9eda-124">需求</span><span class="sxs-lookup"><span data-stu-id="a9eda-124">Requirements</span></span>  
 <span data-ttu-id="a9eda-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a9eda-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9eda-126">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a9eda-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a9eda-127">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a9eda-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a9eda-128">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9eda-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9eda-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9eda-129">See also</span></span>
- [<span data-ttu-id="a9eda-130">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="a9eda-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="a9eda-131">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="a9eda-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="a9eda-132">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="a9eda-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="a9eda-133">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="a9eda-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
