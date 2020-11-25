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
ms.openlocfilehash: 6f6d57a52d960c975d468f370477b5d7e29c3aa2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727337"
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a><span data-ttu-id="4ddfd-102">IHostTaskManager::BeginThreadAffinity 方法</span><span class="sxs-lookup"><span data-stu-id="4ddfd-102">IHostTaskManager::BeginThreadAffinity Method</span></span>

<span data-ttu-id="4ddfd-103">通知主機 managed 程式碼所輸入的期間，不能將目前的工作移至另一個作業系統執行緒。</span><span class="sxs-lookup"><span data-stu-id="4ddfd-103">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ddfd-104">語法</span><span class="sxs-lookup"><span data-stu-id="4ddfd-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4ddfd-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="4ddfd-105">Return Value</span></span>  
  
|<span data-ttu-id="4ddfd-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4ddfd-106">HRESULT</span></span>|<span data-ttu-id="4ddfd-107">描述</span><span class="sxs-lookup"><span data-stu-id="4ddfd-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4ddfd-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="4ddfd-108">S_OK</span></span>|<span data-ttu-id="4ddfd-109">`BeginThreadAffinity` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="4ddfd-109">`BeginThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="4ddfd-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4ddfd-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4ddfd-111">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="4ddfd-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4ddfd-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4ddfd-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4ddfd-113">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="4ddfd-113">The call timed out.</span></span>|  
|<span data-ttu-id="4ddfd-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4ddfd-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4ddfd-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="4ddfd-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4ddfd-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4ddfd-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4ddfd-117">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="4ddfd-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4ddfd-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4ddfd-118">E_FAIL</span></span>|<span data-ttu-id="4ddfd-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="4ddfd-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4ddfd-120">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="4ddfd-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4ddfd-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="4ddfd-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ddfd-122">備註</span><span class="sxs-lookup"><span data-stu-id="4ddfd-122">Remarks</span></span>  

 <span data-ttu-id="4ddfd-123">CLR 通常會 `IHostTaskManager::BeginThreadAffinity` 在呼叫的內容中呼叫 <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="4ddfd-123">The CLR typically calls `IHostTaskManager::BeginThreadAffinity` in the context of a call to <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4ddfd-124">在對 [IHostTaskManager：： EndThreadAffinity](ihosttaskmanager-endthreadaffinity-method.md)進行對應的呼叫之前，不能重新排程目前的工作。</span><span class="sxs-lookup"><span data-stu-id="4ddfd-124">The current task must not be rescheduled until a corresponding call is made to [IHostTaskManager::EndThreadAffinity](ihosttaskmanager-endthreadaffinity-method.md).</span></span> <span data-ttu-id="4ddfd-125">您可以將工作切換出來，但是當它們切換回時，必須將它們指派給與其進行切換的相同作業系統執行緒。的嵌套呼叫 `BeginThreadAffinity` 不會有任何作用，因為呼叫會參考目前的工作。</span><span class="sxs-lookup"><span data-stu-id="4ddfd-125">Tasks can be switched out, but when they are switched back in, they must be assigned to the same operating system thread from which they were switched out. Nested calls to `BeginThreadAffinity` have no effect, because the call refers to the current task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ddfd-126">需求</span><span class="sxs-lookup"><span data-stu-id="4ddfd-126">Requirements</span></span>  

 <span data-ttu-id="4ddfd-127">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4ddfd-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ddfd-128">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="4ddfd-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4ddfd-129">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="4ddfd-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4ddfd-130">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ddfd-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ddfd-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ddfd-131">See also</span></span>

- [<span data-ttu-id="4ddfd-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="4ddfd-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="4ddfd-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="4ddfd-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="4ddfd-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="4ddfd-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="4ddfd-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="4ddfd-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
