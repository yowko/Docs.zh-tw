---
title: "IHostSyncManager::SetCLRSyncManager 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.SetCLRSyncManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::SetCLRSyncManager
helpviewer_keywords:
- IHostSyncManager::SetCLRSyncManager method [.NET Framework hosting]
- SetCLRSyncManager method [.NET Framework hosting]
ms.assetid: 2b8bbe76-a45d-4989-bacb-11df42f8798c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45899e3cb6a08aef6a9b8df197541c4d0233d92d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanagersetclrsyncmanager-method"></a><span data-ttu-id="51748-102">IHostSyncManager::SetCLRSyncManager 方法</span><span class="sxs-lookup"><span data-stu-id="51748-102">IHostSyncManager::SetCLRSyncManager Method</span></span>
<span data-ttu-id="51748-103">設定[ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)與目前的執行個體[IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)執行個體。</span><span class="sxs-lookup"><span data-stu-id="51748-103">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current [IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51748-104">語法</span><span class="sxs-lookup"><span data-stu-id="51748-104">Syntax</span></span>  
  
```  
HRESULT SetCLRSyncManager (  
    [in] ICLRSyncManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="51748-105">參數</span><span class="sxs-lookup"><span data-stu-id="51748-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="51748-106">[in]指標`ICLRSyncManager`common language runtime (CLR) 所提供的執行個體。</span><span class="sxs-lookup"><span data-stu-id="51748-106">[in] A pointer to an `ICLRSyncManager` instance supplied by the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51748-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="51748-107">Return Value</span></span>  
  
|<span data-ttu-id="51748-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="51748-108">HRESULT</span></span>|<span data-ttu-id="51748-109">描述</span><span class="sxs-lookup"><span data-stu-id="51748-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="51748-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="51748-110">S_OK</span></span>|<span data-ttu-id="51748-111">`SetCLRSyncManager`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="51748-111">`SetCLRSyncManager` returned successfully.</span></span>|  
|<span data-ttu-id="51748-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="51748-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="51748-113">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="51748-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="51748-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="51748-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="51748-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="51748-115">The call timed out.</span></span>|  
|<span data-ttu-id="51748-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="51748-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="51748-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="51748-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="51748-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="51748-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="51748-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="51748-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="51748-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="51748-120">E_FAIL</span></span>|<span data-ttu-id="51748-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="51748-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="51748-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="51748-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="51748-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="51748-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51748-124">備註</span><span class="sxs-lookup"><span data-stu-id="51748-124">Remarks</span></span>  
 <span data-ttu-id="51748-125">若要簡化在主機與 CLR 之間的通訊，裝載介面通常成對出現。</span><span class="sxs-lookup"><span data-stu-id="51748-125">To facilitate communication between the host and the CLR, hosting interfaces generally come in pairs.</span></span> <span data-ttu-id="51748-126">一個配對成員的藉由在主機和其他成員由 CLR 實作。</span><span class="sxs-lookup"><span data-stu-id="51748-126">One member of the pair is implemented by the host, and the other member is implemented by the CLR.</span></span> <span data-ttu-id="51748-127">主機端實作中，為`IHostSyncManager`介面對應至`ICLRSyncManager`CLR 所實作的介面。</span><span class="sxs-lookup"><span data-stu-id="51748-127">As a host-side implementation, the `IHostSyncManager` interface corresponds to the `ICLRSyncManager` interface implemented by the CLR.</span></span> <span data-ttu-id="51748-128">CLR 會呼叫`SetCLRSyncManager`提供`ICLRSyncManager`主機與目前的執行個體`IHostSyncManager`執行個體。</span><span class="sxs-lookup"><span data-stu-id="51748-128">The CLR calls `SetCLRSyncManager` to supply an `ICLRSyncManager` instance for the host to associate with the current `IHostSyncManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51748-129">需求</span><span class="sxs-lookup"><span data-stu-id="51748-129">Requirements</span></span>  
 <span data-ttu-id="51748-130">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="51748-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51748-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="51748-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="51748-132">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="51748-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="51748-133">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51748-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51748-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51748-134">See Also</span></span>  
 [<span data-ttu-id="51748-135">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="51748-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="51748-136">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="51748-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
