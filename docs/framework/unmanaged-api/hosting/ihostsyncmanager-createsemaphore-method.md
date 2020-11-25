---
title: IHostSyncManager::CreateSemaphore 方法
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateSemaphore
helpviewer_keywords:
- CreateSemaphore method [.NET Framework hosting]
- IHostSyncManager::CreateSemaphore method [.NET Framework hosting]
ms.assetid: 37679e94-5ff9-4173-8fa5-457febeb89bf
topic_type:
- apiref
ms.openlocfilehash: 9af38a58ce8786c56d9f50089605dc994167497e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722124"
---
# <a name="ihostsyncmanagercreatesemaphore-method"></a><span data-ttu-id="979e9-102">IHostSyncManager::CreateSemaphore 方法</span><span class="sxs-lookup"><span data-stu-id="979e9-102">IHostSyncManager::CreateSemaphore Method</span></span>

<span data-ttu-id="979e9-103">建立 common language runtime (CLR) 的 [IHostSemaphore](ihostsemaphore-interface.md) 物件，以做為等候事件的信號。</span><span class="sxs-lookup"><span data-stu-id="979e9-103">Creates an [IHostSemaphore](ihostsemaphore-interface.md) object for the common language runtime (CLR) to use as a semaphore for wait events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="979e9-104">語法</span><span class="sxs-lookup"><span data-stu-id="979e9-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateSemaphore (  
    [in]  DWORD dwInitial,  
    [in]  DWORD dwMax,  
    [out] IHostSemaphore **ppSemaphore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="979e9-105">參數</span><span class="sxs-lookup"><span data-stu-id="979e9-105">Parameters</span></span>  

 `dwInitial`  
 <span data-ttu-id="979e9-106">在的初始計數 `ppSemaphore` 。</span><span class="sxs-lookup"><span data-stu-id="979e9-106">[in] The initial count for `ppSemaphore`.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="979e9-107">在的最大計數 `ppSemaphore` 。</span><span class="sxs-lookup"><span data-stu-id="979e9-107">[in] The maximum count for `ppSemaphore`.</span></span>  
  
 `ppSemaphore`  
 <span data-ttu-id="979e9-108">擴展實例位址的指標 `IHostSemaphore` ，如果無法建立信號，則為 null。</span><span class="sxs-lookup"><span data-stu-id="979e9-108">[out] A pointer to the address of an `IHostSemaphore` instance, or null if the semaphore could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="979e9-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="979e9-109">Return Value</span></span>  
  
|<span data-ttu-id="979e9-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="979e9-110">HRESULT</span></span>|<span data-ttu-id="979e9-111">描述</span><span class="sxs-lookup"><span data-stu-id="979e9-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="979e9-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="979e9-112">S_OK</span></span>|<span data-ttu-id="979e9-113">`CreateSemaphore` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="979e9-113">`CreateSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="979e9-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="979e9-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="979e9-115">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="979e9-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="979e9-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="979e9-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="979e9-117">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="979e9-117">The call timed out.</span></span>|  
|<span data-ttu-id="979e9-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="979e9-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="979e9-119">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="979e9-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="979e9-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="979e9-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="979e9-121">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="979e9-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="979e9-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="979e9-122">E_FAIL</span></span>|<span data-ttu-id="979e9-123">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="979e9-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="979e9-124">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="979e9-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="979e9-125">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="979e9-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="979e9-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="979e9-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="979e9-127">沒有足夠的記憶體可用來建立要求的事件物件。</span><span class="sxs-lookup"><span data-stu-id="979e9-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="979e9-128">備註</span><span class="sxs-lookup"><span data-stu-id="979e9-128">Remarks</span></span>  

 <span data-ttu-id="979e9-129">`CreateSemaphore` 鏡像具有相同名稱的 Win32 函數。</span><span class="sxs-lookup"><span data-stu-id="979e9-129">`CreateSemaphore` mirrors the Win32 function that has the same name.</span></span> <span data-ttu-id="979e9-130">`dwInitial`和 `dwMax` 參數分別針對信號計數使用相同的語義作為 Win32 `lInitialCount` 和 `lMaximumCount` 參數。</span><span class="sxs-lookup"><span data-stu-id="979e9-130">The `dwInitial` and `dwMax` parameters use the same semantics for the semaphore count as the Win32 `lInitialCount` and `lMaximumCount` parameters, respectively.</span></span> <span data-ttu-id="979e9-131">`dwInitial` 必須介於零到 `dwMax` （含）之間。</span><span class="sxs-lookup"><span data-stu-id="979e9-131">`dwInitial` must be between zero and `dwMax`, inclusive.</span></span> <span data-ttu-id="979e9-132">`dwMax` 必須大於零。</span><span class="sxs-lookup"><span data-stu-id="979e9-132">`dwMax` must be greater than zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="979e9-133">需求</span><span class="sxs-lookup"><span data-stu-id="979e9-133">Requirements</span></span>  

 <span data-ttu-id="979e9-134">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="979e9-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="979e9-135">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="979e9-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="979e9-136">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="979e9-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="979e9-137">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="979e9-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="979e9-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="979e9-138">See also</span></span>

- [<span data-ttu-id="979e9-139">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="979e9-139">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="979e9-140">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="979e9-140">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="979e9-141">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="979e9-141">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
