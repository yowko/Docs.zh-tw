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
ms.openlocfilehash: 026d4c14abed030b80e8e1b3f8363fbd59ac05e4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124911"
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="d1314-102">ICLRTask::Abort 方法</span><span class="sxs-lookup"><span data-stu-id="d1314-102">ICLRTask::Abort Method</span></span>
<span data-ttu-id="d1314-103">要求 common language runtime （CLR）中止目前[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)實例所代表的工作。</span><span class="sxs-lookup"><span data-stu-id="d1314-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1314-104">語法</span><span class="sxs-lookup"><span data-stu-id="d1314-104">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d1314-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="d1314-105">Return Value</span></span>  
  
|<span data-ttu-id="d1314-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d1314-106">HRESULT</span></span>|<span data-ttu-id="d1314-107">描述</span><span class="sxs-lookup"><span data-stu-id="d1314-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d1314-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="d1314-108">S_OK</span></span>|<span data-ttu-id="d1314-109">已成功傳回 `Abort`。</span><span class="sxs-lookup"><span data-stu-id="d1314-109">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="d1314-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d1314-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d1314-111">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="d1314-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d1314-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d1314-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d1314-113">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="d1314-113">The call timed out.</span></span>|  
|<span data-ttu-id="d1314-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d1314-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d1314-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d1314-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d1314-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d1314-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d1314-117">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="d1314-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d1314-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d1314-118">E_FAIL</span></span>|<span data-ttu-id="d1314-119">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="d1314-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d1314-120">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="d1314-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d1314-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d1314-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1314-122">備註</span><span class="sxs-lookup"><span data-stu-id="d1314-122">Remarks</span></span>  
 <span data-ttu-id="d1314-123">當主機呼叫 `Abort`時，CLR 會引發 <xref:System.Threading.ThreadAbortException>。</span><span class="sxs-lookup"><span data-stu-id="d1314-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="d1314-124">它會在例外狀況資訊初始化之後立即傳回，而不會等候使用者程式碼（例如完成項或例外狀況處理機制）執行。</span><span class="sxs-lookup"><span data-stu-id="d1314-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="d1314-125">因此，`Abort` 的呼叫會快速傳回。</span><span class="sxs-lookup"><span data-stu-id="d1314-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1314-126">需求</span><span class="sxs-lookup"><span data-stu-id="d1314-126">Requirements</span></span>  
 <span data-ttu-id="d1314-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d1314-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1314-128">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="d1314-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d1314-129">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d1314-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d1314-130">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1314-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1314-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="d1314-131">See also</span></span>

- [<span data-ttu-id="d1314-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="d1314-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="d1314-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="d1314-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="d1314-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="d1314-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="d1314-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="d1314-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
