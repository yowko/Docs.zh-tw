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
ms.openlocfilehash: aadbbb5fc6abd3829f14670e42149174f6ef238d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690843"
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="bd79a-102">ICLRTask::Abort 方法</span><span class="sxs-lookup"><span data-stu-id="bd79a-102">ICLRTask::Abort Method</span></span>

<span data-ttu-id="bd79a-103">要求 common language runtime (CLR) 中止目前 [ICLRTask](iclrtask-interface.md) 實例所代表的工作。</span><span class="sxs-lookup"><span data-stu-id="bd79a-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd79a-104">語法</span><span class="sxs-lookup"><span data-stu-id="bd79a-104">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="bd79a-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="bd79a-105">Return Value</span></span>  
  
|<span data-ttu-id="bd79a-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bd79a-106">HRESULT</span></span>|<span data-ttu-id="bd79a-107">描述</span><span class="sxs-lookup"><span data-stu-id="bd79a-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bd79a-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="bd79a-108">S_OK</span></span>|<span data-ttu-id="bd79a-109">`Abort` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="bd79a-109">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="bd79a-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bd79a-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bd79a-111">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="bd79a-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bd79a-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bd79a-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bd79a-113">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="bd79a-113">The call timed out.</span></span>|  
|<span data-ttu-id="bd79a-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bd79a-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bd79a-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="bd79a-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bd79a-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bd79a-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bd79a-117">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="bd79a-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bd79a-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bd79a-118">E_FAIL</span></span>|<span data-ttu-id="bd79a-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="bd79a-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bd79a-120">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="bd79a-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bd79a-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="bd79a-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd79a-122">備註</span><span class="sxs-lookup"><span data-stu-id="bd79a-122">Remarks</span></span>  

 <span data-ttu-id="bd79a-123"><xref:System.Threading.ThreadAbortException>當主機呼叫時，CLR 會引發 `Abort` 。</span><span class="sxs-lookup"><span data-stu-id="bd79a-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="bd79a-124">它會在例外狀況資訊初始化後立即傳回，而不會等待使用者程式碼（例如完成項或例外狀況處理機制）執行。</span><span class="sxs-lookup"><span data-stu-id="bd79a-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="bd79a-125">因此，呼叫會 `Abort` 快速傳回。</span><span class="sxs-lookup"><span data-stu-id="bd79a-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd79a-126">需求</span><span class="sxs-lookup"><span data-stu-id="bd79a-126">Requirements</span></span>  

 <span data-ttu-id="bd79a-127">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bd79a-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd79a-128">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="bd79a-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bd79a-129">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="bd79a-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bd79a-130">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd79a-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd79a-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd79a-131">See also</span></span>

- [<span data-ttu-id="bd79a-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="bd79a-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="bd79a-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="bd79a-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="bd79a-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="bd79a-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="bd79a-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="bd79a-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
