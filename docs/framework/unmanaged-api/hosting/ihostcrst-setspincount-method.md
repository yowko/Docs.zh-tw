---
title: IHostCrst::SetSpinCount 方法
ms.date: 03/30/2017
api_name:
- IHostCrst.SetSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::SetSpinCount
helpviewer_keywords:
- IHostCrst::SetSpinCount method [.NET Framework hosting]
- SetSpinCount method [.NET Framework hosting]
ms.assetid: 863fc8ce-9b8a-477e-8dd8-75c8544bb43a
topic_type:
- apiref
ms.openlocfilehash: a8642235cda359b849c49a35ab565397402c37d2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130507"
---
# <a name="ihostcrstsetspincount-method"></a><span data-ttu-id="57c05-102">IHostCrst::SetSpinCount 方法</span><span class="sxs-lookup"><span data-stu-id="57c05-102">IHostCrst::SetSpinCount Method</span></span>
<span data-ttu-id="57c05-103">設定目前[IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)實例的微調計數。</span><span class="sxs-lookup"><span data-stu-id="57c05-103">Sets the spin count for the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57c05-104">語法</span><span class="sxs-lookup"><span data-stu-id="57c05-104">Syntax</span></span>  
  
```cpp  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57c05-105">參數</span><span class="sxs-lookup"><span data-stu-id="57c05-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="57c05-106">在目前 `IHostCrst` 實例的新微調計數。</span><span class="sxs-lookup"><span data-stu-id="57c05-106">[in] The new spin count for the current `IHostCrst` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57c05-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="57c05-107">Return Value</span></span>  
  
|<span data-ttu-id="57c05-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="57c05-108">HRESULT</span></span>|<span data-ttu-id="57c05-109">描述</span><span class="sxs-lookup"><span data-stu-id="57c05-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="57c05-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="57c05-110">S_OK</span></span>|<span data-ttu-id="57c05-111">已成功傳回 `SetSpinCount`。</span><span class="sxs-lookup"><span data-stu-id="57c05-111">`SetSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="57c05-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="57c05-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="57c05-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="57c05-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="57c05-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="57c05-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="57c05-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="57c05-115">The call timed out.</span></span>|  
|<span data-ttu-id="57c05-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="57c05-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="57c05-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="57c05-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="57c05-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="57c05-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="57c05-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="57c05-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="57c05-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="57c05-120">E_FAIL</span></span>|<span data-ttu-id="57c05-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="57c05-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="57c05-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="57c05-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="57c05-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="57c05-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57c05-124">備註</span><span class="sxs-lookup"><span data-stu-id="57c05-124">Remarks</span></span>  
 <span data-ttu-id="57c05-125">在多處理器系統上，如果目前 `IHostCrst` 實例所表示的重要區段無法使用，則呼叫執行緒會旋轉 `dwSpinCount` 時間，然後才在與 critical 區段相關聯的信號上呼叫[IHostSemaphore：： Wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) 。</span><span class="sxs-lookup"><span data-stu-id="57c05-125">On multi-processor systems, if the critical section represented by the current `IHostCrst` instance is unavailable, a calling thread spins `dwSpinCount` times before calling [IHostSemaphore::Wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) on a semaphore associated with the critical section.</span></span> <span data-ttu-id="57c05-126">如果關鍵區段在微調作業期間變得免費，呼叫的執行緒會避免等候作業。</span><span class="sxs-lookup"><span data-stu-id="57c05-126">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span>  
  
 <span data-ttu-id="57c05-127">`dwSpinCount` 的用法與 Win32 `InitializeCriticalSectionAndSpinCount` 函式中相同名稱的參數使用方式相同。</span><span class="sxs-lookup"><span data-stu-id="57c05-127">The usage of `dwSpinCount` is identical to the usage of the parameter of the same name in the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57c05-128">需求</span><span class="sxs-lookup"><span data-stu-id="57c05-128">Requirements</span></span>  
 <span data-ttu-id="57c05-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="57c05-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57c05-130">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="57c05-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57c05-131">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="57c05-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57c05-132">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57c05-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57c05-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="57c05-133">See also</span></span>

- [<span data-ttu-id="57c05-134">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="57c05-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="57c05-135">IHostCrst 介面</span><span class="sxs-lookup"><span data-stu-id="57c05-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="57c05-136">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="57c05-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
