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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97d4561c34c03eefc7487f5f96b7a490a480ac19
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780766"
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="0c279-102">IHostIoCompletionManager::SetCLRIoCompletionManager 方法</span><span class="sxs-lookup"><span data-stu-id="0c279-102">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>
<span data-ttu-id="0c279-103">主應用程式提供的介面指標[ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) common language runtime (CLR) 所實作的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0c279-103">Provides the host with an interface pointer to the [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c279-104">語法</span><span class="sxs-lookup"><span data-stu-id="0c279-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c279-105">參數</span><span class="sxs-lookup"><span data-stu-id="0c279-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="0c279-106">[in]介面指標`ICLRIoCompletionManager`CLR 所提供的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0c279-106">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c279-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="0c279-107">Return Value</span></span>  
  
|<span data-ttu-id="0c279-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0c279-108">HRESULT</span></span>|<span data-ttu-id="0c279-109">描述</span><span class="sxs-lookup"><span data-stu-id="0c279-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0c279-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0c279-110">S_OK</span></span>|<span data-ttu-id="0c279-111">`SetCLRIoCompletionManager` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="0c279-111">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="0c279-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0c279-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0c279-113">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="0c279-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0c279-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0c279-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0c279-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="0c279-115">The call timed out.</span></span>|  
|<span data-ttu-id="0c279-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0c279-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0c279-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="0c279-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0c279-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0c279-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0c279-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="0c279-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0c279-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0c279-120">E_FAIL</span></span>|<span data-ttu-id="0c279-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="0c279-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0c279-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="0c279-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0c279-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="0c279-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c279-124">備註</span><span class="sxs-lookup"><span data-stu-id="0c279-124">Remarks</span></span>  
 <span data-ttu-id="0c279-125">CLR 已呼叫之後`SetCLRIoCompletionManager`，主機必須呼叫[iclriocompletionmanager:: Oncomplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) I/O 要求完成時通知 CLR。</span><span class="sxs-lookup"><span data-stu-id="0c279-125">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c279-126">需求</span><span class="sxs-lookup"><span data-stu-id="0c279-126">Requirements</span></span>  
 <span data-ttu-id="0c279-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0c279-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c279-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0c279-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0c279-129">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0c279-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0c279-130">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c279-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c279-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c279-131">See also</span></span>

- [<span data-ttu-id="0c279-132">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="0c279-132">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="0c279-133">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="0c279-133">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
