---
title: "ICLRSyncManager::DeleteRWLockOwnerIterator 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRSyncManager.DeleteRWLockOwnerIterator
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRSyncManager::DeleteRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator method [.NET Framework hosting]
- DeleteRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: fcfd340a-b7d6-44e4-8167-2c05b789d483
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dce6699dc625c5c867befe1bc2e307cfaea7719a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="bc511-102">ICLRSyncManager::DeleteRWLockOwnerIterator 方法</span><span class="sxs-lookup"><span data-stu-id="bc511-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>
<span data-ttu-id="bc511-103">要求 common language runtime (CLR) 損毀的呼叫所建立的迭代器[iclrsyncmanager:: Createrwlockowneriterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md)。</span><span class="sxs-lookup"><span data-stu-id="bc511-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc511-104">語法</span><span class="sxs-lookup"><span data-stu-id="bc511-104">Syntax</span></span>  
  
```  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bc511-105">參數</span><span class="sxs-lookup"><span data-stu-id="bc511-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="bc511-106">[in]使用呼叫所建立的迭代器`CreateRWLockOwnerIterator`。</span><span class="sxs-lookup"><span data-stu-id="bc511-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc511-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="bc511-107">Return Value</span></span>  
  
|<span data-ttu-id="bc511-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bc511-108">HRESULT</span></span>|<span data-ttu-id="bc511-109">描述</span><span class="sxs-lookup"><span data-stu-id="bc511-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bc511-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bc511-110">S_OK</span></span>|<span data-ttu-id="bc511-111">`DeleteRWLockOwnerIterator`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="bc511-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="bc511-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bc511-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bc511-113">CLR 已載入處理序，或在它無法執行 managed 程式碼，或已成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="bc511-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="bc511-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bc511-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bc511-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="bc511-115">The call timed out.</span></span>|  
|<span data-ttu-id="bc511-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bc511-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bc511-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="bc511-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bc511-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bc511-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bc511-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="bc511-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bc511-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bc511-120">E_FAIL</span></span>|<span data-ttu-id="bc511-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="bc511-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bc511-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="bc511-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bc511-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="bc511-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc511-124">備註</span><span class="sxs-lookup"><span data-stu-id="bc511-124">Remarks</span></span>  
 <span data-ttu-id="bc511-125">主機可以呼叫這個方法和`CreateRWLockOwnerIterator`以確保其執行緒實作保持同步。</span><span class="sxs-lookup"><span data-stu-id="bc511-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc511-126">需求</span><span class="sxs-lookup"><span data-stu-id="bc511-126">Requirements</span></span>  
 <span data-ttu-id="bc511-127">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bc511-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc511-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bc511-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bc511-129">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="bc511-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc511-130">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc511-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc511-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="bc511-131">See Also</span></span>  
 [<span data-ttu-id="bc511-132">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="bc511-132">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="bc511-133">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="bc511-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
