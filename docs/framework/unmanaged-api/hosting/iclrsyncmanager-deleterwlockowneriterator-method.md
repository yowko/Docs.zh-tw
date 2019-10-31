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
ms.openlocfilehash: fb02b5c941e15d172140565e8efb625234947cd7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130570"
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="6ae58-102">ICLRSyncManager::DeleteRWLockOwnerIterator 方法</span><span class="sxs-lookup"><span data-stu-id="6ae58-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>
<span data-ttu-id="6ae58-103">要求 common language runtime （CLR）終結由呼叫[ICLRSyncManager：： CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md)所建立的反覆運算器。</span><span class="sxs-lookup"><span data-stu-id="6ae58-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ae58-104">語法</span><span class="sxs-lookup"><span data-stu-id="6ae58-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ae58-105">參數</span><span class="sxs-lookup"><span data-stu-id="6ae58-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="6ae58-106">在使用 `CreateRWLockOwnerIterator`的呼叫所建立的反覆運算器。</span><span class="sxs-lookup"><span data-stu-id="6ae58-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ae58-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="6ae58-107">Return Value</span></span>  
  
|<span data-ttu-id="6ae58-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6ae58-108">HRESULT</span></span>|<span data-ttu-id="6ae58-109">描述</span><span class="sxs-lookup"><span data-stu-id="6ae58-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6ae58-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6ae58-110">S_OK</span></span>|<span data-ttu-id="6ae58-111">已成功傳回 `DeleteRWLockOwnerIterator`。</span><span class="sxs-lookup"><span data-stu-id="6ae58-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="6ae58-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6ae58-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6ae58-113">CLR 尚未載入進程中，或處於無法執行 managed 程式碼或無法成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="6ae58-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="6ae58-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6ae58-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6ae58-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="6ae58-115">The call timed out.</span></span>|  
|<span data-ttu-id="6ae58-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6ae58-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6ae58-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="6ae58-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6ae58-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6ae58-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6ae58-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="6ae58-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6ae58-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6ae58-120">E_FAIL</span></span>|<span data-ttu-id="6ae58-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="6ae58-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6ae58-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="6ae58-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6ae58-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="6ae58-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ae58-124">備註</span><span class="sxs-lookup"><span data-stu-id="6ae58-124">Remarks</span></span>  
 <span data-ttu-id="6ae58-125">主機可以呼叫這個方法並 `CreateRWLockOwnerIterator`，以確保其執行緒的執行保持同步。</span><span class="sxs-lookup"><span data-stu-id="6ae58-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ae58-126">需求</span><span class="sxs-lookup"><span data-stu-id="6ae58-126">Requirements</span></span>  
 <span data-ttu-id="6ae58-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6ae58-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ae58-128">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="6ae58-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6ae58-129">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6ae58-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ae58-130">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ae58-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ae58-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="6ae58-131">See also</span></span>

- [<span data-ttu-id="6ae58-132">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="6ae58-132">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="6ae58-133">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="6ae58-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
