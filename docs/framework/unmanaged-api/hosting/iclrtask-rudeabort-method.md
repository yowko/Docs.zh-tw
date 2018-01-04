---
title: "ICLRTask::RudeAbort 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.RudeAbort
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::RudeAbort
helpviewer_keywords:
- RudeAbort method, ICLRTask interface [.NET Framework hosting]
- ICLRTask::RudeAbort method [.NET Framework hosting]
ms.assetid: b5785468-fcd7-4cc3-8a5d-8796337b53fc
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f48de1fb44d978b1d9c8960c3e44c360b0801e27
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="a1bd6-102">ICLRTask::RudeAbort 方法</span><span class="sxs-lookup"><span data-stu-id="a1bd6-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="a1bd6-103">指示 common language runtime (CLR)，以中止表示由目前的工作[ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)立即且無條件地執行個體。</span><span class="sxs-lookup"><span data-stu-id="a1bd6-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1bd6-104">語法</span><span class="sxs-lookup"><span data-stu-id="a1bd6-104">Syntax</span></span>  
  
```  
HRESULT RudeAbort ();   
```  
  
## <a name="return-value"></a><span data-ttu-id="a1bd6-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="a1bd6-105">Return Value</span></span>  
  
|<span data-ttu-id="a1bd6-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a1bd6-106">HRESULT</span></span>|<span data-ttu-id="a1bd6-107">描述</span><span class="sxs-lookup"><span data-stu-id="a1bd6-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a1bd6-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a1bd6-108">S_OK</span></span>|<span data-ttu-id="a1bd6-109">`RudeAbort`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="a1bd6-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="a1bd6-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a1bd6-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a1bd6-111">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="a1bd6-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a1bd6-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a1bd6-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a1bd6-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="a1bd6-113">The call timed out.</span></span>|  
|<span data-ttu-id="a1bd6-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a1bd6-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a1bd6-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="a1bd6-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a1bd6-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a1bd6-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a1bd6-117">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="a1bd6-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a1bd6-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a1bd6-118">E_FAIL</span></span>|<span data-ttu-id="a1bd6-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="a1bd6-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a1bd6-120">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="a1bd6-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a1bd6-121">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a1bd6-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1bd6-122">備註</span><span class="sxs-lookup"><span data-stu-id="a1bd6-122">Remarks</span></span>  
 <span data-ttu-id="a1bd6-123">主機會呼叫`RudeAbort`立即中止的工作。</span><span class="sxs-lookup"><span data-stu-id="a1bd6-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="a1bd6-124">完成項和例外狀況處理常式不保證會執行。</span><span class="sxs-lookup"><span data-stu-id="a1bd6-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1bd6-125">需求</span><span class="sxs-lookup"><span data-stu-id="a1bd6-125">Requirements</span></span>  
 <span data-ttu-id="a1bd6-126">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a1bd6-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1bd6-127">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a1bd6-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a1bd6-128">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a1bd6-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1bd6-129">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1bd6-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1bd6-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="a1bd6-130">See Also</span></span>  
 [<span data-ttu-id="a1bd6-131">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="a1bd6-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="a1bd6-132">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="a1bd6-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="a1bd6-133">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="a1bd6-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="a1bd6-134">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="a1bd6-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
