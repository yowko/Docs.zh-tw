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
ms.openlocfilehash: a99bda7a6d21fea159c8f616f2db7d12b1f27579
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435410"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="bce0f-102">ICLRTask::RudeAbort 方法</span><span class="sxs-lookup"><span data-stu-id="bce0f-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="bce0f-103">指示 common language runtime (CLR)，以中止表示由目前的工作[ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)立即且無條件地執行個體。</span><span class="sxs-lookup"><span data-stu-id="bce0f-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bce0f-104">語法</span><span class="sxs-lookup"><span data-stu-id="bce0f-104">Syntax</span></span>  
  
```  
HRESULT RudeAbort ();   
```  
  
## <a name="return-value"></a><span data-ttu-id="bce0f-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="bce0f-105">Return Value</span></span>  
  
|<span data-ttu-id="bce0f-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bce0f-106">HRESULT</span></span>|<span data-ttu-id="bce0f-107">描述</span><span class="sxs-lookup"><span data-stu-id="bce0f-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bce0f-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="bce0f-108">S_OK</span></span>|<span data-ttu-id="bce0f-109">`RudeAbort` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="bce0f-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="bce0f-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bce0f-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bce0f-111">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="bce0f-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bce0f-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bce0f-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bce0f-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="bce0f-113">The call timed out.</span></span>|  
|<span data-ttu-id="bce0f-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bce0f-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bce0f-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="bce0f-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bce0f-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bce0f-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bce0f-117">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="bce0f-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bce0f-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bce0f-118">E_FAIL</span></span>|<span data-ttu-id="bce0f-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="bce0f-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bce0f-120">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="bce0f-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bce0f-121">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="bce0f-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bce0f-122">備註</span><span class="sxs-lookup"><span data-stu-id="bce0f-122">Remarks</span></span>  
 <span data-ttu-id="bce0f-123">主機會呼叫`RudeAbort`立即中止的工作。</span><span class="sxs-lookup"><span data-stu-id="bce0f-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="bce0f-124">完成項和例外狀況處理常式不保證會執行。</span><span class="sxs-lookup"><span data-stu-id="bce0f-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bce0f-125">需求</span><span class="sxs-lookup"><span data-stu-id="bce0f-125">Requirements</span></span>  
 <span data-ttu-id="bce0f-126">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bce0f-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bce0f-127">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bce0f-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bce0f-128">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="bce0f-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bce0f-129">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bce0f-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bce0f-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bce0f-130">See Also</span></span>  
 [<span data-ttu-id="bce0f-131">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="bce0f-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="bce0f-132">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="bce0f-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="bce0f-133">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="bce0f-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="bce0f-134">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="bce0f-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
