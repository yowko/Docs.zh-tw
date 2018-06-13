---
title: IHostTaskManager::SetCLRTaskManager 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetCLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetCLRTaskManager
helpviewer_keywords:
- IHostTaskManager::SetCLRTaskManager method [.NET Framework hosting]
- SetCLRTaskManager method [.NET Framework hosting]
ms.assetid: ec90ee83-bd4b-408b-9274-62a923ab86a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84501ae5e96a2eab4c5da4d4cb211fc60822e339
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445295"
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="9c2c1-102">IHostTaskManager::SetCLRTaskManager 方法</span><span class="sxs-lookup"><span data-stu-id="9c2c1-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="9c2c1-103">主機提供的介面指標[ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) common language runtime (CLR) 所實作的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9c2c1-103">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c2c1-104">語法</span><span class="sxs-lookup"><span data-stu-id="9c2c1-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c2c1-105">參數</span><span class="sxs-lookup"><span data-stu-id="9c2c1-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="9c2c1-106">[in]指標`ICLRTaskManager`common language runtime 所實作的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9c2c1-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c2c1-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="9c2c1-107">Return Value</span></span>  
  
|<span data-ttu-id="9c2c1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9c2c1-108">HRESULT</span></span>|<span data-ttu-id="9c2c1-109">描述</span><span class="sxs-lookup"><span data-stu-id="9c2c1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9c2c1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9c2c1-110">S_OK</span></span>|<span data-ttu-id="9c2c1-111">`SetCLRTaskManager` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="9c2c1-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="9c2c1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9c2c1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9c2c1-113">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="9c2c1-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9c2c1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9c2c1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9c2c1-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="9c2c1-115">The call timed out.</span></span>|  
|<span data-ttu-id="9c2c1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9c2c1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9c2c1-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="9c2c1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9c2c1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9c2c1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9c2c1-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="9c2c1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9c2c1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9c2c1-120">E_FAIL</span></span>|<span data-ttu-id="9c2c1-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="9c2c1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9c2c1-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="9c2c1-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9c2c1-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="9c2c1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c2c1-124">備註</span><span class="sxs-lookup"><span data-stu-id="9c2c1-124">Remarks</span></span>  
 <span data-ttu-id="9c2c1-125">執行階段呼叫`SetCLRTaskManager`為主機提供的介面指標`ICLRTaskManager`執行個體。</span><span class="sxs-lookup"><span data-stu-id="9c2c1-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c2c1-126">需求</span><span class="sxs-lookup"><span data-stu-id="9c2c1-126">Requirements</span></span>  
 <span data-ttu-id="9c2c1-127">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9c2c1-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c2c1-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9c2c1-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9c2c1-129">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9c2c1-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9c2c1-130">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c2c1-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c2c1-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c2c1-131">See Also</span></span>  
 [<span data-ttu-id="9c2c1-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="9c2c1-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="9c2c1-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="9c2c1-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="9c2c1-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="9c2c1-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="9c2c1-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="9c2c1-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
