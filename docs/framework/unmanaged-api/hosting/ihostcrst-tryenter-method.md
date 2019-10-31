---
title: IHostCrst::TryEnter 方法
ms.date: 03/30/2017
api_name:
- IHostCrst.TryEnter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::TryEnter
helpviewer_keywords:
- IHostCrst::TryEnter method [.NET Framework hosting]
- TryEnter method [.NET Framework hosting]
ms.assetid: a922fa98-beab-4f09-a342-cc94fc65687f
topic_type:
- apiref
ms.openlocfilehash: f4b40a595bbdea4dd390a42af6a0d4b1a5efa2f2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130499"
---
# <a name="ihostcrsttryenter-method"></a><span data-ttu-id="c2317-102">IHostCrst::TryEnter 方法</span><span class="sxs-lookup"><span data-stu-id="c2317-102">IHostCrst::TryEnter Method</span></span>
<span data-ttu-id="c2317-103">嘗試輸入目前[IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)實例所表示的重要區段。</span><span class="sxs-lookup"><span data-stu-id="c2317-103">Attempts to enter the critical section represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2317-104">語法</span><span class="sxs-lookup"><span data-stu-id="c2317-104">Syntax</span></span>  
  
```cpp  
HRESULT TryEnter (  
    [in]  DWORD  option,  
    [out] BOOL   *pbSucceeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2317-105">參數</span><span class="sxs-lookup"><span data-stu-id="c2317-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="c2317-106">在其中一個[WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)值，指出當作業封鎖時，主機應採取的動作。</span><span class="sxs-lookup"><span data-stu-id="c2317-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
 `pbSucceeded`  
 <span data-ttu-id="c2317-107">[out] `true` 如果可以輸入關鍵區段，則為，否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="c2317-107">[out] `true` if the critical section can be entered; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2317-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="c2317-108">Return Value</span></span>  
  
|<span data-ttu-id="c2317-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c2317-109">HRESULT</span></span>|<span data-ttu-id="c2317-110">描述</span><span class="sxs-lookup"><span data-stu-id="c2317-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c2317-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c2317-111">S_OK</span></span>|<span data-ttu-id="c2317-112">已成功傳回 `TryEnter`。</span><span class="sxs-lookup"><span data-stu-id="c2317-112">`TryEnter` returned successfully.</span></span>|  
|<span data-ttu-id="c2317-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c2317-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c2317-114">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="c2317-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c2317-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c2317-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c2317-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="c2317-116">The call timed out.</span></span>|  
|<span data-ttu-id="c2317-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c2317-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c2317-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="c2317-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c2317-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c2317-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c2317-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="c2317-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c2317-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c2317-121">E_FAIL</span></span>|<span data-ttu-id="c2317-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="c2317-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c2317-123">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="c2317-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c2317-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="c2317-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2317-125">備註</span><span class="sxs-lookup"><span data-stu-id="c2317-125">Remarks</span></span>  
 <span data-ttu-id="c2317-126">`TryEnter` 會立即傳回，並指出呼叫執行緒是否已進入重要區段。</span><span class="sxs-lookup"><span data-stu-id="c2317-126">`TryEnter` returns immediately and indicates whether the calling thread entered the critical section.</span></span> <span data-ttu-id="c2317-127">這個方法會鏡像 Wind32 `TryEnterCriticalSection` 函數。</span><span class="sxs-lookup"><span data-stu-id="c2317-127">This method mirrors the Wind32 `TryEnterCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2317-128">需求</span><span class="sxs-lookup"><span data-stu-id="c2317-128">Requirements</span></span>  
 <span data-ttu-id="c2317-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c2317-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2317-130">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="c2317-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c2317-131">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c2317-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c2317-132">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2317-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2317-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="c2317-133">See also</span></span>

- [<span data-ttu-id="c2317-134">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="c2317-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="c2317-135">IHostCrst 介面</span><span class="sxs-lookup"><span data-stu-id="c2317-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="c2317-136">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="c2317-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
