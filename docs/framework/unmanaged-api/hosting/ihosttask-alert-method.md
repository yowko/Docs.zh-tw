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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b1c5132be72cfd9f70d3a81297425109f636195
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623752"
---
# <a name="ihosttaskalert-method"></a><span data-ttu-id="78aa3-102">IHostTask::Alert 方法</span><span class="sxs-lookup"><span data-stu-id="78aa3-102">IHostTask::Alert Method</span></span>
<span data-ttu-id="78aa3-103">要求主機喚醒表示由目前的工作[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)執行個體，因此可以中止的工作。</span><span class="sxs-lookup"><span data-stu-id="78aa3-103">Requests that the host wake the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance, so the task can be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78aa3-104">語法</span><span class="sxs-lookup"><span data-stu-id="78aa3-104">Syntax</span></span>  
  
```  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="78aa3-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="78aa3-105">Return Value</span></span>  
  
|<span data-ttu-id="78aa3-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="78aa3-106">HRESULT</span></span>|<span data-ttu-id="78aa3-107">描述</span><span class="sxs-lookup"><span data-stu-id="78aa3-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="78aa3-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="78aa3-108">S_OK</span></span>|<span data-ttu-id="78aa3-109">此方法傳回成功。</span><span class="sxs-lookup"><span data-stu-id="78aa3-109">The method returned successfully.</span></span>|  
|<span data-ttu-id="78aa3-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="78aa3-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="78aa3-111">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="78aa3-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="78aa3-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="78aa3-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="78aa3-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="78aa3-113">The call timed out.</span></span>|  
|<span data-ttu-id="78aa3-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="78aa3-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="78aa3-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="78aa3-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="78aa3-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="78aa3-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="78aa3-117">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="78aa3-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="78aa3-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="78aa3-118">E_FAIL</span></span>|<span data-ttu-id="78aa3-119">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="78aa3-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="78aa3-120">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="78aa3-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="78aa3-121">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="78aa3-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78aa3-122">備註</span><span class="sxs-lookup"><span data-stu-id="78aa3-122">Remarks</span></span>  
 <span data-ttu-id="78aa3-123">CLR 會呼叫`Alert`方法時<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>呼叫使用者程式碼，或當<xref:System.AppDomain>目前相關聯<xref:System.Threading.Thread>關閉。</span><span class="sxs-lookup"><span data-stu-id="78aa3-123">The CLR calls the `Alert` method when <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is called from user code, or when the <xref:System.AppDomain> associated with the current <xref:System.Threading.Thread> shuts down.</span></span> <span data-ttu-id="78aa3-124">主機必須立即傳回，因為以非同步方式進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="78aa3-124">The host must return immediately, because the call is made asynchronously.</span></span> <span data-ttu-id="78aa3-125">如果主應用程式無法立即警示工作，它必須喚醒的下次進入中警示的狀態。</span><span class="sxs-lookup"><span data-stu-id="78aa3-125">If the host cannot alert the task immediately, it must wake up the next time it enters a state in which it can be alerted.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="78aa3-126">`Alert` 會影響執行階段已傳遞到的工作[WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)這類方法的 WAIT_ALERTABLE 值[聯結](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)。</span><span class="sxs-lookup"><span data-stu-id="78aa3-126">`Alert` affects only those tasks to which the runtime has passed a [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) value of WAIT_ALERTABLE to methods such as [Join](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78aa3-127">需求</span><span class="sxs-lookup"><span data-stu-id="78aa3-127">Requirements</span></span>  
 <span data-ttu-id="78aa3-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="78aa3-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78aa3-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="78aa3-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="78aa3-130">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="78aa3-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78aa3-131">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78aa3-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78aa3-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78aa3-132">See also</span></span>
- [<span data-ttu-id="78aa3-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="78aa3-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="78aa3-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="78aa3-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="78aa3-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="78aa3-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="78aa3-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="78aa3-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
