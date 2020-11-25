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
ms.openlocfilehash: bf3ddd91a58669540ef310e268162ec78408494f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702022"
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="fa4ab-102">IHostTaskManager::SwitchToTask 方法</span><span class="sxs-lookup"><span data-stu-id="fa4ab-102">IHostTaskManager::SwitchToTask Method</span></span>

<span data-ttu-id="fa4ab-103">通知主機應該切換出目前的工作。</span><span class="sxs-lookup"><span data-stu-id="fa4ab-103">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa4ab-104">語法</span><span class="sxs-lookup"><span data-stu-id="fa4ab-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa4ab-105">參數</span><span class="sxs-lookup"><span data-stu-id="fa4ab-105">Parameters</span></span>  

 `option`  
 <span data-ttu-id="fa4ab-106">在其中一個 [WAIT_OPTION](wait-option-enumeration.md) 列舉值，表示當要求的作業封鎖時，主機應該採取的動作。</span><span class="sxs-lookup"><span data-stu-id="fa4ab-106">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa4ab-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="fa4ab-107">Return Value</span></span>  
  
|<span data-ttu-id="fa4ab-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fa4ab-108">HRESULT</span></span>|<span data-ttu-id="fa4ab-109">描述</span><span class="sxs-lookup"><span data-stu-id="fa4ab-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fa4ab-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fa4ab-110">S_OK</span></span>|<span data-ttu-id="fa4ab-111">`SwitchToTask` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="fa4ab-111">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="fa4ab-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fa4ab-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fa4ab-113">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="fa4ab-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fa4ab-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fa4ab-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fa4ab-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="fa4ab-115">The call timed out.</span></span>|  
|<span data-ttu-id="fa4ab-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fa4ab-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fa4ab-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="fa4ab-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fa4ab-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fa4ab-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fa4ab-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="fa4ab-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fa4ab-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fa4ab-120">E_FAIL</span></span>|<span data-ttu-id="fa4ab-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="fa4ab-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fa4ab-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="fa4ab-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fa4ab-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="fa4ab-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa4ab-124">備註</span><span class="sxs-lookup"><span data-stu-id="fa4ab-124">Remarks</span></span>  

 <span data-ttu-id="fa4ab-125">主機可以視需要或需要在另一項工作中切換。</span><span class="sxs-lookup"><span data-stu-id="fa4ab-125">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fa4ab-126">`SwitchToTask` 未指定主機應切換至哪個工作;它只會指定應從中切換的工作。</span><span class="sxs-lookup"><span data-stu-id="fa4ab-126">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa4ab-127">需求</span><span class="sxs-lookup"><span data-stu-id="fa4ab-127">Requirements</span></span>  

 <span data-ttu-id="fa4ab-128">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fa4ab-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa4ab-129">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="fa4ab-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fa4ab-130">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="fa4ab-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fa4ab-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa4ab-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa4ab-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa4ab-132">See also</span></span>

- [<span data-ttu-id="fa4ab-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="fa4ab-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="fa4ab-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="fa4ab-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="fa4ab-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="fa4ab-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="fa4ab-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="fa4ab-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
