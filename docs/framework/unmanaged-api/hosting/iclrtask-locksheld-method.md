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
ms.openlocfilehash: c67f00acd61d6e0cdf3adfa0d3d0fda2a06a6f31
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762975"
---
# <a name="iclrtasklocksheld-method"></a><span data-ttu-id="3eb31-102">ICLRTask::LocksHeld 方法</span><span class="sxs-lookup"><span data-stu-id="3eb31-102">ICLRTask::LocksHeld Method</span></span>
<span data-ttu-id="3eb31-103">取得目前保留在工作上的鎖定數目。</span><span class="sxs-lookup"><span data-stu-id="3eb31-103">Gets the number of locks currently held on the task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eb31-104">語法</span><span class="sxs-lookup"><span data-stu-id="3eb31-104">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeld (  
    [out] SIZE_T *pLockCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3eb31-105">參數</span><span class="sxs-lookup"><span data-stu-id="3eb31-105">Parameters</span></span>  
 `pLockCount`  
 <span data-ttu-id="3eb31-106">脫銷在方法呼叫時，在工作上保留的鎖定數目。</span><span class="sxs-lookup"><span data-stu-id="3eb31-106">[out] The number of locks held on the task at the time of the method call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3eb31-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="3eb31-107">Return Value</span></span>  
  
|<span data-ttu-id="3eb31-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3eb31-108">HRESULT</span></span>|<span data-ttu-id="3eb31-109">Description</span><span class="sxs-lookup"><span data-stu-id="3eb31-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3eb31-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3eb31-110">S_OK</span></span>|<span data-ttu-id="3eb31-111">`LocksHeld`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="3eb31-111">`LocksHeld` returned successfully.</span></span>|  
|<span data-ttu-id="3eb31-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3eb31-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3eb31-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="3eb31-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3eb31-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3eb31-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3eb31-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="3eb31-115">The call timed out.</span></span>|  
|<span data-ttu-id="3eb31-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3eb31-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3eb31-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="3eb31-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3eb31-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3eb31-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3eb31-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="3eb31-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3eb31-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3eb31-120">E_FAIL</span></span>|<span data-ttu-id="3eb31-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="3eb31-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3eb31-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="3eb31-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3eb31-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="3eb31-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3eb31-124">規格需求</span><span class="sxs-lookup"><span data-stu-id="3eb31-124">Requirements</span></span>  
 <span data-ttu-id="3eb31-125">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3eb31-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3eb31-126">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="3eb31-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3eb31-127">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3eb31-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3eb31-128">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3eb31-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eb31-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3eb31-129">See also</span></span>

- [<span data-ttu-id="3eb31-130">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="3eb31-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="3eb31-131">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="3eb31-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="3eb31-132">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="3eb31-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="3eb31-133">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="3eb31-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
