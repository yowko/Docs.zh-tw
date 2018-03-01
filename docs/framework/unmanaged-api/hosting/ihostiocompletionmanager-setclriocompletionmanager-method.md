---
title: "IHostIoCompletionManager::SetCLRIoCompletionManager 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4fde1045fd0f15e7255a163c1f1b041800e85921
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="4cd5f-102">IHostIoCompletionManager::SetCLRIoCompletionManager 方法</span><span class="sxs-lookup"><span data-stu-id="4cd5f-102">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>
<span data-ttu-id="4cd5f-103">主機提供的介面指標[ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) common language runtime (CLR) 所實作的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4cd5f-103">Provides the host with an interface pointer to the [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cd5f-104">語法</span><span class="sxs-lookup"><span data-stu-id="4cd5f-104">Syntax</span></span>  
  
```  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4cd5f-105">參數</span><span class="sxs-lookup"><span data-stu-id="4cd5f-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="4cd5f-106">[in]介面指標`ICLRIoCompletionManager`CLR 所提供的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4cd5f-106">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4cd5f-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="4cd5f-107">Return Value</span></span>  
  
|<span data-ttu-id="4cd5f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4cd5f-108">HRESULT</span></span>|<span data-ttu-id="4cd5f-109">描述</span><span class="sxs-lookup"><span data-stu-id="4cd5f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4cd5f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4cd5f-110">S_OK</span></span>|<span data-ttu-id="4cd5f-111">`SetCLRIoCompletionManager`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="4cd5f-111">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="4cd5f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4cd5f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4cd5f-113">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="4cd5f-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4cd5f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4cd5f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4cd5f-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="4cd5f-115">The call timed out.</span></span>|  
|<span data-ttu-id="4cd5f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4cd5f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4cd5f-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="4cd5f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4cd5f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4cd5f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4cd5f-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="4cd5f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4cd5f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4cd5f-120">E_FAIL</span></span>|<span data-ttu-id="4cd5f-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="4cd5f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4cd5f-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="4cd5f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4cd5f-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="4cd5f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4cd5f-124">備註</span><span class="sxs-lookup"><span data-stu-id="4cd5f-124">Remarks</span></span>  
 <span data-ttu-id="4cd5f-125">CLR 已呼叫之後`SetCLRIoCompletionManager`，主機必須呼叫[iclriocompletionmanager:: Oncomplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) I/O 要求已完成時，通知 CLR。</span><span class="sxs-lookup"><span data-stu-id="4cd5f-125">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cd5f-126">需求</span><span class="sxs-lookup"><span data-stu-id="4cd5f-126">Requirements</span></span>  
 <span data-ttu-id="4cd5f-127">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4cd5f-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cd5f-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4cd5f-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4cd5f-129">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4cd5f-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4cd5f-130">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cd5f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cd5f-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="4cd5f-131">See Also</span></span>  
 [<span data-ttu-id="4cd5f-132">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="4cd5f-132">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="4cd5f-133">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="4cd5f-133">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
