---
title: "ICLRTask::Abort 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.Abort
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::Abort
helpviewer_keywords:
- ICLRTask::Abort method [.NET Framework hosting]
- Abort method, ICLRTask interface [.NET Framework hosting]
ms.assetid: b3594b5f-2e41-4e36-9096-3586276a138c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e789afc8f570d647fd44f8f43c23c2cc33ba8f70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="fa484-102">ICLRTask::Abort 方法</span><span class="sxs-lookup"><span data-stu-id="fa484-102">ICLRTask::Abort Method</span></span>
<span data-ttu-id="fa484-103">要求 common language runtime (CLR) 會中止工作的目前[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)執行個體所表示。</span><span class="sxs-lookup"><span data-stu-id="fa484-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa484-104">語法</span><span class="sxs-lookup"><span data-stu-id="fa484-104">Syntax</span></span>  
  
```  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="fa484-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="fa484-105">Return Value</span></span>  
  
|<span data-ttu-id="fa484-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fa484-106">HRESULT</span></span>|<span data-ttu-id="fa484-107">描述</span><span class="sxs-lookup"><span data-stu-id="fa484-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fa484-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="fa484-108">S_OK</span></span>|<span data-ttu-id="fa484-109">`Abort`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="fa484-109">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="fa484-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fa484-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fa484-111">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="fa484-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fa484-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fa484-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fa484-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="fa484-113">The call timed out.</span></span>|  
|<span data-ttu-id="fa484-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fa484-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fa484-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="fa484-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fa484-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fa484-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fa484-117">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="fa484-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fa484-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fa484-118">E_FAIL</span></span>|<span data-ttu-id="fa484-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="fa484-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fa484-120">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="fa484-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fa484-121">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="fa484-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa484-122">備註</span><span class="sxs-lookup"><span data-stu-id="fa484-122">Remarks</span></span>  
 <span data-ttu-id="fa484-123">CLR 會引發<xref:System.Threading.ThreadAbortException>當主機呼叫`Abort`。</span><span class="sxs-lookup"><span data-stu-id="fa484-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="fa484-124">它會傳回例外狀況資訊初始化，則不需等到使用者程式碼，例如完成項或例外狀況處理機制，以執行之後，立即。</span><span class="sxs-lookup"><span data-stu-id="fa484-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="fa484-125">呼叫`Abort`因此快速傳回。</span><span class="sxs-lookup"><span data-stu-id="fa484-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa484-126">需求</span><span class="sxs-lookup"><span data-stu-id="fa484-126">Requirements</span></span>  
 <span data-ttu-id="fa484-127">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fa484-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa484-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fa484-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fa484-129">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fa484-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fa484-130">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa484-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa484-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa484-131">See Also</span></span>  
 [<span data-ttu-id="fa484-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="fa484-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="fa484-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="fa484-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="fa484-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="fa484-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="fa484-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="fa484-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
