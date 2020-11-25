---
title: IHostTask::Alert 方法
ms.date: 03/30/2017
api_name:
- IHostTask.Alert
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Alert
helpviewer_keywords:
- IHostTask::Alert method [.NET Framework hosting]
- Alert method, IHostTask interface [.NET Framework hosting]
ms.assetid: 5245d4b5-b6c3-48df-9cb9-8caf059f43fb
topic_type:
- apiref
ms.openlocfilehash: 5a4870a4472081a78cd1fade51f441c22aa5eb48
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720473"
---
# <a name="ihosttaskalert-method"></a><span data-ttu-id="f0e5c-102">IHostTask::Alert 方法</span><span class="sxs-lookup"><span data-stu-id="f0e5c-102">IHostTask::Alert Method</span></span>

<span data-ttu-id="f0e5c-103">要求主機喚醒目前 [IHostTask](ihosttask-interface.md) 實例所代表的工作，讓工作可以中止。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-103">Requests that the host wake the task represented by the current [IHostTask](ihosttask-interface.md) instance, so the task can be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0e5c-104">語法</span><span class="sxs-lookup"><span data-stu-id="f0e5c-104">Syntax</span></span>  
  
```cpp  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f0e5c-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="f0e5c-105">Return Value</span></span>  
  
|<span data-ttu-id="f0e5c-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f0e5c-106">HRESULT</span></span>|<span data-ttu-id="f0e5c-107">描述</span><span class="sxs-lookup"><span data-stu-id="f0e5c-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f0e5c-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="f0e5c-108">S_OK</span></span>|<span data-ttu-id="f0e5c-109">此方法已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-109">The method returned successfully.</span></span>|  
|<span data-ttu-id="f0e5c-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f0e5c-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f0e5c-111">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f0e5c-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f0e5c-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f0e5c-113">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-113">The call timed out.</span></span>|  
|<span data-ttu-id="f0e5c-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f0e5c-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f0e5c-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f0e5c-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f0e5c-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f0e5c-117">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f0e5c-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f0e5c-118">E_FAIL</span></span>|<span data-ttu-id="f0e5c-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f0e5c-120">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f0e5c-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0e5c-122">備註</span><span class="sxs-lookup"><span data-stu-id="f0e5c-122">Remarks</span></span>  

 <span data-ttu-id="f0e5c-123">`Alert`當 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 從使用者程式碼呼叫方法，或 <xref:System.AppDomain> 與目前的相關聯的關閉時，CLR 會呼叫方法 <xref:System.Threading.Thread> 。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-123">The CLR calls the `Alert` method when <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is called from user code, or when the <xref:System.AppDomain> associated with the current <xref:System.Threading.Thread> shuts down.</span></span> <span data-ttu-id="f0e5c-124">因為呼叫是以非同步方式進行，所以主機必須立即返回。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-124">The host must return immediately, because the call is made asynchronously.</span></span> <span data-ttu-id="f0e5c-125">如果主機無法立即警示工作，它必須在下一次進入可警示的狀態時喚醒。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-125">If the host cannot alert the task immediately, it must wake up the next time it enters a state in which it can be alerted.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f0e5c-126">`Alert` 只會影響執行時間已將 WAIT_ALERTABLE [WAIT_OPTION](wait-option-enumeration.md) 值傳遞給方法（例如 [聯結](ihosttask-join-method.md)）的工作。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-126">`Alert` affects only those tasks to which the runtime has passed a [WAIT_OPTION](wait-option-enumeration.md) value of WAIT_ALERTABLE to methods such as [Join](ihosttask-join-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0e5c-127">需求</span><span class="sxs-lookup"><span data-stu-id="f0e5c-127">Requirements</span></span>  

 <span data-ttu-id="f0e5c-128">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f0e5c-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0e5c-129">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f0e5c-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f0e5c-130">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="f0e5c-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0e5c-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0e5c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0e5c-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0e5c-132">See also</span></span>

- [<span data-ttu-id="f0e5c-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="f0e5c-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="f0e5c-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="f0e5c-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="f0e5c-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="f0e5c-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="f0e5c-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="f0e5c-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
