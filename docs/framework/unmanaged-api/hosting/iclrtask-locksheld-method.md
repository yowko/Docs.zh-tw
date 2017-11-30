---
title: "ICLRTask::LocksHeld 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.LocksHeld
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::LocksHeld
helpviewer_keywords:
- LocksHeld method [.NET Framework hosting]
- ICLRTask::LocksHeld method [.NET Framework hosting]
ms.assetid: e88a4dc3-02cc-4703-a474-292b71c40657
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2d51fded9f2e475759f2912aea659d272ce08855
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtasklocksheld-method"></a><span data-ttu-id="15d85-102">ICLRTask::LocksHeld 方法</span><span class="sxs-lookup"><span data-stu-id="15d85-102">ICLRTask::LocksHeld Method</span></span>
<span data-ttu-id="15d85-103">取得目前工作上保留的鎖定數目。</span><span class="sxs-lookup"><span data-stu-id="15d85-103">Gets the number of locks currently held on the task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15d85-104">語法</span><span class="sxs-lookup"><span data-stu-id="15d85-104">Syntax</span></span>  
  
```  
HRESULT LocksHeld (  
    [out] SIZE_T *pLockCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="15d85-105">參數</span><span class="sxs-lookup"><span data-stu-id="15d85-105">Parameters</span></span>  
 `pLockCount`  
 <span data-ttu-id="15d85-106">[out]在方法呼叫時，工作上持有鎖定的數目。</span><span class="sxs-lookup"><span data-stu-id="15d85-106">[out] The number of locks held on the task at the time of the method call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="15d85-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="15d85-107">Return Value</span></span>  
  
|<span data-ttu-id="15d85-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="15d85-108">HRESULT</span></span>|<span data-ttu-id="15d85-109">描述</span><span class="sxs-lookup"><span data-stu-id="15d85-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="15d85-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="15d85-110">S_OK</span></span>|<span data-ttu-id="15d85-111">`LocksHeld`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="15d85-111">`LocksHeld` returned successfully.</span></span>|  
|<span data-ttu-id="15d85-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="15d85-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="15d85-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="15d85-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="15d85-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="15d85-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="15d85-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="15d85-115">The call timed out.</span></span>|  
|<span data-ttu-id="15d85-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="15d85-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="15d85-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="15d85-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="15d85-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="15d85-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="15d85-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="15d85-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="15d85-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="15d85-120">E_FAIL</span></span>|<span data-ttu-id="15d85-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="15d85-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="15d85-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="15d85-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="15d85-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="15d85-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="15d85-124">需求</span><span class="sxs-lookup"><span data-stu-id="15d85-124">Requirements</span></span>  
 <span data-ttu-id="15d85-125">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="15d85-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15d85-126">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="15d85-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="15d85-127">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="15d85-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="15d85-128">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15d85-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15d85-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15d85-129">See Also</span></span>  
 [<span data-ttu-id="15d85-130">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="15d85-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="15d85-131">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="15d85-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="15d85-132">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="15d85-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="15d85-133">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="15d85-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
