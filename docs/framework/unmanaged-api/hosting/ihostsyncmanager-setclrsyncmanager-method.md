---
title: IHostSyncManager::SetCLRSyncManager 方法
ms.date: 03/30/2017
api_name:
- IHostSyncManager.SetCLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::SetCLRSyncManager
helpviewer_keywords:
- IHostSyncManager::SetCLRSyncManager method [.NET Framework hosting]
- SetCLRSyncManager method [.NET Framework hosting]
ms.assetid: 2b8bbe76-a45d-4989-bacb-11df42f8798c
topic_type:
- apiref
ms.openlocfilehash: 79a41b6705b41414f0926c2ed819e437ecfb51d5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714818"
---
# <a name="ihostsyncmanagersetclrsyncmanager-method"></a><span data-ttu-id="542c1-102">IHostSyncManager::SetCLRSyncManager 方法</span><span class="sxs-lookup"><span data-stu-id="542c1-102">IHostSyncManager::SetCLRSyncManager Method</span></span>

<span data-ttu-id="542c1-103">設定要與目前[IHostSyncManager](ihostsyncmanager-interface.md)實例相關聯的[ICLRSyncManager](iclrsyncmanager-interface.md)實例。</span><span class="sxs-lookup"><span data-stu-id="542c1-103">Sets the [ICLRSyncManager](iclrsyncmanager-interface.md) instance to associate with the current [IHostSyncManager](ihostsyncmanager-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="542c1-104">語法</span><span class="sxs-lookup"><span data-stu-id="542c1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRSyncManager (  
    [in] ICLRSyncManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="542c1-105">參數</span><span class="sxs-lookup"><span data-stu-id="542c1-105">Parameters</span></span>  

 `pManager`  
 <span data-ttu-id="542c1-106">在 `ICLRSyncManager` Common language runtime (CLR) 所提供的實例指標。</span><span class="sxs-lookup"><span data-stu-id="542c1-106">[in] A pointer to an `ICLRSyncManager` instance supplied by the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="542c1-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="542c1-107">Return Value</span></span>  
  
|<span data-ttu-id="542c1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="542c1-108">HRESULT</span></span>|<span data-ttu-id="542c1-109">描述</span><span class="sxs-lookup"><span data-stu-id="542c1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="542c1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="542c1-110">S_OK</span></span>|<span data-ttu-id="542c1-111">`SetCLRSyncManager` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="542c1-111">`SetCLRSyncManager` returned successfully.</span></span>|  
|<span data-ttu-id="542c1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="542c1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="542c1-113">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="542c1-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="542c1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="542c1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="542c1-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="542c1-115">The call timed out.</span></span>|  
|<span data-ttu-id="542c1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="542c1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="542c1-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="542c1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="542c1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="542c1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="542c1-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="542c1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="542c1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="542c1-120">E_FAIL</span></span>|<span data-ttu-id="542c1-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="542c1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="542c1-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="542c1-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="542c1-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="542c1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="542c1-124">備註</span><span class="sxs-lookup"><span data-stu-id="542c1-124">Remarks</span></span>  

 <span data-ttu-id="542c1-125">為了促進主機和 CLR 之間的通訊，裝載介面通常是成對的。</span><span class="sxs-lookup"><span data-stu-id="542c1-125">To facilitate communication between the host and the CLR, hosting interfaces generally come in pairs.</span></span> <span data-ttu-id="542c1-126">此配對的其中一個成員是由主機所執行，而另一個成員是由 CLR 所執行。</span><span class="sxs-lookup"><span data-stu-id="542c1-126">One member of the pair is implemented by the host, and the other member is implemented by the CLR.</span></span> <span data-ttu-id="542c1-127">在主機端的執行中， `IHostSyncManager` 介面會對應到 `ICLRSyncManager` CLR 所執行的介面。</span><span class="sxs-lookup"><span data-stu-id="542c1-127">As a host-side implementation, the `IHostSyncManager` interface corresponds to the `ICLRSyncManager` interface implemented by the CLR.</span></span> <span data-ttu-id="542c1-128">CLR 會呼叫 `SetCLRSyncManager` ，以提供 `ICLRSyncManager` 主控制項的實例，以與目前的 `IHostSyncManager` 實例產生關聯。</span><span class="sxs-lookup"><span data-stu-id="542c1-128">The CLR calls `SetCLRSyncManager` to supply an `ICLRSyncManager` instance for the host to associate with the current `IHostSyncManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="542c1-129">需求</span><span class="sxs-lookup"><span data-stu-id="542c1-129">Requirements</span></span>  

 <span data-ttu-id="542c1-130">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="542c1-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="542c1-131">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="542c1-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="542c1-132">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="542c1-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="542c1-133">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="542c1-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="542c1-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="542c1-134">See also</span></span>

- [<span data-ttu-id="542c1-135">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="542c1-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="542c1-136">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="542c1-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
