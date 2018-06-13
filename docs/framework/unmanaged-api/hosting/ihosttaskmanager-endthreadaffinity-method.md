---
title: IHostTaskManager::EndThreadAffinity 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndThreadAffinity
helpviewer_keywords:
- EndThreadAffinity method [.NET Framework hosting]
- IHostTaskManager::EndThreadAffinity method [.NET Framework hosting]
ms.assetid: 7738a904-0cd7-4fde-a3eb-2323a5533157
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb07e38542893b26595b67d6cf0fa77c522b4def
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442809"
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a><span data-ttu-id="a2b60-102">IHostTaskManager::EndThreadAffinity 方法</span><span class="sxs-lookup"><span data-stu-id="a2b60-102">IHostTaskManager::EndThreadAffinity Method</span></span>
<span data-ttu-id="a2b60-103">通知主機 managed 程式碼會結束目前的工作不會移至另一個作業系統執行緒的期間遵循之前呼叫[ihosttaskmanager:: Beginthreadaffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)。</span><span class="sxs-lookup"><span data-stu-id="a2b60-103">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to [IHostTaskManager::BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2b60-104">語法</span><span class="sxs-lookup"><span data-stu-id="a2b60-104">Syntax</span></span>  
  
```  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a2b60-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="a2b60-105">Return Value</span></span>  
  
|<span data-ttu-id="a2b60-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a2b60-106">HRESULT</span></span>|<span data-ttu-id="a2b60-107">描述</span><span class="sxs-lookup"><span data-stu-id="a2b60-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a2b60-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a2b60-108">S_OK</span></span>|<span data-ttu-id="a2b60-109">`EndThreadAffinity` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="a2b60-109">`EndThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="a2b60-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a2b60-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a2b60-111">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="a2b60-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a2b60-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a2b60-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a2b60-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="a2b60-113">The call timed out.</span></span>|  
|<span data-ttu-id="a2b60-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a2b60-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a2b60-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="a2b60-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a2b60-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a2b60-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a2b60-117">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="a2b60-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a2b60-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a2b60-118">E_FAIL</span></span>|<span data-ttu-id="a2b60-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="a2b60-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a2b60-120">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="a2b60-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a2b60-121">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a2b60-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a2b60-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="a2b60-122">E_UNEXPECTED</span></span>|<span data-ttu-id="a2b60-123">`EndThreadAffinity` 呼叫的前面對應呼叫未`BeginThreadAffinity`。</span><span class="sxs-lookup"><span data-stu-id="a2b60-123">`EndThreadAffinity` was called without an earlier corresponding call to `BeginThreadAffinity`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2b60-124">備註</span><span class="sxs-lookup"><span data-stu-id="a2b60-124">Remarks</span></span>  
 <span data-ttu-id="a2b60-125">CLR 會對應呼叫`BeginThreadAffinity`上目前的工作，然後再呼叫`EndThreadAffinity`。</span><span class="sxs-lookup"><span data-stu-id="a2b60-125">The CLR makes a corresponding call to `BeginThreadAffinity` on the current task before calling `EndThreadAffinity`.</span></span> <span data-ttu-id="a2b60-126">如果沒有這類對應的呼叫，主應用程式的實作[IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)應該傳回 E_UNEXPECTED，並不採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="a2b60-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED, and take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2b60-127">需求</span><span class="sxs-lookup"><span data-stu-id="a2b60-127">Requirements</span></span>  
 <span data-ttu-id="a2b60-128">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a2b60-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2b60-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a2b60-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a2b60-130">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a2b60-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a2b60-131">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2b60-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2b60-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2b60-132">See Also</span></span>  
 <xref:System.Threading>  
 [<span data-ttu-id="a2b60-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="a2b60-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="a2b60-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="a2b60-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="a2b60-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="a2b60-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="a2b60-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="a2b60-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
