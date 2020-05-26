---
title: IHostTaskManager::Sleep 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.Sleep
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::Sleep
helpviewer_keywords:
- IHostTaskManager::Sleep method [.NET Framework hosting]
- Sleep method, IHostTaskManager interface [.NET Framework hosting]
ms.assetid: f67d25f3-9199-4c5f-b1e8-1c819243cfd5
topic_type:
- apiref
ms.openlocfilehash: bb12547155383bb410f592018232ca6f688bab8a
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841902"
---
# <a name="ihosttaskmanagersleep-method"></a><span data-ttu-id="c8370-102">IHostTaskManager::Sleep 方法</span><span class="sxs-lookup"><span data-stu-id="c8370-102">IHostTaskManager::Sleep Method</span></span>
<span data-ttu-id="c8370-103">通知主機目前的工作即將進入睡眠狀態。</span><span class="sxs-lookup"><span data-stu-id="c8370-103">Notifies the host that the current task is going to sleep.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8370-104">語法</span><span class="sxs-lookup"><span data-stu-id="c8370-104">Syntax</span></span>  
  
```cpp  
HRESULT Sleep (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8370-105">參數</span><span class="sxs-lookup"><span data-stu-id="c8370-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="c8370-106">在執行緒將進入睡眠狀態的時間間隔（以毫秒為單位）。</span><span class="sxs-lookup"><span data-stu-id="c8370-106">[in] The time interval, in milliseconds, that the thread will sleep.</span></span>  
  
 `option`  
 <span data-ttu-id="c8370-107">在其中一個[WAIT_OPTION](wait-option-enumeration.md)列舉值，指出當此動作封鎖時，主機應採取的動作。</span><span class="sxs-lookup"><span data-stu-id="c8370-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) enumeration values, indicating what action the host should take if this action blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8370-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="c8370-108">Return Value</span></span>  
  
|<span data-ttu-id="c8370-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c8370-109">HRESULT</span></span>|<span data-ttu-id="c8370-110">描述</span><span class="sxs-lookup"><span data-stu-id="c8370-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c8370-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c8370-111">S_OK</span></span>|<span data-ttu-id="c8370-112">`Sleep`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="c8370-112">`Sleep` returned successfully.</span></span>|  
|<span data-ttu-id="c8370-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c8370-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c8370-114">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="c8370-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c8370-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c8370-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c8370-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="c8370-116">The call timed out.</span></span>|  
|<span data-ttu-id="c8370-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c8370-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c8370-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="c8370-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c8370-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c8370-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c8370-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="c8370-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c8370-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c8370-121">E_FAIL</span></span>|<span data-ttu-id="c8370-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="c8370-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c8370-123">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="c8370-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c8370-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="c8370-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8370-125">備註</span><span class="sxs-lookup"><span data-stu-id="c8370-125">Remarks</span></span>  
 <span data-ttu-id="c8370-126">CLR 通常 `IHostTaskManager::Sleep` <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> 會在從使用者程式碼呼叫時呼叫。</span><span class="sxs-lookup"><span data-stu-id="c8370-126">The CLR typically calls `IHostTaskManager::Sleep` when <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is called from user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8370-127">規格需求</span><span class="sxs-lookup"><span data-stu-id="c8370-127">Requirements</span></span>  
 <span data-ttu-id="c8370-128">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c8370-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8370-129">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="c8370-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c8370-130">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c8370-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8370-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8370-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8370-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8370-132">See also</span></span>

- [<span data-ttu-id="c8370-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="c8370-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="c8370-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="c8370-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="c8370-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="c8370-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="c8370-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="c8370-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
