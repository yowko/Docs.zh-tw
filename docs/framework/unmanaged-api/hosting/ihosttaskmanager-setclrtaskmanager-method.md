---
title: "IHostTaskManager::SetCLRTaskManager 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.SetCLRTaskManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::SetCLRTaskManager
helpviewer_keywords:
- IHostTaskManager::SetCLRTaskManager method [.NET Framework hosting]
- SetCLRTaskManager method [.NET Framework hosting]
ms.assetid: ec90ee83-bd4b-408b-9274-62a923ab86a1
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9f009fee3f9bc439ce61d859759870f9cbb54f09
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="1155f-102">IHostTaskManager::SetCLRTaskManager 方法</span><span class="sxs-lookup"><span data-stu-id="1155f-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="1155f-103">主機提供的介面指標[ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) common language runtime (CLR) 所實作的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1155f-103">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1155f-104">語法</span><span class="sxs-lookup"><span data-stu-id="1155f-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1155f-105">參數</span><span class="sxs-lookup"><span data-stu-id="1155f-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="1155f-106">[in]指標`ICLRTaskManager`common language runtime 所實作的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1155f-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1155f-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="1155f-107">Return Value</span></span>  
  
|<span data-ttu-id="1155f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1155f-108">HRESULT</span></span>|<span data-ttu-id="1155f-109">描述</span><span class="sxs-lookup"><span data-stu-id="1155f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1155f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1155f-110">S_OK</span></span>|<span data-ttu-id="1155f-111">`SetCLRTaskManager`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="1155f-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="1155f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1155f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1155f-113">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="1155f-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1155f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1155f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1155f-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="1155f-115">The call timed out.</span></span>|  
|<span data-ttu-id="1155f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1155f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1155f-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="1155f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1155f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1155f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1155f-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="1155f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1155f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1155f-120">E_FAIL</span></span>|<span data-ttu-id="1155f-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="1155f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1155f-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="1155f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1155f-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="1155f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1155f-124">備註</span><span class="sxs-lookup"><span data-stu-id="1155f-124">Remarks</span></span>  
 <span data-ttu-id="1155f-125">執行階段呼叫`SetCLRTaskManager`為主機提供的介面指標`ICLRTaskManager`執行個體。</span><span class="sxs-lookup"><span data-stu-id="1155f-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1155f-126">需求</span><span class="sxs-lookup"><span data-stu-id="1155f-126">Requirements</span></span>  
 <span data-ttu-id="1155f-127">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1155f-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1155f-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1155f-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1155f-129">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1155f-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1155f-130">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1155f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1155f-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="1155f-131">See Also</span></span>  
 [<span data-ttu-id="1155f-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="1155f-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="1155f-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="1155f-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="1155f-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="1155f-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="1155f-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="1155f-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
