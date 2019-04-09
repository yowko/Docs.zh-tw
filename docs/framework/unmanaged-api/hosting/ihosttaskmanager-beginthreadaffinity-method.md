---
title: IHostTaskManager::BeginThreadAffinity 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginThreadAffinity
helpviewer_keywords:
- IHostTaskManager::BeginThreadAffinity method [.NET Framework hosting]
- BeginThreadAffinity method [.NET Framework hosting]
ms.assetid: fea3ab88-ce41-4c5a-847b-bb78cd748da6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7eb5c7ec85c0adb301fb722155caaed3c14e0e19
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137718"
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a><span data-ttu-id="b6f17-102">IHostTaskManager::BeginThreadAffinity 方法</span><span class="sxs-lookup"><span data-stu-id="b6f17-102">IHostTaskManager::BeginThreadAffinity Method</span></span>
<span data-ttu-id="b6f17-103">通知主機 managed 程式碼會進入目前的工作不會移至另一個作業系統執行緒的週期。</span><span class="sxs-lookup"><span data-stu-id="b6f17-103">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6f17-104">語法</span><span class="sxs-lookup"><span data-stu-id="b6f17-104">Syntax</span></span>  
  
```  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b6f17-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="b6f17-105">Return Value</span></span>  
  
|<span data-ttu-id="b6f17-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b6f17-106">HRESULT</span></span>|<span data-ttu-id="b6f17-107">描述</span><span class="sxs-lookup"><span data-stu-id="b6f17-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b6f17-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="b6f17-108">S_OK</span></span>|`BeginThreadAffinity` <span data-ttu-id="b6f17-109">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="b6f17-109">returned successfully.</span></span>|  
|<span data-ttu-id="b6f17-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b6f17-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b6f17-111">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="b6f17-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b6f17-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b6f17-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b6f17-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="b6f17-113">The call timed out.</span></span>|  
|<span data-ttu-id="b6f17-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b6f17-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b6f17-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b6f17-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b6f17-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b6f17-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b6f17-117">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="b6f17-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b6f17-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b6f17-118">E_FAIL</span></span>|<span data-ttu-id="b6f17-119">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="b6f17-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b6f17-120">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="b6f17-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b6f17-121">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b6f17-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6f17-122">備註</span><span class="sxs-lookup"><span data-stu-id="b6f17-122">Remarks</span></span>  
 <span data-ttu-id="b6f17-123">CLR 通常會呼叫`IHostTaskManager::BeginThreadAffinity`的呼叫內容中<xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="b6f17-123">The CLR typically calls `IHostTaskManager::BeginThreadAffinity` in the context of a call to <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b6f17-124">必須不重新排程目前的工作，直到進行對應的呼叫，以[ihosttaskmanager:: Endthreadaffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)。</span><span class="sxs-lookup"><span data-stu-id="b6f17-124">The current task must not be rescheduled until a corresponding call is made to [IHostTaskManager::EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span></span> <span data-ttu-id="b6f17-125">工作可以要切換移出，但當它們切換回來，它們必須指派給相同的作業系統執行緒從中它們已切換移出。巢狀呼叫`BeginThreadAffinity`沒有任何作用，因為呼叫參考到目前的工作。</span><span class="sxs-lookup"><span data-stu-id="b6f17-125">Tasks can be switched out, but when they are switched back in, they must be assigned to the same operating system thread from which they were switched out. Nested calls to `BeginThreadAffinity` have no effect, because the call refers to the current task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6f17-126">需求</span><span class="sxs-lookup"><span data-stu-id="b6f17-126">Requirements</span></span>  
 <span data-ttu-id="b6f17-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6f17-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6f17-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b6f17-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b6f17-129">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b6f17-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="b6f17-130">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="b6f17-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b6f17-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6f17-131">See also</span></span>

- [<span data-ttu-id="b6f17-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="b6f17-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="b6f17-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="b6f17-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="b6f17-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="b6f17-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="b6f17-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="b6f17-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
