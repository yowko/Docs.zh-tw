---
title: "IHostTask::GetPriority 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.GetPriority
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::GetPriority
helpviewer_keywords:
- GetPriority method [.NET Framework hosting]
- IHostTask::GetPriority method [.NET Framework hosting]
ms.assetid: 4b463cd6-77c1-4f9a-8518-346ad8fc4b70
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ba32e8c442042f59c8346d68cef7d9f6678ae7dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskgetpriority-method"></a><span data-ttu-id="d0203-102">IHostTask::GetPriority 方法</span><span class="sxs-lookup"><span data-stu-id="d0203-102">IHostTask::GetPriority Method</span></span>
<span data-ttu-id="d0203-103">取得表示由目前的工作的執行緒優先權等級[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)執行個體。</span><span class="sxs-lookup"><span data-stu-id="d0203-103">Gets the thread priority level of the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0203-104">語法</span><span class="sxs-lookup"><span data-stu-id="d0203-104">Syntax</span></span>  
  
```  
HRESULT GetPriority (  
    [out] int *pPriority  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d0203-105">參數</span><span class="sxs-lookup"><span data-stu-id="d0203-105">Parameters</span></span>  
 `pPriority`  
 <span data-ttu-id="d0203-106">[out]整數，表示由目前工作的執行緒優先權等級的指標`IHostTask`執行個體。</span><span class="sxs-lookup"><span data-stu-id="d0203-106">[out] A pointer to an integer that indicates the thread priority level of the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0203-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="d0203-107">Return Value</span></span>  
  
|<span data-ttu-id="d0203-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d0203-108">HRESULT</span></span>|<span data-ttu-id="d0203-109">描述</span><span class="sxs-lookup"><span data-stu-id="d0203-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d0203-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d0203-110">S_OK</span></span>|<span data-ttu-id="d0203-111">`GetPriority`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="d0203-111">`GetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="d0203-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d0203-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d0203-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="d0203-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d0203-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d0203-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d0203-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="d0203-115">The call timed out.</span></span>|  
|<span data-ttu-id="d0203-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d0203-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d0203-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d0203-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d0203-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d0203-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d0203-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="d0203-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d0203-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d0203-120">E_FAIL</span></span>|<span data-ttu-id="d0203-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="d0203-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d0203-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="d0203-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d0203-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d0203-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0203-124">備註</span><span class="sxs-lookup"><span data-stu-id="d0203-124">Remarks</span></span>  
 <span data-ttu-id="d0203-125">執行緒的優先權層級的值會由 Win32`SetThreadPriority`函式。</span><span class="sxs-lookup"><span data-stu-id="d0203-125">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0203-126">需求</span><span class="sxs-lookup"><span data-stu-id="d0203-126">Requirements</span></span>  
 <span data-ttu-id="d0203-127">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d0203-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0203-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d0203-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d0203-129">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d0203-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d0203-130">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0203-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0203-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0203-131">See Also</span></span>  
 [<span data-ttu-id="d0203-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="d0203-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="d0203-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="d0203-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="d0203-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="d0203-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="d0203-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="d0203-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
