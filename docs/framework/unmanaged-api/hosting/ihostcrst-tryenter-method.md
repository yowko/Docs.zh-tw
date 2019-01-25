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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9c463b055f5bd7d965e2df9428ee7c4a1e612dd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54675182"
---
# <a name="ihostcrsttryenter-method"></a><span data-ttu-id="a84fb-102">IHostCrst::TryEnter 方法</span><span class="sxs-lookup"><span data-stu-id="a84fb-102">IHostCrst::TryEnter Method</span></span>
<span data-ttu-id="a84fb-103">嘗試進入重要區段表示由目前[IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)執行個體。</span><span class="sxs-lookup"><span data-stu-id="a84fb-103">Attempts to enter the critical section represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a84fb-104">語法</span><span class="sxs-lookup"><span data-stu-id="a84fb-104">Syntax</span></span>  
  
```  
HRESULT TryEnter (  
    [in]  DWORD  option,  
    [out] BOOL   *pbSucceeded  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a84fb-105">參數</span><span class="sxs-lookup"><span data-stu-id="a84fb-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="a84fb-106">[in]其中一個[WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)值，指出如果，主應用程式應執行的動作作業封鎖。</span><span class="sxs-lookup"><span data-stu-id="a84fb-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
 `pbSucceeded`  
 <span data-ttu-id="a84fb-107">[out]`true`重要區段可以是輸入，否則如果`false`。</span><span class="sxs-lookup"><span data-stu-id="a84fb-107">[out] `true` if the critical section can be entered; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a84fb-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="a84fb-108">Return Value</span></span>  
  
|<span data-ttu-id="a84fb-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a84fb-109">HRESULT</span></span>|<span data-ttu-id="a84fb-110">描述</span><span class="sxs-lookup"><span data-stu-id="a84fb-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a84fb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a84fb-111">S_OK</span></span>|<span data-ttu-id="a84fb-112">`TryEnter` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="a84fb-112">`TryEnter` returned successfully.</span></span>|  
|<span data-ttu-id="a84fb-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a84fb-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a84fb-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="a84fb-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a84fb-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a84fb-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a84fb-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="a84fb-116">The call timed out.</span></span>|  
|<span data-ttu-id="a84fb-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a84fb-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a84fb-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="a84fb-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a84fb-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a84fb-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a84fb-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="a84fb-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a84fb-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a84fb-121">E_FAIL</span></span>|<span data-ttu-id="a84fb-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="a84fb-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a84fb-123">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="a84fb-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a84fb-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a84fb-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a84fb-125">備註</span><span class="sxs-lookup"><span data-stu-id="a84fb-125">Remarks</span></span>  
 <span data-ttu-id="a84fb-126">`TryEnter` 會立即傳回，表示呼叫執行緒是否進入重要區段。</span><span class="sxs-lookup"><span data-stu-id="a84fb-126">`TryEnter` returns immediately and indicates whether the calling thread entered the critical section.</span></span> <span data-ttu-id="a84fb-127">這個方法反映 Wind32`TryEnterCriticalSection`函式。</span><span class="sxs-lookup"><span data-stu-id="a84fb-127">This method mirrors the Wind32 `TryEnterCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a84fb-128">需求</span><span class="sxs-lookup"><span data-stu-id="a84fb-128">Requirements</span></span>  
 <span data-ttu-id="a84fb-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a84fb-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a84fb-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a84fb-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a84fb-131">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a84fb-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a84fb-132">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a84fb-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a84fb-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a84fb-133">See also</span></span>
- [<span data-ttu-id="a84fb-134">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="a84fb-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="a84fb-135">IHostCrst 介面</span><span class="sxs-lookup"><span data-stu-id="a84fb-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="a84fb-136">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="a84fb-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
