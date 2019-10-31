---
title: ICLRTask::SwitchOut 方法
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchOut
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchOut
helpviewer_keywords:
- ICLRTask::SwitchOut method [.NET Framework hosting]
- SwitchOut method [.NET Framework hosting]
ms.assetid: b6fb168c-b24b-4ecf-a390-2b5ba3317ae6
topic_type:
- apiref
ms.openlocfilehash: f9c2e77013ff9e31a0a2ef3b4ca511b76ae345e1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124605"
---
# <a name="iclrtaskswitchout-method"></a><span data-ttu-id="24231-102">ICLRTask::SwitchOut 方法</span><span class="sxs-lookup"><span data-stu-id="24231-102">ICLRTask::SwitchOut Method</span></span>
<span data-ttu-id="24231-103">通知 common language runtime （CLR），目前[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)實例所代表的工作已不再處於可運作狀態。</span><span class="sxs-lookup"><span data-stu-id="24231-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is no longer in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24231-104">語法</span><span class="sxs-lookup"><span data-stu-id="24231-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchOut ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="24231-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="24231-105">Return Value</span></span>  
  
|<span data-ttu-id="24231-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="24231-106">HRESULT</span></span>|<span data-ttu-id="24231-107">描述</span><span class="sxs-lookup"><span data-stu-id="24231-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="24231-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="24231-108">S_OK</span></span>|<span data-ttu-id="24231-109">已成功傳回 `SwitchOut`。</span><span class="sxs-lookup"><span data-stu-id="24231-109">`SwitchOut` returned successfully.</span></span>|  
|<span data-ttu-id="24231-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="24231-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="24231-111">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="24231-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="24231-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="24231-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="24231-113">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="24231-113">The call timed out.</span></span>|  
|<span data-ttu-id="24231-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="24231-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="24231-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="24231-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="24231-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="24231-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="24231-117">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="24231-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="24231-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="24231-118">E_FAIL</span></span>|<span data-ttu-id="24231-119">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="24231-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="24231-120">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="24231-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="24231-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="24231-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24231-122">備註</span><span class="sxs-lookup"><span data-stu-id="24231-122">Remarks</span></span>  
 <span data-ttu-id="24231-123">主機會呼叫 `SwitchOut` 來通知 CLR 它已暫時停止執行目前 `ICLRTask` 實例所代表的工作，並重新排程工作。</span><span class="sxs-lookup"><span data-stu-id="24231-123">A host calls `SwitchOut` to inform the CLR that it has temporarily stopped executing the task that the current `ICLRTask` instance represents, and will reschedule the task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24231-124">需求</span><span class="sxs-lookup"><span data-stu-id="24231-124">Requirements</span></span>  
 <span data-ttu-id="24231-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="24231-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24231-126">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="24231-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="24231-127">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="24231-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="24231-128">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24231-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24231-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="24231-129">See also</span></span>

- [<span data-ttu-id="24231-130">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="24231-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="24231-131">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="24231-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="24231-132">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="24231-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="24231-133">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="24231-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
