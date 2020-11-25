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
ms.openlocfilehash: 0752afb42b8c512450b047a5e2e7e1ff34533487
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729573"
---
# <a name="ihostcrstleave-method"></a><span data-ttu-id="2489c-102">IHostCrst::Leave 方法</span><span class="sxs-lookup"><span data-stu-id="2489c-102">IHostCrst::Leave Method</span></span>

<span data-ttu-id="2489c-103">保留目前 [IHostCrst](ihostcrst-interface.md)實例所代表的重要區段。</span><span class="sxs-lookup"><span data-stu-id="2489c-103">Leaves the critical section that is represented by the current instance of [IHostCrst](ihostcrst-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2489c-104">語法</span><span class="sxs-lookup"><span data-stu-id="2489c-104">Syntax</span></span>  
  
```cpp  
HRESULT Leave ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2489c-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="2489c-105">Return Value</span></span>  
  
|<span data-ttu-id="2489c-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2489c-106">HRESULT</span></span>|<span data-ttu-id="2489c-107">描述</span><span class="sxs-lookup"><span data-stu-id="2489c-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2489c-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="2489c-108">S_OK</span></span>|<span data-ttu-id="2489c-109">`Leave` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="2489c-109">`Leave` returned successfully.</span></span>|  
|<span data-ttu-id="2489c-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2489c-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2489c-111">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="2489c-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2489c-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2489c-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2489c-113">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="2489c-113">The call timed out.</span></span>|  
|<span data-ttu-id="2489c-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2489c-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2489c-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="2489c-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2489c-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2489c-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2489c-117">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="2489c-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2489c-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2489c-118">E_FAIL</span></span>|<span data-ttu-id="2489c-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="2489c-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2489c-120">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="2489c-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2489c-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="2489c-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2489c-122">備註</span><span class="sxs-lookup"><span data-stu-id="2489c-122">Remarks</span></span>  

 <span data-ttu-id="2489c-123">`Leave` 允許 CLR 直接與主機的執行緒進行通訊，而不是使用對應的 Win32 `LeaveCriticalSection` 函數。</span><span class="sxs-lookup"><span data-stu-id="2489c-123">`Leave` allows the CLR to communicate directly with the host's threading implementation, rather than using the corresponding Win32 `LeaveCriticalSection` function.</span></span> <span data-ttu-id="2489c-124">取得目前實例所代表之重要區段擁有權的執行緒， `IHostCrst` `Leave` 每次進入該重要區段時，都必須呼叫一次。</span><span class="sxs-lookup"><span data-stu-id="2489c-124">A thread that takes ownership of the critical section represented by the current `IHostCrst` instance must call `Leave` once for each time it enters that critical section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2489c-125">需求</span><span class="sxs-lookup"><span data-stu-id="2489c-125">Requirements</span></span>  

 <span data-ttu-id="2489c-126">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2489c-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2489c-127">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="2489c-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2489c-128">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="2489c-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2489c-129">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2489c-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2489c-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2489c-130">See also</span></span>

- [<span data-ttu-id="2489c-131">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="2489c-131">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="2489c-132">IHostCrst 介面</span><span class="sxs-lookup"><span data-stu-id="2489c-132">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="2489c-133">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="2489c-133">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
