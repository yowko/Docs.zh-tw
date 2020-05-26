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
ms.openlocfilehash: 7271fe8e28da0bb5fd878aae5d36ab703e64ebf0
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803026"
---
# <a name="ihosttaskalert-method"></a><span data-ttu-id="85dea-102">IHostTask::Alert 方法</span><span class="sxs-lookup"><span data-stu-id="85dea-102">IHostTask::Alert Method</span></span>
<span data-ttu-id="85dea-103">要求主機喚醒目前[IHostTask](ihosttask-interface.md)實例所代表的工作，讓工作可以中止。</span><span class="sxs-lookup"><span data-stu-id="85dea-103">Requests that the host wake the task represented by the current [IHostTask](ihosttask-interface.md) instance, so the task can be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85dea-104">語法</span><span class="sxs-lookup"><span data-stu-id="85dea-104">Syntax</span></span>  
  
```cpp  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="85dea-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="85dea-105">Return Value</span></span>  
  
|<span data-ttu-id="85dea-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="85dea-106">HRESULT</span></span>|<span data-ttu-id="85dea-107">描述</span><span class="sxs-lookup"><span data-stu-id="85dea-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="85dea-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="85dea-108">S_OK</span></span>|<span data-ttu-id="85dea-109">此方法已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="85dea-109">The method returned successfully.</span></span>|  
|<span data-ttu-id="85dea-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="85dea-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="85dea-111">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="85dea-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="85dea-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="85dea-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="85dea-113">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="85dea-113">The call timed out.</span></span>|  
|<span data-ttu-id="85dea-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="85dea-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="85dea-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="85dea-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="85dea-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="85dea-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="85dea-117">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="85dea-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="85dea-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="85dea-118">E_FAIL</span></span>|<span data-ttu-id="85dea-119">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="85dea-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="85dea-120">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="85dea-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="85dea-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="85dea-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85dea-122">備註</span><span class="sxs-lookup"><span data-stu-id="85dea-122">Remarks</span></span>  
 <span data-ttu-id="85dea-123">`Alert`當 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 從使用者程式碼呼叫，或 <xref:System.AppDomain> 與目前的相關聯的關閉時，CLR 會呼叫方法 <xref:System.Threading.Thread> 。</span><span class="sxs-lookup"><span data-stu-id="85dea-123">The CLR calls the `Alert` method when <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is called from user code, or when the <xref:System.AppDomain> associated with the current <xref:System.Threading.Thread> shuts down.</span></span> <span data-ttu-id="85dea-124">主機必須立即傳回，因為呼叫是以非同步方式進行。</span><span class="sxs-lookup"><span data-stu-id="85dea-124">The host must return immediately, because the call is made asynchronously.</span></span> <span data-ttu-id="85dea-125">如果主機無法立即警示工作，它必須在下一次進入可警示的狀態時喚醒。</span><span class="sxs-lookup"><span data-stu-id="85dea-125">If the host cannot alert the task immediately, it must wake up the next time it enters a state in which it can be alerted.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="85dea-126">`Alert`只會影響執行時間已將 WAIT_ALERTABLE 的[WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)值傳遞給方法的工作，例如[聯結](ihosttask-join-method.md)。</span><span class="sxs-lookup"><span data-stu-id="85dea-126">`Alert` affects only those tasks to which the runtime has passed a [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) value of WAIT_ALERTABLE to methods such as [Join](ihosttask-join-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85dea-127">規格需求</span><span class="sxs-lookup"><span data-stu-id="85dea-127">Requirements</span></span>  
 <span data-ttu-id="85dea-128">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="85dea-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85dea-129">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="85dea-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="85dea-130">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="85dea-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="85dea-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85dea-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85dea-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85dea-132">See also</span></span>

- [<span data-ttu-id="85dea-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="85dea-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="85dea-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="85dea-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="85dea-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="85dea-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="85dea-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="85dea-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
