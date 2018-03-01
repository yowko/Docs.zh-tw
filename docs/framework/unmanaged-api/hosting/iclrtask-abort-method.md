---
title: "ICLRTask::Abort 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRTask.Abort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Abort
helpviewer_keywords:
- ICLRTask::Abort method [.NET Framework hosting]
- Abort method, ICLRTask interface [.NET Framework hosting]
ms.assetid: b3594b5f-2e41-4e36-9096-3586276a138c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0e417e329b38c8f57dedf2926c0d6ff02a0170f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="a3600-102">ICLRTask::Abort 方法</span><span class="sxs-lookup"><span data-stu-id="a3600-102">ICLRTask::Abort Method</span></span>
<span data-ttu-id="a3600-103">要求 common language runtime (CLR) 會中止工作的目前[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)執行個體所表示。</span><span class="sxs-lookup"><span data-stu-id="a3600-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3600-104">語法</span><span class="sxs-lookup"><span data-stu-id="a3600-104">Syntax</span></span>  
  
```  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a3600-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="a3600-105">Return Value</span></span>  
  
|<span data-ttu-id="a3600-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a3600-106">HRESULT</span></span>|<span data-ttu-id="a3600-107">描述</span><span class="sxs-lookup"><span data-stu-id="a3600-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a3600-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a3600-108">S_OK</span></span>|<span data-ttu-id="a3600-109">`Abort`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="a3600-109">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="a3600-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a3600-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a3600-111">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="a3600-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a3600-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a3600-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a3600-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="a3600-113">The call timed out.</span></span>|  
|<span data-ttu-id="a3600-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a3600-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a3600-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="a3600-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a3600-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a3600-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a3600-117">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="a3600-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a3600-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a3600-118">E_FAIL</span></span>|<span data-ttu-id="a3600-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="a3600-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a3600-120">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="a3600-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a3600-121">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a3600-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3600-122">備註</span><span class="sxs-lookup"><span data-stu-id="a3600-122">Remarks</span></span>  
 <span data-ttu-id="a3600-123">CLR 會引發<xref:System.Threading.ThreadAbortException>當主機呼叫`Abort`。</span><span class="sxs-lookup"><span data-stu-id="a3600-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="a3600-124">它會傳回例外狀況資訊初始化，則不需等到使用者程式碼，例如完成項或例外狀況處理機制，以執行之後，立即。</span><span class="sxs-lookup"><span data-stu-id="a3600-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="a3600-125">呼叫`Abort`因此快速傳回。</span><span class="sxs-lookup"><span data-stu-id="a3600-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3600-126">需求</span><span class="sxs-lookup"><span data-stu-id="a3600-126">Requirements</span></span>  
 <span data-ttu-id="a3600-127">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a3600-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3600-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a3600-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a3600-129">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a3600-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3600-130">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3600-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3600-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="a3600-131">See Also</span></span>  
 [<span data-ttu-id="a3600-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="a3600-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="a3600-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="a3600-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="a3600-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="a3600-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="a3600-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="a3600-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
