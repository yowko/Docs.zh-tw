---
title: ICLRTask::ExitTask 方法
ms.date: 03/30/2017
api_name:
- ICLRTask.ExitTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::ExitTask
helpviewer_keywords:
- ExitTask method [.NET Framework hosting]
- ICLRTask::ExitTask method [.NET Framework hosting]
ms.assetid: 746c85a6-4b33-4f72-a2e9-379fdf2e96af
topic_type:
- apiref
ms.openlocfilehash: 3f6ccf2eb25e96e0f94c558fb642b153ae3472c1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124901"
---
# <a name="iclrtaskexittask-method"></a><span data-ttu-id="e1f2b-102">ICLRTask::ExitTask 方法</span><span class="sxs-lookup"><span data-stu-id="e1f2b-102">ICLRTask::ExitTask Method</span></span>
<span data-ttu-id="e1f2b-103">通知 common language runtime （CLR）目前[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)實例所代表的工作正在結束，並嘗試正常關閉工作。</span><span class="sxs-lookup"><span data-stu-id="e1f2b-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is ending, and attempts to shut the task down gracefully.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1f2b-104">語法</span><span class="sxs-lookup"><span data-stu-id="e1f2b-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e1f2b-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="e1f2b-105">Return Value</span></span>  
  
|<span data-ttu-id="e1f2b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e1f2b-106">HRESULT</span></span>|<span data-ttu-id="e1f2b-107">描述</span><span class="sxs-lookup"><span data-stu-id="e1f2b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e1f2b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e1f2b-108">S_OK</span></span>|<span data-ttu-id="e1f2b-109">已成功傳回 `ExitTask`。</span><span class="sxs-lookup"><span data-stu-id="e1f2b-109">`ExitTask` returned successfully.</span></span>|  
|<span data-ttu-id="e1f2b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e1f2b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e1f2b-111">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="e1f2b-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e1f2b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e1f2b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e1f2b-113">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="e1f2b-113">The call timed out.</span></span>|  
|<span data-ttu-id="e1f2b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e1f2b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e1f2b-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="e1f2b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e1f2b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e1f2b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e1f2b-117">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="e1f2b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e1f2b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e1f2b-118">E_FAIL</span></span>|<span data-ttu-id="e1f2b-119">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="e1f2b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e1f2b-120">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="e1f2b-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e1f2b-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="e1f2b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1f2b-122">備註</span><span class="sxs-lookup"><span data-stu-id="e1f2b-122">Remarks</span></span>  
 <span data-ttu-id="e1f2b-123">`ExitTask` 嘗試正常關閉工作，其方式類似于從非受控類型程式庫卸離執行緒。</span><span class="sxs-lookup"><span data-stu-id="e1f2b-123">`ExitTask` attempts a clean shutdown of a task, in a manner analogous to detaching a thread from an unmanaged type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1f2b-124">需求</span><span class="sxs-lookup"><span data-stu-id="e1f2b-124">Requirements</span></span>  
 <span data-ttu-id="e1f2b-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e1f2b-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1f2b-126">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="e1f2b-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e1f2b-127">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e1f2b-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e1f2b-128">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1f2b-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1f2b-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="e1f2b-129">See also</span></span>

- [<span data-ttu-id="e1f2b-130">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="e1f2b-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="e1f2b-131">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="e1f2b-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="e1f2b-132">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="e1f2b-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="e1f2b-133">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="e1f2b-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
