---
title: ICLRTask::SetTaskIdentifier 方法
ms.date: 03/30/2017
api_name:
- ICLRTask.SetTaskIdentifier
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SetTaskIdentifier
helpviewer_keywords:
- SetTaskIdentifier method [.NET Framework hosting]
- ICLRTask::SetTaskIdentifier method [.NET Framework hosting]
ms.assetid: bdb7f047-1e90-40fc-9e3b-d44a16509073
topic_type:
- apiref
ms.openlocfilehash: e1b93356fd40aacdec2e764946e3e3b12d0bd306
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762938"
---
# <a name="iclrtasksettaskidentifier-method"></a><span data-ttu-id="138bc-102">ICLRTask::SetTaskIdentifier 方法</span><span class="sxs-lookup"><span data-stu-id="138bc-102">ICLRTask::SetTaskIdentifier Method</span></span>
<span data-ttu-id="138bc-103">指示 common language runtime （CLR）將指定的識別碼值與目前[ICLRTask](iclrtask-interface.md)實例所代表的工作產生關聯。</span><span class="sxs-lookup"><span data-stu-id="138bc-103">Instructs the common language runtime (CLR) to associate the specified identifier value with the task represented by the current [ICLRTask](iclrtask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="138bc-104">語法</span><span class="sxs-lookup"><span data-stu-id="138bc-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTaskIdentifier (  
    [in] DWORD Asked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="138bc-105">參數</span><span class="sxs-lookup"><span data-stu-id="138bc-105">Parameters</span></span>  
 `Asked`  
 <span data-ttu-id="138bc-106">在Common language runtime 的唯一識別碼，與目前實例所代表的工作產生關聯 `ICLRTask` 。</span><span class="sxs-lookup"><span data-stu-id="138bc-106">[in] The unique identifier for the common language runtime to associate with the task represented by the current `ICLRTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="138bc-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="138bc-107">Return Value</span></span>  
  
|<span data-ttu-id="138bc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="138bc-108">HRESULT</span></span>|<span data-ttu-id="138bc-109">Description</span><span class="sxs-lookup"><span data-stu-id="138bc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="138bc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="138bc-110">S_OK</span></span>|<span data-ttu-id="138bc-111">`SetTaskIdentifier`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="138bc-111">`SetTaskIdentifier` returned successfully.</span></span>|  
|<span data-ttu-id="138bc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="138bc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="138bc-113">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="138bc-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="138bc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="138bc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="138bc-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="138bc-115">The call timed out.</span></span>|  
|<span data-ttu-id="138bc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="138bc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="138bc-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="138bc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="138bc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="138bc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="138bc-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="138bc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="138bc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="138bc-120">E_FAIL</span></span>|<span data-ttu-id="138bc-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="138bc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="138bc-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="138bc-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="138bc-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="138bc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="138bc-124">備註</span><span class="sxs-lookup"><span data-stu-id="138bc-124">Remarks</span></span>  
 <span data-ttu-id="138bc-125">主機可以將識別碼與工作產生關聯，以協助在偵錯工具環境中整合 CLR 和主機。</span><span class="sxs-lookup"><span data-stu-id="138bc-125">The host can associate an identifier with a task to help integrate the CLR and the host in a debugging environment.</span></span> <span data-ttu-id="138bc-126">識別碼對於 CLR 沒有意義。</span><span class="sxs-lookup"><span data-stu-id="138bc-126">The identifier has no meaning for the CLR.</span></span> <span data-ttu-id="138bc-127">CLR 會將它傳遞給偵錯工具應用程式。</span><span class="sxs-lookup"><span data-stu-id="138bc-127">The CLR passes it along to a debugger application.</span></span> <span data-ttu-id="138bc-128">偵錯工具可以使用此識別碼，將 CLR 呼叫堆疊與主控制項呼叫堆疊建立關聯，並在偵錯工具的使用者介面中查看其各自的追蹤資訊時，讓它們各自成為統一的。</span><span class="sxs-lookup"><span data-stu-id="138bc-128">The debugger can use this identifier to associate a CLR call stack with a host call stack, and enable their respective trace information to be unified when viewed in the debugger's user interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="138bc-129">規格需求</span><span class="sxs-lookup"><span data-stu-id="138bc-129">Requirements</span></span>  
 <span data-ttu-id="138bc-130">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="138bc-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="138bc-131">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="138bc-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="138bc-132">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="138bc-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="138bc-133">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="138bc-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="138bc-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="138bc-134">See also</span></span>

- [<span data-ttu-id="138bc-135">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="138bc-135">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="138bc-136">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="138bc-136">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="138bc-137">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="138bc-137">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="138bc-138">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="138bc-138">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
