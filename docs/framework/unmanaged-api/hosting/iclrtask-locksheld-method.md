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
ms.openlocfilehash: 3a3c42e2877957e3bbf5031e6ba650e4c9e0364e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195951"
---
# <a name="iclrtasklocksheld-method"></a><span data-ttu-id="1dcb8-102">ICLRTask::LocksHeld 方法</span><span class="sxs-lookup"><span data-stu-id="1dcb8-102">ICLRTask::LocksHeld Method</span></span>
<span data-ttu-id="1dcb8-103">取得目前保留在工作上的鎖定數目。</span><span class="sxs-lookup"><span data-stu-id="1dcb8-103">Gets the number of locks currently held on the task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dcb8-104">語法</span><span class="sxs-lookup"><span data-stu-id="1dcb8-104">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeld (  
    [out] SIZE_T *pLockCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1dcb8-105">參數</span><span class="sxs-lookup"><span data-stu-id="1dcb8-105">Parameters</span></span>  
 `pLockCount`  
 <span data-ttu-id="1dcb8-106">脫銷在方法呼叫時，在工作上保留的鎖定數目。</span><span class="sxs-lookup"><span data-stu-id="1dcb8-106">[out] The number of locks held on the task at the time of the method call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1dcb8-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="1dcb8-107">Return Value</span></span>  
  
|<span data-ttu-id="1dcb8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1dcb8-108">HRESULT</span></span>|<span data-ttu-id="1dcb8-109">描述</span><span class="sxs-lookup"><span data-stu-id="1dcb8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1dcb8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1dcb8-110">S_OK</span></span>|<span data-ttu-id="1dcb8-111">已成功傳回 `LocksHeld`。</span><span class="sxs-lookup"><span data-stu-id="1dcb8-111">`LocksHeld` returned successfully.</span></span>|  
|<span data-ttu-id="1dcb8-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1dcb8-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1dcb8-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="1dcb8-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1dcb8-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1dcb8-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1dcb8-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="1dcb8-115">The call timed out.</span></span>|  
|<span data-ttu-id="1dcb8-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1dcb8-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1dcb8-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="1dcb8-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1dcb8-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1dcb8-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1dcb8-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="1dcb8-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1dcb8-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1dcb8-120">E_FAIL</span></span>|<span data-ttu-id="1dcb8-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="1dcb8-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1dcb8-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="1dcb8-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1dcb8-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="1dcb8-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1dcb8-124">需求</span><span class="sxs-lookup"><span data-stu-id="1dcb8-124">Requirements</span></span>  
 <span data-ttu-id="1dcb8-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1dcb8-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dcb8-126">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="1dcb8-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1dcb8-127">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1dcb8-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1dcb8-128">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dcb8-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dcb8-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="1dcb8-129">See also</span></span>

- [<span data-ttu-id="1dcb8-130">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="1dcb8-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="1dcb8-131">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="1dcb8-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="1dcb8-132">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="1dcb8-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="1dcb8-133">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="1dcb8-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
