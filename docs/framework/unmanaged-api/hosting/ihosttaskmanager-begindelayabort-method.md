---
title: IHostTaskManager::BeginDelayAbort 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginDelayAbort
helpviewer_keywords:
- BeginDelayAbort method [.NET Framework hosting]
- IHostTaskManager::BeginDelayAbort method [.NET Framework hosting]
ms.assetid: 75f42a8b-ed68-4718-a030-a179cfba7d72
topic_type:
- apiref
ms.openlocfilehash: f72cc15904d098e159dd7f75f673d43ae987998d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727324"
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a><span data-ttu-id="08bcc-102">IHostTaskManager::BeginDelayAbort 方法</span><span class="sxs-lookup"><span data-stu-id="08bcc-102">IHostTaskManager::BeginDelayAbort Method</span></span>

<span data-ttu-id="08bcc-103">通知主機 managed 程式碼所輸入的期間，不能中止目前的工作。</span><span class="sxs-lookup"><span data-stu-id="08bcc-103">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08bcc-104">語法</span><span class="sxs-lookup"><span data-stu-id="08bcc-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="08bcc-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="08bcc-105">Return Value</span></span>  
  
|<span data-ttu-id="08bcc-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="08bcc-106">HRESULT</span></span>|<span data-ttu-id="08bcc-107">描述</span><span class="sxs-lookup"><span data-stu-id="08bcc-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="08bcc-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="08bcc-108">S_OK</span></span>|<span data-ttu-id="08bcc-109">`BeginDelayAbort` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="08bcc-109">`BeginDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="08bcc-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="08bcc-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="08bcc-111">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="08bcc-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="08bcc-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="08bcc-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="08bcc-113">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="08bcc-113">The call timed out.</span></span>|  
|<span data-ttu-id="08bcc-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="08bcc-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="08bcc-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="08bcc-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="08bcc-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="08bcc-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="08bcc-117">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="08bcc-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="08bcc-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="08bcc-118">E_FAIL</span></span>|<span data-ttu-id="08bcc-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="08bcc-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="08bcc-120">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="08bcc-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="08bcc-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="08bcc-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="08bcc-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="08bcc-122">E_UNEXPECTED</span></span>|<span data-ttu-id="08bcc-123">`BeginDelayAbort` 已經呼叫過，但尚未收到對應的 [EndDelayAbort](ihosttaskmanager-enddelayabort-method.md) 呼叫。</span><span class="sxs-lookup"><span data-stu-id="08bcc-123">`BeginDelayAbort` has already been called, but the corresponding call to [EndDelayAbort](ihosttaskmanager-enddelayabort-method.md) has not yet been received.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08bcc-124">備註</span><span class="sxs-lookup"><span data-stu-id="08bcc-124">Remarks</span></span>  

 <span data-ttu-id="08bcc-125">在呼叫之前，主機不得中止目前的工作 `EndDelayAbort` 。</span><span class="sxs-lookup"><span data-stu-id="08bcc-125">The host must not abort the current task until `EndDelayAbort` is called.</span></span> <span data-ttu-id="08bcc-126">如果在沒有仲介呼叫的情況下發出另一個呼叫 `BeginDelayAbort` `EndDelayAbort` ，主機應該會傳回 E_UNEXPECTED `BeginDelayAbort` ，且不應該採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="08bcc-126">If another call to `BeginDelayAbort` is made without an intervening call to `EndDelayAbort`, the host should return E_UNEXPECTED from `BeginDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08bcc-127">需求</span><span class="sxs-lookup"><span data-stu-id="08bcc-127">Requirements</span></span>  

 <span data-ttu-id="08bcc-128">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="08bcc-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08bcc-129">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="08bcc-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="08bcc-130">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="08bcc-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08bcc-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08bcc-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08bcc-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08bcc-132">See also</span></span>

- [<span data-ttu-id="08bcc-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="08bcc-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="08bcc-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="08bcc-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="08bcc-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="08bcc-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
