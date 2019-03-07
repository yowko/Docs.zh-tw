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
ms.openlocfilehash: ba0cabfe9e96ace255235f1aa7d2b80452c4d72e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482882"
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="b569e-102">ICLRSyncManager::DeleteRWLockOwnerIterator 方法</span><span class="sxs-lookup"><span data-stu-id="b569e-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>
<span data-ttu-id="b569e-103">要求 common language runtime (CLR)，損毀的呼叫所建立的迭代器[iclrsyncmanager:: Createrwlockowneriterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md)。</span><span class="sxs-lookup"><span data-stu-id="b569e-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b569e-104">語法</span><span class="sxs-lookup"><span data-stu-id="b569e-104">Syntax</span></span>  
  
```  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b569e-105">參數</span><span class="sxs-lookup"><span data-stu-id="b569e-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="b569e-106">[in]使用呼叫所建立的迭代器`CreateRWLockOwnerIterator`。</span><span class="sxs-lookup"><span data-stu-id="b569e-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b569e-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="b569e-107">Return Value</span></span>  
  
|<span data-ttu-id="b569e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b569e-108">HRESULT</span></span>|<span data-ttu-id="b569e-109">描述</span><span class="sxs-lookup"><span data-stu-id="b569e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b569e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b569e-110">S_OK</span></span>|<span data-ttu-id="b569e-111">`DeleteRWLockOwnerIterator` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="b569e-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="b569e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b569e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b569e-113">CLR 已載入處理序，或處於不能在其中執行 managed 程式碼，或成功地處理所呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="b569e-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="b569e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b569e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b569e-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="b569e-115">The call timed out.</span></span>|  
|<span data-ttu-id="b569e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b569e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b569e-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b569e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b569e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b569e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b569e-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="b569e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b569e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b569e-120">E_FAIL</span></span>|<span data-ttu-id="b569e-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="b569e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b569e-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="b569e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b569e-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b569e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b569e-124">備註</span><span class="sxs-lookup"><span data-stu-id="b569e-124">Remarks</span></span>  
 <span data-ttu-id="b569e-125">主機可以呼叫這個方法和`CreateRWLockOwnerIterator`以確保其執行緒的實作保持同步。</span><span class="sxs-lookup"><span data-stu-id="b569e-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b569e-126">需求</span><span class="sxs-lookup"><span data-stu-id="b569e-126">Requirements</span></span>  
 <span data-ttu-id="b569e-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b569e-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b569e-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b569e-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b569e-129">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b569e-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b569e-130">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b569e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b569e-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b569e-131">See also</span></span>
- [<span data-ttu-id="b569e-132">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="b569e-132">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="b569e-133">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="b569e-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
