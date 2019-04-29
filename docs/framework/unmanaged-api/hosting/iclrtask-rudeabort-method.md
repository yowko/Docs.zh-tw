---
title: ICLRTask::RudeAbort 方法
ms.date: 03/30/2017
api_name:
- ICLRTask.RudeAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::RudeAbort
helpviewer_keywords:
- RudeAbort method, ICLRTask interface [.NET Framework hosting]
- ICLRTask::RudeAbort method [.NET Framework hosting]
ms.assetid: b5785468-fcd7-4cc3-8a5d-8796337b53fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2db47f90e73922858013885e99e953ddcacbd450
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763512"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="2be94-102">ICLRTask::RudeAbort 方法</span><span class="sxs-lookup"><span data-stu-id="2be94-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="2be94-103">指示 common language runtime (CLR)，以中止表示由目前的工作[ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)立即且無條件地執行個體。</span><span class="sxs-lookup"><span data-stu-id="2be94-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2be94-104">語法</span><span class="sxs-lookup"><span data-stu-id="2be94-104">Syntax</span></span>  
  
```  
HRESULT RudeAbort ();   
```  
  
## <a name="return-value"></a><span data-ttu-id="2be94-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="2be94-105">Return Value</span></span>  
  
|<span data-ttu-id="2be94-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2be94-106">HRESULT</span></span>|<span data-ttu-id="2be94-107">描述</span><span class="sxs-lookup"><span data-stu-id="2be94-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2be94-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="2be94-108">S_OK</span></span>|<span data-ttu-id="2be94-109">`RudeAbort` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="2be94-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="2be94-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2be94-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2be94-111">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="2be94-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2be94-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2be94-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2be94-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="2be94-113">The call timed out.</span></span>|  
|<span data-ttu-id="2be94-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2be94-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2be94-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="2be94-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2be94-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2be94-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2be94-117">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="2be94-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2be94-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2be94-118">E_FAIL</span></span>|<span data-ttu-id="2be94-119">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="2be94-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2be94-120">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="2be94-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2be94-121">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="2be94-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2be94-122">備註</span><span class="sxs-lookup"><span data-stu-id="2be94-122">Remarks</span></span>  
 <span data-ttu-id="2be94-123">主機會呼叫`RudeAbort`立即中止的工作。</span><span class="sxs-lookup"><span data-stu-id="2be94-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="2be94-124">完成項和例外狀況處理常式不會保證執行中。</span><span class="sxs-lookup"><span data-stu-id="2be94-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2be94-125">需求</span><span class="sxs-lookup"><span data-stu-id="2be94-125">Requirements</span></span>  
 <span data-ttu-id="2be94-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2be94-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2be94-127">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2be94-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2be94-128">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2be94-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2be94-129">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2be94-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2be94-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2be94-130">See also</span></span>

- [<span data-ttu-id="2be94-131">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="2be94-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="2be94-132">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="2be94-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="2be94-133">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="2be94-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="2be94-134">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="2be94-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
