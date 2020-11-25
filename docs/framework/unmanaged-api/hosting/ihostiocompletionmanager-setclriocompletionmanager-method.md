---
title: IHostIoCompletionManager::SetCLRIoCompletionManager 方法
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetCLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager method [.NET Framework hosting]
- SetCLRIoCompletionManager method [.NET Framework hosting]
ms.assetid: 4254bb01-3a14-4f34-a3be-60ff1f5072b5
topic_type:
- apiref
ms.openlocfilehash: d370cc81942269bd79e06e0fa57fe5d79832b3c2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724841"
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="7e19e-102">IHostIoCompletionManager::SetCLRIoCompletionManager 方法</span><span class="sxs-lookup"><span data-stu-id="7e19e-102">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>

<span data-ttu-id="7e19e-103">為主機提供 [ICLRIoCompletionManager](iclriocompletionmanager-interface.md) 實例的介面指標，此實例是由 common language RUNTIME (CLR) 所執行。</span><span class="sxs-lookup"><span data-stu-id="7e19e-103">Provides the host with an interface pointer to the [ICLRIoCompletionManager](iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e19e-104">語法</span><span class="sxs-lookup"><span data-stu-id="7e19e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e19e-105">參數</span><span class="sxs-lookup"><span data-stu-id="7e19e-105">Parameters</span></span>  

 `pManager`  
 <span data-ttu-id="7e19e-106">在 `ICLRIoCompletionManager` CLR 所提供之實例的介面指標。</span><span class="sxs-lookup"><span data-stu-id="7e19e-106">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e19e-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="7e19e-107">Return Value</span></span>  
  
|<span data-ttu-id="7e19e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7e19e-108">HRESULT</span></span>|<span data-ttu-id="7e19e-109">描述</span><span class="sxs-lookup"><span data-stu-id="7e19e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7e19e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7e19e-110">S_OK</span></span>|<span data-ttu-id="7e19e-111">`SetCLRIoCompletionManager` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="7e19e-111">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="7e19e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7e19e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7e19e-113">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="7e19e-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7e19e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7e19e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7e19e-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="7e19e-115">The call timed out.</span></span>|  
|<span data-ttu-id="7e19e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7e19e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7e19e-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="7e19e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7e19e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7e19e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7e19e-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="7e19e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7e19e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7e19e-120">E_FAIL</span></span>|<span data-ttu-id="7e19e-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="7e19e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7e19e-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="7e19e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7e19e-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="7e19e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e19e-124">備註</span><span class="sxs-lookup"><span data-stu-id="7e19e-124">Remarks</span></span>  

 <span data-ttu-id="7e19e-125">在 CLR 呼叫之後 `SetCLRIoCompletionManager` ，主機必須呼叫 [ICLRIoCompletionManager：： OnComplete](iclriocompletionmanager-oncomplete-method.md) ，以在完成 i/o 要求時通知 CLR。</span><span class="sxs-lookup"><span data-stu-id="7e19e-125">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e19e-126">需求</span><span class="sxs-lookup"><span data-stu-id="7e19e-126">Requirements</span></span>  

 <span data-ttu-id="7e19e-127">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7e19e-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e19e-128">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="7e19e-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7e19e-129">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="7e19e-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7e19e-130">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e19e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e19e-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e19e-131">See also</span></span>

- [<span data-ttu-id="7e19e-132">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="7e19e-132">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="7e19e-133">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="7e19e-133">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
