---
title: IHostCrst::Enter 方法
ms.date: 03/30/2017
api_name:
- IHostCrst.Enter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Enter
helpviewer_keywords:
- Enter method [.NET Framework hosting]
- IHostCrst::Enter method [.NET Framework hosting]
ms.assetid: 100dd7eb-7053-4295-9bb3-32ba47f6ec79
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a54135a0daff3f207d1365d2c27335440f7f1fb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763785"
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="bf84d-102">IHostCrst::Enter 方法</span><span class="sxs-lookup"><span data-stu-id="bf84d-102">IHostCrst::Enter Method</span></span>
<span data-ttu-id="bf84d-103">進入重要區段表示由目前[IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)執行個體。</span><span class="sxs-lookup"><span data-stu-id="bf84d-103">Enters the critical section that is represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf84d-104">語法</span><span class="sxs-lookup"><span data-stu-id="bf84d-104">Syntax</span></span>  
  
```cpp  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf84d-105">參數</span><span class="sxs-lookup"><span data-stu-id="bf84d-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="bf84d-106">[in]其中一個[WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)值，指出如果，主應用程式應執行的動作作業封鎖。</span><span class="sxs-lookup"><span data-stu-id="bf84d-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf84d-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="bf84d-107">Return Value</span></span>  
  
|<span data-ttu-id="bf84d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bf84d-108">HRESULT</span></span>|<span data-ttu-id="bf84d-109">描述</span><span class="sxs-lookup"><span data-stu-id="bf84d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bf84d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bf84d-110">S_OK</span></span>|<span data-ttu-id="bf84d-111">`Enter` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="bf84d-111">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="bf84d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bf84d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bf84d-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="bf84d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bf84d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bf84d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bf84d-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="bf84d-115">The call timed out.</span></span>|  
|<span data-ttu-id="bf84d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bf84d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bf84d-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="bf84d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bf84d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bf84d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bf84d-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="bf84d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bf84d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bf84d-120">E_FAIL</span></span>|<span data-ttu-id="bf84d-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="bf84d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bf84d-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="bf84d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bf84d-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="bf84d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf84d-124">備註</span><span class="sxs-lookup"><span data-stu-id="bf84d-124">Remarks</span></span>  
 <span data-ttu-id="bf84d-125">`Enter` 鏡像處理 Win32`EnterCriticalSection`函式。</span><span class="sxs-lookup"><span data-stu-id="bf84d-125">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf84d-126">這個方法不會傳回，直到在進入重要區段。</span><span class="sxs-lookup"><span data-stu-id="bf84d-126">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf84d-127">需求</span><span class="sxs-lookup"><span data-stu-id="bf84d-127">Requirements</span></span>  
 <span data-ttu-id="bf84d-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bf84d-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf84d-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bf84d-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bf84d-130">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="bf84d-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bf84d-131">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf84d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf84d-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf84d-132">See also</span></span>

- [<span data-ttu-id="bf84d-133">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="bf84d-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="bf84d-134">IHostCrst 介面</span><span class="sxs-lookup"><span data-stu-id="bf84d-134">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="bf84d-135">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="bf84d-135">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
