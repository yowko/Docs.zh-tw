---
title: IHostTaskManager::SwitchToTask 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SwitchToTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SwitchToTask
helpviewer_keywords:
- IHostTaskManager::SwitchToTask method [.NET Framework hosting]
- SwitchToTask method [.NET Framework hosting]
ms.assetid: 35d0c27e-4b14-49ce-810d-7ab2120177e8
topic_type:
- apiref
ms.openlocfilehash: 7d1511924fc70c42252881a46f8aebb437a3f4f7
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841941"
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="99ed2-102">IHostTaskManager::SwitchToTask 方法</span><span class="sxs-lookup"><span data-stu-id="99ed2-102">IHostTaskManager::SwitchToTask Method</span></span>
<span data-ttu-id="99ed2-103">通知主機應該切換出目前的工作。</span><span class="sxs-lookup"><span data-stu-id="99ed2-103">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99ed2-104">語法</span><span class="sxs-lookup"><span data-stu-id="99ed2-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99ed2-105">參數</span><span class="sxs-lookup"><span data-stu-id="99ed2-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="99ed2-106">在其中一個[WAIT_OPTION](wait-option-enumeration.md)列舉值，指出當要求的作業封鎖時，主機應採取的動作。</span><span class="sxs-lookup"><span data-stu-id="99ed2-106">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99ed2-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="99ed2-107">Return Value</span></span>  
  
|<span data-ttu-id="99ed2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="99ed2-108">HRESULT</span></span>|<span data-ttu-id="99ed2-109">描述</span><span class="sxs-lookup"><span data-stu-id="99ed2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="99ed2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="99ed2-110">S_OK</span></span>|<span data-ttu-id="99ed2-111">`SwitchToTask`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="99ed2-111">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="99ed2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="99ed2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="99ed2-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="99ed2-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="99ed2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="99ed2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="99ed2-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="99ed2-115">The call timed out.</span></span>|  
|<span data-ttu-id="99ed2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="99ed2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="99ed2-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="99ed2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="99ed2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="99ed2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="99ed2-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="99ed2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="99ed2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="99ed2-120">E_FAIL</span></span>|<span data-ttu-id="99ed2-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="99ed2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="99ed2-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="99ed2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="99ed2-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="99ed2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99ed2-124">備註</span><span class="sxs-lookup"><span data-stu-id="99ed2-124">Remarks</span></span>  
 <span data-ttu-id="99ed2-125">主機可以視需要或需要切換至另一個工作。</span><span class="sxs-lookup"><span data-stu-id="99ed2-125">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99ed2-126">`SwitchToTask`不會指定主機應切換至哪一項工作;它只會指定應該切換的工作。</span><span class="sxs-lookup"><span data-stu-id="99ed2-126">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99ed2-127">規格需求</span><span class="sxs-lookup"><span data-stu-id="99ed2-127">Requirements</span></span>  
 <span data-ttu-id="99ed2-128">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="99ed2-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99ed2-129">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="99ed2-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="99ed2-130">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="99ed2-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99ed2-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99ed2-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99ed2-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99ed2-132">See also</span></span>

- [<span data-ttu-id="99ed2-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="99ed2-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="99ed2-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="99ed2-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="99ed2-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="99ed2-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="99ed2-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="99ed2-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
