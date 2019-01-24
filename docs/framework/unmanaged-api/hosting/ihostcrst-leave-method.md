---
title: IHostCrst::Leave 方法
ms.date: 03/30/2017
api_name:
- IHostCrst.Leave
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Leave
helpviewer_keywords:
- IHostCrst::Leave method [.NET Framework hosting]
- Leave method [.NET Framework hosting]
ms.assetid: dfc51d9e-b36d-4dba-9ea1-4f63fa0601ae
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e474a3cf92e818a3e58f4e97786c17af336fa791
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549924"
---
# <a name="ihostcrstleave-method"></a><span data-ttu-id="3e457-102">IHostCrst::Leave 方法</span><span class="sxs-lookup"><span data-stu-id="3e457-102">IHostCrst::Leave Method</span></span>
<span data-ttu-id="3e457-103">離開關鍵區段所表示的目前執行個體[IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="3e457-103">Leaves the critical section that is represented by the current instance of [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e457-104">語法</span><span class="sxs-lookup"><span data-stu-id="3e457-104">Syntax</span></span>  
  
```  
HRESULT Leave ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="3e457-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="3e457-105">Return Value</span></span>  
  
|<span data-ttu-id="3e457-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3e457-106">HRESULT</span></span>|<span data-ttu-id="3e457-107">描述</span><span class="sxs-lookup"><span data-stu-id="3e457-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3e457-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="3e457-108">S_OK</span></span>|<span data-ttu-id="3e457-109">`Leave` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="3e457-109">`Leave` returned successfully.</span></span>|  
|<span data-ttu-id="3e457-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3e457-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3e457-111">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="3e457-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3e457-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3e457-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3e457-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="3e457-113">The call timed out.</span></span>|  
|<span data-ttu-id="3e457-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3e457-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3e457-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="3e457-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3e457-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3e457-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3e457-117">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="3e457-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3e457-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3e457-118">E_FAIL</span></span>|<span data-ttu-id="3e457-119">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="3e457-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3e457-120">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="3e457-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3e457-121">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="3e457-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e457-122">備註</span><span class="sxs-lookup"><span data-stu-id="3e457-122">Remarks</span></span>  
 <span data-ttu-id="3e457-123">`Leave` 可讓 CLR 直接通訊主機的執行緒實作，而不是使用對應的 Win32`LeaveCriticalSection`函式。</span><span class="sxs-lookup"><span data-stu-id="3e457-123">`Leave` allows the CLR to communicate directly with the host's threading implementation, rather than using the corresponding Win32 `LeaveCriticalSection` function.</span></span> <span data-ttu-id="3e457-124">取得擁有權的重要區段表示由目前的執行緒`IHostCrst`執行個體必須呼叫`Leave`之後每次進入該重要區段。</span><span class="sxs-lookup"><span data-stu-id="3e457-124">A thread that takes ownership of the critical section represented by the current `IHostCrst` instance must call `Leave` once for each time it enters that critical section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e457-125">需求</span><span class="sxs-lookup"><span data-stu-id="3e457-125">Requirements</span></span>  
 <span data-ttu-id="3e457-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3e457-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e457-127">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3e457-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3e457-128">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3e457-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e457-129">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e457-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e457-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e457-130">See also</span></span>
- [<span data-ttu-id="3e457-131">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="3e457-131">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="3e457-132">IHostCrst 介面</span><span class="sxs-lookup"><span data-stu-id="3e457-132">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="3e457-133">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="3e457-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
