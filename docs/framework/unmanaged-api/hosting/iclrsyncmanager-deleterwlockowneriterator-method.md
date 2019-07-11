---
title: ICLRSyncManager::DeleteRWLockOwnerIterator 方法
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.DeleteRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator method [.NET Framework hosting]
- DeleteRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: fcfd340a-b7d6-44e4-8167-2c05b789d483
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a30ac0ab8c985af04709ddd8e8e5dd9bca776dcb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759087"
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="e2e32-102">ICLRSyncManager::DeleteRWLockOwnerIterator 方法</span><span class="sxs-lookup"><span data-stu-id="e2e32-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>
<span data-ttu-id="e2e32-103">要求 common language runtime (CLR)，損毀的呼叫所建立的迭代器[iclrsyncmanager:: Createrwlockowneriterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md)。</span><span class="sxs-lookup"><span data-stu-id="e2e32-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2e32-104">語法</span><span class="sxs-lookup"><span data-stu-id="e2e32-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2e32-105">參數</span><span class="sxs-lookup"><span data-stu-id="e2e32-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="e2e32-106">[in]使用呼叫所建立的迭代器`CreateRWLockOwnerIterator`。</span><span class="sxs-lookup"><span data-stu-id="e2e32-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2e32-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="e2e32-107">Return Value</span></span>  
  
|<span data-ttu-id="e2e32-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e2e32-108">HRESULT</span></span>|<span data-ttu-id="e2e32-109">描述</span><span class="sxs-lookup"><span data-stu-id="e2e32-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e2e32-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e2e32-110">S_OK</span></span>|<span data-ttu-id="e2e32-111">`DeleteRWLockOwnerIterator` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="e2e32-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="e2e32-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e2e32-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e2e32-113">CLR 已載入處理序，或處於不能在其中執行 managed 程式碼，或成功地處理所呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="e2e32-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="e2e32-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e2e32-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e2e32-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="e2e32-115">The call timed out.</span></span>|  
|<span data-ttu-id="e2e32-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e2e32-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e2e32-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="e2e32-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e2e32-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e2e32-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e2e32-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="e2e32-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e2e32-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e2e32-120">E_FAIL</span></span>|<span data-ttu-id="e2e32-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="e2e32-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e2e32-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="e2e32-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e2e32-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="e2e32-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2e32-124">備註</span><span class="sxs-lookup"><span data-stu-id="e2e32-124">Remarks</span></span>  
 <span data-ttu-id="e2e32-125">主機可以呼叫這個方法和`CreateRWLockOwnerIterator`以確保其執行緒的實作保持同步。</span><span class="sxs-lookup"><span data-stu-id="e2e32-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2e32-126">需求</span><span class="sxs-lookup"><span data-stu-id="e2e32-126">Requirements</span></span>  
 <span data-ttu-id="e2e32-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e2e32-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2e32-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e2e32-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e2e32-129">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e2e32-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e2e32-130">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2e32-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2e32-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2e32-131">See also</span></span>

- [<span data-ttu-id="e2e32-132">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="e2e32-132">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="e2e32-133">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="e2e32-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
