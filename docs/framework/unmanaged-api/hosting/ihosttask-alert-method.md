---
title: "IHostTask::Alert 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.Alert
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::Alert
helpviewer_keywords:
- IHostTask::Alert method [.NET Framework hosting]
- Alert method, IHostTask interface [.NET Framework hosting]
ms.assetid: 5245d4b5-b6c3-48df-9cb9-8caf059f43fb
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 10dc8b9894c6f5444ccfcfd17f749df1a3fb5d05
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskalert-method"></a><span data-ttu-id="599a2-102">IHostTask::Alert 方法</span><span class="sxs-lookup"><span data-stu-id="599a2-102">IHostTask::Alert Method</span></span>
<span data-ttu-id="599a2-103">要求主機喚醒表示由目前的工作[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)執行個體，因此可以中止的工作。</span><span class="sxs-lookup"><span data-stu-id="599a2-103">Requests that the host wake the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance, so the task can be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="599a2-104">語法</span><span class="sxs-lookup"><span data-stu-id="599a2-104">Syntax</span></span>  
  
```  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="599a2-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="599a2-105">Return Value</span></span>  
  
|<span data-ttu-id="599a2-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="599a2-106">HRESULT</span></span>|<span data-ttu-id="599a2-107">描述</span><span class="sxs-lookup"><span data-stu-id="599a2-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="599a2-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="599a2-108">S_OK</span></span>|<span data-ttu-id="599a2-109">方法成功傳回。</span><span class="sxs-lookup"><span data-stu-id="599a2-109">The method returned successfully.</span></span>|  
|<span data-ttu-id="599a2-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="599a2-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="599a2-111">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="599a2-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="599a2-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="599a2-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="599a2-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="599a2-113">The call timed out.</span></span>|  
|<span data-ttu-id="599a2-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="599a2-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="599a2-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="599a2-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="599a2-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="599a2-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="599a2-117">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="599a2-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="599a2-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="599a2-118">E_FAIL</span></span>|<span data-ttu-id="599a2-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="599a2-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="599a2-120">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="599a2-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="599a2-121">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="599a2-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="599a2-122">備註</span><span class="sxs-lookup"><span data-stu-id="599a2-122">Remarks</span></span>  
 <span data-ttu-id="599a2-123">CLR 會呼叫`Alert`方法時<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>呼叫從使用者程式碼，或當<xref:System.AppDomain>目前相關聯<xref:System.Threading.Thread>關機。</span><span class="sxs-lookup"><span data-stu-id="599a2-123">The CLR calls the `Alert` method when <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is called from user code, or when the <xref:System.AppDomain> associated with the current <xref:System.Threading.Thread> shuts down.</span></span> <span data-ttu-id="599a2-124">主機必須立即傳回，因為以非同步方式進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="599a2-124">The host must return immediately, because the call is made asynchronously.</span></span> <span data-ttu-id="599a2-125">如果主機無法立即警示此工作，它必須喚醒進入的狀態，在其中警示在下一次。</span><span class="sxs-lookup"><span data-stu-id="599a2-125">If the host cannot alert the task immediately, it must wake up the next time it enters a state in which it can be alerted.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="599a2-126">`Alert`會影響已傳遞到執行階段的工作[WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) WAIT_ALERTABLE 值這類方法[聯結](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)。</span><span class="sxs-lookup"><span data-stu-id="599a2-126">`Alert` affects only those tasks to which the runtime has passed a [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) value of WAIT_ALERTABLE to methods such as [Join](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="599a2-127">需求</span><span class="sxs-lookup"><span data-stu-id="599a2-127">Requirements</span></span>  
 <span data-ttu-id="599a2-128">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="599a2-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="599a2-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="599a2-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="599a2-130">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="599a2-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="599a2-131">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="599a2-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="599a2-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="599a2-132">See Also</span></span>  
 [<span data-ttu-id="599a2-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="599a2-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="599a2-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="599a2-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="599a2-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="599a2-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="599a2-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="599a2-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
