---
title: ICLRTask::YieldTask 方法
ms.date: 03/30/2017
api_name:
- ICLRTask.YieldTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::YieldTask
helpviewer_keywords:
- ICLRTask::YieldTask method [.NET Framework hosting]
- YieldTask method [.NET Framework hosting]
ms.assetid: b8eb4095-3a8f-4be3-9446-63e9893dce7d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 821f524cc8ff7f9983f811f539e2badb2306be26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437699"
---
# <a name="iclrtaskyieldtask-method"></a><span data-ttu-id="1ff94-102">ICLRTask::YieldTask 方法</span><span class="sxs-lookup"><span data-stu-id="1ff94-102">ICLRTask::YieldTask Method</span></span>
<span data-ttu-id="1ff94-103">要求 common language runtime (CLR) 擱工作的目前[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)執行個體所表示，並使用其他工作的處理器時間。</span><span class="sxs-lookup"><span data-stu-id="1ff94-103">Requests that the common language runtime (CLR) put aside the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents, and make the processor time available to other tasks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ff94-104">語法</span><span class="sxs-lookup"><span data-stu-id="1ff94-104">Syntax</span></span>  
  
```  
HRESULT YieldTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1ff94-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="1ff94-105">Return Value</span></span>  
  
|<span data-ttu-id="1ff94-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1ff94-106">HRESULT</span></span>|<span data-ttu-id="1ff94-107">描述</span><span class="sxs-lookup"><span data-stu-id="1ff94-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1ff94-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="1ff94-108">S_OK</span></span>|<span data-ttu-id="1ff94-109">`YieldTask` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="1ff94-109">`YieldTask` returned successfully.</span></span>|  
|<span data-ttu-id="1ff94-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1ff94-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1ff94-111">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="1ff94-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1ff94-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1ff94-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1ff94-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="1ff94-113">The call timed out.</span></span>|  
|<span data-ttu-id="1ff94-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1ff94-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1ff94-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="1ff94-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1ff94-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1ff94-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1ff94-117">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="1ff94-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1ff94-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1ff94-118">E_FAIL</span></span>|<span data-ttu-id="1ff94-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="1ff94-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1ff94-120">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="1ff94-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1ff94-121">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="1ff94-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ff94-122">備註</span><span class="sxs-lookup"><span data-stu-id="1ff94-122">Remarks</span></span>  
 <span data-ttu-id="1ff94-123">主機會呼叫`YieldTask`來要求其他工作或處理序的處理器資源。</span><span class="sxs-lookup"><span data-stu-id="1ff94-123">A host calls `YieldTask` to request processor resources for other tasks or processes.</span></span> <span data-ttu-id="1ff94-124">這個方法主要是讓長時間執行的程式碼放棄 CPU 時間。</span><span class="sxs-lookup"><span data-stu-id="1ff94-124">This method is primarily intended to allow long-running code to give up CPU time.</span></span> <span data-ttu-id="1ff94-125">執行階段會嘗試將工作的目前`ICLRTask`的執行個體表示它可以產生處理時間，但不保證一定成功的狀態。</span><span class="sxs-lookup"><span data-stu-id="1ff94-125">The runtime attempts to put the task that the current `ICLRTask` instance represents in a state where it can yield processing time, but makes no guarantee of success.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ff94-126">需求</span><span class="sxs-lookup"><span data-stu-id="1ff94-126">Requirements</span></span>  
 <span data-ttu-id="1ff94-127">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1ff94-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ff94-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1ff94-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1ff94-129">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1ff94-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1ff94-130">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ff94-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ff94-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ff94-131">See Also</span></span>  
 [<span data-ttu-id="1ff94-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="1ff94-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="1ff94-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="1ff94-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="1ff94-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="1ff94-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="1ff94-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="1ff94-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
