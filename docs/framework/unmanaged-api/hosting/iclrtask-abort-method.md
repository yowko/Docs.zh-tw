---
title: ICLRTask::Abort 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9164e64c56a8a4ae908a3d06f878b399550703f9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715396"
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="870e9-102">ICLRTask::Abort 方法</span><span class="sxs-lookup"><span data-stu-id="870e9-102">ICLRTask::Abort Method</span></span>
<span data-ttu-id="870e9-103">要求 common language runtime (CLR) 會中止工作的目前[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)執行個體表示。</span><span class="sxs-lookup"><span data-stu-id="870e9-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="870e9-104">語法</span><span class="sxs-lookup"><span data-stu-id="870e9-104">Syntax</span></span>  
  
```  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="870e9-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="870e9-105">Return Value</span></span>  
  
|<span data-ttu-id="870e9-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="870e9-106">HRESULT</span></span>|<span data-ttu-id="870e9-107">描述</span><span class="sxs-lookup"><span data-stu-id="870e9-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="870e9-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="870e9-108">S_OK</span></span>|<span data-ttu-id="870e9-109">`Abort` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="870e9-109">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="870e9-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="870e9-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="870e9-111">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="870e9-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="870e9-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="870e9-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="870e9-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="870e9-113">The call timed out.</span></span>|  
|<span data-ttu-id="870e9-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="870e9-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="870e9-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="870e9-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="870e9-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="870e9-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="870e9-117">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="870e9-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="870e9-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="870e9-118">E_FAIL</span></span>|<span data-ttu-id="870e9-119">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="870e9-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="870e9-120">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="870e9-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="870e9-121">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="870e9-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="870e9-122">備註</span><span class="sxs-lookup"><span data-stu-id="870e9-122">Remarks</span></span>  
 <span data-ttu-id="870e9-123">CLR 會引發<xref:System.Threading.ThreadAbortException>當主應用程式呼叫`Abort`。</span><span class="sxs-lookup"><span data-stu-id="870e9-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="870e9-124">它會在初始化例外狀況資訊，而不需等到使用者程式碼，例如 「 完成項或例外狀況處理機制，以執行之後，立即傳回。</span><span class="sxs-lookup"><span data-stu-id="870e9-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="870e9-125">呼叫`Abort`因此快速傳回。</span><span class="sxs-lookup"><span data-stu-id="870e9-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="870e9-126">需求</span><span class="sxs-lookup"><span data-stu-id="870e9-126">Requirements</span></span>  
 <span data-ttu-id="870e9-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="870e9-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="870e9-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="870e9-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="870e9-129">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="870e9-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="870e9-130">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="870e9-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="870e9-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="870e9-131">See also</span></span>
- [<span data-ttu-id="870e9-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="870e9-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="870e9-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="870e9-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="870e9-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="870e9-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="870e9-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="870e9-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
