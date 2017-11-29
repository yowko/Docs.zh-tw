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
ms.openlocfilehash: 3df37a9572c47ce4b4a5080f6aed3f307adba360
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="32cad-102">ICLRSyncManager::DeleteRWLockOwnerIterator 方法</span><span class="sxs-lookup"><span data-stu-id="32cad-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>
<span data-ttu-id="32cad-103">要求 common language runtime (CLR) 損毀的呼叫所建立的迭代器[iclrsyncmanager:: Createrwlockowneriterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md)。</span><span class="sxs-lookup"><span data-stu-id="32cad-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32cad-104">語法</span><span class="sxs-lookup"><span data-stu-id="32cad-104">Syntax</span></span>  
  
```  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32cad-105">參數</span><span class="sxs-lookup"><span data-stu-id="32cad-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="32cad-106">[in]使用呼叫所建立的迭代器`CreateRWLockOwnerIterator`。</span><span class="sxs-lookup"><span data-stu-id="32cad-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32cad-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="32cad-107">Return Value</span></span>  
  
|<span data-ttu-id="32cad-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="32cad-108">HRESULT</span></span>|<span data-ttu-id="32cad-109">描述</span><span class="sxs-lookup"><span data-stu-id="32cad-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="32cad-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="32cad-110">S_OK</span></span>|<span data-ttu-id="32cad-111">`DeleteRWLockOwnerIterator`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="32cad-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="32cad-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="32cad-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="32cad-113">CLR 已載入處理序，或在它無法執行 managed 程式碼，或已成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="32cad-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="32cad-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="32cad-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="32cad-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="32cad-115">The call timed out.</span></span>|  
|<span data-ttu-id="32cad-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="32cad-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="32cad-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="32cad-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="32cad-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="32cad-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="32cad-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="32cad-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="32cad-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="32cad-120">E_FAIL</span></span>|<span data-ttu-id="32cad-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="32cad-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="32cad-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="32cad-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="32cad-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="32cad-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32cad-124">備註</span><span class="sxs-lookup"><span data-stu-id="32cad-124">Remarks</span></span>  
 <span data-ttu-id="32cad-125">主機可以呼叫這個方法和`CreateRWLockOwnerIterator`以確保其執行緒實作保持同步。</span><span class="sxs-lookup"><span data-stu-id="32cad-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32cad-126">需求</span><span class="sxs-lookup"><span data-stu-id="32cad-126">Requirements</span></span>  
 <span data-ttu-id="32cad-127">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="32cad-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32cad-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="32cad-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="32cad-129">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="32cad-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="32cad-130">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32cad-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32cad-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32cad-131">See Also</span></span>  
 [<span data-ttu-id="32cad-132">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="32cad-132">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="32cad-133">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="32cad-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
