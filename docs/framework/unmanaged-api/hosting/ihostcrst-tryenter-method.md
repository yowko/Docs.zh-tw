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
ms.openlocfilehash: 02f36068f12bf0a40e5f0ac477803abfb84c72a9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729525"
---
# <a name="ihostcrsttryenter-method"></a><span data-ttu-id="b6a9f-102">IHostCrst::TryEnter 方法</span><span class="sxs-lookup"><span data-stu-id="b6a9f-102">IHostCrst::TryEnter Method</span></span>

<span data-ttu-id="b6a9f-103">嘗試輸入目前 [IHostCrst](ihostcrst-interface.md) 實例所代表的重要區段。</span><span class="sxs-lookup"><span data-stu-id="b6a9f-103">Attempts to enter the critical section represented by the current [IHostCrst](ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6a9f-104">語法</span><span class="sxs-lookup"><span data-stu-id="b6a9f-104">Syntax</span></span>  
  
```cpp  
HRESULT TryEnter (  
    [in]  DWORD  option,  
    [out] BOOL   *pbSucceeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6a9f-105">參數</span><span class="sxs-lookup"><span data-stu-id="b6a9f-105">Parameters</span></span>  

 `option`  
 <span data-ttu-id="b6a9f-106">在其中一個 [WAIT_OPTION](wait-option-enumeration.md) 值，指出作業封鎖時，主機應該採取的動作。</span><span class="sxs-lookup"><span data-stu-id="b6a9f-106">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
 `pbSucceeded`  
 <span data-ttu-id="b6a9f-107">[out] `true` 如果可輸入重要區段，則為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="b6a9f-107">[out] `true` if the critical section can be entered; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6a9f-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="b6a9f-108">Return Value</span></span>  
  
|<span data-ttu-id="b6a9f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b6a9f-109">HRESULT</span></span>|<span data-ttu-id="b6a9f-110">描述</span><span class="sxs-lookup"><span data-stu-id="b6a9f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b6a9f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b6a9f-111">S_OK</span></span>|<span data-ttu-id="b6a9f-112">`TryEnter` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="b6a9f-112">`TryEnter` returned successfully.</span></span>|  
|<span data-ttu-id="b6a9f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b6a9f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b6a9f-114">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="b6a9f-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b6a9f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b6a9f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b6a9f-116">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="b6a9f-116">The call timed out.</span></span>|  
|<span data-ttu-id="b6a9f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b6a9f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b6a9f-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b6a9f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b6a9f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b6a9f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b6a9f-120">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="b6a9f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b6a9f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b6a9f-121">E_FAIL</span></span>|<span data-ttu-id="b6a9f-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="b6a9f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b6a9f-123">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="b6a9f-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b6a9f-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b6a9f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6a9f-125">備註</span><span class="sxs-lookup"><span data-stu-id="b6a9f-125">Remarks</span></span>  

 <span data-ttu-id="b6a9f-126">`TryEnter` 立即傳回，指出呼叫執行緒是否進入重要區段。</span><span class="sxs-lookup"><span data-stu-id="b6a9f-126">`TryEnter` returns immediately and indicates whether the calling thread entered the critical section.</span></span> <span data-ttu-id="b6a9f-127">這個方法會鏡像 Wind32 `TryEnterCriticalSection` 函數。</span><span class="sxs-lookup"><span data-stu-id="b6a9f-127">This method mirrors the Wind32 `TryEnterCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6a9f-128">需求</span><span class="sxs-lookup"><span data-stu-id="b6a9f-128">Requirements</span></span>  

 <span data-ttu-id="b6a9f-129">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6a9f-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6a9f-130">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b6a9f-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b6a9f-131">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="b6a9f-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6a9f-132">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6a9f-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6a9f-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6a9f-133">See also</span></span>

- [<span data-ttu-id="b6a9f-134">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="b6a9f-134">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="b6a9f-135">IHostCrst 介面</span><span class="sxs-lookup"><span data-stu-id="b6a9f-135">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="b6a9f-136">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="b6a9f-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
