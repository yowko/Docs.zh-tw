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
ms.openlocfilehash: ae5561abb7cd0770fd5b7f290a4aa8dff85b6150
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441648"
---
# <a name="ihostcrstleave-method"></a><span data-ttu-id="5da7c-102">IHostCrst::Leave 方法</span><span class="sxs-lookup"><span data-stu-id="5da7c-102">IHostCrst::Leave Method</span></span>
<span data-ttu-id="5da7c-103">離開關鍵區段的目前執行個體所表示之[IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="5da7c-103">Leaves the critical section that is represented by the current instance of [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5da7c-104">語法</span><span class="sxs-lookup"><span data-stu-id="5da7c-104">Syntax</span></span>  
  
```  
HRESULT Leave ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="5da7c-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="5da7c-105">Return Value</span></span>  
  
|<span data-ttu-id="5da7c-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5da7c-106">HRESULT</span></span>|<span data-ttu-id="5da7c-107">描述</span><span class="sxs-lookup"><span data-stu-id="5da7c-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5da7c-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="5da7c-108">S_OK</span></span>|<span data-ttu-id="5da7c-109">`Leave` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="5da7c-109">`Leave` returned successfully.</span></span>|  
|<span data-ttu-id="5da7c-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5da7c-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5da7c-111">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="5da7c-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5da7c-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5da7c-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5da7c-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="5da7c-113">The call timed out.</span></span>|  
|<span data-ttu-id="5da7c-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5da7c-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5da7c-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="5da7c-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5da7c-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5da7c-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5da7c-117">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="5da7c-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5da7c-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5da7c-118">E_FAIL</span></span>|<span data-ttu-id="5da7c-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="5da7c-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5da7c-120">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="5da7c-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5da7c-121">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="5da7c-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5da7c-122">備註</span><span class="sxs-lookup"><span data-stu-id="5da7c-122">Remarks</span></span>  
 <span data-ttu-id="5da7c-123">`Leave` 允許可直接與主機的執行緒實作，而不是使用對應的 Win32 溝通 CLR`LeaveCriticalSection`函式。</span><span class="sxs-lookup"><span data-stu-id="5da7c-123">`Leave` allows the CLR to communicate directly with the host's threading implementation, rather than using the corresponding Win32 `LeaveCriticalSection` function.</span></span> <span data-ttu-id="5da7c-124">取得擁有權的重要區段表示由目前執行緒`IHostCrst`執行個體必須呼叫`Leave`一旦它在每次進入該重要區段。</span><span class="sxs-lookup"><span data-stu-id="5da7c-124">A thread that takes ownership of the critical section represented by the current `IHostCrst` instance must call `Leave` once for each time it enters that critical section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5da7c-125">需求</span><span class="sxs-lookup"><span data-stu-id="5da7c-125">Requirements</span></span>  
 <span data-ttu-id="5da7c-126">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5da7c-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5da7c-127">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5da7c-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5da7c-128">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5da7c-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5da7c-129">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5da7c-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5da7c-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5da7c-130">See Also</span></span>  
 [<span data-ttu-id="5da7c-131">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="5da7c-131">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="5da7c-132">IHostCrst 介面</span><span class="sxs-lookup"><span data-stu-id="5da7c-132">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="5da7c-133">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="5da7c-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
